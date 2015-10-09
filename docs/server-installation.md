<h1>Server Installation</h1>

[TOC]

# Server Installation

The VW Sandbox server runs under [Node.js](https://nodejs.org/en/) ([v0.12.x](http://nodejs.org/dist/latest-v0.12.x/)), an open-source, cross-platform JavaScript runtime for developing server-side web applications.

1. Clone the VW Sandbox GitHub Repository

	```
	 git clone https://github.com/adlnet/Sandbox
	```

2. Assuming you've installed Node.js (v0.12.x), install the VW Sandbox in the app directory

	```
	npm install
	```

3. Run the server in the app directory

	```
	node app.js
	```

4. With the server running, point web browser to:

	```
	http://localhost:3000
	```

The server can be configured using either command line switches listed below and/or a json configuration file (see the [Configuration](#configuration) section).

## Command Line Switches

Switches and values should be seperated by spaces, and surrounded by quotes when the value contains a space.

* `-a <username>`   	- the username of the user who should be treated as the administrator. Default is 'admin'
* `-ap <url_prefix>`	- default is `/adl/sandbox`. Set the default URL prefix for the site.  At least 3 characters and start with slash (e.g., '/ADL')
* `-cc`					- appends a version string (from [JSON Config File](#json-config-file)) to all application string to all URLs to prevent client's from caching old code.  All requests will redirect to {host}/version/{url} with the version number in Version.js

!!! note:

	The -cc option is helpful to ensure client caches are overridden when new versions are available.

* `-clean`    			- deletes a previous build.  `See -compile`. 
* `-config <file>`		- point to a different [JSON Config File](#json-config-file) than the default config.json in the app directory
* `-compile` 			- the server will build the main RequireJS module. This takes a long time on startup, but reduces the number of requests the client will make by almost 50.  The application will not be rebuilt if the source has changed.  You must start with `-clean` to rebuild.
* `-d <directory>`  	- the path to the data directory. The default is `./data`.  The [default database driver](architecture.md#data-access-layer) stores all of its data in the data directory.  

!!! note:

	If the data directory, either specified or unspecified, doesn't exist, the VW Sandbox will attempt to create it.


* `-DB <driver name>` 	- set the database driver
* `-exit`				- quits the process after the build step
* `-ls <milliseconds>`	- simulate a given number of milliseconds latency for each message to the reflector
* `-min`				- the server will minify using Uglyify.js. 
* `-nocache`			- the FileCache will not retain files in memory.  The server will not cache files in memory.  They will be served from disc on every request.  Cache is kept in main memory and limited to main memory capacity.
* `-p <por>`			- the port to use. Default is 3000
* `-sp <port>`			- the port to use when using SSL



So, possible production settings are as follows:

```
node app.js -p 80 -minify -compile -v
```

## JSON Config File

The server side application can also be configured by editing the `config.json` file in the root directory of the application. 

!!! note:

	Command line switches will override JSON configuration file values.  Also remember that you must restart the VW Sandbox server when making changes to the configuration file.

You should find a sample configuration file in the app directory that contains some useful information.  A copy of the sample configuration file is below.

!!! Warning:

	The comments below are not valid JSON and must be removed before using.

```
    "port": 3000, 								// the port to serve on
    "datapath": "c:/vwfData", 					// the database location
    "admin": "admin", 							// the username of the administrator
    "logLevel": 1, 								// the vebosity of the console output
    "build": false, 							// build the require js modules
    "minify": false, 							// minify javascript on serve
    "compile": false, 							// compile with the closure conpiler
    "version": 1,								// the version number to use for URL versioning. Must be an integer!
    "useVersioning": false,						// when true, the server will use a url prefix to identify the software version

    "hostAssets": true,							// when true, assets are hosted locally in the data directory
    "remoteAssetServerURL": null, 				// remote URL where the asset server is hosted if assets are not hosted locally
    "sessionSecret": null 						// enter a good random string here for security of sessions

    "_3DRAPI": null, 							// the endpoint to use to access the service. Null defaults to the public 3DR instance
    "_3DRAPIKey": null, 						// the api key to use for all requests. Null defaults to the public API key
    "_3DRUser": null, 							// username server identifies itself as. Null defaults to Anonymous
    "_3DRPassword": null, 						// password for the server user. Null defaults to Anonymous
    "_3DRUseAuth": false, 						// use anonymous access or not. Null defaults to anonymous.

    "sendEmails": false, 						// send emails to new users and on password reset (note, password reset is really not useful without this!) 
    "emailFrom": "", 							// the sender as it will appear in the emails to users
    "emailService": "", 						// the service provider for outgoing emails. See the nodemailer docs
    "emailPassword": "", 						// the service password for outgoing emails. See the nodemailer docs
    "emailUsername": "", 						// the service username for outgoing emails. See the nodemailer docs

    "lrsEndpoint": null,						// the xAPI Learning Record Store (LRS) endpoint
    "lrsUsername": "",							// the xAPI LRS username
    "lrsPassword": "",							// the xAPI LRS password

    "pfx": null, 								// the path and name of the PFX credential file. If not null, server will use HTTPS and WSS
    "pfxPassphrase": null, 						// the passphrase to open the pfx file
    "sslPort": 443, 							// the port to use for the secure server. Requests to the nonSSL port will redirect here

    "sslCA": ["./ca1.pem", "./ca2.pem"], 		// intermediate certificate authority

    "sessionKey": "virtual", 					// enter a good random string here for security of sessions
    "sessionSecret": "unsecure cookie secret", 	// enter a good random string here for security of sessions

    // use the the following settings to enable social media logins

    "facebook_app_id": null,
    "facebook_app_secret": null,
    "facebook_callback_url": "http://localhost:3000/adl/sandbox/auth/facebook/callback",
    "twitter_consumer_key": null,
    "twitter_consumer_secret": null,
    "twitter_callback_url": "http://localhost:3000/adl/sandbox/auth/twitter/callback",
    "google_client_id": null,
    "google_client_secret": null,
    "google_callback_url": "http://localhost:3000/adl/sandbox/auth/google/callback"
```


## Configure 3D Repository Integration

The VW Sandbox allows users to load 3D assets from an ADL 3D Repository instance. Out of the box (and on the hosted copy at [https://sandbox.adlnet.gov/](https://sandbox.adlnet.gov/), the server is configured to connect to a 3D Repository instance hosted by ADL at [http://3dr.adlnet.gov](http://3dr.adlnet.gov). However, as of version 0.4.11, this can be configured to use any 3DR installation. The VW Sandbox server now proxies traffic to and from the connected 3DR instance, so you don’t even necessarily need to make your 3DR publicly visible, so long as the VW Sandbox server can connect to it.  The 3DR integration features are implemented in `/support/server/3dr_proxy.js`.

The settings for connecting to the 3DR server are stored in the `config.json` file, located in the server application root directory.   See the [JSON Config File](#json-config-file) section.  Below are examples of some of the 3DR values:
 
1.  `_3DRAPI`
    *   Use this to configure the endpoint of the 3DR service
    *   Example: `"_3DRAPI":"https://3dr.adlnet.gov/api/rest/"`
2.  `_3DRAPIKey`
    *   Requests to the 3DR API must include a valid API key. You can create a new key under the Account page on your 3DR instance. The public key on the ADL 3DR site is the default, `00-00-00`
    *   Example: `"_3DRAPIKey":"00-00-00"`
3.  `_3DRUser`
    *   The user name to use when the VWS server connects to the 3DR. You can leave this blank, but in doing so, you will only be able to access publicly accessible models. When you input a 3DR username (usually an email address), the permissions of this user will control the access of anyone using the VWS server
    *   Example: `"_3DRUser":"robert.chadwick.ctr@adlnet.gov"`
4.  `_3DRPassword`
    *   The plain text password for the 3DR user. Because the server proxies the traffic, this password will not be visible to VWS users.
    *   Example: `"_3DRPassword":"Password1234_is_very_strong"`
5.  `_3DRUseAuth`
    *   When set to false, the system will ignore the `_3DRUser` and `_3DRPassword` settings. When true, these setting will be used.
    *   Example: `"_3DRUseAuth": true`

!!! note:
	
	The VW Sandbox Editor currently prevents users from loading models that do not have public access, even though, if requested, the server would actually be able to load them.


## Configure Asset Server Integration

The VW Sandbox includes the [Sandbox Asset Server](https://github.com/adlnet/SandboxAssetServer/), which provides a set of CRUD services to manage VW Sandbox assets.  The Sandbox Asset Server runs by default as a VW Sandbox node module where assets are hosted locally.  However, the Sandbox Asset Server can be run as a standalone server and where VW Sandbox assets are hosted remotely.  Remote hosting of assets is helpful when a team is working together on a collection of assets.

The settings for configuring the VW Sandbox asset server node module are stored in the JSON configuration file, located in the server application root directory.   See the [JSON Config File](#json-config-file) section.  Below are examples of some of the Sandbox Asset Server values:

    "hostAssets": true,				// when true, assets are hosted locally in the data directory
    "remoteAssetServerURL": null, 	// remote URL where the asset server is hosted if assets are not hosted locally
    "sessionSecret": null 			// enter a good random string here for security of sessions

## Production Hosting

Our thoughts clustering and load balancing.
