#Configuration

The server side application can be configured by editing the **config.json** file in the root directory of the application. You should also find a sample configuration file that contains some useful information:


    "port": 3000, //the port to serve on
    "datapath": "c:/vwfData", //the database location
    "admin": "admin", //the username of the administrator
    "logLevel": 1, //the vebosity of the console output
    "build": false, //build the require js modules
    "minify": false, //minify javascript on serve
    "compile": false, //compile with the closure conpiler
    "version": 1, //the version number to use for URL versioning. Must be an integer!
    "useVersioning": false, //when true, the server will use a url prefix to identify the software version

    "_3DRAPI": null, //the endpoint to use to access the service. Null defaults to the public 3DR instance
    "_3DRAPIKey": null, //the api key to use for all requests. Null defaults to the public API key
    "_3DRUser": null, //username server identifies itself as. Null defaults to Anonymous
    "_3DRPassword": null, //password for the server user. Null defaults to Anonymous
    "_3DRUseAuth": false, //use anonymous access or not. Null defaults to anonymous.

    "sendEmails": false, //send emails to new users and on password reset (note, password reset is really not useful without this!) 
    "emailFrom": "", //the sender as it will appear in the emails to users
    "emailService": "", //the service provider for outgoing emails. See the nodemailer docs
    "emailPassword": "", //the service password for outgoing emails. See the nodemailer docs
    "emailUsername": "", //the service username for outgoing emails. See the nodemailer docs

    "lrsEndpoint": null,
    "lrsUsername": "",
    "lrsPassword": "",

    "pfx": null, //the path and name of the PFX credential file. If not null, server will use HTTPS and WSS
    "pfxPassphrase": null, //the passphrase to open the pfx file
    "sslPort": 443, //the port to use for the secure server. Requests to the nonSSL port will redirect here

    "sslCA": ["./ca1.pem", "./ca2.pem"], //intermediate certificate authority

    "sessionKey": "virtual", //enter a good random string here for security of sessions
    "sessionSecret": "unsecure cookie secret", //enter a good random string here for security of sessions

    //use the the following settings to enable social media logins
    "facebook_app_id": null,
    "facebook_app_secret": null,
    "facebook_callback_url": "http://localhost:3000/adl/sandbox/auth/facebook/callback",
    "twitter_consumer_key": null,
    "twitter_consumer_secret": null,
    "twitter_callback_url": "http://localhost:3000/adl/sandbox/auth/twitter/callback",
    "google_client_id": null,
    "google_client_secret": null,
    "google_callback_url": "http://localhost:3000/adl/sandbox/auth/google/callback"

There are also a few command line switches you can use to override the settings in the config file. They are:

1. **-d**  -set the data path. Default is "./data"
1. **-p**  -set the port number. Default is 3000
1. **-ls** -simulate a given number of milliseconds latency for each message to the reflector
1. **-a**  -set the user who should be considered the system administrator. Default is 'admin'
1. **-sp** -the port to use when using SSL
1. **-v**  -enable versioning. All URLs will redirect to {host}/version/{url}. Use for cache busting
1. **-DB** -set the database driver??
1. **-l**  -the verbosity level of the console log
1. **-cc** -activates and specifies versioning??
1. **-ap** -set the default URL for the site
1. **-cluster**  -turns clustering on or off??
1. **-exit**     -quits the process after the build step
1. **-nocache**  -the FileCache will not retain files in memory. Not much reason to disable these days.
1. **-min**      -the server will minify using Uglyify.js??
1. **-compile**  -treats build and compile as the same. the server will build the main RequireJS module. This takes a long time on startup, but reduces the number of requests the client will make by almost 50.
1. **-clean**    -clean??
