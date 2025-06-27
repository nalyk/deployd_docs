deployd-docs
============

documentation for the deployd platform

### Quick Start
 
Get Deployd up and running and build your first API with the [getting started guide](/docs/getting-started).

### Example Apps

[Check out the examples](/examples) to see how Deployd APIs are built.

### Guides

[Complete guides](/guides) describing the core concepts needed to build APIs with Deployd, including [accessing collections](/docs/collections), [authenticating users](/docs/users), and [using modules](/docs/using-modules).

### APIs

A [complete list of APIs](/api) available when developing a Deployd app.
<!--{
  title: 'FAQ',
  layout: 'faq'
}-->

## FAQ

### Can I host Deployd on my own server?

Yes. See the [deploying to your own server](/docs/server/your-server.md) guide for more info.

### Can I use Deployd without the JavaScript library? (e.g. for mobile apps)

Yes, you can use Deployd as a JSON API [over HTTP](/docs/collections/reference/http.md).

### Can I use Deployd with front-end frameworks like Backbone, AngularJS, Ember, Knockout, etc?

Yes, Deployd is unopinionated on the front-end and you can use any libraries that you like. For frameworks that provide their own AJAX implementation (particularly Backbone), you should probably use the [HTTP API](/docs/collections/reference/http.md) rather than dpd.js in most cases. Dpd.js is still useful for realtime and user authentication, as most of those frameworks don't provide any built-in way to do this.

If you're interested, some of Deployd.com (such as the community page and the documentation's search feature) was built with [AngularJS](http://angularjs.org/) and certain parts of the Dashboard (such as the data and property editor) were built with [Knockout](http://knockoutjs.com/). 

### Is Deployd anything like [Meteor](http://www.meteor.com/)?

Yes and no. Deployd is often compared to Meteor, since they are similar in several ways:

- They're both open source frameworks useful for building rich front-end web apps.
- They both simplify backend or API development.
- They both provide realtime functionality.

However, they are different in a few significant ways:

- Deployd creates APIs that can be used by web apps, mobile apps, and other web servers. Meteor, at the time of this writing, focuses exclusively on web development.
- Deployd provides a dashboard to let you define collections and manage data. Meteor simply exposes the MongoDB API. 
- Deployd is unopinionated on the front-end, letting you use whatever libraries you're familiar with; or no libraries at all. Meteor's realtime templating system unifies back-end and front-end development, but it dictates how you write your front-end code.

Deployd and Meteor solve many of the same problems in very different ways. You should try both frameworks to see which one better meets your needs.

In the future, the two frameworks may not be mutually exclusive. Deployd focuses on data management and business logic while Meteor focuses on front-end rendering in real time; it may be possible to integrate the two for the best of both worlds.<!--{
  title: 'Installing Deployd',
  tags: ['install']
}-->

## Installing Deployd

### Requirements

- [Nodejs needs to be installed](https://nodejs.org/en/download/)
- [MongoDB community Server should be installed](https://www.mongodb.com/download-center?jmp=docs)

### Install from NPM (recommended way)

You can install Deployd as a **node module** using `npm`. Just run the following:

    npm install deployd -g
    
The `dpd` program should be available. Try `dpd -V`.

### From Source

You can download the latest source on [github](http://github.com/deployd/deployd).

    git clone https://github.com/deployd/deployd.git
    npm install
    npm link

### Mac / Windows

The macosx installer has been deprecated, please, use the npm install.

<!--{
  title: 'What is Deployd?',
  tags: ['about', 'getting started', 'introduction'],
  order: 0,
  url: 'what-is-deployd'
}-->

## What is Deployd?

#### Deployd is a tool that makes building APIs simple by providing important ready-made functionality out of the box that meet the demands of complex applications.

### Configuration should feel like creation

In a tool like Deployd, where its purpose is to provide ready-made functionality, a lot of configuration is necessary to make sure the end result behaves the way you need it to. We didn’t want to send users to a configuration file, though. That’s not inspiring, and it’s tedious. When you’re making an app, it should feel like you’re creating something, not just selecting values.

Some frameworks bypass this by allowing you to configure the app with code. In Deployd, you might have created your API by writing a class that inherits from a Collection base class. This is better than writing configuration files, but ultimately it leads to a lot of boilerplate code. In a Convention Over Configuration environment, when you want to use the default functionality, you write an essentially empty file. When you want to override the default functionality, you write everything from scratch.

Our solution is the Dashboard. Simply put, it’s a web-based IDE for Deployd configuration files. It’s an expressive interface that lets you create your app’s API visually.

### Logic should be code

Though we didn’t want to have our users write code for the structural setup that’s better handled in a custom interface, we realized that we can’t have users add business logic in this way. Business logic is different for every app, and we can’t account for every use case.

At the same time, we can’t force business logic out of the server-side and onto the client; that would leave your app open to attack by people who figure out your API.

We decided that there’s no better way to define logic than by writing code, so we made Deployd scriptable. By writing events, or hooks into the default functionality (such as creating objects, updating them, and querying them), you can create almost any app with any rules: validation, security, query optimizations, relationships, and more.

### An API Engine

We call Deployd an **API Engine** - because we think its closest relative is actually a video game engine.

A game engine assumes that every game has levels (or maps, or rooms, or scenes) which contain game objects, which need to be rendered to the screen and interact with each other. Most engines have a level editor, where you can build up these levels without any programming or code generation; when you’re finished with your level, it’s not exactly a playable game, but it works and you can walk around in a map that you built - this is the creation over configuration principle in effect.

Similarly, Deployd assumes that every API you build has [collections of data objects](/docs/collections) which need to support CRUD operations, (Create, Read, Update, Delete). Collections are created in Deployd's version of a level editor called the dashboard.

Continuing with the analogy, a game engine also knows that your game will need things like collision detection and movement, but it doesn’t know exactly how you want to implement that, so it allows you to write scripts at strategic points like “on collision” or “on tick”.  

How a rocket is rendered to the screen is pretty consistent for any game, but what happens when that rocket hits an enemy is always different, so you write the latter behavior as a short script, and the game engine runs it at the right time. This strategy spares you from boilerplate without taking away the power and flexibility of writing custom code.

In Deployd, the low-level, redundant parts are routing and database access, so those are built into the core and you don’t have to worry about them. Business logic, which is different for every app, is scripted in [Events](/docs/collections/adding-logic.md) - hooks into the CRUD operations.

For some people, this isn’t the right approach for a final app; they prefer to have full control over the backend to tweak the performance and low-level functionality as they see fit and feel uncomfortable being limited to business logic. (Many game developers choose not to use a game engine and prefer a lower-level rendering library for virtually the same reasons) In those cases, we recommend Deployd as a prototyping tool rather than a full backend framework.

For the developers who prefer to spend their time building user interfaces, though, the scriptable engine approach is liberating. 



    
<!--{
  title: 'Your first Deployd API',
  tags: ['tutorial', 'hello world']
}-->

## Your first Deployd API

If you haven't already, [install Deployd](/docs/getting-started/installing-deployd.md).

You can create a new project by running the following commands in your terminal/command prompt (using [terminal on mac](http://smokingapples.com/software/tutorials/mac-terminal-tips/) / cmd [on windows](http://pcsupport.about.com/od/termsc/p/command-prompt.htm)).

    dpd create hello-world
    cd hello-world
    dpd -d

This will create your API, run Deployd, and open up your dashboard.

![Dashboard](/tutorials/first-api/images/new-dashboard.png)

Create a new collection by selecting it from the Resource **+** dropdown. In the "Create New Collection" prompt, enter `/things`.

Give your 'things' collection a property of `name` and press enter. *Note - Most screens in the dashboard have keyboard shortcuts.*

Add some data to the collection by opening up the data editor. Click the "Data" menu item under "Things". With the data editor open and the new row selected, you can just start typing a name. Type "foo", then hit enter, "bat", enter, "baz", enter.

Now you should have a data editor that looks like this.

![Dashboard](/tutorials/first-api/images/data-editor.png)

Click the "API" menu item to see documentation for accessing your collection. If you open up `http://localhost:2403/things` in a browser, you should see the following JSON:

![Dashboard](/tutorials/first-api/images/json.png)

Open up `http://localhost:2403` in your browser and pull up your console. Try the following:

    dpd.things.get(console.log);
    dpd.things.get({$limit: 1}, console.log);
    dpd.things.get({name: 'foo'}, console.log);

You should see something like the following:

![Dashboard](/tutorials/first-api/images/console.png)

### More Tutorials and Examples

 - [Your first App](/docs/getting-started/your-first-app.md)

### Debugging

Deployd uses [debug](https://www.npmjs.com/package/debug) to log requests and show other internal debug info. Check how to use it under [The "dpd" Command Line Tool](/docs/basics/cli.md), and [Creating a Module](/docs/developing-modules/creating-modules.md).
<!--{
	title: 'Your first app with Deployd',
	tags: ['tutorial']
}-->

## Building your first app with Deployd

In this tutorial, you'll see how to create a simple app from the ground up in Deployd. This tutorial assumes a working knowledge of jQuery. It doesn't assume any knowledge of Deployd, but it's recommended to read [Your First API with Deployd](/docs/getting-started/your-first-api.md) if you haven't already.

### Getting started

Create a new app in the command line:

	$ dpd create comments
	$ cd comments

Using your text editor of choice, replace the default `index.html` file in the `public` folder:

	<!DOCTYPE html>
	<html>
	<head>
		<title>Deployd Tutorial</title>
		<style type="text/css">
			body { font-size: 16pt; }
			.container { width: 960px; margin-left: auto; margin-right: auto; }
			form { border: #cccccc 1px solid; padding: 20px; margin-bottom: 10px; -moz-border-radius: 5px; -webkit-border-radius: 5px; border-radius: 5px; }
			.form-element { margin-bottom: 10px; }
			#refresh-btn { margin-bottom: 20px; }
			.comment { padding: 10px; margin-bottom: 10px; border-bottom: #cccccc 1px solid; }
			.comment .links { float: right; }
			.comment .links a { margin-left: 10px; }
			.comment .author { font-style: italic; }
		</style>
	</head>
	<body>
		<div class="container">
			<div id="comments">
			</div>
			<form id="comment-form">
				<div class="form-element">
					<label for="name">Name: </label>
					<input type="text" id="name" name="name" />
				</div>
				<div class="form-element">
					<textarea id="comment" name="comment" rows="5" cols="50">
					</textarea>
				</div>
				<div class="form-element">
					<button type="submit">Add New Comment</button>
				</div>
			</form>
		</div>
		
		<script src="http://code.jquery.com/jquery-latest.min.js"></script>
		<script type="text/javascript" src="script.js"></script>
	</body>
	</html>

Also add a file `script.js` and paste this code:

	$(document).ready(function() {

		$('#comment-form').submit(function() {
			//Get the data from the form
			var name = $('#name').val();
			var comment = $('#comment').val();

			//Clear the form elements
			$('#name').val('');
			$('#comment').val('');

			addComment({
				name: name,
				comment: comment
			});

			return false;
		});

		function addComment(comment) {
			$('<div class="comment">')
				.append('<div class="author">Posted by: ' + comment.name + '</div>')
				.append('<p>' + comment.comment + '</p>')
				.appendTo('#comments');
		}

	});

Run the app:

	$ dpd --open
	dpd>

The `open` command will automatically open `http://localhost:2403` in your browser.

![App Preview](/tutorials/first-app/images/comments-app-preview.png)

This basic app asks for a name and message body to post a comment. Take a moment to read the code and see how it works. 

Next, we'll add a Deployd backend to this app, so that users can interact with each other and post comments.

### Creating a backend

Open the dashboard by typing `dashboard` into the `dpd>` prompt. 

1. Create a new Collection Resource and call it `/comments`.
2. On the Properties editor, add two "string" properties called `name` and `comment`.
3. In the Data editor, add a couple of comments so you can start testing right away.

That's all you have to do in the backend for now!

### Integrating in the frontend

In `index.html`, add the following script reference in between jQuery and `script.js` (near line 37):

	<script type="text/javascript" src="/dpd.js"></script>

This will add a reference to [dpd.js](/docs/collections/accessing-collections.md), a simple library dynamically built specifically for your app's backend. Dpd.js will automatically detect what resources you have added to your app and add them to the `dpd` object. Each resource object has asynchronous functions to communicate with your Deployd app.  

In `script.js`, add a `loadComments()` function inside of `$(document).ready`:

	function loadComments() {
		dpd.comments.get(function(comments, error) { //Use dpd.js to access the API
			$('#comments').empty(); //Empty the list
			comments.forEach(function(comment) { //Loop through the result
				addComment(comment); //Add it to the DOM.
			});
		});
	}

And call it when the page loads:

	$(document).ready(function() {

		loadComments();

		//...

	});

If you run the app now, you should see the comments that you created in the Dashboard.

The `get()` function that makes this work sends an HTTP `GET` request to `/comments`, and returns an array of objects in the resource. There's nothing magical happening in dpd.js; you can use standard AJAX or HTTP requests if you prefer, or if you're unable to use dpd.js. (e.g. for mobile apps)

*Note: If you haven't used AJAX much, note that all dpd.js functions are asynchronous and don't directly return a value.*

	//Won't work: 
	var comments = dpd.comments.get(); 

This means that your JavaScript will continue to execute and respond to user input while data is loading, which will make your app feel much faster to your users.

### Saving data

Notice that any comments you add through the app's form are still gone when you refresh. Let's make the form save comments to the database. 

Delete these lines from `script.js` (near line 10, depending on where you put your `loadComments()` function):

	//Clear the form elements
	$('#name').val('');
	$('#comment').val('');

	addComment({
		name: name,
		comment: comment
	});

And replace them with: 

	dpd.comments.post({
			name: name,
			comment: comment
	}, function(comment, error) {
			if (error) return showError(error);
			
			addComment(comment);
			$('#name').val('');
			$('#comment').val('');
	});

Add a utility function at the very top of `script.js` to alert any errors we get:

	function showError(error) {
			var message = "An error occurred";
			if (error.message) {
					message = error.message;
			} else if (error.errors) {
					var errors = error.errors;
					message = "";
					Object.keys(errors).forEach(function(k) {
							message += k + ": " + errors[k] + "\n";
					});
			}
			
			alert(message);
	}

An `error` object can include either a `message` property or an `errors` object containing validation errors. 

If you load the page now, you should be able to submit a comment that appears even after you refresh.

### Conclusion

In this tutorial, you saw how to create a simple app in Deployd. In the next part (coming soon), you'll see how to secure this app with Events.

The source code for this chapter includes a few extra features. If you're feeling adventurous, try adding them yourself:

- A refresh button that reloads the comments without refreshing the page
- Edit and Delete links next to each comment. Hint: use the `put()` and `del()` functions from dpd.js.

<a class="btn btn-primary" href="https://github.com/downloads/deployd/examples/comments-1.zip"><i class="icon-white icon-download"></i> Download Source</a>
<!--{
  title: 'The "dpd" Command Line Tool'
}-->

## Using the dpd command line tool

### Commands

#### dpd

Start Deployd the current project in development mode with an interactive shell/repl for interacting with the running server.

#### dpd create [name]

Create a Deployd project in a new directory with the given `name`.

#### dpd showkey

Print the app's key for use in a remote dashboard or for making remote authenticated / administrative requests.

#### dpd keygen

Generate a new key for remote access / administration.

#### dpd remote

Open up the remote dashboard in your browser.

### Help

Here is the help output of `dpd -h`:

    Usage: dpd [options] [command]

    Commands:

      create [project-name]
      	create a project in a new directory
      	eg. `dpd create my-app`

      keygen
      	generate a key for remote access (./.dpd/keys.json)

      showkey
      	shows current key for connecting to remote dashboard (./.dpd/keys.json)

      remote
      	open the remote dashboard in your browser


      *
      	[default] start the server in the current project in development mode
      	with an interactive shell/repl for interacting with the running server
      	e.g. dpd (starts server in current directory),
      	     dpd my-app/app.dpd (starts app from file)

    Options:

      -h, --help                   output usage information
      -V, --version                output the version number
      -m, --mongod [path]          path to mongod executable (defaults to `mongod`)
      -p, --port [port]            port to host server (defaults to 2403)
      -w, --wait                   wait for input before exiting
      -d, --dashboard              start the dashboard immediately
      -o, --open                   open in a browser
      -e, --environment [env]      defaults to development
      -H, --host [host]            specify host for mongo server
      -P, --mongoPort [mongoPort]  mongodb port to connect to
      -n, --dbname [dbname]        name of the mongo database
      -a, --auth                   prompts for mongo server credentials

### Debugging

Deployd uses [debug](https://www.npmjs.com/package/debug) to log requests and show other internal debug info. To activate it you need to set the `DEBUG` env variable to `*`, for example:

    $ DEBUG=* dpd
<!--{
  title: 'The Public Directory',
  tags: ['guide']
}-->

## The Public Directory

Deployd serves static files from your app's `/public` directory. This directory is created when you run `dpd create`. These files will be served with the appropriate cache headers (`Last-Modified` and `Etag`) so browsers will cache them.

If available, Deployd will serve `index.html` as the default file in a folder.

### Environments

When Deployd is run with the environment setting (see the documentation on the [cli](/docs/basics/cli.md)), it will attempt to serve files from the `/public-[environment]` directory instead. For example, if Deployd is run with `dpd -e production`, it will serve files from the `/public-production` directory.

This is useful for optimizing your app in production. You can serve a slightly different version of your front-end with minified JavaScript and CSS. You can also use it to serve compiled versions of pre-processed languages such as LESS, SASS, and CoffeeScript. 

If the environment-specific public directory does not exist, it will serve from the standard `/public` directory.<!--{
  title: 'Using Source Control with Deployd',
  tags: ['guide']
}-->

## Using Source Control with Deployd

Deployd projects are designed to be committed to version control systems so teams can easily manage the source of their applications. 

### Recommended Ignored Files

You shouldn't commit the `/data` or `.dpd` directories. The files in these directories are environment specific and should be kept out of version control. All other Deployd files should be committed.
<!--{
  title: 'Accessing Collections with dpd.js',
  tags: ['guide', 'collection']
}-->

## Accessing Collections with dpd.js

`dpd.js` is an auto-generated library that updates as you update the resources in your Deployd API. If you are writing your front-end in the `public` directory, include a script tag tag in your HTML:

    <script src="/dpd.js" type="text/javascript"></script>

*Note: The dpd.js file will not appear in the `public` directory because it is generated at runtime.*

### Example Usage

    dpd.todos.get(function(todos, error) {
      if (error) {
        alert(error.message);
      } else {
        for (var i = 0; i < todos.length; i++) {
          renderTodo(todos[i]);
        };
      }
    });

Dpd.js functions are *asynchronous*: they do not return a value, but execute a callback function when the AJAX operation is complete.

    // Does not work
    var result = dpd.todos.get();

<!--...-->

    // Works as expected
    dpd.todos.get(function(result, error) {
      // Work with result
    });

For details on using dpd.js, see the [dpd.js reference](/docs/collections/reference/dpd-js.md)

Also see [A Simple Todo App](/docs/collections/examples/a-simple-todo-app.md) for a working example.

### Using dpd.js on a different origin

You can use the dpd.js library outside of the `public` folder by using an absolute URL to the file.

This will not work on browsers that do not support Cross-Origin Resource Sharing (namely Internet Explorer 7 and below).


### Accessing Collections without Dpd.js

The dpd.js library is not required; it is only a utility library for accessing Deployd's HTTP API with AJAX. For details on the HTTP API, see the [HTTP API Refernence](/docs/collections/reference/http.md).

Some front-end libraries include support for HTTP or REST APIs; for examples of how to use these instead of dpd.js, see [A Simple Todo App with Backbone](/docs/collections/examples/a-simple-todo-app-with-backbone.md) and [A Simple Todo App with AngularJS](/docs/collections/examples/a-simple-todo-app-with-angular.md)<!--{
  title: 'Adding Custom Business Logic with Events',
  tags: ['guide', 'collection', 'events']
}-->

## Adding Custom Business Logic with Events

Events allow you to add custom business logic to your Collection. By writing Events, you can add validation, relationships, and security to your app. Events are written in JavaScript (specifically, the ECMAScript 5 standard) and have access to the [Collection Events API](/docs/collections/reference/event-api.md).

The following events are available for scripting:

### On Get

> file: resources/{resourcename}/get.js

Called whenever an object is loaded from the server. Commonly used to hide properties, restrict access to private objects, and calculate dynamic values.

    // Example On Get: Hide Secret Properties
    if (!me || me.id !== this.creatorId) {
      hide('secret');
    }

<!--seperate-->

    // Example On Get: Load A Post's Comments
    if (query.loadComments) {
      dpd.comments.get({postId: this.id}, function(comments) {
        this.comments = comments;
      });  
    }

*Note: When a list of objects is loaded, `On Get` will run once for each object in the list. Calling `cancel()` in this case will remove the object from the list, rather than cancelling the entire request.*

### On Validate 

> file: resources/{resourcename}/validate.js

Called whenever an object's values change, including when it is first created. Commonly used to validate property values and calculate certain dynamic values (i.e. last modified time). 

    // Example On Validate: Enforce a max length
    if (this.body.length > 100) {
      error('body', "Cannot be more than 100 characters");
    }

<!--seperate-->

    // Example On Validate: Normalize an @handle
    if (this.handle.indexOf('@') !== 0) {
      this.handle = '@' + this.handle;
    }

*Note: `On Post` or `On Put` will execute after `On Validate`, unless `cancel()` or `error()` is called*


### On Post

> file: resources/{resourcename}/post.js

Called when an object is created. Commonly used to prevent unauthorized creation and save data relevant to the creation of an object, such as its creator.

    // Example On Post: Save the date created
    this.createdDate = new Date().getTime();

<!--seperate-->

    // Example On Post: Prevent unauthorized users from posting
    if (!me) {
      cancel("You must be logged in", 401);
    }


### On Put

> file: resources/{resourcename}/put.js

Called when an object is updated. Commonly used to restrict editing access to certain roles, or to protect certain properties from editing. It is strongly recommended that you `protect()` any properties that should not be modifiable by users after an object is created.

    // Example On Put: Protect readonly/automatic properties
    protect('createdDate');
    protect('creatorId');

### On Delete 

> file: resources/{resourcename}/delete.js

Called when an object is deleted. Commonly used to prevent unauthorized deletion.

    // Example On Delete: Prevent non-admins from deleting
    if (!me || me.role !== 'admin') {
      cancel("You must be an admin to delete this", 401);
    }
    
### On Before request 

> file: resources/{resourcename}/beforerequest.js

called before GET/POST/PUT/DELETE requests

### Asynchronous

> Want to look up stuff in the database, but your request finishes before your db-call returns?


* In that case, you want **async** webrequest.

By default events are **synchronous**, however they can be turned into async like so:


    var async = require("async");
    $addCallback();

    var payload = this // in case of POST/PUT

    async.each(body.storeData, function (data, done) {
      doStuffOnData(data, function (err, result) {
         done(err, result);
      );
    }, function (err){
        if (err) return cancel(err);
        $finishCallback()`; instead of `done(err,{})`
    });

> NOTE: in case of **dpd-event** events, use `setResult({})` instead of `done(err,{})`
<!--{
  title: 'Building a Custom Client',
  tags: ['reference', 'collection', 'http', 'websockets', 'cors']
}-->

## Accessing Collections - Building a Custom Client
 
In this guide, we will build an HTTP client from scratch to perform CRUD as well as listen for events from a Collection.

### REST

Most REST clients should work with Deployd Collections right away, though Deployd does not strictly follow REST. For example, Backbone.js and AngularJS's HTTP utilities work with Deployd without modification.

### WebSockets

To fully implement the Collection API, a client must be compatible with WebSockets and Socket.IO specifically. Clients are responsible for sending heartbeat information as well as reconnecting in the case of unexpected disconnects.
    
### Building a Node.js Client

The following is implemented in [Node.js](http://nodejs.org/), but the basic idea can be applied to any language or platform.

#### Basics

All we need to create a collection client is a constructor and a single method for making requests.

    var request = require('request');

    function Collection(url) {
      this.url = url
    }

    Collection.prototype.request = function (options, fn) {
      var url = this.url;
      options.url = url + (options.url || '');  
      request(options, function (err, res, body) {
        if(res.statusCode >= 400) {
          err = body || {message: 'an unknown error occurred'};
          return fn(err);
        }
    
        fn(null, body);
      });
    }
    
Now we can construct new collections by passing the URL as the only argument to our constructor.

    var c = new Collection('http://foo.deploydapp.com/todos');

    c.request({url: '?done=false'}, function(err, todos) {
      console.log(todos); // [...]
    });

We can add an object to our collection by passing an object as the json body and setting the `method` to "POST".

    var todo = {
      title: 'wash the car'
    };

    c.request({json: todo, method: 'POST'}, function(err, todo) {
      console.log(todo); // {id: '...', ...}
    });
    
To update an object we just need to set the `method` to "PUT".

    var todo = {
      id: '06a5254f11ff7853',
      done: true
    };

    c.request({json: todo, method: 'PUT'}, function(err, todo) {
      console.log(todo); // {id: '...', ...}
    });

Deleting an object requires an ID and the method must be set to "DELETE".

    var id = '06a5254f11ff7853';

    c.request({url: '/' + id, method: 'DELETE'}, function(err, todo) {
      console.log(err); // null - if no error occurred
    });
    
### Listening to Events

The simplest way to listen events is to use a Socket.IO client. You can find a list of clients [here](https://github.com/LearnBoost/socket.io/wiki).

Using the node.js Socket.IO client, we can create a socket by connecting to our deployed app. Then calling the socket's `on()` method to listen to a custom event emitted by a collection.

    var io = require('socket.io-client');
    var socket = io.connect('http://foo.deploydapp.com');

    socket.on('my event', function (data) {
      console.log(data); // emit()ed from the server
    });
<!--{
  title: 'Creating Collections',
  tags: ['guide', 'collection']
}-->

## Creating Collections

A Collection exposes a database-like API directly to clients over HTTP and WebSockets. Clients can run advanced queries, create and update objects, and listen for realtime messages to sync with the Collection when it updates. You can create a Collection in the dashboard by clicking the "Resources +" button in the sidebar, and choosing "Collection".

### Properties

Every Collection requires a set of properties that describe the data it can store. By default every object in a Collection is created with an `id`. If an object being `POST`ed or `PUT` into a Collection includes properties or values that don't match what the collection allows, they will be ignored. The following property types are available when creating a Collection:

 - `String` - Acts like a JavaScript string
 - `Number` - Stores numeric values, including floating points.
 - `Boolean` - Either true or false. (To avoid confusion, Deployd will consider null or undefined to be false)
 - `Object` - Stores any JSON object. Useful for storing arbitrary data on an object without needing to validate schema.
 - `Array` - Stores an array of any type.

### The Data Editor

Once you create a Collection from the dashboard, you can add and edit its data using the data editor. The data editor is designed to edit all sorts of data, including objects and arrays.

#### Basic Use

Double-click in a cell to start editing. Press Enter to save your changes, or Escape to cancel and undo your changes.

While editing a string property, click the "edit" icon next to the field to open up a multiline editor.

Click the trash can icon in any row to delete it.

Edit the bottom-most row to create a new object. Press Enter when editing a property to save the row, or click the checkmark in the margin.

#### Useful Shortcuts

 - Use the arrow keys to move your selection without using the mouse.
 - Press "Enter" when a cell is selected to start editing.
 - Start typing when a cell is selected to overwrite its existing value. 
 - If you accidentally save a change, press Ctrl/Cmd-Z to reverse it.
 - Press Ctrl-Delete to remove a row. Press Ctrl/Cmd-Z to add it back. (heads up: it will have a different `id`)
 - Press Ctrl-Enter to open up the multiline editor for a string property; this lets you write long text values.
 - Press Ctrl-Enter while in the multiline editor to save it (pressing Enter will just create a new line)
 - Press Tab to save the current property and edit the next one.
<!--{
  title: 'A Simple Todo App with AngularJS',
  tags: ['example', 'collection', 'angularjs']
}-->

## A Simple Todo App with AngularJS

![Todo app](/examples/images/todo-app.png)

This app demonstrates how to access a Collection's API using the [AngularJS](http://angularjs.org/) framework.

<a href="https://github.com/downloads/deployd/examples/todo-app-angular.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/examples/tree/master/collection/todo-app-angular" class="btn">View Source</a>

### Useful files

- [index.html](https://github.com/deployd/examples/blob/master/collection/todo-app-angular/public/index.html)
- [todo.js](https://github.com/deployd/examples/blob/master/collection/todo-app-angular/public/js/todo.js)<!--{
  title: 'A Simple Todo App with Backbone.js',
  tags: ['example', 'collection', 'backbone']
}-->

## A Simple Todo App with Backbone.js

![Todo app](/examples/images/todo-app.png)

This app demonstrates how to access a Collection's API using [Backbone.js](http://backbonejs.org/).

<a href="https://github.com/downloads/deployd/examples/todo-app-backbone.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/examples/tree/master/collection/todo-app-backbone" class="btn">View Source</a>

### Useful files

- [index.html](https://github.com/deployd/examples/blob/master/collection/todo-app-backbone/public/index.html)
- [todo.js](https://github.com/deployd/examples/blob/master/collection/todo-app-backbone/public/js/todo.js)<!--{
  title: 'A Simple Todo App',
  tags: ['example', 'collection', 'dpd.js']
}-->

## A Simple Todo App

![Todo app](/examples/images/todo-app.png)

This app demonstrates how to access a Collection's API using dpd.js.

<a href="https://github.com/downloads/deployd/examples/todo-app.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/examples/tree/master/collection/todo-app" class="btn">View Source</a>

### Useful files

- [todo.js](https://github.com/deployd/examples/blob/master/collection/todo-app/public/js/todo.js)<!--{
  title: 'Chatroom',
  tags: ['example', 'collection', 'dpd.js', 'realtime']
}-->

## Chatroom

![Todo app](/examples/images/chat-room.png)

This app demonstrates how to send messages to the client using Sockets when data is updated on the server.

<a href="https://github.com/downloads/deployd/examples/chatroom.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/examples/tree/master/collection/chatroom" class="btn">View Source</a>

### Useful files

- [chatroom.js](https://github.com/deployd/examples/blob/master/collection/chatroom/public/js/chatroom.js)
- [messages/validate.js](https://github.com/deployd/examples/blob/master/collection/chatroom/resources/messages/validate.js) (On Validate `/messages`)
- [messages/post.js](https://github.com/deployd/examples/blob/master/collection/chatroom/resources/messages/post.js) (On POST `/messages`)## Collections

The most commonly used resource in a Deployd app is the Collection. It exposes a database like API that allows any client to query, modify and sync the data in your app, all without having to write a ton of boilerplate code on the server.

### Properties

Collection properties allow you to restrict what type of data a collection can store. You define them using the **property editor** in the dashboard. 

![Property Editor](/images/property-editor.png)

### Data

Collection's use JSON to store and transport your objects over the wire. Deployd comes bundled with a fully featured **data-editor** for easily managing the data in your collection.

### Events

[Control the behavior and business logic](/docs/collections/adding-logic.md) of the data in your collection by writing events. Events also allow you to easily create [relationships between collections](/docs/collections/relationships-between-collections.md).

### Notifying Clients of Changes

Deployd allows you to [send messages to the browser in real time](/docs/collections/notifying-clients.md) when a Collection is updated.<!--{
  title: 'Notifying the Client of Changes with Messages',
  tags: ['guide', 'collection', 'sockets', 'emit']
}-->

## Notifying the Client of Changes with Messages

Keeping all of the clients of your API up-to-date with your collection's latest data is simple with collection events. For example, in a `PUT` event, you can notify all connected clients of the changes to the object being updated by calling the [emit()](/docs/collections/reference/event-api.md#s-emit) function to send all connected users a message.

The `emit()` function takes an event argument and an arbitrary data object to send to all of the connected clients  (eg. `emit('my message', {foo: 'bar'})`). Dpd.js clients can listen for these events using the `on()` method (eg. `dpd.todos.on('my message', fn)`).

### Example

Let's say you want to make a chatroom app and you have a Collection called `/messages`. 

In the `On POST` event of `/messages`, you would add the following line:

    emit('messages:create', this);

This sends a message called `messages:create` (This could be anything) with the current object (`this`) as an argument. The `messages:` prefix namespaces the event to the collection.

On the client, you would listen for that event using `dpd.on()` and respond by updating the DOM:

    dpd.messages.on('create', function(message) {
      renderMessage(message);
    });

The `message` argument is the value you passed on the server (`this`).

See the [Chatroom Example](/docs/collections/examples/chatroom.md) for a working version of this code.

### Browser and Server Support

The realtime messaging features of Deployd are built on [Socket.IO](http://socket.io/) and work on almost every major browser:

- Internet Explorer 5.5+
- Safari 3+
- Google Chrome 4+
- Firefox 3+
- Opera 10.61+
- iOS Safari
- Android WebKit
- WebOS WebKit

(taken from [Socket.IO's site](http://socket.io/#browser-support))

### Further Reading

- [Event API](/docs/collections/notifying-clients.md)
- [dpd.js Reference](/docs/collections/reference/dpd-js.md)
- [HTTP API Reference](/docs/collections/reference/http.md)

<!--{
  title: 'Using dpd.js',
  tags: ['reference', 'collection', 'http', 'websockets', 'cors']
}-->

## Dpd.js

`dpd.js` is an auto-generated library that provides access to Collections and other Deployd features on the front-end. For a basic overview, see [Accessing Collections with dpd.js](/docs/collections/accessing-collections.md).

### Accessing the Collection

The API for your Collection is automatically generated as `dpd.[collectionname]`.

Examples:

    dpd.todos
    dpd.users
    dpd.todolists

*Note: If your Collection name has a dash in it (e.g. `/todo-lists`), the dash is removed when accessing it in this way (e.g. `dpd.todolists`).*

You can also access your collection by using `dpd(collectionName)` as a function.

Examples:

    dpd('todos')
    dpd('users')
    dpd('todo-lists')

*Note: Collections accessed in this way will not have helper functions besides `get`, `post`, `put`, `del`, and `exec` (see [Dpd.js for Custom Resources](/docs/using-modules/reference/dpd-js.md) for details on these generic functions)*


### Collection API

The examples below use a Collection called `/todos` with the following schema:

- `id`
- string `title`
- string `category`

#### Callbacks

Every function in the Collection API takes a callback function (represented by `fn` in the docs) with the signature `function(result, error)`.

The callback will be executed asynchronously when the API has received a response from the server.

The `result` argument differs depending on the function. If the result failed, it will be `null` and the `error` argument will contain the error message.

The `error` argument, if there was an error, is an object:

 - `status` (number): The HTTP status code of the request. Common codes include:
  - 400 - Bad Request: The request contained invalid data and could not be completed
  - 401 - Unauthorized: The current session is not authorized to perform that action
  - 500 - Internal Server Error: Something went wrong on the server
 - `message` (string): A message describing the error. Not always present.
 - `errors` (object): A hash of error messages corresponding to the properties of the object that were sent - usually indicates validation errors. Not always present.

Examples of errors:

    {
      "status": 401,
      "message": "You are not allowed to access that collection!"
    }

<!--...-->

    {
      "status": 400,
      "errors": {
          "title": "Title must be less than 100 characters",
          "category": "Not a valid category"
      }
    }


#### Promises

Every function in the collection API returns a promise.
We use the [`ayepromise` library](https://github.com/cburgmer/ayepromise) (which follows the [Promises/A+ 1.1 specs](https://promisesaplus.com/)).
To learn how to use promises, please, refer [to this article](http://www.html5rocks.com/en/tutorials/es6/promises).

The first callback contains the same `result` same with the classic callbacks.
The second callback contains the `error` object as described above.
Here's an example to use promises within dpd.js:

    dpd.todos.post({message: "Hello world"}).then(function(todo) {
      // do something with todo
      console.log(todo); // display {id: "###", message: 'Hello world'}
    }, function(err) {
      // do something with the error
      console.log(err); // display an error if the request failed
    });

<!--...-->

    dpd.todos.get('1234324324').then(function(todo) {
      // do something with todo
      console.log(todo); // display {id: "###", message: 'Hello world'}
    }, function(err) {
      // do something with the error
      console.log(err.errors.message); // display the error message
    });


#### .get([id], [query], fn) <!-- api -->

##### Listing Data

The `.get(fn)` function returns an array of objects in the collection.

    // Get all todos
    dpd.todos.get(function(results, error) {
      //Do something
    });

`results` is an array of objects:

    [
      {
        "id": "320d6151a9aad8ce",
        "title": "Wash the dog",
        "category": "pets"
      }, {
        "id": "320d6151a9aad8ce"
        "title": "Write autobiography",
        "category": "writing"
      }
    ]

If the collection has no objects, it will be an empty array:

    []

##### Querying Data

The `.get(query, fn)` function filters results by the specified query object. See [Querying Collections](/docs/collections/reference/querying-collections.md) for information on constructing a query.

    // Get all todos that are in the pets category
    dpd.todos.get({category: 'pets'}, function(results, error) {
      // Do something
    });

`results` is an array of objects:

    [
      {
        "id": "320d6151a9aad8ce",
        "title": "Wash the dog",
        "category": "pets"
      }
    ]

##### Getting a Specific Object

The `.get(id, fn)` function returns a single object by its `id` property.

    // Get a specific todo
    dpd.todos.get("320d6151a9aad8ce", function(result, error) {
      // Do something
    });

`result` is the object that you requested:

    {
      "id": "320d6151a9aad8ce",
      "title": "Wash the dog",
      "category": "pets"
    }

#### .post([id], object, fn) <!-- api -->

##### Creating an Object

The `.post(object, fn)` function creates an object in the collection with the specified properties.

    // Create a todo
    dpd.todos.post({title: "Walk the dog"}, function(result, error)) {
      // Do something
    });

`result` is the object that you posted, with any additional calculated properties and the `id`:

    {
      "id": "91c621a3026ca8ef",
      "title": "Walk the dog"
    }

##### Updating an Object

The `.post(id, object, fn)` function, or `.post(object, fn)` where `object` has an `id` property, will update an object. Using the `.post()` function in this way behaves the same as the `put()` function.

This is useful when you want to insert an object if it does not exist and update it if it does.

#### .put([id or query], object, fn) <!-- api -->

##### Updating an Object

The `.put(id, object, fn)` function will update an object that is already in the collection. It will only change the properties that are provided. It is also possible to incrementally update certain properties; see [Updating Objects in Collections](/docs/collections/reference/updating-objects.md) for details.

    // Update a todo
    dpd.todos.put("91c621a3026ca8ef", {title: "Walk the cat"}, function(result, error)) {
      // Do something
    });

You can also use the syntax `put(object, fn)` if `object` has an `id` property:

    // Update a todo
    dpd.todos.put({id: "91c621a3026ca8ef", title: "Walk the cat"}, function(result, error)) {
      // Do something
    });

Finally, you can provide a `query` object to ensure that the object you are updating has the correct properties. You must still provide an `id` property. This can be useful as a failsafe.

    // Update a todo only if it is in the "pets" category
    dpd.todos.put(
      {id: "91c621a3026ca8ef", category: "pets"},
      {title: "Walk the cat"},
      function(result, error) {
        // Do something
      });

`result` is the entire object after the update:

    {
      "id": "91c621a3026ca8ef",
      "title": "Walk the cat",
      "category": "pets"
    }

The `.put()` function will return an error if the `id` and/or `query` does not match any object in the collection:

    {
      "status":400,
      "message":"No object exists that matches that query"
    }

#### .del(id or query, fn) <!-- api -->

##### Deleting an Object

The `.del(id, fn)` function will delete an object from the collection.

    // Delete an object
    dpd.todos.del("91c621a3026ca8ef", function(result, error) {
      // Do something
    });

You can also use the syntax `.del(query, fn)` if `object` has an `id` property. You can add additional properties to the `query` object to ensure that you are removing the correct object:

    // Delete an object
    dpd.todos.del({id: "91c621a3026ca8ef", title: "Walk the dog"}, function(result, error) {
      // Do something
    });

`result` will always be null.

### Realtime API

#### dpd.on(message, fn) <!-- api -->

The `dpd.on(message, fn)` function listens for realtime messages emitted from the server. See [Notifying the Client of Changes](/docs/collections/notifying-clients.md) for information on sending realtime messages with the `emit()` function.

* `message` - The name of the message to listen for
* `fn` - Callback `function(messageData)`. Called every time the message is received. There is no `error` argument.

<!--seperate-->

    // Listen for a new todo
    dpd.on('todos:create', function(post) {
      // Do something
    });

In your Collection Event:

    // On Post
    emit('todos:create', this);

Calling `.on()` on the collection itself will namespace the message by the collection name:

    // Same as dpd.on('todos:create', fn)
    dpd.todos.on('create', function(post) {
      // Do something
    });

#### dpd.off(message, [fn]) <!-- api -->

The `dpd.off(message)` function stops listening for the specified message.

    dpd.off('todos:create');

You can also provide a function that was originally set as a listener to remove only that function.

    function onTodoCreated(post) {
      // Do something
    }

    dpd.on('todos:create', onTodoCreated);

    dpd.off('todos:create', onTodoCreated);

Calling `.off()` on the collection itself will namespace the message by the collection name:

    // Same as dpd.off('todos:create');
    dpd.todos.off('create');

#### dpd.once(message, fn) <!-- api -->

The `dpd.once(message, fn)` function listens for a realtime message emitted by the server and runs the `fn` callback exactly once.

    dpd.once('todos:create', function(post) {
      // Do something
    });

Calling `.once()` on the collection itself will namespace the message by the collection name:

    // Same as dpd.once('todos:create');
    dpd.todos.once('create', function(post) {
      // Do something
    });

#### dpd.socketReady(fn) <!-- api -->

The `dpd.socketReady(fn)` function waits for a connection to be established to the server and executes the `fn` callback with no arguments. If a connection has already been established, it will execute the `fn` callback immediately.

It can sometimes take a second or more to establish a connection, and messages sent during this time will not be received by your front end. This function is useful for ensuring that you will receive an message when it is broadcast.

    dpd.socketReady(function() {
      // Do something
    });

#### dpd.socket <!-- api -->

The `dpd.socket` object is a [socket.io](http://socket.io/#how-to-use) object. This is useful if you want to finely control how messages are received.
<!--{
  title: 'Event API',
  tags: ['reference', 'collection']
}-->

## Event API

### this <!--api-->

The current object is represented as `this`. You can always read its properties. Modifying its properties in an `On Get` request will change the result that the client receives, while modifying its properties in an `On Post`, `On Put`, or `On Validate` will change the value in the database.

    // Example: On Validate
    // If a property is too long, truncate it
    if (this.message.length > 140) {
      this.message = this.message.substring(0, 137) + '...';
    }

*Note*: In some cases, the meaning of `this` will change to something less useful inside of a function. If you are using functions such as `Array.forEach()`, you may need to bind another variable to `this`:

    // Won't work - sum remains at 0
    this.sum = 0;
    this.targets.forEach(function(t) {
      this.sum += t.points;
    });

<!--seperate-->

    //Works as expected
    var self = this;

    this.sum = 0;
    this.targets.forEach(function(t) {
      self.sum += t.points;
    });


### ctx <!-- ctx -->

The context of the request. This object contains everything from the request (request, response, body, headers, etc...):

    // Example:
    if (ctx && ctx.req && ctx.req.headers && ctx.req.headers.host !== '192.168.178.34:2403') {
      cancel("You are not authorized to do that", 401);
    }

The entire object is [available as a gist here](https://gist.github.com/NicolasRitouet/2fc5dd20f3af7dc7e192).

### me <!-- api -->

The currently logged in User from a User Collection. `undefined` if no user is logged in.

    // Example: On Post
    // Save the creator's information
    if (me) {
        this.creatorId = me.id;
        this.creatorName = me.name;
    }

### isMe() <!-- api -->

    isMe(id)

Checks whether the current user matches the provided `id`.

    // Example: On Get /users
    // Hide properties unless this is the current user
    if (!isMe(this.id)) {
        hide('privateVariable');
    }

<!-- seperate -->

    // Example: On Put
    // Make sure that only the creator can edit a post
    cancelUnless(isMe(this.id), "You are not authorized to edit that post", 401);

### query <!-- api -->

The query string object. On a specific query (such as `/posts/a59551a90be9abd8`), this includes an `id` property.

    // Example: On Get
    // Don't show the body of a post in a general query
    if (!query.id) {
      hide(this.body);
    }

### cancel() <!-- api -->

    cancel(message, [statusCode])

Stops the current request with the provided error message and HTTP status code. Status code defaults to `400`. Commonly used for security and authorization.

It is strongly recommended that you `cancel()` any events that are not accessible to your front-end, because your API is open to anyone.

    // Example: On Post
    // Don't allow non-admins to create items
    if (!me.admin) {
      cancel("You are not authorized to do that", 401);
    }

*Note: In a GET event where multiple values are queried (such as on `/posts`), the `cancel()` function will remove the current item from the results without an error message.*

### cancelIf(), cancelUnless() <!-- api -->

    cancelIf(condition, message, [statusCode])
    cancelUnless(condition, message, [statusCode])

Calls `cancel(message, statusCode)` if the provided condition is truthy (for `cancelIf()`) or falsy (for `cancelUnless()`).

    Example: On Post
    // Prevent banned users from posting
    cancelUnless(me, "You are not logged in", 401);
    cancelIf(me.isBanned, "You are banned", 401);

### error() <!-- api -->

    error(key, message)

Adds an error message to an `errors` object in the response. Cancels the request, but continues running the event so it can collect multiple errors to display to the user. Commonly used for validation.

    // Example: On Validate
    // Don't allow certain words
    // Returns response {"errors": {"name": "Contains forbidden words"}}
    if (!this.name.match(/(foo|bar)/)) {
      error('name', "Contains forbidden words");
    }

### errorIf(), errorUnless() <!-- api -->

    errorIf(condition, key, message)
    errorUnless(condition, key, message)

Calls `error(key, message)` if the provided condition is truthy (for `errorIf()`) or falsy (for `errorUnless()`).

    // Example: On Validate
    // Require message to be a certain length
    errorUnless(this.message && this.message.length > 2, 'message', "Must be at least 2 characters");

### hide() <!-- api -->

    hide(property)

Hides a property from the response.

    // Example: On Get
    // Don't show private information
    if (!me || me.id !== this.creatorId) {
      hide('secret');
    }

### protect() <!-- api -->

    protect(property)

Prevents a property from being updated. It is strongly recommended you `protect()` any properties that should not be modified after an object is created.

    // Example: On Put
    // Protect a property
    protect('createdDate');

<!-- seperate -->

    // Example: On Put
    // Only the creator can change the title
    if (!(me && me.id === this.creatorId)) {
      protect('title');
    }


### changed() <!-- api -->

    changed(property)

Returns whether a property has been updated.

    // Example: On Put
    // Validate the title when it changes
    if(changed('title') && this.title.length < 5) {
      error('title', 'must be over 5 characters');
    }

### previous <!-- api -->

An `Object` containing the previous values of the item to be updated.

    // Example: On Put
    if(this.votes < previous.votes) {
      emit('votes have decreased');
    }

### emit() <!-- api -->

    emit([userCollection, query], message, [data])

Emits a realtime message to the client.

    // Example: On Post
    // Alert clients that a new post has been created
    emit('postCreated', this);

In the front end:

    // Listen for new posts
    dpd.on('postCreated', function(post) {
        //do something...
    });

You can use `userCollection` and `query` parameters to limit the message broadcast to specific users.

    // Example: On Put
    // Alert the owner that their post has been modified
    if (me.id !== this.creatorId) {
      emit(dpd.users, {id: this.creatorId}, 'postModified', this);
    }

See [Notifying Clients of Changes with Sockets](/docs/collections/notifying-clients.md) for an overview on realtime functionality.

### dpd <!-- ref -->

The entire [dpd.js](/docs/collections/reference/dpd-js.md) library, except for the realtime functions, is available in events. It will also properly bind `this` in callbacks.

    // Example: On Get
    // If specific query, get comments
    dpd.comments.get({postId: this.id}, function(results) {
      this.comments = results;
    });

<!--seperate-->

    // Example: On Delete
    // Log item elsewhere
    dpd.archived.post(this);

Dpd.js will prevent recursive requests if you set the [$limitRecursion](/docs/collections/reference/querying-collections.md#s-$limitRecursion) property. This works by returning `null` from a `dpd` function call that has already been called several times further up in the stack.

    // Example: On Get /recursive
    // Call self
    dpd.recursive.get({$limitRecursion: 1}, function(results) {
        if (results) this.recursive = results;
    });

<!--seperate-->

    // GET /recursive
    {
        "id": "a59551a90be9abd8",
        "recursive": [
            {
                "id": "a59551a90be9abd8"
            }
        ]
    }


### internal <!-- api -->

Equal to true if this request has been sent by another script.

    // Example: On GET /posts
    // Posts with a parent are invisible, but are counted by their parent
    if (this.parentId && !internal) cancel();

    dpd.posts.get({parentId: this.id}, function(posts) {
        this.childPosts = posts.length;
    });

### isRoot <!-- api -->

Equal to true if this request has been authenticated as [root](/docs/collections/reference/http.md#s-Root-Requests) (has the `dpd-ssh-key` header with the appropriate key; such as from the dashboard)

    // Example: On PUT /users
    // Protect reputation property - should only be calculated by a custom script.

    if (!isRoot) protect('reputation');


### console.log() <!-- api -->

    console.log([arguments]...)

Logs the values provided to the command line. Useful for debugging.
<!--{
  title: 'Over HTTP',
  tags: ['reference', 'collection', 'http', 'websockets', 'cors']
}-->

## Accessing Collections Over HTTP

Deployd exposes an HTTP API to your Collections which can be used by any platform or library that supports HTTP or AJAX. Though it does not strictly adhere to REST, it should also work with most libraries designed for REST.

### Collection API

The examples below use a Collection called `/todos` with the following schema:

- `id`
- string `title`
- string `category`

Your Collection is available at the URL you specified. If you are using the default development hostname of `localhost:2403`, for example, the `/todos` collection will be available at `http://localhost:2403/todos`.

#### Requests <!-- ref -->

A request to the Deployd API should include the `Content-Type` header. The following content types are supported:

- `application/json` (recommended)
- `application/x-www-form-urlencoded` (All values will be parsed as strings)

The `Content-Type` header is not necessary for `GET` or `DELETE` requests which have no body.

#### Responses <!-- ref -->

Deployd will send standard HTTP status codes depending on the results on an operation. If the code is 200 (OK), the request was successful and the result is available in the body as JSON.

If the code is 204 (No Content), the request was successful, but there is no result.

If the code is 400 or greater, it will return the error message formatted as a JSON object:

 - `status` (number): The HTTP status code of the request. Common codes include:
  - 400 - Bad Request: The request contained invalid data and could not be completed
  - 401 - Unauthorized: The current session is not authorized to perform that action
  - 500 - Internal Server Error: Something went wrong on the server
 - `message` (string): A message describing the error. Not always present.
 - `errors` (object): A hash of error messages corresponding to the properties of the object that was sent - usually indicates validation errors. Not always present.

Examples of errors:
  
    {
      "status": 401,
      "message": "You are not allowed to access that collection!"
    }

<!--...-->

    {
      "status": 400,
      "errors": {
          "title": "Title must be less than 100 characters",
          "category": "Not a valid category"
      }
    }

#### Listing Data <!-- ref -->

To retreive an array of objects in the collection, send a `GET` request to your collection's path:

    GET /todos

The response will be an array of objects: 

    200 OK
    [
      {
        "id": "320d6151a9aad8ce",
        "title": "Wash the dog",
        "category": "pets"
      }, {
        "id": "320d6151a9aad8ce"
        "title": "Write autobiography",
        "category": "writing"
      }
    ]

If the collection has no objects, it will be an empty array:

    200 OK
    []    

#### Querying Data <!-- ref -->

To filter results by the specified query object, send a `GET` request to your collection's path with a query string.  See [Querying Collections](/docs/collections/reference/querying-collections.md) for information on constructing a query.

    GET /todos?category=pets

For more advanced queries, you will need to pass the query string as JSON instead:

    GET /todos?{"category": "pets"}

The response body is an array of objects: 

    200 OK
    [
      {
        "id": "320d6151a9aad8ce",
        "title": "Wash the dog",
        "category": "pets"
      }
    ]

#### Getting a Specific Object <!-- ref -->

To retrieve a single object by its `id` property, send a `GET` request with the `id` value as the path.

    GET /todos/320d6151a9aad8ce

The response body is the object that you requested:

    200 OK
    {
      "id": "320d6151a9aad8ce",
      "title": "Wash the dog",
      "category": "pets"
    }

#### Creating an Object <!-- ref -->

To create an object in the collection, send a `POST` request with the object's properties in the body.

    POST /todos
    {
      "title": "Walk the dog"
    }

The response body is the object that you posted, with any additional calculated properties and the `id`:

    {
      "id": "91c621a3026ca8ef",
      "title": "Walk the dog"
    }

#### Updating an Object <!-- ref -->

To update an object that is already in the collection, send a `POST` or `PUT` request with the `id` value as the path and with the properties you wish to update in the body. It will only change the properties that are provided. It is also possible to incrementally update certain properties; see [Updating Objects in Collections](/docs/collections/reference/updating-objects.md) for details.

    PUT /todos/91c621a3026ca8ef
    {
      "title": "Walk the cat"
    }

<!--...-->

    POST /todos/91c621a3026ca8ef
    {
      "title": "Walk the cat"
    }

You can also omit the `id` in the path if you provide an `id` property in the body:

    PUT /todos
    {
      "id": "91c621a3026ca8ef"
      "title": "Walk the cat"
    }

Finally, you can provide a query string to ensure that the object you are updating has the correct properties. You must still provide an `id`. This can be useful as a failsafe.

    PUT /todos/91c621a3026ca8ef?category=pets
    {
      "title": "Walk the cat"
    }

The response body is the entire object after the update:

    200 OK  
    {
      "id": "91c621a3026ca8ef",
      "title": "Walk the cat",
      "category": "pets"
    }

The `PUT` verb will return an error if the `id` and/or `query` does not match any object in the collection:

    400 Bad Request
    {
      "status": 400,
      "message": "No object exists that matches that query"
    }

#### Deleting an Object <!-- ref -->

To delete an object from the collection, send a `DELETE` request with the `id` value as a path.

    DELETE /todos/91c621a3026ca8ef

You can also pass a query string to ensure that you are removing the correct object:

    DELETE /todos/91c621a3026ca8ef?title=Walk the dog

You can omit the `id` in the path if you provide it in the query string:
  
    DELETE /todos?id=91c621a3026ca8ef&title=Walk the dog

The response body will always be empty.

### Realtime API

Deployd uses [Socket.io](http://socket.io/#home) for its realtime functionality. If you are not using dpd.js, you can use the [Socket.io client library](https://github.com/LearnBoost/socket.io-client/blob/master/dist/socket.io.js). 

    var socket = io.connect('/');
    socket.on('todos:create', function(todo) {
      // Do something
    });

The Socket.io community has created client libraries for other languages and platforms as well.


### Root Requests

You can elevate your session to root access by adding the header `dpd-ssh-key`. It must have the value of your app's key (you can find this by typing `dpd showkey` into the command line); although in the `development` environment, the `dpd-ssh-key` header can have any value.

Sending a request as root has several effects. Most notably, you can use the `{$skipEvents: true}` property in either the query string or request body. This will cause events not to run. This is useful for bypassing authentication or validation. 

Your front-end app should never gain root access, and you should never store the app's key in a place where it can be accessed by users, even if they understand the system. This is primarily useful for writing data management utilities for yourself, other developers, and system administrators.

### Examples

The examples below show how to use various JavaScript front-end libraries to access a Collection called `/todos`.

#### [jQuery](http://jquery.com/)

    $.ajax('/todos', {
      type: "GET",
      success: function(todos) {
        // Do something
      },
      error: function(xhr) {
        alert(xhr.responseText);
      }
    });

    $.ajax('/todos', {
      type: "POST",
      contentType: "application/json",
      data: JSON.stringify({
        title: "Walk the dog"
      }),
      success: function(todo) {
        // Do something
      }, 
      error: function(xhr) {
        alert(xhr.responseText);
      }
    });

*Note: When providing a request body, jQuery defaults to form encoding. Deployd works best with a JSON body, so you'll need to set the contentType option and manually convert to JSON.*

#### [Backbone.js](http://backbonejs.org)

    var Todo = Backbone.Model.extend({});
    var Todos = Backbone.Collection.extend({
      model: Todo,
      url: "/todos"
    });

    var todos = new Todos();  

    todos.fetch({
      success: function(collection, response) {
        // Do something
      }, error: function(collection, response) {
        alert(response);
      }
    });

    todos.create({
      title: "Walk the dog"
    }, {
      success: function(collection, response) {
        // Do something
      }, error: function(collection, response) {
        alert(response);
      }
    });


#### [Angular.js](http://angularjs.org/)

Using [$http](http://docs.angularjs.org/api/ng.$http):
  
    function Controller($scope, $http) {
      $http.get('/todos')
        .success(function(todos) {
          $scope.todos = todos;
        })
        .error(function(err) {
          alert(err);
        });

      $http.post('/todos', {
          title: "Walk the dog"
        })
        .success(function(todo) {
          // Do something
        })
        .error(function(err) {
          alert(err);
        });
    }

Using [ngResource](http://docs.angularjs.org/api/ngResource.$resource):

    var myApp = angular.module('myApp', ['ngResource']);

    myApp.factory('Todos', function($resource) {
      return $resource('/todos/:todoId', {todoId: '@id'});
    });

    function Controller($scope, Todos) {
      $scope.todos = Todos.query(function(response) {
        // Do something
      }, function(error) {
        alert(error);
      });

      Todos.save({
        title: "Walk the dog"
      }, function(todo) {
        // Do something
      }, function(error) {
        alert(error);
      });
    }

    myApp.controller('Controller', Controller);


### Cross-Origin Requests
The most common bug when implementing a CORS client for Deploy is to include headers that are not allowed. A client must not send any custom headers besides the following:


    Origin, Accept, Accept-Language, Content-Language, Content-Type, Last-Event-ID

This will not work on browsers that do not support Cross-Origin Resource Sharing (namely Internet Explorer 7 and below).

#### Cross-Origin Requests with dpd.js
When using dpd.js, all the required CORS headers are sent by default to any domain.  You don't have to make any changes to your requests.  dpd.js takes care of it for you.

#### Cross-Origin Requests with jQuery

When using jQuery.ajax() on cross-origin requests the credentials are not sent along with the request automatically.  You have to add them to each ajax() request using the xhrFields parameter.  Here is an example  of login followed by getting some data.

	// Logging a user in.
	$.ajax({
	  url: 'http://<domain>:<port>/users/login',
	  type: "POST",
	  data: {username:"un", password:"pw"},
	  cache: false,
	  xhrFields:{
	    withCredentials: true
	  },
	  success: function(data) {
	    console.log(data);
	  },
	  error: function(xhr) {
	    console.log(xhr.responseText);
	  }
	});

	// On subsequent requests or in the success callback above.  (After having logged in) 
	$.ajax({
	  url: 'http://<domain>:<port>/<collection>',
	  type: "GET",
	  cache: false,
	  xhrFields:{
	    withCredentials: true
	  },
	  success: function(data) {
	    console.log(data);
	  },
	  error: function(xhr) {
	    console.log(xhr.responseText);
	  }
	});

### HTTP method override

Provides faux HTTP method support.

Most browsers doesn’t support methods other than “GET” and “POST” when it comes to submitting forms. So It's support something like 'Rails'.

Pass an optional key to use when checking for a method override, othewise defaults to _method. The original method is available via req.originalMethod.

It's support both URL query and POST body

    URL       : ?_method=METHOD_NAME or
    JSON body : { _method: 'METHOD_NAME' }

$.ajax({
            type: "POST",
            url : "/todos/"+ todoId,
            data: { _method:"DELETE" },
            success: function(res) {
#### Ajax Example
    $.ajax({
      type : "POST",
      url  : "/todos/OBJECT_ID"
      data : { _method:"DELETE" },
      success: function(todo) {
        // Object was deleted. response body empty.
      }, 
      error: function(xhr) {}
    });

    or

    $.ajax({
      type : "POST",
      url  : "/todos/OBJECT_ID?_method=DELETE",
      success: function(todo) {
        // Object was deleted. response body empty.
      }, 
      error: function(xhr) {}
    });


<!--{
	title: 'Querying Collections',
	tags: ['reference', 'collection']
}-->

## Querying Collections

### Simple Queries

Collections can be queried over HTTP using the query string.

This example will return all the `posts` with an author "Joe":

	GET /posts?author=Joe	


### Advanced Queries

When querying a [Collection](/docs/collections/), you can use special commands to create a more advanced query. 

Deployd supports all of [MongoDB's conditional operators](http://www.mongodb.org/display/DOCS/Advanced+Queries#AdvancedQueries-ConditionalOperators); only the common operators and Deployd's custom commands are documented here.

When using an advanced query in REST, you must pass JSON as the query string, for example:
	
	GET /posts?{"likes": {"$gt": 10}}

If you are using dpd.js, this will be handled automatically.

#### Comparison ($gt, $lt, $gte, $lte) <!-- api -->

Compares a Number property to a given value.

 - `$gt` - Greater than
 - `$lt` - Less than
 - `$gte` - Greater than or equal to
 - `$lte` - Less than or equal to

		// Finds all posts with more than 10 likes
		{
			likes: {$gt: 10}
		}

#### $ne (Not Equal) <!-- api -->

The `$ne` command lets you choose a value to exclude. 

	// Get all posts except those posted by Bob
	{
		author: {$ne: "Bob"}
	}

#### $in <!-- api -->

The `$in` command allows you to specify an array of possible matches.

	// Get articles in the "food", "business", and "technology" categories
	{
		category: {$in: ["food", "business", "technology"]}
	}

#### $regex <!-- api -->

The `$regex` command allows you to specify a [regular expression](https://developer.mozilla.org/en-US/docs/JavaScript/Guide/Regular_Expressions) to match a string property.

You can also use the `$options` command to specify regular expression flags.

	// Get usernames that might be email addresses (x@y.z)
	{
		"username": {$regex: "[a-z0-9\-]+@[a-z0-9\-]+\.[a-z0-9\-]+", $options: 'i' }
	}

### Query commands

Query commands apply to the entire query, not just a single property.

#### $fields <!-- api -->

The `$fields` command allows you to include or exclude properties from your results.

    	// Exclude the "email" property
    	{
    		$fields: {email: 0}
    	}

<!--...-->

    	// Only include the "title" property
    	{
    		$fields: {title: 1}
    	}

#### $or <!-- api -->

The `$or` command allows you to specify multiple queries for an object to match in an array.

    // Get all public posts and all posts by a specified user (even if those are private)
    {
        $or: [{
          isPublic: true
        }, {
          creator: "Bob"
        }]
    }

#### $sort <!-- api -->

The `$sort` command allows you to order your results by the value of a property. The value can be 1 for ascending sort (lowest first; A-Z, 0-10) or -1 for descending (highest first; Z-A, 10-0)

    // Sort posts by likes, descending
    {
    	$sort: {likes: -1}
    }

#### $limit <!-- api -->

The `$limit` command allows you to limit the amount of objects that are returned from a query. This is commonly used for paging, along with `$skip`.

    // Return the top 10 scores
    {
    	$sort: {score: -1},
    	$limit: 10
    }

#### $skip <!-- api -->

The `$skip` command allows you to exclude a given number of the first objects returned from a query. This is commonly used for paging, along with `$limit`. 

	// Return the third page of posts, with 10 posts per page
	{
		$skip: 20,
		$limit: 10
	}
	
#### $limitRecursion <!-- api -->

The `$limitRecursion` command allows you to override the default recursive limits in Deployd. This is useful when you want to query a very deeply nested structure of data. Otherwise you can still query nested structures, but Deployd will stop the recursion after 2 levels. See the [Collection Relationships guide](/docs/collections/relationships-between-collections.md) for more info.
<!--{
  title: 'Updating Objects in Collections',
  tags: ['reference']
}-->

## Updating Objects in Collections

When updating an object in a Collection, you can use special modifier commands to more granularly change property values. 

### $inc <!-- api -->

The `$inc` command increments the value of a given Number property.

    // Give a player 5 points
    {
      score: {$inc: 5}
    }

### $push <!-- api -->

The `$push` command adds a value to an Array property.

    // Add a follower to a user by storing their id.
    {
      followers: {$push: 'a59551a90be9abd8'}
    }

### $pushAll <!-- api -->

The `$pushAll` command adds multiple values to an Array property.

    // Add mentions of users
    {
      mentions: {
        $pushAll: ['a59551a90be9abd8', 'd0be45d1445d3809']
      }
    }

### $pull <!-- api -->

The `$pull` command removes a value from an Array property.

    // Remove a user from followers
    {
      followers: {$pull: 'a59551a90be9abd8'}
    }

*Note: If there is more than one matching value in the Array, this will remove all of them*

### $pullAll <!-- api -->

The `$pullAll` command removes multiple values from an Array property.

    // Remove multiple users
    {
      followers: {$pullAll: ['a59551a90be9abd8', 'd0be45d1445d3809']}
    }

*Note: This will remove all of the matching values from the Array*<!--{
  title: 'Relationships Between Collections with Events',
  tags: ['guide', 'collection', 'events', 'relationships']
}-->

## Relationships Between Collections with Events

Designing the relationships between the collections in your application is crucial to a useful API. In typical databases, there are very specific ways to implement the relation of objects in one table (or collection) and another. Deployd lets you relate your data however your application requires and is flexible enough to allow you to easily change the way objects are related.

### Types of Relationships

When designing the collections in your application keep in mind the following strategies for relating data. There isn't a single best way to create relationships, so you will have to take into account how data will change in your collections. 

#### Embedding Data

Deployd allows your collection to store complex structures such as nested objects or arrays. This is useful if you want to embed data inside your collection's objects. Keep in mind this is only recommended when the embedded data is not likely to change. For example, a `blog-posts` collection could have an `author` property with a type set to `Object`.

    {
      "title": "Foo Bar Bat Baz?",
      "author": {
        "name": "Joe Bob",
        "id": "5ef0f7d515764998"
      }
    }
    
This style of relationship allows users of the collection to display the name of the author without running any other queries. The downside is an update event is required to keep the author name in sync if it ever changes. If your data changes often, this may not be the best approach.

#### Contains Many or One-to-Many

Similarly to storing nested objects in your collection, you can also store arrays of arbitrary JSON. This is useful when you want to setup a **contains** relationship. For example, in a gradebook application, your `classes` collection objects could **contain** `students`.

    {
      "title": "Language Arts",
      "students": ["5ef0f7d515764998", "5ef0f7d515764531", ...] 
    }
    
By storing an array of student ids you can easily query classes by student.

    dpd.classes.get({students: '5ef0f7d515764998'}, function(classes) {
      console.log(classes); // [...] - all the classes the student is in.
    });
    

#### Many-to-Many

There are several ways to handle **many-to-many** relationships. The most common way is to include an `Array` property that stores the `id`s of the related objects on both collections.

Continuing with the gradebook example, a student may have many classes, and a class may have many students. The `classes` collection would have a `students` `Array` property containing the student ids and the `students` collection would have a classes `Array` property containing class ids.

This lets you query each collection to get the students in a class or the classes a student is taking by providing the id of the class or student.

    dpd.students.get({id: {$in: class.students}}, function(students) {
      console.log(students);
    }); 
    
    // or
    
    dpd.classes.get({id: {$in: student.classes}}, function(classes) {
      console.log(classes);
    });
    
If you wanted to include the full objects when querying the API you could implement a simple `GET` event.

    // on GET /students

    if(query.include === 'classes') {
      dpd.classes.get({id: {$in: student.classes}}, function(classes) {
        this.classes = classes;
      });
    }

Then if you added the `include` param when querying from the browser, a student would come back with all of its classes.

    dpd.students.get({id: '2ef0f7d515764991', include: 'classes'}, fn);

would output

    {
      "id": "2ef0f7d515764991",
      "name": "Joe Bob",
      "classes": [{
        "id": "...",
        "title": "Language Arts"
      }, ...]
    }
    
#### Parent-Child

Some collections contain objects related to other objects in the same collection. A simple example of this is threaded comments. Where a comment can be in reply to another comment, creating a tree-like structure when rendered.

To accomplish this, all you need is a `parent` property containing the `id` of a parent object if one exists. Since Deployd supports recursive queries in a collection's `GET` event, the following works as you would expect.

    // on GET /comments
    var comment = this;

    dpd.comments.get({parent: comment.id}, function(comments) {
      if(comments && comments.length) comment.children = comments;
    });
    
Running the following query from the browser would result in a nested structure of all possible comments:

    // from the browser
    dpd.comments.get({id: '2ef0f7d515764991'}, console.log);
    
would output

    {
      "id": "2ef0f7d515764991"
      "text": "Hello, World!",
      "children": [
        {
          "id": "tef0f7d515761234",
          "text": "Foo bar...",
          "children": [
            {
              "id": "ff00f7d515764642",
              "text": "I agree!"
            },
            {
              "id": "2200f7d51576123",
              "text": "I do not agree!"
            },
          ]
        }
      ]
    }

If you expect that a query could become an infinite loop (or if it already is an infinite loop; a good sign of this is requests that time out before returning a result), put a `$limitRecursion` property on your query with the maximum number of levels to iterate:

    // on GET /comments
    var comment = this;

    dpd.comments.get({parent: comment.id, $limitRecursion: 10}, function(comments) {
      if(comments && comments.length) comments.children = comments;
    });
<!--{
  title: 'Creating a Module',
  tags: ['modules', 'custom', 'extending']
}-->

## Creating a Module

### Background

Deployd modules are 100% compatible with regular [node modules](http://npmjs.org). This means you can use any of the 17,000+ node modules when building your Deployd app.

### Hello World

Any module in your app's `node_modules` folder will be loaded when the Deployd server starts.

You don't have to `require()` or load anything to instantiate your module. The following will log 'hello world' when you run `dpd`.

    // /my-app/node_modules/hello.js
    console.log('hello world');

### Accessing the Server

In order to do anything interesting you need a reference to the current Deployd [server](/docs/developing-modules/internal-api/server.md) object. The server is always available at `process.server`. This means you don't need to require anything to use most of the [internal APIs](/docs/developing-modules/internal-api/collection.md).

### One Off Modules

The simplest kind of module is a **one-off module**. These are easy to create but hard to reuse. Typically any behavior that is specific to just your app that can't be implemented using an existing module can be built with a simple **one-off module**.

Here's an example one off module that maintains a count of requests to the url `/hits` and writes it to a file every minute.

    // /my-app/node_modules/hits.js
    var fs = require('fs');
    process.server.hits = 0;

    process.server.on('request', function(req) {
      if(req.url === '/hits') {
        process.server.hits++;
      }
    });

    // write a file every minute
    setInterval(function() {
      fs.writeFile('hits.json', JSON.stringify({hits: process.server.hits}));
    }, 60000);

### Reusable Modules

Modules can also expose useful APIs of their own. The simplest way to create reusable modules is to define a `Resource Type`. `Resource Types` are exposed in the dashboard and are much easier to reuse, and you can share them with other Deployd developers. See the [custom resource type guide](/docs/developing-modules/custom-resource-types.md) for more info.

### Debugging

Deployd uses [debug](https://www.npmjs.com/package/debug) to log requests and show other internal debug info. To activate it you need to set the `DEBUG` env variable to `*`, for example:

    process.env['DEBUG'] = '*';
<!--{
	title: 'Creating a Custom Resource Type',
	tags: ['modules', 'custom', 'extending', 'resource', 'type']
}-->

## Creating a Custom Resource Type

Deployd modules can register new *Resource Types*, which can be created with a route and configured per instance. Deployd comes with two built-in Resource Types: "Collection" and "User Collection". You can create your own custom resource types by extending the [Resource](/docs/developing-modules/internal-api/resource.md) constructor and implementing a `handle()` method. Deployd will automatically load any Resource Types that are exported by a module.

Here is a simple custom resource type:

	var Resource = require('deployd/lib/resource')
		, util = require('util');

	function Hello(name, options) {
		Resource.apply(this, arguments);
	}
	util.inherits(Hello, Resource);
	module.exports = Hello;

	Hello.prototype.clientGeneration = true;

	Hello.prototype.handle = function (ctx, next) {
		if(ctx.req && ctx.req.method !== 'GET') return next();

		ctx.done(null, {hello: 'world'});
	}

This will allow you to add a "Hello" resource in the Dashboard. This resource will respond to every GET request with `{"hello": "world"}`.

### Example Resource Type

The most basic Custom Resource Type that is useful is the [Event Resource](/docs/using-modules/official/event.md), which will simply execute an `On GET` event when it receives a `GET` request and an `On POST` event when it receives a `POST` request.

 This is the source for that module: 

	var Resource = require('deployd/lib/resource')
		, util = require('util');

	function EventResource() {
		Resource.apply(this, arguments);
	}
	util.inherits(EventResource, Resource);

	EventResource.label = "Event";
	EventResource.events = ["get", "post"];

	module.exports = EventResource;

	EventResource.prototype.clientGeneration = true;

	EventResource.prototype.handle = function (ctx, next) {
		var parts = ctx.url.split('/').filter(function(p) { return p; });

		var result = {};

		var domain = {
				url: ctx.url
			, parts: parts
			, query: ctx.query
			, body: ctx.body
			, 'this': result
			, setResult: function(val) {
				result = val;
			}
		};

		if (ctx.method === "POST" && this.events.post) {
			this.events.post.run(ctx, domain, function(err) {
				ctx.done(err, result);
			});
		} else if (ctx.method === "GET" && this.events.get) {
			this.events.get.run(ctx, domain, function(err) {
				ctx.done(err, domain.result);
			});
		} else {
			next();
		}
	};

Let's look at it line-by-line:

	var Resource = require('deployd/lib/resource')
		, util = require('util');

 To create a Resource, you'll need the [Resource](/docs/developing-modules/internal-api/resource.md) module and Node's [util](http://nodejs.org/api/util.html) module.

	function EventResource() {
		Resource.apply(this, arguments);
	}

Creates the constructor for the `EventResource`, also applying the base `Resource` constructor. 

	util.inherits(EventResource, Resource);

Causes `EventResource` to inherit its prototype from `Resource` using Node's [util.inherits()](http://nodejs.org/api/util.html#util_util_inherits_constructor_superconstructor) function.

	EventResource.label = "Event";

Changes the [Resource.label](/docs/developing-modules/internal-api/resource.md#s-Resource.label) property to set how the `EventResource` appears in the "Add Resource" menu in the Dashboard. Without this setting, it would appear using the constructor name, `EventResource`.

	EventResource.events = ["get", "post"];

Configures two [events](/docs/developing-modules/internal-api/resource.md#s-Resource.events) for the Resource type: `get` and `post`. These will appear on the "Events" page in the Dashboard with no extra configuration. 

*Note: The Dashboard provides the "On" prefix, e.g. "On Get"*

	module.exports = EventResource;

Exports the `EventResource` constructor. This is how Deployd finds and loads the resource type.

	EventResource.prototype.clientGeneration = true;

Sets the [clientGeneration](/docs/developing-modules/internal-api/resource.md#s-resource.clientGeneration) flag, which ensures that resources created with this resource type will be generated into dpd.js.

	EventResource.prototype.handle = function (ctx, next) {

Defines a [handle()](/docs/developing-modules/internal-api/resource.md#s-resource.handle-ctx-next) function. This function will be called whenever a request is routed to this resource. The `ctx` object is a [Context](/docs/developing-modules/internal-api/context.md), which includes useful properties ([body](/docs/developing-modules/internal-api/context.md#s-ctx.body), [query](/docs/developing-modules/internal-api/context.md#s-ctx.query), etc.) and functions (particularly [done()](/docs/developing-modules/internal-api/context.md#s-ctx.done-err-result)) to simplify working with HTTP.

The `next` function gives control back to the router.

	var parts = ctx.url.split('/').filter(function(p) { return p; });

	var result = {};

Set up some local variables; `parts` is an array of the `/`-separated parts in the URL.

	var domain = {
			url: ctx.url
		, parts: parts
		, query: ctx.query
		, body: ctx.body
		, 'this': result
		, setResult: function(val) {
			result = val;
		}
	};

Create a *domain* for the events. These are objects and functions that will be accessible from the event. Notice that the `setResult` function is a closure that assigns its argument to the local `result` variable.

	if (ctx.method === "POST" && this.events.post) {
		this.events.post.run(ctx, domain, function(err) {
			ctx.done(err, result);
		});
	}

Run the `POST` event using the [Script.run()](/docs/developing-modules/internal-api/script.md#s-script.run-ctx-domain-[fn]) function if applicable, passing it the current context and domain. 

The [this.events](/docs/developing-modules/internal-api/resource.md#s-Resource.events) object contains all of the available events; if the user has not written a `POST` event, though, `this.events.post` might be `null`.

The callback for `Script.run` returns an error `err` if something went wrong in the script (or if the script writer called [cancel()](/docs/using-modules/reference/event-api.md#s-cancel))

Finally, call [ctx.done()](/docs/developing-modules/internal-api/context.md#s-ctx.done-err-result) with both the error and result (`result` is the local variable we set up earlier which the scriptwriter can change using `setResult()`. The response body is always the second parameter, but it is ignored if an error is passed.

	} else if (ctx.method === "GET" && this.events.get) {
		this.events.get.run(ctx, domain, function(err) {
			ctx.done(err, domain.result);
		});
	}

Do the same thing for the `GET` event.

	} else {
		next();
	}

If no event applies, call `next()`. This tells the router that this resource cannot handle the current request, and the router will allow other resources to handle it. If every resource calls `next()`, then Deployd will return a `404` status code.<!--{
  title: 'Email Resource',
  tags: ['example', 'module', 'event']
}-->

## Email Resource Type

This module demonstrates how to use a Node module such as [Nodemailer](https://github.com/andris9/Nodemailer) to make a reusable resource type.

For information on how to use this module in your app, see the [Email Resource documentation](/docs/using-modules/official/email.md).

<a href="https://github.com/deployd/dpd-email/archive/master.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/dpd-email" class="btn">View Source</a>

### Useful files

- [index.js](https://github.com/deployd/dpd-email/blob/master/index.js)<!--{
  title: 'Event Resource',
  tags: ['example', 'module', 'event']
}-->

## Event Resource Type

This module demonstrates how to run user-defined Events in your resource. See the [Creating Custom Resource Types](/docs/developing-modules/custom-resource-types.md#s-Example-Resource-Type) page for an analysis of the source.

For information on how to use this module in your app, see the [Event Resource documentation](/docs/using-modules/official/event.md).

<a href="https://github.com/deployd/dpd-event/archive/master.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/dpd-event" class="btn">View Source</a>

### Useful files

- [index.js](https://github.com/deployd/dpd-event/blob/master/index.js)<!--{
  title: 'S3 Bucket Resource',
  tags: ['example', 'module', 'event']
}-->

## S3 Bucket Resource Type

This module demonstrates how to receive file uploads in a custom resource type.

For information on how to use this module in your app, see the [S3 Bucket Resource documentation](/docs/using-modules/official/s3.md).

<a href="https://github.com/deployd/dpd-s3/archive/master.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/dpd-s3" class="btn">View Source</a>

### Useful files

- [index.js](https://github.com/deployd/dpd-s3/blob/master/index.js)<!--{
  title: 'Collection Resource Type',
  tags: ['collection', 'resource', 'type']
}-->

## Collection Resource Type

Collections are the most common Resource Type in Deployd. They allow the user to store and load data from their app's [Store](/docs/developing-modules/internal-api/store.md). Behind the scenes, they validate incoming requests and execute event scripts for `get`, `post`, `put`, `delete`, and `validate`. If all event scripts execute without error (or `cancel()`ing), the request is proxied to the collection's `Store`.

### Class: Collection

A `Collection` inherits from `Resource`. Any constructor that inherits from `Collection` must include its own `Collection.external` prototype object.

Example inheriting from `Collection`:

    var Collection = require('deployd/lib/resources/collection');
    var util = require('util');

    function MyCollection(name, options) {
      Collection.apply(this, arguments);
    }
    MyCollection.external = Collection.external;

    util.inherits(MyCollection, Collection);

### collection.store <!-- api -->

* {Store}

The backing persistence abstraction layer. Supports saving and reading data from a database. See [Store](/docs/developing-modules/internal-api/store.md) for more info.

### collection.validate(body, create) <!-- api -->

Validate the request `body` against the Collection's properties
and return an object containing any `errors`.

* `body` {Object}

The object to validate

* `create` {Boolean}

Should validate a new object being created

* return `errors` {Object}

### collection.sanitize(body) <!-- api -->

Sanitize the request `body` against the Collection's properties 
object and return an object containing only properties that exist in the
`collection.config.properties` object.

* `body` {Object}
* return `sanitized` {Object}

### collection.sanitizeQuery(query) <!-- api -->

Sanitize the request `query` against the `collection.properties` 
and return an object containing only properties that exist in the
`collection.properties` object.

* `query` {Object}
* return `sanitizedQuery` {Object}

### collection.parseId(ctx) <!-- api -->

Parse the `ctx.url` for an id. Override this to change how an object's id is parsed out of a url.

* `ctx` {Context}

### collection.find(ctx, fn) <!-- api -->

Find all the objects in a collection that match the given `ctx.query`. Then execute a `get` event script, if one exists, using each object found. Finally call `fn(err)` passing an `error` if one occurred.

* `ctx` {Context}
* `fn(err)`

### collection.remove(ctx, fn) <!-- api -->

Execute a `delete` event script, if one exists, using each object found. Then remove a single object that matches the `ctx.query.id`. Finally call `fn(err)` passing an `error` if one occurred.

* `ctx` {Context}
* `fn(err)`

### collection.save(ctx, fn) <!-- api -->

First execute a `validate` event script if one exists. If the event does not error, try to save the `ctx.body` into the store. If `ctx.body.id` exists, perform an `update` and execute the `put` event script. Otherwise perform an `insert` and execute the `post` event script. Finally call `fn(err)`, passing an `error` if one occurred.

* `ctx` {Context}
* `fn(err)`




<!--{
  title: 'Context',
  tags: ['context', 'http', 'req', 'res', 'query', 'url']
}-->

## Context

Contexts are a thin abstraction between http requests, `Resource`s, and `Script`s. They provide utility methods to simplify interacting with node's [http.ServerRequest](http://nodejs.org/api/http.html#http_class_http_serverrequest) and [http.ServerResponse](http://nodejs.org/api/http.html#http_class_http_serverresponse) objects.

A `Context` is built from a request and response and passed to a matching `Resource` by the `Router`. This might originate from an external http request or a call to an **internal client** from a `Script`.

### Mock Contexts

Contexts may be created without a real request and response such as during an internal request using the `dpd` object. See [Internal Client](/docs/developing-modules/internal-api/internal-client.md) for more info.

### Class: Context

    var Context = require('deployd/lib/context');
    var ctx = new Context(resource, req, res, server);

#### ctx.done(err, result) <!-- api -->

Continuous callback sugar for easily calling `res.end()`. Conforms to the idiomatic callback signature for most node APIs. It can be passed directly to most APIs that require a callback in node.

    fs.readFile('bar.txt', ctx.done);

* `err` {Error | Object}

An error if one occurred during handling of the `ctx`. Otherwise it should be `null`.

* `result` {Object}

The result of executing the `ctx`. This should be an object that is serializable as JSON.

#### ctx.body <!-- api -->

* {Object}

The body of the request if sent as `application/json` or `application/x-www-form-urlencoded`.

#### ctx.query <!-- api -->

* {Object}

The query string of the request serialized as an `Object`. Supports both `?key=value` as well as `?{"key":"value"}`.

#### ctx.method <!-- api -->

* {Object}

An alias to the request's method.
<!--{
  title: 'Internal Client',
  tags: ['dpd', 'internal', 'client', 'resources']
}-->

## Internal Client

The `internal-client` module is responsible for building a server-side version of **dpd.js**. It is intended for use in `Script`s but can be used by resources to access other resources' REST APIs.

*Note: As in dpd.js, the callback for an internal client request receives the arguments `(data, err)`, which is different than the Node convention of `(err, data)`.*

### internalClient.build(server, [session], [stack])

    var internalClient = require('deployd/lib/internal-client');

    process.server.on('listening', function() {
      var dpd = internalClient.build(process.server);
      dpd.todos.get(function(data, err) {
        // Do something
      });  
    });

* `server` {Server}

The Deployd server to build a client for. 

* `session` {Session} *(optional)*

The `Session` object on the current request.

* `stack` {Array} *(optional)*

Used internally to prevent recursive calls to resources.

### Mock context

In order to make requests on resources within the Deployd server, `internal-client` creates mock `req` and `res` objects. These objects are not Streams and cannot be treated exactly like the standard `http.ServerRequest` and `http.ServerResponse` objects in Node, but they imitate their interfaces with the following properties:

#### req

* `url` {String}

The URL of the request, i.e. "/hello"

* `method` {String}

The method of the request, i.e. "GET", "POST"

* `query` {Object}

The query object.

* `body` {Object}

The body of the request.

* `session` {Session}

The current session, if any.

* `internal` {Boolean}

Always equal to `true` to indicate an internal request and a mock `req` object.

#### res

* `statusCode` {Number}

Set this to a standard HTTP response code.

* `setHeader()` {Function}

No-op.

* `end(data)` {Function}

Returns data to the internal client call. If `data` is JSON, it will be parsed into an object, otherwise it will simply be passed as a string. If the `res.statusCode` is not 200 or 204, `data` will be passed as an error.

* `internal` {Boolean}

Always equal to `true` to indicate an internal request and a mock `res` object.<!--{
  title: 'Resource Types',
  tags: ['resource', 'type']
}-->

## Resource Types

Resources are the building block of a Deployd app. They provide a way to handle http requests at a root url. They must implement a `handle(ctx, next)` method that either handles a request or calls `next()` to give the request back to the router.

Resources can also be attributed with meta-data to allow the dashboard to dynamically render an editor gui for configuring a resource instance.

### Events / Scripts

A `Resource` can execute `Script`s during the handling of an http request when certain events occur. This allows users of the resource to inject logic during specific events during an http request without having to extend the resource or create their own.

For example, the `Collection` resource executes the *get.js* event script when it retrieves each object from its store. If a *get.js* file exists in the instance folder of a resource (eg. `/my-project/resources/my-collection/get.js`), it will be pulled in by the resource and exposed as `myResource.scripts.get`.

### Class: Resource <!-- ref -->

A `Resource` inherits from `EventEmitter`. The following events are available.

 - `changed`      after a resource config has changed
 - `deleted`      after a resource config has been deleted

Inheriting from Resource:

    var Resource = require('deployd/lib/resource')
      , util = require('util');
      
    function MyResource(name, options) {
      // run the parent constructor
      // before using any properties/methods
      Resource.apply(this, arguments);
    }
    util.inherits(MyResource, Resource);
    module.exports = MyResource;

* `name` {String}

The name of the resource.

* `options` {Object}

 - `configPath`        the project relative path to the resource instance
 - `path`              the base path a resource should handle
 - `db` *(optional)*   the database a resource will use for persistence
 - `config`            the instance configuration object
 - `server`            the server object

The following resource would respond with a file at the url `/my-file.html`.

    function MyFileResource(name, options) {
      Resource.apply(this, arguments);

      this.on('changed', function(config) {
        console.log('MyFileResource changed', config);
      });
    }
    util.inherits(MyFileResource, Resource);

    MyFileResource.prototype.handle = function (ctx, next) {
      if (ctx.url === '/my-file.html') {
        fs.createReadStream('my-file.html').pipe(ctx.res);
      } else {
        next();
      }
    }



### Overriding Behavior

Certain methods on a `Resource` prototype are called by the runtime. Their default behavior should be overridden to define an inherited `Resources` behavior.

### resource.handle(ctx, next) <!-- api -->

Handle an incoming request. This gets called by the router.

The resource can either handle this context and call `ctx.done(err, obj)` with an error or result JSON object, or call `next()` to give the context back to the router. If a resource calls `next()` the router might find another match for the request, or respond with a `404`.

* ctx {[Context](/docs/developing-modules/internal-api/context.md)}

The http context created by the `Router`. This provides an abstraction between the actual request and response. A `Resource` should call `ctx.done` or pipe to `ctx.res` if it can handle a request. Otherwise it should call `next()`.

Override the handle method to return a string:

    function MyResource(settings) {
      Resource.apply(this, arguments);
    }
    util.inherits(MyResource, Resource);

    MyResource.prototype.handle = function (ctx, next) {
      // respond with the file contents (or an error if one occurs)
      fs.readFile('myfile.txt', ctx.done);
    }
    
### resource.load(fn) <!-- api -->

Load any dependencies and call `fn(err)` with any errors that occur. This is automatically called by the runtime to support asynchronous construction of a resource (such as loading files).

*Note: If this method is overridden, the super method must be called to support loading of the `MyResource.events` array.*

### resource.clientGeneration <!-- api -->

If `true`, ensures that this resource is included in `dpd.js`.

    MyResource.prototype.clientGeneration = true;

### resource.config <!-- api -->

The instance configuration object; used to access the resource's configuration from member functions.

    MyResource.prototype.handle = function (ctx, next) {
      fs.readFile(this.config.filePath, ctx.done);
    }

### External Prototype  <!-- ref -->

This is a special type of prototype object that is used to build the `dpd` object. Each function on the `Resource.external` prototype `Object` are exposed externally in two places

 1. To the generated `dpd.js` browser JavaScript client
 2. To the `Context.dpd` object generated for inter-resource calls
    
Here is an example of a simple resource that exposes a method on the external prototype.

`/my-project/node_modules/example.js`

    var util = require('util');
    var Resource = require('deployd/lib/resource');
    function Example(name, options) {
      Resource.apply(this, arguments);
    }
    util.inherits(Example, Resource);

    Example.external = {};

    Example.external.hello = function(options, ctx, fn) {
      console.log(options.msg); // 'hello world'
    }

When the `hello()` method is called, a context does not need to be provided as the `dpd` object is built with a context. A callback may be provided which will be executed with results of `fn(err, result)`.

`/my-project/public/hello.js`

    dpd.example.hello({msg: 'hello world'});
    
`/my-project/resources/other-resource/get.js`

    dpd.example.hello({msg: 'hello world'});

### Resource.events <!-- api -->

* {Array}

If a `Resource` constructor includes an array of events, it will try to load the scripts in its instance folder (eg. `/my-project/resources/my-resource/get.js`) using [resource.loadScripts(eventNames, fn)](#s-resource.load-fn).

    MyResource.events = ['get'];
    
This will be available to each instance of this resource as `this.events`. 

`/my-project/node_modules/my-resource.js`

    MyResource.prototype.handle = function(ctx, next) {
      if(this.events && this.events.get) {
        var domain = {
          say: function(msg) {
            console.log(msg); // 'hello world'
          }
        }
        this.events.get.run(ctx, domain, ctx.done);
      }
    }

`/my-project/resources/my-resource/get.js`

    say('hello world');

### Resource.label <!-- api -->

The resource type's name as it appears in the dashboard. If this is not set, it will appear with its constructor name.

    Hello.label = 'Hello World';

### Resource.defaultPath <!-- api -->

The default path suggested to users creating a resource. If this is not set, it will use the constructor's name in lowercase.

    Hello.defaultPath = '/hello-world'; 

### Collection.basicDashboard <!-- api -->

Set this property to an object to create a custom configuration page for your resource type.

- `settings` - An array of objects describing which properties to display. 
- `name` - The name of the property. This is how the value will be passed into the `config` object, so make sure it's something JavaScript-friendly, e.g. `maxItems`.
- `type` - The type of control to edit this property. Allowed types are `text`, `textarea`, `number`, and `checkbox`.
- `description` (Optional) - Explanatory text to appear below the field.

<!-- separate -->

    Hello.basicDashboard = {
      settings: [{
          name: 'propertyName',
          type: 'text',
          description: "This description appears below the text field"
      }, {
          name: 'longTextProperty',
          type: 'textarea'
      }, {
          name: 'numericProperty',
          type: 'number'
      }, {
          name: 'booleanProperty',
          type: 'checkbox'
      }]
    };

The above sample will produce the following dashboard page:

![Example basic dashboard](/images/basic-dashboard.png)

### Collection.dashboard <!-- api -->

A resource can describe the dependencies of a fully custom dashboard editor UI. This will be passed to the dashboard during rendering to create a custom UI.

This example creates the custom dashboard for the `Collection` resource. It automatically includes pages and page-specific scripts:

    Collection.dashboard = {
        path: path.join(__dirname, 'dashboard')
      , pages: ['Properties', 'Data', 'Events', 'API']
      , scripts: [
          '/js/ui.js'
        , '/js/util.js'
      ]
    }

* `path` {String}

The absolute path to this resource's dashboard

* `pages` {Array} *(optional)*

An array of pages to appear in the sidebar. If this is not provided, the only page available will be "Config" (and "Events", if `MyResource.events` is set).

The dashboard will load content from `[current-page].html` and `js/[current-page].js`.

*Note: The "Config" page will load from `index.html` and `js/index.js`.*

* `scripts` {Array} *(optional)*

An array of extra JavaScript files to load with the dashboard pages.

#### Dashboard asset loading <!-- ref -->

When you request a page from a custom dashboard, it will load the following files, if they are available, from the `dashboard.path`:

 - `[current-page].html`
 - `js/[current-page].js`
 - `style.css`

The default page is `index`; the `config` page will also redirect to `index`. 

The `config` or `index` page will load the basic dashboard if no `index.html` file is provided.
The `events` page will load the default event editor if no `events.html` file is provided.

It will also load the JavaScript files in the `dashboard.scripts` property.

#### Creating a custom dashboard

##### Event editor control <!-- ref -->

To embed the event editor in your dashboard, include this empty div:
  
    <div id="event-editor" class="default-editor"></div>

##### Styling <!-- ref -->

For styling, the dashboard uses a re-skinned version of [Twitter Bootstrap 2.0.2](http://twitter.github.com/bootstrap/). 

##### JavaScript <!-- ref -->

The dashboard provides several JavaScript libraries by default:

- [jQuery 1.7.2](http://jquery.com/)
- [jquery.cookie](https://github.com/carhartl/jquery-cookie/)
- [Underscore 1.3.3](http://underscorejs.org/)
- [Twitter Bootstrap 2.0.2](http://twitter.github.com/bootstrap/javascript.html)
- [UIKit](http://visionmedia.github.com/uikit/)
- [Ace Editor](https://github.com/ajaxorg/ace) (no-conflict version)
    - JavaScript mode
    - JSON mode
    - Custom theme for the Dashboard (`ace/theme/deployd`)
- [Google Code Prettify](http://code.google.com/p/google-code-prettify/)
- dpd.js
    - *Note:* all dpd.js requests will be sent as [root](/docs/collections/reference/http.md#s-root-requests)

Within the dashboard, a `Context` object is available:

    //Automatically generated by Deployd:
    window.Context = {
      resourceId: '/hello', // The id of the current resource
      resourceType: 'Hello', // The type of the current resource
      page: 'properties', // The current page, in multi-page dashboards
      basicDashboard: {} // The configuration of the basic dashboard
    };

You can use this to query the current resource:

    dpd(Context.resourceId).get(function(result, err) {
      //Do something
    });

In the dashboard, you also have access to the special `__resources` resource, which lets you update your app's configuration files:

    // Get the config for the current resource
    dpd('__resources').get(Context.resourceId, function(result, err) {
      //Do something
    });
    
    // Set a property for the current resource
    dpd('__resources').put(Context.resourceId, {someProperty: true}, function(result, err) {
      //Do something
    });
    
    // Set all properties for the current resource, deleting any that are not provided
    dpd('__resources').put(Context.resourceId, {someProperty: true, $setAll: true}, function(result, err) {
      //Do something
    });
    
    // Save another file, which will be loaded by the resource
    dpd('__resources').post(Context.resourceId + '/content.md', {value: "# Hello World!"}, function(result, err)) {
      //Do something
    });<!--{
  title: 'Event Scripts',
  tags: ['event', 'scripts']
}-->

## Event Scripts

A `Script` provides a mechanism to run JavaScript source in a sandbox. A `Script` is executed with a `Context` and a `domain` object using [the node vm module](http://nodejs.org/api/vm.html). Each `Script` runs independently. They do not share global scope or state with other scripts or modules.

### Async Mode

Scripts can be run in an **async mode**. This mode is triggered when a `Script` is `run(ctx, domain, fn)` with a callback (`fn`). When run in this mode a `Script` will try scrub all functions in the domain for operations that require a callback. If a callback is required, the function is re-written to count the callbacks completion and notify the script. When all pending callbacks are complete the script is considered finished.

### Async Errors

If a script is run with a callback (in **async mode**), any error will emit an internal `error` event. This will stop the execution of the script and pass the error to the script's callback.

### Class: Script

    var Script = require('deployd/lib/script');
    var script = new Script('hello()', 'hello.js');

A `Script`'s source is compiled when its constructor is called. It can be `run()` many times with independent `Context`s and `domain`s.

### script.run(ctx, domain, [fn]) <!-- api -->

* ctx {Context}

A `Context` with a `session`, `query`, `req` and `res`.

* domain {Object}

An `Object` containing functions to be injected into the `Script`s sandbox. This will override any existing functions or objects in the `Script`s sandbox / global scope.

This example `domain` provides a log function to a script.

    var script = new Script('log("hello world")');
    var context = {};
    var domain = {};
    var msg;

    domain.log = function(str) {
      console.log(msg = str);
    }

    script.run(ctx, domain, function(err) {
      console.log(msg); // 'hello world'
    });

* fn(err) *optional*

If a callback is provided the script will be run in **async mode**. The callback will receive any error even if the error occurs asynchronously. Otherwise it will be called without any arguments when the script is finished executing (see: async mode).

    var s = new Script('setTimeout(function() { throw "test err" }, 22)');
  
    // give the script access to setTimeout
    var domain = {setTimeout: setTimeout};
  
    s.run({}, domain, function (e) {
      console.log(e); // test err
    });
    
### Script.load(path, fn) <!-- api -->

* `path` {String}

* `fn(err, script)`

Load a new `script` at the given file `path`. Runs the callback with an error if one occurred, or a new `Script` loaded from the contents of the file.
    
### Default Domain

Scripts are executed with a default sandbox and set of domain functions. These are functions that every `Script` usually needs, and are available to every `Script`. These can be overridden by passing a value such as `{cancel: ...}` in a `domain`. See [Event API for Custom Resources](/docs/using-modules/reference/event-api.md) for documentation on this default domain.
<!--{
  title: 'Server',
  tags: ['resource', 'type']
}-->

## Server

Deployd's `Server` extends node's `http.Server`. A `Server` is created with an options object that tells Deployd what port to serve on and which database to connect to.

The `Server` object is also the main entry point for modules. After it is started, the `Server` instance is available at `process.server`.

### Class: Server

Servers are created when calling the Deployd exported function.

    var deployd = require('deployd')
      , options = {port: 3000}
      , server = deployd(options);

* `options` {Object}

  - `port` {Number} - the port to listen on
  - `db` {Object} - the database to connect to
    - `db.connectionString` {String} - The URI of the mongoDB using [standard Connection String](http://docs.mongodb.org/manual/reference/connection-string/). If `db.connectionString` is set, the other db options are ignored.
    - `port` {Number} - the port of the database server
    - `host` {String} - the ip or domain of the database server
    - `name` {String} - the name of the database
    - `credentials` {Object} - credentials for the server
      - `username` {String}
      - `password` {String}
  - `env` {String} - the environment to run in.

*Note:* If `options.env` is "development", the dashboard will not require authentication and configuration will not be cached. Make sure to change this to "production" or something similar when deploying.

### Server.listen([port], [host]) <!-- api -->

Load any configuration and start listening for incoming connections.

    var dpd = require('deployd')
      , server = dpd()

    dpd.listen();
    dpd.on('listening', function() {
      console.log(server.options.port); // 2403
    });

### Server.createStore(namespace)  <!-- api -->

Create a new `Store` for persisting data using the database info that was passed to the server when it was created.

    // Create a new server
    var server = new Server({port: 3000, db: {host: 'localhost', port: 27015, name: 'my-db'}});

    // Attach a store to the server
    var todos = server.createStore('todos');

    // Use the store to CRUD data
    todos.insert({name: 'go to the store', done: true}, ...); // see `Store` for more info

### Server.sockets <!-- api -->

The **socket.io** sockets `Manager` object ([view source](https://github.com/LearnBoost/socket.io/blob/master/lib/manager.js)).

### Server.sessions <!-- api -->

The server's [SessionStore](/docs/developing-modules/internal-api/session-store.md).

### Server.router <!-- api -->

The server's `Router`.

### Server.resources <!-- api -->

An `Array` of the server's [Resource](/docs/developing-modules/internal-api/resource.md) instances. These are built from the config and type loaders.


## deployd.attach

deployd.attach can attach Server Class functions into a regular http server. It also provide `handleRequest` function to act as express middleware.

    var deployd = require('deployd')
      , options = {}
      , server = require('http').createServer(app)
      , server = deployd.attach(server, options);

* `options` {Object}

  - `socketIo` {Object} - socket.io instance
  - `db` {Object} - the database to connect to
    - `port` {Number} - the port of the database server
    - `host` {String} - the ip or domain of the database server
    - `name` {String} - the name of the database
    - `credentials` {Object} - credentials for the server
      - `username` {String}
      - `password` {String}
  - `env` {String} - the environment to run in.

*Note:* If `options.env` is "development", the dashboard will not require authentication and configuration will not be cached. Make sure to change this to "production" or something similar when deploying.
<!--{
  title: 'Session Store',
  tags: ['session', 'store', 'users']
}-->

## Session Store

Sessions are persisted in a modified store. This store has several methods to help create and manage sessions.

### Class: SessionStore

A store for persisting sessions in-between connection and disconnection. Automatically creates session IDs on inserted objects.

    var db = process.server.db;
    var sockets = process.server.sockets;
    var name = 'sessions';
    var store = new SessionStore(name, db, sockets);
    
* `name` {String} 

The name of the db store.

* `db` {Db} 

The server db instance

* `sockets` {Socket.IO.sockets} 

The socket.io `sockets` object.

#### SessionStore.createSession(sid, fn) <!-- api -->

* `sid` {String} *optional*

An existing session id.

* `fn(err, session)` {Function}

Called once the session has been created.

<!--{
  title: 'Session',
  tags: ['session', 'sockets', 'authenticaiton', 'auth']
}-->

## Session

An in-memory representation of a client or user connection that can be saved to disk. Data will be passed around via a [Context](/docs/developing-modules/internal-api/context.md) to resources.

### Class: Session

A store for persisting sessions in-between connection and disconnection. Automatically creates session IDs on inserted objects.

    var session = new Session({id: 'my-sid', new SessionStore('sessions', db)});
    session.set({uid: 'my-uid'}).save();

    
* `data` {Object} 

The data used to construct the session.

* `store` {SessionStore} 

The store used to persist the session.

* `sockets` {Socket.IO.sockets} 

The Socket.IO sockets object used to attach an existing socket.

#### Session.set(changes) <!-- api -->

* `changes` {Object} 

An object containing changes to the session's data.

#### Session.save(fn) <!-- api -->

* `fn(err, data)` {Function} *optional*

Save the in memory representation of a session to its store.

#### Session.fetch(fn) <!-- api -->

* `fn(err, data)` {Function} *optional*

Reset the session using the data persisted in its store.

#### Session.remove(fn) <!-- api -->

* `fn(err, data)` {Function} *optional*

Remove the session.

#### Session.emitToAll(event, data) <!-- api -->

* `event` {String}

The event to emit to all session's sockets.

* `data` {Object} *optional*

The data to send to sockets listening to the given event.

#### Session.emitToUsers(collection, query, event, data) <!-- api -->

* `collection` {Collection}

The user-collection instance (eg. dpd.todos) to use to find users.

* `query` {Object}

Only emit the event to users that match this query.

* `event` {String}

The event to emit to all session's sockets.

* `data` {Object} *optional*

The data to send to sockets listening to the given event.<!--{
  title: 'Store',
  tags: ['db', 'store', 'createStore']
}-->

## Store

An abstraction of a collection of objects in a database. Collections are HTTP wrappers around a `Store`. You can access or create a store the same way.

    var myStore = process.server.createStore('my-store');

### Class: Store

You shouldn't construct `Store`s directly. Instead use the [process.server.createStore()](/docs/developing-modules/internal-api/server.md#s-Server.createStore-namespace) method.

#### Store.insert(object, fn) <!-- api -->

* `object` {Object}

The data to insert into the store.

* `fn(err, result)` {Function}

Called once the insert operation is finished.

#### Store.count(query, fn) <!-- api -->

* `query` {Object}

Only count objects that match this query.

* `fn(err, count)` {Function}

Called once the count operation is finished. `count` is a number.

#### Store.find(query, fn) <!-- api -->

* `query` {Object}

Only returns objects that match this query.

* `fn(err, results)` {Function}

Called once the find operation is finished.

#### Store.first(query, fn) <!-- api -->

* `query` {Object}

* `fn(err, result)` {Function}

Find the first object in the store that match the given query.

#### Store.update(query, changes, fn) <!-- api -->

* `query` {Object}

* `changes` {Object}

* `fn(err, updated)` {Function}

Update an object or objects in the store that match the given query only modifying the values in the given changes object.

#### Store.remove(query, fn) <!-- api -->

* `query` {Object}

* `fn(err, updated)` {Function}

Remove an object or objects in the store that match the given query.

#### Store.rename(name, fn) <!-- api -->

* `name` {String}

* `fn(err)` {Function}

Rename the store.


<!--{
  title: 'Using Deployd as a Node.js Module',
  tags: ['node', 'module', 'server']
}-->

## Using Deployd as a Node.js Module

Deployd is a node module and can be used inside other node programs or as the basis of an entire node program.

### Installing

For an app in your current directory:

    npm install deployd

You can also install globally:

    npm install deployd -g

### Hello World

Here is a simple *hello world* using Deployd as a node module.

    // hello.js
    var deployd = require('deployd')
      , options = {port: 3000};

    var dpd = deployd(options);

    dpd.listen();

Run this like any other node program.

    node hello.js

### Server Options <!-- ref -->

- **port** {Number} - the port to listen on
- **db** {Object} - the database to connect to
 - **db.connectionString** {String} - The URI of the mongoDB using [standard Connection String](http://docs.mongodb.org/manual/reference/connection-string/). If `db.connectionString` is set, the other db options are ignored.
 - **db.port** {Number} - the port of the database server
 - **db.host** {String} - the ip or domain of the database server
 - **db.name** {String} - the name of the database
 - **db.credentials** {Object} - credentials for db
  - **db.credentials.username** {String}
  - **db.credentials.password** {String}
- **env** {String} - the environment to run in.

*Note: If options.env is "development", the dashboard will not require authentication and configuration will not be cached. Make sure to change this to "production" or something similar when deploying.*

### Caveats

- Deployd mounts its server on `process.server`. This means you can only run one Deployd server in a process.
- Deployd loads resources from the `process.cwd`. Add this to ensure you are in the right directory: `process.chdir(__dirname)`.
- In order to access the `/dashboard` without a key you must run Deployd with the `env` option set to `development`.
<!--{
  title: 'Building a custom run script in Node.js',
  tags: ['node', 'module', 'server', 'deployment']
}-->

## Building a custom run script in Node.js

When running in non-local environments we recommend using a simple node script to start your deployd server. With each environment using its own script, you can easily separate out environmental variables (such as connection information) and actions (such as clearing out a test database).

### Example - Production

    // production.js
    var deployd = require('deployd');

    var server = deployd({
      port: process.env.PORT || 5000,
      env: 'production',
      db: {
        host: 'my.production.mongo.host',
        port: 27105,
        name: 'my-db',
        credentials: {
          username: 'username',
          password: 'password'
        }
      }
    });

    server.listen();

    server.on('listening', function() {
      console.log("Server is listening");
    });

    server.on('error', function(err) {
      console.error(err);
      process.nextTick(function() { // Give the server a chance to return an error
        process.exit();
      });
    });

### Example - Staging

    // staging.js
    var deployd = require('deployd');

    var server = deployd({
      port: process.env.PORT || 5000,
      env: 'staging',
      db: {
        host: 'my.production.mongo.host',
        port: 27105,
        name: 'my-db',
        credentials: {
          username: 'username',
          password: 'password'
        }
      }
    });

    // remove all data in the 'todos' collection
    var todos = server.createStore('todos');
      
    todos.remove(function() {
      // all todos removed
      server.listen();
    });

    server.on('error', function(err) {
      console.error(err);
      process.nextTick(function() { // Give the server a chance to return an error
        process.exit();
      });
    });
    
### Running Your App in Production

To run your app as a daemon, use the `forever` module. You can install it from npm.

    npm install forever -g
    
Then start the appropriate run script based on your environment.

    forever start production.js
    
This will daemonize your app and make sure it runs even if it crashes.<!--{
  title: 'Using grunt or gulp with Deployd',
  tags: ['grunt', 'gulp', 'package.json']
}-->

## Using grunt or gulp with Deployd

By default, Deployd will load all npm modules found in `node_modules`. This can be problematic if you want to use Grunt, gulp or other development tools: Deployd will try to load them since they are inside the `node_modules`folder and will fail.  
To avoid that, you can add a package.json and let Deployd know which dependencies to load.


Inside `devDependencies`, you can add your grunt/gulp plugins and inside `dependencies`, add the dpd modules you need.


Example:  

    "dependencies": {
      "deployd": "^0.7.0",
      "dpd-fileupload": "^0.0.10"
    },
    "devDependencies": {
      "gulp": "^3.6.2",
      "gulp-jshint": "^1.6.1"
    }
<!--{
  title: 'Using Deployd as an Express middleware',
  tags: ['express', 'connect', 'middleware', 'server']
}-->

## Using Deployd as an Express middleware

Deployd can be used with express/connect. Deployd will attach functions and handler to express server object.

### Installing

For an app in your current directory:

    npm install deployd express socket.io

### Hello World

Here is a simple *hello world* using Deployd as an express middleware.

    // hello-server-attach.js
    var PORT = process.env.PORT || 3000;
    var ENV = process.env.NODE_ENV || 'development';

    // setup http + express + socket.io
    var express = require('express');
    var app = express();
    var server = require('http').createServer(app);
    var io = require('socket.io').listen(server, {'log level': 0});

    // setup deployd
    require('deployd').attach(server, {
        socketIo: io,  // if not provided, attach will create one for you.
        env: ENV,
        db: {host:'localhost', port:27017, name:'test-app'}
    });

    // After attach, express can use server.handleRequest as middleware
    app.use(server.handleRequest);

    // start server
    server.listen(PORT);


Run this like any other express server.

    node hello-server-attach.js

### Server Options <!-- ref -->

- **db** {Object} - the database to connect to
 - **db.connectionString** {String} - The URI of the mongoDB using [standard Connection String](http://docs.mongodb.org/manual/reference/connection-string/). If `db.connectionString` is set, the other db options are ignored.
 - **db.port** {Number} - the port of the database server
 - **db.host** {String} - the ip or domain of the database server
 - **db.name** {String} - the name of the database
 - **db.credentials** {Object} - credentials for db
  - **db.credentials.username** {String}
  - **db.credentials.password** {String}
- **env** {String} - the environment to run in.
- **socketIo** {Object} - socket.io instance.

*Note: If options.env is "development", the dashboard will not require authentication and configuration will not be cached. Make sure to change this to "production" or something similar when deploying.*

### Caveats

- Deployd mounts its server on `process.server`. This means you can only run one Deployd server in a process.
- Deployd loads resources from the `process.cwd`. Add this to ensure you are in the right directory: `process.chdir(__dirname)`.
- In order to access the `/dashboard` without a key you must run Deployd with the `env` option set to `development`.
<!--{
  title: 'Deploying to your own Server',
  tags: ['guide', 'deploy', 'hosting']
}-->

## Deploying to your own Server

To deploy your app on your server, or on a cloud hosting service such as EC2 or Heroku, the server must support [Node.js](http://nodejs.org/). 

Deployd also requires a [MongoDB](http://www.mongodb.org/) database, which can be hosted on the same server or externally. 

If you have root shell access on the deployment server, you can install Deployd on it using the command `npm install -g deployd`. 
Otherwise, you will need to install Deployd as a dependency of your app itself using `npm install deployd` in the root directory of your app.

You can use the `dpd` CLI to run your server; this will start up an instance of MongoDB automatically, using the "data" folder. (Requires MongoDB installed on the server)

### Dashboard Access

To set up the dashboard on your server, type `dpd keygen` on your server's command line to create a remote access key. Type `dpd showkey` to get the key; you should store this somewhere secure.

You can then go to the `/dashboard` route on the server and type in that key to gain access.

### Server Script

Since Deployd is itself a node module, you can write your own scripts to run in production instead of using the command line interface. Read the [Building a Custom Run Script](/docs/server/run-script.md) Guide.

*Note: Some hosts do not support WebSockets, so `dpd.on()` may not work correctly on certain deployments.*
<!--{
  title: 'Working with Sessions',
  tags: ['users', 'sessions', 'authentication']
}-->

## Working with Sessions

### Background

Since HTTP is a stateless protocol, a mechanism is required to tie independent requests and connections to a single remote **session**. In Deployd, sessions are maintained by signing each request with a session id. Currently the only mechanism for signing requests is HTTP cookies.

If a request does not contain a `sid` cookie with an existing session id, a session will be created and set as a cookie on the response.

### Sockets

WebSocket connections are identified and attached to sessions by the cookies sent during the upgrade request of a websocket.

### API

As of `v0.6` the `sessions` API is very limited. In upcoming versions the API will include the following:

- create sessions from modules
- get sockets by session or user id
- store arbitrary info on sessions
- query sessions
- *remote session api*
- query sessions by machine ip
- emit to sessions <!--{
  title: 'Authenticating Users',
  tags: ['reference', 'collection', 'users']
}-->

## Authenticating Users

A User Collection can be accessed in the same ways as a Collection, both with [dpd.js](/docs/collections/accessing-collections.md) and [HTTP](/docs/collections/reference/http.md). It also adds new methods to the API for authentication.

The examples below use a User Collection called `/users` with the following schema:

- `id`
- `username`
- `password`
- string `displayName`

### Logging in <!--ref-->

Log in a user with their username and password. If successful, the browser will save a secure cookie for their session. This request responds with the session details:

    {
      "id": "s0446b993caaad577a..." //Session id
      "path": "/users" // The path of the User Collection - useful if you have different types of users.
      "uid": "ec54ad870eaca95f" //The id of the user
    }

If the username or password is incorrect, Deployd will respond with a generic error:

    {
      "status": 401,
      "message: "bad credentials"
    }

For security reasons, users should not be informed which of their credentials (username, password, or both) were incorrect.

#### dpd.js

To authenticate a user, use the `.login(credentials, fn)` function, including the `username` and `password` properties in the request body.

    dpd.users.login({
      username: "johnsmith",
      password: "password"
    }, function(result, error) {
      // Do something
    });

You can also use the `.exec('login', credentials, fn)` function. This is useful if you have accessed the collection by using `dpd()` as a function and the `login()` function is unavailable.

    dpd('users').exec('login', {
      username: "johnsmith",
      password: "password"
    }, function(result, error) {
      // Do something
    });

#### HTTP

To authenticate a user, send a `POST` request to `/login` with `username` and `password` properties in the request body.

    POST /users/login
    {
      "username": "johnsmith",
      "password": "password"
    }


### Logging out <!--ref-->

Logging out will remove the session cookie on the browser and destroy the current session. It does not return a result.

#### dpd.js

To log out a user, use the `.logout(fn)` function.

    dpd.users.logout(function(result, error) {
      // Do something
    });

`result` will always be null.

You can also use the `.exec('logout', fn)` function. This is useful if you have accessed the collection by using `dpd()` as a function and the `logout()` function is unavailable.

    dpd('users').exec('logout', function(result, error) {
      // Do something
    });

#### HTTP

To log out a user, send a `POST` request to `/logout`. Include the `sid` cookie to identify your session.

    POST /users/logout
    Cookie: sid=6009c5b070d834a2d336224a93...

The response body will always be empty unless there was an error.

### Getting the current user <!--ref-->

This will return the current user.

    {
      "id": "2975ff2778493818",
      "username": "johnsmith",
      "displayName": "John Smith"
    }

If there is no current user, it will not return a value.

#### dpd.js

To get the current user, use the `.me(fn)` function. 

    dpd.users.me(function(result, error) {
      // Do something
    });

If there is no current user, `result` will be null.

You can also use the `.get('me', fn)` function. This is useful if you have accessed the collection by using `dpd()` as a function and the `me()` function is unavailable.

    dpd('users').get('me', function(result, error) {
      // Do something
    });

#### HTTP

To get the current user, send a `GET` request to `/me`. Include the `sid` cookie to identify your session.

    GET /users/me 
    Cookie: sid=6009c5b070d834a2d336224a93...

If there is no current user, the response body will be blank:

    204 No Content<!--{
  title: 'Creating User Collections',
  tags: ['guide', 'collection', 'users']
}-->

## Creating User Collections

### User Collection

A User Collection extends a [Collection](/docs/collections/creating-collections.md), adding the functionality needed to authenticate users with your app. You can create one by choosing "User Collection" when adding a Resource.

#### Properties

User Collections can have the same properties as a Collection, with two additional non-removable properties:

- `username` - The user's identifier; must be unique.
- `password` - An encrypted password. It can never be retrieved from the database, only queried against.

In addition to the above constraints, these two properties can only be modified by:

- A session authenticated as that user
- An internal request, such as a call from an event.
- A root request<!--{
  title: 'Microblogging app',
  tags: ['example', 'collection', 'users', 'dpd.js', 'angular']
}-->

## Microblogging app

This app demonstrates how to create a microblogging app (similar to Twitter) using User Collections. It also demonstrates how to use dpd.js with AngularJS on the front-end.

The app supports registering, logging in, making posts, and mentioning other users in posts with their @username.

<a href="https://github.com/downloads/deployd/examples/micro-blog.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/examples/tree/master/users/micro-blog" class="btn">View Source</a>

### Useful files

Events:

- [On Validate /posts](https://github.com/deployd/examples/blob/master/users/micro-blog/resources/posts/validate.js) (responsible for calculating the `mentions` property)
- [On POST /posts](https://github.com/deployd/examples/blob/master/users/micro-blog/resources/posts/post.js)

Front-end:

- [global.js](https://github.com/deployd/examples/blob/master/users/micro-blog/public/js/global.js) (The `Feed` class demonstrates paging)
- [index.js](https://github.com/deployd/examples/blob/master/users/micro-blog/public/js/index.js)<!--{
  title: 'Simple Login Form',
  tags: ['example', 'collection', 'users', 'dpd.js']
}-->

## Simple Login Form

This app demonstrates how to use the "login", "logout", and "me" functions on a User Collection.

<a href="https://github.com/downloads/deployd/examples/login-form.zip" class="btn btn-primary">Download</a> <a href="https://github.com/deployd/examples/tree/master/users/login-form" class="btn">View Source</a>

### Useful files

- [index.html](https://github.com/deployd/examples/blob/master/users/login-form/public/index.html) (Login form)
- [register.html](https://github.com/deployd/examples/blob/master/users/login-form/public/register.html)
- [welcome.html](https://github.com/deployd/examples/blob/master/users/login-form/public/register.html)<!--{
  title: 'Accessing Users in Events',
  tags: ['guide', 'collection', 'users', 'events']
}-->

## Accessing Users in Events with "me"

In any Collection Event, the `me` object refers to the current user. You can use this to secure your app and protect your users. This page lists a few examples of how to use the `me` object effectively.

### Keeping track of an object's creator

    // On Post /todo-lists
    cancelUnless(me, "You must be logged in to create a todo list", 401);

    this.creatorId = me.id;

### Securing an object

You can ensure that only the creator of an object can update it:

    // On Put /todos
    if (!(me && me.id === this.creatorId)) {
      cancel("This is not your todo", 401);
    }

### Checking for roles

If you store an `array` of `roles` on your User Collection, you can use that to verify that the current user can perform an action:

    // On POST /blog-posts
    if (!(me && me.roles.indexOf("author") !== -1)) {
      cancel("You must be an author to create a blog post", 401);
    }

### Awarding the user points

In a gamification setup, you might want to award the user some points for creating an object:

    // On POST /answers
    if (me) {
      dpd.users.put(me.id, {
        points: {$inc: 1}
      }, function() {});
    }

    // On PUT /users
    // External APIs should not be able to edit the point value
    if (!internal) {
      protect('points');
    }
<!--{
  title: 'Installing a Module',
  tags: ['installing', 'module']
}-->

## Installing a Module

### From NPM

Deployd modules are 100% compatible with [node modules](http://npmjs.org). This means you can install a module with [npm](http://npmjs.org) from your project's root directory.

    cd my-dpd-project
    mkdir -p node_modules
    npm install my-dpd-module

To find deployd modules available on npm [search for `dpd`](https://encrypted.google.com/search?q=dpd&q=site:npmjs.org&hl=en).

If you need to use a task manager like Grunt or Gulp for your development environement, you'll have to add a package.json as explained [in this page](/docs/server/use-grunt-or-gulp.md).

### From Source

You can also install a module from source by putting it in your project's `node_modules` folder. Even a single file is valid (eg: `/node_modules/foo.js`).
<!--{
  title: 'Email',
  tags: ['resource type', 'module', 'email'],
  description: 'Send emails from clients or during events.'
}-->

## Email Resource

This custom resource type allows you to send an email to your users.

The Email resource is built on the [Nodemailer](https://github.com/andris9/Nodemailer) module for Node.js; much of the documentation on this page is taken from their README.

### Installation

In your app's root directory, type `npm install dpd-email` into the command line or [download from source](https://github.com/deployd/dpd-email). This should create a `dpd-email` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before using the email resource, you must go to its Dashboard page and configure it.

These settings are required:

- `host`: The hostname of your SMTP provider.
- `port`: The port number of your SMTP provider. Defaults to 25; 587 is also common.
- `ssl`: If checked, use SSL to communicate with your SMTP provider. Unneeded for port 587; as it will automatically upgrade to a secure connection.
- `username`: The SMTP username for your app.
- `password`: The SMTP username for your app.

These settings are optional:

- `defaultFromAddress`: A "from" email address to provide by default. If this is not provided, you will need to provide this address in every request.
- `internalOnly`: If checked, only allow internal requests (such as those from events) to send emails. Recommended for security.
- `productionOnly`: If checked, attempting to send an email in the `development` environment will simply print it to the Deployd console. 

### Usage

To send an email, call `dpd.email.post(options, callback)` (replacing `email` with your resource name). The `options` argument is an object:

- `from`: The email address of the sender. Required if `defaultFromAddress` is not configured. All e-mail addresses can be plain (`sender@server.com`) or formatted (`Sender Name <sender@server.com>`)
- `to`: Comma separated list of recipients e-mail addresses that will appear on the To: field
- `cc`: Comma separated list of recipients e-mail addresses that will appear on the Cc: field
- `bcc`: Comma separated list of recipients e-mail addresses that will appear on the Bcc: field
- `subject`: The subject of the e-mail.
- `text`: The plaintext version of the message
- `html`: The HTML version of the message

### Example Usage

    // On POST /users

    dpd.email.post({
      to: this.email,
      from: "deployd-server@example.com", 
      subject: "MyApp registration",
      text: this.username + ",\n\n" +
            "Thank you for registering for MyApp!"
    }, function() {});
<!--{
  title: 'Event Resource',
  tags: ['resource type', 'module'],
  description: 'Create custom events at a specified URL.'
}-->

## Event Resource

This custom resource type allows you to write an event that will run when the resource's route receives a `GET` or `POST` request.

### Installation

In your app's root directory, type `npm install dpd-event` into the command line or [download the source](https://github.com/deployd/dpd-event). This should create a `dpd-event` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Usage

The `On POST` event will be executed when the resource's route (or a subroute) receives a `POST` request, and likewise with the `On GET` event.

It is strongly recommended that you reserve the `On GET` event for operations that return a value, but don't have any side effects of modifying the database or performing some other operation.  

If your resource is called `/add-follower`, you can trigger its `POST` event from dpd.js:

    dpd.addfollower.post('320d6151a9aad8ce', {userId: '6d75e75d9bd9b8a6'}, function(result, error) {
      // Do something
    })

And over HTTP:

    POST /add-follower/320d6151a9aad8ce
    Content-Type: application/json
    {
      "userId": "6d75e75d9bd9b8a6"
    }

### Event API

In addition to the generic [custom resource event API](/docs/using-modules/reference/event-api.md), the following functions and variables are available while scripting the Event resource:


#### setResult(result) <!-- api -->

Sets the response body. The `result` argument can be a string or an object.

    // On GET /top-score
    dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
      setResult(result[0]);
    });

#### url <!-- api -->

The URL of the request, without the resource's base URL. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce`, the `url` value will be `/320d6151a9aad8ce`.

    // On GET /statistics
    // Get the top score
    if (url === '/top-score') {
      dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
        setResult(result[0]);
      });
    }

#### parts <!-- api -->

An array of the parts of the url, separated by `/`. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce/6d75e75d9bd9b8a6`, the `parts` value will be `['320d6151a9aad8ce', '6d75e75d9bd9b8a6']`.

    // On POST /add-score
    // Give the specified user (/add-score/:userId) 5 points
    var userId = parts[0];
    if (!userId) cancel("You must provide a user");

    dpd.users.put({id: userId}, {score: {$inc: 5}}, function(result, err) {
      if (err) cancel(err);
    });

#### query <!-- api -->

The query string object.
  
    // On GET /sum
    // Return the sum of the a and b properties (/sum?a=5&b=1)

    setResult(query.a + query.b);

#### body <!-- api -->

The body of the request.

    // On POST /sum
    // Return the sum of the a and b properties {a: 5, b: 1}

    setResult(body.a + body.b);<!--{
	title: 'Importer',
	tags: ['resource type', 'module', 'import'],
  description: 'Import collections from existing MongoDBs.'
}-->

## Importer

This custom resource type allows you to import collections from an existing MongoDB.

### Installation

Create a project. Then install the dpd-importer module.

    dpd create my-app
    cd my-app
    mkdir node_modules
    npm install dpd-importer
    dpd -d
    
In your dashboard - click the green new resource button and choose **Importer**.

Give the new resource the default name "/importer". Open it by clicking "IMPOTER" in the left menu.

Enter the information of your old MongoDB server. Clicking on **Start Import** will start creating deployd collections from data in the provided db by streaming data directly from the old db into your new deployd db. The importer will do its best to create properties based on the types it infers from your data.<!--{
	title: 'S3 Bucket',
	tags: ['resource type', 'module', 's3'],
  description: 'Store and retrieve files from an S3 Bucket.'
}-->

## S3 Bucket Resource

This custom resource type allows you to store and retrieve files from an [Amazon S3](http://aws.amazon.com/s3/) bucket.

### Installation

In your app's root directory, type `npm install s3-bucket-resource` into the command line or [download the source](https://github.com/deployd/dpd-s3). This should create a `dpd-s3` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before you can use the S3 Bucket resource, you must set the three properties on its "Config" page:

- `bucket`: The name of your S3 Bucket
- `key`: The security key of your S3 Bucket
- `secret`: The secret key of your S3 Bucket

### Usage

#### Upload <!-- ref -->

There are two ways to upload files. Both ways require HTTP access; you cannot upload files with dpd.js.

##### Direct upload 

Send a `POST` request to the url where you want to upload the file, including the file name. Set the `Content-Type` header to that of the file you are uploading and pass the file's content in the request body.

It will return a `200 OK` if the upload was successful. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

	POST /my-bucket/README.txt
	Content-Type: text/plain
	Hello, world!

	200 OK

##### Multipart upload

You can upload files directly from a browser using the `multipart/form-data` type and the `<input type="file" />` tag:

	<form action="/installer-downloads" enctype="multipart/form-data" method="post">
		<input type="file" name="upload" multiple="multiple" />
		<button type="submit">Upload</button>
	</form>

To send a multipart request manually, send a `POST` request to the url where you want to upload the file, *not* including the file name. The `Content-Type` header must be `multipart/form-data`. Set the request body according to the [multipart/form-data standard](http://www.w3.org/TR/html401/interact/forms.html#h-17.13.4.2).

If the upload was successful and there is a `Referrer` header on the request (e.g. if it was submitted as a form from a browser), the response will redirect to the referrer. Otherwise, it will return `200 OK`. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

#### Retrieving files <!-- ref -->

To download a file, send a `GET` request to the url where the file exists. 

	GET /my-bucket/README.txt

	200 OK
	Content-Type: text/plain
	Hello, world!

#### Deleting files <!-- ref -->

To delete a file, send a `DELETE` request to the url where the file exists.

	DELETE /my-bucket/README.txt

	200 OK

This can also be done with dpd.js:

	dpd.mybucket.del('README.txt', function(response, error) {
		// Do something
	});

### Events

The S3 Bucket Resource has three events:

- `On Upload`: Executed before a file is uploaded to S3.
- `On Get`: Executed before a file is downloaded from S3.
- `On Delete`: Executed before a file is deleted.

### Event API

#### url <!-- api -->

The URL of the request. Does not include the resource's name; if the request URL is `/my-bucket/README.txt`, the `url` property will be `/README.txt`.

#### fileSize  <!-- api -->

Only available in `On Upload`. The size of the file, in bytes.

		// On Upload
		// Set a limit on file size
		if (fileSize > 1024*1024*1024) { // 1GB
			cancel("File is too big; limit is 1GB");
		}

#### fileName <!-- api -->

Only available in `On Upload`. The name of the file that is being uploaded.

		// On Upload
		dpd.uploads.post({ filename: fileName, creator: me.id }, function() {})
<!--{
	title: 'Dpd.js for Custom Resources',
	tags: ['dpd.js', 'custom', 'resource']
}-->

## Dpd.js for Custom Resources

Because Custom Resource Types can specify APIs very different from a Collection, Dpd.js acts as a generic HTTP library for Custom Resources.

### Accessing the Resource

The API for your Resource is automatically generated as `dpd.[resource]`.

Examples:

	dpd.emails
	dpd.addfollower
	dpd.uploads

*Note: If your Resource name has a dash in it (e.g. `/add-follower`), the dash is removed when accessing it in this way (e.g. `dpd.addfollower`).*

You can also access your resource by using `dpd(resourceName)` as a function.

Examples:

	dpd('emails')
	dpd('add-follower')
	dpd('uploads')

### Callbacks

Every function in the Dpd.js API takes a callback function (represented by `fn` in the docs) with the signature `function(result, error)`.

The callback will be executed asynchronously when the API has received a response from the server.

The `result` argument differs depending on the function. If the result failed, it will be `null` and the `error` argument will contain the error message.

The `error` argument, if there was an error, is an object:

 - `status` (number): The HTTP status code of the request. Common codes include:
	- 400 - Bad Request: The request contained invalid data and could not be completed
	- 401 - Unauthorized: The current session is not authorized to perform that action
	- 500 - Internal Server Error: Something went wrong on the server
 - `message` (string): A message describing the error. Not always present.
 - `errors` (object): A hash of error messages corresponding to the properties of the object that was sent - usually indicates validation errors. Not always present.

Examples of errors:

	{
		"status": 401,
		"message": "You are not allowed to access that resource!"
	}

<!--...-->

	{
		"status": 400,
		"errors": {
			"title": "Title must be less than 100 characters",
			"category": "Not a valid category"
		}
	}



#### Promises

Every function in the collection API returns a promise.
We use the [`ayepromise` library](https://github.com/cburgmer/ayepromise) (which follows the [Promises/A+ 1.1 specs](https://promisesaplus.com/)).
To learn how to use promises, please, refer [to this article](http://www.html5rocks.com/en/tutorials/es6/promises).

The first callback contains the same `result` same with the classic callbacks.
The second callback contains the `error` object as described above.
Here's an example to use promises within dpd.js:

	dpd.todos.post({message: "Hello world"}).then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err); // display an error if the request failed
	});

<!--...-->

	dpd.todos.get('1234324324').then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err.errors.message); // display the error message
	});


### get() <!-- api -->

	dpd.[resource].get([func], [path], [query], fn)

Makes a GET HTTP request at the URL `/<resource>/<func>/<path>`, using the `query` object as the query string if provided.

- `func` - A special identifier, i.e. `/me`.
- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `fn` - Callback `function(result, error)`.

###  post() <!-- api -->

	dpd.[resource].post([path], [query], body, fn)

Makes a POST HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### put() <!-- api -->

	dpd.[resource].put([path], [query], body, fn)

Makes a PUT HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### del() <!-- api -->

	dpd.[resource].del([path], [query], fn)

Makes a DELETE HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `fn` - Callback `function(result, error)`.


### exec() <!-- api -->

	dpd.[resource].exec(func, [path], [body], fn)

Makes an RPC-style POST HTTP request at the URL `/<resource>/<func>/<path>`. Useful for functions that don't make sense in REST-style APIs, such as `/users/login`.

- `func` - The name of the function to call
- `path` - An identifier for a particular object, usually the id
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### Realtime API

The Generic Realtime API behaves the same way as the [Collection Realtime API](/docs/collections/reference/dpd-js.md#s-Realtime-API).
<!--{
  title: 'Event API for Custom Resources',
  tags: ['event', 'custom', 'resource']
}-->

## Event API for Custom Resources

### Background

Custom Resources may load **event scripts** to allow you to inject business logic during requests to the resource. For example, the collection resource exposes an event called *validate*. Given the following todo resource folder:

    /my-app
      /resources
        /todos
          validate.js

The collection resource would load the contents of `validate.js` as the `validate` event.

### Default Event Script Domain

Event scripts do not share a global scope with other modules in your app. Instead each time an event script is run, a new scope is created for it.

The following functions and objects are available to all event scripts.

#### ctx <!-- ctx -->

The context of the request. This object contains everything from the request (request, response, body, headers, etc...):

    // Example:
    if (ctx && ctx.req && ctx.req.headers && ctx.req.headers.host !== '192.168.178.34:2403') {
      cancel("You are not authorized to do that", 401);
    }

The entire object is [available as a gist here](https://gist.github.com/NicolasRitouet/2fc5dd20f3af7dc7e192).

#### me <!-- api -->

The current user if one exists on the current `Context`.

#### isMe() <!-- api -->

    isMe(id)

Returns true if the current user (`me`) matches the provided `id`.

#### this <!-- api -->

If the resource does not implement a custom domain, this will be an empty object. Otherwise `this` usually refers to the current domain's instance (eg. an object in a collection).

#### cancel() <!-- api -->

    cancel(message, [statusCode])

Stops the current request with the provided error message and HTTP status code. Status code defaults to `400`.

#### cancelIf(), cancelUnless() <!-- api -->

    cancelIf(condition, message, [statusCode])
    cancelUnless(condition, message, [statusCode])

Calls `cancel(message, statusCode)` if the provided condition is truthy (for `cancelIf()`) or falsy (for `cancelUnless`).

#### internal <!-- api -->

A boolean property, true if this request has been initiated by another script.

#### isRoot <!-- api -->

A boolean property, true if this request is authenticated as root (from the dashboard or a custom script).

#### query <!-- api -->

The current HTTP query. (eg ?foo=bar - query would be {foo: 'bar'}).

#### emit() <!-- api -->

    emit([userCollection, query], message, [data])

Emits a realtime message to the client. You can use `userCollection` and `query` parameters to limit the message broadcast to specific users.

#### console <!-- api -->

Support for console.log() and other console methods.
<!--{
  title: 'Using a Custom Resource Type',
  tags: ['resource type', 'module']
}-->

### Using a Custom Resource Type

Deployd modules can register new *Resource Types*, which can be created with a route and configured per instance. Deployd comes with two built-in Resource Types: "Collection" and "User Collection". 

To add more Resource Types, you can [install](/docs/using-modules/installing-modules.md) a module that includes one. The examples on this page use the [Event resource](/docs/using-modules/official/event.md).

#### Creating an instance of a Custom Resource Type

Once the module is properly installed, you can add the custom resource just like a Collection. Custom Resources will usually have an asterisk <i class="icon-asterisk"></i> icon. 

![Creating an Event resource](/tutorials/resource-type/creating-custom-resource.png)

*Note: After adding any module, you will have to restart the Deployd server to see its effects. If you don't see the custom resource type in the list, you may have to restart the server and refresh the dashboard.*

#### Configuring a Custom Resource Type

See the documentation of your Custom Resource Type module for details on configuration options. Most custom resource types implement a "Config" page and an "Events" page.

The "Config" page can take different forms. For very basic modules, it's often a simple JSON editor where you can enter optional values. Others will list their available configuration values in a form.

The "Events" page is similar to the Collection "Events" page.

Depending on the complexity of the custom resource type, it may have different configuration pages.<!--{
  title: 'Installing a Module',
  tags: ['installing', 'module']
}-->

## Installing a Module

### From NPM

Deployd modules are 100% compatible with [node modules](http://npmjs.org). This means you can install a module with [npm](http://npmjs.org) from your project's root directory.

    cd my-dpd-project
    mkdir -p node_modules
    npm install my-dpd-module

To find deployd modules available on npm [search for `dpd`](https://encrypted.google.com/search?q=dpd&q=site:npmjs.org&hl=en).

If you need to use a task manager like Grunt or Gulp for your development environement, you'll have to add a package.json as explained [in this page](/docs/server/use-grunt-or-gulp.md).

### From Source

You can also install a module from source by putting it in your project's `node_modules` folder. Even a single file is valid (eg: `/node_modules/foo.js`).
<!--{
  title: 'Email',
  tags: ['resource type', 'module', 'email'],
  description: 'Send emails from clients or during events.'
}-->

## Email Resource

This custom resource type allows you to send an email to your users.

The Email resource is built on the [Nodemailer](https://github.com/andris9/Nodemailer) module for Node.js; much of the documentation on this page is taken from their README.

### Installation

In your app's root directory, type `npm install dpd-email` into the command line or [download from source](https://github.com/deployd/dpd-email). This should create a `dpd-email` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before using the email resource, you must go to its Dashboard page and configure it.

These settings are required:

- `host`: The hostname of your SMTP provider.
- `port`: The port number of your SMTP provider. Defaults to 25; 587 is also common.
- `ssl`: If checked, use SSL to communicate with your SMTP provider. Unneeded for port 587; as it will automatically upgrade to a secure connection.
- `username`: The SMTP username for your app.
- `password`: The SMTP username for your app.

These settings are optional:

- `defaultFromAddress`: A "from" email address to provide by default. If this is not provided, you will need to provide this address in every request.
- `internalOnly`: If checked, only allow internal requests (such as those from events) to send emails. Recommended for security.
- `productionOnly`: If checked, attempting to send an email in the `development` environment will simply print it to the Deployd console. 

### Usage

To send an email, call `dpd.email.post(options, callback)` (replacing `email` with your resource name). The `options` argument is an object:

- `from`: The email address of the sender. Required if `defaultFromAddress` is not configured. All e-mail addresses can be plain (`sender@server.com`) or formatted (`Sender Name <sender@server.com>`)
- `to`: Comma separated list of recipients e-mail addresses that will appear on the To: field
- `cc`: Comma separated list of recipients e-mail addresses that will appear on the Cc: field
- `bcc`: Comma separated list of recipients e-mail addresses that will appear on the Bcc: field
- `subject`: The subject of the e-mail.
- `text`: The plaintext version of the message
- `html`: The HTML version of the message

### Example Usage

    // On POST /users

    dpd.email.post({
      to: this.email,
      from: "deployd-server@example.com", 
      subject: "MyApp registration",
      text: this.username + ",\n\n" +
            "Thank you for registering for MyApp!"
    }, function() {});
<!--{
  title: 'Event Resource',
  tags: ['resource type', 'module'],
  description: 'Create custom events at a specified URL.'
}-->

## Event Resource

This custom resource type allows you to write an event that will run when the resource's route receives a `GET` or `POST` request.

### Installation

In your app's root directory, type `npm install dpd-event` into the command line or [download the source](https://github.com/deployd/dpd-event). This should create a `dpd-event` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Usage

The `On POST` event will be executed when the resource's route (or a subroute) receives a `POST` request, and likewise with the `On GET` event.

It is strongly recommended that you reserve the `On GET` event for operations that return a value, but don't have any side effects of modifying the database or performing some other operation.  

If your resource is called `/add-follower`, you can trigger its `POST` event from dpd.js:

    dpd.addfollower.post('320d6151a9aad8ce', {userId: '6d75e75d9bd9b8a6'}, function(result, error) {
      // Do something
    })

And over HTTP:

    POST /add-follower/320d6151a9aad8ce
    Content-Type: application/json
    {
      "userId": "6d75e75d9bd9b8a6"
    }

### Event API

In addition to the generic [custom resource event API](/docs/using-modules/reference/event-api.md), the following functions and variables are available while scripting the Event resource:


#### setResult(result) <!-- api -->

Sets the response body. The `result` argument can be a string or an object.

    // On GET /top-score
    dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
      setResult(result[0]);
    });

#### url <!-- api -->

The URL of the request, without the resource's base URL. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce`, the `url` value will be `/320d6151a9aad8ce`.

    // On GET /statistics
    // Get the top score
    if (url === '/top-score') {
      dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
        setResult(result[0]);
      });
    }

#### parts <!-- api -->

An array of the parts of the url, separated by `/`. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce/6d75e75d9bd9b8a6`, the `parts` value will be `['320d6151a9aad8ce', '6d75e75d9bd9b8a6']`.

    // On POST /add-score
    // Give the specified user (/add-score/:userId) 5 points
    var userId = parts[0];
    if (!userId) cancel("You must provide a user");

    dpd.users.put({id: userId}, {score: {$inc: 5}}, function(result, err) {
      if (err) cancel(err);
    });

#### query <!-- api -->

The query string object.
  
    // On GET /sum
    // Return the sum of the a and b properties (/sum?a=5&b=1)

    setResult(query.a + query.b);

#### body <!-- api -->

The body of the request.

    // On POST /sum
    // Return the sum of the a and b properties {a: 5, b: 1}

    setResult(body.a + body.b);<!--{
	title: 'Importer',
	tags: ['resource type', 'module', 'import'],
  description: 'Import collections from existing MongoDBs.'
}-->

## Importer

This custom resource type allows you to import collections from an existing MongoDB.

### Installation

Create a project. Then install the dpd-importer module.

    dpd create my-app
    cd my-app
    mkdir node_modules
    npm install dpd-importer
    dpd -d
    
In your dashboard - click the green new resource button and choose **Importer**.

Give the new resource the default name "/importer". Open it by clicking "IMPOTER" in the left menu.

Enter the information of your old MongoDB server. Clicking on **Start Import** will start creating deployd collections from data in the provided db by streaming data directly from the old db into your new deployd db. The importer will do its best to create properties based on the types it infers from your data.<!--{
	title: 'S3 Bucket',
	tags: ['resource type', 'module', 's3'],
  description: 'Store and retrieve files from an S3 Bucket.'
}-->

## S3 Bucket Resource

This custom resource type allows you to store and retrieve files from an [Amazon S3](http://aws.amazon.com/s3/) bucket.

### Installation

In your app's root directory, type `npm install s3-bucket-resource` into the command line or [download the source](https://github.com/deployd/dpd-s3). This should create a `dpd-s3` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before you can use the S3 Bucket resource, you must set the three properties on its "Config" page:

- `bucket`: The name of your S3 Bucket
- `key`: The security key of your S3 Bucket
- `secret`: The secret key of your S3 Bucket

### Usage

#### Upload <!-- ref -->

There are two ways to upload files. Both ways require HTTP access; you cannot upload files with dpd.js.

##### Direct upload 

Send a `POST` request to the url where you want to upload the file, including the file name. Set the `Content-Type` header to that of the file you are uploading and pass the file's content in the request body.

It will return a `200 OK` if the upload was successful. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

	POST /my-bucket/README.txt
	Content-Type: text/plain
	Hello, world!

	200 OK

##### Multipart upload

You can upload files directly from a browser using the `multipart/form-data` type and the `<input type="file" />` tag:

	<form action="/installer-downloads" enctype="multipart/form-data" method="post">
		<input type="file" name="upload" multiple="multiple" />
		<button type="submit">Upload</button>
	</form>

To send a multipart request manually, send a `POST` request to the url where you want to upload the file, *not* including the file name. The `Content-Type` header must be `multipart/form-data`. Set the request body according to the [multipart/form-data standard](http://www.w3.org/TR/html401/interact/forms.html#h-17.13.4.2).

If the upload was successful and there is a `Referrer` header on the request (e.g. if it was submitted as a form from a browser), the response will redirect to the referrer. Otherwise, it will return `200 OK`. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

#### Retrieving files <!-- ref -->

To download a file, send a `GET` request to the url where the file exists. 

	GET /my-bucket/README.txt

	200 OK
	Content-Type: text/plain
	Hello, world!

#### Deleting files <!-- ref -->

To delete a file, send a `DELETE` request to the url where the file exists.

	DELETE /my-bucket/README.txt

	200 OK

This can also be done with dpd.js:

	dpd.mybucket.del('README.txt', function(response, error) {
		// Do something
	});

### Events

The S3 Bucket Resource has three events:

- `On Upload`: Executed before a file is uploaded to S3.
- `On Get`: Executed before a file is downloaded from S3.
- `On Delete`: Executed before a file is deleted.

### Event API

#### url <!-- api -->

The URL of the request. Does not include the resource's name; if the request URL is `/my-bucket/README.txt`, the `url` property will be `/README.txt`.

#### fileSize  <!-- api -->

Only available in `On Upload`. The size of the file, in bytes.

		// On Upload
		// Set a limit on file size
		if (fileSize > 1024*1024*1024) { // 1GB
			cancel("File is too big; limit is 1GB");
		}

#### fileName <!-- api -->

Only available in `On Upload`. The name of the file that is being uploaded.

		// On Upload
		dpd.uploads.post({ filename: fileName, creator: me.id }, function() {})
<!--{
	title: 'Dpd.js for Custom Resources',
	tags: ['dpd.js', 'custom', 'resource']
}-->

## Dpd.js for Custom Resources

Because Custom Resource Types can specify APIs very different from a Collection, Dpd.js acts as a generic HTTP library for Custom Resources.

### Accessing the Resource

The API for your Resource is automatically generated as `dpd.[resource]`.

Examples:

	dpd.emails
	dpd.addfollower
	dpd.uploads

*Note: If your Resource name has a dash in it (e.g. `/add-follower`), the dash is removed when accessing it in this way (e.g. `dpd.addfollower`).*

You can also access your resource by using `dpd(resourceName)` as a function.

Examples:

	dpd('emails')
	dpd('add-follower')
	dpd('uploads')

### Callbacks

Every function in the Dpd.js API takes a callback function (represented by `fn` in the docs) with the signature `function(result, error)`.

The callback will be executed asynchronously when the API has received a response from the server.

The `result` argument differs depending on the function. If the result failed, it will be `null` and the `error` argument will contain the error message.

The `error` argument, if there was an error, is an object:

 - `status` (number): The HTTP status code of the request. Common codes include:
	- 400 - Bad Request: The request contained invalid data and could not be completed
	- 401 - Unauthorized: The current session is not authorized to perform that action
	- 500 - Internal Server Error: Something went wrong on the server
 - `message` (string): A message describing the error. Not always present.
 - `errors` (object): A hash of error messages corresponding to the properties of the object that was sent - usually indicates validation errors. Not always present.

Examples of errors:

	{
		"status": 401,
		"message": "You are not allowed to access that resource!"
	}

<!--...-->

	{
		"status": 400,
		"errors": {
			"title": "Title must be less than 100 characters",
			"category": "Not a valid category"
		}
	}



#### Promises

Every function in the collection API returns a promise.
We use the [`ayepromise` library](https://github.com/cburgmer/ayepromise) (which follows the [Promises/A+ 1.1 specs](https://promisesaplus.com/)).
To learn how to use promises, please, refer [to this article](http://www.html5rocks.com/en/tutorials/es6/promises).

The first callback contains the same `result` same with the classic callbacks.
The second callback contains the `error` object as described above.
Here's an example to use promises within dpd.js:

	dpd.todos.post({message: "Hello world"}).then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err); // display an error if the request failed
	});

<!--...-->

	dpd.todos.get('1234324324').then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err.errors.message); // display the error message
	});


### get() <!-- api -->

	dpd.[resource].get([func], [path], [query], fn)

Makes a GET HTTP request at the URL `/<resource>/<func>/<path>`, using the `query` object as the query string if provided.

- `func` - A special identifier, i.e. `/me`.
- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `fn` - Callback `function(result, error)`.

###  post() <!-- api -->

	dpd.[resource].post([path], [query], body, fn)

Makes a POST HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### put() <!-- api -->

	dpd.[resource].put([path], [query], body, fn)

Makes a PUT HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### del() <!-- api -->

	dpd.[resource].del([path], [query], fn)

Makes a DELETE HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `fn` - Callback `function(result, error)`.


### exec() <!-- api -->

	dpd.[resource].exec(func, [path], [body], fn)

Makes an RPC-style POST HTTP request at the URL `/<resource>/<func>/<path>`. Useful for functions that don't make sense in REST-style APIs, such as `/users/login`.

- `func` - The name of the function to call
- `path` - An identifier for a particular object, usually the id
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### Realtime API

The Generic Realtime API behaves the same way as the [Collection Realtime API](/docs/collections/reference/dpd-js.md#s-Realtime-API).
<!--{
  title: 'Event API for Custom Resources',
  tags: ['event', 'custom', 'resource']
}-->

## Event API for Custom Resources

### Background

Custom Resources may load **event scripts** to allow you to inject business logic during requests to the resource. For example, the collection resource exposes an event called *validate*. Given the following todo resource folder:

    /my-app
      /resources
        /todos
          validate.js

The collection resource would load the contents of `validate.js` as the `validate` event.

### Default Event Script Domain

Event scripts do not share a global scope with other modules in your app. Instead each time an event script is run, a new scope is created for it.

The following functions and objects are available to all event scripts.

#### ctx <!-- ctx -->

The context of the request. This object contains everything from the request (request, response, body, headers, etc...):

    // Example:
    if (ctx && ctx.req && ctx.req.headers && ctx.req.headers.host !== '192.168.178.34:2403') {
      cancel("You are not authorized to do that", 401);
    }

The entire object is [available as a gist here](https://gist.github.com/NicolasRitouet/2fc5dd20f3af7dc7e192).

#### me <!-- api -->

The current user if one exists on the current `Context`.

#### isMe() <!-- api -->

    isMe(id)

Returns true if the current user (`me`) matches the provided `id`.

#### this <!-- api -->

If the resource does not implement a custom domain, this will be an empty object. Otherwise `this` usually refers to the current domain's instance (eg. an object in a collection).

#### cancel() <!-- api -->

    cancel(message, [statusCode])

Stops the current request with the provided error message and HTTP status code. Status code defaults to `400`.

#### cancelIf(), cancelUnless() <!-- api -->

    cancelIf(condition, message, [statusCode])
    cancelUnless(condition, message, [statusCode])

Calls `cancel(message, statusCode)` if the provided condition is truthy (for `cancelIf()`) or falsy (for `cancelUnless`).

#### internal <!-- api -->

A boolean property, true if this request has been initiated by another script.

#### isRoot <!-- api -->

A boolean property, true if this request is authenticated as root (from the dashboard or a custom script).

#### query <!-- api -->

The current HTTP query. (eg ?foo=bar - query would be {foo: 'bar'}).

#### emit() <!-- api -->

    emit([userCollection, query], message, [data])

Emits a realtime message to the client. You can use `userCollection` and `query` parameters to limit the message broadcast to specific users.

#### console <!-- api -->

Support for console.log() and other console methods.
<!--{
  title: 'Using a Custom Resource Type',
  tags: ['resource type', 'module']
}-->

### Using a Custom Resource Type

Deployd modules can register new *Resource Types*, which can be created with a route and configured per instance. Deployd comes with two built-in Resource Types: "Collection" and "User Collection". 

To add more Resource Types, you can [install](/docs/using-modules/installing-modules.md) a module that includes one. The examples on this page use the [Event resource](/docs/using-modules/official/event.md).

#### Creating an instance of a Custom Resource Type

Once the module is properly installed, you can add the custom resource just like a Collection. Custom Resources will usually have an asterisk <i class="icon-asterisk"></i> icon. 

![Creating an Event resource](/tutorials/resource-type/creating-custom-resource.png)

*Note: After adding any module, you will have to restart the Deployd server to see its effects. If you don't see the custom resource type in the list, you may have to restart the server and refresh the dashboard.*

#### Configuring a Custom Resource Type

See the documentation of your Custom Resource Type module for details on configuration options. Most custom resource types implement a "Config" page and an "Events" page.

The "Config" page can take different forms. For very basic modules, it's often a simple JSON editor where you can enter optional values. Others will list their available configuration values in a form.

The "Events" page is similar to the Collection "Events" page.

Depending on the complexity of the custom resource type, it may have different configuration pages.<!--{
  title: 'Installing a Module',
  tags: ['installing', 'module']
}-->

## Installing a Module

### From NPM

Deployd modules are 100% compatible with [node modules](http://npmjs.org). This means you can install a module with [npm](http://npmjs.org) from your project's root directory.

    cd my-dpd-project
    mkdir -p node_modules
    npm install my-dpd-module

To find deployd modules available on npm [search for `dpd`](https://encrypted.google.com/search?q=dpd&q=site:npmjs.org&hl=en).

If you need to use a task manager like Grunt or Gulp for your development environement, you'll have to add a package.json as explained [in this page](/docs/server/use-grunt-or-gulp.md).

### From Source

You can also install a module from source by putting it in your project's `node_modules` folder. Even a single file is valid (eg: `/node_modules/foo.js`).
<!--{
  title: 'Email',
  tags: ['resource type', 'module', 'email'],
  description: 'Send emails from clients or during events.'
}-->

## Email Resource

This custom resource type allows you to send an email to your users.

The Email resource is built on the [Nodemailer](https://github.com/andris9/Nodemailer) module for Node.js; much of the documentation on this page is taken from their README.

### Installation

In your app's root directory, type `npm install dpd-email` into the command line or [download from source](https://github.com/deployd/dpd-email). This should create a `dpd-email` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before using the email resource, you must go to its Dashboard page and configure it.

These settings are required:

- `host`: The hostname of your SMTP provider.
- `port`: The port number of your SMTP provider. Defaults to 25; 587 is also common.
- `ssl`: If checked, use SSL to communicate with your SMTP provider. Unneeded for port 587; as it will automatically upgrade to a secure connection.
- `username`: The SMTP username for your app.
- `password`: The SMTP username for your app.

These settings are optional:

- `defaultFromAddress`: A "from" email address to provide by default. If this is not provided, you will need to provide this address in every request.
- `internalOnly`: If checked, only allow internal requests (such as those from events) to send emails. Recommended for security.
- `productionOnly`: If checked, attempting to send an email in the `development` environment will simply print it to the Deployd console. 

### Usage

To send an email, call `dpd.email.post(options, callback)` (replacing `email` with your resource name). The `options` argument is an object:

- `from`: The email address of the sender. Required if `defaultFromAddress` is not configured. All e-mail addresses can be plain (`sender@server.com`) or formatted (`Sender Name <sender@server.com>`)
- `to`: Comma separated list of recipients e-mail addresses that will appear on the To: field
- `cc`: Comma separated list of recipients e-mail addresses that will appear on the Cc: field
- `bcc`: Comma separated list of recipients e-mail addresses that will appear on the Bcc: field
- `subject`: The subject of the e-mail.
- `text`: The plaintext version of the message
- `html`: The HTML version of the message

### Example Usage

    // On POST /users

    dpd.email.post({
      to: this.email,
      from: "deployd-server@example.com", 
      subject: "MyApp registration",
      text: this.username + ",\n\n" +
            "Thank you for registering for MyApp!"
    }, function() {});
<!--{
  title: 'Event Resource',
  tags: ['resource type', 'module'],
  description: 'Create custom events at a specified URL.'
}-->

## Event Resource

This custom resource type allows you to write an event that will run when the resource's route receives a `GET` or `POST` request.

### Installation

In your app's root directory, type `npm install dpd-event` into the command line or [download the source](https://github.com/deployd/dpd-event). This should create a `dpd-event` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Usage

The `On POST` event will be executed when the resource's route (or a subroute) receives a `POST` request, and likewise with the `On GET` event.

It is strongly recommended that you reserve the `On GET` event for operations that return a value, but don't have any side effects of modifying the database or performing some other operation.  

If your resource is called `/add-follower`, you can trigger its `POST` event from dpd.js:

    dpd.addfollower.post('320d6151a9aad8ce', {userId: '6d75e75d9bd9b8a6'}, function(result, error) {
      // Do something
    })

And over HTTP:

    POST /add-follower/320d6151a9aad8ce
    Content-Type: application/json
    {
      "userId": "6d75e75d9bd9b8a6"
    }

### Event API

In addition to the generic [custom resource event API](/docs/using-modules/reference/event-api.md), the following functions and variables are available while scripting the Event resource:


#### setResult(result) <!-- api -->

Sets the response body. The `result` argument can be a string or an object.

    // On GET /top-score
    dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
      setResult(result[0]);
    });

#### url <!-- api -->

The URL of the request, without the resource's base URL. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce`, the `url` value will be `/320d6151a9aad8ce`.

    // On GET /statistics
    // Get the top score
    if (url === '/top-score') {
      dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
        setResult(result[0]);
      });
    }

#### parts <!-- api -->

An array of the parts of the url, separated by `/`. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce/6d75e75d9bd9b8a6`, the `parts` value will be `['320d6151a9aad8ce', '6d75e75d9bd9b8a6']`.

    // On POST /add-score
    // Give the specified user (/add-score/:userId) 5 points
    var userId = parts[0];
    if (!userId) cancel("You must provide a user");

    dpd.users.put({id: userId}, {score: {$inc: 5}}, function(result, err) {
      if (err) cancel(err);
    });

#### query <!-- api -->

The query string object.
  
    // On GET /sum
    // Return the sum of the a and b properties (/sum?a=5&b=1)

    setResult(query.a + query.b);

#### body <!-- api -->

The body of the request.

    // On POST /sum
    // Return the sum of the a and b properties {a: 5, b: 1}

    setResult(body.a + body.b);<!--{
	title: 'Importer',
	tags: ['resource type', 'module', 'import'],
  description: 'Import collections from existing MongoDBs.'
}-->

## Importer

This custom resource type allows you to import collections from an existing MongoDB.

### Installation

Create a project. Then install the dpd-importer module.

    dpd create my-app
    cd my-app
    mkdir node_modules
    npm install dpd-importer
    dpd -d
    
In your dashboard - click the green new resource button and choose **Importer**.

Give the new resource the default name "/importer". Open it by clicking "IMPOTER" in the left menu.

Enter the information of your old MongoDB server. Clicking on **Start Import** will start creating deployd collections from data in the provided db by streaming data directly from the old db into your new deployd db. The importer will do its best to create properties based on the types it infers from your data.<!--{
	title: 'S3 Bucket',
	tags: ['resource type', 'module', 's3'],
  description: 'Store and retrieve files from an S3 Bucket.'
}-->

## S3 Bucket Resource

This custom resource type allows you to store and retrieve files from an [Amazon S3](http://aws.amazon.com/s3/) bucket.

### Installation

In your app's root directory, type `npm install s3-bucket-resource` into the command line or [download the source](https://github.com/deployd/dpd-s3). This should create a `dpd-s3` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before you can use the S3 Bucket resource, you must set the three properties on its "Config" page:

- `bucket`: The name of your S3 Bucket
- `key`: The security key of your S3 Bucket
- `secret`: The secret key of your S3 Bucket

### Usage

#### Upload <!-- ref -->

There are two ways to upload files. Both ways require HTTP access; you cannot upload files with dpd.js.

##### Direct upload 

Send a `POST` request to the url where you want to upload the file, including the file name. Set the `Content-Type` header to that of the file you are uploading and pass the file's content in the request body.

It will return a `200 OK` if the upload was successful. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

	POST /my-bucket/README.txt
	Content-Type: text/plain
	Hello, world!

	200 OK

##### Multipart upload

You can upload files directly from a browser using the `multipart/form-data` type and the `<input type="file" />` tag:

	<form action="/installer-downloads" enctype="multipart/form-data" method="post">
		<input type="file" name="upload" multiple="multiple" />
		<button type="submit">Upload</button>
	</form>

To send a multipart request manually, send a `POST` request to the url where you want to upload the file, *not* including the file name. The `Content-Type` header must be `multipart/form-data`. Set the request body according to the [multipart/form-data standard](http://www.w3.org/TR/html401/interact/forms.html#h-17.13.4.2).

If the upload was successful and there is a `Referrer` header on the request (e.g. if it was submitted as a form from a browser), the response will redirect to the referrer. Otherwise, it will return `200 OK`. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

#### Retrieving files <!-- ref -->

To download a file, send a `GET` request to the url where the file exists. 

	GET /my-bucket/README.txt

	200 OK
	Content-Type: text/plain
	Hello, world!

#### Deleting files <!-- ref -->

To delete a file, send a `DELETE` request to the url where the file exists.

	DELETE /my-bucket/README.txt

	200 OK

This can also be done with dpd.js:

	dpd.mybucket.del('README.txt', function(response, error) {
		// Do something
	});

### Events

The S3 Bucket Resource has three events:

- `On Upload`: Executed before a file is uploaded to S3.
- `On Get`: Executed before a file is downloaded from S3.
- `On Delete`: Executed before a file is deleted.

### Event API

#### url <!-- api -->

The URL of the request. Does not include the resource's name; if the request URL is `/my-bucket/README.txt`, the `url` property will be `/README.txt`.

#### fileSize  <!-- api -->

Only available in `On Upload`. The size of the file, in bytes.

		// On Upload
		// Set a limit on file size
		if (fileSize > 1024*1024*1024) { // 1GB
			cancel("File is too big; limit is 1GB");
		}

#### fileName <!-- api -->

Only available in `On Upload`. The name of the file that is being uploaded.

		// On Upload
		dpd.uploads.post({ filename: fileName, creator: me.id }, function() {})
<!--{
	title: 'Dpd.js for Custom Resources',
	tags: ['dpd.js', 'custom', 'resource']
}-->

## Dpd.js for Custom Resources

Because Custom Resource Types can specify APIs very different from a Collection, Dpd.js acts as a generic HTTP library for Custom Resources.

### Accessing the Resource

The API for your Resource is automatically generated as `dpd.[resource]`.

Examples:

	dpd.emails
	dpd.addfollower
	dpd.uploads

*Note: If your Resource name has a dash in it (e.g. `/add-follower`), the dash is removed when accessing it in this way (e.g. `dpd.addfollower`).*

You can also access your resource by using `dpd(resourceName)` as a function.

Examples:

	dpd('emails')
	dpd('add-follower')
	dpd('uploads')

### Callbacks

Every function in the Dpd.js API takes a callback function (represented by `fn` in the docs) with the signature `function(result, error)`.

The callback will be executed asynchronously when the API has received a response from the server.

The `result` argument differs depending on the function. If the result failed, it will be `null` and the `error` argument will contain the error message.

The `error` argument, if there was an error, is an object:

 - `status` (number): The HTTP status code of the request. Common codes include:
	- 400 - Bad Request: The request contained invalid data and could not be completed
	- 401 - Unauthorized: The current session is not authorized to perform that action
	- 500 - Internal Server Error: Something went wrong on the server
 - `message` (string): A message describing the error. Not always present.
 - `errors` (object): A hash of error messages corresponding to the properties of the object that was sent - usually indicates validation errors. Not always present.

Examples of errors:

	{
		"status": 401,
		"message": "You are not allowed to access that resource!"
	}

<!--...-->

	{
		"status": 400,
		"errors": {
			"title": "Title must be less than 100 characters",
			"category": "Not a valid category"
		}
	}



#### Promises

Every function in the collection API returns a promise.
We use the [`ayepromise` library](https://github.com/cburgmer/ayepromise) (which follows the [Promises/A+ 1.1 specs](https://promisesaplus.com/)).
To learn how to use promises, please, refer [to this article](http://www.html5rocks.com/en/tutorials/es6/promises).

The first callback contains the same `result` same with the classic callbacks.
The second callback contains the `error` object as described above.
Here's an example to use promises within dpd.js:

	dpd.todos.post({message: "Hello world"}).then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err); // display an error if the request failed
	});

<!--...-->

	dpd.todos.get('1234324324').then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err.errors.message); // display the error message
	});


### get() <!-- api -->

	dpd.[resource].get([func], [path], [query], fn)

Makes a GET HTTP request at the URL `/<resource>/<func>/<path>`, using the `query` object as the query string if provided.

- `func` - A special identifier, i.e. `/me`.
- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `fn` - Callback `function(result, error)`.

###  post() <!-- api -->

	dpd.[resource].post([path], [query], body, fn)

Makes a POST HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### put() <!-- api -->

	dpd.[resource].put([path], [query], body, fn)

Makes a PUT HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### del() <!-- api -->

	dpd.[resource].del([path], [query], fn)

Makes a DELETE HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `fn` - Callback `function(result, error)`.


### exec() <!-- api -->

	dpd.[resource].exec(func, [path], [body], fn)

Makes an RPC-style POST HTTP request at the URL `/<resource>/<func>/<path>`. Useful for functions that don't make sense in REST-style APIs, such as `/users/login`.

- `func` - The name of the function to call
- `path` - An identifier for a particular object, usually the id
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### Realtime API

The Generic Realtime API behaves the same way as the [Collection Realtime API](/docs/collections/reference/dpd-js.md#s-Realtime-API).
<!--{
  title: 'Event API for Custom Resources',
  tags: ['event', 'custom', 'resource']
}-->

## Event API for Custom Resources

### Background

Custom Resources may load **event scripts** to allow you to inject business logic during requests to the resource. For example, the collection resource exposes an event called *validate*. Given the following todo resource folder:

    /my-app
      /resources
        /todos
          validate.js

The collection resource would load the contents of `validate.js` as the `validate` event.

### Default Event Script Domain

Event scripts do not share a global scope with other modules in your app. Instead each time an event script is run, a new scope is created for it.

The following functions and objects are available to all event scripts.

#### ctx <!-- ctx -->

The context of the request. This object contains everything from the request (request, response, body, headers, etc...):

    // Example:
    if (ctx && ctx.req && ctx.req.headers && ctx.req.headers.host !== '192.168.178.34:2403') {
      cancel("You are not authorized to do that", 401);
    }

The entire object is [available as a gist here](https://gist.github.com/NicolasRitouet/2fc5dd20f3af7dc7e192).

#### me <!-- api -->

The current user if one exists on the current `Context`.

#### isMe() <!-- api -->

    isMe(id)

Returns true if the current user (`me`) matches the provided `id`.

#### this <!-- api -->

If the resource does not implement a custom domain, this will be an empty object. Otherwise `this` usually refers to the current domain's instance (eg. an object in a collection).

#### cancel() <!-- api -->

    cancel(message, [statusCode])

Stops the current request with the provided error message and HTTP status code. Status code defaults to `400`.

#### cancelIf(), cancelUnless() <!-- api -->

    cancelIf(condition, message, [statusCode])
    cancelUnless(condition, message, [statusCode])

Calls `cancel(message, statusCode)` if the provided condition is truthy (for `cancelIf()`) or falsy (for `cancelUnless`).

#### internal <!-- api -->

A boolean property, true if this request has been initiated by another script.

#### isRoot <!-- api -->

A boolean property, true if this request is authenticated as root (from the dashboard or a custom script).

#### query <!-- api -->

The current HTTP query. (eg ?foo=bar - query would be {foo: 'bar'}).

#### emit() <!-- api -->

    emit([userCollection, query], message, [data])

Emits a realtime message to the client. You can use `userCollection` and `query` parameters to limit the message broadcast to specific users.

#### console <!-- api -->

Support for console.log() and other console methods.
<!--{
  title: 'Using a Custom Resource Type',
  tags: ['resource type', 'module']
}-->

### Using a Custom Resource Type

Deployd modules can register new *Resource Types*, which can be created with a route and configured per instance. Deployd comes with two built-in Resource Types: "Collection" and "User Collection". 

To add more Resource Types, you can [install](/docs/using-modules/installing-modules.md) a module that includes one. The examples on this page use the [Event resource](/docs/using-modules/official/event.md).

#### Creating an instance of a Custom Resource Type

Once the module is properly installed, you can add the custom resource just like a Collection. Custom Resources will usually have an asterisk <i class="icon-asterisk"></i> icon. 

![Creating an Event resource](/tutorials/resource-type/creating-custom-resource.png)

*Note: After adding any module, you will have to restart the Deployd server to see its effects. If you don't see the custom resource type in the list, you may have to restart the server and refresh the dashboard.*

#### Configuring a Custom Resource Type

See the documentation of your Custom Resource Type module for details on configuration options. Most custom resource types implement a "Config" page and an "Events" page.

The "Config" page can take different forms. For very basic modules, it's often a simple JSON editor where you can enter optional values. Others will list their available configuration values in a form.

The "Events" page is similar to the Collection "Events" page.

Depending on the complexity of the custom resource type, it may have different configuration pages.<!--{
  title: 'Installing a Module',
  tags: ['installing', 'module']
}-->

## Installing a Module

### From NPM

Deployd modules are 100% compatible with [node modules](http://npmjs.org). This means you can install a module with [npm](http://npmjs.org) from your project's root directory.

    cd my-dpd-project
    mkdir -p node_modules
    npm install my-dpd-module

To find deployd modules available on npm [search for `dpd`](https://encrypted.google.com/search?q=dpd&q=site:npmjs.org&hl=en).

If you need to use a task manager like Grunt or Gulp for your development environement, you'll have to add a package.json as explained [in this page](/docs/server/use-grunt-or-gulp.md).

### From Source

You can also install a module from source by putting it in your project's `node_modules` folder. Even a single file is valid (eg: `/node_modules/foo.js`).
<!--{
  title: 'Email',
  tags: ['resource type', 'module', 'email'],
  description: 'Send emails from clients or during events.'
}-->

## Email Resource

This custom resource type allows you to send an email to your users.

The Email resource is built on the [Nodemailer](https://github.com/andris9/Nodemailer) module for Node.js; much of the documentation on this page is taken from their README.

### Installation

In your app's root directory, type `npm install dpd-email` into the command line or [download from source](https://github.com/deployd/dpd-email). This should create a `dpd-email` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before using the email resource, you must go to its Dashboard page and configure it.

These settings are required:

- `host`: The hostname of your SMTP provider.
- `port`: The port number of your SMTP provider. Defaults to 25; 587 is also common.
- `ssl`: If checked, use SSL to communicate with your SMTP provider. Unneeded for port 587; as it will automatically upgrade to a secure connection.
- `username`: The SMTP username for your app.
- `password`: The SMTP username for your app.

These settings are optional:

- `defaultFromAddress`: A "from" email address to provide by default. If this is not provided, you will need to provide this address in every request.
- `internalOnly`: If checked, only allow internal requests (such as those from events) to send emails. Recommended for security.
- `productionOnly`: If checked, attempting to send an email in the `development` environment will simply print it to the Deployd console. 

### Usage

To send an email, call `dpd.email.post(options, callback)` (replacing `email` with your resource name). The `options` argument is an object:

- `from`: The email address of the sender. Required if `defaultFromAddress` is not configured. All e-mail addresses can be plain (`sender@server.com`) or formatted (`Sender Name <sender@server.com>`)
- `to`: Comma separated list of recipients e-mail addresses that will appear on the To: field
- `cc`: Comma separated list of recipients e-mail addresses that will appear on the Cc: field
- `bcc`: Comma separated list of recipients e-mail addresses that will appear on the Bcc: field
- `subject`: The subject of the e-mail.
- `text`: The plaintext version of the message
- `html`: The HTML version of the message

### Example Usage

    // On POST /users

    dpd.email.post({
      to: this.email,
      from: "deployd-server@example.com", 
      subject: "MyApp registration",
      text: this.username + ",\n\n" +
            "Thank you for registering for MyApp!"
    }, function() {});
<!--{
  title: 'Event Resource',
  tags: ['resource type', 'module'],
  description: 'Create custom events at a specified URL.'
}-->

## Event Resource

This custom resource type allows you to write an event that will run when the resource's route receives a `GET` or `POST` request.

### Installation

In your app's root directory, type `npm install dpd-event` into the command line or [download the source](https://github.com/deployd/dpd-event). This should create a `dpd-event` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Usage

The `On POST` event will be executed when the resource's route (or a subroute) receives a `POST` request, and likewise with the `On GET` event.

It is strongly recommended that you reserve the `On GET` event for operations that return a value, but don't have any side effects of modifying the database or performing some other operation.  

If your resource is called `/add-follower`, you can trigger its `POST` event from dpd.js:

    dpd.addfollower.post('320d6151a9aad8ce', {userId: '6d75e75d9bd9b8a6'}, function(result, error) {
      // Do something
    })

And over HTTP:

    POST /add-follower/320d6151a9aad8ce
    Content-Type: application/json
    {
      "userId": "6d75e75d9bd9b8a6"
    }

### Event API

In addition to the generic [custom resource event API](/docs/using-modules/reference/event-api.md), the following functions and variables are available while scripting the Event resource:


#### setResult(result) <!-- api -->

Sets the response body. The `result` argument can be a string or an object.

    // On GET /top-score
    dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
      setResult(result[0]);
    });

#### url <!-- api -->

The URL of the request, without the resource's base URL. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce`, the `url` value will be `/320d6151a9aad8ce`.

    // On GET /statistics
    // Get the top score
    if (url === '/top-score') {
      dpd.scores.get({$limit: 1, $sort: {score: -1}, function(result) {
        setResult(result[0]);
      });
    }

#### parts <!-- api -->

An array of the parts of the url, separated by `/`. If the resource is called `/add-follower` and receives a request at `/add-follower/320d6151a9aad8ce/6d75e75d9bd9b8a6`, the `parts` value will be `['320d6151a9aad8ce', '6d75e75d9bd9b8a6']`.

    // On POST /add-score
    // Give the specified user (/add-score/:userId) 5 points
    var userId = parts[0];
    if (!userId) cancel("You must provide a user");

    dpd.users.put({id: userId}, {score: {$inc: 5}}, function(result, err) {
      if (err) cancel(err);
    });

#### query <!-- api -->

The query string object.
  
    // On GET /sum
    // Return the sum of the a and b properties (/sum?a=5&b=1)

    setResult(query.a + query.b);

#### body <!-- api -->

The body of the request.

    // On POST /sum
    // Return the sum of the a and b properties {a: 5, b: 1}

    setResult(body.a + body.b);<!--{
	title: 'Importer',
	tags: ['resource type', 'module', 'import'],
  description: 'Import collections from existing MongoDBs.'
}-->

## Importer

This custom resource type allows you to import collections from an existing MongoDB.

### Installation

Create a project. Then install the dpd-importer module.

    dpd create my-app
    cd my-app
    mkdir node_modules
    npm install dpd-importer
    dpd -d
    
In your dashboard - click the green new resource button and choose **Importer**.

Give the new resource the default name "/importer". Open it by clicking "IMPOTER" in the left menu.

Enter the information of your old MongoDB server. Clicking on **Start Import** will start creating deployd collections from data in the provided db by streaming data directly from the old db into your new deployd db. The importer will do its best to create properties based on the types it infers from your data.<!--{
	title: 'S3 Bucket',
	tags: ['resource type', 'module', 's3'],
  description: 'Store and retrieve files from an S3 Bucket.'
}-->

## S3 Bucket Resource

This custom resource type allows you to store and retrieve files from an [Amazon S3](http://aws.amazon.com/s3/) bucket.

### Installation

In your app's root directory, type `npm install s3-bucket-resource` into the command line or [download the source](https://github.com/deployd/dpd-s3). This should create a `dpd-s3` directory in your app's `node_modules` directory.

See [Installing Modules](/docs/using-modules/installing-modules.md) for details.

### Configuration

Before you can use the S3 Bucket resource, you must set the three properties on its "Config" page:

- `bucket`: The name of your S3 Bucket
- `key`: The security key of your S3 Bucket
- `secret`: The secret key of your S3 Bucket

### Usage

#### Upload <!-- ref -->

There are two ways to upload files. Both ways require HTTP access; you cannot upload files with dpd.js.

##### Direct upload 

Send a `POST` request to the url where you want to upload the file, including the file name. Set the `Content-Type` header to that of the file you are uploading and pass the file's content in the request body.

It will return a `200 OK` if the upload was successful. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

	POST /my-bucket/README.txt
	Content-Type: text/plain
	Hello, world!

	200 OK

##### Multipart upload

You can upload files directly from a browser using the `multipart/form-data` type and the `<input type="file" />` tag:

	<form action="/installer-downloads" enctype="multipart/form-data" method="post">
		<input type="file" name="upload" multiple="multiple" />
		<button type="submit">Upload</button>
	</form>

To send a multipart request manually, send a `POST` request to the url where you want to upload the file, *not* including the file name. The `Content-Type` header must be `multipart/form-data`. Set the request body according to the [multipart/form-data standard](http://www.w3.org/TR/html401/interact/forms.html#h-17.13.4.2).

If the upload was successful and there is a `Referrer` header on the request (e.g. if it was submitted as a form from a browser), the response will redirect to the referrer. Otherwise, it will return `200 OK`. If there was an error, it will return the error directly from S3. This is usually in XML; see [Amazon's S3 documentation](http://aws.amazon.com/documentation/s3/) for information.

#### Retrieving files <!-- ref -->

To download a file, send a `GET` request to the url where the file exists. 

	GET /my-bucket/README.txt

	200 OK
	Content-Type: text/plain
	Hello, world!

#### Deleting files <!-- ref -->

To delete a file, send a `DELETE` request to the url where the file exists.

	DELETE /my-bucket/README.txt

	200 OK

This can also be done with dpd.js:

	dpd.mybucket.del('README.txt', function(response, error) {
		// Do something
	});

### Events

The S3 Bucket Resource has three events:

- `On Upload`: Executed before a file is uploaded to S3.
- `On Get`: Executed before a file is downloaded from S3.
- `On Delete`: Executed before a file is deleted.

### Event API

#### url <!-- api -->

The URL of the request. Does not include the resource's name; if the request URL is `/my-bucket/README.txt`, the `url` property will be `/README.txt`.

#### fileSize  <!-- api -->

Only available in `On Upload`. The size of the file, in bytes.

		// On Upload
		// Set a limit on file size
		if (fileSize > 1024*1024*1024) { // 1GB
			cancel("File is too big; limit is 1GB");
		}

#### fileName <!-- api -->

Only available in `On Upload`. The name of the file that is being uploaded.

		// On Upload
		dpd.uploads.post({ filename: fileName, creator: me.id }, function() {})
<!--{
	title: 'Dpd.js for Custom Resources',
	tags: ['dpd.js', 'custom', 'resource']
}-->

## Dpd.js for Custom Resources

Because Custom Resource Types can specify APIs very different from a Collection, Dpd.js acts as a generic HTTP library for Custom Resources.

### Accessing the Resource

The API for your Resource is automatically generated as `dpd.[resource]`.

Examples:

	dpd.emails
	dpd.addfollower
	dpd.uploads

*Note: If your Resource name has a dash in it (e.g. `/add-follower`), the dash is removed when accessing it in this way (e.g. `dpd.addfollower`).*

You can also access your resource by using `dpd(resourceName)` as a function.

Examples:

	dpd('emails')
	dpd('add-follower')
	dpd('uploads')

### Callbacks

Every function in the Dpd.js API takes a callback function (represented by `fn` in the docs) with the signature `function(result, error)`.

The callback will be executed asynchronously when the API has received a response from the server.

The `result` argument differs depending on the function. If the result failed, it will be `null` and the `error` argument will contain the error message.

The `error` argument, if there was an error, is an object:

 - `status` (number): The HTTP status code of the request. Common codes include:
	- 400 - Bad Request: The request contained invalid data and could not be completed
	- 401 - Unauthorized: The current session is not authorized to perform that action
	- 500 - Internal Server Error: Something went wrong on the server
 - `message` (string): A message describing the error. Not always present.
 - `errors` (object): A hash of error messages corresponding to the properties of the object that was sent - usually indicates validation errors. Not always present.

Examples of errors:

	{
		"status": 401,
		"message": "You are not allowed to access that resource!"
	}

<!--...-->

	{
		"status": 400,
		"errors": {
			"title": "Title must be less than 100 characters",
			"category": "Not a valid category"
		}
	}



#### Promises

Every function in the collection API returns a promise.
We use the [`ayepromise` library](https://github.com/cburgmer/ayepromise) (which follows the [Promises/A+ 1.1 specs](https://promisesaplus.com/)).
To learn how to use promises, please, refer [to this article](http://www.html5rocks.com/en/tutorials/es6/promises).

The first callback contains the same `result` same with the classic callbacks.
The second callback contains the `error` object as described above.
Here's an example to use promises within dpd.js:

	dpd.todos.post({message: "Hello world"}).then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err); // display an error if the request failed
	});

<!--...-->

	dpd.todos.get('1234324324').then(function(todo) {
		// do something with todo
		console.log(todo); // display {id: "###", message: 'Hello world'}
	}, function(err) {
		// do something with the error
		console.log(err.errors.message); // display the error message
	});


### get() <!-- api -->

	dpd.[resource].get([func], [path], [query], fn)

Makes a GET HTTP request at the URL `/<resource>/<func>/<path>`, using the `query` object as the query string if provided.

- `func` - A special identifier, i.e. `/me`.
- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `fn` - Callback `function(result, error)`.

###  post() <!-- api -->

	dpd.[resource].post([path], [query], body, fn)

Makes a POST HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### put() <!-- api -->

	dpd.[resource].put([path], [query], body, fn)

Makes a PUT HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided and `body` as the request body.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### del() <!-- api -->

	dpd.[resource].del([path], [query], fn)

Makes a DELETE HTTP request at the URL `/<resource>/<path>`, using the `query` object as the query string if provided.

- `path` - An identifier for a particular object, usually the id
- `query` - An object defining the querystring. If the object is complex, it will be serialized as JSON and passed as the `q` parameter.
- `fn` - Callback `function(result, error)`.


### exec() <!-- api -->

	dpd.[resource].exec(func, [path], [body], fn)

Makes an RPC-style POST HTTP request at the URL `/<resource>/<func>/<path>`. Useful for functions that don't make sense in REST-style APIs, such as `/users/login`.

- `func` - The name of the function to call
- `path` - An identifier for a particular object, usually the id
- `body` - The body of the request; will be serialized as JSON and sent with `Content-Type: application/json` header.
- `fn` - Callback `function(result, error)`.

### Realtime API

The Generic Realtime API behaves the same way as the [Collection Realtime API](/docs/collections/reference/dpd-js.md#s-Realtime-API).
<!--{
  title: 'Event API for Custom Resources',
  tags: ['event', 'custom', 'resource']
}-->

## Event API for Custom Resources

### Background

Custom Resources may load **event scripts** to allow you to inject business logic during requests to the resource. For example, the collection resource exposes an event called *validate*. Given the following todo resource folder:

    /my-app
      /resources
        /todos
          validate.js

The collection resource would load the contents of `validate.js` as the `validate` event.

### Default Event Script Domain

Event scripts do not share a global scope with other modules in your app. Instead each time an event script is run, a new scope is created for it.

The following functions and objects are available to all event scripts.

#### ctx <!-- ctx -->

The context of the request. This object contains everything from the request (request, response, body, headers, etc...):

    // Example:
    if (ctx && ctx.req && ctx.req.headers && ctx.req.headers.host !== '192.168.178.34:2403') {
      cancel("You are not authorized to do that", 401);
    }

The entire object is [available as a gist here](https://gist.github.com/NicolasRitouet/2fc5dd20f3af7dc7e192).

#### me <!-- api -->

The current user if one exists on the current `Context`.

#### isMe() <!-- api -->

    isMe(id)

Returns true if the current user (`me`) matches the provided `id`.

#### this <!-- api -->

If the resource does not implement a custom domain, this will be an empty object. Otherwise `this` usually refers to the current domain's instance (eg. an object in a collection).

#### cancel() <!-- api -->

    cancel(message, [statusCode])

Stops the current request with the provided error message and HTTP status code. Status code defaults to `400`.

#### cancelIf(), cancelUnless() <!-- api -->

    cancelIf(condition, message, [statusCode])
    cancelUnless(condition, message, [statusCode])

Calls `cancel(message, statusCode)` if the provided condition is truthy (for `cancelIf()`) or falsy (for `cancelUnless`).

#### internal <!-- api -->

A boolean property, true if this request has been initiated by another script.

#### isRoot <!-- api -->

A boolean property, true if this request is authenticated as root (from the dashboard or a custom script).

#### query <!-- api -->

The current HTTP query. (eg ?foo=bar - query would be {foo: 'bar'}).

#### emit() <!-- api -->

    emit([userCollection, query], message, [data])

Emits a realtime message to the client. You can use `userCollection` and `query` parameters to limit the message broadcast to specific users.

#### console <!-- api -->

Support for console.log() and other console methods.
<!--{
  title: 'Using a Custom Resource Type',
  tags: ['resource type', 'module']
}-->

### Using a Custom Resource Type

Deployd modules can register new *Resource Types*, which can be created with a route and configured per instance. Deployd comes with two built-in Resource Types: "Collection" and "User Collection". 

To add more Resource Types, you can [install](/docs/using-modules/installing-modules.md) a module that includes one. The examples on this page use the [Event resource](/docs/using-modules/official/event.md).

#### Creating an instance of a Custom Resource Type

Once the module is properly installed, you can add the custom resource just like a Collection. Custom Resources will usually have an asterisk <i class="icon-asterisk"></i> icon. 

![Creating an Event resource](/tutorials/resource-type/creating-custom-resource.png)

*Note: After adding any module, you will have to restart the Deployd server to see its effects. If you don't see the custom resource type in the list, you may have to restart the server and refresh the dashboard.*

#### Configuring a Custom Resource Type

See the documentation of your Custom Resource Type module for details on configuration options. Most custom resource types implement a "Config" page and an "Events" page.

The "Config" page can take different forms. For very basic modules, it's often a simple JSON editor where you can enter optional values. Others will list their available configuration values in a form.

The "Events" page is similar to the Collection "Events" page.

Depending on the complexity of the custom resource type, it may have different configuration pages.
