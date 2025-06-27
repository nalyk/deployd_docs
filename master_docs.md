deployd-docs
============

documentation for the deployd platform



Workflow
---------------

    # make sure http-server is installed by (you can use your favour http server)
    # npm install -g http-server

    # start a simple http server
    http-server _site &

    # open browser and go to http://localhost:8080/


    # open another terminal
    node staticGen.js
    # change the docs files, and test the out until it is ok


    # push to git remote origin gh-pages by
    node bin/gen-gh-pages.js


Then, go to github and create a pull request to deployd/docs gh-pages branch.

Thanks
### Quick Start
 
Get Deployd up and running and build your first API with the [getting started guide](/docs/getting-started).

### Example Apps

[Check out the examples](/examples) to see how Deployd APIs are built.

### Guides

[Complete guides](/guides) describing the core concepts needed to build APIs with Deployd, including [accessing collections](/docs/collections), [authenticating users](/docs/users), and [using modules](/docs/using-modules).

### APIs

A [complete list of APIs](/api) available when developing a Deployd app.
