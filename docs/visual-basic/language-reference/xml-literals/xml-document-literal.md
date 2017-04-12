---
title: "XML 文件常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralDocument
dev_langs:
- VB
helpviewer_keywords:
- XML document literal [Visual Basic]
- XML literals [Visual Basic], document
- XML documents [Visual Basic], creating
- document literal [Visual Basic]
ms.assetid: f7bbee56-0911-41de-b907-96f20450137b
caps.latest.revision: 20
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 5d64faddad66eba4029969654388ba7df17e5854
ms.lasthandoff: 03/13/2017

---
# <a name="xml-document-literal-visual-basic"></a>XML 文件常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument>  
  
## <a name="syntax"></a>語法  
  
```  
<?xml version="1.0" [encoding="encoding"] [standalone="standalone"] ?>  
[ piCommentList ]  
rootElement  
[ piCommentList ]  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`encoding`|選擇項。 使用宣告編碼文件常值文字。|  
|`standalone`|選擇項。 常值文字。 必須是"yes"或"no"。|  
|`piCommentList`|選擇項。 XML 處理指示和 XML 註解的清單。 採用下列格式︰<br /><br /> `piComment [` `piComment` `... ]`<br /><br /> 每個`piComment`可以是下列其中之一︰<br /><br /> -   [XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)。<br />-   [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)。|  
|`rootElement`|必要項。 文件的根項目。 格式為下列其中一項︰<br /><br /> <ul><li>[XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)。</li><li>內嵌運算式格式`<%=` `elementExp` `%>`。 `elementExp`傳回下列其中之一︰<br /><br /> <ul><li><xref:System.Xml.Linq.XElement>物件。</xref:System.Xml.Linq.XElement></li><li>集合，其中包含一個<xref:System.Xml.Linq.XElement>物件和任意數目的<xref:System.Xml.Linq.XProcessingInstruction>和<xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment> </xref:System.Xml.Linq.XProcessingInstruction> </xref:System.Xml.Linq.XElement></li></ul></li></ul><br /> 如需詳細資訊，請參閱[XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XDocument>物件。</xref:System.Xml.Linq.XDocument>  
  
## <a name="remarks"></a>備註  
 常值開頭的 XML 宣告來識別 XML 文件常值。 雖然每個 XML 文件常值必須有一個根 XML 項目，它可以有任意數目的 XML 處理指示和 XML 註解。  
  
 XML 文件常值不能出現在 XML 項目。  
  
> [!NOTE]
>  XML 常值可以跨越多行程式碼，而不需使用行接續字元。 這可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 文件常值轉換成呼叫<xref:System.Xml.Linq.XDocument.%23ctor%2A>和<xref:System.Xml.Linq.XDeclaration.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XDeclaration.%23ctor%2A> </xref:System.Xml.Linq.XDocument.%23ctor%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立 XML 文件具有 XML 宣告、 處理指示、 註解和包含另一個項目。  
  
 [!code-vb[VbXMLSamples #&30;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-document-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XElement>   
 <xref:System.Xml.Linq.XProcessingInstruction></xref:System.Xml.Linq.XProcessingInstruction>   
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 <xref:System.Xml.Linq.XDocument></xref:System.Xml.Linq.XDocument>   
 [XML 處理指示常值](../../../visual-basic/language-reference/xml-literals/xml-processing-instruction-literal.md)   
 [XML 註解常值](../../../visual-basic/language-reference/xml-literals/xml-comment-literal.md)   
 [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)   
 [XML 中內嵌的運算式](../../../visual-basic/programming-guide/language-features/xml/embedded-expressions-in-xml.md)
