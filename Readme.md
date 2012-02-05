Heroku buildpack: Pelican
========================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack) for statically generated blogs and websites.
It uses [virtualenv](http://www.virtualenv.org/), [pip](http://www.pip-installer.org/) and [Pelican](http://readthedocs.org/docs/pelican/en/2.7.2/). 

Usage
-----

Example usage:

    $ ls
    content/  pelican.conf.py

    $ heroku create --stack cedar --buildpack git@github.com:pearkes/heroku-buildpack-pelican.git

    $ git push heroku master
    ...
    -----> Heroku receiving push
    -----> Fetching custom buildpack... done
    -----> Pelican app detected
    -----> Preparing virtualenv version 1.6.4
           New python executable in ./bin/python
           Installing setuptools............done.
           Installing pip...............done.
    -----> Installing pelican using pip version 1.0.2
    -----> Bundling Apache v2.2.19
    -----> Generating static content for deploy


The buildpack will detect if your project is suitable for pelican if it has a pelican.conf.py file and content file in it's root. If you're new to pelican, and wish to look at possible themes or examples, check out [Bait](http://github.com/pearkes/bait)