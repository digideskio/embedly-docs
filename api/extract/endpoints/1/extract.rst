Extract API
===========

The Extract endpoint is designed to provide users with important
information from each link. This endpoint includes the article text,
keywords, related links, and even video embeds.

Example call (1 URL)::

    http://api.embed.ly/1/extract?key=:key&url=:url&maxwidth=:maxwidth&maxheight=:maxheight&format=:format&callback=:callback

Example call (multiple URLs)::

    http://api.embed.ly/1/extract?key=:key&urls=:url1,:url2,:url3&maxwidth=:maxwidth&maxheight=:maxheight&format=:format&callback=:callback

Examples
--------
`Embedly Explore </docs/explore/extract>`_ can be used to get a better handle
on what this API returns. Try these:

* `Techcrunch Article </docs/explore/extract?url=http://techcrunch.com/2010/11/18/mark-zuckerberg/>`_
* `Deadspin Post </docs/explore/extract?url=http://deadspin.com/5690535/the-bottom-100-the-worst-players-in-nfl-history-part-1>`_
* `Embedly blog </docs/explore/extract?url=http://blog.embed.ly/31814817>`_

Arguments
----------------
See the :doc:`Query Arguments <../../arguments>` documentation.

Response
--------

Example response
^^^^^^^^^^^^^^^^

.. code-block:: json

  {
    "provider_url": "http://blog.embed.ly",
    "lead": null,
    "language": "English",
    "original_url": "http://blog.embed.ly/javascript-hackathon-downcityjs-betaspring",
    "url": "http://blog.embed.ly/javascript-hackathon-downcityjs-betaspring",

    "entities": [
    {"count": 4, "name": "Aaron"},
    {"count": 1, "name": "Vinh"},
    {"count": 1, "name": "Reddit"},
    {"count": 1, "name": "Kyle Nichols"},
    {"count": 1, "name": "Kawan"}],

    "safe": true,
    "provider_display": "blog.embed.ly",
    "related": [],

    "keywords": [
    {"score": 31, "name": "api"},
    {"score": 28, "name": "embed"},
    {"score": 21, "name": "aaron"},
    {"score": 14, "name": "best"},
    {"score": 10, "name": "thumbwar"},
    {"score": 10,"name": "friends"}],

    "title": "DowncityJS Hackathon Recap - Embedly",
    "description": "We provided our API for the event and some prizes for
    best use of our API as a solo participant.......",

    "content": "<div>\n<strong>We provided our API for the event and some prizes
    for best use of our API as a solo participant and as a group, we were pleased
    with the outcome! </strong> <p><strong>Best use of our API:  </strong>
    <strong>Cheer Me \u00dcp, a service which allows you to send a friendly
    and uplifting message to someone having a tough time. They'll receive it with
    cat gifs and all, embedded from sites like Tumblr and Reddit using the
    Embedly API. </strong></p>\n<strong>Best Solo: Thom Nichols for
    <a href=\"https://github.com/tomstrummer\">Xirq.us </a>, they used Embedly
    to embed photos and media.....
    We're looking forward to seeing the real thing and will
    definitely be sending some pleasant messages to some
    unsuspecting mopes.
    <img src=\"https://lh3.googleusercontent.com/MaaMmP0N4psfPqQOUqegiz3q-
    SxnRd3sFn-XNKy92XLXo-R6dZIcFv7PkvgleeCqynGsUj4s9GUTnL__W77OpjmaTcBgis98nh
    udlkwsZp7-CNCqihX1zalDbQ\"></strong> <p> </p>\n</div>",
    "favicon_url": "http://blog.embed.ly/images/favicon.png",
    "authors": [{"url": "http://posterous.com/users/iHySgjJhRuY0q",
    "name": "Nina Stepanov"}],

    "media": {},

    "offset": null,
    "published": 1360022400000,

    "images": [ {
    "caption":null,
    "url":"https://lh3.googleusercontent.com/MaaMmP0N4psfPqQOUqegiz3q-SxnRd3sFn-XNKy92XLXo-
    R6dZIcFv7PkvgleeCqynGsUj4s9GUTnL__W77OpjmaTcBgis98nhudlkwsZp7-CNCqihX1zalDbQ",
    "height":768,
    "width":1024,
    "colors":[
    {
    "color":[ 14, 16, 18],
    "weight":0.311767578125
    },
    {
    "color":[238, 232, 203],
    "weight":0.131103515625
    }],
    "entropy":6.568857137759403,
    "size":228025
    }],

    "favicon_colors": [
    {"color": [243, 245, 245], "weight": 0.68701171875},
    {"color": [10, 169, 25], "weight": 0.223388671875},
    {"color": [0, 100, 6], "weight": 0.089599609375}],

    "provider_name": "Embed",
    "cache_age": 86301,
    "type": "html"
  }

Response Attributes
^^^^^^^^^^^^^^^^^^^

``original_url``
    The url that was passed into Embedly. This will be something like a bit.ly
    shortened link or if there is no redirect it will be the same as the
    ``url`` attribute.

``url``
    The effective url of the request. Whatever Embedly found at the end of any
    redirects.

``type``
    See :ref:`extract-response-types`.

``cache_age``
    How long Embedly is going to cache the response for? Generally, this is for
    a day, unless some external factor tells us to reevaluate the resource.

``safe``
   See :doc:`../../features/safe`

``provider_name``
    The name of the resource provider.

``provider_url``
    The url of the resource provider.

``provider_display``
    For display purposes we ``include provider_display``, it's the subdomain,
    hostname, and public suffix of the provider.

``favicon_url``
    The url of the favicon.

``favicon_colors``
    List of dominant colors extracted from ``favicon_url``.
    See :ref:`Dominant Colors <extract-images>`

``title``
    The title of the resource. It's picked in the following order:

    * The rss entry's title
    * The oEmbed title
    * The open graph title
    * The ``meta`` title tag
    * The ``title`` attribute in the ``head`` element

``authors``
    A list of all the authors that are associated with this article. Each author
    has a ``url`` and ``name``. Here is an example response::

        [{
          "name": "Sean Creeley"
          "url": "http://blog.embed.ly/screeley"
        }]

    Most articles have only one author, but ``authors`` makes it flexible enough
    to add more if necessary.

``media``
    See :ref:`media`

``published``
    A representation of the date which the article was published in milliseconds.
    If an ``offset`` is present, then there was timezone data present, otherwise
    we assume the Date is in UTC. Like all dates, this is a little confusing, so
    we will explain. Say the Embedly parser came across the following HTML::

      <span class="pubdate">Aug 24, 2012</span>

    Because there is no timezone information, Embedly will not return an
    ``offset`` and the ``published`` attribute will be in UTC. We will return the
    following response::

      "published": 1345766400000

``offset``
    The UTC offset of the date in milliseconds. See the above section for more
    information about ``offset`` and how to use it with the ``published`` time.

``description``
    The description of the resource. It's picked in the following order:

    * The oEmbed description
    * The open graph description
    * The ``meta`` description tag
    * An excerpt pulled programmaticly by Embedly

``lead``
    Often there is a lead paragraph that is a brief summary of the rest of the
    article. Embedly tries to pull this lead paragraph out for a better reading
    experience. It is always a ``p`` tag, i.e.::

      "lead": "<p>This is a summary of the below article</p>"

``content``
    This is the html that we pulled from the URL. It's been sanitized, so it will
    only contain the following tags::

      'a', 'abbr', 'acronym', 'b', 'big', 'blockquote', 'br', 'cite', 'code',
      'del', 'dfn', 'em', 'i', 'ins', 'kbd', 'mark', 'pre', 'q', 's', 'samp',
      'small', 'span', 'strike', 'strong', 'sub', 'sup', 'time', 'tt', 'u',
      'var', 'p', 'div', 'a', 'h2', 'h3', 'h4', 'h5', 'h6', 'img', 'ol', 'ul',
      'li'

    All tag attributes have been removed as well. The only effective
    attributes are:

      * ``href`` on an ``a`` tag
      * ``src`` on an ``img`` tag

    More information on :doc:`Article extraction <../../features/article>`.

``keywords``
    See :doc:`../../features/keywords`

``entities``
    See :doc:`../../features/entities`

``related``
    See :doc:`../../features/related`

``images``
    See :ref:`Images and Dominant Colors <extract-images>`


.. _media:

Media
-----
The media is primary type of content (video, photo, etc.) that is
associated with a ``url``. It follows the general pattern of the
:doc:`oEmbed Response </api/embed/endpoints/1/oembed>`, but with only a limited
set of attributes. Note: It is optional and only available if we can classify it
as such type.

``type``
    The resource type. Valid values, along with value-specific parameters, are
    described below.


The photo type
^^^^^^^^^^^^^^
This type is used for representing static photos. The following parameters are
defined:

``url``
    The source URL of the image. Consumers should be able to insert this URL
    into an``<img>``element. Only HTTP and HTTPS URLs are valid.

``width``
    The width in pixels of the image specified in the ``url`` parameter.

``height``
    The height in pixels of the image specified in the ``url`` parameter.


The video type
^^^^^^^^^^^^^^
This type is used for representing playable videos. The following parameters
are defined:

``html``
    The HTML required to embed a video player. The HTML should have no padding
    or margins. Consumers may wish to load the HTML in an off-domain iframe to
    avoid XSS vulnerabilities.

``width``
    The width in pixels required to display the HTML. If not supplied
    the HTML returned will expand horizontally to the size of its parent
    container.

``height``
    The height in pixels required to display the HTML. If not supplied
    the HTML returned will expand vertically to the size of its parent
    container.


The rich type
^^^^^^^^^^^^^
This type is used for rich HTML content that does not fall under one of the
other categories. The following parameters are defined:

``html`` (required)
    The HTML required to display the resource. The HTML should have no padding
    or margins. Consumers may wish to load the HTML in an off-domain iframe to
    avoid XSS vulnerabilities. The markup should be valid XHTML 1.0 Basic.

``width`` (required)
    The width in pixels required to display the HTML. If not supplied
    the HTML returned will expand horizontally to the size of its parent
    container.

``height`` (required)
    The height in pixels required to display the HTML. If not supplied
    the HTML returned will expand vertically to the size of its parent
    container.


Error Codes
-----------

JSON Requests
^^^^^^^^^^^^^

400 Bad Request
  * Required "url" parameter is missing.
  * Either "url" or "urls" parameter is reqiured.
  * Invalid URL format.
  * Invalid "maxheight" parameter.
  * Invalid "maxwidth" parameter.
  * Invalid "urls" parameter, exceeded max count of 20.

401 Unauthorized
  * Invalid key or oauth_consumer_key provided: <key>, contact: support@embed.ly.
  * The provided key does not support this endpoint: <key>, contact: support@embed.ly.
  * URL is private or restricted.

403 Forbidden
  * This service requires an embedly key parameter, contact: support@embed.ly or sign up: http://embed.ly/signup.
  * Invalid IP provided: <ip>, contact: support@embed.ly.
  * Invalid referrer provided: <referrer>, contact: support@embed.ly.

404 Not Found
  URL Not Found, we will log this and determine if usable.

500 Server issues
   Embed.ly is having trouble with this url. Please try again or contact us, support@embed.ly.

501 Not Implemented
   Not implemented for format: acceptable values are ``{json}``.

503 Service Unavailable
  ``Note``: This happens if our service is down, please contact us immediately: support@embed.ly.

JSONP Requests
^^^^^^^^^^^^^^

Format
    ``callbackFunction({"url": "url with error", "error_code": "error code",
    "error_message": "error message", "type": "error"})``

Error Response
    ``jsonp1273162787542({"url": "http://flickr.com/embedly", "error_code": 404, "error_message":
    "HTTP 404: Not Found", "type": "error"})``
