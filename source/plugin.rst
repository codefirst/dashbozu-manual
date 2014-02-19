Plugin
===============================

Input plugins
-------------------------------

Dashbozu supports below services to input activities.

* `GitHub <https://github.com/>`_
* `Bitbucket <https://bitbucket.org/>`_
* `Travis CI <https://travis-ci.org/>`_
* `Heroku <https://www.heroku.com/>`_
* `New Relic <http://newrelic.com/>`_
* `Errbit <https://github.com/errbit/errbit>`_
* `Wercker <http://wercker.com/>`_
* `Jenkins <http://jenkins-ci.org/>`_
* `Sunline <http://www.codefirst.org/sunline/>`_

GitHub
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Access to Webhooks & Services page of your repository.
Push **Add Hook** and input below information.

* Payload URL: http://dashbozu.example.com/hook/your-api-key/github
* Payload version: application/vnd.github.v3+form
* Which events would you like to trigger this webhook?: Let me select individual events.

  * Push: Checked
  * Pull Request: Checked
  * Issues: Checked
  * Issue comment: Checked

* Active: Checked

Bitbucket
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Access to your repository setting page.
Add below URL to "POST" and "Pull Request POST" services.

::

    http://your.dashbozu.host/hook/your-api-key/bitbucket

Travis CI
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
::

    gem install travis
    travis encrypt http://your.dashbozu.host/hook/your-api-key/travis_ci

You will get encrypted value. Edit **.travis.yml**.

::

    ...
    notifications:
      webhooks:
        secure: "your-encrypted-value"


Heroku
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Install deployhook addon:

::

    $ heroku addons:add deployhooks:http --url=http://dashbozu.example.com/hook/your-api-key/heroku

New Relic
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Access to your New Relic notification setting page.
Set below URL to "WebHook".

::

    http://your.dashbozu.host/hook/your-api-key/new_relic

Errbit
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Access to App Edit page.
Add WEBHOOK to NOTIFICATION SERVICE, and set below URL to URL.

::

    http://your.dashbozu.host/hook/your-api-key/errbit

Wercker
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Write **wercker.yml** as following:

::

    build:
       after-steps:
          - mzp/http-notify:
              url: $DASHBOZU_URL

And set URL as a application environment(we recomend as protected value):

::

    http://your.dashbozu.host/hook/your-api-key/wercker


Jenkins
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Install 'Notification Plugin' from Jenkins update center.

And set below settings.

* Format: JSON
* Protocol: HTTP
* URL: http://your.dashbozu.host/hook/your-api-key/jenkins

Sunline
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Add hooks to script as following:

::

    http://your.dashbozu.host/hook/your-api-key/sunline

Output plugins
-------------------------------

Dashbozu supports below services to output activities.

* `ChatWork <http://www.chatwork.com/>`_
* `AsakusaSatellite <http://www.codefirst.org/AsakusaSatellite/>`_

ChatWork
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Set below ENV variables.

* OUTPUT_CHAT_WORK_TOKEN
* OUTPUT_CHAT_WORK_ROOM_ID
* OUTPUT_CHAT_WORK_MESSAGE_TEMPLATE

AsakusaSatellite
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Set below ENV variables.

* OUTPUT_ASAKUSA_SATELLILTE_URL
* OUTPUT_ASAKUSA_SATELLILTE_API_KEY
* OUTPUT_ASAKUSA_SATELLILTE_ROOM_ID
* OUTPUT_ASAKUSA_SATELLILTE_MESSAGE_TEMPLATE

