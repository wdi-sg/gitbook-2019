# Asset Pipeline and Front-end in Rails

## Objectives

* Incorporate JavaScript, CSS, SCSS, images, and other static files into a Rails application
* Understand the Asset Pipeline
* Utilize helper methods/tags for including static resources
* Use `gon` to pass data to the front-end

We can work with JavaScript, CSS, and images in Rails just like we did in our front-end only projects. Rails uses the concept of an Asset Pipeline to handle pre-processing and loading of static assets. The "Rails way" is to put all of your assets (JavaScript, CSS/SASS, images) in the `assets` folder. Just do it!

## JavaScript

To load JavaScript files in Rails we simply create `.js` files in the `app/assets/javascripts` directory and Rails will automatically load them in the head of the page using `<script>` tags.

To adjust the load order, we can add the scripts along with the `//=` lines at the bottom of `application.js`

#### application.js

application.js is used to load other JavaScript files and allows us to change the load order of the files. You *CAN* put JavaScript code directly in this file. But it's best practice to avoid this and use separate files as before.

At the bottom of `application.js` there are a few lines that look like comments and start with `//=` these are used to specify which files to load and in what order. The last line (`//= require_tree .`) loads all of the files in the `javascripts` directory that aren't loaded explicitly above.

For example, if we had a file called `importantScript.js` in our `javascripts` directory and we needed it to be loaded first we could simply do something like this...

```js
//= require 'importantScript.js'
//= require jquery_ujs
//= require turbolinks
//= require_tree .
```

#### Blame Turbolinks
Rails includes a package called Turbolinks, which provides some optimization for our sites by minimising the amount of the page that is redrawn between requests. It's clever but can cause issues if we are expecting js/jquery page ready events to fire.

##Stylesheets

Rails uses SASS, which is a preprocessor for CSS that allows us to use some additional features that standard CSS doesn't support. These files end with the `.scss` file extension and are processed on the server (back-end) before they are sent to the user/browser as plain CSS.

Learn SASS here: [SASS](../additional-topics/sass/readme.md)

Just like with JavaScript, Rails will auto-load any CSS or SCSS file that are in `app/assets/stylesheets`.

Also, similar to JavaScript we can adjust the load order by editing the bottom of `application.css`, and again we should avoid putting CSS directly in this file.

##Images

We can load images by placing them in `app/assets/images` and using the rails `image_tag` helper to load them for us.

####Images in views (erb)

If we have a file `app/assets/images/pic.jpg` we can display it in an erb file like this:

```html
<%= image_tag 'pic.jpg' %>
```

We can also get a string of the image URL/path by calling `image_url` or `image_path`.

####Images in CSS (using SCSS)

We also have access to a `image_url` helper method in `scss` files. It will be used in place of the standard css `url('/path/to/image.jpg')` format.

```css
.some-class {
  background-image: asset-url('pic.jpg');
}
```

**NOTE:** make sure the file is named `scss` and not just `css`. The `css` files are served to the browser as-is (no pre-processing), but `scss` are run through the sass pre-proccessor first which will run the `image_url` method and insert the correct image path.


## Additional Reading

* [Rails Guides - Assets Pipeline](http://guides.rubyonrails.org/asset_pipeline.html)
* [Rails API - Asset Tag Helpers](http://api.rubyonrails.org/classes/ActionView/Helpers/AssetTagHelper.html)
* [SASS documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)
* [gon gem](https://github.com/gazay/gon)


### Pairing Exercise
Use the (user-songs)[] rails app, or use one of yours.

### Part 1: SASS setup

Make sure the file has `.scss` extension (or `.sass` for Sass syntax). If you have just generated a new Rails app,
it may come with a `.css` file instead. If this file exists, it will be served instead of Sass, so rename it:

```console
mv app/assets/stylesheets/application.css app/assets/stylesheets/application.scss
```




Create a file and put some SASS code in it

```bash
touch app/assets/stylesheets/stuff.scss
```

```css
body{
  background-color:pink;

  p{
    background-color:blue;
  }
}
```

Import it in `application.scss`

```
@import 'stuff'
```

> Warning: you can't use the file extention of the sass file in your import
> Warning: the order of the import statements matter.


### Asset Pipeline
Inside of your config file: `config/environments/development.rb`:

Check out the asset pipeline options:
Switch each of these and see how your assets change.

When debug mode is off, Sprockets concatenates and runs the necessary preprocessors on all files. With debug mode turned off the manifest above would generate instead:
```
config.assets.debug = false
```

When this option is true, digests will be generated for asset URLs. Put this option in to see what happens.
```
config.assets.digest = false
```

See what assets precompile does:

Before you run `precompile` you have to have the `yarn` library installed.

```bash
npm install -g yarn
```

```
rails assets:precompile
```

Look in the place where rails *actually* serves the compiled assets from:
```
ls -la public/assets
```



##### Static Assets
Rails is smart enough to put in the proper urls when it's a SASS file.

Choose an image file. Name it `pic.jpg` and put it in `app/assets/images`

Output an `image_url` in the view template to see where it goes.
```
<%= image_url 'pic.jpg' %>
```

Make an image tag with the url
```
<img src="<%= image_url 'pic.jpg' %>"/>
```

### Install bootstrap
According to the instructions:

[https://github.com/twbs/bootstrap-rubygem#a-ruby-on-rails](https://github.com/twbs/bootstrap-rubygem#a-ruby-on-rails)


Add `bootstrap` to your Gemfile:

```ruby
gem 'bootstrap', '~> 4.1.0'
```

```
bundle install
```

Make some changes in `app/assets/stylesheets/application.css`:

Take out all require statements. ( they look like comments, but they are actually looked at by the pipeline system)

Import Bootstrap styles:

```scss
// Custom bootstrap variables must be set or imported *before* bootstrap.
@import "bootstrap";
```

### bootstrap javascript & dependencies

Bootstrap JavaScript depends on jQuery.
Add the `jquery-rails` gem to your Gemfile:

```ruby
gem 'jquery-rails'
```

Bootstrap tooltips and popovers depend on [popper.js] for positioning.
The `bootstrap` gem already depends on the
[popper_js](https://github.com/glebm/popper_js-rubygem) gem.

Add Bootstrap dependencies and Bootstrap to your `application.js`:

```js
//= require jquery3
//= require popper
//= require bootstrap-sprockets
```

### Style Our App
Use SASS to style our pages. Gitbook page here:[https://wdi-sg.github.io/gitbook-2018/06-ruby-rails/additional-topics/sass/readme.html](https://wdi-sg.github.io/gitbook-2018/06-ruby-rails/additional-topics/sass/readme.html)

The available variables can be found [here](assets/stylesheets/bootstrap/_variables.scss).

### Bootstrapify the song list.

app/views/songs/index.html.erb
```
<div class="container">
  <div class="row">
    <table class="table table-striped">
      <thead>
        <tr>
          <th scope="col">#</th>
          <th scope="col">title</th>
          <th scope="col">created</th>
        </tr>
      </thead>
      <tbody>
      <% @songs.each do |song| %>
        <tr>
          <td><%= song.id %></td>
          <td class="song-title"><%= song.title %></td>
          <td><%= song.created_at.strftime('%d.%m.%Y') %></td>
        </tr>
      <% end %>
      </tbody>
    </table>
  </div>
</div>
```

#### New Form:
Let's make some changes to the new form to conform with the bootstrap form. [https://getbootstrap.com/docs/4.0/components/forms/](https://getbootstrap.com/docs/4.0/components/forms/)

You shouldn't need any additional styles for this page if your markup and classes use bootstrap.

#### Index Page
Make the top part of our index page a bootstrap jumbotron: [https://getbootstrap.com/docs/4.0/components/jumbotron/](https://getbootstrap.com/docs/4.0/components/jumbotron/)

Make sure it has a `container` and `row` bootstrap class `div` around it. (like the table markup below)

In `app/assets/stylesheets` make a new stylesheet `song-index.scss` and import it in `application.scss`.

In the new SASS file set a background image for the jumbotron. SASS and Rails are smart enough to put figure out that you want an asset image in your css:
```
background-image: asset-url('pic.jpg');
```

You can also use one from [unsplash.it](https://unsplash.it)

### Javascript in rails

Add functionality that will take all of the items in your index list and arrange them- but *on the front end* - using DOM manipulation.

Add a button
```
<button id="submit" type="button" class="btn">sort</button>
```

Add the listener:
```
var doSort = function(){
  alert("hello!");
};

window.onload = function(){
  $('#submit').click(doSort);
};
```

The function `doSort` should use DOM manipulation to take all the items out and put them back in sorted.
