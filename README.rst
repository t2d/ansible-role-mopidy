ansible-role-mopidy
===================

.. image:: http://img.shields.io/badge/ansible--galaxy-mopidy-blue.svg
  :target: https://galaxy.ansible.com/t2d/mopidy/

.. image:: https://travis-ci.org/t2d/ansible-role-mopidy.svg?branch=master
    :target: https://travis-ci.org/t2d/ansible-role-mopidy

Ansible role that installs Mopidy_ on Ubuntu/Debian. Thanks to
Daniel White for the inspiration :)

.. _mopidy: https://www.mopidy.com/

Role Variables
--------------

Available variables are listed below, along with default values (see `defaults/main.yml`)

A list of package manager extensions::

    mopidy_packages:
      - mopidy-spotify

A list of pip extensions::

    mopidy_pip:
      - mopidy-pandora

A list of additional options to configure. Each item requires the `section`, `option` and `value` properties
to be defined. These are used by the ini_file_ module to configure `/etc/mopidy/mopidy.conf`::

    mopidy_settings:
      - { section: 'spotify', option: 'username', value: '{{ spotify_username }}' }
      - { section: 'spotify', option: 'password', value: '{{ spotify_password }}' }
      - { section: 'pandora', option: 'username', value: '{{ pandora_username }}' }
      - { section: 'pandora', option: 'password', value: '{{ pandora_password }}' }
      ... <snip, please see defaults/main.yml file :)

.. _ini_file: http://docs.ansible.com/ansible/ini_file_module.html

Example
-------

playbook.yml::

    - hosts: mopidy-hosts
      roles:
        - { role: t2d.mopidy, tags: mopidy, mopidy-packages: ["mopidy-local-sqlite",] }

Testing
-------

A vagrant file has been included for easy testing. To get a running mopidy::

    vagrant up

License
-------

Please see included LICENSE file for license specifics

Copyright 2017 Jon Robison
