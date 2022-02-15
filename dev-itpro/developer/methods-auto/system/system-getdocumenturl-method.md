---
title: "System.GetDocumentUrl(Guid) Method"
description: "Gets the URL for the specified temporary media object ID."
ms.author: solsen
ms.custom: na
ms.date: 11/05/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# System.GetDocumentUrl(Guid) Method
> **Version**: _Available or changed with runtime version 1.0._

Gets the URL for the specified temporary media object ID.

> [!NOTE]
> This method is supported only in Business Central on-premises.

## Syntax
```AL
Url :=   System.GetDocumentUrl(ID: Guid)
```
> [!NOTE]
> This method can be invoked without specifying the data type name.
## Parameters
*ID*  
&emsp;Type: [Guid](../guid/guid-data-type.md)  
The temporary media object ID.  


## Return Value
*Url*  
&emsp;Type: [String](../string/string-data-type.md)  
The URL for the specified temporary media object ID.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[System Data Type](system-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)