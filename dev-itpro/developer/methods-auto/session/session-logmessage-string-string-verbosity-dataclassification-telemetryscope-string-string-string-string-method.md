---
title: "Session.LogMessage(String, String, Verbosity, DataClassification, TelemetryScope, String, String [, String] [, String]) Method"
description: "Logs a trace message to a telemetry account."
ms.author: solsen
ms.custom: na
ms.date: 03/17/2022
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Session.LogMessage(String, String, Verbosity, DataClassification, TelemetryScope, String, String [, String] [, String]) Method
> **Version**: _Available or changed with runtime version 5.4._

Logs a trace message to a telemetry account.


## Syntax
```AL
 Session.LogMessage(EventId: String, Message: String, Verbosity: Verbosity, DataClassification: DataClassification, TelemetryScope: TelemetryScope, Dimension1: String, Value1: String [, Dimension2: String] [, Value2: String])
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*EventId*  
&emsp;Type: [String](../text/text-data-type.md)  
The event ID of trace message.   

*Message*  
&emsp;Type: [String](../text/text-data-type.md)  
The message logged into telemetry.   

*Verbosity*  
&emsp;Type: [Verbosity](../verbosity/verbosity-option.md)  
The verbosity of the log.   

*DataClassification*  
&emsp;Type: [DataClassification](../dataclassification/dataclassification-option.md)  
Classification of data in message.   

*TelemetryScope*  
&emsp;Type: [TelemetryScope](../telemetryscope/telemetryscope-option.md)  
Specifies the scope of this trace message:
- ExtensionPublisher: Will emit this trace message to the Extension Publisher's telemetry account.
- All: Will emit this trace message additionally to the Partner's telemetry account.   

*Dimension1*  
&emsp;Type: [String](../text/text-data-type.md)  
Additional dimension that will be emitted to the telemetry account and that can be used to specify filters in the query.   

*Value1*  
&emsp;Type: [String](../text/text-data-type.md)  
The value of Dimension1.   

*[Optional] Dimension2*  
&emsp;Type: [String](../text/text-data-type.md)  
Additional dimension that will be emitted to the telemetry account and that can be used to specify filters in the query.   

*[Optional] Value2*  
&emsp;Type: [String](../text/text-data-type.md)  
The value of Dimension2.   



[//]: # (IMPORTANT: END>DO_NOT_EDIT)

## Remarks

For more information about using this method, see [Creating Custom Telemetry Events for Application Insights](../../devenv-instrument-application-for-telemetry-app-insights.md).

## Example

```al
trigger OnRun();
begin
    LogMessage('MyExt-0001', 'This is a critical error message', Verbosity::Critical, DataClassification::CustomerContent, TelemetryScope::ExtensionPublisher, 'result', 'failed', 'reason', 'critical error in code');
end;
```
## See Also
[Session Data Type](session-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)