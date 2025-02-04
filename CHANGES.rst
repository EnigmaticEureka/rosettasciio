Changelog
*********

Changelog entries for the development version are available at
https://rosettasciio.readthedocs.io/en/latest/changes.html

.. towncrier-draft-entries:: |release| [UNRELEASED]

.. towncrier release notes start

0.1 (2023-06-06)
================

New features
------------

- Add support for reading the ``.xml``-format from Horiba Jobin Yvon's LabSpec software. (`#25 <https://github.com/hyperspy/rosettasciio/issues/25>`_)
- Add support for reading the ``.tvf``-format from TriVista. (`#27 <https://github.com/hyperspy/rosettasciio/issues/27>`_)
- Add support for reading the ``.wdf``-format from Renishaw's WIRE software. (`#55 <https://github.com/hyperspy/rosettasciio/issues/55>`_)
- Added subclassing of ``.sur`` files in CL signal type and updated metadata parsing (`#98 <https://github.com/hyperspy/rosettasciio/issues/98>`_)
- Add optional kwarg to tiff reader ``multipage_as_list`` which when set to True uses ``pages`` interface and returns list of signal for every page with full metadata. (`#104 <https://github.com/hyperspy/rosettasciio/issues/104>`_)


Bug Fixes
---------

- Ensure that the ``.msa`` plugin handles ``SIGNALTYPE`` values according to the official format specification. (`#39 <https://github.com/hyperspy/rosettasciio/issues/39>`_)
- Fix error when reading Velox file containing FFT with an odd number of pixels (`#49 <https://github.com/hyperspy/rosettasciio/issues/49>`_)
- Fix error when reading JEOL ``.pts`` file with un-ordered frame list or when length of ``frame_start_index`` is smaller than the sweep count (`#68 <https://github.com/hyperspy/rosettasciio/issues/68>`_)
- Fix exporting scalebar with reciprocal units containing space (`#90 <https://github.com/hyperspy/rosettasciio/issues/90>`_)
- Fix array indexing bug when loading a ``sur`` file format containing spectra series. (`#98 <https://github.com/hyperspy/rosettasciio/issues/98>`_)
- For more robust xml to dict conversion, ``convert_xml_to_dict`` is replaced by ``XmlToDict`` (introduced by PR #111). (`#101 <https://github.com/hyperspy/rosettasciio/issues/101>`_)
- Fix bugs with reading non-FEI and Velox ``mrc`` files, improve documentation of ``mrc`` and ``mrcz`` file format. Closes `#71 <https://github.com/hyperspy/rosettasciio/issues/71>`_, `#91 <https://github.com/hyperspy/rosettasciio/issues/91>`_, `#93 <https://github.com/hyperspy/rosettasciio/issues/93>`_, `#96 <https://github.com/hyperspy/rosettasciio/issues/96>`_, `#130 <https://github.com/hyperspy/rosettasciio/issues/130>`_. (`#131 <https://github.com/hyperspy/rosettasciio/issues/131>`_)


Improved Documentation
----------------------

- Consolidate docstrings and documentation for all plugins (see also `#47 <https://github.com/hyperspy/rosettasciio/pull/47>`_, `#59 <https://github.com/hyperspy/rosettasciio/pull/59>`_, `#64 <https://github.com/hyperspy/rosettasciio/pull/64>`_, `#72 <https://github.com/hyperspy/rosettasciio/pull/72>`_) (`#76 <https://github.com/hyperspy/rosettasciio/issues/76>`_)
- Remove persistent search field in left sidebar since this makes finding the sidebar on narrow screens difficult.
  Set maximal major version of Sphinx to 5. (`#84 <https://github.com/hyperspy/rosettasciio/issues/84>`_)


Deprecations
------------

- Remove deprecated ``record_by`` attribute from file readers where remaining (`#102 <https://github.com/hyperspy/rosettasciio/issues/102>`_)


Enhancements
------------

- Recognise both byte and string object for ``NXdata`` tag in NeXus reader (`#112 <https://github.com/hyperspy/rosettasciio/issues/112>`_)


API changes
-----------

- Move, enhance and share xml to dict/list translation and other tools (new api for devs) from ``Bruker._api`` to utils:
  ``utils.date_time_tools.msfiletime_to_unix`` function to convert the uint64 MSFILETIME to  datetime.datetime object.
  ``utils.tools.sanitize_msxml_float`` function to sanitize some MSXML generated xml where comma is used as float decimal separator.
  ``utils.tools.XmlToDict`` Xml to dict/list translator class with rich customization options as kwargs, and main method for translation ``dictionarize`` (`#111 <https://github.com/hyperspy/rosettasciio/issues/111>`_)


Maintenance
-----------

- Initiate GitHub actions for tests and documentation. (`#1 <https://github.com/hyperspy/rosettasciio/issues/1>`_)
- Initiate towncrier changelog and create templates for PRs and issues. (`#3 <https://github.com/hyperspy/rosettasciio/issues/3>`_)
- Add github CI workflow to check links, build docs and push to the ``gh-pages`` branch. Fix links and add EDAX reference file specification (`#4 <https://github.com/hyperspy/rosettasciio/issues/4>`_)
- Add azure pipelines CI to run test suite using conda-forge packages. Add pytest and coverage configuration in ``pyproject.toml`` (`#6 <https://github.com/hyperspy/rosettasciio/issues/6>`_)
- Fix minimum install, add corresponding tests build and tidy up leftover code (`#13 <https://github.com/hyperspy/rosettasciio/issues/13>`_)
- Fixes and code consistency improvements based on analysis provided by lgtm.org (`#23 <https://github.com/hyperspy/rosettasciio/issues/23>`_)
- Added github action for code scanning using the codeQL engine. (`#26 <https://github.com/hyperspy/rosettasciio/issues/26>`_)
- Following the deprecation cycle announced in `HyperSpy <https://hyperspy.org/hyperspy-doc/current/user_guide/changes.html>`_,
  the following keywords and attributes have been removed:

  - :ref:`Bruker composite file (BCF) <bcf-format>`: The ``'spectrum'`` option for the
    ``select_type`` parameter was removed. Use 'spectrum_image' instead.
  - :ref:`Electron Microscopy Dataset (EMD) NCEM <emd_ncem-format>`: Using the
    keyword ``'dataset_name'`` was removed, use ``'dataset_path'`` instead.
  - :ref:`NeXus data format <nexus-format>`: The ``dataset_keys``, ``dataset_paths``
    and ``metadata_keys`` keywords were removed. Use ``dataset_key``, ``dataset_path``
    and ``metadata_key`` instead. (`#30 <https://github.com/hyperspy/rosettasciio/issues/30>`_)
- Unify the ``format_name`` scheme of IO plugins using ``name`` instead and add ``name_aliases`` (list) for backwards compatibility. (`#35 <https://github.com/hyperspy/rosettasciio/issues/35>`_)
- Add drone CI to test on ``arm64``/``aarch64`` platform (`#42 <https://github.com/hyperspy/rosettasciio/issues/42>`_)
- Unify naming of folders/submodules to match documented format ``name`` (`#81 <https://github.com/hyperspy/rosettasciio/issues/81>`_)
- Add black as a development dependency.
  Add pre-commit configuration file with black code style check, which when installed will require changes to pass a style check before commiting. (`#86 <https://github.com/hyperspy/rosettasciio/issues/86>`_)
- Add support for python-box 7 (`#100 <https://github.com/hyperspy/rosettasciio/issues/100>`_)
- Migrate to API v3 of ``imageio.v3`` (`#106 <https://github.com/hyperspy/rosettasciio/issues/106>`_)
- Add explicit support for python 3.11 and drop support for python 3.6, 3.7 (`#109 <https://github.com/hyperspy/rosettasciio/issues/109>`_)
- Remove test data from packaging and download them when necessary (`#123 <https://github.com/hyperspy/rosettasciio/issues/123>`_)
- Define packaging in ``pyproject.toml`` and keep ``setup.py`` to handle compilation of C extension (`#125 <https://github.com/hyperspy/rosettasciio/issues/125>`_)
- Add release GitHub workflow to automate release process and add corresponding documentation in `releasing_guide.md <https://github.com/hyperspy/rosettasciio/blob/main/releasing_guide.md>`_ (`#126 <https://github.com/hyperspy/rosettasciio/issues/126>`_)
- Add pre-commit hook to update test data registry and pre-commit.ci to run from pull request (`#129 <https://github.com/hyperspy/rosettasciio/issues/129>`_)
- Tidy up ``rsciio`` namespace: privatise ``docstrings``, move ``conftest.py`` and ``exceptions`` to tests and utils folder, respectively (`#132 <https://github.com/hyperspy/rosettasciio/issues/132>`_)


Initiation (2022-07-23)
=======================

- RosettaSciIO was split out of the `HyperSpy repository 
  <https://github.com/hyperspy/hyperspy>`_ on July 23, 2022. The IO-plugins
  and related functions so far developed in HyperSpy were moved to this
  new repository.
