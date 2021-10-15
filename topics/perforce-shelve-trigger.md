[//]: # (title: Perforce Shelve Trigger)
[//]: # (auxiliary-id: Perforce Shelve Trigger)

The _Perforce shelve trigger_ automatically runs a build on detecting a change in [shelved Perforce files](https://www.perforce.com/manuals/v17.1/p4guide/Content/CmdRef/p4_shelve.html).

>You can also run such a build manually, with the [custom run](running-custom-build.md).

The trigger supports Perforce 2018.2 or later.

The trigger monitors all [Perforce VCS roots](perforce.md) associated with the current [build configuration](build-configuration.md). You can filter monitored changelists by their description. To do this, specify the required keyword to search.

>See how to invoke this trigger [via TeamCity REST API](https://www.jetbrains.com/help/teamcity/rest/edit-build-configuration-settings.html#Manage+Build+Triggers).

On any change made in shelved files of a matching changelist, TeamCity will start a new [personal build](personal-build.md) with the contents of these files.