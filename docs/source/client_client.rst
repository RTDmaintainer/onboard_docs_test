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
