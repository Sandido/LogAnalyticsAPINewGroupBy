# LogAnalyticsAPINewGroupBy

### This repository is to deliver a fix to DataDog. ###

### These are instructions to apply the Powershell fix to the customer's environment ###

Check for registered repositories
--------------------------

To check for registered Powershell repositories on your machine, run the following command. 

    Get-PSRepository

Registering a new Repository
-----------------------------
To install your module from the .nupkg file provided in the pkgs folder, you will need to create a local PowerShell repository that points at the pkgs folder.

    Register-PSRepository -Name LocalRepository -SourceLocation {{pathToNugetPkgsFolder}} -PackageManagementProvider NuGet -InstallationPolicy Trusted

After registering your repository, you can ensure that it was created by running Get-PSRepository and verifying that your repository appears and points at the appropriate folder containing the .nupkg files.


Installing the Module
------------------------
To install the module, you will need to run the following command:

    Install-Module -Name {{moduleName}} -Repository LocalRepository 

For the LogAnalytics functionality, the module to install is Az.Compute. 

If you're using PowerShell 5.0 or 5.1, this will install the modules to C:\Program Files\WindowsPowerShell\Modules.

If you're using PowerShell 6.0 and greater, this will install the modules to C:\Program Files\PowerShell\Modules.
