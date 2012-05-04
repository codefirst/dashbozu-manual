Install hooks
===============================

Jenkins
-------------------------------

Add following command to your job:

::

    curl "http://dashbozu.example.com/hook/jenkins?url=[jenkins url]&project=[project name]"

Git
-------------------------------

Copy to script to your git repository.

::

    cp $DASHBOZU_HOME/script/gitbozuhook.rb /path/to/gitdir/hooks

And add ``post-receive``:

::

    #! /bin/sh
    read oldrev newrev refname
    ruby /path/to/gitdir/hooks/gitbozuhook.rb $oldrev $newrev $refname [dashbozu url]/hook/git

Redmine
-------------------------------

Install psot script plugin:

::

    $ cd $RAILS_ROOT/vender/plugins
    $ git clone git://github.com/suer/redmine_post_script.git

Update ``$RAILS_ROOT/vender/plugins/redmine_post_script/bin/post_script.rb``:

::

    require 'open-uri'
    open("http://dashbozu.example.com/hook/redmine?url=https://example.com/redmine/activity.atom?key=[API key]") {|_|}

Heroku
-------------------------------

Install deployhook addon:

::

    $ heroku addons:add deployhooks:http --url=http://dashbozu.example.com/hook/heroku

