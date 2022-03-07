---
title: "XmlAttributeCollection.Remove(String, String) Method"
description: "Removes the specified attribute from the collection."
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
# XmlAttributeCollection.Remove(String, String) Method
> **Version**: _Available or changed with runtime version 1.0._

Removes the specified attribute from the collection.


## Syntax
```AL
 XmlAttributeCollection.Remove(LocalName: String, NamespaceUri: String)
```
## Parameters
*XmlAttributeCollection*  
&emsp;Type: [XmlAttributeCollection](xmlattributecollection-data-type.md)  
An instance of the [XmlAttributeCollection](xmlattributecollection-data-type.md) data type.  

*LocalName*  
&emsp;Type: [String](/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)  
The local name of the attribute to remove.
        
*NamespaceUri*  
&emsp;Type: [String](/dynamics365/business-central/dev-itpro/developer/methods-auto/text/text-data-type)  
The namespace URI of the attribute to remove.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlAttributeCollection Data Type](xmlattributecollection-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)