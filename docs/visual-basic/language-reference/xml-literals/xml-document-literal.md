---
title: XML 文件常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralDocument
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
ms.openlocfilehash: 3a2182d2937827bc8dc45e22307a3668420261a2
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/04/2020
ms.locfileid: "84400198"
---
# <a name="xml-document-literal-visual-basic"></a>XML 文件常值 (Visual Basic)
代表物件的常值 <xref:System.Xml.Linq.XDocument> 。  
  
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
|`encoding`|選擇性。 常值文字，用來宣告檔所使用的編碼方式。|  
|`standalone`|選擇性。 常值文字。 必須是 "yes" 或 "no"。|  
|`piCommentList`|選擇性。 XML 處理指示和 XML 批註的清單。 採用下列格式：<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 每個都 `piComment` 可以是下列其中一項：<br /><br /> -   [XML 處理指示常](xml-processing-instruction-literal.md)值。<br />-   [XML 批註常](xml-comment-literal.md)值。|  
|`rootElement`|必要。 檔的根項目。 格式為下列其中一項：<br /><br /> <ul><li>[XML 元素常](xml-element-literal.md)值。</li><li>表單的內嵌運算式 `<%=` `elementExp` `%>` 。 會傳回 `elementExp` 下列其中一項：<br /><br /> <ul><li><xref:System.Xml.Linq.XElement> 物件。</li><li>包含一個 <xref:System.Xml.Linq.XElement> 物件和任意數目之 <xref:System.Xml.Linq.XProcessingInstruction> 和物件的集合 <xref:System.Xml.Linq.XComment> 。</li></ul></li></ul><br /> 如需詳細資訊，請參閱[XML 中的內嵌運算式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XDocument> 物件。  
  
## <a name="remarks"></a>備註  
 XML 檔常值是由文字開頭的 XML 宣告所識別。 雖然每個 XML 檔常值必須只有一個根 XML 元素，但它可以有任意數目的 XML 處理指示和 XML 批註。  
  
 Xml 檔常值不能出現在 XML 元素中。  
  
> [!NOTE]
> XML 常值可以跨越多行，而不需要使用行接續字元。 這可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。  
  
 Visual Basic 編譯器會將 XML 檔常值轉換成呼叫 <xref:System.Xml.Linq.XDocument.%23ctor%2A> 和構造函式 <xref:System.Xml.Linq.XDeclaration.%23ctor%2A> 。  
  
## <a name="example"></a>範例  
 下列範例會建立 XML 檔，其中具有 XML 宣告、處理指示、批註，以及包含另一個元素的專案。  
  
 [!code-vb[VbXMLSamples#30](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples13.vb#30)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XElement>
- <xref:System.Xml.Linq.XProcessingInstruction>
- <xref:System.Xml.Linq.XComment>
- <xref:System.Xml.Linq.XDocument>
- [XML 處理指示常值](xml-processing-instruction-literal.md)
- [XML 文件常值](xml-comment-literal.md)
- [XML 元素常值](xml-element-literal.md)
- [XML 常值](index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
- [XML 中內嵌的運算式](../../programming-guide/language-features/xml/embedded-expressions-in-xml.md)
