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

## Putty
Download `PuTTY` from [here](http://www.putty.org/) and add it to the path. To check if all is ok, open a terminal and type `putty`. If putty opens, then all is configured correctly.

### Create putty sessions
To create new sessions using putty complete the fields `host name or IP`, `port`, select the connection type and set a new name to the session usign the `Saved Sessions` field. When done click on the `Save` button.

References:
* [Putty official page](http://www.putty.org/)
* [Save putty session logging](https://stackoverflow.com/questions/21231877/saving-the-putty-session-logging)

## Terminal
I use [`ConEmu`](https://conemu.github.io/) as Windows console, because it allows tabs and more features. I have a custom configuration to create new tasks to open other services. Into the [ConEmu](conemu) directory live my default config file and console background image.

### Open SSH session usign ConEmu
Before open the SSH we need the session configured using putty. When done, open `Settings...` > `Startup` > `Tasks` and select the `+` button. Change the name, apply a hotkey and put into the commands box:
```bat
putty.exe -new_console -load "your_session_name"
```

References:
* [ConEmu main page](https://conemu.github.io/)
* [Change ConEmu default directory](https://superuser.com/questions/482325/change-conemus-default-start-directory)
* [Configure ConEmu with Putty](http://thecrumb.com/2013/03/04/configuring-conemu-and-putty/)

## Programing languages
List of programing languages that I use in my day to day at work. All can be used from the command line and are present in my `Path`.
* [`Go lang`](https://golang.org/)
* [`Oracle Java 8`](http://www.oracle.com/technetwork/es/java/javase/downloads/index.html)
* [`Python 3`](https://www.python.org/downloads/)
* [`Kotlin`](https://kotlinlang.org/)

Important references:
* [How to setup golang](https://golang.org/doc/install)

## Developer tools
I use multiple tools, and the configurations for each one are more different. When possible, each tool has an environment variable for the root directory.

### Git
Download and install `git` from [here](https://git-scm.com/download/win). When installing I prefer to use `nano` as text editor. To configure the global settings
```sh
git config --global user.name "name"
git config --global user.email "email"
```
Interesting links:
* [Can I recover a branch after it's deletion?](https://stackoverflow.com/questions/3640764/can-i-recover-a-branch-after-its-deletion-in-git/3640806#3640806)
* [Delete branches locally and remotely](https://stackoverflow.com/questions/2003505/how-do-i-delete-a-git-branch-both-locally-and-remotely/2003515#2003515)
* [Pushing code to two remotes](https://stackoverflow.com/questions/14290113/git-pushing-code-to-two-remotes/14290145#14290145)
* [Accept a self signed certificate](https://stackoverflow.com/questions/11621768/how-can-i-make-git-accept-a-self-signed-certificate/11622001#11622001)
* [Git documentation](https://git-scm.com/docs)

### Gradle
Download it from [here](https://gradle.org/install/). I always use the complete flavor, that comes with docs and sources. I added gradle to the `Path` using the `GRADLE_HOME` variable. To configure Gradle to be used with a corporate proxy I need to create the file `<user.home>\.gradle\gradle.properties` and set the proxy settings to it. See [the default gradle properties file](gradle).

References:
* [Gradle main page](https://gradle.org/)
* [Configure Gradle to use a proxy](https://docs.gradle.org/current/userguide/build_environment.html)

### Maven
Download the latest version from [here](https://maven.apache.org/download.cgi). Extract and create the environment variable `MAVEN_HOME`. Add to the `Path`. To configure Maven to use the proxy, you need to add a new setting to the `settings.xml` file from the `<user.home>\.m2` directory. If the file not exists then we will need to create it. See the [maven example file](maven)

References:
* [Maven home](https://maven.apache.org/)
* [Configuring a proxy](https://maven.apache.org/guides/mini/guide-proxies.html)

### Ant
Download the latest version from [here](http://ant.apache.org/bindownload.cgi). Create the `ANT_HOME` environment variable and add it to the `Path`

References:
* [Apache ant home page](http://ant.apache.org/)

### Postman
Download and install from [here](https://www.getpostman.com/)
* [Official web page](https://www.getpostman.com/)
* [Create collections](https://www.getpostman.com/docs/postman/collections/creating_collections)
* [Mock server](https://www.getpostman.com/docs/postman/mock_servers/setting_up_mock)
* [API security testing](https://blog.smartbear.com/apis/api-security-testing-how-to-hack-an-api-and-get-away-with-it-part-1-of-3/)
