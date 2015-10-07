# Installing a copy of the VW Sandbox server on your own machine.

The VW Sandbox server runs under [Node.js](https://nodejs.org/en/) ([v0.12.x](http://nodejs.org/dist/latest-v0.12.x/)), an open-source, cross-platform JavaScript runtime for developing server-side web applications.

#### **FOR WINDOWS**
To start, download the entire repository as a ZIP file (be sure to get the node_threejs branch). Unzip this file onto a directory on your local computer. Lets say, for example, c:\SandboxServer\. 

Download the supporting media assets. You can find them at http://3dr.adlnet.gov/dev/VWFSupportFiles.zip.

Unzip this file into another directory. Lets say c:\SandboxData\. Be sure to keep the directory structure inside the zip file intact, as it is important. 

Now, you can run the server. Navigate into the folder where you unzipped the source repository (for example, c:\SandboxServer). Execute the command:

`node.exe app.js -d "C:\SandboxData" -p 80`

This tells the server to run, serving the media assets from the c:\SandboxData directory, and using port 80.

The server has several command line switches. Switches and values should be seperated by spaces, and surrounded by quotes when the value contains a space.

* -p   - the port to use. Default is 3000
* -d   - the path to the data directory. The default is "./data"

  *NOTE:* If the data directory, either specified or unspecified, doesn't exist, the Sandbox will attempt to create it.

* -a   - the username of the user who should be treated as the administrator. Default is 'admin'
* -l   - the verbosity level of the console log
* -v   - enable versioning. All requests will forward to a URL with the version number in Version.js
* -nocache - the FileCache will not retain files in memory. Not much reason to disable this these days.
* -compile - the server will build the main RequireJS module. This takes a long time on startup, but reduces the number of requests the client will make by almost 50.
* -min   - the server will minify using Uglyify.js. 

So, production settings:
`node.exe app.js -d "C:\SandboxData" -p 80 -minify -compile -v`

#### **FOR MACINTOSH**
1. Download Node.js from http://nodejs.org/download/
1. Download the entire ADL Sandbox repository as a ZIP file (be sure to get the master branch) from https://github.com/adlnet/Sandbox/archive/master.zip
1. Download the supporting VWF media assets from http://3dr.adlnet.gov/dev/VWFSupportFiles.zip.

1. Install Node.js , afterwards you'll be asked to confirm /usr/local/bin is in your $PATH 
1. Open up the Terminal and execute  "ls /usr/local/bin"  you should see "node" and "npm" as an output. NPM is Node Package Manager, it is installed along with Node.
1. If you like, you can verify the installation of node and npm by executing "node -v" and "npm -v" respectively.


1. Unzip the Node_threejs.zip file into another folder, lets say "SandboxServer" on your local computer.
1. Unzip VWFSupportFiles.zip into another folder, lets say "SandboxData".  Be sure to keep the directory structure inside the zip file intact, as it is important. 
1. Now, you can run the server. Navigate into the folder where you unzipped the source repository (for example, SandboxServer). Execute the command:

        % node app.js -d SandboxData