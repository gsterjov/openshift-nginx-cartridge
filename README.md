## Openshift Nginx Cartridge

A cartridge for openshift that enables Nginx to be used as the web server.


### Installation

To install this cartridge use the cartridge reflector when creating an app

	rhc create-app myapp http://cartreflect-claytondev.rhcloud.com/reflect?github=gsterjov/openshift-nginx-cartridge


### Configuration

The cartridge installs two config files. One at <code>$OPENSHIFT_NGINX_DIR/conf/nginx.conf</code> which gets loaded by the executable
and sets up specific app configuration such as logs and pid files.

The config then includes another nginx.conf which must exist at <code>$OPENSHIFT_REPO_DIR/nginx.conf</code>. This config should
contain all your server specific set up including which ip/port to listen on.

The repo nginx.conf is actually seen in your repository as <code>nginx.conf.erb</code> so environment variables can be used
in the config. Every time the server starts it first processes <code>nginx.conf.erb</code>.


A <code>public/</code> folder is included where static content is served by default. However, as can be seen in the <code>nginx.conf.erb</code> file it
is entirely configurable and only exists as a form of documentation.