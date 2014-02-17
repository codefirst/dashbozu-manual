Setup
============

Install
----------------

Install dependencies:

::

    $ bundle install --path .bundle --without development test

Precompile assets:

::

    $ bundle exec rake assets:precompile RAILS_ENV=production

Run server:

::

    $ bundle exec rails s -e production

Parameters
---------------

Edit config/dashbozu.yml

or set environment variables:

* GITHUB\_KEY
* GITHUB\_SECRET
* BITBUCKET\_KEY
* BITBUCKET\_SECRET

If you do not have GitHub and Bitbucket keys, go to

* https://github.com/settings/applications
* https://bitbucket.org/account/user/YOUR-ACCOUNT/api


