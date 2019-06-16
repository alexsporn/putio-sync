putio-sync
==========

Script for automatically downloading files from put.io

Installation and Usage
----------------------

Installation can be performed via pip::

    $ pip install putiosync

This will install a new application 'putiosync' that can be called from the command
line as follows::

    $ putiosync <download_directory>

Other options and customizations are available by using the '-h' or '--help' options.

Authentication
--------------

The first time you run the application, a webbrowser will be opened to
put.io asking for permissions.  If authorized, you'll get your access
token which you will enter into the application.

Docker Container
----------------

The script can also be run using the containing Dockerfile.

You need to map the volume `/volume/putio_download` to a path on your host system.
Additional parameters can be passed by setting the `PUTIO_SYNC_ARGS` environment variable with all the arguments.

It is recommended to also set the environment variable `PUTIO_SYNC_SETTINGS_DIR` to a path mapped to the host. Otherwise you will loose all the settings after a container update.
In there create a file called `putiosync.json`. The content is then the authentication token from here:
https://app.put.io/authenticate?client_id=1067&response_type=oob

Json file content:
```
{"token": "YOUR_AUTH_TOKEN"}
```

Alternatively you can:

 - run the docker container with an interactive bash to provide the auth token:
```
docker run -t -i putio-sync
```
 - set the environment variable `PUTIO_SYNC_TOKEN`. This is not recommended since it is a security risk (The token is listed in the process list)

You may need to set a manual port mapping. Putio Sync is listening on the TCP port 7001

Contributing Back
-----------------

* Found a bug? Create an issue on github.
* Fixed a bug or added a feature?  Fork the project on github and
  submit a pull request
