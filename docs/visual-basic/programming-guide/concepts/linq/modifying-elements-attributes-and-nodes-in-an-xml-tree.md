---
title: 修改項目、 屬性和 XML Tree1 中的節點
ms.date: 07/20/2015
ms.assetid: 865cf54e-f8ac-4871-863b-a3e6fc61a4b9
ms.openlocfilehash: 91a7cca2e39e5ddc62d6010fbe4efad9bd7ff3c2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>修改 XML 樹狀中的項目、屬性和節點
下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。  
  
 下列方法會修改 <xref:System.Xml.Linq.XElement>。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=nameWithType>|以剖析的 XML 取代項目。|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=nameWithType>|移除項目的所有內容 (子節點和屬性)。|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=nameWithType>|移除項目的屬性。|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=nameWithType>|取代項目的所有內容 (子節點和屬性)。|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=nameWithType>|取代項目的屬性。|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=nameWithType>|設定屬性的值。 建立屬性 (如果不存在)。 如果值設定為 `null`，移除屬性。|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=nameWithType>|設定子項目的值。 建立項目 (如果不存在)。 如果值設定為 `null`，移除項目。|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=nameWithType>|以指定的文字取代項目的內容 (子節點)。|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=nameWithType>|設定項目的值。|  
  
 下列方法會修改 <xref:System.Xml.Linq.XAttribute>。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=nameWithType>|設定屬性的值。|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=nameWithType>|設定屬性的值。|  
  
 下列方法會修改 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=nameWithType>|以新內容取代節點。|  
  
 下列方法會修改 <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=nameWithType>|以新的內容取代子節點。|  
  
## <a name="see-also"></a>另請參閱  
 [修改 XML 樹狀 (LINQ to XML) (Visual Basic)](../../../../visual-basic/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
