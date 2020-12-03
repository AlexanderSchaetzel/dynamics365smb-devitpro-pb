---
title: "Technical Validation Checklist"
description: Describing the steps you must go through to successfully submit your app to AppSource using AppSourceCop.
author: SusanneWindfeldPedersen
ms.custom: na
ms.date: 11/13/2020
ms.reviewer: solsen
ms.suite: na
ms.topic: article
ms.service: "dynamics365-business-central"
ms.author: freddyk
---

# Technical Validation

Below you will find a checklist of all requirements that you **must meet before submitting** an extension for validation. You will also find a description of how the Business Central Validation is performing technical and manual validation and how you can implement a validation pipeline to perform the same technical validation yourself.

## Technical Validation Checklist

If you do not meet these mandatory requirements, your extension will fail validation. To get code validation helping you bring your extension package to AppSource, you can enable the **AppSourceCop** code analyzer. For more information, see [Using the Code Analysis Tool](devenv-using-code-analysis-tool.md).

|Requirement|Example/Guidance|
|-----------|----------------|
|Develop your extension in Visual Studio Code.|[Developing [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)]s](devenv-dev-overview.md)|
|The app.json file has mandatory settings that you must include. Here you can also read more about dependency syntax and multiple countries per a single app syntax.|[Mandatory app.json settings](devenv-json-files.md)|
|Coding of `Date` must follow a specific format (**no longer region-specific**)|Use the format `yyyymmddD`. For example, `20170825D`.|
|Remote services (including all Web services calls) can use either HTTP or HTTPS. However, HTTP calls are only possible by using the HttpRequest AL type.|[Guidance on HTTP use](devenv-restapi-overview.md)|
|Only JavaScript based Web client add-ins are supported. The zipping process is handled automatically by the compiler. Simply include the new AL `controladdin` type, JavaScript sources, and build the app.|[Control Add-Ins](devenv-control-addin-object.md)|
|The .app file must be digitally signed.|[Signing an APP Package File](devenv-sign-extension.md)|
|The user scenario document must contain detailed steps for all setup and user validation testing.|[User Scenario Documentation](../compliance/apptest-userscenario.md)|
|Set the application areas that apply to your controls. Failure to do so will result in the control not appearing in [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)].|[Application Area guidance](properties/devenv-applicationarea-property.md)|
|Permission set(s) must be created by your extension and when marked, should give the user all setup and usage abilities. A user must not be required to have SUPER permissions for setup and usage of your extension.|[Exporting Permission Sets](devenv-export-permission-sets.md)<br>[Managing Users and Permissions](/dynamics365/business-central/ui-how-users-permissions)|
|Before submitting for validation, ensure that you can publish/sync/install/uninstall/reinstall your extension. **This must be done in a [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] environment**.|[How to publish your app](devenv-how-publish-and-install-an-extension-v2.md)|
|Thoroughly test your extension in a [!INCLUDE[d365fin_long_md](includes/d365fin_long_md.md)] environment.|[Testing Your Extension](../compliance/apptest-testingyourextension.md)|
|Do not use `OnBeforeCompanyOpen` or `OnAfterCompanyOpen`|[Replacement Options](../compliance/apptest-onbeforecompanyopen.md)|
|Include the proper upgrade code allowing your app to successfully upgrade from version to version.|[Upgrading Extensions](devenv-upgrading-extensions.md)|
|Pages and code units that are designed to be exposed as Web services must not generate any UI that would cause an exception in the calling code.|[Web Services Usage](../compliance/apptest-webservices.md)|
|You are required to prefix or suffix the **Name** of your fields and objects. This eliminates collision between apps.|[Prefix/Suffix Guidelines](../compliance/apptest-prefix-suffix.md)|
|You are required to include a Visual Studio Code test package with your extension. Ensure that you include as much code coverage as you can.|[Testing the Advanced Sample Extension](devenv-extension-advanced-example-test.md)|
|DataClassification is required for fields of all tables/table extensions. Property must be set to other than `ToBeClassified`.|[Classifying Data](devenv-classifying-data.md)|
|You must use the Profile object to add profiles instead of inserting them into the **Profiles** table.|[Profile Object](devenv-profile-object.md)|
|Use `addfirst` and `addlast` for placing your actions on Business Central pages. This eliminates breaking your app due to Business Central core changes.|[Placing Actions and Controls](devenv-page-ext-object.md#using-keywords-to-place-actions-and-controls)|

<!-- 
|Permission set(s) must be created by your extension and when marked, should give the user all setup and usage abilities. A user must not be required to have SUPER permissions for setup and usage of your extension.|[Packaging the Permission Set](/powershell/module/microsoft.dynamics.nav.apps.tools/new-navapppackage?view=dynamicsnav-ps-2017)| , [How to: Export Permission Sets](../How-to-Import-Export-Permission-Sets-Permissions.md) |
-->

## Technical validation performed by the Business Central validation team

The primary responsibility of the technical validation is to ensure that the Business Central online service is stable and that the apps can be installed and run without destabilizing the service.  

The technical validation is for a large part automated and will validate the steps described in the technical checklist above through some pipelines.  

The submitted apps will be extracted and investigated following this list:

1. The apps are investigated. All dependencies must be included in the submission. We will lookup prior versions of the apps in the depot. If your app has a dependency on a third party app in AppSource, you should not include this, we will locate it in the depot. **Any unresolved dependencies will cause the submission to be rejected.**
2. If the version numbers haven't changed and the countries haven’t changed, the validation is skipped and **the apps will not be updated.**
3. App.json is investigated for mandatory fields. **If mandatory fields are missing, the submission is rejected.**
4. Affixes for the submission are located. **If affixes haven't been registered or cannot be located, the submission is rejected.**
5. Business Central Artifacts are located for the version the apps is submitted for (*Current*, *NextMinor*, or *NextMajor*).
6. For every country in the submission list, we perform the same validation:
   - A sandbox container based on the Business Central Artifacts with the right country version is created.
   - Any dependency apps not included in the submission are installed. **If any installation fails, the submission is rejected.**
   - In order of dependencies, all apps in the submission are tested using AppSourceCop analyzer. For more information, see [AppSourceCop Analyzer](analyzers/appsourcecop.md)
     - If any **breaking changes are identified, the submission is rejected.**
     - If mandatory affixes **are not included on all object names, the submission is rejected.**
   - In order of dependencies, all prior versions of the apps are published and installed. **If any installation fails, the submission is rejected.**
   - In order of dependencies, all new versions of the apps are published and upgrade is run (apps must be digitally signed, else they won’t install). **If any installation/upgrade fails, the submission is rejected.**
   - A simple connection test is run; opening a role center and check simple actions and pages. If the connection test fails, **the submission investigated and potentially rejected.**
7. If all country validations succeed and no errors are found then **the submission is accepted.**

> [!Important]  
> Microsoft recommends that all partners are performing the same checks as described above before submitting apps for validation to maximize chances of validation success.
> 
> You can find resources for how to setup a build pipeline, which performs all these steps here: https://aka.ms/cicdhol and you can find sample repositories, performing these steps here:
> -	https://dev.azure.com/businesscentralapps/HelloWorld.AppSource (for Azure DevOps)
> -	https://github.com/BusinessCentralApps/HelloWorld.AppSource (for GitHub Actions)

## Manual validation performed by the Business Central validation team

The primary responsibility of the manual validation is to ensure that the apps are working as described.

Manual validation is not done on all submissions. They will be done as sample tests.

For manual validation, we spin up a container with the right artifacts (same as used during technical validation) and the necessary apps are installed. Rapidstart packages needed for the manual test is installed.

The manual test validation document is executed manually and if the document doesn’t match the app functionality the submission is rejected.

> [!Important]  
> Microsoft recommends that all partners are performing the manual validation as the last check before submitting for validation.
>
> This can be done either in online sandbox environments or in sandbox docker containers.

## See Also
[Developing [!INCLUDE[d365al_ext_md](../includes/d365al_ext_md.md)]s](devenv-dev-overview.md)  
