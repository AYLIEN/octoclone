Octoclone
=========


                 _              | |
      ___   ____| |_  ___   ____| | ___  ____   ____
     / _ \ / ___)  _)/ _ \ / ___) |/ _ \|  _ \ / _  )
    | |_| ( (___| |_| |_| ( (___| | |_| | | | ( (/ /
     \___/ \____)\___)___/ \____)_|\___/|_| |_|\____)


A GitHub backup solution that just works!
(based on GitHub API v3)

Installation
------------

octoclone is available through rubygems and known to work with ruby 1.9.
to install, just type

    $ gem install octoclone


Usage
-----
Make sure that the key file of the entered username is added to GitHub (entering username and password is not enough)

You may add `~/.ssh/id_rsa.pub` to your GitHub account by running

    $ octoclone -k

Or if you want to add a custom key, run

    $ octoclone -ki "~/.ssh/id_dsa.pub"

You may remove keys interactively with

    $ octoclone -x

Now you may run

    $ octoclone -cd "/path/to/backup/dir"

Tarballs
--------

Tarballs are made from whatever that is cloned. So if you specify `--public`, only public repositories of the target users are included in the tarball.

Tarballs are created using the `-a` option

Uploading to Amazon S3
----------------------

In order to upload to S3, first you must specify `key_id`, `secret` and `bucket` in the `s3_cred.yml` file. A sample file is included, you may rename and fill it with your own credientials.
Also, to upload cloned files to S3, you must create a tarball, which itself
needs the `-c` option to clone files. The uploaded tarball will be named like `2012-11-15_11-19-02_octoclone_backup.tgz`.

So to backup all your repos, tarball them and upload them to S3, simply run:

    $ octoclone -ca --s3

by default, tarball and cloned files are stored in `/tmp`.

Further help
------------

    $ octoclone --help
