---
title: "XML (Visual Basic) 中內嵌運算式 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vb.XmlEmbeddedExpression
dev_langs:
- VB
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
caps.latest.revision: 22
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: e5cd40e55ec23de3ad1bb2f5f065762c893d9cb3
ms.lasthandoff: 03/13/2017

---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML 中內嵌的運算式 (Visual Basic)
內嵌的運算式可讓您建立 XML 常值包含在執行階段評估的運算式。 內嵌運算式的語法是`<%=` `expression` `%>`，這會是相同的語法中使用[!INCLUDE[vstecasp](../../../../csharp/language-reference/preprocessor-directives/includes/vstecasp_md.md)]。  
  
 例如，您可以建立的 XML 項目常值，結合使用常值文字內容有內嵌的運算式。  
  
 [!code-vb[VbXMLSamples #&27;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_1.vb)]  
  
 如果`isbnNumber`包含整數 12345 和`modifiedDate`包含的日期 3/5/2006，此程式碼執行時，值`book`是︰  
  
```  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>內嵌的運算式的位置和驗證  
 內嵌的運算式只可以出現在 XML 常值運算式內的特定位置。 可以傳回型別運算式的運算式位置控制項，以及如何`Nothing`處理。 下表描述允許的位置和內嵌運算式的型別。  
  
|常值中的位置|運算式的型別|處理`Nothing`|  
|---|---|---|  
|XML 項目名稱|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|錯誤|  
|XML 項目內容|`Object`或陣列`Object`|略過|  
|XML 項目屬性名稱|<xref:System.Xml.Linq.XName></xref:System.Xml.Linq.XName>|錯誤，除非也是屬性值`Nothing`|  
|XML 項目屬性值|`Object`|略過屬性宣告|  
|XML 項目屬性|<xref:System.Xml.Linq.XAttribute>或集合<xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute></xref:System.Xml.Linq.XAttribute>|略過|  
|XML 文件根項目|<xref:System.Xml.Linq.XElement>一個<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件</xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XElement>的集合，或</xref:System.Xml.Linq.XElement>|略過|  
  
-   XML 項目名稱中內嵌運算式的範例︰  
  
     [!code-vb[VbXMLSamples #&32;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_2.vb)]  
  
-   XML 項目的內嵌運算式內容中的範例︰  
  
     [!code-vb[VbXMLSamples #&33;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_3.vb)]  
  
-   XML 項目屬性名稱中內嵌運算式的範例︰  
  
     [!code-vb[VbXMLSamples #&34;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_4.vb)]  
  
-   內嵌運算式中的 XML 項目屬性值的範例︰  
  
     [!code-vb[VbXMLSamples #&35;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_5.vb)]  
  
-   內嵌運算式中的 XML 項目屬性的範例︰  
  
     [!code-vb[VbXMLSamples #&36;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_6.vb)]  
  
-   XML 文件根項目中內嵌運算式的範例︰  
  
     [!code-vb[VbXMLSamples #&37;](../../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/embedded-expressions-in-xml_7.vb)]  
  
 如果您啟用`Option Strict`，編譯器會檢查每個內嵌的運算式的型別擴展的必要型別。 唯一的例外狀況是在程式碼執行時，系統驗證的 XML 文件的根項目。 如果您編譯而不需`Option Strict`，您可以將內嵌運算式的型別`Object`和執行階段就會驗證它們的型別。  
  
 選擇性的內容的位置內嵌運算式，包含`Nothing`會被忽略。 這表示您不需要檢查的項目內容，屬性值，而且陣列項目不`Nothing`使用 XML 常值之前。 必要值，例如項目和屬性名稱不能`Nothing`。  
  
 如需特定類型的常值中使用內嵌的運算式的詳細資訊，請參閱[XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)， [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="scoping-rules"></a>範圍規則  
 編譯器會將每個 XML 常值轉換成適當的常值類型的建構函式呼叫。 建構函式，會將常值的內容和內嵌的運算式，在 XML 常值中傳遞做為引數。 這表示所有[!INCLUDE[vbprvb](../../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]用於 XML 常值的程式設計項目也是用於內嵌的運算式。  
  
 在 XML 常值，您可存取的 XML 命名空間前置詞宣告`Imports`陳述式。 您可以宣告新的 XML 命名空間前置詞，或遮蔽現有 XML 命名空間前置詞，在項目中使用`xmlns`屬性。 內嵌的運算式中的 XML 常值的子節點，該項目的但不是使用新的命名空間。  
  
> [!NOTE]
>  當您宣告 XML 命名空間前置詞使用`xmlns`命名空間屬性的屬性值必須是常數字串。 在這方面，使用`xmlns`屬性，就像是`Imports`陳述式來宣告 XML 命名空間。 您無法使用內嵌的運算式來指定 XML 命名空間值。  
  
## <a name="see-also"></a>另請參閱  
 [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)   
 [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)   
 [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)   
 [XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
