Docker orchestration for NBSAP
==============================

.. contents ::


Prerequisites
-------------

* Install `Docker <https://docker.com>`_
* Install `Docker Compose <https://docs.docker.com/compose>`_
* Install `Apache <https://www.digitalocean.com/community/tutorials/how-to-install-linux-apache-mysql-php-lamp-stack-on-centos-6#step-one—install-apache>`_

Usage in production
-------------------

1. Clone the repository::

    $ git https://github.com/eaudeweb/nbsap.docker.git
    $ cd nbsap.docker
   
2. Start application stack::

    $ docker-compose up -d

3. Verify that all containers are up (check ``State`` column)::

    $ docker-compose ps

4. Wait until the migrations are done. You can see the migrations status using::

    $ docker logs -f nbsapdocker_$INSTANCE_NAME_1

5. After the migrations are done, you can see your instance in action at::

    http://localhost:$INSTANCE_PORT


Where ``$INSTANCE_PORT`` is one of the following:

* 8002 for Benin
* 8004 for Burundi
* 8010 for Maroc
* 8011 for Niger
* 8013 for Training

6. Restore a mysql database::

    $ cat backup.sql | docker exec -i nbsapdocker_mysql_1 /usr/bin/mysql -u root --password=$PASSWORD DATABASE

You should replace ``$PASSWORD`` with the password set in ``mysql.env``, ``DATABASE`` with the ``DATABASES_NAME`` set in the instance coresponding env file and ``backup.sql`` with the name of the .sql file containing your data dump.

7. Setup virtual host file::

    $ cp conf-files/nbsap.conf /etc/httpd/conf.d/nbsap.conf
    $ service httpd reload

8. If you need to run in debug mode, add the following lines in ``docker-compose.yml``, in the corresponding service::

    environment:
      DEBUG: 'True'

    # restart the container
    $ docker-compose restart INSTANCE_NAME

9. If something does not work as you expect, check the logs::

    $ docker logs -f nbsapdocker_$INSTANCE_NAME_1

You can open a new issue `here <https://github.com/eaudeweb/nbsap.docker/issues>`_. You should put in the new issue the errors and the logs.


For development follow these `steps <https://github.com/eea/eea.docker.tct/tree/master#run-in-devel-with-docker-compose>`_.

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


Contacts
========

People involved in this project are:

* Cornel Nitu (cornel.nitu at eaudeweb.ro)
* Iulia Chiriac (iulia.chiriac at eaudeweb.ro)
* Gabriela Strezea (gabriela.strezea at eaudeweb.ro)


Copyright and license
=====================

Copyright 2007 European Environment Agency (EEA)

Licensed under the EUPL, Version 1.1 or – as soon they will be approved
by the European Commission - subsequent versions of the EUPL (the "Licence");

You may not use this work except in compliance with the Licence.

You may obtain a copy of the Licence at:
https://joinup.ec.europa.eu/software/page/eupl/licence-eupl

Unless required by applicable law or agreed to in writing, software distributed under the Licence is distributed on an "AS IS" basis,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.

See the Licence for the specific language governing permissions and limitations under the Licence.
