# webpacker

Rails was not concieved for an asset pipeline any more complex than it already is. What if you have to include other (npm) library dependencies before you compile the assets? What about sass that is declared within the component?

We need another system to run webpack on top of rails that could integrate with the asset pipeline.

From the official webpacker documentation: [https://github.com/rails/webpacker](https://github.com/rails/webpacker)


#### Generate a normal rails app, but with the required webpacker files:

Install the libraries you need:
```
brew install yarn
```

Create and initialize the app: (this one includes all the models and views)
```
rails _6.0.2_ new react-webpacker-test --webpack=react -d postgresql --skip-turbolinks --skip--coffee

cd react-webpacker-test
rails db:create
```

Check out your app:
```
rails s
```

You should have a working rails CRUD app à la unit 3.

#### Setting up the react app:

Now check out the app directory structure:

You should have a set of files in `app/javascript`
```yml
app/javascript:
  └── packs:
      # only webpack entry files here
      └── application.js
      └── hello_react.jsx
```

Create the root controller and view:
```
rails g controller onepage index
```

Set the root route in `config/routes.rb` to be the controller you just created:
```
get '/react' => 'onepage#react'
```

Create the script tag for them in your view file `app/views/onepage/index.html.erb`:

The argument to javascript_pack_tag corresponds to the file in the packs folder.

```
<%= javascript_pack_tag 'hello_react' %>
```

If you are using react styles you can do this:
```
<%= stylesheet_pack_tag 'hello_react' %>
```

Your basic react setup is done.

Run the app to see it work:

Open up *two* terminals:

1.
```
./bin/webpack-dev-server
```

2.
```
rails server
```

#### Other assets in the rails asset pipeline:
Refer to this page of the webpacker docs: [https://github.com/rails/webpacker/blob/master/docs/assets.md](https://github.com/rails/webpacker/blob/master/docs/assets.md)

#### Production Build
```
./bin/webpack
```

See where these files are being built to:
```
ls -la public/packs
```

### Pairing Exercise
Create and run a react app inside a rails app, as above.

##### Standard React Setup:

Create a components directory

```bash
mkdir app/javascript/components
```

Create a new component called `app` in the `components` directory

Create a new component called `form` in the `components` directory

Use `form` component in `app`

#### Further
Copy your previous assignment react code into the rails app.

#### Further
Create a second react app in this rails app.

