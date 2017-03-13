---
title: "Embedded Expressions in XML (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlEmbeddedExpression"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "embedded expressions [Visual Basic]"
  - "LINQ to XML [Visual Basic], embedded expressions"
  - "XML literals [Visual Basic], embedded expressions"
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 22
---
# Embedded Expressions in XML (Visual Basic)
[!INCLUDE[vs2017banner](../../../../visual-basic/includes/vs2017banner.md)]

內嵌運算式可以讓您建立 XML 常值 \(Literal\)，其中包含在執行階段進行評估的運算式。  內嵌運算式的語法為 `<%=` `expression` `%>`，與 [!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp-md.md)] 中使用的語法相同。  
  
 例如，您可以建立 XML 項目常值，將常值文字內容與內嵌運算式結合在一起。  
  
 [!code-vb[VbXMLSamples#27](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 如果 `isbnNumber` 包含整數 12345 且 `modifiedDate` 包含日期 3\/5\/2006，則當程式碼執行時，`book` 的值是：  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## 內嵌運算式位置及驗證  
 內嵌運算式只能顯示在 XML 常值運算式內的特定位置。  運算式位置控制運算式可以傳回的型別以及處理 `Nothing` 的方式。  下表說明允許的內嵌運算式位置和型別。  
  
||||  
|-|-|-|  
|常值中的位置|運算式型別|處理 `Nothing`|  
|XML 項目名稱|<xref:System.Xml.Linq.XName>|錯誤|  
|XML 項目內容|`Object` 或 `Object` 的陣列|略過|  
|XML 項目屬性名稱|<xref:System.Xml.Linq.XName>|錯誤，除非屬性 \(Attribute\) 值也是 `Nothing`|  
|XML 項目屬性值|`Object`|略過屬性宣告|  
|XML 項目屬性|<xref:System.Xml.Linq.XAttribute> 或 <xref:System.Xml.Linq.XAttribute> 的集合|略過|  
|XML 文件根項目|<xref:System.Xml.Linq.XElement> 或一個 <xref:System.Xml.Linq.XElement> 物件和任意數量 <xref:System.Xml.Linq.XProcessingInstruction> 及 <xref:System.Xml.Linq.XComment> 物件的集合|略過|  
  
-   XML 項目名稱中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#32](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   XML 項目內容中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#33](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   XML 項目屬性名稱中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#34](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   XML 項目屬性值中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#35](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   XML 項目屬性中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#36](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   XML 文件根項目中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#37](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 如果您啟用 `Option Strict`，編譯器 \(Compiler\) 會檢查每個內嵌運算式的型別是否擴展為所需型別。  唯一的例外狀況 \(Exception\) 是 XML 文件的根項目 \(Root Element\)，根項目是在程式碼執行時進行驗證。  如果編譯時不使用 `Option Strict`，則可內嵌型別 `Object` 的運算式，而其型別會在執行階段驗證。  
  
 在內容為選擇性的位置中，會略過包含 `Nothing` 的內嵌運算式。  這表示在您使用 XML 常值之前，不需要檢查項目內容、屬性值及陣列項目是否為 `Nothing`。  必要的值 \(例如項目和屬性名稱\) 不得為 `Nothing`。  
  
 如需在特定常值型別中使用內嵌運算式的詳細資訊，請參閱 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)和 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## 設定規則的範圍  
 編譯器會將每個 XML 常值轉換為適當常值型別的建構函式 \(Constructor\) 呼叫。  XML 常值中的常值內容和內嵌運算式會傳遞給建構函式的引數。  這表示所有可供 XML 常值使用的 [!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 程式設計項目，也可供內嵌運算式使用。  
  
 在 XML 常值中，您可以存取以 `Imports` 陳述式 \(Statement\) 宣告的 XML 命名空間前置字元。  您可以使用 `xmlns` 屬性，在項目中宣告新的 XML 命名空間前置字元，或遮蔽現有 XML 命名空間前置字元。  新的命名空間 \(Namespace\) 可供該項目的子節點使用，但是不可供內嵌運算式中的 XML 常值使用。  
  
> [!NOTE]
>  當您使用 `xmlns` 命名空間屬性宣告 XML 命名空間前置字元時，屬性值必須是常數字串。  就這點而言，使用 `xmlns` 屬性類似於使用 `Imports` 陳述式宣告 XML 命名空間。  您無法使用內嵌運算式指定 XML 命名空間值。  
  
## 請參閱  
 [Creating XML in Visual Basic](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML Document Literal](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML Element Literal](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Option Strict Statement](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Imports Statement \(.NET Namespace and Type\)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [XML Literals Overview](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)