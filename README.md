CenturyLink Data Container
=====================
[![](https://badge.imagelayers.io/centurylink/data-container.svg)](https://imagelayers.io/?images=centurylink/data-container:latest 'Get your own badge on imagelayers.io')

This image is used for creating data containers within the [Panamax](http://panamax.io) application. Panamax leverages these containers for docker `--volumes-from` operations.

Example usage - create the data container:

`$ docker run --rm --name datacontainer1 -v /dbdata centurylink/data-container:1.0`

From this, another container can connect to the data container via the `--volumes-from` option.

`$ docker run --rm --name mysql1 --volumes-from datacontainer1 centurylink/mysql:5.5`

Running a docker inspect on `mysql1` shows the data container mounted from `datacontainer1`:

```
$ docker inspect mysql1

...

 },
    "Volumes": {
        "/dbdata": "/var/lib/docker/vfs/dir/da2641445e5b6d1fd45ece8c77756a51e0163269a5a8476bb989a296535330eb",
        "/var/lib/mysql": "/var/lib/docker/vfs/dir/1828c0e3bf0b3450bdb4cda55cc4e953aae79315ae026caaf13d5605a31f7f1c"
    },
``` 
