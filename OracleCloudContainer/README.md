# This file belongs to a Demo in an Oracle Cloud Environment is about the Commands of Docker
#start of the workshop
Welcome to Oracle Cloud Shell.

Cloud Shell now runs on Oracle Linux 8. For more information, see the release notes. For help, contact Oracle Support.

Your Cloud Shell machine comes with 5GB of storage for your home directory. Your Cloud Shell (machine and home directory) are located in: Canada Southeast (Montreal).
You are using Cloud Shell in tenancy marcotrejolemus as OCI local user marco.trejo.lemus@outlook.com

Type `help` for more info.
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker -v
podman version 4.9.4-rhel
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker hello-world
Error: unrecognized command `podman hello-world`
Try 'podman --help' for more information
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker ps
CONTAINER ID  IMAGE       COMMAND     CREATED     STATUS      PORTS       NAMES
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker run -it busybox sh
Resolved "busybox" as an alias (/etc/containers/registries.conf.d/000-shortnames.conf)
Trying to pull docker.io/library/busybox:latest...
Getting image source signatures
Copying blob 265dab34035e done   | 
Copying config 82c58a5c5b done   | 
Writing manifest to image destination
/ # pwd
/
/ # ls
bin    dev    etc    home   lib    lib64  proc   root   run    sys    tmp    usr    var
/ # exit
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker ps -a
CONTAINER ID  IMAGE                             COMMAND     CREATED         STATUS                     PORTS       NAMES
7fdbf9e21811  docker.io/library/busybox:latest  sh          49 seconds ago  Exited (0) 20 seconds ago              objective_yalow
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker run -d -p 80:80 docker/getting-started
✔ docker.io/docker/getting-started:latest
Trying to pull docker.io/docker/getting-started:latest...
Getting image source signatures
Copying blob 33a28b928e89 done   | 
Copying blob 261da4162673 done   | 
Copying blob 2f61404bb4b8 done   | 
Copying blob a60aada4c44a done   | 
Copying blob fa3f58a317be done   | 
Copying blob 476bb2a1cc22 done   | 
Copying blob a879581b8e12 done   | 
Copying blob d0193f05f10f done   | 
Copying blob 14f901bbf056 done   | 
Copying config 289dc403af done   | 
Writing manifest to image destination
Error: rootlessport cannot expose privileged port 80, you can add 'net.ipv4.ip_unprivileged_port_start=80' to /etc/sysctl.conf (currently 1024), or choose a larger port number (>= 1024): listen tcp 0.0.0.0:80: bind: permission denied
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker run -d -p 8080:80 docker/getting-started
a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker ps -a
CONTAINER ID  IMAGE                                    COMMAND               CREATED        STATUS                    PORTS                 NAMES
7fdbf9e21811  docker.io/library/busybox:latest         sh                    5 minutes ago  Exited (0) 5 minutes ago                        objective_yalow
97d5fc4d5a28  docker.io/docker/getting-started:latest  nginx -g daemon o...  2 minutes ago  Created                   0.0.0.0:80->80/tcp    interesting_yonath
a17eb7127a59  docker.io/docker/getting-started:latest  nginx -g daemon o...  7 seconds ago  Up 8 seconds              0.0.0.0:8080->80/tcp  keen_leavitt
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker rm 97d5fc4d5a28
97d5fc4d5a28
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker ps -a
CONTAINER ID  IMAGE                                    COMMAND               CREATED             STATUS                    PORTS                 NAMES
7fdbf9e21811  docker.io/library/busybox:latest         sh                    7 minutes ago       Exited (0) 6 minutes ago                        objective_yalow
a17eb7127a59  docker.io/docker/getting-started:latest  nginx -g daemon o...  About a minute ago  Up About a minute         0.0.0.0:8080->80/tcp  keen_leavitt
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker rm a17eb7127a59
Error: cannot remove container a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b as it is running - running or paused containers cannot be removed without force: container state improper
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker ps -a
CONTAINER ID  IMAGE                                    COMMAND               CREATED        STATUS                    PORTS                 NAMES
7fdbf9e21811  docker.io/library/busybox:latest         sh                    8 minutes ago  Exited (0) 7 minutes ago                        objective_yalow
a17eb7127a59  docker.io/docker/getting-started:latest  nginx -g daemon o...  2 minutes ago  Up 2 minutes              0.0.0.0:8080->80/tcp  keen_leavitt
# marco_trej@cloudshell:~ (ca-montreal-1)$ curl 127.0.0.1:8080
<!doctype html><html lang=en class=no-js> <head><meta charset=utf-8><meta name=viewport content="width=device-width,initial-scale=1"><meta http-equiv=x-ua-compatible content="ie=edge"><meta name=description content="Getting Started with Docker"><script>var anchor=window.location.hash.substr(1);location.href="/tutorial/"+(anchor?"#"+anchor:"")</script><meta http-equiv=refresh content="0; url=/tutorial/"><meta name=robots content=noindex><link href=/tutorial/ rel=canonical><meta name=author content=Docker><meta name=lang:clipboard.copy content="Copy to clipboard"><meta name=lang:clipboard.copied content="Copied to clipboard"><meta name=lang:search.language content=en><meta name=lang:search.pipeline.stopwords content=True><meta name=lang:search.pipeline.trimmer content=True><meta name=lang:search.result.none content="No matching documents"><meta name=lang:search.result.one content="1 matching document"><meta name=lang:search.result.other content="# matching documents"><meta name=lang:search.tokenizer content=[\s\-]+><link rel="shortcut icon" href=assets/images/favicon.png><meta name=generator content="mkdocs-1.3.0, mkdocs-material-4.6.3"><title>Getting Started</title><link rel=stylesheet href=assets/stylesheets/application.adb8469c.css><link rel=stylesheet href=assets/stylesheets/application-palette.a8b3c06d.css><meta name=theme-color content=#2196f3><script src=assets/javascripts/modernizr.86422ebf.js></script><link href=https://fonts.gstatic.com rel=preconnect crossorigin><link rel=stylesheet href="https://fonts.googleapis.com/css?family=Roboto:300,400,400i,700%7CRoboto+Mono&display=fallback"><style>body,input{font-family:"Roboto","Helvetica Neue",Helvetica,Arial,sans-serif}code,kbd,pre{font-family:"Roboto Mono","Courier New",Courier,monospace}</style><link rel=stylesheet href=assets/fonts/material-icons.css><link rel=stylesheet href=css/styles.css><link rel=stylesheet href=css/dark-mode.css></head> <body dir=ltr data-md-color-primary=blue data-md-color-accent=blue> <svg class=md-svg> <defs> <svg xmlns=http://www.w3.org/2000/svg width=416 height=448 viewbox="0 0 416 448" id=__github><path fill=currentColor d="M160 304q0 10-3.125 20.5t-10.75 19T128 352t-18.125-8.5-10.75-19T96 304t3.125-20.5 10.75-19T128 256t18.125 8.5 10.75 19T160 304zm160 0q0 10-3.125 20.5t-10.75 19T288 352t-18.125-8.5-10.75-19T256 304t3.125-20.5 10.75-19T288 256t18.125 8.5 10.75 19T320 304zm40 0q0-30-17.25-51T296 232q-10.25 0-48.75 5.25Q229.5 240 208 240t-39.25-2.75Q130.75 232 120 232q-29.5 0-46.75 21T56 304q0 22 8 38.375t20.25 25.75 30.5 15 35 7.375 37.25 1.75h42q20.5 0 37.25-1.75t35-7.375 30.5-15 20.25-25.75T360 304zm56-44q0 51.75-15.25 82.75-9.5 19.25-26.375 33.25t-35.25 21.5-42.5 11.875-42.875 5.5T212 416q-19.5 0-35.5-.75t-36.875-3.125-38.125-7.5-34.25-12.875T37 371.5t-21.5-28.75Q0 312 0 260q0-59.25 34-99-6.75-20.5-6.75-42.5 0-29 12.75-54.5 27 0 47.5 9.875t47.25 30.875Q171.5 96 212 96q37 0 70 8 26.25-20.5 46.75-30.25T376 64q12.75 25.5 12.75 54.5 0 21.75-6.75 42 34 40 34 99.5z"/></svg> </defs> </svg> <input class=md-toggle data-md-toggle=drawer type=checkbox id=__drawer autocomplete=off> <input class=md-toggle data-md-toggle=search type=checkbox id=__search autocomplete=off> <label class=md-overlay data-md-component=overlay for=__drawer></label> <header class=md-header data-md-component=header> <nav class="md-header-nav md-grid"> <div class=md-flex> <div class="md-flex__cell md-flex__cell--shrink"> <a href=. title="Getting Started" aria-label="Getting Started" class="md-header-nav__button md-logo"> <img alt=logo src=images/docker-labs-logo.svg width=24 height=24> </a> </div> <div class="md-flex__cell md-flex__cell--shrink"> <label class="md-icon md-icon--menu md-header-nav__button" for=__drawer></label> </div> <div class="md-flex__cell md-flex__cell--stretch"> <div class="md-flex__ellipsis md-header-nav__title" data-md-component=title> <span class=md-header-nav__topic> Getting Started </span> <span class=md-header-nav__topic> Home </span> </div> </div> <div class="md-flex__cell md-flex__cell--shrink"> <label class="md-icon md-icon--search md-header-nav__button" for=__search></label> <div class=md-search data-md-component=search role=dialog> <label class=md-search__overlay for=__search></label> <div class=md-search__inner role=search> <form class=md-search__form name=search> <input type=text class=md-search__input aria-label=search name=query placeholder=Search autocapitalize=off autocorrect=off autocomplete=off spellcheck=false data-md-component=query data-md-state=active> <label class="md-icon md-search__icon" for=__search></label> <button type=reset class="md-icon md-search__icon" data-md-component=reset tabindex=-1> &#xE5CD; </button> </form> <div class=md-search__output> <div class=md-search__scrollwrap data-md-scrollfix> <div class=md-search-result data-md-component=result> <div class=md-search-result__meta> Type to start searching </div> <ol class=md-search-result__list></ol> </div> </div> </div> </div> </div> </div> <div class="md-flex__cell md-flex__cell--shrink"> <div class=md-header-nav__source> <a href=https://github.com/docker/getting-started title="Go to repository" class=md-source data-md-source=github> <div class=md-source__icon> <svg viewbox="0 0 24 24" width=24 height=24> <use xlink:href=#__github width=24 height=24></use> </svg> </div> <div class=md-source__repository> docker/getting-started </div> </a> </div> </div> </div> </nav> </header> <div class=md-container> <main class=md-main role=main> <div class="md-main__inner md-grid" data-md-component=container> <div class="md-sidebar md-sidebar--primary" data-md-component=navigation> <div class=md-sidebar__scrollwrap> <div class=md-sidebar__inner> <nav class="md-nav md-nav--primary" data-md-level=0> <label class="md-nav__title md-nav__title--site" for=__drawer> <a href=. title="Getting Started" class="md-nav__button md-logo"> <img alt=logo src=images/docker-labs-logo.svg width=48 height=48> </a> Getting Started </label> <div class=md-nav__source> <a href=https://github.com/docker/getting-started title="Go to repository" class=md-source data-md-source=github> <div class=md-source__icon> <svg viewbox="0 0 24 24" width=24 height=24> <use xlink:href=#__github width=24 height=24></use> </svg> </div> <div class=md-source__repository> docker/getting-started </div> </a> </div> <ul class=md-nav__list data-md-scrollfix> <li class=md-nav__item> <a href=tutorial/ title="Getting Started" class=md-nav__link> Getting Started </a> </li> <li class=md-nav__item> <a href=tutorial/our-application/ title="Our Application" class=md-nav__link> Our Application </a> </li> <li class=md-nav__item> <a href=tutorial/updating-our-app/ title="Updating our App" class=md-nav__link> Updating our App </a> </li> <li class=md-nav__item> <a href=tutorial/sharing-our-app/ title="Sharing our App" class=md-nav__link> Sharing our App </a> </li> <li class=md-nav__item> <a href=tutorial/persisting-our-data/ title="Persisting our DB" class=md-nav__link> Persisting our DB </a> </li> <li class=md-nav__item> <a href=tutorial/using-bind-mounts/ title="Using Bind Mounts" class=md-nav__link> Using Bind Mounts </a> </li> <li class=md-nav__item> <a href=tutorial/multi-container-apps/ title="Multi-Container Apps" class=md-nav__link> Multi-Container Apps </a> </li> <li class=md-nav__item> <a href=tutorial/using-docker-compose/ title="Using Docker Compose" class=md-nav__link> Using Docker Compose </a> </li> <li class=md-nav__item> <a href=tutorial/image-building-best-practices/ title="Image Building Best Practices" class=md-nav__link> Image Building Best Practices </a> </li> <li class=md-nav__item> <a href=tutorial/what-next/ title="What Next?" class=md-nav__link> What Next? </a> </li> </ul> </nav> </div> </div> </div> <div class=md-content> <article class="md-content__inner md-typeset"> <h1>Home</h1> </article> </div> </div> </main> <footer class=md-footer> <div class="md-footer-meta md-typeset"> <div class="md-footer-meta__inner md-grid"> <div class=md-footer-copyright> <div class=md-footer-copyright__highlight> Copyright &copy; 2020-2022 Docker </div> powered by <a href=https://www.mkdocs.org target=_blank rel=noopener>MkDocs</a> and <a href=https://squidfunk.github.io/mkdocs-material/ target=_blank rel=noopener> Material for MkDocs</a> </div> <div class=md-footer-social> <link rel=stylesheet href=assets/fonts/font-awesome.css> <a href=https://github.com/docker/getting-started target=_blank rel=noopener title=github-alt class="md-footer-social__link fa fa-github-alt"></a> </div> </div> </div> </footer> </div> <script src=assets/javascripts/application.c33a9706.js></script> <script>app.initialize({version:"1.3.0",url:{base:"."}})</script> </body> </html>
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker ps -a
CONTAINER ID  IMAGE                                    COMMAND               CREATED         STATUS                     PORTS                 NAMES
7fdbf9e21811  docker.io/library/busybox:latest         sh                    14 minutes ago  Exited (0) 13 minutes ago                        objective_yalow
a17eb7127a59  docker.io/docker/getting-started:latest  nginx -g daemon o...  8 minutes ago   Up 8 minutes               0.0.0.0:8080->80/tcp  keen_leavitt
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker stop 7fdbf9e21811
7fdbf9e21811
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker stop a17eb7127a59
a17eb7127a59
# marco_trej@cloudshell:~ (ca-montreal-1)$ curl 127.0.0.1:8080
curl: (7) Failed to connect to 127.0.0.1 port 8080: Connection refused
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker start a17eb7127a59
a17eb7127a59
# marco_trej@cloudshell:~ (ca-montreal-1)$ curl 127.0.0.1:8080
<!doctype html><html lang=en class=no-js> <head><meta charset=utf-8><meta name=viewport content="width=device-width,initial-scale=1"><meta http-equiv=x-ua-compatible content="ie=edge"><meta name=description content="Getting Started with Docker"><script>var anchor=window.location.hash.substr(1);location.href="/tutorial/"+(anchor?"#"+anchor:"")</script><meta http-equiv=refresh content="0; url=/tutorial/"><meta name=robots content=noindex><link href=/tutorial/ rel=canonical><meta name=author content=Docker><meta name=lang:clipboard.copy content="Copy to clipboard"><meta name=lang:clipboard.copied content="Copied to clipboard"><meta name=lang:search.language content=en><meta name=lang:search.pipeline.stopwords content=True><meta name=lang:search.pipeline.trimmer content=True><meta name=lang:search.result.none content="No matching documents"><meta name=lang:search.result.one content="1 matching document"><meta name=lang:search.result.other content="# matching documents"><meta name=lang:search.tokenizer content=[\s\-]+><link rel="shortcut icon" href=assets/images/favicon.png><meta name=generator content="mkdocs-1.3.0, mkdocs-material-4.6.3"><title>Getting Started</title><link rel=stylesheet href=assets/stylesheets/application.adb8469c.css><link rel=stylesheet href=assets/stylesheets/application-palette.a8b3c06d.css><meta name=theme-color content=#2196f3><script src=assets/javascripts/modernizr.86422ebf.js></script><link href=https://fonts.gstatic.com rel=preconnect crossorigin><link rel=stylesheet href="https://fonts.googleapis.com/css?family=Roboto:300,400,400i,700%7CRoboto+Mono&display=fallback"><style>body,input{font-family:"Roboto","Helvetica Neue",Helvetica,Arial,sans-serif}code,kbd,pre{font-family:"Roboto Mono","Courier New",Courier,monospace}</style><link rel=stylesheet href=assets/fonts/material-icons.css><link rel=stylesheet href=css/styles.css><link rel=stylesheet href=css/dark-mode.css></head> <body dir=ltr data-md-color-primary=blue data-md-color-accent=blue> <svg class=md-svg> <defs> <svg xmlns=http://www.w3.org/2000/svg width=416 height=448 viewbox="0 0 416 448" id=__github><path fill=currentColor d="M160 304q0 10-3.125 20.5t-10.75 19T128 352t-18.125-8.5-10.75-19T96 304t3.125-20.5 10.75-19T128 256t18.125 8.5 10.75 19T160 304zm160 0q0 10-3.125 20.5t-10.75 19T288 352t-18.125-8.5-10.75-19T256 304t3.125-20.5 10.75-19T288 256t18.125 8.5 10.75 19T320 304zm40 0q0-30-17.25-51T296 232q-10.25 0-48.75 5.25Q229.5 240 208 240t-39.25-2.75Q130.75 232 120 232q-29.5 0-46.75 21T56 304q0 22 8 38.375t20.25 25.75 30.5 15 35 7.375 37.25 1.75h42q20.5 0 37.25-1.75t35-7.375 30.5-15 20.25-25.75T360 304zm56-44q0 51.75-15.25 82.75-9.5 19.25-26.375 33.25t-35.25 21.5-42.5 11.875-42.875 5.5T212 416q-19.5 0-35.5-.75t-36.875-3.125-38.125-7.5-34.25-12.875T37 371.5t-21.5-28.75Q0 312 0 260q0-59.25 34-99-6.75-20.5-6.75-42.5 0-29 12.75-54.5 27 0 47.5 9.875t47.25 30.875Q171.5 96 212 96q37 0 70 8 26.25-20.5 46.75-30.25T376 64q12.75 25.5 12.75 54.5 0 21.75-6.75 42 34 40 34 99.5z"/></svg> </defs> </svg> <input class=md-toggle data-md-toggle=drawer type=checkbox id=__drawer autocomplete=off> <input class=md-toggle data-md-toggle=search type=checkbox id=__search autocomplete=off> <label class=md-overlay data-md-component=overlay for=__drawer></label> <header class=md-header data-md-component=header> <nav class="md-header-nav md-grid"> <div class=md-flex> <div class="md-flex__cell md-flex__cell--shrink"> <a href=. title="Getting Started" aria-label="Getting Started" class="md-header-nav__button md-logo"> <img alt=logo src=images/docker-labs-logo.svg width=24 height=24> </a> </div> <div class="md-flex__cell md-flex__cell--shrink"> <label class="md-icon md-icon--menu md-header-nav__button" for=__drawer></label> </div> <div class="md-flex__cell md-flex__cell--stretch"> <div class="md-flex__ellipsis md-header-nav__title" data-md-component=title> <span class=md-header-nav__topic> Getting Started </span> <span class=md-header-nav__topic> Home </span> </div> </div> <div class="md-flex__cell md-flex__cell--shrink"> <label class="md-icon md-icon--search md-header-nav__button" for=__search></label> <div class=md-search data-md-component=search role=dialog> <label class=md-search__overlay for=__search></label> <div class=md-search__inner role=search> <form class=md-search__form name=search> <input type=text class=md-search__input aria-label=search name=query placeholder=Search autocapitalize=off autocorrect=off autocomplete=off spellcheck=false data-md-component=query data-md-state=active> <label class="md-icon md-search__icon" for=__search></label> <button type=reset class="md-icon md-search__icon" data-md-component=reset tabindex=-1> &#xE5CD; </button> </form> <div class=md-search__output> <div class=md-search__scrollwrap data-md-scrollfix> <div class=md-search-result data-md-component=result> <div class=md-search-result__meta> Type to start searching </div> <ol class=md-search-result__list></ol> </div> </div> </div> </div> </div> </div> <div class="md-flex__cell md-flex__cell--shrink"> <div class=md-header-nav__source> <a href=https://github.com/docker/getting-started title="Go to repository" class=md-source data-md-source=github> <div class=md-source__icon> <svg viewbox="0 0 24 24" width=24 height=24> <use xlink:href=#__github width=24 height=24></use> </svg> </div> <div class=md-source__repository> docker/getting-started </div> </a> </div> </div> </div> </nav> </header> <div class=md-container> <main class=md-main role=main> <div class="md-main__inner md-grid" data-md-component=container> <div class="md-sidebar md-sidebar--primary" data-md-component=navigation> <div class=md-sidebar__scrollwrap> <div class=md-sidebar__inner> <nav class="md-nav md-nav--primary" data-md-level=0> <label class="md-nav__title md-nav__title--site" for=__drawer> <a href=. title="Getting Started" class="md-nav__button md-logo"> <img alt=logo src=images/docker-labs-logo.svg width=48 height=48> </a> Getting Started </label> <div class=md-nav__source> <a href=https://github.com/docker/getting-started title="Go to repository" class=md-source data-md-source=github> <div class=md-source__icon> <svg viewbox="0 0 24 24" width=24 height=24> <use xlink:href=#__github width=24 height=24></use> </svg> </div> <div class=md-source__repository> docker/getting-started </div> </a> </div> <ul class=md-nav__list data-md-scrollfix> <li class=md-nav__item> <a href=tutorial/ title="Getting Started" class=md-nav__link> Getting Started </a> </li> <li class=md-nav__item> <a href=tutorial/our-application/ title="Our Application" class=md-nav__link> Our Application </a> </li> <li class=md-nav__item> <a href=tutorial/updating-our-app/ title="Updating our App" class=md-nav__link> Updating our App </a> </li> <li class=md-nav__item> <a href=tutorial/sharing-our-app/ title="Sharing our App" class=md-nav__link> Sharing our App </a> </li> <li class=md-nav__item> <a href=tutorial/persisting-our-data/ title="Persisting our DB" class=md-nav__link> Persisting our DB </a> </li> <li class=md-nav__item> <a href=tutorial/using-bind-mounts/ title="Using Bind Mounts" class=md-nav__link> Using Bind Mounts </a> </li> <li class=md-nav__item> <a href=tutorial/multi-container-apps/ title="Multi-Container Apps" class=md-nav__link> Multi-Container Apps </a> </li> <li class=md-nav__item> <a href=tutorial/using-docker-compose/ title="Using Docker Compose" class=md-nav__link> Using Docker Compose </a> </li> <li class=md-nav__item> <a href=tutorial/image-building-best-practices/ title="Image Building Best Practices" class=md-nav__link> Image Building Best Practices </a> </li> <li class=md-nav__item> <a href=tutorial/what-next/ title="What Next?" class=md-nav__link> What Next? </a> </li> </ul> </nav> </div> </div> </div> <div class=md-content> <article class="md-content__inner md-typeset"> <h1>Home</h1> </article> </div> </div> </main> <footer class=md-footer> <div class="md-footer-meta md-typeset"> <div class="md-footer-meta__inner md-grid"> <div class=md-footer-copyright> <div class=md-footer-copyright__highlight> Copyright &copy; 2020-2022 Docker </div> powered by <a href=https://www.mkdocs.org target=_blank rel=noopener>MkDocs</a> and <a href=https://squidfunk.github.io/mkdocs-material/ target=_blank rel=noopener> Material for MkDocs</a> </div> <div class=md-footer-social> <link rel=stylesheet href=assets/fonts/font-awesome.css> <a href=https://github.com/docker/getting-started target=_blank rel=noopener title=github-alt class="md-footer-social__link fa fa-github-alt"></a> </div> </div> </div> </footer> </div> <script src=assets/javascripts/application.c33a9706.js></script> <script>app.initialize({version:"1.3.0",url:{base:"."}})</script> </body> </html>
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker restart a17eb7127a59
a17eb7127a59
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker port a17eb7127a59
80/tcp -> 0.0.0.0:8080
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker logs a17eb7127a59
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: Getting the checksum of /etc/nginx/conf.d/default.conf
10-listen-on-ipv6-by-default.sh: info: Enabled listen on IPv6 in /etc/nginx/conf.d/default.conf
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2025/03/28 02:26:49 [notice] 1#1: using the "epoll" event method
2025/03/28 02:26:49 [notice] 1#1: nginx/1.23.3
2025/03/28 02:26:49 [notice] 1#1: built by gcc 12.2.1 20220924 (Alpine 12.2.1_git20220924-r4) 
2025/03/28 02:26:49 [notice] 1#1: OS: Linux 5.4.17-2136.341.3.1.el8uek.aarch64
2025/03/28 02:26:49 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2025/03/28 02:26:49 [notice] 1#1: start worker processes
2025/03/28 02:26:49 [notice] 1#1: start worker process 30
2025/03/28 02:26:49 [notice] 1#1: start worker process 31
10.0.2.100 - - [28/Mar/2025:02:34:16 +0000] "GET / HTTP/1.1" 200 8702 "-" "curl/7.61.1" "-"
2025/03/28 02:36:20 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2025/03/28 02:36:20 [notice] 30#30: gracefully shutting down
2025/03/28 02:36:20 [notice] 30#30: exiting
2025/03/28 02:36:20 [notice] 30#30: exit
2025/03/28 02:36:20 [notice] 31#31: gracefully shutting down
2025/03/28 02:36:20 [notice] 31#31: exiting
2025/03/28 02:36:20 [notice] 31#31: exit
2025/03/28 02:36:20 [notice] 1#1: signal 17 (SIGCHLD) received from 31
2025/03/28 02:36:20 [notice] 1#1: worker process 30 exited with code 0
2025/03/28 02:36:20 [notice] 1#1: worker process 31 exited with code 0
2025/03/28 02:36:20 [notice] 1#1: exit
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2025/03/28 02:38:51 [notice] 1#1: using the "epoll" event method
2025/03/28 02:38:51 [notice] 1#1: nginx/1.23.3
2025/03/28 02:38:51 [notice] 1#1: built by gcc 12.2.1 20220924 (Alpine 12.2.1_git20220924-r4) 
2025/03/28 02:38:51 [notice] 1#1: OS: Linux 5.4.17-2136.341.3.1.el8uek.aarch64
2025/03/28 02:38:51 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2025/03/28 02:38:51 [notice] 1#1: start worker processes
2025/03/28 02:38:51 [notice] 1#1: start worker process 22
2025/03/28 02:38:51 [notice] 1#1: start worker process 23
10.0.2.100 - - [28/Mar/2025:02:39:03 +0000] "GET / HTTP/1.1" 200 8702 "-" "curl/7.61.1" "-"
2025/03/28 02:39:15 [notice] 1#1: signal 3 (SIGQUIT) received, shutting down
2025/03/28 02:39:15 [notice] 23#23: gracefully shutting down
2025/03/28 02:39:15 [notice] 23#23: exiting
2025/03/28 02:39:15 [notice] 22#22: gracefully shutting down
2025/03/28 02:39:15 [notice] 23#23: exit
2025/03/28 02:39:15 [notice] 22#22: exiting
2025/03/28 02:39:15 [notice] 22#22: exit
2025/03/28 02:39:15 [notice] 1#1: signal 17 (SIGCHLD) received from 23
2025/03/28 02:39:15 [notice] 1#1: worker process 22 exited with code 0
2025/03/28 02:39:15 [notice] 1#1: worker process 23 exited with code 0
2025/03/28 02:39:15 [notice] 1#1: exit
/docker-entrypoint.sh: /docker-entrypoint.d/ is not empty, will attempt to perform configuration
/docker-entrypoint.sh: Looking for shell scripts in /docker-entrypoint.d/
/docker-entrypoint.sh: Launching /docker-entrypoint.d/10-listen-on-ipv6-by-default.sh
10-listen-on-ipv6-by-default.sh: info: IPv6 listen already enabled
/docker-entrypoint.sh: Launching /docker-entrypoint.d/20-envsubst-on-templates.sh
/docker-entrypoint.sh: Launching /docker-entrypoint.d/30-tune-worker-processes.sh
/docker-entrypoint.sh: Configuration complete; ready for start up
2025/03/28 02:39:16 [notice] 1#1: using the "epoll" event method
2025/03/28 02:39:16 [notice] 1#1: nginx/1.23.3
2025/03/28 02:39:16 [notice] 1#1: built by gcc 12.2.1 20220924 (Alpine 12.2.1_git20220924-r4) 
2025/03/28 02:39:16 [notice] 1#1: OS: Linux 5.4.17-2136.341.3.1.el8uek.aarch64
2025/03/28 02:39:16 [notice] 1#1: getrlimit(RLIMIT_NOFILE): 1048576:1048576
2025/03/28 02:39:16 [notice] 1#1: start worker processes
2025/03/28 02:39:16 [notice] 1#1: start worker process 21
2025/03/28 02:39:16 [notice] 1#1: start worker process 22
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker inspect a17eb7127a59
[
     {
          "Id": "a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b",
          "Created": "2025-03-28T02:26:49.173288968Z",
          "Path": "/docker-entrypoint.sh",
          "Args": [
               "nginx",
               "-g",
               "daemon off;"
          ],
          "State": {
               "OciVersion": "1.1.0+dev",
               "Status": "running",
               "Running": true,
               "Paused": false,
               "Restarting": false,
               "OOMKilled": false,
               "Dead": false,
               "Pid": 3269,
               "ConmonPid": 3259,
               "ExitCode": 0,
               "Error": "",
               "StartedAt": "2025-03-28T02:39:16.16491791Z",
               "FinishedAt": "2025-03-28T02:39:15.558138091Z",
               "Health": {
                    "Status": "",
                    "FailingStreak": 0,
                    "Log": null
               },
               "CgroupPath": "/",
               "CheckpointedAt": "0001-01-01T00:00:00Z",
               "RestoredAt": "0001-01-01T00:00:00Z"
          },
          "Image": "289dc403af49e8876db321c0c403ec50d79d74a236b1119d0c071d25ddd1205b",
          "ImageDigest": "sha256:d79336f4812b6547a53e735480dde67f8f8f7071b414fbd9297609ffb989abc1",
          "ImageName": "docker.io/docker/getting-started:latest",
          "Rootfs": "",
          "Pod": "",
          "ResolvConfPath": "/tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/resolv.conf",
          "HostnamePath": "/tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/hostname",
          "HostsPath": "/tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/hosts",
          "StaticDir": "/home/marco_trej/.local/share/containers/storage/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata",
          "OCIConfigPath": "/home/marco_trej/.local/share/containers/storage/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/config.json",
          "OCIRuntime": "runc",
          "ConmonPidFile": "/tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/conmon.pid",
          "PidFile": "/tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/pidfile",
          "Name": "keen_leavitt",
          "RestartCount": 0,
          "Driver": "overlay",
          "MountLabel": "",
          "ProcessLabel": "",
          "AppArmorProfile": "",
          "EffectiveCaps": [
               "CAP_CHOWN",
               "CAP_DAC_OVERRIDE",
               "CAP_FOWNER",
               "CAP_FSETID",
               "CAP_KILL",
               "CAP_NET_BIND_SERVICE",
               "CAP_NET_RAW",
               "CAP_SETFCAP",
               "CAP_SETGID",
               "CAP_SETPCAP",
               "CAP_SETUID",
               "CAP_SYS_CHROOT"
          ],
          "BoundingCaps": [
               "CAP_CHOWN",
               "CAP_DAC_OVERRIDE",
               "CAP_FOWNER",
               "CAP_FSETID",
               "CAP_KILL",
               "CAP_NET_BIND_SERVICE",
               "CAP_NET_RAW",
               "CAP_SETFCAP",
               "CAP_SETGID",
               "CAP_SETPCAP",
               "CAP_SETUID",
               "CAP_SYS_CHROOT"
          ],
          "ExecIDs": [],
          "GraphDriver": {
               "Name": "overlay",
               "Data": {
                    "LowerDir": "/home/marco_trej/.local/share/containers/storage/overlay/146ffdad9d9ec06a828a8b3dacf1f56a5e5f1e3c1a539a717b429e4241493e79/diff:/home/marco_trej/.local/share/containers/storage/overlay/6fc65fa43f89a6b7519f85bee3457a7ef0ea05f4e84f1c9e9b9110f4dce98693/diff:/home/marco_trej/.local/share/containers/storage/overlay/fe0e75a1787eb02fe2ab5f6713120e9e1e67ebe6763dfcea4f398206b151413d/diff:/home/marco_trej/.local/share/containers/storage/overlay/6463b6dff26d1cc72a12c547531e25c7d555810a86685dc84587f4a742bf2ef7/diff:/home/marco_trej/.local/share/containers/storage/overlay/7bd68780e83c567cfdbfd4508708165485563e6d5530c40595b01a3857bed60e/diff:/home/marco_trej/.local/share/containers/storage/overlay/1a0678208aff32cce55f938771fc1f7ff809ea101460820997b80bc48e05e9bc/diff:/home/marco_trej/.local/share/containers/storage/overlay/526df376f1cbad7faba2708e4ede520514df7dac9e39b672b71c6d2970a0ec05/diff:/home/marco_trej/.local/share/containers/storage/overlay/a13a1a261818b2a879ffe624bd2ae763452fd211e033ab941f6fcf1443df2361/diff:/home/marco_trej/.local/share/containers/storage/overlay/1b577a8fb8ce25023a0ec0a17a6dc3d6aa9cca989f75457800cb55179ee2e834/diff",
                    "MergedDir": "/home/marco_trej/.local/share/containers/storage/overlay/a9c6bea4d1b9968d1f343cfc182df5794158e61255c40d2d46268a42ad0b8c33/merged",
                    "UpperDir": "/home/marco_trej/.local/share/containers/storage/overlay/a9c6bea4d1b9968d1f343cfc182df5794158e61255c40d2d46268a42ad0b8c33/diff",
                    "WorkDir": "/home/marco_trej/.local/share/containers/storage/overlay/a9c6bea4d1b9968d1f343cfc182df5794158e61255c40d2d46268a42ad0b8c33/work"
               }
          },
          "Mounts": [
               {
                    "Type": "bind",
                    "Source": "/proc",
                    "Destination": "/proc",
                    "Driver": "",
                    "Mode": "",
                    "Options": [
                         "noexec",
                         "nosuid",
                         "nodev",
                         "rbind"
                    ],
                    "RW": true,
                    "Propagation": "rprivate"
               }
          ],
          "Dependencies": [],
          "NetworkSettings": {
               "EndpointID": "",
               "Gateway": "",
               "IPAddress": "",
               "IPPrefixLen": 0,
               "IPv6Gateway": "",
               "GlobalIPv6Address": "",
               "GlobalIPv6PrefixLen": 0,
               "MacAddress": "",
               "Bridge": "",
               "SandboxID": "",
               "HairpinMode": false,
               "LinkLocalIPv6Address": "",
               "LinkLocalIPv6PrefixLen": 0,
               "Ports": {
                    "80/tcp": [
                         {
                              "HostIp": "",
                              "HostPort": "8080"
                         }
                    ]
               },
               "SandboxKey": "/run/user/1101/netns/netns-e5897a7a-ac73-7b28-bc92-ef81798463fb"
          },
          "Namespace": "",
          "IsInfra": false,
          "IsService": false,
          "KubeExitCodePropagation": "invalid",
          "lockNumber": 2,
          "Config": {
               "Hostname": "a17eb7127a59",
               "Domainname": "",
               "User": "",
               "AttachStdin": false,
               "AttachStdout": false,
               "AttachStderr": false,
               "Tty": false,
               "OpenStdin": false,
               "StdinOnce": false,
               "Env": [
                    "PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin",
                    "container=podman",
                    "PKG_RELEASE=1",
                    "NJS_VERSION=0.7.9",
                    "NGINX_VERSION=1.23.3",
                    "HOME=/root",
                    "HOSTNAME=a17eb7127a59"
               ],
               "Cmd": [
                    "nginx",
                    "-g",
                    "daemon off;"
               ],
               "Image": "docker.io/docker/getting-started:latest",
               "Volumes": null,
               "WorkingDir": "/",
               "Entrypoint": "/docker-entrypoint.sh",
               "OnBuild": null,
               "Labels": {
                    "maintainer": "NGINX Docker Maintainers <docker-maint@nginx.com>"
               },
               "Annotations": {
                    "io.container.manager": "libpod",
                    "org.opencontainers.image.stopSignal": "3"
               },
               "StopSignal": 3,
               "HealthcheckOnFailureAction": "none",
               "CreateCommand": [
                    "/usr/bin/podman",
                    "run",
                    "-d",
                    "-p",
                    "8080:80",
                    "docker/getting-started"
               ],
               "Umask": "0022",
               "Timeout": 0,
               "StopTimeout": 10,
               "Passwd": true,
               "sdNotifyMode": "container",
               "ExposedPorts": {
                    "80/tcp": {}
               }
          },
          "HostConfig": {
               "Binds": [
                    "/proc:/proc:rw,rprivate,noexec,nosuid,nodev,rbind"
               ],
               "CgroupManager": "cgroupfs",
               "CgroupMode": "private",
               "ContainerIDFile": "",
               "LogConfig": {
                    "Type": "k8s-file",
                    "Config": null,
                    "Path": "/home/marco_trej/.local/share/containers/storage/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/ctr.log",
                    "Tag": "",
                    "Size": "0B"
               },
               "NetworkMode": "slirp4netns",
               "PortBindings": {
                    "80/tcp": [
                         {
                              "HostIp": "",
                              "HostPort": "8080"
                         }
                    ]
               },
               "RestartPolicy": {
                    "Name": "",
                    "MaximumRetryCount": 0
               },
               "AutoRemove": false,
               "VolumeDriver": "",
               "VolumesFrom": null,
               "CapAdd": [],
               "CapDrop": [],
               "Dns": [],
               "DnsOptions": [],
               "DnsSearch": [],
               "ExtraHosts": [],
               "GroupAdd": [],
               "IpcMode": "shareable",
               "Cgroup": "",
               "Cgroups": "default",
               "Links": null,
               "OomScoreAdj": 0,
               "PidMode": "private",
               "Privileged": false,
               "PublishAllPorts": false,
               "ReadonlyRootfs": false,
               "SecurityOpt": [],
               "Tmpfs": {},
               "UTSMode": "private",
               "UsernsMode": "",
               "ShmSize": 65536000,
               "Runtime": "oci",
               "ConsoleSize": [
                    0,
                    0
               ],
               "Isolation": "",
               "CpuShares": 0,
               "Memory": 0,
               "NanoCpus": 0,
               "CgroupParent": "",
               "BlkioWeight": 0,
               "BlkioWeightDevice": null,
               "BlkioDeviceReadBps": null,
               "BlkioDeviceWriteBps": null,
               "BlkioDeviceReadIOps": null,
               "BlkioDeviceWriteIOps": null,
               "CpuPeriod": 0,
               "CpuQuota": 0,
               "CpuRealtimePeriod": 0,
               "CpuRealtimeRuntime": 0,
               "CpusetCpus": "",
               "CpusetMems": "",
               "Devices": [],
               "DiskQuota": 0,
               "KernelMemory": 0,
               "MemoryReservation": 0,
               "MemorySwap": 0,
               "MemorySwappiness": 0,
               "OomKillDisable": false,
               "PidsLimit": 0,
               "Ulimits": [
                    {
                         "Name": "RLIMIT_NPROC",
                         "Soft": 4194304,
                         "Hard": 4194304
                    },
                    {
                         "Name": "RLIMIT_NOFILE",
                         "Soft": 1048576,
                         "Hard": 1048576
                    }
               ],
               "CpuCount": 0,
               "CpuPercent": 0,
               "IOMaximumIOps": 0,
               "IOMaximumBandwidth": 0,
               "CgroupConf": null
          }
     }
]
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker top a17eb7127a59
USER        PID         PPID        %CPU        ELAPSED            TTY         TIME        COMMAND
nobody      1           0           0.000       9h14m35.62454292s  ?           0s          /bin/bash 
root        1009        0           0.000       34m15.624774361s   ?           0s          /bin/bash /usr/local/bin/runExtension.sh -t initializer -i 2 
root        1243        1009        0.000       34m14.624871602s   ?           0s          /bin/bash /etc/extensions/theia/scripts/1/theia-runner.sh 
root        1309        0           0.000       34m13.624966642s   ?           0s          /bin/bash 
root        1328        1243        0.000       34m13.625099963s   ?           0s          /usr/bin/node /usr/bin/yarn start -p 4444 -h 0.0.0.0 
root        1526        1328        0.000       34m13.625196564s   ?           0s          /usr/bin/node /etc/cloud-shell-editor/browser-app/node_modules/.bin/theia start --plugins=local-dir:plugins --mode production -p 4444 -h 0.0.0.0 
root        1669        1526        0.146       34m11.625292484s   ?           3s          /usr/bin/node /etc/cloud-shell-editor/browser-app/src-gen/backend/main.js --plugins=local-dir:plugins --mode production -p 4444 -h 0.0.0.0 
root        1680        1669        0.098       34m1.625387325s    ?           2s          /usr/bin/node /etc/cloud-shell-editor/node_modules/@theia/core/lib/node/messaging/ipc-bootstrap --nsfwOptions={} 
root        1869        1           0.000       23m50.625481326s   ?           0s          catatonit -P 
root        3046        1           0.000       4m56.625598646s    ?           0s          /usr/bin/fuse-overlayfs -o lowerdir=/home/marco_trej/.local/share/containers/storage/overlay/l/D43GGHCLJSQTUQZB7XN5SQHNZG:/home/marco_trej/.local/share/containers/storage/overlay/l/UZ2TNN26BLG3HBZDKF5FZNU4GE:/home/marco_trej/.local/share/containers/storage/overlay/l/3FSQNGBLBT5HML66BQSM3DFYXC:/home/marco_trej/.local/share/containers/storage/overlay/l/4VBDFILF6FELJMY4XQU5DA22CX:/home/marco_trej/.local/share/containers/storage/overlay/l/VHUKTRYH5KYI7THQH53LKF24TL:/home/marco_trej/.local/share/containers/storage/overlay/l/ON6ILQOPAL6OJ2BGKWPAWTZHI4:/home/marco_trej/.local/share/containers/storage/overlay/l/TZJH2RVUDEPZAFVA2HDT7JWWYQ:/home/marco_trej/.local/share/containers/storage/overlay/l/JPX5MIS2PRQE47PKOVX7N4AQGG:/home/marco_trej/.local/share/containers/storage/overlay/l/2U5BOZWXI2TIOJBRDKKSNCCQS6,upperdir=/home/marco_trej/.local/share/containers/storage/overlay/a9c6bea4d1b9968d1f343cfc182df5794158e61255c40d2d46268a42ad0b8c33/diff,workdir=/home/marco_trej/.local/share/containers/storage/overlay/a9c6bea4d1b9968d1f343cfc182df5794158e61255c40d2d46268a42ad0b8c33/work /home/marco_trej/.local/share/containers/storage/overlay/a9c6bea4d1b9968d1f343cfc182df5794158e61255c40d2d46268a42ad0b8c33/merged 
root        3238        1           0.000       4m31.625697567s    ?           0s          /usr/bin/slirp4netns --disable-host-loopback --mtu=65520 --enable-sandbox --enable-seccomp --enable-ipv6 -c -r 3 -e 4 --netns-type=path /run/user/1101/netns/netns-e5897a7a-ac73-7b28-bc92-ef81798463fb tap0 
root        3240        1           0.000       4m31.625794408s    ?           0s          rootlessport 
root        3245        3240        0.000       4m31.625892448s    ?           0s          rootlessport-child 
root        3259        1           0.000       4m30.625989889s    ?           0s          /usr/bin/conmon --api-version 1 -c a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b -u a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b -r /usr/bin/runc -b /home/marco_trej/.local/share/containers/storage/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata -p /tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/pidfile -n keen_leavitt --exit-dir /run/user/1101/libpod/tmp/exits --full-attach -l k8s-file:/home/marco_trej/.local/share/containers/storage/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/ctr.log --log-level warning --syslog --runtime-arg --log-format=json --runtime-arg --log --runtime-arg=/tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/oci-log --conmon-pidfile /tmp/containers-user-1101/containers/overlay-containers/a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b/userdata/conmon.pid --exit-command /usr/bin/podman --exit-command-arg --root --exit-command-arg /home/marco_trej/.local/share/containers/storage --exit-command-arg --runroot --exit-command-arg /tmp/containers-user-1101/containers --exit-command-arg --log-level --exit-command-arg warning --exit-command-arg --cgroup-manager --exit-command-arg cgroupfs --exit-command-arg --tmpdir --exit-command-arg /run/user/1101/libpod/tmp --exit-command-arg --network-config-dir --exit-command-arg  --exit-command-arg --network-backend --exit-command-arg cni --exit-command-arg --volumepath --exit-command-arg /home/marco_trej/.local/share/containers/storage/volumes --exit-command-arg --db-backend --exit-command-arg sqlite --exit-command-arg --transient-store=false --exit-command-arg --runtime --exit-command-arg runc --exit-command-arg --storage-driver --exit-command-arg overlay --exit-command-arg --events-backend --exit-command-arg file --exit-command-arg container --exit-command-arg cleanup --exit-command-arg a17eb7127a5909284b01a459d1b295457e3c787869fd06f105f3b22131d9de0b 
root        3269        3259        0.000       4m30.626089889s    ?           0s          nginx: master process nginx -g daemon off; 
nginx       3306        3269        0.000       4m30.62618525s     ?           0s          nginx: worker process 
nginx       3307        3269        0.000       4m30.626281131s    ?           0s          nginx: worker process 
root        3543        1309        0.000       626.376171ms       ?           0s          /usr/bin/podman top a17eb7127a59 
root        3549        3543        0.000       626.471772ms       ?           0s          /usr/bin/podman top a17eb7127a59 
# marco_trej@cloudshell:~ (ca-montreal-1)$ docker exec -it a17eb7127a59 sh
/ #  (Ctrl +D to exit)
# marco_trej@cloudshell:~ (ca-montreal-1)$
## Thi is the end of the practice in where we can see the commands running over a n Oracle Cloud service
# End of the workshop
