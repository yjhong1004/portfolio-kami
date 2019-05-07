---
layout: post
title: Kele
thumbnail-path: "img/blocitoff.png"
short-description: Create a Ruby Gem API client.

---

{:.center}
![]({{ site.baseurl }}/img/blocitoff.png)

## Explanation

My goal for this project is to create a Ruby Gem API client that would easily access the student endpoints of Bloc's (Bloc.io) API.

## Problem

Complete these user stories:

1. As a user, I want to initialize and authorize Kele with a Bloc username and password.
2. As a user, I want to retrieve the current user as a JSON blob.
3. As a user, I want to retrieve a list of my mentor's availability.
4. As a user, I want to retrieve roadmaps and checkpoints.
5. As a user, I want to retrieve a list of my messages, respond to an existing message, and create a new message thread.
6. As a user, I want to retrieve a list of checkpoints remaining in my current section.

## Solution

1. As a user, I want to initialize and authorize Kele with a Bloc username and password.

```
require 'httparty'
require 'json'


class Kele
  include HTTParty
  def base_uri
    'https://www.bloc.io/api/v1'
  end
  def initialize(email, password)
    @options = {
      email: email,
      password: password
    }
    response = self.class.post("#{base_uri}/sessions", @options)
    @auth_token = response['auth_token']
    if @auth_token.nil?
      puts "Sorry, invalid credentials."
    end
  end
end
```

We test out our code and should be able to retrieve and store our authentication token when we pass in valid credentials.

```
$ irb
>> require './lib/kele'
=> true
>> Kele.new("jane@gmail.com", "abc123")

```

2. As a user, I want to retrieve the current user as a JSON blob.

```
def get_me
    response = self.class.get("#{base_uri}/users/me", headers: { "authorization" => @auth_token })
    JSON.parse(response.body)
  end
```

We need to make sure that we can retrieve our own personal user data and be able to convert the data to a Ruby hash.
```
$ irb
>> require './lib/kele'
=> true
>> kele_client = Kele.new("jane@gmail.com", "abc123")
>> kele_client.get_me
```
The results of the test above should show a hash of your personal data.

3. As a user, I want to retrieve a list of my mentor's availability.

In this user story, we want to access a list of a mentor's available time slots for our user. We first define the get_mentor_availability method.

```
def get_mentor_availability(mentor_id)
    response = self.class.get("#{base_uri}/mentors/#{mentor_id}/student_availability", headers: {"authorization" => @auth_token} )
    JSON.parse(response.body)
end
```

We need to test this method to ensure that we retrieve a list of our mentor's available time slots and to convert the time slots to a Ruby array.

```
$ irb
>> require './lib/kele'
=> true
>> kele_client = Kele.new("jane@gmail.com", "abc123")
>> mentor_id = 99
>> kele_client.get_mentor_availability(mentor_id)
```

4. As a user, I want to retrieve roadmaps and checkpoints.
It's important to note here that we moved the code into a module to better organize our application. We can access this Roadmap module in our Kele class by requiring the 'lib/roadmap.rb'.

```
module Roadmap
  def get_roadmap(chain_id)
    response = self.class.get("#{base_uri}/roadmaps/#{chain_id}", headers: {"authorization" => @auth_token} )
    JSON.parse(response.body)
  end

  def get_checkpoint(checkpoint_id)
    response = self.class.get("#{base_uri}/checkpoints/#{checkpoint_id}", headers: {"authorization" => @auth_token})
    JSON.parse(response.body)
  end
end

```
We want to test to make sure that we can retrieve the roadmap and the checkpoints. We also want to retrieve the checkpoints' bodies and assignments.

```
$ irb
>> require './lib/kele'
=> true
>> kele_client = Kele.new("jane@gmail.com", "abc123")
>> chain_id = 99
>> kele_client.get_roadmap(chain_id)
```

```
$ irb
>> require './lib/kele'
=> true
>> kele_client = Kele.new("jane@gmail.com", "abc123")
>> checkpoint_id = 99
>> kele_client.get_checkpoint(checkpoint_id)
```

5. As a user, I want to retrieve a list of my messages, respond to an existing message, and create a new message thread.

The Bloc platform organizes all messages in message threads. So we would need to retrieve the message threads first and then return a specified page.

```
def get_messages(page_number = nil)
    if page_number == nil
      response = self.class.get("#{base_uri}/message_threads", body: {}, headers: {"authorization" => @auth_token})
    else
    response = self.class.get("#{base_uri}/message_threads", body: {
      "page": page_number
    }, headers: {"authorization" => @auth_token})
    end

    JSON.parse(response.body)
  end
```
We want to create a create_message function that will create a message in a message thread.
```
def create_message(sender, recipient_id, subject, token, stripped_text)
    response = self.class.post("#{base_uri}/messages", body: {
      "sender": sender,
      "recipient_id": recipient_id,
      "subject": subject,
      "token": string,
      "stripped-text": stripped-text
      }, headers: {"authorization" => @auth_token})
end
```
We want to test Kele in IRB to make sure we retrieve all messages for the current user and to create a new message and thread.
```
$ irb
>> require './lib/kele'
=> true
>> kele_client = Kele.new("Hannah.McExample@gmail.com", "abc123")
>> kele_client.get_messages(1)
>> kele_client.get_messages
```
kele_client.get_messages(1) will return the first page of message threads
kele_client.get_messages will return all message threads

6. As a user, I want to retrieve a list of checkpoints remaining in my current section.

```
def get_remaining_checkpoints(chain_id)
    response = self.class.get("#{base_uri}/enrollment_chains/#{chain_id}/checkpoints_remaining_in_section", headers: {"authorization" => @auth_token})
    JSON.parse(response.body)
  end
```

We want to test our code using IRB to make sure we get a list of remaining checkpoints.

```
$ irb
>> require './lib/kele'
=> true
>> kele_client = Kele.new("Hannah.McExample@gmail.com", "abc123")
>> kele_client.get_remaining_checkpoints(chain_id)

```










## Results


## Conclusion

Bacon ipsum dolor amet filet mignon meatball spare ribs fatback bacon shankle. Kielbasa andouille fatback salami, boudin bresaola pig alcatra turkey spare ribs jerky. Corned beef bresaola leberkas salami alcatra beef landjaeger venison shank bacon meatloaf beef ribs picanha. Leberkas sausage brisket porchetta shankle prosciutto chicken picanha kielbasa pig kevin t-bone turducken filet mignon jowl.
