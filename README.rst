===========
Local CNAME
===========

.. image:: https://img.shields.io/pypi/l/local-cname.svg
   :target: https://github.com/Neki/local-cname/blob/master/LICENSE
   :alt: License

This is a little helper script to emulate a local CNAME DNS by writing to ``/etc/hosts``.
DNS changes (e.g. to rollout new services) can be tested by overwriting DNS names in the local ``/etc/hosts`` file.
The hosts file only supports IP addresses thus making it cumbersome to emulate a DNS ``CNAME`` without a local DNS server/proxy.
The ``local-cname`` is a very small script to automatically lookup DNS names and write IP addresses to the hosts file.
It is self-contained and restores your local ``/etc/hosts`` file on exit (press CTRL+C).

This version is a fork of https://github.com/hjacobs/local-cname with an additional patch to prevent concurrent executions
(patch was submitted upstream, but is not applied yet).

Installation:

.. code-block:: bash

    $ git clone https://github.com/Neki/local-cname
    $ cd local-cname
    $ pip install .  # might need "sudo" or use "--user"

Usage:

.. code-block:: bash

    $ sudo local-cname FROM_DNS_NAME TO_DNS_NAME
      # press CTRL+C to cancel and restore your old /etc/hosts

Example:

.. code-block:: bash

    $ sudo local-cname google.com duckduckgo.com
    $ ping google.com


