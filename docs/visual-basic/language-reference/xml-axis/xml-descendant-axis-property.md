---
title: "XML Descendant Axis Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyDescendantsAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML descendant axis property [Visual Basic]"
  - "descendant axis property [Visual Baisc]"
  - "XML axis [Visual Basic], descendant"
  - "XML [Visual Basic], accessing"
ms.assetid: a178f85b-5d54-438f-8479-40b62af6fe76
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# XML Descendant Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供存取下列項目的子代 \(Descendant\)：<xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合，或 <xref:System.Xml.Linq.XDocument> 物件的集合。  
  
## 語法  
  
```  
  
object...<descendant>  
```  
  
## 組件  
 `object`  
 必要項。  <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合，或 <xref:System.Xml.Linq.XDocument> 物件的集合。  
  
 ...\<  
 必要項。  代表子代軸屬性的開始。  
  
 `descendant`  
 必要項。  要存取的子代節點名稱，格式為 \[`prefix``:`\]`name`。  
  
|組件|描述|  
|--------|--------|  
|`prefix`|選擇項。  子代節點的 XML 命名空間前置字元。  必須是使用 `Imports` 陳述式 \(Statement\) 定義的全域 XML 命名空間。|  
|`name`|必要項。  子代節點的區域名稱。  請參閱 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 必要項。  代表子代軸屬性的結尾。  
  
## 傳回值  
 <xref:System.Xml.Linq.XElement> 物件的集合。  
  
## 備註  
 您可以使用 XML 子代軸屬性，從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件中，或是從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件的集合中，依名稱存取子代節點。  使用 XML `Value` 屬性可以存取所傳回集合中第一個子代節點的值。  如需詳細資訊，請參閱 [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將子代軸屬性轉換為對 <xref:System.Xml.Linq.XContainer.Descendants%2A> 方法的呼叫。  
  
## XML 命名空間  
 子代軸屬性中的名稱只能使用以 `Imports` 陳述式在全域宣告的 XML 命名空間，  不能使用在 XML 項目常值 \(Literal\) 內宣告的區域 XML 命名空間。  如需詳細資訊，請參閱 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## 範例  
 下列範例顯示如何從 `contacts` 物件存取名為 `name` 之第一個子代節點的值，以及名為 `phone` 之所有子代節點的值。  
  
 [!code-vb[VbXMLSamples#25](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_1.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Name: Patrick Hines`  
  
 `Home Phone = 206-555-0144`  
  
## 範例  
 下列範例將 `ns` 宣告為 XML 命名空間前置字元。  然後使用這個命名空間前置字元建立 XML 常值，並以限定名稱 `ns:name` 存取第一個子節點的值。  
  
 [!code-vb[VbXMLSamples#26](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-descendant-axis-property_2.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Name: Patrick Hines`  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)