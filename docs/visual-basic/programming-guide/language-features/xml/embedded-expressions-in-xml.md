---
title: XML 中內嵌的運算式
ms.date: 07/20/2015
f1_keywords:
- vb.XmlEmbeddedExpression
helpviewer_keywords:
- embedded expressions [Visual Basic]
- LINQ to XML [Visual Basic], embedded expressions
- XML literals [Visual Basic], embedded expressions
ms.assetid: bf2eb779-b751-4b7c-854f-9f2161482352
ms.openlocfilehash: 0cdb960160457108ddf18c554dae5f5993269833
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/22/2019
ms.locfileid: "74332346"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML 中內嵌的運算式 (Visual Basic)
內嵌運算式可讓您建立 XML 常值，其中包含在執行時間評估的運算式。 內嵌運算式的語法是 `<%=` `expression` `%>`，這與 ASP.NET 中所使用的語法相同。  
  
 例如，您可以建立 XML 元素常值，並結合內嵌運算式與常值文字內容。  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 如果 `isbnNumber` 包含整數12345，而 `modifiedDate` 包含日期3/5/2006，則當此程式碼執行時，`book` 的值為：  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>內嵌運算式位置和驗證  
 內嵌運算式只能出現在 XML 常值運算式內的特定位置。 運算式位置會控制運算式可以傳回的類型，以及處理 `Nothing` 的方式。 下表描述內嵌運算式的允許位置和類型。  
  
|常值中的位置|運算式的類型|`Nothing` 的處理|  
|---|---|---|  
|XML 元素名稱|<xref:System.Xml.Linq.XName>|錯誤|  
|XML 元素內容|`Object` 的 `Object` 或陣列|略過|  
|XML 元素屬性名稱|<xref:System.Xml.Linq.XName>|錯誤，除非屬性值也 `Nothing`|  
|XML 元素屬性值|`Object`|已忽略屬性宣告|  
|XML 元素屬性|<xref:System.Xml.Linq.XAttribute> 或 <xref:System.Xml.Linq.XAttribute> 的集合|略過|  
|XML 檔根項目|<xref:System.Xml.Linq.XElement> 或一個 <xref:System.Xml.Linq.XElement> 物件的集合，以及任意數目的 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 物件|略過|  
  
- XML 元素名稱中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- XML 元素內容中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- XML 元素屬性名稱中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- XML 元素屬性值中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- XML 元素屬性中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- XML 檔根項目中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 如果您啟用 `Option Strict`，編譯器會檢查每個內嵌運算式的類型是否加寬成所需的類型。 唯一的例外是針對 XML 檔的根項目，這會在程式碼執行時進行驗證。 如果您編譯時沒有 `Option Strict`，您可以內嵌類型 `Object` 的運算式，並在執行時間驗證其類型。  
  
 在內容為選擇性的位置中，會忽略包含 `Nothing` 的內嵌運算式。 這表示您不需要在使用 XML 常值之前，檢查元素內容、屬性值和陣列元素是否 `Nothing`。 無法 `Nothing`必要的值，例如元素和屬性名稱。  
  
 如需在特定類型的常值中使用內嵌運算式的詳細資訊，請參閱[Xml 檔常](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)值、 [xml 元素常](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)值。  
  
## <a name="scoping-rules"></a>範圍規則  
 編譯器會將每個 XML 常值轉換成適當常數值型別的函式呼叫。 XML 常值中的常值內容和內嵌運算式會當做引數傳遞至函式。 這表示可用於 XML 常值的所有 Visual Basic 程式設計專案也可用於其內嵌運算式。  
  
 在 XML 常值內，您可以存取以 `Imports` 語句宣告的 XML 命名空間前置詞。 您可以使用 `xmlns` 屬性，在元素中宣告新的 XML 命名空間前置詞，或遮蔽現有的 XML 命名空間前置詞。 新的命名空間可用於該元素的子節點，但不能用於內嵌運算式中的 XML 常值。  
  
> [!NOTE]
> 當您使用 `xmlns` namespace 屬性來宣告 XML 命名空間前置詞時，屬性值必須是常數位串。 在這方面，使用 `xmlns` 屬性就像使用 `Imports` 語句來宣告 XML 命名空間。 您不能使用內嵌運算式來指定 XML 命名空間值。  
  
## <a name="see-also"></a>請參閱

- [在 Visual Basic 中建立 XML](../../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 文件常值](../../../../visual-basic/language-reference/xml-literals/xml-document-literal.md)
- [XML 項目常值](../../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [Option Strict 陳述式](../../../../visual-basic/language-reference/statements/option-strict-statement.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML 常值概觀](../../../../visual-basic/programming-guide/language-features/xml/xml-literals-overview.md)
