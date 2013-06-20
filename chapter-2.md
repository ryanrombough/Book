# Chapter Two: Layouts and Templates

When a user comes to our site for the first time, we want to greet them with a welcome page where they can sign up for our site. In the this section we are going to create a welcome route and serve up our welcome page via using a template. To do this we are going to install a templating engine called handlebars. Template engines allow us to easily render dynamic content in our HTML files. Handlebars is a popular JavaScript templating engine and is quite widely used for node development. Let's start by adding it to our package.json file.

```javascript
{
  "name": "twitterclone",
  "description": "Null to Node Twitter Clone App",
  "version": "0.0.1",
  "dependencies": {
    "express": "3.x",
    "express3-handlebars": "0.4.x"
  }
}
```

Make sure to add a commas at the end of each dependecy EXCEPT for the last one or you will run into trouble. Now let's run npm install in our root directory so that it will install handlebars.

```bash
$ npm install
```

Now in app.js, let's import handlebars.

```javascript
var express = require('express');
var app = express();
var routes = require('./routes');
var hbs = require('express3-handlebars');

...
```

And we need to tell our app to set handlebars as our templating engine.

```javascript
// Set handlebars as the default tempating engine
// and use main.handlebars as our default layout.
app.engine('handlebars', hbs({defaultLayout: 'main'}));
app.set('view engine', 'handlebars');
```

For reference, your appl.js file should look something like this now.

```javascript
var express = require('express');
var app = express();
var routes = require('./routes');
var hbs = require('express3-handlebars');

// Set handlebars as the default tempating engine
// and use main.handlebars as our default layout.
app.engine('handlebars', hbs({defaultLayout: 'main'}));
app.set('view engine', 'handlebars');

app.get('/', routes.index);

app.listen(3000);
console.log('App running on port 3000');
```

Now, since we are telling our app to use a layout file called main, we need to create it. Create a directory at the same level as app.js called views. Within that directory, create another directory called layouts. This will be where we keep all of our handlebars templates and layouts.

A layout is an html file that contains the structure of our site, it contains all of the content in our site that will persist from page to page, that way we don't have to write the same html files over and over. This is a really important concept to understand because it saves a lot of time down the road. If we want to change something with the layout of our site, we only have to change it in our layout file, instead of tediously updating every html file by hand and making mistakes along the way.

So let's create a really basic layout. Inside the layout directory let's create a file called main.handlebars and fill it with some basic HTML content.

```html
<!doctype html>
<html>
<head>
  <title>Twitter Clone</title>
</head>
<body>
  {{{ body }}}
</body>
</html>
```

Notice, that we have an odd line containing `{{{ body }}}`. This is the handlebars way of declaring that this is where we want the content of our template to be rendered. When we create a template, all of the content we put inside that template will be rendered where `{{{ body }}}` is in our layout. Very handy.

Now let's get to that template content. In our views directory let's create a file called welcome.handlebars and add a simple bit of HTML content.

```html
<h1>{{ title }}</h1>
<p>Glad you could make it!</p>
```

Let's restart our app and see what our welcome page looks like now. Not too exciting, but that is about to change. We're going to make our layout a bit nicer. 

For simplicity, we're going to use Twitter's <a href="http://twitter.github.io/bootstrap/" target="_blank">Bootstrap</a> to develop the front end of our website. Bootstrap is a front-end framework that comes with some really nice features. It will help us create a nice clean site that looks good without much effort.

<a href="http://twitter.github.io/bootstrap/assets/bootstrap.zip">Download</a> the Bootstrap source files. Create a directory in the root of your project named public. Unzip the files and copy the bootstrap directory into /public. We also need to tell our app that we will be serving files up from our public directory.

```javascript
...

app.engine('handlebars', hbs({defaultLayout: 'main'}));
app.set('view engine', 'handlebars');
app.use('/public', express.static('public'));

...
```

Now let's modify our main.handlebars file.

```html

```




