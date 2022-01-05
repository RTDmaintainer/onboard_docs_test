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
