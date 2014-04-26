prerender
=========
Full example application that shows how to combine several tools to get a prerendering solution
 that allows to provide html snapshots to searchbots for SPA (that would otherwise be invisible for the search engine).

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
