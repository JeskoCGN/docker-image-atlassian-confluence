Docker Re-Wrapper of Confluence Docker Image: cptactionhank/atlassian-confluence

Extensive documentation can be found here: https://github.com/cptactionhank/docker-atlassian-confluence

This image enables the configuration of a proxy! Proxy configuration is required by Atlassian product when used behind a proxy.

# Log File configuration

You can reconfigure the logfile location with the environment variable CONFLUENCE_LOGFILE_LOCATION!

Example:

~~~~
$ docker run -d --name confluence \
    -e "CONFLUENCE_LOGFILE_LOCATION=/var/atlassian/confluence/logs" \
    blacklabelops/confluence
~~~~

> Will write logs to /var/atlassian/confluence/logs. Note: Must be accessible by daemon:daemon user!


# Proxy configuration

You can specify your proxy host and proxy port with the environment variables CONFLUENCE_PROXY_NAME and CONFLUENCE_PROXY_PORT. The value will be set inside the Atlassian server.xml at startup!

When you use https then you also have to include the environment variable CONFLUENCE_PROXY_SCHEME.

Example HTTPS:

* Proxy Name: myhost.example.com
* Proxy Port: 443
* Poxy Protocol Scheme: https

Just type:

~~~~
$ docker run -d --name confluence \
    -e "CONFLUENCE_PROXY_NAME=myhost.example.com" \
    -e "CONFLUENCE_PROXY_PORT=443" \
    -e "CONFLUENCE_PROXY_SCHEME=https" \
    blacklabelops/confluence
~~~~

> Will set the values inside the server.xml in /opt/confluence/conf/server.xml
