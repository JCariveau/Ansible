============================
Arensb.Truenas Release Notes
============================

.. contents:: Topics


v1.8.0
======

Release Summary
---------------

Added several new modules.

Minor Changes
-------------

- Added the `pool_scrub_task` plugin, to schedule zfs pool scrub tasks.
- Added the `smart_test_task` plugin, to schedule S.M.A.R.T. disk tests.
- Added the `smart` plugin, to manage the S.M.A.R.T. service.

New Modules
-----------

- arensb.truenas.pool_scrub_task - Schedule periodic scrub of ZFS pools.
- arensb.truenas.smart - Configure S.M.A.R.T. service
- arensb.truenas.smart_test_task - Schedule S.M.A.R.T. tests

v1.7.2
======

Minor Changes
-------------

- Flesh out instructions for building a release.

Bugfixes
--------

- Remove an unneeded, undocumented, and confusing result value.

v1.7.1
======

Bugfixes
--------

- In 'service', services weren't actually being enabled/disabled, or started/stopped.

v1.7.0
======

Major Changes
-------------

- Add the 'truenas_facts' module, for gathering Ansible facts about TrueNAS systems.

Minor Changes
-------------

- Add C(version_added) to each module's documentation.
- Link to the online documentation in README.md, where it'll be visible
  from both github and Ansible Galaxy.

New Modules
-----------

- arensb.truenas.truenas_facts - Gather TrueNAS-related facts

v1.6.2
======

Minor Changes
-------------

- Add auto-generated CHANGELOG.html
- Add online documentation.

v1.6.0
======

Release Summary
---------------

Use native client code on the TrueNAS machine.

Major Changes
-------------

- For now, the old behavior is still the default. To use the new behavior, set the "middleware_method" environment variable to "client", at either the play, block, or task level, using the "environment:" Ansible directive.
- The default behavior will be switched from "midclt" to "client" in a later version.
- Up until now, these modules have been invoking the 'midclt' utility on the TrueNAS client to communicate with the middleware daemon. But that is implemented using a Python module. This release makes it possible to use that Python module directly, resulting in a significant speed improvement (as well as simpler code).

v1.5.2
======

v1.5.1
======

Release Summary
---------------

fix docstrings

Minor Changes
-------------

- Fix formatting in docstrings, so docs should generate better now.

v1.5.0
======

Release Summary
---------------

add ZFS snapshot tasks

Major Changes
-------------

- Added the C(pool_snapshot_task) module, which manages periodic snapshot tasks for ZFS volumes.

v1.4.5
======

Release Summary
---------------

Fix the way sudo is handled for users.

Breaking Changes / Porting Guide
--------------------------------

- The C(sudo) and C(sudo_nopasswd) options are deprecated.

Deprecated Features
-------------------

- In the user module, C(sudo) and C(sudo_nopasswd) options are deprecated. The C(sudo_commands) and C(sudo_commands_nopasswd) options are the preferred way to specify sudo permissions.

Bugfixes
--------

- user module sudo variables didn't work with recent versions of TrueNAS SCALE.
