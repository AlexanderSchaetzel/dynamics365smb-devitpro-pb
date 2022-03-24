---
title: "XmlAttribute.CreateNamespaceDeclaration(String, String) Method"
description: "Creates an attribute that represents a namespace declaration."
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
# XmlAttribute.CreateNamespaceDeclaration(String, String) Method
> **Version**: _Available or changed with runtime version 1.0._

Creates an attribute that represents a namespace declaration.


## Syntax
```AL
XmlAttribute :=   XmlAttribute.CreateNamespaceDeclaration(Prefix: String, NamespaceUri: String)
```
## Parameters
*Prefix*  
&emsp;Type: [String](/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)  
The prefix of the attribute (if any).
        
*NamespaceUri*  
&emsp;Type: [String](/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)  
The URI of the attribute. If the prefix is xmlns, then this parameter must be http://www.w3.org/2000/xmlns/; otherwise an exception is thrown.  


## Return Value
*XmlAttribute*  
&emsp;Type: [XmlAttribute](xmlattribute-data-type.md)  
The created XmlAttribute node.


[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlAttribute Data Type](xmlattribute-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)