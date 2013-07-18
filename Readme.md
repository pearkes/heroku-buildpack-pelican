**Heads up!**

There is an official Pelican buildpack for Heroku available over at [getpelican/heroku-buildpack-pelican](https://github.com/getpelican/heroku-buildpack-pelican).

As I'm no longer actively working on or using this one, I'd recommend using the official buildpack.

Heroku buildpack: Pelican
========================

This is a [Heroku buildpack](http://devcenter.heroku.com/articles/buildpack) for statically generated blogs and websites.
It uses [virtualenv](http://www.virtualenv.org/), [pip](http://www.pip-installer.org/) and [Pelican](http://readthedocs.org/docs/pelican/). 

Usage
-----

Example usage:

    $ ls
    content/  pelican.conf.py

    $ heroku create --stack cedar --buildpack https://github.com/pearkes/heroku-buildpack-pelican.git

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
    -----> Generating static content for deploy with default theme

Requirements
-----
Content:

A content directory, with Markdown or reST files for posts. For example usage of content structure, check-out the [Pelican sample](https://github.com/ametaireau/pelican/tree/master/samples).

Configuration:

A `pelican.conf.py` file must exist in the root directory of your project.

Themes:

For use of a custom theme, instead of Pelican's default, a `theme/` directory must exist in the root. The `theme/` directory should have the following structure:
    
    ├── static
    │   ├── css
    │   └── images
    └── templates
        ├── archives.html    // to display archives
        ├── article.html     // processed for each article
        ├── categories.html  // must list all the categories
        ├── category.html    // processed for each category
        ├── index.html       // the index. List all the articles
        ├── page.html        // processed for each page
        ├── tag.html         // processed for each tag
        └── tags.html        // must list all the tags. Can be a tag cloud.
        
For more on themes, visit the [Pelican documentation](http://pelican.readthedocs.org/en/2.7.2/themes.html).

Local Developement
-----
Installation:
    
    $ pip install pelican markdown pygments docutils
    
Generate:

    $ ls 
    content/ pelican.conf.py
    
    $ pelican . -s pelican.conf.py

Or, with a theme:

    $ ls 
    content/ theme/ pelican.conf.py
    
    $ pelican . -s pelican.conf.py -t theme/

Open your generated files:
    
    $ open output/index.html
