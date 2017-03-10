---
title: "XML Value Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyExtensionValue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Value property [Visual Basic]"
  - "Visual Basic code, accessing XML"
  - "XML axis [Visual Basic], Value"
  - "XML Value property [Visual Basic]"
ms.assetid: 7ddd057a-a195-4e9b-ad8b-2ee0e615a20f
caps.latest.revision: 18
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 18
---
# XML Value Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供存取 <xref:System.Xml.Linq.XElement> 物件的集合中第一個項目的值。  
  
## 語法  
  
```  
  
object.Value  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`object`|必要項。  <xref:System.Xml.Linq.XElement> 物件的集合。|  
  
## 傳回值  
 `String`，包含集合中第一個項目的值，如果該集合是空的則為 `Nothing`。  
  
## 備註  
 <xref:System.Xml.Linq.XElement.Value%2A> 屬性 \(Property\) 可讓您輕鬆地存取 <xref:System.Xml.Linq.XElement> 物件的集合中第一個項目的值。  這個屬性 \(Property\) 會先檢查集合中是否至少包含一個物件。  如果集合是空的，則這個屬性 \(Property\) 會傳回 `Nothing`。  否則，這個屬性 \(Property\) 會傳回集合中第一個項目的 <xref:System.Xml.Linq.XElement.Value%2A> 屬性 \(Property\) 值。  
  
> [!NOTE]
>  當您使用 '@' 識別項存取 XML 屬性 \(Attribute\) 的值時，屬性 \(Attribute\) 值會以 `String` 傳回，您不需要明確指定 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性 \(Property\)。  
  
 若要存取集合中的其他項目，您可以使用 XML 擴充索引子屬性 \(Property\)。  如需詳細資訊，請參閱 [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)。  
  
## 繼承  
 大多數的使用者不需要實作 <xref:System.Collections.Generic.IEnumerable%601>，因此可以忽略本節的內容。  
  
 The <xref:System.Xml.Linq.XElement.Value%2A> 屬性 \(Property\) 是一個擴充屬性，適用於會實作 `IEnumerable(Of XElement)` 的型別。  繫結這個擴充屬性就像繫結擴充方法：如果有型別實作其中一個介面並定義了名為 "Value" 的屬性 \(Property\)，則該屬性 \(Property\) 會優先於擴充屬性。  換句話說，只要在實作 `IEnumerable(Of XElement)` 的類別 \(Class\) 中定義新的屬性 \(Property\)，即可覆寫這個 <xref:System.Xml.Linq.XElement.Value%2A> 屬性 \(Property\)。  
  
## 範例  
 下列範例顯示如何使用 <xref:System.Xml.Linq.XElement.Value%2A> 屬性 \(Property\) 存取 <xref:System.Xml.Linq.XElement> 物件之集合中的第一個節點。  這個範例會使用子項軸屬性 \(Property\) 取得 `contact` 物件中所有名為 `phone` 之子節點的集合。  
  
 [!code-vb[VbXMLSamples#15](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-value-property_1.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Phone number: 206-555-0144`  
  
## 範例  
 下列範例顯示如何從 <xref:System.Xml.Linq.XAttribute> 物件的集合中取得 XML 屬性 \(Attribute\) 的值。  這個範例會使用屬性 \(Attribute\) 軸屬性 \(Property\) 顯示所有 `phone` 項目之 `type` 屬性 \(Attribute\) 的值。  
  
 [!code-vb[VbXMLSamples#16](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/xml-value-property_2.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `home`  
  
 `work`  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Collections.Generic.IEnumerable%601>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [擴充方法](../../../visual-basic/programming-guide/language-features/procedures/extension-methods.md)   
 [Extension Indexer Property](../../../visual-basic/language-reference/xml-axis/extension-indexer-property.md)   
 [XML Child Axis Property](../../../visual-basic/language-reference/xml-axis/xml-child-axis-property.md)   
 [XML Attribute Axis Property](../../../visual-basic/language-reference/xml-axis/xml-attribute-axis-property.md)