## `ern code-push release`

#### Description

* Update/publish one or more MiniApps in a target released native application version Over the Air (OTA)  
* Perform compatibility checks to ensure that the new MiniApp versions are compatible with the target native application version
*  Update the Cauldron with a new `CodePush` entry containing the versions of all MiniApps that are part of this publication  

**Note:** The `ern code-push <miniapps..>` command pushes JavaScript code changes only, not native ones. Therefore compatibility checks will ensure that the MiniApp's native dependencies are compatible with the versions running in the target native application version.

#### Syntax

`ern code-push release <miniapps..>`  

**Arguments**

`<miniapps..>`

* One or more MiniApps (delimited by spaces) version(s) to CodePush.
* You can only add MiniApp versions that have been published to NPM. 
* You cannot use the `file` or `git` schemes for the MiniApp(s).

**Options**  

`--descriptor/-d <descriptor>`

* Specify a target native application version to publish the new MiniApp version to using a *complete native application descriptor* from the Cauldron  
* **Default**  If this option is not used, the command lists all released native application versions from the Cauldron and prompts you to choose a version.  

`--force/-f`

* Bypass all compatibility checks and force OTA update through CodePush.

`--appName <appName>`

* Specify the `code-push` application name that this update is targeting  
* **Default**  If this option is not used, the `ern code-push <miniapps..>` command uses the application name from the *complete native application descriptor* and you are prompted to confirm the name.  

`--deploymentName/-d <deploymentName>`

* Specify the `code-push` deployment name that this update is targeting  
* **Default**  If this option is not used, the command prompts you for the deployment name to target. If deployment names for your native applications are stored in the Cauldron, a list displays the names and you are prompted to choose the target.  

`--targetBinaryVersion/-t <targetBinaryVersion>`

* Specify one or more versions of the native application to target  

`--mandatory/-m`

* Specify that the update is mandatory  
* The update is installed immediately after the download is complete.
* **Default**  Updates are not mandatory.  

`--rollout/-r <rollout>`

* Specify the percentage of users who will have immediate access to this release  
* **Default**  100

`--skipConfirmation/-s`

* Skip final confirmation prompt if no compatibility issues are detected and proceeed with CodePush
* **Default** Do not skip confirmation prompt

#### Remarks
 
* MiniApps are packaged in a single bundle. If the native application version contains 5 MiniApps and you update a single version, then the remaining 4 MiniApp versions are left untouched in the bundle.  
* The `ern code-push <miniapps..>` command executes the `code-push release-react` command.
* You do not need to run the `ern code-push <miniapps..>` command from within a MiniApp working directory.  The MiniApp is retrieved from npm and therefore should have a versioned npm package descriptor corresponding to the published MiniApp version.  

#### Related commands

[code-push release-react] | Release a React Native update to an app development.
 
[code-push release-react]: https://github.com/Microsoft/code-push/tree/master/cli