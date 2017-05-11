National Biodiversity Strategies and Action Plan
================================================

.. contents ::


Project name and whereabouts
----------------------------
The project name is National Biodiversity Strategies and Action Plan (or simply NBSAP).
It is a platform for organizing the implementation of a country's
national biodiversity strategy after AICHI (and by case after EU Strategy).
It consists of two panels each corresponding an operation: viewing and editing.
The first panel allows anyone to overview the aichi goals, targets and
indicators along with national strategy mappings (the way a country develops its
own strategy in terms of objectives and actions) and its implementation.
The second panel(Admin), authentication-available only, allows an user to actually define
the national strategy. (e.g. add/modify/delete an objective, action or even
elements from AICHI) in the purpose of building it.


Installation
------------

* Install `Docker <https://docker.com>`_
* Install `Docker Compose <https://docs.docker.com/compose>`_

Usage
-----

1. Clone the repository::

    $ git https://github.com/eaudeweb/nbsap.docker.git
    $ cd nbsap.docker
   
2. Start application stack::

    $ docker-compose up -d
    $ docker-compose logs

3. See it in action::

    http://0.0.0.0:$INSTANCE_PORT

Where ``$INSTANCE_PORT`` is one of the following:
  * *Benin* - 8002
  * *Burundi* - 8004
  * *Maroc* - 8010
  * *Niger* - 8011
  * *Training* - 8013


Upgrade
-------

1. Get the latest source code::

    $ cd nbsap.docker
    $ git pull

2. Get the latest docker images::

    $ docker-compose pull

3. Restart application stack::

    $ docker-compose up -d

4. Check that everything is up-and-running::

   $ docker-compose ps

5. See the logs::

   $ docker-compose logs


Contacts
========

People involved in this project are:

* Cornel Nitu (cornel.nitu at eaudeweb.ro)
* Iulia Chiriac (iulia.chiriac at eaudeweb.ro)
* Gabriela Strezea (gabriela.strezea at eaudeweb.ro)
