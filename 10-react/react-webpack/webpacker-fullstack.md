# react / rails / webpacker



#### Generate a normal rails app, but with the required webpacker files:

Install the libraries you need:
```
brew install yarn
```

Create and initialize the app: (this one includes all the models and views)
```
rails _6.0.2_ new react-blog --webpack=react -d postgresql --skip-turbolinks --skip--coffee

cd react-blog
rails db:create
```

Check out your app:
```
rails s
```

You should have a working rails CRUD app à la unit 3.

### generate the rest of the app:


#### Install devise:

```
bundle add devise
```

```
rails generate devise:install
rails generate devise user
```

```
rails db:migrate
```

```
rails g devise:views
```

#### Scaffold the post:
```
rails generate scaffold Post title:string content:text user:belongs_to
```

```
rails db:migrate
```

Add the association to the user model:
```
has_many :post
```

Check out your app:
```
rails s
```

You should have a working rails CRUD app à la unit 3:

Go to:
[http://localhost:3000/users/sign_in](http://localhost:3000/users/sign_in)
[http://localhost:3000/posts](http://localhost:3000/posts)

Create a post:
[http://localhost:3000/posts/new](http://localhost:3000/posts/new)


#### Seed some more data:
```
bundle add ffaker
```

In seeds.rb
```
user1 = User.new({email: FFaker::Internet.email, password: 'password', password_confirmation: 'password'})
user1.save

user2 = User.new({email: FFaker::Internet.email, password: 'password', password_confirmation: 'password'})
user2.save

user3 = User.new({email: FFaker::Internet.email, password: 'password', password_confirmation: 'password'})
user3.save

user4 = User.new({email: FFaker::Internet.email, password: 'password', password_confirmation: 'password'})
user4.save

users = [user1,user2,user3,user4]

users.each do |user|
  20.times do |n|
    user.post.create({title: FFaker::Lorem.words ,content: FFaker::Lorem.paragraph})
  end
end
```

## Set up the rails react app

Create the root controller and view:
```
rails g controller onepage index
```

Create the script tag for them in your view file `app/views/onepage/index.html.erb`:

The argument to javascript_pack_tag corresponds to the file in the packs folder.

```
<%= javascript_pack_tag 'hello_react' %>
```

### Logged in React
We want to limit this react page to only users who are logged in.

Lock down the entire controller:

```
before_action :authenticate_user!
```

(You can do this to the posts controller as well)

### AJAX from React

Run the react app to see it work:

Open up *two* terminals:

1.
```
./bin/webpack-dev-server
```

2.
```
rails server
```

We'll be using the `axios` library to make AJAX requests.

```
yarn add axios
```

Add axios at the top of your component's file:
```
import axios from 'axios';
```

Add a button to your component:

```
<button onClick={()=>{ this.getPosts() }}>
  Click to See Posts
</button>
```

Write `getPosts` method *inside* your component:

```
getPosts(){

  const url = '/posts.json';

  axios.get(url)
    .then((response) => {

      const data = response.data

      this.setState({ posts: data })

    }).catch((error)=>{
      console.log(error);
    })
}
```

Render the posts in react:

Create a `posts` variable that contains the array of posts element so you can render it:

```
// console log the posts, this should be an array of objects
const posts = this.state.posts.map((post, index)=>{
  return (<div>
    <p>{post.title}</p>
    <p>{post.content}</p>
  </div>);
});
```

### Extra

Add the user model to the posts:

```
respond_to do |format|
  format.json {
      render :json => @posts,
      include: :user
  }

  format.html
end
```

### Pairing Exercise

Repeat the above.

#### Further

Add code so that the posts shown on the react page are only those created by the currently logged in user.

#### Further

Add code so that the user can create a post in the DB.

Look up the documentation for POST in axios library: https://github.com/axios/axios

Don't re-request the list of posts from the rails app. Instead, send back the newly-created post in the response to the POST request. When your react app recieves the request, put that post into the `this.state.posts` array.

#### Further

Add validation in the rails app *AND* the react app for a post.

- the title must be more than 3 characters
- the content must me more than 10 characters

#### Further
Surfacce the *rails* validation error messages in the react app.

#### Further
Add edit

#### Further
Add `likes`. A user can like a post. Add a table to the database and the appropriate controllers. Add the AJAX request to the react app.

#### Further
Add `moment`: `yarn add moment` Use moment to format the dates of the posts.

#### Further
Change the seed file so that the dates of the posts are further apart. Make more posts (100-200)

Add a react library that lets the user picka range of dates.

Google `react calendar picker` or `react calendar range picker`.

When the user picks a date or range of dates, show posts for those dates.

