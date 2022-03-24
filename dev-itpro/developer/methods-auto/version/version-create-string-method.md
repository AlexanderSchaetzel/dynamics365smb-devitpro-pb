---
title: "Version.Create(String) Method"
description: "Creates a version object from the provided string."
ms.author: solsen
ms.custom: na
ms.date: 07/07/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Version.Create(String) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates a version object from the provided string. The string should be in the format W.X.Y.Z, where W, X, Y and Z represent positive integers and where Y and Z are optional. If the input string is not in the expected format, an exception is thrown.


## Syntax
```AL
Value :=   Version.Create(Version: String)
```
## Parameters
*Version*  
&emsp;Type: [String](/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)  
The string to convert into a version object.  


## Return Value
*Value*  
&emsp;Type: [Version](version-data-type.md)  
The version created from the provided string.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Version Data Type](version-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)