---
title: "XML CDATA 常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralCdata
dev_langs:
- VB
helpviewer_keywords:
- CDATA literal [Visual Basic]
- XML CDATA literal [Visual Basic]
- XML literals [Visual Basic], CDATA
ms.assetid: 9eafb6a4-dd9d-4866-85e8-0654c65abc44
caps.latest.revision: 16
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
ms.openlocfilehash: 24e52bf203ff3df57e26137da24abcc2cb7e8e20
ms.lasthandoff: 03/13/2017

---
# <a name="xml-cdata-literal-visual-basic"></a>XML CDATA 常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XCData>物件。</xref:System.Xml.Linq.XCData>  
  
## <a name="syntax"></a>語法  
  
```  
<![CDATA[content]]>  
```  
  
## <a name="parts"></a>組件  
 `<![CDATA[`  
 必要項。 表示 XML CDATA 區段的開頭。  
  
 `content`  
 必要項。 XML CDATA 區段中顯示的文字內容。  
  
 `]]>`  
 必要項。 代表區段的結尾。  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XCData>物件。</xref:System.Xml.Linq.XCData>  
  
## <a name="remarks"></a>備註  
 XML CDATA 區段包含應該包括但不是剖析 xml，其中包含它的原始文字。 XML CDATA 區段可以包含任何文字。 這包括保留的 XML 字元。 XML CDATA 區段的結尾是序列"]] > 」。 這表示下列各點︰  
  
-   您無法在 XML CDATA 常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML CDATA 內容。  
  
-   XML CDATA 區段不可為巢狀，因為`content`不能包含值"]] > 」。  
  
 您可以將 XML CDATA 常值指派給變數，或將它包含在 XML 項目常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行，但不會使用行接續字元。 這可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML CDATA 常值轉換成呼叫<xref:System.Xml.Linq.XCData.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XCData.%23ctor%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立包含文字的 CDATA 區段 」 可以包含常值\<XML > 標記 」。  
  
 [!code-vb[VbXMLSamples #&23;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-cdata-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XCData></xref:System.Xml.Linq.XCData>   
 [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
