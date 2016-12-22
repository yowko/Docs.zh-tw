---
title: "XML Child Axis Property (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyChildAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic code, accessing XML"
  - "XML axis [Visual Basic], child"
  - "child axis property [Visual Basic]"
  - "XML child axis property [Visual Basic]"
  - "XML [Visual Basic], accessing"
ms.assetid: 89a59d00-985e-4f5c-b59f-29b47bad11cb
caps.latest.revision: 18
caps.handback.revision: 18
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# XML Child Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

提供下列任一項目之子系的存取：<xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件的集合，或是 <xref:System.Xml.Linq.XDocument> 物件的集合。  
  
## 語法  
  
```  
  
object.<child>  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`object`|必要項。  <xref:System.Xml.Linq.XElement> 物件、<xref:System.Xml.Linq.XDocument> 物件、<xref:System.Xml.Linq.XElement> 物件集合或 <xref:System.Xml.Linq.XDocument> 物件集合。|  
|.\<|必要項。  代表子軸屬性的開頭。|  
|`child`|必要項。  要存取的子節點名稱，其格式為 \[`prefix``:`\]`name`。<br /><br /> -   `Prefix`：選擇項。  子節點的 XML 命名空間前置詞。  必須是以 `Imports` 陳述式定義的全域 XML 命名空間。<br />-   `Name` \- 必要項。  本機子節點名稱。  請參閱[Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
|\>|必要項。  代表子軸屬性的結尾。|  
  
## 傳回值  
 <xref:System.Xml.Linq.XElement> 物件的集合。  
  
## 備註  
 您可以使用 XML 子軸屬性，從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件，或從 <xref:System.Xml.Linq.XElement> 或 <xref:System.Xml.Linq.XDocument> 物件集合依據名稱存取子節點。  使用 XML `Value` 屬性來存取傳回的集合中第一個子節點的值。  如需詳細資訊，請參閱 [XML Value Property](../../../visual-basic/language-reference/xml-axis/xml-value-property.md)。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器會將子軸屬性轉換成對 <xref:System.Xml.Linq.XContainer.Elements%2A> 方法的呼叫。  
  
## XML 命名空間  
 子軸屬性中的名稱只可以使用以 `Imports` 陳述式全域宣告的 XML 命名空間前置詞。  它不能使用在 XML 項目常值內本機宣告的 XML 命名空間前置詞。  如需詳細資訊，請參閱 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## 範例  
 下列範例示範如何從 `contact` 物件存取名為 `phone` 的子節點。  
  
 [!code-vb[VbXMLSamples#17](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_1.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Home Phone = 206-555-0144`  
  
## 範例  
 下列範例示範如何從 `contacts` 物件的 `contact` 子軸屬性傳回的集合存取名為 `phone` 的子節點。  
  
 [!code-vb[VbXMLSamples#18](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_2.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Home Phone = 206-555-0144`  
  
## 範例  
 下列範例會宣告 `ns` 作為 XML 命名空間前置詞。  然後它會使用命名空間的前置詞來建立 XML 常值，以及存取完整名稱為 `ns:name` 的第一個子節點。  
  
 [!code-vb[VbXMLSamples#19](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-child-axis-property_3.vb)]  
  
 此程式碼顯示下列文字：  
  
 `Patrick Hines`  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)