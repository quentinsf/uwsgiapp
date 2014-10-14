uwsgiapp
========

A script for stopping and starting apps running under uWSGI's emperor mode.

## Background

When [uWSGI][1] is running with the `--emperor dirname` option, it will start, stop and restart processes
automatically as their \*.ini configuration files are created, deleted or updated in the directory *dirname*.

This is great for automated management of multiple processes. If you want to manage things by hand, though, it's a bit inconvenient to keep adding and removing files.

This utility assumes that you've created a directory structure analagous to the 'sites-enabled' and 'sites-available'
model often used by Apache and nginx installations, where you manipulate symbolic links instead of the original files.  

In our case, you'll have all your app-specific uWSGI INI files in a directory called *apps-available*.  When you want uWSGI to be running them, you create symlinks to them in a directory called *apps-enabled*.

Start uWSGI in emperor mode, specifying the *apps-enabled* directory.  e.g.

    uwsgi --emperor /etc/uwsgi/apps-enabled

Now you can just create, remove or touch the symlinks in *apps-enabled* without affecting your master app configuration files.

## Making it easier

Now, the `uwsgiapp` script just makes this a bit easier, giving you handy commands to manipulate the symlinks:

    uwsgiapp start myapp

    uwsgiapp stop myapp

    uwsgiapp restart myapp

## Installation

Just download the script, make sure it's executable with

    chmod +x uwsgiapp
    
and put it somewhere on your path, or specify its location explicitly, e.g.:

    uswgsiapp -h

or

    /usr/local/bin/uwsgiapp -h
    

## Disclaimers

This comes with no warranties, express or implied. You use it at your own risk.  I hope it's useful!

[Quentin Stafford--Fraser][2]  
[Telemarq Ltd][3]

[1]: http://uwsgi-docs.readthedocs.org
[2]: http://www.qandr.org
[3]: http://telemarq.com


