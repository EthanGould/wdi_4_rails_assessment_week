# Week 4 Comprehensive Assessment

Fork this repository, update this file to include your answers, and submit a pull request. You may refer to any notes, past projects, or external resources you want. The questions do not have to be completed in order.

* The routes for the `Photo` resource should be nested under the `User` resource. What line should I put in `config/routes.rb` to create a complete set of nested RESTful routes for these resources?

resources :user do
  resources :photo
end

* A `User` will have many `Articles`. I need to create a migration for the articles table that has a title, body and something to link it to the User that owns it. What should I run on the command line to get started?

rails g migration CreateArticles title body user:references

* When do I use `has_many` vs `has_many :through`?

has_many is for a 'one-to-many' relationship: for comments on picture you would say 'a user has_many comments'
has_many :through represents a 'many-to-many' relationship: for subscribers and magazines, they could be related through a 'subcriptions' table that shows what users are subscribed to which magazines. This relationship is necessary because a user may have a subscrition to more that one magazine.

* How can I I iterate through all of the articles associated with the current user? Write the code that would make this happen.

@user = current_user

<ul>
  <% @user.articles.each do |article| %>
    <li><%= article.content %></li>
  <% end %>
</ul>

* How can I create a new article associated with a user who has_many articles?

you would specify in the article contoroller that it 'belongs_to :user'

* What method does Devise give us that represents a user who is logged in?

Devise provides the method 'current_user' that represents the user who is logged in.

* What command runs my migrations on Heroku?

heroku run rake db:migrate

* What command will show the logs on Heroku?

heroku logs

* Describe the purpose of Heroku

Heroku is designed to easily deploy web apps. It provides a server for your app which allows it to be accessible to anyone from a url.

* Describe when you would use polymorphic relationships

A polymorphic relationship is used when something 'belongs_to' multiple things. An example of this would be when you want to have a voting feature on comments AND articles. A vote can belong to the comment and the article. Both the comments and the articles are said to be 'voteable'.

