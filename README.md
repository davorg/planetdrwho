# Planet Dr Who

This repo contains the code and data that powers the site [Planet Doctor Who](https://drwho.theplanetarum.org).
The site aggregates news and information about the how *Doctor Who* from various corners of the internet.

The site is built using [Perlanet](https://github.com/davorg/perlanet) which is a tool for aggregating web
feeds (it's a version of the Python tool "Planet" written in Perl - hence the rather silly name).

The way it works is this:

* `perlanetrc` contains YAML with the data that drives the file. Most importantly, it has the
`feeds` list which defines the feeds that are aggregated into the web site (and a new Atom feed).

* `index.tt` is a template which is expanded (using the [Template Toolkit](https://tt2.org/) into
the web site's front (and only) page. The template is passed a number of variables which can be
used to display the new, aggregated feed. For example the `feed` variable is an an object (actually
an instance of [XML::Feed](https://metacpan.org/pod/XML::Feed) which contains the new feed.

* `index.html` and `atom.xml` are the generated files which make up the web site and the new Atom
feed. They are generated on a schedule using [GitHub Actions](https://github.com/features/actions).

* `.github/workflows/buildsite.yml` is the file that controls how the site is built.

* `cpanfile` defines the Perl libraries that are required to generate the web site.

* Everything else is a file that is used to display the new web site - fonts, images, CSS files, etc

The generated web site is hosted on [GitHub Pages](https://pages.github.com/).
