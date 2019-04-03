---
title: XML 文件常值 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: f58c1365e145166dfe122d455854d44526300a1e
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/02/2019
ms.locfileid: "58814623"
---
# <a name="xml-document-literal-visual-basic"></a>XML 文件常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XDocument>物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`encoding`|選擇性。 宣告的編碼文件會使用常值的文字。|  
|`standalone`|選擇性。 常值文字。 必須是"yes"或"no"。|  
|`piCommentList`|選擇性。 XML 處理指示和 XML 註解的清單。 會採用下列格式：<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 每個`piComment`可以是下列其中之一：<br /><br /> -   [XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。<br />-   [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。|  
|`rootElement`|必要項。 文件的根項目。 格式可以是下列其中一項：<br /><br /> <ul><li>[XML 元素常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</li><li>內嵌格式的運算式`<%=` `elementExp` `%>`。 `elementExp`傳回下列其中之一：<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> 物件。</li><li>集合，其中包含一個<xref:System.Xml.Linq.XElement>物件和任何數目<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件。</li></ul></li></ul><br /> 如需詳細資訊，請參閱 < [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XDocument> 物件。  
  
## <a name="remarks"></a>備註  
 XML 文件常值是由常值開頭的 XML 宣告識別。 雖然每個 XML 文件常值必須有一個根 XML 項目，但是它可以有任意數目的 XML 處理指示和 XML 註解。  
  
 XML 文件常值不能出現在 XML 項目。  
  
> [!NOTE]
>  XML 常值可以跨越多行，而不使用行接續字元。 這可讓您從 XML 文件複製內容，並將它貼到 Visual Basic 程式直接。  
  
 Visual Basic 編譯器會將 XML 文件常值轉換成呼叫<xref:System.Xml.Linq.XDocument.%23ctor%2A>和<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>建構函式。  
  
## <a name="example"></a>範例  
 下列範例會建立 XML 文件具有 XML 宣告、 處理指示、 註解和此項目包含另一個項目。  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)
- [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)
- [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
- [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
