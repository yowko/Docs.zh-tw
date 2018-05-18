---
title: 在 DOM 中建立新節點
ms.date: 03/30/2017
ms.technology: dotnet-standard
ms.assetid: 6c2b9789-b61a-49f9-b33f-db01a945edf2
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bbc8d6c1055afc1a0799522f341551d04bab4ace
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="create-new-nodes-in-the-dom"></a>在 DOM 中建立新節點
<xref:System.Xml.XmlDocument> 有一個適用於所有節點型別的建立方法。 必要時請為該方法提供名稱，並針對具有內容的節點 (例如，文字節點) 提供內容或其他參數，即可建立節點。 下列方法需要填入名稱及一些其他參數來建立適當的節點。  
  
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
  
 如需屬性的詳細資訊，請參閱[為 DOM 中的項目建立新屬性](../../../../docs/standard/data/xml/creating-new-attributes-for-elements-in-the-dom.md)。 如需項目及屬性名稱驗證的詳細資訊，請參閱[建立新節點時的 XML 項目和屬性名稱驗證](../../../../docs/standard/data/xml/xml-element-and-attribute-name-verification-when-creating-new-nodes.md)。 若要建立實體參考，請參閱[建立新實體參考](../../../../docs/standard/data/xml/creating-new-entity-references.md)。 如需命名空間如何影響實體參考之擴充的詳細資訊，請參閱[命名空間對包含項目和屬性的新節點之實體參考擴充的影響](../../../../docs/standard/data/xml/namespace-affect-on-entity-ref-expansion-for-new-nodes.md)。  
  
 一旦建立新節點，即有數個方法可用來將其插入樹狀。 該表格會列出這些方法，並說明新節點在 XML 文件物件模型 (DOM) 中會出現於何處。  
  
|方法|節點取代|  
|------------|--------------------|  
|<xref:System.Xml.XmlNode.InsertBefore%2A>|在參考節點之前插入。 例如，若要在位置 5 插入新節點：<br /><br /> `Dim refChild As XmlNode = node.ChildNodes(4) 'The reference is zero-based.node.InsertBefore(newChild, refChild);`<br /><br /> `XmlNode refChild = node.ChildNodes[4]; //The reference is zero-based. node.InsertBefore(newChild, refChild);`<br /><br /> 如需詳細資訊，請參閱 <xref:System.Xml.XmlNode.InsertBefore%2A> 方法。|  
|<xref:System.Xml.XmlNode.InsertAfter%2A>|在參考節點之後插入。 例如: <br /><br /> `node.InsertAfter(newChild, refChild)`<br /><br /> `node.InsertAfter(newChild, refChild);`<br /><br /> 如需詳細資訊，請參閱 <xref:System.Xml.XmlNode.InsertAfter%2A> 方法。|  
|<xref:System.Xml.XmlNode.AppendChild%2A>|將節點加入至指定節點之子節點的清單結尾處。 如果加入的節點為 <xref:System.Xml.XmlDocumentFragment>，則文件片段的全部內容都會移至此節點的子清單中。 如需詳細資訊，請參閱 <xref:System.Xml.XmlNode.AppendChild%2A> 方法。|  
|<xref:System.Xml.XmlNode.PrependChild%2A>|將節點加入至指定節點之子節點的清單開頭。 如果加入的節點為 <xref:System.Xml.XmlDocumentFragment>，則文件片段的全部內容都會移至此節點的子清單中。 如需詳細資訊，請參閱 <xref:System.Xml.XmlNode.PrependChild%2A> 方法。|  
|<xref:System.Xml.XmlAttributeCollection.Append%2A>|將 <xref:System.Xml.XmlAttribute> 節點附加至與項目關聯之屬性集合的結尾。 如需詳細資訊，請參閱 <xref:System.Xml.XmlAttributeCollection.Append%2A> 方法。|  
  
## <a name="see-also"></a>請參閱  
 [XML 文件物件模型 (DOM)](../../../../docs/standard/data/xml/xml-document-object-model-dom.md)
