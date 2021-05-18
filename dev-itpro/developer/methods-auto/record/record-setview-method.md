---
title: "Record.SetView Method"
description: "Sets the current sort order, key, and filters on a table."
ms.author: solsen
ms.custom: na
ms.date: 05/11/2021
ms.reviewer: na
ms.suite: na
ms.tgt_pltfrm: na
ms.topic: reference
ms.service: "dynamics365-business-central"
author: SusanneWindfeldPedersen
---
[//]: # (START>DO_NOT_EDIT)
[//]: # (IMPORTANT:Do not edit any of the content between here and the END>DO_NOT_EDIT.)
[//]: # (Any modifications should be made in the .xml files in the ModernDev repo.)
# Record.SetView Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the current sort order, key, and filters on a table.


## Syntax
```
 Record.SetView(String: String)
```
## Parameters
*Record*  
&emsp;Type: [Record](record-data-type.md)  
An instance of the [Record](record-data-type.md) data type.

*String*  
&emsp;Type: [String](../string/string-data-type.md)  
A string that contains the sort order, key, and filter to set. The string format is the same as the SourceTableView Property on pages.
          



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[Record Data Type](record-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)