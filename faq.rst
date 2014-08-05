.. _faq:

Frequently Asked Questions
==========================
Great minds think alike. If none of these answer your question(s),
check out our FAQ Forum at `<http://support.embed.ly>`_

General
-------

What is Embedly?
^^^^^^^^^^^^^^^^
Embedly is a set of front-end tools that help web and app developers
create better user experiences. We believe the best tools are simple,
easy to use, and perfectly suited to their task. You’ll find that
embodied in Embed, Extract, and Display—tools that provide ultra-fast
ways to present richer content more effectively.

For more information, see our introductions
:doc:`for authors </products/index>` or
:doc:`for developers </api/tutorials/start>`.

Why Embedly?
^^^^^^^^^^^^
Because it's the easiest way to present rich content and create user experiences.
In less then 10 minutes, you can embed content from hundreds of providers and
generate rich previews for any URL on the web.

Here's a quote from James Patterson, the Platform Lead at Yammer:

  If we weren't using Embedly we'd have had to spend probably around a week of
  an engineer's time to build something that gets the basic job done. It
  wouldn't be nearly as good, we'd have to deal with constant bug fixes and
  we'd be paying Amazon $200-$300 a month to host it anyway. Using Embedly is
  a no-brainer.

See our `customers </customers>`_ page for more testimonials.

We take care of every step of the process: retrieving information
about a URL, checking it against malware registries, extracting content,
making additional API calls to providers that support them, parsing RSS
feeds, and performing validation. We save you time so that you can focus
on making your app great.

Am I paying for content?
^^^^^^^^^^^^^^^^^^^^^^^^
No, you're paying for the use of Embedly's processing engine. You're
responsible for any copyright implications that may come from embedding
third-party content in your site or app.

How fast is Embedly?
^^^^^^^^^^^^^^^^^^^^
Fast. Embedly uses several techniques to accelerate the embedding process:

* **Caching**: The first time we see a URL, we store its contents in our
  cache so that repeated requests can be processed immediately. We invalidate
  the cache at least once every 24 hours, depending on the response headers
  we receive.
* **Parallel processing**: Once we've resolved the initial URL, we perform
  the API calls, image parsing, and malware detection in parallel.
* **Batch processing**: Send up to 20 URLs at a time to Embedly, and we'll
  process them all in parallel.

Where can I find a demo of Embedly in action?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
You should check out what our `customers </customers>`_ have been building.

API
---

Most of our common API questions can be found in our
`Support Forum <http://support.embed.ly>`_.
If you don't see an answer, post a question.


Upgrade to Products
-------------------

If you are currently on a Free, Starter, Basic, Core, or Plus plan
you have the option to keep your plan or move to our new products.

Why products?
^^^^^^^^^^^^^
We've realized that many users have specific use cases with Embedly's
services. This includes a range of embedding,
aggregating articles and stories, or building visually engaging applications.
The products allow us to group each of these unique functions into easily
understood, documented, and supported offerings.

Can I keep my existing plan?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Yes, if you are currently on a Free, Starter, Basic, Core, or Plus plan
you have the option to keep your plan. There will no changes to the
pricing or usage. You will however not be able to move up or down to a
different plan.

What happens when I add a new product?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Adding a new product will remove your existing plan and adjust
your account to the product usage and pricing offered. You will not be
able to move back to your old plan.

Why can't I just have both a plan and products?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Mostly, it would be a billing support nightmare
to manage both on one account. The products were
built to allow the services to scale and become a
better offering. If you are perplexed and want to
try it out, feel free to create a new account.


What are the legacy endpoints?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
The Preview and Objectify endpoints are becoming legacy endpoints,
they will still exist for users with Starter, Basic, Core, or Plus plans.
Read more about the :doc:`api/legacy/endpoints/index`.

Will the legacy endpoints work after I upgrade to a product?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Yes, if you your old plan has access to the Preview and/or Objectify endpoints
and you upgrade to the `Extract <http://embed.ly/extract>`_ product.

Will my API key change after the upgrade to products?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
Your API key will stay the same after the upgrade.
You may regenerate your key at anytime through the Account tab.

Where can I find contractors to integrate Embedly for me?
^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^^
We offer `several libraries <http://embed.ly/docs/libraries>`_ to help integrate Embedly,
so developers with experience in web development or mobile app development should be able
to help you integrate Embedly. There is also `a listing of developers who can help <http://embed.ly/odesk>`_,
provided by oDesk.


