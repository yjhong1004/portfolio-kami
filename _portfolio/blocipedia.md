---
layout: post
title: Blocipedia
thumbnail-path: "img/blocipedia.png"
short-description: Build a production quality SaaS app that allows users to create their own wikis.

---

{:.center}
![]({{ site.baseurl }}/img/blocipedia.png)

## Summary

Blocipedia is a web application that allows users to share information. It is similar to Wikipedia, which is an online encyclopedia, created by volunteers around the world.

## Explanation

My goal for this project was to learn how to create a basic Ruby on Rails application and to utilize different Ruby gems.

## Problem

Ruby on Rails is a Model-View-Controller framework. This allows us to build our application with user stories in mind. We want to accomplish the following user stories:

1. As a user, I want to sign up for a free account by providing a username, password and email
2. As a user, I want to sign in and out of Blocipedia
3. As a user with a standard account, I want to create, read, update, and delete public wikis
4. As a developer, I want to offer three user roles: admin, standard, or premium
5. As a developer, I want to seed the development database automatically with users and wikis
6. As a user, I want to upgrade my account from a free to a paid plan
7. As a premium user, I want to create private wikis
8. As a user, I want to edit wikis using Markdown syntax
9. As a premium user, I want to add and remove collaborators for my private wikis

## Solution

Let's take a look at our first user story. We want our users to be able to sign up for an account using their email address. In other words, we want to authenticate our users. Although we can go through our CRUD actions to implement authentication, the easiest way to accomplish this is to utilize our Devise gem. This gem also takes care of our sign in/sign out functions for our users. Now that we have our users authenticated, we want to authorize our users to be able to create, read, update, and delete public wikis. We want to create different roles for our users to authorize certain functions for certain roles. We want to offer three roles: admin, standard, and premium. We have another amazing gem to use to help with our authorization process, called Pundit.

```
after_initialize :init
  def init
    self.role ||= 0.0
  end
  enum role: [:standard, :admin, :premium]
```
After we implement authorization, we want to use seed data to test out our application. We have another great gem, called Faker, that creates fake data for us automatically.

Up to this point of the application, we have our foundation: we have our users and their ability to create wikis.

We want to take it even further. We have two other user roles that we can implement. Our premium role for users should provide users with special privileges. We want to upgrade our users to a paid plan to access the premium features.

Going from the standard free plan to a premium paid plan is a bit complicated. So we can create a user flow to help things along.

An example of a user flow for this app:

```
1. The user signs up for a free plan.
2. The user upgrades their free plan and is prompted to pay with Stripe.
3. The user's role is changed from standard to premium.
4. The user is able to create private wikis.
```

We use Stripe to charge users to change their role from standard to premium. If we have the ability to upgrade a user's role to premium, we should also be able to downgrade a user back to the standard role.

```
def downgrade
    self.wikis.update_all(private: false )
    self.update_attribute(:role, 'standard')
end
```

One privilege for premium users is the ability to create private wikis.
We implement a form in the wikis views, which will only be shown to admin and premium users, through the help of Pundit.

```
<% if current_user.admin? || current_user.premium? %>
  <div class="form-group">
    <%= f.label :private, class: 'checkbox' do %>
      <%= f.check_box :private %> Private wiki
    <% end %>
  </div>
<% end %>
```

We want our premium users to be able to add and remove collaborators to their privated wikis. In order to accomplish this user story, we developed the create and destroy functions for wiki collaborators in the Collaborators Controller. The create function is connected to the new wiki view. In the new wiki view, the premium user would have an option to add collaborators using the create function. We also updated the wiki policy so that we can allow only certain users the ability to create and destroy collaborators.

```
attr_reader :user, :scope

     def initialize(user, scope)
       @user = user
       @scope = scope
     end

     def resolve
       wikis = []
       if user.role == 'admin'
         wikis = scope.all
       elsif user.role == 'premium'
          scope.where(private: [false, nil] || wiki.owner == user || wiki.collaborators.include?(user))
       elsif user.role == 'standard'
         scope.where(private: [false, nil] || wiki.collaborators.include?(user))
       else
         scope.where(private: [false, nil])
       end
     end
   end
```

## Results

This is where I will put my heroku link.


## Conclusion

Some major programming skills that I've learned throught this project:
Authorization: Implementing user sign up and sign in actions.
Authentication: creating different user roles and determining which role can access certain functions.
Utilization of gems like Devise, Pundit, Faker, and Stripe.
