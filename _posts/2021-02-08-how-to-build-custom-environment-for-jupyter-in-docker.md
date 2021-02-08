---
layout: post
title: "How to build a custom environment for Jupyter in Docker"
author: "Augusto Herrmann"
lang: en
ref: 2021-02-08-how-to-build-custom-environment-for-jupyter-in-docker
category: [en, blog]
tags: [
  jupyter,python,docker,containers,jupyter lab,jupyter notebook,
  requirements,packages
]
cover: /assets/images/2021/02/jovian-cloudscape-juno-2018.jpeg
snippet-image: /assets/images/2021/02/jovian-cloudscape-juno-2018.jpeg
desc: >-
  Running Jupyter Lab and Jupyter Notebook inside a Docker container is a
  good way to keep your environments isolated from your system. While
  there are Docker images ready for doing that, it may unfortunately not
  be super obvious to configure them and to prepare a custom environment
  with your own preferred Python packages. Here is how you can build a
  flexible, customizable environment for your own notebooks.
image-credits: "Juno probe / NASA"
---

If you have been doing software development in recent years, you've
probably come across the use of containers not only for deployment, but
also during development to ensure that your build is completely
reproducible in different systems.

Also very popular in data science, data visualization and related
circles is using Python and [Jupyter](https://jupyter.org/) Notebooks
and Jupyter Lab to explore and experiment with data. Some people
[criticize Jupyter for often result in unreproducible work](https://adamrule.com/files/papers/chi_2018.pdf),
something that is really important for the scientific method, because
the development environment may differ from the one reproducing it and
the cells could be executed out of order. For instance, in
[an experiment](https://blog.jetbrains.com/datalore/2020/12/17/we-downloaded-10-000-000-jupyter-notebooks-from-github-this-is-what-we-learned/)
made by the Jetbrains Datalore team last year which downloaded almost
10 million notebooks from Github, they found 36% of those notebooks to
be inconsistent, that is, run in a non linear order.

On the other hand, if your environment is well defined in a
[Docker](https://en.wikipedia.org/wiki/Docker_(software)) container
and you make sure to do the good practice of executing the cells in the
proper order, notebooks can be completely reproducible.

It might not be so obvious how to do it, however. So here is a step by
step guide on how to use Jupyter Lab and Jupyter Notebook inside Docker
with the Python packages of your choice.

This guide is written with a GNU-Linux based system in mind and has been
tested on Ubuntu 18.04 and 20.04. It should also work on other GNU-Linux
based systems. However, if you are using Windows or MacOS, you will have
to make some adaptations for it to work, mainly concerning the command
line operations and environment variables, but those are not covered in
this guide.

## Preparations

Before we begin, make sure you have
[installed Docker](https://docs.docker.com/engine/install/) and
[Docker Compose](https://docs.docker.com/compose/install/).

## Choosing a base image

The
[Jupyter Docker Stacks](https://jupyter-docker-stacks.readthedocs.io/en/latest/index.html)
do provide some ready to run images and some
[recipes](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/recipes.html#using-pip-install-or-conda-install-in-a-child-docker-image)
for creating your own Docker image inheriting from those (what they call
a child Docker image).

For that, we must first choose a base Docker image to inherit from. For
this exercise we are going to use `jupyter/scipy-notebook`, which
includes [Pandas](https://pandas.pydata.org/), [NumPy](https://numpy.org/)
and a few other things. However, take a look at the
[image selection](https://jupyter-docker-stacks.readthedocs.io/en/latest/using/selecting.html)
section of the Jupyter Docker Stacks documentation to see other options.

Then we create a `Dockerfile` to build the custom Docker image and
add the following line to define the base image:

```dockerfile
FROM jupyter/scipy-notebook
```

If you don't want to create a new `Dockerfile` from scratch, you can
also clone
[this example repository](https://github.com/augusto-herrmann/docker-jupyter-extensible)
from Github, which has a `Dockerfile` ready to use.

## Setting up the locales

{% assign linked_post=site.posts | where:"ref", "2021-02-05-how-to-deal-with-international-data-formats-in-python" | where:"lang", page.lang %}
If you are ever going to work with data from locales other than the US,
[you should probably set up one or more other locales]({{linked_post.first.url}}).
For example, this
will make it easy to work with different decimal number separators or
with weekday and month names in different languages.

For this exercise, we are going to configure the system locales to use
both en_US.UTF-8 (English, US) and pt_BR.UTF-8 (Brazilian Portuguese)
locales. The following section of the `Dockerfile` does just that.

```dockerfile
# install the locales you want to use
RUN set -ex \
   && sed -i 's/^# en_US.UTF-8 UTF-8$/en_US.UTF-8 UTF-8/g' /etc/locale.gen \
   && sed -i 's/^# pt_BR.UTF-8 UTF-8$/pt_BR.UTF-8 UTF-8/g' /etc/locale.gen \
   && locale-gen en_US.UTF-8 pt_BR.UTF-8 \
   && update-locale LANG=en_US.UTF-8 LC_ALL=en_US.UTF-8 \
```

## Choosing your Python packages

Next, we are going to choose the Python packages that are going to be
available to Jupyter inside the environment. In this example, we choose
the data visualization tool [Plotly](https://plotly.com/python/) and the
map plotting package
[Folium](https://python-visualization.github.io/folium/). This is the
section of the `Dockerfile` where we define that.

```dockerfile
# install Python packages you often use
RUN set -ex \
   && conda install --quiet --yes \
   # choose the Python packages you need
   'plotly==4.9.0' \
   'folium==0.11.0' \
   && conda clean --all -f -y \
   # install Jupyter Lab extensions you need
   && jupyter labextension install jupyterlab-plotly@4.9.0 --no-build \
   && jupyter lab build -y \
   && jupyter lab clean -y \
   && rm -rf "/home/${NB_USER}/.cache/yarn" \
   && rm -rf "/home/${NB_USER}/.node-gyp" \
   && fix-permissions "${CONDA_DIR}" \
   && fix-permissions "/home/${NB_USER}"
```

Replace or add it with the Python packages and Jupyter lab extensions
you want.

## Building the container

This step is very easy to do, but may take a very long time to finish.
Just run the following command:

```sh
$ docker build --rm -t docker-jupyter-extensible .
```

and then go have a meal or do something else and come back after a
while.

## Fixing file permissions

A common problem when mounting a folder from the host inside the
container is that the file owners often do not match, so you end up
either not able to access the folder or having it read-only. To fix
that, we need to set up the user and group used inside the container to
have the same id numbers as the user and group you are using on the
host. It may sound complicated, but with those images it is really
easy to do.

Just create a file named `.env` by running the following command:

```sh
$ printf "UID=$(id -u)\nGID=$(id -g)\n" > .env
```

This will allow you to use the `notebooks` folder both inside and
outside the container.

## Running the container

We are good to go! Every time you want to start Jupyter, just run the
container with the command:

```sh
$ docker-compose up
```

You should see the messages from the container in the terminal. If
everything goes right, you should see a link starting with
`http://127.0.0.1:8888` that also contains an access token. Open this
link on a browser to use Jupyter Notebook. If you want to use Jupyter
Lab instead, just change the beginning of the URL to
`http://127.0.0.1:8888/lab`, but keep everything after it, including
the access token.

<figure markdown="1">
![Terminal screen showing the output of starting the Jupyter container.]({{ 'assets/images/2021/02/docker-jupyter-in-terminal.gif' | relative_url }})
<figcaption>The output of the terminal when starting the container
shows the URL and token for opening Jupyter Lab and Jupyter Notebook
in the browser.</figcaption>
</figure>

To check that the packages have been properly installed and configured,
just open a new notebook and import them. See, for instance,
[Plotly Express](https://plotly.com/python/plotly-express/):

<figure markdown="1">
![A browser window with Jupyter lab running Plotly Express.]({{ 'assets/images/2021/02/jupyter-lab-with-plotly-express.gif' | relative_url }})
<figcaption>A chart example from Plotly Express running inside our
new Docker container.</figcaption>
</figure>

Now have fun with your new Jupyter Lab or Jupyter Notebook!

If later you want to add some new packages, just go back to
[the “choose your packages” step](#choosing-your-python-packages), make
your desired changes and follow from there, building the container
again.
