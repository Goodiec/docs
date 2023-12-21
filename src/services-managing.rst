Managing ODK-X Services
==============================

.. _services-managing:

.. contents:: :local:

.. _services-architect-prereqs:

Prerequisites
---------------------

ODK-X Services is a prerequisite to all Data Management Application. You will also need the ODK-X tools:

  - :doc:`app-designer-intro`
  - :doc:`cloud-endpoints-intro`

You will also need at least one of the following ODK-X tools:

  - :doc:`survey-using`
  - :doc:`tables-using`

Survey and Tables can work independently and do not require you to use both.

If you have not installed Services already, follow our guide for :doc:`basics-install`

.. _services-managing-servers:

Compatible Servers
~~~~~~~~~~~~~~~~~~~~~~

It is important to match your version of ODK-X Services with an appropriate version of a :doc:`cloud-endpoints-intro`. To do this, find the release from the `Services Releases page <https://github.com/odk-x/services/releases>`_ and match it to a release from the `Sync Endpoint Releases page <https://github.com/odk-x/sync-endpoint/releases>`_.


.. _services-managing-server-config:

Server Configuration
--------------------------------

Before you are able to synchronize data or application files to a device, you will need to configure your server settings within Services. This tells the device which server to contact and what user to authenticate. After these settings are configured, you can optionally lock them with an administrator password. See :ref:`services-managing-admin-settings`.

  1. Open Services. Click on the hamburger icon (:guilabel:`☰`)

    .. image:: /img/services-managing/services-options-settings.*
      :alt: Services Menu Options
      :class: device-screen-vertical

  2. Select :menuselection:`Settings --> Server Settings`

    .. image:: /img/services-managing/services-settings.*
      :alt: Services Settings Menu
      :class: device-screen-vertical

    .. image:: /img/services-managing/services-server-settings.*
      :alt: Services Server Settings Menu
      :class: device-screen-vertical

  3. Choose :guilabel:`Server URL` and specify your server URL

    .. note::

      If you are using SSL, be sure to specify :code:`https://...`

  4. Authenticate user credentials

    .. note::

      If your server is configured to allow anonymous access this step is optional.

    a. Change the :guilabel:`Server Sign-on Credential` to :menuselection:`Username` and enter the appropriate credentials in the :guilabel:`Username` and :guilabel:`Server Password` fields.
    b. Exit out of the :menuselection:`Server Settings` page, and then the :menuselection:`Settings` page, by using the back button and you should see that you have been logged in as an :guilabel:`Authenticated User`.

      .. image:: /img/services-managing/services-authenticated-user-logged-in.*
        :alt: Services Authenticated User logged In
        :class: device-screen-vertical

.. _services-using-reset-app-server:

Resetting the App Server
-------------------------

Resetting your app server pushes the configuration and data on your tablet up to the server. After pushing files from :doc:`app-designer-intro` to the device, this is how to push those files to the server to initialize your Data Management Application. All other devices synchronizing with your server will receive these configuration and data files.

.. note::

  This option should only be used to initialize or update your Cloud Endpoint.

.. warning::

  If a data table on the server does not exist on the device, that table, all of its data, and all associated files (such as forms) will be deleted from the server.

If a data table on the server is identical to one on the device, the data in that table will be synced and the files on the server will be updated to be exactly those present on the device (deleting any files associated with this table that existed only on the server).

Before resetting:

  1. It is critical that you first ensure that your device contains all the tables, files, and data you want to preserve in your application. See :ref:`instructions <services-using-sync>`.

  2. Authenticate as a user who has administrator privileges. See :ref:`instructions <services-using-change-user>`.

To reset the server you must launch the Sync screen. Launch Services. Click the :guilabel:`Sync` icon.

    .. image:: /img/services-managing/services-homescreen-sync.*
      :alt: Services Sync Button
      :class: device-screen-vertical

You will then see the Sync screen.

  .. image:: /img/services-managing/services-sync-admin.*
    :alt: Sync Screen
    :class: device-screen-vertical

Before resetting, you should verify all options are set correctly.

If you do not see the :guilabel:`Reset App Server` button then you need to change users to an administrator. Instructions are provided in the :ref:`services-using-change-user` section.

  .. warning::

    If you authenticate as a different user after modifying data in the database, you could lose changes. Each user can have their own set of permissions to read, write, and delete different portions of the database. If you switch from one set of permissions to another, changes to areas that the new user is not allowed to modify may be lost.

    To prevent this be sure to synchronize all changes before authenticating new users.

The sync interaction has four options for managing file attachments. These are offered if bandwidth or storage is a concern:

  - :menuselection:`Fully Sync Attachments` - *Default* - Synchronize all file attachments with the server.
  - :menuselection:`Upload Attachments Only` - Only upload attachments from the device to the server.
  - :menuselection:`Download Attachments Only` - Only download attachments from the server to the device.
  - :menuselection:`Do Not Sync Attachments` -  Do not sync any attachments.

  .. note::

    All four of the attachment options will fully synchronize your database. This includes all completed forms and collected data.

Click on :guilabel:`Reset App Server`. A confirmation dialog will popup asking you to confirm resetting the App Server. Again, this can delete all data on this Cloud Endpoint! If you are sure you want to continue, click :guilabel:`Reset`.

Services will contact the ODK-X Cloud Endpoint and attempt to push all configuration and data currently on the tablet up to the specified Cloud Endpoint. A progress dialog will be displayed and, alternatively, the status of resetting the app server can be obtained by looking at the notifications generated by Services in the notification area.

.. warning::

  Should you begin modifying data rows while syncing, the changes to those rows will not be synced until you save them as incomplete or finalize the row, and the act of editing will generally mark the sync as having ended with conflicts. This means that you must complete your edits and re-issue the sync to ensure that your changes are propagated up to the server.


.. _services-managing-admin-settings:

Administrator Settings
------------------------
Administer settings allow you to lock in certain settings so that they cannot be changed without the administrator password.

.. tip::

  To modify a setting locked behind administrator privileges, enter the administrator password and then access that setting.

.. _services-set-admin-password:

Setting an Administrator Password
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

  1. Open Services. Click on the hamburger icon (:guilabel:`☰`).

    .. image:: /img/services-managing/services-options-settings.*
      :alt: Services Menu Options
      :class: device-screen-vertical

  2. Select :menuselection:`Settings --> Restrictions`

    .. image:: /img/services-managing/services-restrictions-settings.*
      :alt: Services Settings Menu
      :class: device-screen-vertical

    .. image:: /img/services-managing/services-admin-pass-disabled.*
      :alt: Services Admin Password Disabled
      :class: device-screen-vertical

  3. Select :menuselection:`Admin Password`. A prompt will appear where you can enter a new admin password.

    .. image:: /img/services-managing/services-admin-pass-prompt.*
      :alt: Services Admin Password Prompt
      :class: device-screen-vertical

  4. After creating an admin password, the screen shows that it is enabled.

    .. image:: /img/services-managing/services-admin-pass-enabled.*
      :alt: Services Admin Password Enabled
      :class: device-screen-vertical

  5. Back out to the Settings screen


.. _services-access-admin-settings:

Accessing Administrator Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
After the administrator password is set, you can enter it to access the administrator settings.

  1. From the Settings screen, select :menuselection:`Admin Access to Settings`

    .. image:: /img/services-managing/services-admin-settings-available.*
      :alt: Services Settings With Admin
      :class: device-screen-vertical

  2. You will be prompted to enter the admin password.

    .. image:: /img/services-managing/services-enter-admin-pass.*
      :alt: Services Admin Password Entry
      :class: device-screen-vertical

  3. After entering the correct password, you will see the full list of administrator settings available to you.

    .. image:: /img/services-managing/services-admin-settings.*
      :alt: Services Admin Settings
      :class: device-screen-vertical


.. _services-admin-server-settings:

Managing Server Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
:menuselection:`Settings --> Server`

  .. image:: /img/services-managing/services-admin-server.*
    :alt: Services Admin Server Settings
    :class: device-screen-vertical

  - :menuselection:`Server URL` - if checked the Server URL will be locked.
  - :menuselection:`Server Sign-on Credential` - if checked the means of authenticating will be locked.
  - :menuselection:`Username` - if checked the username field will be locked.
  - :menuselection:`Server Password` - if checked the password field will be locked.

.. _services-admin-tables-settings:

Managing Tables Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
:menuselection:`Settings --> ODK-X Tables`

  .. image:: /img/services-managing/services-admin-tables.*
    :alt: Services Admin Tables Settings
    :class: device-screen-vertical

  - :menuselection:`Use custom home screen` - if checked the custom home screen option will be locked.

.. _services-admin-device-settings:

Managing Device Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~
:menuselection:`Settings --> Prefrences`

  .. image:: /img/services-managing/services-admin-device.*
    :alt: Services Admin Device Settings
    :class: device-screen-vertical

  - :menuselection:`Default Locale` - specifies your preferred localization. By default this is set to US English. If you provide translations for your Data Management Application, this is where to enable them.
  - :menuselection:`Text Font Size` - if checked the text font size will be locked.
  - :menuselection:`Show Splash Screen` - if checked the splash screen image and enable/disable flag will be locked.
  - :menuselection:`Selected Splash Image` - holds the image that will be displayed in the splash screen. By default this is an ODK logo, but can be set to your organization's own logo or another image.

.. _services-locking-admin-settings:

Locking Administrator Settings
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When you have finished configuring the administrator settings, back out of the menu. You will then see the normal settings menu, but with all appropriate settings locked. To modify these locked settings, follow the instructions for :ref:`services-access-admin-settings` and repeat the process.

.. _services-managing-reset-config:

Resetting Configuration
------------------------

This option will clear the ODK-X cache of table and form definitions and scan the file system to refill that cache. This is automatically run after each successful sync operation to ensure that Survey and Tables display the correct information. If you have manually modified files inside of the :file:`/sdcard/opendatakit/` folder via :program:`grunt` commands, with :program:`Files by Google`, or by some other means, you may need to use this option to refresh the cache. If you are not seeing forms or tables that you expect, this option may fix that problem.

.. note::

  This option does NOT delete any data or files. It also does not reset your server URL setting. But it will log you out of your currently authenticated user and clear your device and tables settings.

After pressing this option, you will be prompted to confirm this is what you want to do.

  .. image:: /img/services-managing/services-reset-config-prompt.*
    :alt: Reset Configuration Prompt
    :class: device-screen-vertical

Press :guilabel:`OK` to clear the config. Back out of the :guilabel:`Settings` menu. The next time you run Tables or Survey they will rerun their initialization logic, which may take a few moments.
