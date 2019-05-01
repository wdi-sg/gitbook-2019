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

### Pairing Exercise
Add SASS and Javascript to one of your rails apps.

#### further
Add the official bootstrap gem to your app: (https://github.com/twbs/bootstrap-rubygem)[https://github.com/twbs/bootstrap-rubygem]


## Additional Reading

* [Rails Guides - Assets Pipeline](http://guides.rubyonrails.org/asset_pipeline.html)
* [Rails API - Asset Tag Helpers](http://api.rubyonrails.org/classes/ActionView/Helpers/AssetTagHelper.html)
* [SASS documentation](http://sass-lang.com/documentation/file.SASS_REFERENCE.html)
* [gon gem](https://github.com/gazay/gon)
