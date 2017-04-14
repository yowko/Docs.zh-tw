---
title: "移除 DOM 中的節點內容 | Microsoft Docs"
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
ms.assetid: 615d81a7-f44f-416c-a9ab-bfe03f85e6e4
caps.latest.revision: 3
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 3
---
# 移除 DOM 中的節點內容
針對繼承自 <xref:System.Xml.XmlCharacterData> 的 <xref:System.Xml.XmlComment>、<xref:System.Xml.XmlText>、<xref:System.Xml.XmlCDataSection>、<xref:System.Xml.XmlWhitespace> 及 <xref:System.Xml.XmlSignificantWhitespace> 節點型別，您可使用 <xref:System.Xml.XmlCharacterData.DeleteData%2A> 方法移除字元，該方法會移除節點中的字元範圍。  若要完全移除內容，可以移除包含內容的節點。  若要保留內容不正確的節點，應修改該節點的內容。  如需修改節點內容的詳細資訊，請參閱[修改 XML 文件中的節點、內容和值](../../../../docs/standard/data/xml/modifying-nodes-content-and-values-in-an-xml-document.md)。  
  
## 請參閱  
 [XML 文件物件模型 \(DOM\)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)