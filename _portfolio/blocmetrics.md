---
layout: post
title: BlocMetrics
thumbnail-path: "img/blocflix.png"
short-description: BlocMetrics is program that tracks user actions on a website, similar to Google Analytics.

---

{:.center}
![]({{ site.baseurl }}/img/blocflix.png)

## Explanation

My goals for this project are to create a client-side JavaScript snippet that allows a user to track events on their website.
This project is essentially a server-side API that captures and saves those events to a database.


## Problem

Complete these user stories:

1. As a user, I want to sign up for a free account by providing a name, password, and email.
2. As a user, I want to sign in and out of Blocmetrics.
3. As a user, I want to register an application with Blocmetrics for tracking.
4. As a user, I want events associated with registered applications.
5. As a developer, I want to receive incoming events in an API controller.
6. As a user, I want to use JavaScript to capture client-side events in my application.
7. As a user, I want to see a graph of events for each registered application.


## Solution

1. As a user, I want to sign up for a free account by providing a name, password, and email.
2. As a user, I want to sign in and out of Blocmetrics.

We utilized the devise gem for authentication. This is an easy way to allow users to sign up for accounts and to receive email confirmations. Refer to the devise gem information linked below.

https://github.com/plataformatec/devise

We need to always test our code. The navigation should change to indicate a signed in/signed out user.

3. As a user, I want to register an application with Blocmetrics for tracking.

Blocmetrics should track events from multiple applications. Therefore, we need to register each application with a unique attribute, or its URL, so that when Blocmetrics receives an event, it knows which application to associate the event.

We have the code for the registered applications controller with the appropriate CRUD actions.

```
def create
    @registered_application = RegisteredApplication.new(app_params)
    @registered_application.user = current_user
    if @registered_application.save
      flash[:notice] = "Application was saved into the system!"
      redirect_to @registered_application
    else
      flash[:notice] = "There was an error!"
      render :new
    end
end
```

```
def update
    @registered_application = RegisteredApplication.find(params[:id])
    @registered_application.name = params[:registered_application][:name]
    @registered_application.url = params[:registered_application][:url]
    if @registered_application.save
      flash[:notice] = "Application was saved into the system!"
      redirect_to @registered_application
    else
      flash[:notice] = "There was an error!"
      render :edit
    end
  end
```

```
def destroy
   @registered_application = RegisteredApplication.find(params[:id])
   if @registered_application.destroy
     flash[:notice] = "\"#{@registered_application.name}\" was deleted successfully."
      redirect_to registered_applications_path
    else
      flash.now[:alert] = "There was an error deleting the app."
      render :show
    end
 end
```

We need to make sure that our CRUD actions are accessed in our views. Our create action and views should be able to create a new registration associated with a user. Our delete action should de-register and destroy the application registration.

As always, we need to be able to test our code. And ask several questions:

Are you able to register multiple applications?
Are the registered applications displayed after creation?
Are you able to de-register and then re-register an application by the same name?
Are you able to view an index of registered applications?

4. As a user, I want events associated with registered applications.
When Blocmetrics receives an event, it should store the name of the event. This will be done through the event model that is associated with a registered application with an event name attribute.

At this point of the project, I seeded the database to test my application with some fake data. I used the Faker gem to simulate tracked events.

Eventually, we will display graphs of different events, but up to this point of the project, we want to display the name and count of each type of event associated with the application.

```
<h1><%= @registered_application.name %></h1>
<p><%=@registered_application.url %></p>
<% @events.each do |key, value| %>
  <h6><%= key %>: <%= value.size %></h6>
<% end %>
<p><%= @events.count %> events exist for this app</p>
<div class="col-md-4">
  <%= link_to "Edit", edit_registered_application_path(@registered_application), class: 'btn btn-success' %>

```

5. As a developer, I want to receive incoming events in an API controller.

At this point of the project, we want to work with real time data. In order for Blocmetrics to receive incoming events from registered applications, we will need an API controller and routes.

Our events controller needs to match our API route. In order to find the registered application that matches the source of the API request, we use request.env['HTTP_ORIGIN']. If we find an API request from an unregistered application, we would get a return of nil. We need to return an error to the requestor if this happens, using:

```
render json: "Unregistered application", status: :unprocessable_entity.
```
If the event saves successfully in API::EventsController#create, we want to return a success message:

```
render json: @event, status: :created
```

If it doesn;t, we want to return a failure message:

```
render json: {errors: @event.errors}, status: :unprocessable_entity
```
The full create code is shown below:

```
  def create
    registered_application = RegisteredApplication.find_by(url: request.env['HTTP_ORIGIN'])
    if registered_application
      @event = registered_application.events.new(event_params)
      if @event.save
        render json: @event, status: :created
      else
        render json: {errors: @event.errors}, status: :unprocessable_entity
      end
    else
      render json: "Unregistered application", status: :unprocessable_entity
    end
  end

```
We want to define a private event_params method for EventsController. :name is the only attribute that needs to be permitted.

```
private
  def event_params
    params.require(:event).permit(:name)
  end
```

CORS
Client side Javascript code will need to send an AJAX request to the Blocmetrics API so that we can store events. Due to security risks, browsers normally don't allow cross-origin requests. This is where cross-origin resource sharing comes in (CORS). CORS works by making preliminary request to the target server, asking if the cross-domain request will be permitted. This uses HTTP OPTION verb, which is not part of Rails' restful routes. An OPTION request precedes a GET or POST request and checks whether the route accepts a cross-origin request.

This is how our routes should look like:

```
Rails.application.routes.draw do

  namespace :api, defaults: { format: :json } do
    match '/events', to: 'events#preflight', via: [:options]
    resources :events, only: [:create]
  end
  resources :registered_applications
```

The browser expects the OPTIONS request to return a 200. Our preflight action doesn't need to render anything apart from a 200 status code.

```
def preflight
    head 200
end
```
We need to set CROS response headers so our controller actions will allow POST requests across domains.

```
class API::EventsController < ApplicationController
  before_filter :set_access_control_headers
  def set_access_control_headers
    headers['Access-Control-Allow-Origin'] = '*'
    headers['Access-Control-Allow-Methods'] = 'POST, GET, OPTIONS'
    headers['Access-Control-Allow-Headers'] = 'Content-Type'
  end
  ...
end
```
Lastly, we want to test our API using curl.
In our terminal, we input
```
$ curl -v -H "Accept: application/json" -H "Origin: http://registered_application.com" -H "Content-Type: application/json" -X POST -d '{"name":"foobar"}'  http://localhost:3000/api/events
```
We need to confirm that a new event was created with the event name "foobar" and successfully associated with the registered application. We should also confirm with another curl request, that from an unregistered URL, a new event is not created.

6. As a user, I want to use JavaScript to capture client-side events in my application.

Blocmetrics should be able to track events using JavaScript snippets. The only function our snippet needs to support is
```
blocmetrics.report('event name here');
```
The function above makes an AJAX request to the server-side API to create the event on our server.

```
var blocmetrics = {};
  blocmetrics.report = function(eventName){
    var event = {event: { name: eventName }};
    var request = new XMLHttpRequest();
    request.open("POST", "http://localhost:3000/api/events", true);
    request.setRequestHeader('Content-Type', 'application/json');
    request.send(JSON.stringify(event));
  };
console.log('blocmetrics ready')
```

7. As a user, I want to see a graph of events for each registered application.
We added a JavaScript charting library, Chartkick library into our Gemfile.
Chartkick can generate an events pie chart using this line of code:
```
<%= pie_chart @registered_application.events.group(:name).count %>
```
In order to create a line chart of events over time, utilize the Groupdate gem. We add this code in our show view for registered applications.

```
<%= line_chart @registered_application.events.group_by_day(:created_at).count %>
```

We need to make confirm that a pie chart of all events and a line graph of all events over time are displayed on our show page of a registered application.

## Results



## Conclusion
