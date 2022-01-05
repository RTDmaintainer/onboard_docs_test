Module onboard.client
=====================

Sub-modules
-----------
* onboard.client.client
* onboard.client.dataframes
* onboard.client.exceptions
* onboard.client.helpers
* onboard.client.models
* onboard.client.util
 
Module onboard.client.client
============================

Classes
-------

`APIClient(api_url, user=None, pw=None, api_key=None, token=None, name='')`
:   Base class that implements HTTP methods against the API on top of requests

    ### Ancestors (in MRO)

    * onboard.client.helpers.ClientBase

    ### Descendants

    * onboard.client.client.DevelopmentAPIClient
    * onboard.client.client.ProductionAPIClient

    ### Methods

    `check_data_availability(self, selector: onboard.client.models.PointSelector) ‑> Tuple[Optional[datetime.datetime], Optional[datetime.datetime]]`
    :   Returns a tuple of data timestamps (most stale, most recent) for selected points

    `copy_point_data(*args, **kwargs)`
    :

    `get_account_actions(*args, **kwargs)`
    :

    `get_alerts(*args, **kwargs)`
    :

    `get_all_buildings(*args, **kwargs)`
    :

    `get_all_equipment(self) ‑> List[Dict[~KT, ~VT]]`
    :   returns all equipment instances for all visible buildings

    `get_all_measurements(*args, **kwargs)`
    :

    `get_all_point_types(*args, **kwargs)`
    :

    `get_all_points(self) ‑> List[Dict[~KT, ~VT]]`
    :   returns all points for all visible buildings

    `get_all_units(*args, **kwargs)`
    :

    `get_building_changelog(*args, **kwargs)`
    :

    `get_building_equipment(*args, **kwargs)`
    :

    `get_equipment_by_ids(*args, **kwargs)`
    :

    `get_equipment_types(*args, **kwargs)`
    :

    `get_ingest_stats(*args, **kwargs)`
    :

    `get_organizations(*args, **kwargs)`
    :

    `get_points_by_datasource(self, datasource_hashes: List[str]) ‑> List[Dict[str, str]]`
    :

    `get_points_by_ids(self, point_ids: List[int]) ‑> List[Dict[str, str]]`
    :

    `get_tags(*args, **kwargs)`
    :

    `get_users(*args, **kwargs)`
    :

    `query_point_timeseries(*args, **kwargs)`
    :   .. deprecated:: 1.3.0 Use stream_point_timeseries instead

    `select_points(*args, **kwargs)`
    :

    `send_ingest_stats(*args, **kwargs)`
    :

    `stream_point_timeseries(self, query: onboard.client.models.TimeseriesQuery) ‑> Iterator[onboard.client.models.PointData]`
    :   Query a time interval for an explicit set of point ids or
        with a selector which describes which sensors to include.
        
        Example values docmentaed on the model tab here:
            https://api.onboarddata.io/doc/#/buildings%3Aread/post_query_v2

    `update_point_data(*args, **kwargs)`
    :

    `whoami(*args, **kwargs)`
    :

`DevelopmentAPIClient(user=None, pw=None, api_key=None, token=None)`
:   Base class that implements HTTP methods against the API on top of requests

    ### Ancestors (in MRO)

    * onboard.client.client.APIClient
    * onboard.client.helpers.ClientBase

`ProductionAPIClient(user: Optional[str] = None, pw: Optional[str] = None, api_key: Optional[str] = None, token: Optional[str] = None)`
:   Base class that implements HTTP methods against the API on top of requests

    ### Ancestors (in MRO)

    * onboard.client.client.APIClient
    * onboard.client.helpers.ClientBase
 
Module onboard.client.dataframes
================================

Functions
---------

    
`df_objs_to_numeric(df: pandas.core.frame.DataFrame)`
:   

    
`df_time_index(df: pandas.core.frame.DataFrame, time_col='timestamp', utc=True) ‑> pandas.core.frame.DataFrame`
:   

    
`points_df_from_streaming_timeseries(timeseries: Iterable[onboard.client.models.PointData], points=[], point_column_label=None) ‑> pandas.core.frame.DataFrame`
:   Returns a pandas dataframe from the results of a timeseries query

    
`points_df_from_timeseries(timeseries, points=[]) ‑> pandas.core.frame.DataFrame`
:   Returns a pandas dataframe from the results of a timeseries query
 
Module onboard.client.exceptions
================================

Classes
-------

`OnboardApiException(*args, **kwargs)`
:   Wrapper for exceptions throw by the API client

    ### Ancestors (in MRO)

    * builtins.Exception
    * builtins.BaseException

    ### Descendants

    * onboard.client.exceptions.OnboardTemporaryException

`OnboardTemporaryException(*args, **kwargs)`
:   These exceptions indicate that a call failed in a temporary manner
    and should be retried

    ### Ancestors (in MRO)

    * onboard.client.exceptions.OnboardApiException
    * builtins.Exception
    * builtins.BaseException
 
Module onboard.client.helpers
=============================

Classes
-------

`ClientBase(api_url: Optional[str], user: Optional[str], pw: Optional[str], api_key: Optional[str], token: Optional[str], name: [typing.Union[str, NoneType]])`
:   Base class that implements HTTP methods against the API on top of requests

    ### Descendants

    * onboard.client.client.APIClient

    ### Methods

    `auth(self)`
    :

    `delete(self, url: str, **kwargs) ‑> requests.models.Response`
    :

    `dt_to_str(self, dt: Union[str, datetime.datetime]) ‑> str`
    :

    `get(self, url: str, **kwargs) ‑> requests.models.Response`
    :

    `headers(self)`
    :

    `post(self, url: str, **kwargs) ‑> requests.models.Response`
    :

    `put(self, url: str, **kwargs) ‑> requests.models.Response`
    :

    `ts_to_dt(self, ts: Optional[float]) ‑> datetime.datetime`
    :

    `url(self, url: str) ‑> str`
    :
 
Module onboard.client.models
============================

Classes
-------

`IngestStats()`
:   

    ### Methods

    `add_points(self, points)`
    :

    `elapsed(self, elapsed)`
    :

    `json(self)`
    :

    `summary(self, info)`
    :

`PointData(point_id: int, raw: str, unit: str, columns: List[str], values: List[List[Union[str, float, int, None]]])`
:   PointData(point_id: int, raw: str, unit: str, columns: List[str], values: List[List[Union[str, float, int, NoneType]]])

    ### Class variables

    `columns: List[str]`
    :

    `point_id: int`
    :

    `raw: str`
    :

    `unit: str`
    :

    `values: List[List[Union[str, float, int, None]]]`
    :

`PointDataUpdate(point_id, value, last_updated)`
:   Model for bulk-updating a point's data value and timestamp

    ### Instance variables

    `last_updated`
    :   Return an attribute of instance, which is of type owner.

    `point_id`
    :   Return an attribute of instance, which is of type owner.

    `value`
    :   Return an attribute of instance, which is of type owner.

    ### Methods

    `json(self)`
    :

`PointSelector(orgs: List[Union[int, str]] = <factory>, buildings: List[Union[int, str]] = <factory>, point_ids: List[int] = <factory>, point_names: List[str] = <factory>, point_hashes: List[str] = <factory>, point_topics: List[str] = <factory>, updated_since: Optional[datetime.datetime] = None, point_types: List[Union[int, str]] = <factory>, equipment: List[Union[int, str]] = <factory>, equipment_types: List[Union[int, str]] = <factory>)`
:   A flexible interface to allow users to select sets of points

    ### Class variables

    `buildings: List[Union[int, str]]`
    :

    `equipment: List[Union[int, str]]`
    :

    `equipment_types: List[Union[int, str]]`
    :

    `orgs: List[Union[int, str]]`
    :

    `point_hashes: List[str]`
    :

    `point_ids: List[int]`
    :

    `point_names: List[str]`
    :

    `point_topics: List[str]`
    :

    `point_types: List[Union[int, str]]`
    :

    `updated_since: Optional[datetime.datetime]`
    :

    ### Static methods

    `from_json(dict)`
    :

    ### Methods

    `json(self)`
    :

`TimeseriesQuery(start: datetime.datetime, end: datetime.datetime, selector: Optional[onboard.client.models.PointSelector] = None, point_ids: List[int] = <factory>, units: List[str] = <factory>)`
:   Parameters needed to fetch timeseries data.
    
    Exactly one of point_ids or selector is required
    
    Note: the server may perform additional validation and reject queries
    which are constructable by the client
    
    For example values please refer to
        https://api.onboarddata.io/doc/#/buildings%3Aread/post_query_v2

    ### Class variables

    `end: datetime.datetime`
    :

    `point_ids: List[int]`
    :

    `selector: Optional[onboard.client.models.PointSelector]`
    :

    `start: datetime.datetime`
    :

    `units: List[str]`
    :

    ### Static methods

    `points_or_selector_required(point_ids, values)`
    :

    `times_valid(value, values)`
    :

    ### Methods

    `json(self)`
    :
 
Module onboard.client.util
==========================

Functions
---------

    
`divide_chunks(input_list: List[~T], n: int) ‑> Iterable[List[~T]]`
:   

    
`json(func)`
:   Decorator for making sure requests responses are handled consistently
