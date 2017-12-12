# Workstation setup
Notes to know how I configured my workstation. The base system is `Windows 10` and all instructions use the conventions for this platform. 

Setup customized work environment is hard. I always forget some configuration. This document exists to detail the configuration of my work machine. If I have to change my work station, the configuration I'm going to apply is the one indicated in this document.

> **Note**: All software that I use is free, and can be used in corporate environments for commercial purposes. If any program needs a commercial license it will be indicated.

## Proxy configuration
I set three environment variables to configure the proxy settings only for my user.
* `HTTP_PROXY` and `HTTPS_PROXY`. The format should be: 
`http://<username>:<password>@<host>:<port>`
* `NO_PROXY`: Tipically this contains the value: `127.0.0.1,::1,192.168.*` to exclude from the proxy. Note that is a comma-separated list

References for this topic:
* [Set network range in the no_proxy environment variable](https://unix.stackexchange.com/questions/23452/set-a-network-range-in-the-no-proxy-environment-variable)
* [Set environment variables](https://msdn.microsoft.com/es-es/library/hh272656(v=vs.120).aspx)
* [Proxy settings in Windows](https://www.calazan.com/how-to-set-the-proxy-settings-in-windows-via-command-line/)
