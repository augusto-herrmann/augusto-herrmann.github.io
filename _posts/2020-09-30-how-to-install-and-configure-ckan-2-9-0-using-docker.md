---
layout: post
title: How to install and configure CKAN 2.9.0 using Docker
author: "Augusto Herrmann"
lang: en
ref: 2020-09-30-how-to-install-and-configure-ckan-2-9-0-using-docker
category: [en, blog]
tags: [ckan, docker, how to]
cover: /assets/images/2020/09/max-gotts-AFg4iczGE9g-unsplash.jpg
snippet-image: /assets/images/2020/09/ckan-master-class-moscow-urban-forum-2014.jpg
desc: >-
  After a few years, I try using CKAN again with Docker. Let's find out
  just how much straightforward (or not) it is to set up an open data
  catalog with version 2.9.0 of CKAN.
image-credits: "Max Gotts / Unsplash"
---

In 2014, I was invited to do a couple of mini courses on CKAN, one of them at
the pleasant island of Florianóplis and the other in the freezing winter of
Moscow. I had some experience with it already
[when creating collaboratively the dados.gov.br open data portal](https://blog.okfn.org/2012/05/10/new-brazilian-portal-dados-gov-br-made-by-citizens/)
in 2012, but I had to study it again in 2014 in order to catch up with then
recent developments.

<figure markdown="1">
![Augusto with a microphone at the stage of the IV Moscow Urban Forum, presenting CKAN]({{ 'assets/images/2020/09/ckan-master-class-moscow-urban-forum-2014.jpg' | relative_url }})
<figcaption>Augusto presents his CKAN course at the IV Moscow Urban Forum in
2014 (photo credits:
<a target="_blank" href="https://www.flickr.com/photos/mosurbanforum/albums/72157649677233946">Moscow Urban Forum</a>).</figcaption>
</figure>

The slides from those mini courses, one in English and the other in
Portuguese, are available on SlideShare:

* [CKAN Overview](https://pt.slideshare.net/AugustoHerrmannBatis/ckan-overview)
  (presented at the
  [IV Moscow Urban Forum](https://mosurbanforum.com/archive/2014/), in Moscow)
* [Minicurso de CKAN](https://pt.slideshare.net/AugustoHerrmannBatis/minicurso-de-ckan)
  (presented at the
  [Linked Open Data Brazil](https://web.archive.org/web/20180408101700/http://lodbrasil.com.br/)
  conference in Florianóplis, in Portuguese)

They are based on version 2.2 of CKAN and cover topics ranging from the
technical stuff, like installing, configuring and maintaining CKAN to the
daily operation by editors and people who will write the dataset descriptions,
fill in the metadata about resources (e.g. the format of a file), etc.

Now, the local IT department is interested in using CKAN and has asked me
about it, so I took the opportunity to once more get some hands-on experience
with installing and configuring the current version. Which is, at the time
of this writing, 2.9.0.

## What has changed?

Back then, there was already a way to install CKAN by using a Docker image,
but it was a bit experimental. I don't think there was even Docker Compose
recipe for doing it, as Docker Compose was very new at the time. The most
recommended way to install it was still to do it from source. Nowadays, Docker
containers are the rule of the day to keep your IT infrastructure neatly
organized, and you'd have to come up with a pretty good excuse for not using
them.

The
[CKAN documentation still offers three ways to install](https://docs.ckan.org/en/2.9/maintaining/installing/index.html),
so that hasn't changed. Thankfully, using Docker is still a possible and
supported path forward. The options are:

* operating system packages, available for Ubuntu 18.04 and 20.04;
* from source, if you have another operating system or want to develop
  CKAN; or
* using Docker Compose, for a more manageable container based infrastructure.

As may be obvious from the title, we're going to choose the Docker Compose
based install.

We'll just follow the
[instructions from the CKAN documentation](https://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html)
and use the default configuration choices wherever possible.

## Preparations and dependencies

First, make sure you have a lot of free disk space, as all those images may
take a whole lot of it. As they are based on Ubuntu 16.04, which is quite old
by now, chances are that you are using a more recent operating system than
that. So Docker will have to download a lot of stuff to make up for the
difference. In my case, I'm using Ubuntu 18.04, so the full install took just
about 5 GB of space.

The Docker volumes, by default, are stored on `/var/lib/docker`. At any
moment after installation, you may check out what Docker volumes you have
with the command

```bash
$ docker volume ls
```

You can also use

```bash
$ docker volume inspect [volume]
```

to see where the files inside `[volume]` are actually stored (under the
variable `Mountpoint`). For more information, see the
[Docker documentation on volumes](https://docs.docker.com/engine/tutorials/dockervolumes/).

You also need to install, if you haven't already, Docker and Docker Compose.
I'm taking as a base Ubuntu 18.04, but it should be similar for other
Ubuntu based GNU/Linux systems. Just do

```bash
$ sudo apt install docker.io docker-compose
```

or follow the instructions from the documentation of
[Docker](https://docs.docker.com/engine/installation/linux/docker-ce/ubuntu/)
and
[Docker Compose](https://docs.docker.com/compose/install/).

## Building the Docker images

First we need to download the CKAN repository from Github. Go to a
directory of your choice and clone the repository. Depending on your
download speed, this might take a while.

```bash
$ cd /path/to/my/projects
$ git clone https://github.com/ckan/ckan.git
```

The repository has all current and previous versions in version control,
so we choose the (supposedly) stable version 2.9.0 by checking out its
corresponding tag:

```bash
$ cd ckan
ckan$ git checkout tags/ckan-2.9.0
```

Next, copy `contrib/docker/.env.template` to `contrib/docker/.env`. That
contains some environment variables you might want to change, such as the site
URL, port and passwords. If you're just checking out how CKAN works, i.e., in
a non-production environment, it's ok to leave it as it is (with the
defaults).

Now we build the Docker images. This step takes a long time, a lot of disk
space and downloads many images and packages, so you might want to go do
something else while it runs.

**Spoiler:** we will come across a problem in the next step after building
the image. To save some time, you might not want to execute the next step
and move on right through to [the fix](#the-fix).

```bash
ckan$ cd contrib/docker
ckan/contrib/docker$ docker-compose up -d --build
```

Next, we restart the container cluster with:

```bash
ckan/contrib/docker$ docker-compose restart ckan
WARNING: The CKAN_MAX_UPLOAD_SIZE_MB variable is not set. Defaulting to a blank string.
Restarting ckan ... done
```

Check to see if the container is running:

```bash
ckan/contrib/docker$ docker ps | grep ckan
67693ebf5e92        docker_ckan                 "/ckan-entrypoint.sh…"   49 seconds ago       Up 6 seconds              0.0.0.0:5000->5000/tcp   ckan
```

And the system logs

```bash
ckan/contrib/docker$ docker-compose logs -f ckan
WARNING: The CKAN_MAX_UPLOAD_SIZE_MB variable is not set. Defaulting to a blank string.
Attaching to ckan
ckan          | db:5432 - accepting connections
ckan          | Command 'db' not known (you may need to run setup.py egg_info)
ckan          | Known commands:
ckan          |   create       Create the file layout for a Python distribution
ckan          |   exe          Run #! executable files
ckan          |   help         Display help
ckan          |   make-config  Install a package and create a fresh config file/directory
ckan          |   points       Show information about entry points
ckan          |   post         Run a request for the described application
ckan          |   request      Run a request for the described application
ckan          |   serve        Serve the described application
ckan          |   setup-app    Setup an application, given a config file
ckan          | db:5432 - accepting connections
ckan          | Command 'db' not known (you may need to run setup.py egg_info)
ckan          | Known commands:
ckan          |   create       Create the file layout for a Python distribution
ckan          |   exe          Run #! executable files
ckan          |   help         Display help
ckan          |   make-config  Install a package and create a fresh config file/directory
ckan          |   points       Show information about entry points
ckan          |   post         Run a request for the described application
ckan          |   request      Run a request for the described application
ckan          |   serve        Serve the described application
ckan          |   setup-app    Setup an application, given a config file
ckan exited with code 2
```

Oops. We have a problem. Apparently the command `db` is not being found
somewhere.

<figure markdown="1">
![Slide from the CKAN presentation, featuring a photo by Petras Gagilas of a frustrated baby]({{ 'assets/images/2020/09/frustration-slide.jpg' | relative_url }})
<figcaption>Oh, no! What should we do?</figcaption>
</figure>

### The fix

Searching around, I found on the CKAN issue tracker in Github that this error
happens due to [a bug](https://github.com/ckan/ckan/issues/5572) on this
version of CKAN. Apparently it has been already fixed by [this pull
request](https://github.com/ckan/ckan/pull/5381) by Mark Stuart that has
already been accepted and merged into the master branch (soon to be [renamed
to main](https://github.com/github/renaming), like everything on Github).
However, that fix is not yet incorporated into a stable release.

So we are left with a few alternatives to proceed:

1. Use an older version of CKAN, like 2.8.5, and hope it doesn't have the
   bug;
2. use another method of installation instead of Docker;
3. use the master branch, which might contain experimental features and is
   not yet stable code; or
4. use version 2.9.0, but apply a patch just for this fix.

We decided to use the latter,
[as suggested by mabah-mst on that issue](https://github.com/ckan/ckan/issues/5572#issuecomment-693263908),
by running the following commands:

```bash
ckan/contrib/docker$ cd ../..
ckan$ git checkout tags/ckan-2.9.0
#Apply fix to get CKAN to start at all in the docker-compose: https://github.com/ckan/ckan/pull/5381
ckan$ git diff 9abeaa1b7d2f6539ade946cc3f407878f49950eb^ 9abeaa1b7d2f6539ade946cc3f407878f49950eb | git apply
```

That way, we get the stable 2.9.0 release and *just* this fix, and not any
other possible experimental features that may have been incorporated into the
master branch.

Now let's build the thing again. And await once more...

```bash
ckan$ cd contrib/docker
ckan/contrib/docker$ docker-compose up -d --build
```

Now check again to see if the container is running properly:

```bash
ckan/contrib/docker$ docker ps | grep ckan
582466833e55        docker_ckan                 "/ckan-entrypoint.sh…"   4 hours ago         Up 4 hours             0.0.0.0:5000->5000/tcp   ckan
```

and open a browser at the default port of 5000 (`localhost:5000`) to check it
out.

*Voilà*! CKAN is running!

<figure markdown="1">
![ckan Datasets Organizations Groups About search box Welcome to CKAN]({{ 'assets/images/2020/09/default-ckan.gif' | relative_url }})
<figcaption>The home screen of a default CKAN installation.</figcaption>
</figure>

## Basic setup

If the site language you're going to use isn't English, now is a good time
to change the default language. For that, you need to find and edit the
`production.ini` file. To find out where it is, type

```bash
ckan/contrib/docker$ docker volume inspect docker_ckan_config 
[
    {
        "CreatedAt": "2020-09-29T10:16:51-03:00",
        "Driver": "local",
        "Labels": {
            "com.docker.compose.project": "docker",
            "com.docker.compose.volume": "ckan_config"
        },
        "Mountpoint": "/var/lib/docker/volumes/docker_ckan_config/_data",
        "Name": "docker_ckan_config",
        "Options": null,
        "Scope": "local"
    }
]
```
and you can see it is under `Mountpoint`, at
`/var/lib/docker/volumes/docker_ckan_config/_data`. The directory permissions
belong to the root user, so you'll have to edit it using `sudo` (e.g.
`sudo vim /var/lib/docker/volumes/docker_ckan_config/_data/production.ini`
or
`sudo gedit /var/lib/docker/volumes/docker_ckan_config/_data/production.ini`).

Look for the section named "Internationalisation Settings". Change the
`ckan.locale_default` and `ckan.locale_order` variables accordingly.

```ini
## Internationalisation Settings
ckan.locale_default = pt_BR
ckan.locale_order = en pt_BR ja it cs_CZ ca es fr el sv sr sr@latin no sk fi ru de pl nl bg ko_KR hu sa sl lv
ckan.locales_offered =
ckan.locales_filtered_out = en_GB
```

**Fun fact:** the first ever translation of CKAN to Brazilian Portuguese was
made in 2009 by yours truly. I also kept it updated, some years on, as new
versions of CKAN came out.

Restart CKAN and you should see the new default language come into effect.

```bash
ckan/contrib/docker$ docker-compose restart ckan
```

### Enabling the first user

Now we need to create the administrator user to begin working with CKAN.

We take a look at the
[documentation](https://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html#create-ckan-admin-user)
to find out the command to create an admin, for example, with the username
johndoe.

```bash
ckan/contrib/docker$ docker exec -it ckan /usr/local/bin/ckan-paster --plugin=ckan sysadmin -c /etc/ckan/production.ini add johndoe
Command 'sysadmin' not known (you may need to run setup.py egg_info)
Known commands:
  create       Create the file layout for a Python distribution
  exe          Run #! executable files
  help         Display help
  make-config  Install a package and create a fresh config file/directory
  points       Show information about entry points
  post         Run a request for the described application
  request      Run a request for the described application
  serve        Serve the described application
  setup-app    Setup an application, given a config file
```

But alas, that doesn't work! The command `sysadmin` is not known. As it turns
out, it's [another bug](https://github.com/ckan/ckan/issues/5621). This time,
I had to open a new issue myself. A couple of days later,
[Konstantin Sivakov](https://github.com/ckan/ckan/issues/5621#issuecomment-699672432)
pointed out that that particular command has
[changed in CKAN 2.9](https://docs.ckan.org/en/2.9/changelog.html#migration-notes):

> The old paster CLI has been removed in favour of the new ckan command. In
> most cases the commands and subcommands syntax is the same, but the `-c` or
> `--config` parameter to point to the ini file needs to provided immediately
> after the ckan command, eg:
> 
> `ckan -c /etc/ckan/default/ckan.ini sysadmin`
> 

A sign of a healthy free and open source software community is if and how long
it takes until you get a response a question when you encounter a problem like
this. In our case, it took just a couple of days, which means that the CKAN
community is very much alive and helpful. Thanks to
[Brett](https://github.com/ckan/ckan/issues/5621#issuecomment-699862976), here
is the solution:

```bash
ckan/contrib/docker$ docker exec -it ckan
$ source /usr/lib/ckan/venv/bin/activate
(venv) $ ckan -c /etc/ckan/production.ini sysadmin add admin email=admin@localhost name=admin
```

Of course you can (and should) change the username and email here. The email
address can be used later, for example, in case you forget your password and
need to reset it, without having to access the command like on the server again.
If everything goes correctly, the system should prompt you to insert a
password and to confirm it by typing a second time.

### Site administrator configuration through the web

Now we can log in to CKAN and start configuring the settings that can be
adjusted through the web interface. Open `localhost:5000` in a web browser.

<figure markdown="1">
![ckan: Login, Username, Password, Remember me]({{ 'assets/images/2020/09/ckan-login-en.gif' | relative_url }})
<figcaption>CKAN's login screen.</figcaption>
</figure>

After logging in, you should see a new bar at the top with your username and
a few interface elements you can click.

<figure markdown="1">
![ckan: Datasets, Organizations, Groups, About]({{ 'assets/images/2020/09/ckan-top-bar-en.png' | relative_url }})
<figcaption>The logged in user top bar.</figcaption>
</figure>

Click the hammer icon 🔨 there and at the "config" tab you can adjust more
settings, such as the site's name, logo, description and colors. Choose a
layout for the home page. You can also specify a custom CSS file to further
customize the look and feel of your data catalog.

<figure markdown="1">
![ckan: Config, Site Title, Style, Site Tag Line, Site logo, About, Intro Text, Custom CSS, Homepage]({{ 'assets/images/2020/09/ckan-site-config-en.gif' | relative_url }})
<figcaption>The CKAN site config screen.</figcaption>
</figure>

### Setting up organizations and groups

As a site administrator, you are also capable of inserting new datasets on
your catalog. But more usually, you would want to distribute that workload to
other people with a more focused role. There are many different ways you can
organize this. If you have a medium to large institution, you may want to
create "organizations" for each of your departments, so that each one manages
their own datasets. Organizations in CKAN are just a way to manage a large
quantity of datasets, delegating responsibilities to each department over their
respective datasets.

This might be a good time to set up the email service configuration, so that
CKAN can send emails to people when you create users and also for the password
reset system to function properly. For that, you need to edit the `.env` file,
at the following section:

```ini
# Email settings
CKAN_SMTP_SERVER=smtp.corporateict.domain:25
CKAN_SMTP_STARTTLS=True
CKAN_SMTP_USER=user
CKAN_SMTP_PASSWORD=pass
CKAN_SMTP_MAIL_FROM=ckan@localhost
```

Use your own SMTP server address and credentials there. Then restart CKAN
with

```bash
ckan/contrib/docker$ docker-compose restart ckan
```

for the changes to take effect. Now we can add the first organization:

<figure markdown="1">
![Organizations: Add Organization, search organizations, No organizations found]({{ 'assets/images/2020/09/ckan-organizations-en.png' | relative_url }})
<figcaption>The organizations screen.</figcaption>
</figure>

Click "Organizations", then the "Add organization" button.

<figure markdown="1">
![Create an Organization: Name, Description, Image]({{ 'assets/images/2020/09/ckan-new-organization-en.png' | relative_url }})
<figcaption>Adding a new organization.</figcaption>
</figure>

This is pretty simple. Add a name, a description and optionally an image to
represent it. Click "Create Organization". Then immediately click "🔧 Manage",
then the "👥 Members" tab, then "Add Member". Choose the role "Admin", as this
will be the administrator of this organization. Under "new user", fill in
their email address. They should receive a message with a link to create their
new user, which will automatically receive the permissions you set here
(in this case, the role of the administrator of this organization, which is
different from the site-wide administrator we're using).

<figure markdown="1">
![Add member: Existing user: if you wish to add an existing user, search for their username below; username. Or. New User: If you wish to invite a new user, enter their email address; Email address. Role: member.]({{ 'assets/images/2020/09/ckan-add-member-en.gif' | relative_url }})
<figcaption>Adding a new user.</figcaption>
</figure>

The organization administrator will then have to follow the link on their
email, activate their own accounts and log in. After that, they can follow the
same procedure above to add other users with the role of "Editor". After
activating their own accounts, editors can create and edit datasets in CKAN
inside their respective organizations.

Another way to organize datasets in the data catalog is by creating thematic
groups (e.g. health, education, transportation, etc.). This is completely
optional, but if you want to use it you can go at any moment to "Groups" at
the menu at the top, click "Add Group", and fill in the group information:
name, description and an image.

<figure markdown="1">
![Create a Group: Name, Description, Image]({{ 'assets/images/2020/09/ckan-create-group-en.png' | relative_url }})
<figcaption>Adding a new group.</figcaption>
</figure>

After that, the group should be available for editors to choose from when
creating or editing datasets.

For more information on managing organizations and datasets, see
[the corresponding section of the CKAN Sysadmin Guide](https://docs.ckan.org/en/2.9/sysadmin-guide.html#managing-organizations-and-datasets).

You should also instruct editors on how to create dataset and operate CKAN.
People with the role of editor should be someone who understands well the data
they're adding, because they will need to describe them adequately in plain
language to the end users of the data portal in a way that is easy to
understand. For instructions on how to create and edit datasets, the CKAN
documentation has a
[User Guide](https://docs.ckan.org/en/2.9/user-guide.html).

## Going into production mode

That covers the basic setup. Before going into production mode, it is
especially important that you edit and review all of the settings in both the
`.env` and the `production.ini` files. Please read the
"[steps toward production](https://docs.ckan.org/en/2.9/maintaining/installing/install-from-docker-compose.html#steps-towards-production)"
section of the Maintainer's Guide in the CKAN Documentation for more
information.

## Final thoughts

Overall, we had some problems with version 2.9.0, as the instructions from
the documentation did not work right away. However, with help from the CKAN
community, we were able to overcome those hurdles and to end up with a
working installation of the latest version of CKAN in a Docker environment.

**Edit:** for another possible way to install CKAN 2.9.0 with Docker, please
see this [blog post](https://blog.thenets.org/install-ckan-using-docker/) by
Luiz Felipe Costa. Luiz developed the CKAN customization for the
[dados.gov.br](https:/dados.gov.br)
[revision from 2017](https://wiki.dados.gov.br/ProdutoGT3_Portal%20de%20Dados%20Abertos.ashx#%E2%9E%83_E%C2%BA_Ciclo_CABH_15),
which I was the product owner of, and I can only recommend his services.
