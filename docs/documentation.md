To document all elements of the project mkdocs is being used. Your looking at it now.

* [Mkdocs](https://www.mkdocs.org/#getting-started) - Mkdocs documentation.

MkDocs supports Python versions 2.7, 3.4, 3.5, 3.6, 3.7 and pypy.

# Prerequisites
Although not strictly required it is a good idea to use:

### Python 2
- [virtualenv](https://virtualenv.pypa.io/en/latest/)
- [virtualenvwrapper](https://virtualenvwrapper.readthedocs.io/en/latest/)

If using Python ver 2 use of the above allows separating off a Python virtual environment to install libraries to.

### Python 3
Python 3 has built in virtual environments built in.

- [Python 3 virtualenv](https://docs.python.org/3/library/venv.html)

Inline `code` has `back-ticks around` it.

## MkDocs Installation

`pip install mkdocs`

`mkdocs <PROJECT NAME>`

`cd <PROJECT NAME>`

##Local Server
start local server:
`mkdocs serve`

To view the site navigate to: [http://localhost:8000/](http://localhost:8000/)

## Adding Pages
Edit the mkdocs.yml file and add in elements o the nav list.
Then create the corresponding file e.g. docs/about.md

Add the following to to mkdocs.yml:
```
site_name: <SITE NAME>
nav:
- Home: index.md
- About: about.md
theme: readthedocs
```
## Building the site
To create the site run:
`mkdocs build`

This creates subfolder called `site/`
It is a good idea to add `site/` to `.gitignore`

## Deployment

The contents of the site folder can be deployed to hosting solution, i.e. AWS S3 or Github pages

To clean things down use:
`mkdocs build --clean`

Also see section on [deploy in MkDocs documentation](https://www.mkdocs.org/user-guide/deploying-your-docs/).
