---
title: "Deprecated Features in W1"
description: describes the features that have been moved, removed, or replaced in the W1 version 
author: bholtorf
ms.custom: na
ms.date: 04/01/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: conceptual
ms.service: "dynamics365-business-central"
---

# Deprecated Features in W1

This article describes the features that have been moved, removed, or replaced in the W1 version of [!INCLUDE[prod_short](../developer/includes/prod_short.md)].  

[!INCLUDE [feature-deprecation](../includes/feature-deprecation.md)]

## Changes in 2022 release wave 1

### .NET add-ins not using .NET Standard (Removal)

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Replaced| .NET Framework has been superseded by .NET Standard. .NET add-ins compiled with .NET Framework won't work in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1. |


### <a name="accesskeys"></a>Web Service Access Keys (Basic Auth) for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] Online

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed (for SaaS only)| The capability to access web services in [!INCLUDE[prod_short](../developer/includes/prod_short.md)] using Web Service Access Key (Basic Auth) is deprecated for SaaS. OAuth2 will be the authentication option for SaaS. OAuth samples are published in the [BCTech repo](https://github.com/microsoft/BCTech/tree/master/samples/PSOAuthBCAccess). For on-premises, Web Service Access Key (Basic Auth) will remain an option for the time being. This change has no impact on how [!INCLUDE[prod_short](../developer/includes/prod_short.md)] connects to external services.|

### <a name="permissions"></a>Permissions defined as data

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2022 release wave 1.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed | With releases of [!INCLUDE [prod_short](../developer/includes/prod_short.md)] prior to 2021 release wave 1 (v.18.0), System and Extension permissions and entitlements were defined as data in the application database. This has changed with [!INCLUDE [prod_short](../developer/includes/prod_short.md)] v.18.0. With [!INCLUDE [prod_short](../developer/includes/prod_short.md)] 2022 release wave 1, the support for defining permissions and entitlements as data in the application database will be removed. For more information, see [Entitlements and Permissions Overview](../developer/devenv-entitlements-and-permissionsets-overview.md).|

## Changes in 2021 release wave 2

### Business Central app for Windows

The Business Central app that's available from the [Microsoft Store](https://go.microsoft.com/fwlink/?LinkId=734848) is no longer supported with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Replaced| The legacy app for Windows was based on Universal Windows Platform (UWP). In it's place, we offer an app that's based on Progressive Web Application (PWA) technology, which is a more modern technology that provides a better user experience going forward. The legacy app will still be available on the Windows Store for users running Business Central 2021 release wave 1 or earlier.|

### Removal of the Business Central Server Administration tool (Warning)

The following feature will be **Removed** in a later release.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed | The Business Central Server Administration tool for configuring the [!INCLUDE[server](../developer/includes/server.md)] in on-premises installations will be removed in a later release. Please transition to using the provided Powershell cmdlets in the [!INCLUDE[adminshell](../developer/includes/adminshell.md)] instead. |

### StartSession calls in upgrade/install context will fail

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2.

|Moved, Removed, or Replaced? |    Why?|
|-----------------------------|-----|
|Removed | A new session created with AL StartSession has no link to the session that created it. This implementation can cause problems, for example, in cases where the creating session is an upgrade codeunit. If an error occurs later in the process, which requires a rollback, the server can't roll back any transactions done in the session created by the AL StartSession. This condition can leave data in the system in a bad state. Starting with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2, any StartSession call in upgrade/install context will fail immediately. |

### Standard APIs, Beta version

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2.

|Moved, Removed, or Replaced? |    Why?|
|-----------------------------|-----|
|Removed | Beta version of the standard APIs will be removed by 2021 release wave 2. At this point, Beta APIs won't be available in new releases of [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. There are many improvements to v1.0 and v2.0 of the standard APIs. Improvements include more APIs, better performance and improved OData capabilities. It's recommended that integrations move to v2.0 of the standard APIs.|

### Automation APIs, Beta version

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2.


|Moved, Removed, or Replaced?|    Why?|
|----------------------------|------|
|Removed | Beta version of the Automation APIs will be removed by 2021 release wave 2. At this point, Automation Beta APIs won't be available in new releases of [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. It's recommended that integrations move to v2.0 of the Automation APIs.|

### Client secret authentication in integrations between Microsoft-hosted Business Central online and Microsoft Dataverse

The following feature will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed | The ability to connect [!INCLUDE[prod_short](../developer/includes/prod_short.md)] with Dataverse using the client secret Service-to-Service authentication will be removed for online tenants hosted by Microsoft in March, 2022. To further strengthen security, we introduced the ability to use certificate-based authentication in Business Central 2021 release wave 1 (version 18 and later). Existing users can easily switch to certificate-based authentication. For more information, see [Upgrade Connections from Business Central Online to Use Certificate-Based Authentication](https://go.microsoft.com/fwlink/?linkid=2167233). On-premises customers, and online tenants that are hosted by ISVs, can continue using client secret authentication for their connections to Dataverse.|

### Legacy Outlook add-in for synchronizing data

The legacy Outlook add-in for synchronizing data, such as to-dos, contacts, and tasks, between Business Central and Outlook will be **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 2.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed | This add-in used Business Central web services based on outdated technology.|

> [!NOTE]
> The feature is separate from and has no affect on the [!INCLUDE[prod_short](../developer/includes/prod_short.md)]add-in for Outlook, which is described at [Using Business Central as your Business Inbox in Outlook](/dynamics365/business-central/work-outlook-addin).

## Changes in 2021 release wave 1

### .NET add-ins not using .NET Standard (Warning)

In [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1, a warning shows if you include .NET add-ins that are compiled with .NET Framework and not with .NET Standard. The capability of using .NET add-ins compiled with .NET Framework will be removed in a later release.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Replaced | .NET Framework has been superseded by .NET Standard. .NET add-ins compiled with .NET Framework is deprecated as of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1, but the feature won't be removed in this release. It's recommended that .NET add-ins are migrated to .NET Standard as soon as possible.|


### Expose UI pages as SOAP endpoints (Warning)

In [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1, a warning shows if you expose UI pages as SOAP endpoints. The capability of exposing UI pages as SOAP endpoints will be removed in a later release.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Replaced | SOAP has been superseded by OData V4. SOAP endpoints are deprecated as of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1, but the feature won't be removed in this release. It's recommended that integrations are migrated to OData V4 as soon as possible.|

### OData V3

The following feature is **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed | OData V3 has been superseded by OData v4. OData V3 is deprecated, and is removed as of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1. It's recommended that integrations are migrated to OData v4 as soon as possible.  |

### The Help Server component

The following component is **Removed** with [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed |In 2021 release wave 1, the Help Server component is removed from the product media for deployment on-premises. If a customer is on a version between Dynamics NAV 2016 and [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2020 release wave 2 on-premises, and they rely on Help Server to provide access to Help, then nothing changes. When they upgrade to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] 2021 release wave 1, they must host their custom Help on another type of website. We recommend that new solutions do not rely on the Help Server component due to the deprecation. The [custom help toolkit](../help/custom-help-toolkit.md) can help deploy content to any website, for example. |

#### What does this mean?

<!--BDM-->
We have simplified the story for how to deploy Help for a customer-specific solution of [!INCLUDE[prod_short](../developer/includes/prod_short.md)], and for deploying Help for an AppSource app. No matter what your solution is, deploy your solution-specific or customized Help to any website that you prefer. Out of the box, [!INCLUDE[prod_short](../developer/includes/prod_short.md)] uses the [Docs.microsoft.com](/dynamics365/business-central/) site for the Learn more-links and contextual Help. Each customer and each partner can override this with their own Help. It's now the same for [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online and on-premises, so any investment on-premises carries forward if you migrate to [!INCLUDE[prod_short](../developer/includes/prod_short.md)] online.

## Deprecated Features in 2020 release wave 1
The following feature was marked as `obsolete:pending` in 2020 release wave 1.

### Best Price Calculations
When you have recorded special prices and line discounts for sales and purchases, Business Central ensures that your profit on item trade is always optimal by automatically calculating the best price on sales and purchase documents and on job and item journal lines.

|Moved, Removed, or Replaced?|Why?|
|----|----|
|Replaced|The functionality is replaced with new calculations that you can extend to include additional sources or calculation methods. The current capabilities will be available, and can be used in parallel with the new, until 2021 release wave 1. For more information, see [Extending Best Price Calculations](../developer/devenv-extending-best-price-calculations.md).|

## Deprecated Features in 2019 release wave 2
The following sections describe the features that were deprecated in 2019 release wave 2.

### The Bank Data Conversion Service
You can use the bank data conversion service from AMC to convert bank data from an XML file that you export from [!INCLUDE[prod_short](../developer/includes/prod_short.md)] into a format that your bank can accept.

|Moved, Removed, or Replaced?|Why?|
|----|----|
|Moved|The functionality has been moved to an extension. It now ships as the AMC Banking 365 Fundamentals extension, which can convert bank data to formats that are used by more than 600 banks worldwide. For more information, see [Using the AMC Banking 365 Fundamentals extension](/dynamics365/business-central/ui-extensions-amc-banking).|

### The Windows Client
You can use [!INCLUDE[prod_short](../developer/includes/prod_short.md)] in the Windows client that is installed on your computer.

|Moved, Removed, or Replaced?|Why?|
|----|----|
|Removed| Business Central continues to evolve the modern client experiences where users work with Business Central in the browser, Windows 10 desktop app, or mobile apps on Android and iOS. The legacy Dynamics NAV Windows client is no longer available for deployment. Instead, users can switch to the modern experience in the browser, the Android/iOS mobile apps, or the Windows 10 desktop app (available through the respective stores). |

### Reports 204-207
You can generate external-facing documents, such as sales invoices and order confirmations, that you send to customers as PDF files.

The reports in the 204-207 range are replaced by the following updated reports in the 1304 to 1307 range:

- 204, Sales-Quote -> 1304, Standard Sales-Quote
- 205, Order-Confirmation -> 1305, Standard Sales-Order Conf.
- 206, Sales-Invoice -> 1306, Standard Sales-Invoice
- 207, Credit-Memo -> 1307, Standard Sales-Credit Memo

> [!NOTE]
> The **No. of Copies** field is removed from the new reports because of performance reasons and because selection of the quantity to print works differently on modern printers. To print a report more than once, users can list the same report multiple times on the **Report Selection** page for the document type in question.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Replaced|The reports in the 204-207 range are replaced by the reports in the 1304 to 1307 range. To avoid duplicated features, the reports in the 204-207 range will be removed.|
<!--This is just stubbed in. Need the actual names of the reports and a better description of the information they provided.-->

### User Personalizations and Profile Configurations
You can personalize pages and configure profiles by adding or removing fields, and [!INCLUDE[prod_short](../developer/includes/prod_short.md)] will save your changes.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Replaced|The shift to AL caused the legacy personalization and profile configuration features to become outdated, so we have introduced new tooling. In this release, existing personalizations and configurations are discarded, and you must use the new tools to recreate them. Your new changes will be kept in future releases.|

### Excel COM Add-In
You can export data to an Excel workbook.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed| The Excel COM add-in was installed along with the Windows client. Now that the Windows Client is no longer available, neither is the add-in. To export data to Excel, use the **Edit in Excel** action.|

### Printing Programmatically
You can print documents such as invoices automatically, without prompting the user or without the user choosing to do so.

|Moved, Removed, or Replaced? |Why?|
|---------|---------|
|Removed| This feature was tied to the Windows Client, which is no longer available. |

## Objects that have been marked as obsolete
Part of deprecating features is marking the objects that comprise them as "obsolete." Before we deprecate an object, we tag it as "obsolete:pending" to alert our partners of it's deprecation. The object will have the tag for one year before we remove it from [!INCLUDE[prod_short](../developer/includes/prod_short.md)].
<!--should probably mention the other tags too. For example, "after one year we will mark the object as "ObsoleteState:Removed."-->

## Breaking Changes
When we move, remove, or replace an object, breaking changes can result in other apps or extensions that use the object. To help our partners identify and resolve breaking changes, we have created a [Breaking Changes](https://github.com/microsoft/ALAppExtensions/blob/master/BREAKINGCHANGES.md) document that lists known issues and suggestions for what to do about them.

## Features that are available only in the online version
<!--Should we include a section about this?-->
Some features are available only under very specific circumstances, or not at all intended for use in on-premises versions of [!INCLUDE[prod_short](../developer/includes/prod_short.md)]. For a list and descriptions of those features, see [Features not implemented in on-premises deployments](../features-not-implemented-on-premises.md).

## See Also

[AlAppExtensions repository](https://github.com/microsoft/ALAppExtensions)  
[Best Practices for Deprecation of Code in the Base App](../developer/devenv-deprecation-guidelines.md)  
[Microsoft Timeline for Deprecating Code in Business Central](../developer/devenv-deprecation-timeline.md)  
