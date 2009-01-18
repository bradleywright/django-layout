Django Layout
=============

Intended as a nice default starting point for Django, including deployment server configs. Essentially replaces `django-admin.py startproject [THING]`.

Project Naming
--------------

Obviously the `.git` objects are included when checking out from GitHub, so you should copy the appropriate directories to somewhere Git-free (if you want):

    $ cp -R . ../mynewdjangoproject
    $ rm -rf ../mynewdjangoproject/.git

By default it comes named as `yoursite`, but you should obviously name it yourself:

    $ mv yoursite mydomain

Python Path
------------

`manage.py` automatically patches your sys.path to include files under `lib`, so you can feel free to put Python modules here:

    $ svn co http://.../mymodule.py lib/.
    # inside a Python file in your Django project
    import mymodule
    # just works!

This allows you to bundle your own library modules or external dependencies (dmigrations, simplejson etc.) with your project as required. It also means that a checkout to a plain Python system should Just Work™.

Dependencies
------------

This project has a dependency on [Django Static Management](http://github.com/bradleywright/django-static-management), another project of mine. It provides an easy way of managing static files. It's included as a `git submodule`, so you'll need to run the following commands to get the latest version:

    $ cd yoursite/static_management
    $ git remote update
    $ git merge origin/master
    $ cd ../..
    $ git commit -a -m "Update to HEAD of static management"
