---
title: "XML Attribute Axis Property (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.XmlPropertyAttributeAxis"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "attribute axis property [Visual Basic]"
  - "Visual Basic code, accessing XML"
  - "XML attribute axis property [Visual Basic]"
  - "XML axis [Visual Basic], attribute"
  - "XML [Visual Basic], accessing"
ms.assetid: 7a4777e1-0618-4de9-9510-fb9ace2bf4db
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# XML Attribute Axis Property (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

提供存取 <xref:System.Xml.Linq.XElement> 物件中屬性的值，或 <xref:System.Xml.Linq.XElement> 物件集合內第一個項目的屬性值。  
  
## 語法  
  
```  
  
      object.@attribute  
-or-  
object.@<attribute>  
```  
  
## 組件  
 `object`  
 必要項。  <xref:System.Xml.Linq.XElement> 物件或 <xref:System.Xml.Linq.XElement> 物件的集合。  
  
 .@  
 必要項。  代表屬性 \(Attribute\) 軸屬性 \(Property\) 的開始。  
  
 \<  
 選擇項。  當 `attribute` 在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中不是有效的識別項時，代表屬性 \(Attribute\) 名稱的開始。  
  
 `attribute`  
 必要項。  要存取的屬性 \(Attribute\) 名稱，格式為 \[`prefix`:\]`name`。  
  
|組件|描述|  
|--------|--------|  
|`prefix`|選擇項。  屬性 \(Attribute\) 的 XML 命名空間前置字元  必須是使用 `Imports` 陳述式定義的全域 XML 命名空間。|  
|`name`|必要項。  區域屬性 \(Attribute\) 名稱。  請參閱 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)。|  
  
 \>  
 選擇項。  當 `attribute` 在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中不是有效的識別項時，代表屬性 \(Attribute\) 名稱的結尾。  
  
## 傳回值  
 字串，含有 `attribute` 的值。  如果沒有屬性名稱，則會傳回 `Nothing`。  
  
## 備註  
 您可以使用 XML 屬性 \(Attribute\) 軸屬性 \(Property\)，依名稱存取 <xref:System.Xml.Linq.XElement> 物件中或 <xref:System.Xml.Linq.XElement> 物件的集合內第一個項目中的屬性 \(Attribute\) 值。  您可以依名稱擷取屬性 \(Attribute\) 值，或者藉由指定前有 @ 識別項的新名稱，將新的屬性 \(Attribute\) 加入至項目。  
  
 當您使用 @ 識別項參考 XML 屬性 \(Attribute\) 時，屬性 \(Attribute\) 值會以字串傳回，您不需要明確指定 <xref:System.Xml.Linq.XAttribute.Value%2A> 屬性 \(Property\)。  
  
 XML 屬性的命名規則與 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 識別項的命名規則不同。若要存取其名稱並非有效 Visual Basic 識別項的 XML 屬性，請將名稱置於角括弧 \(\< 和 \>\) 之內。  
  
## XML 命名空間  
 屬性 \(Attribute\) 軸屬性 \(Property\) 中的名稱只能使用以 `Imports` 陳述式在全域定義的 XML 命名空間前置字元。  不能使用在 XML 項目常值 \(Literal\) 內定義的區域 XML 命名空間前置字元。  如需詳細資訊，請參閱 [Imports Statement \(XML Namespace\)](../../../visual-basic/language-reference/statements/imports-statement-xml-namespace.md)。  
  
## 範例  
 下列範例顯示如何從名為 `phone` 的 XML 項目集合中，取得名為 `type` 之 XML 屬性 \(Attribute\) 的值。  
  
 [!code-vb[VbXMLSamples#12](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_1.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `<phoneTypes>`  
  
 `<type>home</type>`  
  
 `<type>work</type>`  
  
 `</phoneTypes>`  
  
## 範例  
 下列範例顯示兩種為 XML 項目建立屬性 \(Attribute\) 的方法，一種是在 XML 中以宣告方式建立，一種是以動態方式將屬性 \(Attribute\) 加入至 <xref:System.Xml.Linq.XElement> 物件的執行個體 \(Instance\)。  `type` 屬性 \(Attribute\) 是以宣告方式建立，而 `owne`r 屬性 \(Attribute\) 是以動態方式建立。  
  
 [!code-vb[VbXMLSamples#44](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_2.vb)]  
  
 這個程式碼會顯示下列文字：  
  
```  
<phone type="home" owner="Harris, Phyllis">206-555-0144</phone>  
```  
  
## 範例  
 下列範例會使用角括弧語法取得名為 `number-type` 之 XML 屬性 \(Attribute\) 的值，這個名稱在 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 中不是有效的識別項。  
  
 [!code-vb[VbXMLSamples#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_3.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Phone type: work`  
  
## 範例  
 下列範例將 `ns` 宣告為 XML 命名空間前置字元。  然後使用這個命名空間前置字元建立 XML 常值，並以限定名稱 "`ns:name` 存取第一個子節點。  
  
 [!code-vb[VbXMLSamples#14](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-attribute-axis-property_4.vb)]  
  
 這個程式碼會顯示下列文字：  
  
 `Phone type: home`  
  
## 請參閱  
 <xref:System.Xml.Linq.XElement>   
 [XML Axis Properties](../../../visual-basic/language-reference/xml-axis/xml-axis-properties.md)   
 [XML Literals](../../../visual-basic/language-reference/xml-literals/index.md)   
 [Creating XML in Visual Basic](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [Names of Declared XML Elements and Attributes](../../../visual-basic/programming-guide/language-features/xml/names-of-declared-xml-elements-and-attributes.md)