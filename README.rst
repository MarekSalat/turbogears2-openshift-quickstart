TurboGears2 with python 3.3 on Red Hat's OpenShift Express
==========================================

This quickstart helps you get up and running with a fully-functional
TurboGears2 instance on OpenShift with python 3.3. It automatically handles creating a Python
virtualenv, populating a MySQL database, and deploying your application to the
cloud.

* Create an account at http://openshift.redhat.com/

Features
--------

* Completely free, thanks to Red Hat's OpenShift Express
* MySQL database automatically setup for your application
* Dynamic database configuration at runtime. No passwords stored in your configs.
* Your application's test suite is run after each push
* Automatic deployment upon git push
* No need to think about servers, let alone apache/mod_wsgi configuration


The manual method
-----------------

If you don't want to use the `openshift-quickstarter`, you can easily create a new OpenShift WSGI application and merge this quickstart into it manually:

::

    rhc create-app -a yourAppName
    rhc add-cartridge -a yourAppName -e add-mysql-5.5
    cd yourAppName
    git remote add upstream -m master https://github.com/MarekSalat/turbogears2-openshift-quickstart
    git pull -s recursive -X theirs upstream master
    git push

Monitoring your logs
--------------------

::

    rhc tail -a yourAppName

Trubleshot
----------

- If you want to change your name of app in wsgi/tg2app (currently myproject). You need to change path in .openshift/action_hooks/build line 13.

- If you are working on windows, you need to change run permision for build and deploy script (see http://openshift.github.io/documentation/oo_user_guide.html#the-openshift-directory).

::
	git update-index --chmod=+x .openshift/action_hooks/*
	git push

You may have problem with this command. Solution is simple. Go to the folder and make chmod on each file separetly.