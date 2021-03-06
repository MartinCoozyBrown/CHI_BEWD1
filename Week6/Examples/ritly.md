![GeneralAssemb.ly](http://studio.generalassemb.ly/GA_Slide_Assets/Exercise_icon_md.png)

Time to review. You now have all the necessary knowledge to build a small Rails app. Let's build!

#Ritly
####Time: 60 min

We are going to build an app similar to [Bitly](https://bitly.com), called Ritly. The challenge is going to be understanding the flow of control in a Rails app.

You can get the starter code from here: [https://github.com/billpatrianakos/Ritly](https://github.com/billpatrianakos/Ritly)

Here is a brief overview of the app.

*   Visitors to Ritly will be able to request a randomly generated code for their URL link and save it to the database.
* Visitors to Ritly can go to ```localhost:3000/<CODE>```, where ```<CODE>``` is a randomly generated code, and the application will redirect them to the  matched link in the database.
* Visitors to Ritly can go to ```localhost:3000/<CODE>/preview```, and the app will preview the matching URL link from the database.


###Task Instructions

We are going to challenge your understanding of a Rails app. With the demo, description above and hints below build Ritly.

Here are a few hints.

####The URLs Table

|id|link |hash code|created at|updated at|
|:---|:----|:--------|:---------|:---------|
|1|http://www.generalassemb.ly|516396|Wed, 19 Jun 2013 21:23:30 UTC +00:00|Wed, 19 Jun 2013 21:23:30 UTC +00:00|
|2|http://www.google.com|234687|Wed, 19 Jun 2013 21:25:32 UTC +00:00|Wed, 19 Jun 2013 21:25:32 UTC +00:00|
|3|http://www.bustedtees.com|093674|Wed, 19 Jun 2013 21:23:30 UTC +00:00|Wed, 19 Jun 2013 21:23:30 UTC +00:00|


####The routes.rb file

```ruby
    Ritly::Application.routes.draw do
      root "home#index"
      resources :urls #TODO: restrict this to just :create, :new and :show

      get '/:code', to: 'urls#redirectors'
      get '/:code/preview', to: 'urls#preview'
    end
```

####The Views

* show.html.erb
  * Visitors are redirected to the show page after they request a randomly generated code for their URL link.
  * Displays the random code that was generated: "Your code is: random_code" Go to localhost:3000/random_code to visit your URL.


####Generating a Random Number or Hash

* To generate a random number in Ruby: ```rand(10000)```.
* __Bonus__ Use SecureRandom.urlsafe_base64(8) to generate a random hash code.

Remember, Google is your friend!
