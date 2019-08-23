---
title: XML 註解常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 91369392f33f2a86a7a4cb5ffb3faa668c113348
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69965404"
---
# <a name="xml-comment-literal-visual-basic"></a>XML 註解常值 (Visual Basic)
代表<xref:System.Xml.Linq.XComment>物件的常值。  
  
## <a name="syntax"></a>語法  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`<!--`|必要項。 表示 XML 批註的開頭。|  
|`content`|必要項。 要出現在 XML 批註中的文字。 不能包含一系列的兩個連字號 (--), 也不能以連字號連續的結束記號結束。|  
|`-->`|必要項。 表示 XML 批註的結尾。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XComment> 物件。  
  
## <a name="remarks"></a>備註  
 XML 批註常值不包含檔內容;其中包含檔的相關資訊。 XML 批註區段的結尾是「-->」序列。 這表示下列幾點:  
  
- 您不能在 XML 批註常值中使用內嵌運算式, 因為內嵌的運算式分隔符號是有效的 XML 批註內容。  
  
- XML 批註區段無法嵌套, 因為`content`不能包含值 "-->"。  
  
 您可以將 XML 批註常值指派給變數, 也可以將它包含在 XML 元素常值中。  
  
> [!NOTE]
> XML 常值可以跨越多行, 而不需要使用行接續字元。 這項功能可讓您從 XML 檔案複製內容, 並將它直接貼到 Visual Basic 程式中。  
  
 Visual Basic 編譯器會將 XML 批註常值轉換為對此<xref:System.Xml.Linq.XComment.%23ctor%2A>函式的呼叫。  
  
## <a name="example"></a>範例  
 下列範例會建立包含文字 "This is a comment" 的 XML 批註。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XComment>
- [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
