Elasticsearch
=========

Install Elasticsearch for Servers for Hackers

Requirements
------------

Python makes URL calls, and requires the installation of `PIP` and `httplib2`. This is done within the tasks `main.yml` file.

Role Variables
--------------

* **cluster**: sfhsearch
* **node**: sfhnode
* **num_replicas**: 1
* **num_shards**: 5
* **index_name**: serversforhackers

> This currently assumes a cluster of 1 node.

License
-------

MIT