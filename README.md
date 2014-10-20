Drupalgeddon Checks
==================

I want a quick way of checking for known attack signatures on multiple
sites across a set of servers. Making a Drush command is a quick way
to enable this.

A signature-based malware detector in PHP is probably a bad thing :)
but this might be a useful tool for this situation, so here it is.

Oh, feel free to fork / add / extend checks in the checks directory -
one check per file, match the filename and function name. You'll see.

(This probably grew out of some idle thinking about adding our own
custom checks to Archimedes / Aegir setup.)

Disclaimer
----------

Signature-based detection is questionably valuable, but if it helps
you identify a site that needs cleanup then that's better than not
knowing. Yay!

It's certainly not a watertight solution since it depends on the right
signatures being in this module ... so, if you are able to contribute
additional checks, please do so. Contributions are welcome via
[Drupal.org issue queue](https://www.drupal.org/project/drupalgeddon)
or [Github](https://github.com/xurizaemon/drupalgeddon).

Installation
------------

    drush dl drupalgeddon

Usage
-----

To test a single site,

    drush drupalgeddon-test

But of course Drush is much more powerful with aliases ...

    drush @example.org drupalgeddon-test

Then you can test all the sites on your server at once.

    $ drush -y @sites drupalgeddon-test
    You are about to execute 'drupalgeddon-test' non-interactively (--yes forced) on all of the following targets:
    sites.abcd-d6.example.org       >> Site is not Drupal 7.                     [ok]
    sites.abcde.example.org         >> Site did not test positive. Good luck!    [ok]
    sites.abcdef.example.org        >> Site did not test positive. Good luck!    [ok]
    sites.abcdefg.example.org       >> Site did not test positive. Good luck!    [ok]
