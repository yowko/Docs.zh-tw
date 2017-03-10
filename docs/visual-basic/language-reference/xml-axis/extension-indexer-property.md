---
title: "Extension Indexer Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyExtensionIndexer"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML extension indexer [Visual Basic]"
  - "extension indexer [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: a16a4b13-54be-432c-82b3-a87091464ada
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Extension Indexer Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供對集合中個別項目的存取。  
  
## 語法  
  
```  
  
object(index)  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`object`|必要項。  可查詢的集合。  也就是，實作 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 的集合。|  
|\(|必要項。  代表索引子屬性的開頭。|  
|`index`|必要項。  整數運算式，指定集合中以零起始的項目位置。|  
|\)|必要項。  代表索引子屬性的結尾。|  
  
## 傳回值  
 集合中指定位置上的物件，如果索引超過範圍外則為 `Nothing`。  
  
## 備註  
 您可以使用擴充索引子屬性存取集合中的個別項目。  此索引子屬性通常用在 XML 軸屬性的輸出。  XML 子項和 XML 子代軸屬性會傳回 <xref:System.Xml.Linq.XElement> 物件或屬性 \(Attribute\) 值的集合。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器會將擴充索引子屬性轉換為對 `ElementAtOrDefault` 方法的呼叫。與陣列索引子不同，如果索引超出範圍，`ElementAtOrDefault` 方法就會傳回 `Nothing`。  當您無法輕易判斷集合中的項目數量時，這種行為相當有用。  
  
 索引子屬性如同實作 <xref:System.Collections.Generic.IEnumerable%601> 或 <xref:System.Linq.IQueryable%601> 之集合的擴充屬性：只在集合沒有索引子或預設屬性時使用。  
  
 若要存取 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XAttribute> 物件集合中第一個項目的值，您可以使用 XML `Value` 屬性。  如需詳細資訊，請參閱 [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
## 範例  
 下列範例顯示如何使用擴充索引子存取 <xref:System.Xml.Linq.XElement> 物件集合中的第二個子節點。  將使用子項軸屬性存取集合，該屬性會取得 `contact` 物件中名為 `phone` 的所有子項目。  
  
 [!code-vb[VbXMLSamples#24](../../../visual-basic/language-reference/operators/codesnippet/visualbasic/extension-indexer-property_1.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Second phone number: 425-555-0145`  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)