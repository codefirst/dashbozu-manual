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
* `dploy.io <http://dploy.io/>`_
* `Jenkins <https://jenkins-ci.org/>`_
* `Redmine <http://redmine.org/>`_
* `Sunline <https://www.codefirst.org/sunline/>`_
* `Hatena Bookmark <http://b.hatena.ne.jp/>`_

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

dploy.io
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Set 'Post-Deployment URL' in 'Servers Configuration':

::

    http://your.dashbozu.host/hook/your-api-key/dploy

Jenkins
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Install 'Notification Plugin' from Jenkins update center.

And set below settings.

* Format: JSON
* Protocol: HTTP
* URL: http://your.dashbozu.host/hook/your-api-key/jenkins

Redmine
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Install `Redmine Webhook Plugin <https://github.com/suer/redmine_webhook>`_ .

Add post URL in project settings page as following:

::

    http://your.dashbozu.host/hook/your-api-key/redmine


Sunline
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Add hooks to script as following:

::

    http://your.dashbozu.host/hook/your-api-key/sunline

Hatena Bookmark
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Set Web Hook configuration in your preference:

::

    http://your.dashbozu.host/hook/your-api-key/hatena_bookmark



Output plugins
-------------------------------

Dashbozu supports below services to output activities.

* `ChatWork <http://www.chatwork.com/>`_
* `AsakusaSatellite <https://www.codefirst.org/AsakusaSatellite/>`_
* WebHook

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

WebHook
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Set below ENV variables.

* OUTPUT_HTTP_URL

It posts data as JSON format.
For example:

::

    {
      "id":34,
      "title":"[Deploy] test - aaaa",
      "body":"new_commit",
      "source":"heroku",
      "project_id":1,
      "url":"http://www.example.com/",
      "icon_url":"https://secure.gravatar.com/avatar/462233d5aedf66a793dcd95f814f8811?secure=true\u0026size=32",
      "status":"error",
      "author":"mallowlabs@gmail.com",
      "created_at":"2014-01-19T14:46:47.476Z",
      "updated_at":"2014-01-19T14:46:47.489Z",
      "encrypted_identifier":"afd6033f1b0ebe47c0152016566e29c26cfeb2d1"
    }

