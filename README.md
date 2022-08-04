# herrmann.tech website

This is the source code to my professional website and blog, which is live at
[herrmann.tech](https://herrmann.tech).

The website uses [Jekyll](https://jekyllrb.com/) version 3.8 to build static
web pages.

When devloping locally, to build, use:

```bash
export JEKYLL_VERSION=3.8
docker run --rm --volume="$PWD:/srv/jekyll" -it jekyll/minimal:$JEKYLL_VERSION jekyll build --baseurl {your local repository}/_site/ --watch
```
