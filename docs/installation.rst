..  Licensed to the Apache Software Foundation (ASF) under one
    or more contributor license agreements.  See the NOTICE file
    distributed with this work for additional information
    regarding copyright ownership.  The ASF licenses this file
    to you under the Apache License, Version 2.0 (the
    "License"); you may not use this file except in compliance
    with the License.  You may obtain a copy of the License at

..    http://www.apache.org/licenses/LICENSE-2.0

..  Unless required by applicable law or agreed to in writing,
    software distributed under the License is distributed on an
    "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY
    KIND, either express or implied.  See the License for the
    specific language governing permissions and limitations
    under the License.

Installation
------------

Getting Airflow
'''''''''''''''

The easiest way to install the latest stable version of Airflow is with ``pip``:

.. code-block:: bash

    pip install apache-airflow

You can also install Airflow with support for extra features like ``gcp`` or ``postgres``:

.. code-block:: bash

    pip install 'apache-airflow[postgres,gcp]'

Extra Packages
''''''''''''''

The ``apache-airflow`` PyPI basic package only installs what's needed to get started.
Subpackages can be installed depending on what will be useful in your
environment. For instance, if you don't need connectivity with Postgres,
you won't have to go through the trouble of installing the ``postgres-devel``
yum package, or whatever equivalent applies on the distribution you are using.

Behind the scenes, Airflow does conditional imports of operators that require
these extra dependencies.

Here's the list of the subpackages and what they enable:

+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| subpackage          | install command                                     | enables                                                              |
+=====================+=====================================================+======================================================================+
| all                 | ``pip install 'apache-airflow[all]'``               | All Airflow features known to man                                    |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| all_dbs             | ``pip install 'apache-airflow[all_dbs]'``           | All databases integrations                                           |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| async               | ``pip install 'apache-airflow[async]'``             | Async worker classes for Gunicorn                                    |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| azure               | ``pip install 'apache-airflow[azure]'``             | Microsoft Azure                                                      |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| aws                 | ``pip install 'apache-airflow[aws]'``               | Amazon Web Services                                                  |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| celery              | ``pip install 'apache-airflow[celery]'``            | CeleryExecutor                                                       |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| cloudant            | ``pip install 'apache-airflow[cloudant]'``          | Cloudant hook                                                        |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| crypto              | ``pip install 'apache-airflow[crypto]'``            | Encrypt connection passwords in metadata db                          |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| devel               | ``pip install 'apache-airflow[devel]'``             | Minimum dev tools requirements                                       |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| devel_hadoop        | ``pip install 'apache-airflow[devel_hadoop]'``      | Airflow + dependencies on the Hadoop stack                           |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| druid               | ``pip install 'apache-airflow[druid]'``             | Druid related operators & hooks                                      |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| gcp                 | ``pip install 'apache-airflow[gcp]'``               | Google Cloud Platform                                                |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| github_enterprise   | ``pip install 'apache-airflow[github_enterprise]'`` | GitHub Enterprise auth backend                                       |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| google_auth         | ``pip install 'apache-airflow[google_auth]'``       | Google auth backend                                                  |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| hdfs                | ``pip install 'apache-airflow[hdfs]'``              | HDFS hooks and operators                                             |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| hive                | ``pip install 'apache-airflow[hive]'``              | All Hive related operators                                           |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| jdbc                | ``pip install 'apache-airflow[jdbc]'``              | JDBC hooks and operators                                             |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| kerberos            | ``pip install 'apache-airflow[kerberos]'``          | Kerberos integration for Kerberized Hadoop                           |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| kubernetes          | ``pip install 'apache-airflow[kubernetes]'``        | Kubernetes Executor and operator                                     |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| ldap                | ``pip install 'apache-airflow[ldap]'``              | LDAP authentication for users                                        |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| mssql               | ``pip install 'apache-airflow[mssql]'``             | Microsoft SQL Server operators and hook,                             |
|                     |                                                     | support as an Airflow backend                                        |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| mysql               | ``pip install 'apache-airflow[mysql]'``             | MySQL operators and hook, support as an Airflow                      |
|                     |                                                     | backend. The version of MySQL server has to be                       |
|                     |                                                     | 5.6.4+. The exact version upper bound depends                        |
|                     |                                                     | on version of ``mysqlclient`` package. For                           |
|                     |                                                     | example, ``mysqlclient`` 1.3.12 can only be                          |
|                     |                                                     | used with MySQL server 5.6.4 through 5.7.                            |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| password            | ``pip install 'apache-airflow[password]'``          | Password authentication for users                                    |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| postgres            | ``pip install 'apache-airflow[postgres]'``          | PostgreSQL operators and hook, support as an                         |
|                     |                                                     | Airflow backend                                                      |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| qds                 | ``pip install 'apache-airflow[qds]'``               | Enable QDS (Qubole Data Service) support                             |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| rabbitmq            | ``pip install 'apache-airflow[rabbitmq]'``          | RabbitMQ support as a Celery backend                                 |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| redis               | ``pip install 'apache-airflow[redis]'``             | Redis hooks and sensors                                              |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| samba               | ``pip install 'apache-airflow[samba]'``             | :class:`airflow.operators.hive_to_samba_operator.Hive2SambaOperator` |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| slack               | ``pip install 'apache-airflow[slack]'``             | :class:`airflow.operators.slack_operator.SlackAPIOperator`           |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| ssh                 | ``pip install 'apache-airflow[ssh]'``               | SSH hooks and Operator                                               |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+
| vertica             | ``pip install 'apache-airflow[vertica]'``           | Vertica hook support as an Airflow backend                           |
+---------------------+-----------------------------------------------------+----------------------------------------------------------------------+

Initiating Airflow Database
'''''''''''''''''''''''''''

Airflow requires a database to be initiated before you can run tasks. If
you're just experimenting and learning Airflow, you can stick with the
default SQLite option. If you don't want to use SQLite, then take a look at
:doc:`howto/initialize-database` to setup a different database.

After configuration, you'll need to initialize the database before you can
run tasks:

.. code-block:: bash

    airflow initdb
