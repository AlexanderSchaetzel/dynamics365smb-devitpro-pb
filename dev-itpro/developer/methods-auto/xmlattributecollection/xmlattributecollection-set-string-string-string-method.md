---
title: "XmlAttributeCollection.Set(String, String, String) Method"
description: "Sets the value of the specified attribute or creates it if is not part of the collection."
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
# XmlAttributeCollection.Set(String, String, String) Method
> **Version**: _Available or changed with runtime version 1.0._

Sets the value of the specified attribute or creates it if is not part of the collection.


## Syntax
```AL
 XmlAttributeCollection.Set(LocalName: String, NamespaceUri: String, Value: String)
```
## Parameters
*XmlAttributeCollection*  
&emsp;Type: [XmlAttributeCollection](xmlattributecollection-data-type.md)  
An instance of the [XmlAttributeCollection](xmlattributecollection-data-type.md) data type.  

*LocalName*  
&emsp;Type: [String](../string/string-data-type.md)  
The local name of the attribute to set.
        
*NamespaceUri*  
&emsp;Type: [String](../string/string-data-type.md)  
The namespace URI of the attribute to set.
        
*Value*  
&emsp;Type: [String](../string/string-data-type.md)  
The value to set for the attribute.  



[//]: # (IMPORTANT: END>DO_NOT_EDIT)
## See Also
[XmlAttributeCollection Data Type](xmlattributecollection-data-type.md)  
[Getting Started with AL](../../devenv-get-started.md)  
[Developing Extensions](../../devenv-dev-overview.md)