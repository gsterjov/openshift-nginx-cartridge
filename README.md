## Openshift Nginx Cartridge

A cartridge for openshift that enables Nginx to be used as the web server.


### Installation

To install this cartridge use the cartridge reflector when creating an app

	rhc create-app myapp http://cartreflect-claytondev.rhcloud.com/reflect?github=gsterjov/openshift-nginx-cartridge


### Configuration

The cartridge installs two config files. One at  *$OPENSHIFT_NGINX_DIR/conf/nginx.conf*  which gets loaded by the executable
and sets up specific app configuration such as logs and pid files.

The config then includes another nginx.conf which must exist at  *$OPENSHIFT_REPO_DIR/nginx.conf*. This config should
contain all your server specific set up including which ip/port to listen on.

The repo nginx.conf is actually seen in your repository as  **nginx.conf.erb**  so environment variables can be used
in the config. Every time the server starts it first processes  *nginx.conf.erb*.


A  *public/*  folder is included where static content is served by default. However, as can be seen in the  *nginx.conf.erb*  file it
is entirely configurable and only exists as a form of documentation.