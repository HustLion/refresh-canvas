# Goal

Learn mako usage and page layout from this repo.

# Analysis

`tutorial` folder.

Use `make.py` to make the final pages.

Prerequisites:

	#https://pypi.python.org/pypi/pip

	sudo apt-get install python-pip
	sudo apt-get install python-yaml

	sudo pip install Mako

## Structure

`make.py` arranges all pages to form the final.

JQuery UI files are located in the `js` folder which will be copied to `build/js` by the `make.py` script. CodeMirror is also employed this way.

`yaml` is used to seperately write every component of a page then converted to python code by `yaml` package. The python code will be used for `Mako`.

`Mako` is used like this:

	file(page["outfilename"], 'w').write(Template(filename="templates/template.mak",lookup=TemplateLookup(directories=['.'])).render(**page))

The `Template()` function actually does the job.

In `templates` folder, `template.mak` is the actual template of all those pages. And we can see the reference to jQuery UI scripts too.

## Summary
`template.mak` uses `Mako` syntax, which design the page.

Files in `chapters` folder use `yaml` syntax, which provides the contents.

`make.py` gathers all files related and calls `Mako` to interpret `Mako` syntax to html.

Workflow: `template.mak`->`yaml`->`make.py`

Optionally we can use `rsync` to deploy instantly to our servers.

