.. _errata:

===============================
 Percona XtraDB Cluster Errata 
===============================

Known Issues
-------------

Following are issues which may impact you while running PXC:
 - Create Table As Select (CTAS) under highly concurent DDL workload (other than CTAS) may deadlock.
 - For fresh installs, it is highly recommended to use the meta-packages to install packages. Refer to  :ref:`installation` guide for more details.

Also make sure to check limitations page :ref:`here <limitations>`. You can also review this `milestone <https://launchpad.net/percona-xtradb-cluster/+milestone/future-5.5>`_ for features/bugfixes to be included in future releases (i.e. releases after the upcoming/recent release).

Incompatibilities
-------------------

Following are incompatibilities between PXC 5.5.33 (and higher) and older versions:
 - wsrep_sst_donor now supports comma separated list of nodes as a consequence of bug :bug:`1129512`. This only affects if you use this option as a list. This is not compatible with nodes running older PXC, hence **entire** cluster will be affected as far as SST is concerned, since donor nodes won't recognise the request from joiner nodes if former are not upgraded. Minimal workaround is to upgrade Galera package or to not use this new feature (wsrep_sst_donor with single node can still be used). However, upgrading the full PXC is strongly recommended, however, just upgrading PXC galera package will do for this.
