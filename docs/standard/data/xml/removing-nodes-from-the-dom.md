---
title: "從 DOM 移除節點 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-standard"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
ms.assetid: 0a98e0ca-0555-45c1-ab69-0d8d20ca1abd
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 從 DOM 移除節點
若要從 XML 文件物件模型 \(DOM\) 移除節點，請使用 <xref:System.Xml.XmlNode.RemoveChild%2A> 方法移除特定的節點。  換言之，如果節點不是分葉節點，則在移除節點時，該方法會移除屬於要移除之節點的子樹狀目錄。  
  
 從 DOM 移除多個節點時，可視需要使用 <xref:System.Xml.XmlNode.RemoveAll%2A> 方法，移除目前節點的所有子節點及屬性。  
  
 如果您正使用 <xref:System.Xml.XmlNamedNodeMap>，則可使用 <xref:System.Xml.XmlNamedNodeMap.RemoveNamedItem%2A> 方法移除節點。  
  
 若要移除屬性，請參閱[移除 DOM 中項目節點的屬性](../../../../docs/standard/data/xml/removing-attributes-from-an-element-node-in-the-dom.md)。  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)