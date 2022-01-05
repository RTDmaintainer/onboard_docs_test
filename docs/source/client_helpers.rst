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
