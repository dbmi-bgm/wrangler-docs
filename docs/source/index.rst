=============
Wrangler Docs
=============

.. image:: https://readthedocs.org/projects/wrangler-docs/badge/?version=latest

A centralized repository for storing documentation for 4DN/CGAP data wranglers. Pushes to master will automatically trigger a docs build. The badge above indicates the latest build status. Sphinx is very reluctant to fail so it is unlikely to do so even in the presence of many formatting errors. Documentation should be written in ``rst`` format. `Here <https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html>`_ is a helpful CheatSheet on how to use the format. This document should ideally be identical to ``docs/source/index.rst`` except that in ``index.rst`` you will want to use the ``toctree`` directive to specify the documentation hierarchy (see `here <https://thomas-cokelaer.info/tutorials/sphinx/rest_syntax.html#include-other-rst-files-with-the-toctree-directive>`_).


Other Documentation Sources
^^^^^^^^^^^^^^^^^^^^^^^^^^^

  - CGAP `Docs <https://cgap-portal.readthedocs.io/en/latest/>`_
  - FourFront `Docs <https://fourfront.readthedocs.io/en/latest/>`_
  - Foursight `Docs <https://foursight.readthedocs.io/en/latest/>`_
  - Utils `Docs <https://dcic-utils.readthedocs.io/en/latest/>`_

.. toctree::
  :maxdepth: 2
  :numbered:
  :tiitlesonly:
