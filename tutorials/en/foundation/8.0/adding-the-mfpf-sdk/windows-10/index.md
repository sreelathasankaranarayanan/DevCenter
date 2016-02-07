---
layout: tutorial
title: Adding the MobileFirst Platform Foundation SDK to Windows 10 UWP Applications
breadcrumb_title: Windows 10 UWP SDK
relevantTo: [windows10]
weight: 5
---
## Overview
In this tutorial you will learn how to add the MobileFirst Native SDK using Nuget to either a new or existing Windows 8.1 Universal application. You will also learn how to configure the MobileFirst Server to recognize the application, as well as find information about the MobileFirst configuration files that are added to the project.

The MobileFirst Platform Foundation SDK provides a set of API methods enabling a developer to implement various MobileFirst features, such as: authentication and security mechanisms, notifications, resource requests, collecting analytics data and more.

> For a complete list of MobileFirst SDK abilities [visit the user documentation](http://www-01.ibm.com/support/knowledgecenter/SSHS8R_8.0.0/wl_welcome.html).

**Prerequisites:**

- Microsoft Visual Studio 2015 running on Windows 10 and MobileFirst Developer CLI installed on the developer workstation.  
- MobileFirst Server to run locally, or a remotely running MobileFirst Server.
- Make sure you have read the [Setting up your MobileFirst development environment](../../setting-up-your-development-environment/setting-up-the-mobilefirst-development-environment) tutorial.

#### Jump to:

- [Adding the MobileFirst Native SDK](#adding-the-mobilefirst-native-sdk)
- [Updating the MobileFirst Native SDK](#updating-the-mobilefirst-native-sdk)
- [Generated MobileFirst Native SDK artifacts](#generated-mobilefirst-native-sdk-artifacts)
- [Tutorials to follow next](#tutorials-to-follow-next)

## Adding the MobileFirst Native SDK
Follow the below instructions to manually add the MobileFirst Native SDK to either a new or existing Visual Studio project, and registering the application in the MobileFirst Server.

Before starting, make sure the MobileFirst Server is running.  
If using a locally installed server: From a **Command-line** window, navigate to the server's **scripts** folder and run the command: `./start.sh` in Mac and Linux or  `start.cmd` in Windows.

### Creating an application
Create a Windows 8.1 Universal project using Visual Studio 2013/2015 or use an existing project.  

### Creating and registering the application

1. Open the **Command-line** and navigate to the root of the Visual Studio project.  

2. Run the command:

    ```bash
    mfpdev app register
    ```

    The `mfpdev app register` CLI command first connects to the MobileFirst Server to register the application, followed by generating the **mfpclient.resw** file at the root of the Visual Studio project, and adding to it the metadata that identifies the MobileFirst Server.

    > <span class="glyphicon glyphicon-info-sign" aria-hidden="true"></span> **Tip:** The application registration can also be performed from the MobileFirst Operations Console:    
        1. Open your browser of choice and load the MobileFirst Operations Console using the address `http://localhost:9080/mfpconsole/`. You can also open the console from the **Command-line** using the CLI command `mfpdev server console`.  
        2. Click on the "New" button next to "Applications" to create a new application and follow the on-screen instructions.  
        3. After successfully registering your application you can optionally download a "skeleton" Visual Studio project pre-bundled with the MobileFirst Native SDK.

### Adding the SDK

1. To import worklight studio packages, NuGet package manager is used.
NuGet is the package manager for the Microsoft development platform including .NET. The NuGet client tools provide the ability to produce and consume packages. The NuGet Gallery is the central package repository used by all package authors and consumers.

2. Open the Windows 8.1 Universal project in Visual studio 2013/2015. Right click the project solution and navigate → Manage Nuget packages for solution.

    ![Add-Nuget-tosolution-VS-settings](Add-Nuget-tosolution0.png)

3. In the search option , search for IBM MobileFirst Platform. Choose IBM.MobileFirstPlatform.8.0.0.0.

    ![Add-Nuget-tosolution-search](Add-Nuget-tosolution1.png)

    ![Add-Nuget-tosolution-choose](Add-Nuget-tosolution2.png)

4. Click Install. This installs the IBM MobileFirstPlatform Native SDK and its dependencies.

## Updating the MobileFirst Native SDK
To update the MobileFirst Native SDK with the latest release, run the following command from the root folder of the Visual Studio project in a **Command-line** window:

```bash
Nuget update
```

## Generated MobileFirst Native SDK artifacts

### mfpclient.resw
Located at the root of the project, this file contains server connectivity properties and is user-editable:

- `protocol` – The communication protocol to MobileFirst Server. Either `HTTP` or `HTTPS`.
- `WlAppId` - The identifier of the application. This should be same as the Application identifier in the server.
- `host` – The hostname of the MobileFirst Server instance.
- `port` – The port of the MobileFirst Server instance.
- `wlServerContext` – The context root path of the application on the MobileFirst Server instance.
- `languagePreference` - Sets the default language for client sdk system messages

In Visual Studio, open the **Properties** window of the `mfpclient.resw` file and set the **Copy to Output Directory** option to **Copy always**.

Add the following capabilities to the `Package.appxmanifest`:

- Internet (Client &amp; Server)
- Private Networks (Client &amp; Server)

## Tutorials to follow next
With the MobileFirst Native SDK now integrated, you can now:

- Review the [Adapters development tutorials](../../adapters/)
- Review the [Authentication and security tutorials](../../authentication-and-security/)
- Review the [Notifications tutorials](../../notifications/)
- Review [All Tutorials](../../all-tutorials)