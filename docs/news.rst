Release Notes
=============

.. towncrier release notes start

2.2.1 (2021-11-09)
==================

Deprecations and Removals
-------------------------
- Removed Android, BlackBerry, PhantomJS imports from selenium_driver.py as latest Selenium is not supporting this drivers

2.2.0 (2018-10-29)
==================

Deprecations and Removals
-------------------------

- Removed PhantomJS support from Splinter driver due to removal in Splinter v0.9.0. (#93)


2.1.0 (2018-08-13)
==================

Bugfixes
--------

- Replace use of ``implprefix`` with ``HookimplMarker`` due to deprecation.

  Existing PyPOM plugins will need to be updated to import the `hookimpl` and use
  it to decorate hook implementations rather than rely on the prefix of the
  function names.

  Before::

    def pypom_after_wait_for_page_to_load(page):
        pass

  After::

    from pypom import hookimpl

    @hookimpl
    def pypom_after_wait_for_page_to_load(page):
        pass (#90)


2.0.0 (2018-04-17)
==================

* Added support for plugins.

  * This introduces plugin hooks ``pypom_after_wait_for_page_to_load`` and
    ``pypom_after_wait_for_region_to_load``.
  * In order to take advantage of plugin support you must avoid implementing
    ``wait_for_page_to_load`` or ``wait_for_region_to_load`` in your page
    objects.
  * This was previously the only way to implement a custom wait for your pages
    and regions, but now means the calls to plugin hooks would be bypassed.
  * Custom waits can now be achieved by implementing a ``loaded`` property on
    the page or region, which returns ``True`` when the page or region has
    finished loading.
  * See the user guide for more details.

* Any unused ``url_kwargs`` after formatting ``URL_TEMPLATE`` are added as URL
  query string parameters.

1.3.0 (2018-02-28)
==================

* Added support for EventFiringWebDriver

  * Thanks to `@Greums <https://github.com/Greums>`_ for the PR

1.2.0 (2017-06-20)
==================

* Dropped support for Python 2.6

1.1.1 (2016-11-21)
==================

* Fixed packaging of ``pypom.interfaces``

1.1.0 (2016-11-17)
==================

* Added support for Splinter

  * Thanks to `@davidemoro <https://github.com/davidemoro>`_ for the PR

1.0.0 (2016-05-24)
==================

* Official release
