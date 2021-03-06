.. MyTARDIS documentation master file, created by sphinx-quickstart on
   Fri Jul 3 10:23:35 2009. You can adapt this file completely to your
   liking, but it should at least contain the root `toctree`
   directive.

========
MyTARDIS
========

MyTARDIS is a multi-institutional collaborative venture that
facilitates the archiving and sharing of data and metadata collected
at major facilities such as the Australian Synchrotron and ANSTO and
within Institutions.

An example of the benefit of a system such a MyTARDIS in the protein
crystallography community is that while the model coordinates and
(less often) the structure factors (processed experimental data) are
stored in the community Protein Data Bank (PDB) the raw diffraction
data is often not available. There are several reasons why this is
important, which can be summarised as:

 * The availability of raw data is extremely useful for the
   development of improved methods of image analysis and data
   processing.
 * Fostering the archival of raw data at an institutional level is one
   the best ways of ensuring that this data is not lost (laboratory
   archives are typically volatile).

Homepage
--------

You can get a copy of MyTARDIS from http://code.google.com/p/mytardis/

===========
Quick Start
===========

Prerequisites
-------------

Redhat::

   sudo yum install cyrus-sasl-ldap cyrus-sasl-devel openldap-devel libxslt libxslt-devel libxslt-python

Debian/Ubuntu::

   sudo apt-get install libsasl2-dev libldap libldap2-dev libxslt1.1 libxslt1-dev python-libxslt1

Download
--------

To get the current trunk::

   svn co https://mytardis.googlecode.com/svn/trunk/ mytardis
   cd mytardis

Building
--------

MyTARDIS is using the buildout buildsystem to handle dependencies and create the python class path::

   python bootstrap.py
   ./bin/buildout

MyTARDIS can now be executed in it's simplist form using::

   ./bin/django runserver

This will execute django using the builtin SQLite DBMS and only be accessable on *localhost*.



Prerequisites
-------------

- Linux or similar server
- Python 2.6

Installation
------------

Unpack the distribution or pull from the git repository

Configuration
-------------

This page describes how to install MaVRec as a local server, using SQLite3 as
a backend with initial data.

Install dependencies (from Ubuntu, use Yum for RedHat etc.)::

    sudo apt-get install build-essential python-dev
    sudo apt-get install subversion

Bootstrap build environment::
    
    cd smra
    python2.6 boostrap.py
    
Get required system python dependencies (internet required)::

    bin/buildout
    
Run testcases to verify success::

    bin/django test 

Copy prototypical settings file for local version::

    cp smra/settings_changeme.py smra/settings.py

If required, modify standard Django ``smra/settings.py`` file to change database etc.
Documentation in ``settings_changeme.py``

The configure MaVRec for interactive use, modify the file ``bin/django`` and replace::

    djangorecipe.manage.main('smra.test_settings')
    
with::
    
    djangorecipe.manage.main('smra.settings')
    
Setup database and initial data and create an admin user::

    bin/django syncdb --migrate
    
Start the development server::

    bin/django runserver
    

System should now be running at http://127.0.0.1:8000

========
Contents
========

.. toctree::
   :maxdepth: 2

   install
   admin
   overview
   schemaparamsets
   ingesting

   ref/auth_framework
   ref/filters

   architecture
   data

   changes
   contributing


==================
Indices and tables
==================

* :ref:`genindex`
* :ref:`modindex`
* :ref:`search`

