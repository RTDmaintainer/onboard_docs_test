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
