## alban.andrieu.squirrel

[![Travis CI](http://img.shields.io/travis/AlbanAndrieu/ansible-squirrel.svg?style=flat)](http://travis-ci.org/AlbanAndrieu/ansible-squirrel) [![Branch](http://img.shields.io/github/tag/AlbanAndrieu/ansible-squirrel.svg?style=flat-square)](https://github.com/AlbanAndrieu/ansible-squirrel/tree/master) [![Donate](https://img.shields.io/gratipay/AlbanAndrieu.svg?style=flat)](https://www.gratipay.com/AlbanAndrieu)  [![Ansible Galaxy](http://img.shields.io/badge/galaxy-alban.andrieu.squirrel-blue.svg?style=flat)](https://galaxy.ansible.com/list#/roles/1776) [![Platforms](http://img.shields.io/badge/platforms-ubuntu-lightgrey.svg?style=flat)](#)

Ensures that squirrel is properly installed and configured on `Ubuntu` using `Ansible` script.
Default settings is using squirrel luna.
This ``Simple`` role allows you to install [squirrel](https://www.squirrel.org) with basic plugins.

This playbook is be used by [Docker Hub](https://hub.docker.com) to create a [Docker](http://docker.io) image.

Taken from
------------------

https://www.squirrel.org/downloads/

###Requirements

Tools which might be needed by [squirrel](https://www.squirrel.org), like jdk, maven...
See available playbook on [GitHub](https://github.com/search?p=3&q=user%3AAlbanAndrieu+ansible%2A&type=Repositories)

### Installation

This role requires at least Ansible `v1.6.3`.

To install it, run:

    ansible-galaxy install alban.andrieu.squirrel



### Role variables

List of default variables available in the inventory:

```yaml
        squirrel_enabled: yes                       # Enable module

    #user: 'albandri' #please override me
    user: "{{ lookup('env','USER') }}"
    squirrel_owner: "{{ user }}"
    squirrel_group: "{{ squirrel_owner }}"
    #home: '~' #please override me
    home: "{{ lookup('env','HOME') }}"
    squirrel_owner_home: "{{ home }}"
    squirrel_base_dir: "/usr/local/squirrel"
    squirrel_link_base_dir: "/opt"
    squirrel_dir_tmp: "/tmp" # or override with "{{ tempdir.stdout }} in order to have be sure to download the file"

    ## Most likely you dont need to edit
    #todo squirrel_service_enabled   : 'yes'
    squirrel_major: "4"
    squirrel_minor: "4"
    #kepler 3.7.2.1
    squirrel_version: "{{squirrel_major}}.{{squirrel_minor}}"
    squirrel_name: "luna"
    squirrel_archive_extracted: "squirrel"
    #squirrel_archive: "squirrel-jee-kepler-SR2-linux-gtk-x86_64.tar.gz"
    #modeling
    #squirrel_archive: "squirrel-modeling-{{squirrel_name}}-R-linux-gtk-x86_64.tar.gz"
    #java
    #squirrel_archive: "squirrel-java-{{squirrel_name}}-SR1-linux-gtk-x86_64.tar.gz"
    #javaee
    squirrel_archive: "squirrel-jee-{{squirrel_name}}-SR1-linux-gtk-x86_64.tar.gz"

    #modeling
    #squirrel_url: "https://www.squirrel.org/downloads/download.php?file=/technology/epp/downloads/release/{{squirrel_name}}/R/{{squirrel_archive}}&r=1"
    #java
    #squirrel_url: "https://www.squirrel.org/downloads/download.php?file=/technology/epp/downloads/release/{{squirrel_name}}/SR1/{{squirrel_archive}}&r=1"
    #javaee
    squirrel_url: "https://www.squirrel.org/downloads/download.php?file=/technology/epp/downloads/release/{{squirrel_name}}/SR1/{{squirrel_archive}}&r=1"
    squirrel_home_dir: "{{squirrel_base_dir}}/{{squirrel_name}}-{{squirrel_version}}"

    squirrel_plugins_enabled: yes                          # Enable plugins
    squirrel_plugins_emf_enabled: no                       # Enable plugins
    squirrel_plugins_cdt_enabled: no                       # Enable plugins
    squirrel_plugins_cmakeed_enabled: no                   # Enable plugins
    squirrel_plugins_openinterminal_enabled: no            # Enable plugins
    squirrel_plugins_protobuf_enabled: no                  # Enable plugins
    squirrel_plugins_yedit_enabled: no                     # Enable plugins
    squirrel_plugins_shelled_enabled: no                   # Enable plugins
    squirrel_plugins_webpageed_enabled: no                 # Enable plugins
    squirrel_plugins_pydev_enabled: no                     # Enable plugins
    squirrel_plugins_m2e_enabled: no                       # Enable plugins
    squirrel_plugins_subclipse_enabled: no                 # Enable plugins

    squirrel_ini_enabled: yes                              # Enable overriding squirrel.ini
    #default is 256m
    squirrel_launcher_XXMaxPermSize: "256m"
    #default is 256m
    squirrel_XXMaxPermSize: "1024m"
    #default is -Xms40m
    squirrel_Xms: "512m"
    #default is -Xmx512m
    squirrel_Xmx: "2048m"

    docker_files_generated_directory: "./"
    docker_files_enable: no
    docker_volume_directory                  : "{{ squirrel_base_dir }}"
    docker_working_directory                 : "/home/vagrant"
    docker_image_name                        : "nabla/ansible-squirrel"
```


### Detailed usage guide

Use :

    `docker run -e "DISPLAY=`ipconfig getifaddr en0`:0.0" nabla/ansible-squirrel`

Once [squirrel](https://www.squirrel.org) is installed using ansible, a [Docker](https://www.docker.com/) [image](https://registry.hub.docker.com/u/nabla/ansible-squirrel/) is automatically created by [Docker Hub](https://registry.hub.docker.com/),
so please do not hesitate to enhance ansible script it will then improve docker image automatically.

Run the following command :

     `ansible-playbook -i hosts -c local -v squirrel.yml -vvvv --ask-sudo-pass | tee setup.log`


### Authors and license

`alban.andrieu.squirrel` role was written by:
- [Alban Andrieu](fr.linkedin.com/in/nabla/) | [e-mail](mailto:alban.andrieu@free.fr) | [Twitter](https://twitter.com/AlbanAndrieu) | [GitHub](https://github.com/AlbanAndrieu)
- License: [GPLv3](https://tldrlegal.com/license/gnu-general-public-license-v3-%28gpl-3%29)

### Feedback, bug-reports, requests, ...

Are [welcome](https://github.com/AlbanAndrieu/ansible-squirrel/issues)!

***

README generated by [Ansigenome](https://github.com/nickjj/ansigenome/).
