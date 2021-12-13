[//]: # (title: Configuring Your User Profile)
[//]: # (auxiliary-id: Configuring Your User Profile;Managing your User Account)

To get to your user profile settings, click your avatar in the header and select __Profile__ from the drop-down menu.

### Changing Your Password

If [built-in authentication](configuring-authentication-settings.md#Built-in+Authentication) is configured, TeamCity server maintains passwords for the user authentication. You can change the password in __Your Profile | General | Built-in Authentication__. Enter an existing and new passwords and click __Save changes__.

The password can only be changed for the built-in authentication. If you do not see these fields, this means that TeamCity is configured to use external authentication and the password should be changed in the corresponding external system. 

You can reset your built-in authentication password using the _Reset password_ link on the sign-in page.

>If you have not received the email with the reset instructions, check if TeamCity [Email Notifier](notifier.md) is enabled. Contact your server administrator for details.
> 
{type="note"}

If you change or reset your password, TeamCity will automatically sign you out of all sessions.

## Managing Access Tokens

If [token-based authentication](configuring-authentication-settings.md#Token-Based+Authentication) is enabled on the TeamCity server, you can create access tokens and use them for authentication:
* instead of your password (for example, in scripts or IDE plugin login), _or_
* as the value of the `Authorization: Bearer <token-value>` HTTP header. For instance, in REST API requests:   
   ```Shell
   curl --header "Authorization: Bearer <token-value>" http://<host>:<port>/app/rest/builds
   ```

You can manage tokens in __Your Profile | Access Tokens__. Note that the token value is only available during token creation and is not possible for retrieval afterwards.
  
To automatically revoke a token after its expiration, specify its time limit.

<video href="_3oKTnYwKa8"
title="New in TeamCity 2020.2: Short-lived Access Tokens"/>

<anchor name="token-scope"/>

You can create tokens with limited permissions for REST API requests. By default, the __Permissions scope__ field value is set to "_Same as current user_", which means that the created token will grant the same permissions as those of the current user. You can use such token both for authentication in the UI and for REST API requests.   
If you change the value to "_Limit per project_", you will be able to limit the token's access to a certain project and select particular permissions for it. The list of available projects and their permissions depend on your user permissions. Such token can only be used for REST API requests.

<img src="create-access-token.png" alt="Create an access token"/>

Note that some operations allowed by enabled permissions might be blocked by the absence of other permissions. Please make sure to thoroughly manage the token's scope to get predictable results of your requests. In case of any issues, you can contact us via any convenient [feedback channel](feedback.md).

## Managing Version Control Username Settings

In __Your Profile | General__, you can see the list of your version control usernames in the __Version Control Username Settings__ area.   
By default, TeamCity uses your login name as the VCS username. Click __Edit__ to provide actual usernames for version control systems you use. Make sure the usernames are correct.   
These settings are not used for authentication for the particular VCS, and so on.

These settings enable you to:
* track your changes status on the [Changes](viewing-your-changes.md),
* highlight such builds on the Projects page if the appropriate [option is selected](#Customizing+UI),
* notify you on such builds when the __Builds affected by my changes__ option is selected in [notifications settings](adding-notification-rules.md#What+Will+Be+Watched).

## Configuring Two-Factor Authentication

TeamCity administrators can enable [two-factor authentication](managing-two-factor-authentication.md) (2FA) on the whole server. In this case, you will be prompted to configure 2FA settings for your user account. To do this:

1. Download and install any suitable authenticator app on your mobile device: for example, Google Authenticator or Microsoft Authenticator.
2. In TeamCity, open __Your Profile | Two-factor Authentication__.
3. Scan the generated QR code with the authenticator app, or enter the provided key manually (choose "time-based" as the key type).
4. Enter the numeric code generated by the app to TeamCity.
5. Save the provided recovery keys to a secure place. They will be needed if you ever lose access to the authenticator.
6. Save the settings.

Next time you will be signing in to TeamCity, it will prompt you to enter the confirmation code from the authenticator.

## Customizing UI

In __Your Profile | General__, you can customize the following UI settings:
* Highlight my changes and investigations: Select to highlight builds that include your changes (changes committed by a user with the VCS username provided in the [Version Control Username Settings](#Managing+Version+Control+Username+Settings) section) and problems you were assigned to investigate on the __Projects__ page, __Project Home__ page, __Build Configuration Home__ page.
* Show date/time in my timezone: Check the option, if you want TeamCity to automatically detect your time zone and show the date and time (for example, build start, VCS change time, and so on) according to it.
* Show all personal builds
* Add builds manually triggered by you to your [favorites](favorite-build.md).

## Viewing your Roles and Permissions

In __Your Profile | Groups__, you can view the list of user groups you are assigned to.

In __Your Profile | Roles__, you can view your roles and permissions in different projects. Note that roles are assigned to a user by the system administrator.

## Managing Notification Rules

In __Your Profile | Notification Rules__, you can view what notification rules you inherit from your user group and create new personal rules.

## Uploading Avatar

Since version 2021.2, users can upload their avatars in the user profile. The avatars are displayed around the TeamCity UI, next to the changes (commits) of their authors. Only users with the _View all users_ [permission](managing-roles-and-permissions.md) can see them.

<seealso>
        <category ref="concepts">
            <a href="managing-roles-and-permissions.md">Roles and Permissions</a>
        </category>
        <category ref="user-guide">
            <a href="viewing-your-changes.md">Viewing Your Changes</a>
            <a href="adding-notification-rules.md">Subscribing to Notifications</a>
        </category>
</seealso>