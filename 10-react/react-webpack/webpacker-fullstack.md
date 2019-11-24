# react / rails / webpacker

Install devise:

```
bundle add devise
```

```
rails generate devise:install
rails generate devise user
rails g devise:views
```

Scaffold the post:
```
rails generate scaffold Post title:string content:text user:belongs_to
```

Lock down the entire controller
```
before_action :authenticate_user!
```

```
rails db:migrate
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
user1 = User.new({email: 'kenny@testing.com', password: 'password', password_confirmation: 'password'})
user1.confirm!
user1.save

user2 = User.new({email: 'cheekean@testing.com', password: 'password', password_confirmation: 'password'})
user2.confirm!
user2.save

user3 = User.new({email: 'susan@testing.com', password: 'password', password_confirmation: 'password'})
user3.confirm!
user3.save

user4 = User.new({email: 'john@testing.com', password: 'password', password_confirmation: 'password'})
user4.confirm!
user4.save

users = [user1,user2,user3,user4]

users.each do |user|
  20.times do |n|
    user.post.create({title: FFaker::Lorem.words ,content: FFaker::Lorem.paragraph})
  end
end
```

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
<button onClick={()=>{ this.getPosts() }}
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

