---
title: "修改 XML Tree3 中的項目、屬性和節點 | Microsoft Docs"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
ms.assetid: 0ed22e4e-4c6b-4eb1-b0eb-06685efd8c33
caps.latest.revision: 3
author: BillWagner
ms.author: wiwagn
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 6fa51b22af73d716b01444540edb7c8d814cd293
ms.lasthandoff: 03/13/2017


---
# <a name="modifying-elements-attributes-and-nodes-in-an-xml-tree"></a>修改 XML 樹狀中的項目、屬性和節點
下表摘要說明您可以用於修改項目、其子項目或其屬性的方法和屬性。  
  
 下列方法會修改 <xref:System.Xml.Linq.XElement>。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XElement.Parse%2A?displayProperty=fullName>|以剖析的 XML 取代項目。|  
|<xref:System.Xml.Linq.XElement.RemoveAll%2A?displayProperty=fullName>|移除項目的所有內容 (子節點和屬性)。|  
|<xref:System.Xml.Linq.XElement.RemoveAttributes%2A?displayProperty=fullName>|移除項目的屬性。|  
|<xref:System.Xml.Linq.XElement.ReplaceAll%2A?displayProperty=fullName>|取代項目的所有內容 (子節點和屬性)。|  
|<xref:System.Xml.Linq.XElement.ReplaceAttributes%2A?displayProperty=fullName>|取代項目的屬性。|  
|<xref:System.Xml.Linq.XElement.SetAttributeValue%2A?displayProperty=fullName>|設定屬性的值。 建立屬性 (如果不存在)。 如果值設定為 `null`，移除屬性。|  
|<xref:System.Xml.Linq.XElement.SetElementValue%2A?displayProperty=fullName>|設定子項目的值。 建立項目 (如果不存在)。 如果值設定為 `null`，移除項目。|  
|<xref:System.Xml.Linq.XElement.Value%2A?displayProperty=fullName>|以指定的文字取代項目的內容 (子節點)。|  
|<xref:System.Xml.Linq.XElement.SetValue%2A?displayProperty=fullName>|設定項目的值。|  
  
 下列方法會修改 <xref:System.Xml.Linq.XAttribute>。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XAttribute.Value%2A?displayProperty=fullName>|設定屬性的值。|  
|<xref:System.Xml.Linq.XAttribute.SetValue%2A?displayProperty=fullName>|設定屬性的值。|  
  
 下列方法會修改 <xref:System.Xml.Linq.XNode> (包括 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。  
  
|方法|說明|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XNode.ReplaceWith%2A?displayProperty=fullName>|以新內容取代節點。|  
  
 下列方法會修改 <xref:System.Xml.Linq.XContainer> (<xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument>)。  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Xml.Linq.XContainer.ReplaceNodes%2A?displayProperty=fullName>|以新的內容取代子節點。|  
  
## <a name="see-also"></a>另請參閱  
 [修改 XML 樹狀結構 (LINQ to XML) (C#)](../../../../csharp/programming-guide/concepts/linq/modifying-xml-trees-linq-to-xml.md)
