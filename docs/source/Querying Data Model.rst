Querying Data Model
===================

Onboard's data model contains both equipment types (e.g. fans, air handling units) and point types (e.g. zone temperature). We can query the full data model within our API.

Equipment types
---------------

First, we make an API call with client.get_equipment_types(). This returns a JSON object, which we will convert to a dataframe using Pandas:

   >>> from onboard.client import OnboardClient
   >>> client = OnboardClient(api_key='')
   >>> import pandas as pd
   >>> # Get all equipment types from the Data Model
   >>> equip_type = pd.json_normalize(client.get_equipment_types())
   >>> equip_type.columns
   ['id', 'tag_name', 'name_long', 'name_abbr', 'active', 'flow_order',
   'critical_point_types', 'sub_types', 'tags']

equip_type now contains a dataframe listing all equipment types in our data model, along with associated attributes (e.g. tags, full names, associated point types, and sub-equipment types).

The sub-equipment types are nested as dataframes within each row, and can be listed for an equipment type (e.g. 'fan') like so:

   >>> sub_type = pd.DataFrame(equip_type[equip_type.tag_name == 'fan']['sub_types'].item())
      id  equipment_type_id         tag_name          name_long name_abbr
   0  12                 26       exhaustFan        Exhaust Fan       EFN
   1  13                 26        reliefFan         Relief Fan      RlFN
   2  14                 26        returnFan         Return Fan       RFN
   3  15                 26        supplyFan         Supply Fan       SFN
   ...

Note that not all equipment types have associated sub types.

Point types
-----------

Accessing point types is very similar, and can be accessed through client.get_all_point_types():

   >>> # Get all point types from the Data Model
   >>> point_type = pd.DataFrame(client.get_all_point_types())

point_type now contains a dataframe listing all the tags associated with each point type.

We can extract the metadata associated with each tag in our data model like so:

   >>> # Get all tags and their definitions from the Data Model
   >>> pd.DataFrame(client.get_tags())
         id        name                                         definition def_source                                            def_url
   0    120     battery  A container that stores chemical energy that c...      brick  https://brickschema.org/ontology/1.1/classes/B...
   1    191  exhaustVAV  A device that regulates the volume of air bein...    onboard                                               None
   2    193         oil  A viscous liquid derived from petroleum, espec...      brick  https://brickschema.org/ontology/1.2/classes/Oil/
   3    114    fumeHood  A fume-collection device mounted over a work s...      brick  https://brickschema.org/ontology/1.1/classes/F...
   ...

This returns a dataframe containing definitions for all tags in our data model, with attribution where applicable.
