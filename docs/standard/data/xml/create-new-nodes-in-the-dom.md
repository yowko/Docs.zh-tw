---
title: "在 DOM 中建立新節點 | Microsoft Docs"
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
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
caps.latest.revision: 4
author: "mairaw"
ms.author: "mairaw"
manager: "wpickett"
caps.handback.revision: 4
---
# 在 DOM 中建立新節點
<xref:System.Xml.XmlDocument>有所有的節點型別建立方法。 必要時請為該方法提供名稱，並針對具有內容的節點 (例如，文字節點) 提供內容或其他參數，即可建立節點。 下列方法需要填入名稱及一些其他參數來建立適當的節點。  
  
-   <xref:System.Xml.XmlDocument.CreateCDataSection%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateComment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentFragment%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateDocumentType%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateElement%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateProcessingInstruction%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateSignificantWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateTextNode%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateWhitespace%2A>  
  
-   <xref:System.Xml.XmlDocument.CreateXmlDeclaration%2A>  
  
 其他節點型別除了需為參數提供資料以外，還有更多需求。  
  
 如需屬性的資訊，請參閱[的 DOM 中的項目建立新屬性](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md)。 在項目和屬性名稱驗證的資訊，請參閱[XML 項目和屬性名稱的驗證時建立新的節點](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md)。 建立實體參考，請參閱[建立新實體參考](../../../../docs/standard/data/xml/creating-new-entity-references.md)。 如需命名空間如何影響實體參考擴充的資訊，請參閱[實體參考擴充的新節點包含項目和屬性的命名空間會影響](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md)。  
  
 一旦建立新節點，即有數個方法可用來將其插入樹狀。 該表格會列出這些方法，並說明新節點在 XML 文件物件模型 (DOM) 中會出現於何處。  
  
|方法|節點取代|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|在參考節點之前插入。 例如，若要在位置 5 插入新節點：<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> 如需詳細資訊，請參閱<xref:System.Xml.XmlNode.InsertBefore%2A>方法。|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|在參考節點之後插入。 例如：<br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> 如需詳細資訊，請參閱<xref:System.Xml.XmlNode.InsertAfter%2A>方法。|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|將節點加入至指定節點之子節點的清單結尾處。 如果加入的節點是<xref:System.Xml.XmlDocumentFragment>，文件片段的全部內容都會移到這個節點的子清單。 如需詳細資訊，請參閱<xref:System.Xml.XmlNode.AppendChild%2A>方法。|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|將節點加入至指定節點之子節點的清單開頭。 如果加入的節點是<xref:System.Xml.XmlDocumentFragment>，文件片段的全部內容都會移到這個節點的子清單。 如需詳細資訊，請參閱<xref:System.Xml.XmlNode.PrependChild%2A>方法。|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|將附加<xref:System.Xml.XmlAttribute>節點的項目相關聯的屬性集合的結尾。 如需詳細資訊，請參閱<xref:System.Xml.XmlAttributeCollection.Append%2A>方法。|  
  
## <a name="see-also"></a>另請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)