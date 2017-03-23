---
title: "XML 註解常值 (Visual Basic) |Microsoft 文件"
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlLiteralComment
dev_langs:
- VB
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
caps.latest.revision: 19
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
ms.openlocfilehash: 88cfb984be42345ae1e5c998cf82aa1415d2455e
ms.lasthandoff: 03/13/2017

---
# <a name="xml-comment-literal-visual-basic"></a>XML 註解常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment>  
  
## <a name="syntax"></a>語法  
  
```  
<!-- content -->  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`<!--`|必要項。 代表 XML 註解的開始。|  
|`content`|必要項。 出現在 XML 註解中的文字。 不能包含一系列的兩個連字號 （-） 或連字號相鄰結尾標記的結束。|  
|`-->`|必要項。 代表 XML 註解的結尾。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XComment>物件。</xref:System.Xml.Linq.XComment>  
  
## <a name="remarks"></a>備註  
 XML 註解常值不包含文件內容。其中包含文件的相關資訊。 XML 註解區段結尾的 「--> 」 順序。 這表示下列各點︰  
  
-   您無法在 XML 註解常值中使用內嵌的運算式，因為內嵌的運算式分隔符號是有效的 XML 註解內容。  
  
-   XML 註解區段不可為巢狀，因為`content`不能包含"-->"的值。  
  
 您可以將 XML 註解常值指派給變數，或將它包含在 XML 項目常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行程式碼，而不需使用行接續字元。 這項功能可讓您從 XML 文件內容複製並貼上直接至[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]程式。  
  
 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器會將 XML 註解常值轉換成呼叫<xref:System.Xml.Linq.XComment.%23ctor%2A>建構函式。</xref:System.Xml.Linq.XComment.%23ctor%2A>  
  
## <a name="example"></a>範例  
 下列範例會建立包含文字的 XML 註解 「 這是註解 」。  
  
 [!code-vb[VbXMLSamples #&9;](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XComment></xref:System.Xml.Linq.XComment>   
 [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)   
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)   
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
