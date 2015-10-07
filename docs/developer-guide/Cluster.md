# Cluster Server

Allows a client to host and serve multiple users. Refers to the file [sandboxCluster.js.](https://github.com/adlnet/Sandbox/blob/development/support/server/sandboxCluster.js "sandboxCluster.js")  More warm and friendly description of what this portion of the program does.

More technical and specific description of what this part of the program does.

<a id='properties'></a>
## Properties

<a id='http'></a>
### http

Type: `function`

require('http') Brief description goes here.

<a id='httpProxy'></a>
### httpProxy

Type: `function`

require('http-proxy') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='async'></a>
### async

Type: `function`

require('async') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='fork'></a>
### fork

Type: `function`

require('child_process').fork Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='request'></a>
### request

Type: `function`

require('request') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='fs'></a>
### fs

Type: `function`

require('fs') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='libpath'></a>
### libpath

Type: `function`

require('path') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='url'></a>
### url

Type: `function`

require('url') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='port'></a>
### port

Type: `number`

Constant value of the port for hosting (3000). Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='count'></a>
### count

Type: `number`

Tracks the number of ... Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='server'></a>
### server

Type: `function`

Function to be assigned later. Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='proxies'></a>
### proxies

Type: `Array`

Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='DB'></a>
### DB

Type: `function`

Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='appPath'></a>
### appPath

Type: `String`

Constant String value "/adl/sandbox". Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='spdy'></a>
### spdy

Type: `function`

require('spdy') Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='datapath'></a>
### datapath

Type: `String`

Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='maxSockets'></a>
### maxSockets

Type: `number`

Constant value of 100 for the http global agent maximum number of sockets. Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='states'></a>
### states

Type: `Object`

Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='compile'></a>
### compile

Type: `Boolean`

Be as specific as possible on the type.  Include ranges or other limitations if possible. And still be brief.

<a id='methods'></a>
##Methods

<a id='readConfigFile'></a>
###readConfigFile(cb)

Reads and saves the configuration into the global scope so other modules can use. Brief description of method.

**Arguments:**

`cb` (`function`)  
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*

<a id='readCommandLine'></a>
###readCommandLine(cb)

Reads and parses flags from the command line. Brief description of method.

Flags:

- `-p` Specify a specific port.
- `-c` Specify a cluster count.
- `-d` Specify a datapath.
- `-ap` Set the default URL for the site.
- `-build`, `-compile` Start the compilation process.

**Arguments:**

`cb` (`function`)
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*

<a id='buildIfRequired'></a>
###buildIfRequired(cb)

Brief description of method.

**Arguments:**

`cb` (`function`)
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*

<a id='startupDB'></a>
###startupDB(cb)

Brief description of method.

**Arguments:**

`cb` (`function`)
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*

<a id='forkChildren'></a>
###forkChildren(cb)

Brief description of method.

**Arguments:**

`cb` (`function`)
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*

<a id='hookUpMessaging'></a>
###hookUpMessaging(cb)

Brief description of method.

**Arguments:**

`cb` (`fucntion`)
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*

<a id='startProxyServer'></a>
###startProxyServer(cb)

Create your custom server and just call `proxy.web()` to proxy a web request to the target passed in the options also you can use `proxy.ws()` to proxy a websockets requestBrief description of method.

**Arguments:**

`cb` (`function`)
Callback function. Brief description of argument. (I have also found it useful to add two spaces at the end of the name and type row, or else the description stays on the same line.  I don't understand why, but it does seem to work.) Or if there are no arguments:

**Returns:**

*(Nothing)*
