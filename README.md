privoxy-adblock
===============

A bash script for OS X that converts adblock lists to privoxy's format.

Based on code by Andrwe Lord Weber found [here](http://andrwe.org/scripting/bash/privoxy-blocklist). The original script did not work well in OS X due to the fact that it depended on `pidof` and other GNU/Linux specific behavior.

This script is modified to work in an OS X environment and does not require root privileges.

**Note:** This script requires `wget` to be installed on the system.

Usage
-----
By default, this script fetches the easylist script and installs it into `/usr/local/etc/privoxy`. If that is not appropriate for your system, parameters can be passed to control the behavior of the script.

    $ privoxy-adblock.sh [-d] [-p <privoxy config dir>] [-u <url1>] [-u <url2>]...

| Switch/Parameter        | Description                             |
| :---------------------: | --------------------------------------- |
| -d                      | Turn on debugging                       |
| -p &lt;privoxy path&gt; | Path to privoxy configuration directory |
| -u &lt;url&gt;          | Downloads/converts adblock filter list  |

The script supports the passing of multiple URLs, the output of the converted adblock filter lists will be `[basename].script.action` and `[basename].script.filter`.

Once the files have been created, they must be added to the privoxy configuration. For example:

    actionsfile easylist.script.action
    filterfile easylist.script.filter

Once the file is added, rerunning the script with the same parameters will automatically update the privoxy filters.

Environment Variables
---------------------

| Environment Variable    | Description                             | Default |
| :---------------------: | --------------------------------------- | :-----: |
| SEDCMD                  | The command used to invoke sed          | sed     |

