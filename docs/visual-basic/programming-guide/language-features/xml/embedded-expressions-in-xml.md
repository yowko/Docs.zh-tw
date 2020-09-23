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
ms.openlocfilehash: 44a6c3408b57fa7f89e2834aa677fe8801ef21f3
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058309"
---
# <a name="embedded-expressions-in-xml-visual-basic"></a>XML 中內嵌的運算式 (Visual Basic)

內嵌的運算式可讓您建立 XML 常值，其中包含在執行時間評估的運算式。 內嵌運算式的語法是，與 `<%=` `expression` `%>` ASP.NET 中使用的語法相同。  
  
 例如，您可以建立 XML 元素常值，並將內嵌運算式與常值文字內容結合在一起。  
  
 [!code-vb[VbXMLSamples#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#27)]  
  
 如果 `isbnNumber` 包含整數12345並 `modifiedDate` 包含日期3/5/2006，則當此程式碼執行時，的值 `book` 為：  
  
```xml  
<book category="fiction" isbn="12345">  
  <modifiedDate>3/5/2006</modifiedDate>  
</book>  
```  
  
## <a name="embedded-expression-location-and-validation"></a>內嵌運算式位置和驗證  

 內嵌的運算式只能出現在 XML 常值運算式內的特定位置。 運算式位置會控制運算式可傳回的類型，以及 `Nothing` 處理方式。 下表描述內嵌運算式的允許位置和類型。  
  
|常值中的位置|運算式的類型|處理 `Nothing`|  
|---|---|---|  
|XML 元素名稱|<xref:System.Xml.Linq.XName>|錯誤|  
|XML 元素內容|`Object` 或的陣列 `Object`|忽略|  
|XML 元素屬性名稱|<xref:System.Xml.Linq.XName>|錯誤，除非屬性值也是 `Nothing`|  
|XML 元素屬性值|`Object`|忽略屬性宣告|  
|XML 元素屬性|<xref:System.Xml.Linq.XAttribute> 或的集合 <xref:System.Xml.Linq.XAttribute>|忽略|  
|XML 檔根項目|<xref:System.Xml.Linq.XElement> 或一個物件的集合 <xref:System.Xml.Linq.XElement> ，以及任意數目的 <xref:System.Xml.Linq.XProcessingInstruction> 和 <xref:System.Xml.Linq.XComment> 物件|忽略|  
  
- XML 元素名稱中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#32)]  
  
- XML 元素內容中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#33)]  
  
- XML 元素屬性名稱中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#34)]  
  
- XML 元素屬性值中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#35](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#35)]  
  
- XML 元素屬性中內嵌運算式的範例：  
  
     [!code-vb[VbXMLSamples#36](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#36)]  
  
- XML 檔根項目中的內嵌運算式範例：  
  
     [!code-vb[VbXMLSamples#37](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#37)]  
  
 如果您啟用 `Option Strict` ，編譯器會檢查每個內嵌運算式的類型是否會擴大為所需的類型。 唯一的例外是 XML 檔的根項目，這會在程式碼執行時進行驗證。 如果您在沒有的情況 `Option Strict` 下進行編譯，您可以內嵌類型的運算式， `Object` 並在執行時間驗證其型別。  
  
 在內容為選擇性的位置中， `Nothing` 會忽略包含的內嵌運算式。 這表示在 `Nothing` 您使用 XML 常值之前，不需要檢查元素內容、屬性值和陣列元素。 必要值（例如元素和屬性名稱）不可為 `Nothing` 。  
  
 如需在特定類型的常值中使用內嵌運算式的詳細資訊，請參閱 [Xml 檔常](../../../language-reference/xml-literals/xml-document-literal.md)值、 [xml 元素常](../../../language-reference/xml-literals/xml-element-literal.md)值。  
  
## <a name="scoping-rules"></a>範圍規則  

 編譯器會將每個 XML 常值轉換成適當常數值型別的函式呼叫。 XML 常值中的常值內容和內嵌運算式會以引數的形式傳遞至函式。 這表示，XML 常值可用的所有 Visual Basic 程式設計專案也可供其內嵌運算式使用。  
  
 在 XML 常值中，您可以存取以語句宣告的 XML 命名空間前置詞 `Imports` 。 您可以使用屬性，在專案中宣告新的 XML 命名空間前置詞，或遮蔽現有的 XML 命名空間前置詞 `xmlns` 。 新的命名空間可用於該專案的子節點，但不適用於內嵌運算式中的 XML 常值。  
  
> [!NOTE]
> 當您使用 namespace 屬性宣告 XML 命名空間前置詞時 `xmlns` ，屬性值必須是常數位符串。 在這方面，使用 `xmlns` 屬性就像使用 `Imports` 語句來宣告 XML 命名空間。 您無法使用內嵌運算式來指定 XML 命名空間值。  
  
## <a name="see-also"></a>另請參閱

- [在 Visual Basic 中建立 XML](creating-xml.md)
- [XML 文件常值](../../../language-reference/xml-literals/xml-document-literal.md)
- [XML 元素常值](../../../language-reference/xml-literals/xml-element-literal.md)
- [Long](../../../language-reference/statements/option-strict-statement.md)
- [Imports 陳述式 (.NET 命名空間和類型)](../../../language-reference/statements/imports-statement-net-namespace-and-type.md)
- [XML 常值概觀](xml-literals-overview.md)
