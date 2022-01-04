Querying Data Model
===================

Let's query some data from Onboard's Data Model

   >>> import pandas as pd
   >>> # Get all equipment types from the Data Model
   >>> equip_type = pd.json_normalize(client.get_equipment_types())
   >>> equip_type

This returns a d
