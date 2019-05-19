---
title: XML 中內嵌的運算式 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: ef8ac62d9d969ce4463931d69b0302376ca0ccc4
ms.sourcegitcommit: c4e9d05644c9cb89de5ce6002723de107ea2e2c4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2019
ms.locfileid: "65881531"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML 中內嵌的運算式 (Visual Basic)
內嵌的運算式可讓您建立 XML 常值包含在執行階段評估的運算式。 內嵌運算式的語法`<%=` `expression` `%>`，這是 ASP.NET 中使用的語法相同。  
  
 例如，您可以建立的 XML 項目常值，結合使用常值的文字內容的內嵌的運算式。  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 如果`isbnNumber`包含整數 12345 並`modifiedDate`包含日期 3/5/2006，此程式碼執行時，值`book`是：  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>內嵌的運算式的位置和驗證  
 內嵌的運算式只可以出現在 XML 常值運算式內的特定位置。 運算式的位置控制項類型的運算式可以傳回及如何`Nothing`處理。 下表描述允許的位置和內嵌運算式的型別。  
  
|常值中的位置|運算式的型別|處理 `Nothing`|  
|---|---|---|  
|XML 項目名稱|<xref:System.Xml.Linq.XName>|錯誤|  
|XML 項目內容|`Object` 或陣列 `Object`|略過|  
|XML 項目屬性名稱|<xref:System.Xml.Linq.XName>|錯誤，除非屬性值也是 `Nothing`|  
|XML 項目屬性值|`Object`|忽略的屬性宣告|  
|XML 項目屬性|<xref:System.Xml.Linq.XAttribute> 或集合 <xref:System.Xml.Linq.XAttribute>|略過|  
|XML 文件根項目|<xref:System.Xml.Linq.XElement> 或其中一個集合<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件|略過|  
  
- XML 項目名稱中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- XML 項目的內嵌運算式內容中的範例：  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- XML 項目屬性名稱中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- XML 項目屬性值的內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- 內嵌運算式中的 XML 項目屬性的範例：  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- 內嵌運算式的 XML 文件根項目中的範例：  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 如果您啟用`Option Strict`，編譯器會檢查每個內嵌的運算式類型可擴展為要求的類型。 程式碼執行時驗證的 XML 文件的根項目是唯一的例外狀況。 如果您編譯而不要`Option Strict`，您可以將內嵌類型的運算式`Object`和其類型在執行階段驗證。  
  
 內容是選擇性的其中的位置中內嵌包含的運算式`Nothing`都會被忽略。 這表示您沒有檢查項目內容，屬性值，而且陣列項目不是`Nothing`才能使用 XML 常值。 必要值，例如項目和屬性名稱不可以是`Nothing`。  
  
 如需使用特定類型的常值中的內嵌的運算式的詳細資訊，請參閱[XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)， [XML 元素常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。  
  
## <a name="scoping-rules"></a>範圍規則  
 編譯器會將每個 XML 常值轉換成適當的常值類型的建構函式呼叫。 建構函式，會將 XML 常值中內嵌的運算式與常值內容傳遞做為引數。 這表示所有 Visual Basic 程式設計項目可使用 XML 常值都可內嵌的運算式。  
  
 在 XML 常值，您可以存取以宣告的前置詞的 XML 命名空間`Imports`陳述式。 您可以宣告新的 XML 命名空間前置詞，或遮蔽現有 XML 命名空間前置詞，在項目中使用`xmlns`屬性。 內嵌的運算式中的 XML 常值之子節點的該元素，但不是使用新的命名空間。  
  
> [!NOTE]
>  當您宣告 XML 命名空間前置詞使用`xmlns`命名空間屬性的屬性值必須是常數字串。 在這方面，使用`xmlns`屬性，就像是`Imports`陳述式來宣告 XML 命名空間。 您無法使用內嵌的運算式來指定 XML 命名空間值。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
