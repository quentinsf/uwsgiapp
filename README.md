uwsgiapp
========

A script for stopping and starting apps running under uWSGI's emperor mode.

## Background

When uWSGI is running with the --emperor <dirname> extension, it will start, stop and restart processes
automatically as their *.ini configuration files are created, deleted or updated in <dirname>.
This is great for automated management of multiple processes.

If you want to manage things by hand, though, it's a little less convenient to keep adding and removing files.

This utility assumes that you've created a directory structure analagous to the 'sites-enabled' and 'sites-available'
model often used by Apache and nginx installations.  

In our case, you'll have all your app-specific uWSGI INI files in a
directory called 'apps-available'.  When you want uWSGI to be running them, you create a symlink in a directory called 'apps-enabled'.
uWSGI should be started up with the --emperor option specifying the apps-enabled directory.  e.g.

    uwsgi --emperor /etc/uwsgi/apps-enabled

Now you can just create, remove or touch the symlinks without affecting your master app configuration files.

## Making it easier

The `uwsgiapp` script just makes this easier, giving you commands to manipulate the symlinks.

    uwsgiapp start myapp1

    uwsgiapp stop myapp1

    uwsgiapp restart myapp1

## Installation

Just download the script, make sure it's executable with

    chmod +x uwsgiapp
    
and put it somewhere on your path, or specify its location explicitly.

    uwsgiapp -h
    
will tell you the syntax.

## Disclaimers

This comes with no warranties, express or implied. You use it at your own risk.  I hope it's useful!

Quentin Stafford--Fraser

