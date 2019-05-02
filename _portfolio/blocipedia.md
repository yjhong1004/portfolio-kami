---
layout: post
title: Blocipedia
thumbnail-path: "img/blocipedia.png"
short-description: Build a production quality SaaS app that allows users to create their own wikis.

---

{:.center}
![]({{ site.baseurl }}/img/blocipedia.png)

## Explanation

My goal for this project was to learn how to recreate a web application similar to Wikipedia, using Ruby on Rails.



## Problem

Complete these user stories:

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

1. As a user, I want to sign up for a free account by providing a username, password and email
2. As a user, I want to sign in and out of Blocipedia

The first thing I did was to create a basic user scheme for a Ruby on Rails application. This was done by implementing user authentication. I would be able to give the users of a Ruby on Rails application the ability to sign up for the application using the Devise gem. Although I can utilize CRUD to create users and to authenticate user, the Devise gem worked amazingly well in doing all of the heavy work for me.


3. As a user with a standard account, I want to create, read, update, and delete public wikis:
In order to complete this user story, I created a Wiki controller and its accompanying views.

```
class WikisController < ApplicationController
  def index
    @wikis = policy_scope(Wiki)
  end
  ...
```
4. As a developer, I want to offer three user roles: admin, standard, or premium

There is a clear distinction between authorization and authentication. The latter was completed in the first user story. We'll now focus on the the former. Authorization allows certain classes of users to be able to do certain actions. We accomplish this using the Pundit gem. Before we fully implement authorization, we want to create these classes of users. We first add a standard user role in the user model.

```
after_initialize :init
  def init
    self.role ||= 0.0
  end
  enum role: [:standard, :admin, :premium]
```
Once we implement the roles for users, we utilize the pundit gem to authorize all users access to the index view (collection of wikis). Standard signed in users to new/create/edit/update actions. We also allow wiki owners to delete their own wikis.

5. As a developer, I want to seed the development database automatically with users and wikis

This user story allows us to utilize the Faker gem to generate fake data for users and wikis.

6. As a user, I want to upgrade my account from a free to a paid plan

This is where we are introduced to the premium user role. We first determined a user flow. An example of a user flow for this app:

```
1. The user signs up for a free plan.
2. The user upgrades their free plan and is prompted to pay with Stripe.
3. The user's role is changed from standard to premium.
4. The user is able to create private wikis.
```

We use Stripe to charge users to change their role from standard to premium. If we have the ability to upgrade a user's role to premium, we should also be able to downgrade a user back to the standard role. This is best included in the User model.

```
def downgrade
    self.wikis.update_all(private: false )
    self.update_attribute(:role, 'standard')
end
```

7. As a premium user, I want to create private wikis:

In order to accomplish this user story, I need a way to change premium users' wikis to private. We implement a form in the wikis views, which will only be shown to admin and premium users.

```
<% if current_user.admin? || current_user.premium? %>
  <div class="form-group">
    <%= f.label :private, class: 'checkbox' do %>
      <%= f.check_box :private %> Private wiki
    <% end %>
  </div>
<% end %>
```

In my wiki policy, I would authorize

```
def resolve
      if user.nil? || user.standard?
        scope.where(private: [false, nil])
      elsif user.admin? || user.premium?
        scope.where(private: [false, nil, true])
      end
    end
  end
```

8. As a user, I want to edit wikis using Markdown syntax:

I installed the redcarpet gem to utilize the Markdown syntax. I then implement it in the wiki show view.

9. As a premium user, I want to add and remove collaborators for my private wikis:

I developed the create and destroy functions for wiki collaborators in the Collaborators Controller. The create function is connected to the new wiki view. In the new wiki view, the premium user would have an option to add collaborators using the create function.

We also updated the wiki policy so that we can allow only certain users the ability to create and destroy collaborators.

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
