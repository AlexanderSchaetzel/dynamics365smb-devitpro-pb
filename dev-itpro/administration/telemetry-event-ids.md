---
title: Telemetry Event IDs in Application Insights | Microsoft Docs
description: Learn about the event IDs of Business Central events emitted to Azure Application Insights.  
author: jswymer
ms.topic: conceptual
ms.devlang: na
ms.tgt_pltfrm: na
ms.workload: na
ms.search.keywords: administration, tenant, admin, environment, sandbox, telemetry
ms.date: 05/12/2021
ms.author: jswymer
---
# Telemetry Event IDs in Application Insights

The following tables list the IDs of [!INCLUDE[prod_short](../developer/includes/prod_short.md)] telemetry trace events that can be emitted in Azure Application Insights.

<!--
PartnerDiagnosticsEventSchemaTag.cs-->

## Application events

| Event ID | Area | Message |
|----------|-------------|-----------------|
|AL0000CTV|Email|[Email sent successfully](telemetry-email-trace.md#success)|
| AL0000CTE | Field monitoring  | [Sensitive field value has changed: {alfieldCaption} ({alFieldNumber}) in table {altableCaption} ({alTableNumber})](telemetry-field-monitoring-trace.md#changed) |
|AL0000CTP|Email|[Failed to send email](telemetry-email-trace.md#failed)|
| AL0000DD3 | Field monitoring | [Sensitive field monitor status has changed to {almonitorStatus}](telemetry-field-monitoring-trace.md#status) |
|AL0000EMW|Field monitoring |[Sensitive field added to or removed from monitor: {alfieldCaption} ({alFieldNumber}) in table {alTableCaption} ({alTableNumber})](telemetry-field-monitoring-trace.md#added)|
|AL0000E2A|Permissions|[User-defined permission set added: {alPermissionSetId}](telemetry-permission-changes-trace.md#setadded)|
|AL0000E2B|Permissions|[User-defined permission set removed: {alPermissionSetId}](telemetry-permission-changes-trace.md#setremoved)|
|AL0000E28 |Permissions|[Permission set link added: {alSourcePermissionSetId} -> {alLinkedPermissionSetId}](telemetry-permission-changes-trace.md#linkadded)|
|AL0000E29 |Permissions|[Permission set link removed: {alSourcePermissionSetId} -> {alLinkedPermissionSetId}](telemetry-permission-changes-trace.md#linkremoved)|
|AL0000E2C |Permissions|[Permission set assigned to user: {alPermissionSetId}](telemetry-permission-changes-trace.md#assigneduser)|
|AL0000E2D |Permissions|[Permission set removed from user: {alPermissionSetId}](telemetry-permission-changes-trace.md#removeduser)|
|AL0000E2E |Permissions|[Permission set assigned to user group: {alPermissionSetId}](telemetry-permission-changes-trace.md#assignedusergroup)|
|AL0000E2F |Permissions|[Permission set removed from user group: {alPermissionSetId}](telemetry-permission-changes-trace.md#removedusergroup)|
|AL0000D3L |Retention Policy |[Retention Policy Log Entry Logged: {alMessageType}](telemetry-retention-policy-trace.md#info)|
|AL0000D6H |Retention Policy|[Records Deleted Using Retention Policy: Deleted {alRecordsDeleted} records from Table {alTableNo}, {alTableName}](telemetry-retention-policy-trace.md#deleted)|
|AL0000D6I|Retention Policy|[First retention policy enabled on: {alCompanyName}](telemetry-retention-policy-trace.md#first)|
|AL0000D6J|	Retention Policy|[Last retention policy disabled on: {alCompanyName}](telemetry-retention-policy-trace.md#last)|

## Client events

| Event ID | Area | Message |
|----------|-------------|-----------------|
| CL0001 | Page views | [Page opened: {alObjectName}](telemetry-page-view-trace.md#page-opened-alobjectname) |

## Lifecycle events

| Event ID | Area | Message |
|----------|-------------|-----------------|
| AL0000E24 | Job Queue Lifecycle | [Job queue entry enqueued: {alJobQueueId} ](telemetry-job-queue-lifecycle-trace.md#enqueued) |
| AL0000E25 | Job Queue Lifecycle | [Job queue entry started: {alJobQueueId} ](telemetry-job-queue-lifecycle-trace.md#started) |
| AL0000E26 | Job Queue Lifecycle | [Job queue entry finished: {alJobQueueId} ](telemetry-job-queue-lifecycle-trace.md#finished) |
|AL0000E3F|Configuration Package|[Configuration package export started: {alPackageCode}](telemetry-configuration-package-trace.md#exportstarted)|
|AL0000E3G|Configuration Package|[Configuration package exported successfully: {alPackageCode}](telemetry-configuration-package-trace.md#exportsuccessful)|
|AL0000E3H|Configuration Package|[Configuration package import started: {alPackageCode}](telemetry-configuration-package-trace.md#importstarted)|
|AL0000E3I|Configuration Package|[Configuration package imported successfully: {alPackageCode}](telemetry-configuration-package-trace.md#importsuccessful)|
|AL0000E3N|Configuration Package|[Configuration package apply started: {alPackageCode}](telemetry-configuration-package-trace.md#applystarted)|
|AL0000E3O|Configuration Package|[Configuration package applied successfully: {alPackageCode}](telemetry-configuration-package-trace.md#applysuccessful)|
|AL0000E3P|Configuration Package|[Configuration package deleted successfully: {alPackageCode}](telemetry-configuration-package-trace.md#deletesuccessful)|
| AL0000EJ9 | Extension Lifecycle | [Upgrade tag searched for: {AlUpgradeTag}](telemetry-extension-update-trace.md#upgrade-tag-searched-for) |
| AL0000EJA | Extension Lifecycle | [Upgrade tag set: {AlUpgradeTag}](telemetry-extension-update-trace.md#upgrade-tag-set) |
| LC0001 | Company Lifecycle | [Company created: {companyName}](telemetry-company-lifecycle-trace.md#company-created) |
| LC0002 | Company Lifecycle | [Company creation canceled: {companyName}](telemetry-company-lifecycle-trace.md#company-creation-canceled) |
| LC0003 | Company Lifecycle | [Company creation failed: {companyName}](telemetry-company-lifecycle-trace.md#company-creation-failed) |
| LC0004 | Company Lifecycle | [Company copied: {companyNameSource} to {companyNameDestination}](telemetry-company-lifecycle-trace.md#company-copied) |
| LC0005 | Company Lifecycle | [Company copied canceled: {companyNameSource} to {companyNameDestination}](telemetry-company-lifecycle-trace.md#company-copy-canceled) |
| LC0006 | Company Lifecycle | [Company copy failed: {companyNameSource} to {companyNameDestination}](telemetry-company-lifecycle-trace.md#company-copy-failed) | 
| LC0007 | Company Lifecycle | [Company deleted: {companyName}](telemetry-company-lifecycle-trace.md#company-deleted)| 
| LC0008 | Company Lifecycle | [Company deletion canceled: {companyName}](telemetry-company-lifecycle-trace.md#company-deletion-canceled) | 
| LC0009 | Company Lifecycle | [Company deletion failed: {companyName}](telemetry-company-lifecycle-trace.md#company-deletion-failed) | 
| LC0010 | Extension Lifecycle | [Extension installed successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#installedsuccess) |
| LC0011 | Extension Lifecycle | [Extension failed to install: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#installedfailed) |
| LC0012 | Extension Lifecycle | [Extension synchronized successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId}](telemetry-extension-lifecycle-trace.md#syncedsuccess) |
| LC0013 | Extension Lifecycle | [Extension failed to synchronize: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#syncedfailed) |
| LC0014 | Extension Lifecycle | [Extension published successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#publishedsuccess) |
| LC0015 | Extension Lifecycle | [Extension failed to publish: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#publishedfailed) |
| LC0016 | Extension Lifecycle | [Extension un-installed successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#uninstalledsuccess) |
| LC0017 | Extension Lifecycle | [Extension failed to un-install: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#uninstalledfailed) |
| LC0018 | Extension Lifecycle | [Extension unpublished successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#unpublishedsuccess) |
| LC0019 | Extension Lifecycle | [Extension failed to un-publish: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#unpublishedfailed) |
| LC0020 | Extension Lifecycle | [Extension compiled successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#compiledsuccess) |
| LC0021 | Extension Lifecycle | [Extension failed to compile: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#compiledfailed) |
| LC0022 | Extension Lifecycle | [Extension updated successfully: {extensionName} version {extensionVersion} by {extensionPublisher}](telemetry-extension-lifecycle-trace.md#updatedsuccess) |
| LC0023 | Extension Lifecycle | [Extension failed to update: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#updatedfailed) |
|LC0024|Table Index Lifecycle|[Index enabled: {tableName}](telemetry-table-index-trace.md#enabled)|
|LC0025|Table Index Lifecycle|[Index disabled: {tableName}](telemetry-table-index-trace.md#disabled)|
| LC0026 | Extension Lifecycle | [Dependent Extension installed successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#dependentinstalledsuccess) |
| LC0027 | Extension Lifecycle | [Dependent extension un-installed successfully: {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-extension-lifecycle-trace.md#dependentunistalled) |
| LC0028 | AppSource Submission | [AppSource submission validation request started: {validationRequestId}](telemetry-appsource-submission-validation-trace.md#validationrequeststarted) |
| LC0029 | AppSource Submission | [AppSource submission validation request completed successfully: {validationRequestId}](telemetry-appsource-submission-validation-trace.md#validationrequestcompleted) |
| LC0030 | AppSource Submission | [(Version, country-region) validation started: version {version}, country/region {countryRegion}](telemetry-appsource-submission-validation-trace.md#versioncountrystarted) |
| LC0031 | AppSource Submission | [(Version, country-region) validation completed successfully: version {version}, country/region {countryRegion}](telemetry-appsource-submission-validation-trace.md#versioncountrycompleted) |
| LC0032 | AppSource Submission | [Extension validation started: version {version}, country/region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-appsource-submission-validation-trace.md#extensionvalidationstarted) |
| LC0033 | AppSource Submission | [Extension validation completed successfully: version {version}, country/region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-appsource-submission-validation-trace.md#extensionvalidationcompleted) |
| LC0034 |AppSource Submission | [Validation diagnostic reported: version {version}, country/region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-appsource-submission-validation-trace.md#validationdiagnosticreported) |
|LC0035|AppSource Submission|[AppSource submission validation request completed with failures: {validationRequestId}](telemetry-appsource-submission-validation-trace.md#submissionrequestcompletedwithfailures) |
|LC0036|AppSource Submission|[(Version, country-region) validation completed with failures: version {version}, country-region {countryRegion}](telemetry-appsource-submission-validation-trace.md#versioncountryvalidationcompletedwithfailures) |
| LC0037| AppSource Submission | [Extension validation completed with failures: version {version}, country-region {countryRegion} for extension {extensionName} version {extensionVersion} by {extensionPublisher} ({extensionId})](telemetry-appsource-submission-validation-trace.md#extensionvalidationcompletedwithfailures)  |
|LC0038|AppSource Submission|[Diagnostic reported on AppSource submission validation request: {validationRequestId}](telemetry-appsource-submission-validation-trace.md#submissionrequestdiagnostic)|
| LC0040 |Task Scheduler | [Task {taskId} created: {codeunitObjectId} scheduled to run after {notBefore}. Ready to run: {isReady}](telemetry-task-scheduler-trace.md#task-created) |
| LC0041 | Task Scheduler  | [Task {taskId} ready: {codeunitObjectId} set ready to run after {notBefore}.](telemetry-task-scheduler-trace.md#task-ready) |
| LC0042 | Task Scheduler  | [Task {taskId} removed: {codeunitObjectId}.](telemetry-task-scheduler-trace.md#task-removed) |
| LC0043 | Task Scheduler  | [Task {taskId} main/failure codeunit {codeunitObjectId} completed.](telemetry-task-scheduler-trace.md#task-completed) |
| LC0044 |Task Scheduler  | [Task {taskId} main/failure codeunit {codeunitObjectId} canceled.](telemetry-task-scheduler-trace.md#task-canceled) |
| LC0045 |Task Scheduler  | [Task {taskId} main/failure codeunit {codeunitObjectId} failed.](telemetry-task-scheduler-trace.md#task-failed) |

## Runtime events

| Event ID | Area | Message |
|----------|-------------|-----------------|
| RT0001 | Authorization| [Authorization Failed (Pre Open Company): {failure reason}](telemetry-authorization-trace.md#authorizationfailedpreopencompany) |
| RT0002 | Authorization| [Authorization Failed (Open Company): {failure reason}](telemetry-authorization-trace.md#authorization-failed-open-company) |
| RT0003 | Authorization| [Authorization Succeeded (Pre Open Company)](telemetry-authorization-trace.md#authorizationsucceededpreopencompany) | 
| RT0004 | Authorization| [Authorization Succeeded (Open Company)](telemetry-authorization-trace.md#authorization-succeeded-open-company) |
| RT0005 | Performance | [Operation exceeded time threshold (SQL query)](telemetry-long-running-sql-query-trace.md) |
| RT0006 | Report generation | [Success report generation](telemetry-reports-trace.md#successful-report-generation) |
| RT0006 | Report generation | [Report rendering failed: {report ID} - {report name}](telemetry-reports-trace.md#failed-report-generation) |
| RT0007 | Report generation | [Cancellation report generation](telemetry-reports-trace.md#cancellation-report-generation) | 
| RT0008 | Incoming Web service requests | [Web service called ({category of request}): {endpoint}](telemetry-webservices-trace.md) |
|RT0010|Extension lifecycle|[Extension Update Failed: exception raised in extension {extensionName} by {extensionPublisher} (updating to version {extensionTargetedVersion})](telemetry-extension-update-trace.md#extension-update-failed-exception-raised-in-extension) |
| RT0011 | Report generation | [Report cancelled but a commit occurred](telemetry-reports-trace.md#commit) | 
| RT0012 | Performance | [Database lock timed out](telemetry-database-locks-trace.md#database-lock-timed-out) | 
| RT0013 | Performance | [Database lock snapshot: {snapshotId}](telemetry-database-locks-trace.md#database-lock-snapshot) |
| RT0014 | Security | [App Key Vault initialization succeeded: '{keyVaultUri}'](telemetry-extension-key-vault-trace.md#initializedsuccess) |
| RT0015 | Security | [App Key Vault initialization failed](telemetry-extension-key-vault-trace.md#initializedfailed) |
| RT0016 | Security | [App Key Vault secret retrieval succeeded from key vault '{keyVaultUri}'](telemetry-extension-key-vault-trace.md#retrievedsuccess) |
| RT0017 | Security | [App Key Vault secret retrieval failed from key vault: '{keyVaultUri}'](telemetry-extension-key-vault-trace.md#retrievedfailed) |
| RT0018 | Performance | [Operation exceeded time threshold (AL method)](telemetry-al-method-trace.md) |
| RT0019 | Outgoing Web service requests  | [Web Service Called (Outgoing): {endpoint}](telemetry-webservices-outgoing-trace.md) |
| RT0020 | Web service key request| [Authentication with Web Service Key succeeded: {endpoint}](telemetry-webservices-access-key-trace.md#succeeded) |
| RT0021 | Web service key request| [Authentication with Web Service Key failed: {endpoint}](telemetry-webservices-access-key-trace.md#failed) |

## See also

[Monitoring and Analyzing Telemetry](telemetry-overview.md)  
[Enable Sending Telemetry to Application Insights](telemetry-enable-application-insights.md)  
