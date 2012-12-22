Must-know tools for (web) Python developer
==========================================

------

- **Domen KoÅ¾ar**
  - **from Slovenia**
    - **currently Erasmus student at UPC, Telecommunications**
      - **Python/Plone/Django/Pyramid developer**

---------

Static analysis
===============

- PEP8 (maybe autopep)
  - pyflakes (syntax error check, redundant imports, unused variables,
etc.)
- pylint (does a lot more than static analysis, be careful not to lose
whole day listening to a tool)
- pre_commit_chech.sh (commit hook to run all static analysis tools,
useful also as save hook)

----

Livereload
==========

- https://github.com/guard/guard-livereload
  - when a file changes on filesystem, resource is updated in the
browser
- spares time for developer to reload webpage
  - integration for various frameworks:
https://github.com/livereload/livereload-examples

----

Travis-CI
=========

- http://travis-ci.org
  - GitHub gets more love
    - open source distributed build platform for continuous integration
of github repositories
- supports 11 languages (including Python)
  - each build runs inside Ubuntu virtual machines and has sudo access

example `.travis.yml`::

    language: python
    python:
      - 2.6
              - 2.7
                    install:
      - python bootstrap.py
              - bin/buildout
                    script:
      - bin/nosetests -v -s
            notifications:
      irc:
        - "irc.freenode.org#niteoweb"

----

niteoweb.skel.{pyramid, plone}
==============================

- https://github.com/niteoweb/niteoweb.skel.pyramid
  - https://github.com/niteoweb/niteoweb.skel.plone
    - initial project folder structure for our new projects
      - keeps track of new things we learn about development workflow
        - reduces time with starting new projects, good for agile
development

----

Fabric
======

- http://docs.fabfile.org/
  - high-level interface to ssh and deployment tools
    - script your servers instead of unsuccessfully documenting them

Example `fabfile.py`::

    from fabric.api import run

    def host_type():
        run('uname -s')

Execute `host_type` on server `localhost` and `linuxbox`::

    $ fab -H localhost,linuxbox host_type
    [localhost] run: uname -s
    [localhost] out: Darwin
    [linuxbox] run: uname -s
    [linuxbox] out: Linux

    Done.
    Disconnecting from localhost... done.
    Disconnecting from linuxbox... done.

----

WebHelpers
==========

- http://sluggo.scrapping.cc/python/WebHelpers
  - useful functions for web development

Example::

    >>> distance_of_time_in_words(86399)
    '23 hours, 59 minutes and 59 seconds'

    >>> format_byte_size(2048)
    '2.0 kB'

    >>> truncate('Once upon a time in a world far far away', 14)
    'Once upon a...'

    >>> import webhelpers.feedgenerator as feedgenerator
    >>> feed = feedgenerator.Rss201rev2Feed(
    ...     title=u"Poynter E-Media Tidbits",
    ...     link=u"http://www.poynter.org/column.asp?id=31",
    ...     description=u"A group weblog by the sharpest minds in online
media/journalism/publishing.",
    ...     language=u"en",
    ... )
    >>> feed.add_item(title="Hello",
link=u"http://www.holovaty.com/test/", description="Testing.")
    >>> fp = open('test.rss', 'w')
    >>> feed.write(fp, 'utf-8')
    >>> fp.close()

----

Requests
========

- http://docs.python-requests.org
  - HTTP Library for humans
    - replaces urllib2 and other HTTP clients

Example::

    >>> r = requests.get('https://api.github.com', auth=('user',
'pass'))
    >>> r.status_code
    204
    >>> r.headers['content-type']
    'application/json'
    >>> r.text
    ...

----

Sphinx
======

- http://sphinx.pocoo.org/
  - Makes writing Python documentation fun again
    - Initially written for Python 2.7+ documentation

----

Beets
=====

- http://beets.readthedocs.org
  - the music geekâ€™s media organizer
    - fetch music metadata from multiple services and organize your
music library
- interactive command line interface

----

The Hitchhikerâ€™s Guide to Python
================================

- http://docs.python-guide.org/

---- 

Thanks!
=======

- Twitter: iElectric (follow me to get link to this presentation)
  - Blog: www.domenkozar.com
    - Slides: RestructuredText to HTML5 with
https://github.com/adamzap/landslide 
