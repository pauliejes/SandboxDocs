# Asset Server Integration

We use a separate system called the ADL 3D Repository for our asset hosting. You can find the running instance of this system at [https://3DR.adlnet.gov](https://3dr.adlnet.gov/ "ADL 3D Repository"), or visit its repo at [https://github.com/adlnet/3D-Repository](https://github.com/adlnet/3D-Repository "3D Repository on GitHub"). 

Because we can't currently align the permissions between the Sandbox and the 3DR servers, all requests for assets should be proxied through the Sandbox server. The address of the 3DR server to use can be found in the configuration file. See [Configuration](Configuration) or [Asset Server Config](http://sandboxdocs.readthedocs.org/en/latest/Developer%20Guide/Assets/ "Asset Pipeline")

The 3DR integration features are implemented in `/support/server/3dr_proxy.js`. See [File Organization](http://sandboxdocs.readthedocs.org/en/latest/Developer%20Guide/File-Organization/ "File Organization").