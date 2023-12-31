
.. _porting_2.14_guide_core:

*******************************
Ansible-core 2.14 Porting Guide
*******************************

This section discusses the behavioral changes between ``ansible-core`` 2.13 and ``ansible-core`` 2.14.

It is intended to assist in updating your playbooks, plugins and other parts of your Ansible infrastructure so they will work with this version of Ansible.

We suggest you read this page along with `ansible-core Changelog for 2.14 <https://github.com/ansible/ansible/blob/stable-2.14/changelogs/CHANGELOG-v2.14.rst>`_ to understand what updates you may need to make.

This document is part of a collection on porting. The complete list of porting guides can be found at :ref:`porting guides <porting_guides>`.

.. contents:: Topics


Playbook
========

* Variables are now evaluated lazily; only when they are actually used. For example, in ansible-core 2.14 an expression ``{{ defined_variable or undefined_variable }}`` does not fail on ``undefined_variable`` if the first part of ``or`` is evaluated to ``True`` as it is not needed to evaluate the second part. One particular case of a change in behavior to note is the task below which uses the ``undefined`` test. Prior to version 2.14 this would result in a fatal error trying to access the undefined value in the dictionary. In 2.14 the assertion passes as the dictionary is evaluated as undefined through one of its undefined values:

 .. code-block:: yaml

     - assert:
         that:
           - some_defined_dict_with_undefined_values is undefined
       vars:
         dict_value: 1
         some_defined_dict_with_undefined_values:
           key1: value1
           key2: '{{ dict_value }}'
           key3: '{{ undefined_dict_value }}'


Command Line
============

No notable changes


Deprecated
==========

No notable changes


Modules
=======

No notable changes


Modules removed
---------------

The following modules no longer exist:

* No notable changes


Deprecation notices
-------------------

No notable changes


Noteworthy module changes
-------------------------

No notable changes


Plugins
=======

No notable changes


Porting custom scripts
======================

No notable changes


Networking
==========

No notable changes
