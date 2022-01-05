Initial Setup
=============

Installation
------------

The Python Onboard API client is available to install through pip:

   >>> pip install onboard.client

or by cloning our `Github repo <https://github.com/onboard-data/client-py/>`_:

.. code-block:: bash

   git clone git@github.com:onboard-data/client-py

Please note, the client requires Python >= 3.7.

Setting up API access
---------------------

You'll need an API key or existing account in order to use this client. If you don't have one and would like to start prototyping against an example building please request `a key here <https://onboarddata.io/api-keys/>`_.

Once you have a key, data access is explicitly granted by attaching one or more 'scopes' to the key. Our endpoints are grouped by scope on the `swagger documentation viewer <https://api.onboarddata.io/doc/>`_.

   >>> from onboard.client import OnboardClient
   >>> client = OnboardClient(api_key='your-api-key-here')
   >>>
   >>> # Verify access & connectivity
   >>> client.whoami()
   {'result': 'ok', 'apiKeyInHeader': True, ... 'authLevel': 4}

You can also retrieve a list of your currently authorized scopes with :code:`client.whoami()['apiKeyScopes']`.`
