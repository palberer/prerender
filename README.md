prerender
=========
Full example application that shows how to combine several tools to get a prerendering solution
 that allows to provide html snapshots to searchbots for SPA (that would otherwise be invisible for the search engine).

 Note: I tried this on linux (fedora core 20) only.

- uses nginx to host a local copy of the angular-phonecat example application
    - hostname: tutorial.local.dev
    - port: 80

- uses service from prerender.io to do the actual prerendering
    - port: 3000

- uses nginx to expose this service
    - hostname: prerender.local.dev
    - port: 80

- uses nginx to route traffic from search bots to the prerender.io service

You need to modify your hosts file with the following entries:

    127.0.0.1   tutorial.local.dev
    127.0.0.1   prerender.local.dev

In order to try out the whole example, you need to:
- install node, nginx and bower
- run "bower install" to install the dependencies
- launch the prerendering service from folder prerender.io via "node server.js"
- launch nginx using the local config file
- visit http://tutorial.local.dev to see that the web is running
- visit http://prerender.local.dev/http://tutorial.local.dev to see that the prerendering service is running
- disable javascript in your browser and visit http://tutorial.local.dev?_escaped_fragment_ -> you should get the same view like in step 3.
- you can also try to have javascript enabled and visit http://tutorial.local.dev?_escaped_fragment_ -> the browser is getting the prerender view, but angular still kicks in and the page is running as a SPA!
