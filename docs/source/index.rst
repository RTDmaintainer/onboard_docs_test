Onboard Data Python API documentation
=====================================

.. image:: https://readthedocs.org/projects/onboard-docs-test/badge/?version=latest
    :target: https://onboard-docs-test.readthedocs.io/en/latest/?badge=latest

.. image:: https://badge.fury.io/py/onboard.client.svg
    :target: https://badge.fury.io/py/onboard.client

.. image:: https://shields.io/pypi/pyversions/onboard.client.svg
    :target: https://pypi.org/project/onboard.client/

.. image:: https://camo.githubusercontent.com/3656aeb94541a2464bac21509c34b7942cf127702885cd6ce0002120d2bfa189/68747470733a2f2f696d672e736869656c64732e696f2f707970692f6c2f6f6e626f6172642e636c69656e74
    :target: https://camo.githubusercontent.com/3656aeb94541a2464bac21509c34b7942cf127702885cd6ce0002120d2bfa189/68747470733a2f2f696d672e736869656c64732e696f2f707970692f6c2f6f6e626f6172642e636c69656e74

This package provides Python bindings to `Onboard Data's <https://onboarddata.io/>`_ building data API, allowing easy and lightweight access to building data.

For example, we can retrieve the last week of temperature data from all Zone Temperature points associated with FCUs in the Laboratory building:

.. code-block:: python

    import pandas as pd
    import onboard.client
    from datetime import datetime, timezone, timedelta
    from onboard.client.models import PointSelector, TimeseriesQuery, PointData
    from typing import List
    client = OnboardClient(api_key='your-api-key-here')

    query = PointSelector()
    query.point_types     = ['Zone Temperature'] # can list multiple
    query.equipment_types = ['fcu']
    query.buildings       = ['Laboratory']
    selection = client.select_points(query)

    start = datetime.now(pytz.utc) - timedelta(days=7)
    end   = datetime.now(pytz.utc)

    timeseries_query = TimeseriesQuery(point_ids = selection['points'], start = start, end = end)
    sensor_data = points_df_from_streaming_timeseries(client.stream_point_timeseries(timeseries_query))

For installation instructions, and to get set up with API access, refer to :ref:`Initial Setup`_.

.. note::

   While we are committed to backwards-compatibility, this project is under active development. If you discover a feature that would be helpful, or any unexpected behavior, please contact us at xxx@onboarddata.io

Contents
--------

.. toctree::

   Initial Setup
   Querying Data Model
   Querying Building-Specific Data

License
-------

Copyright 2018-2022 Onboard Data Inc

Licensed under the Apache License, Version 2.0 (the "License"); you may not use this file except in compliance with the License. You may obtain a copy of the License at

 http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software distributed under the License is distributed on an "AS IS" BASIS, WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied. See the License for the specific language governing permissions and limitations under the License.
