Introduction
============

`django_statsd` is a middleware that uses `dogstatsd-python` to log query
and view durations to statsd.

* Source
    - https://github.com/ckald/django-statsd-1
* Bug reports 
    - https://github.com/ckald/django-statsd-1/issues
* Python Statsd
    - https://github.com/DataDog/dogstatsd-python
* Statsd 
    - code: https://github.com/etsy/statsd
    - blog post: http://codeascraft.etsy.com/2011/02/15/measure-anything-measure-everything/


Install
=======

To install simply execute `python setup.py install`.
If you want to run the tests first, run `python setup.py test`


Usage
=====

To install, add the following to your ``settings.py``:

1. ``django_statsd`` to the ``INSTALLED_APPS`` setting.
2. ``django_statsd.middleware.StatsdMiddleware`` to the **top** of your 
    ``MIDDLEWARE_CLASSES``
3. ``django_statsd.middleware.StatsdMiddlewareTimer`` to the **bottom** of your 
    ``MIDDLEWARE_CLASSES``
4. Add configuration parameters: ``STATSD_TRACK_MIDDLEWARE = True``, ``STATSD_PREFIX = "server.prefix.or.else"``

Advanced Usage
--------------

    >>> def some_view(request):
    ...     with request.timings('something_to_time'):
    ...         # do something here
    ...         pass
    >>>    
    >>> def some_view(request):
    ...     request.timings.start('something_to_time')
    ...     # do something here
    ...     request.timings.stop('something_to_time')

