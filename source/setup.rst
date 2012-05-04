Setup
============

Setup Play 2.0 or later
------------------------

* Documentation: Installing  Playframework (http://www.playframework.org/documentation/2.0/Installing)

Setup PostgreSQL
------------------------

Install PostgreSQL by your package system(e.g. homebrew). And type following command:

::

    $ cd /path/to/db
    $ initdb .
    $ postgres -D .

And type at other terminal:

::

    $ createdb dashbozu


Run Dashbozu
-----------------------

Type below commands.

::

    $ play stage
    $ target/start -Dconfig.resource=prod.conf

And access [http://localhost:9000](http://localhost:9000)

(Optional) Realtime update
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Signup(or login) http://pusher.com/ and add new App. And update ``prod.conf``:

::

    pusher.enable=true
    pusher.id=<pusher_id>
    pusher.key=<key>
    pusher.secret=<secret>

(Optional) Push notification to iPhone
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Signup(or login) http://boxcar.com and add new service. And update ``prod.conf``:

::

    boxcar.enable=true
    boxcar.key=<key>
    boxcar.secret=<secret>

And install boxcar App to your iPhone/iPad.

