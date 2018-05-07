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
ms.openlocfilehash: 60c354215c627683fd6c69d9ca66fc115c26ccda
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="xml-comment-literal-visual-basic"></a>XML 註解常值 (Visual Basic)
常值代表<xref:System.Xml.Linq.XComment>物件。  
  
## <a name="syntax"></a>語法  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`<!--`|必要。 代表 XML 註解的開始。|  
|`content`|必要。 要出現在 XML 註解的文字。 不能包含一系列的兩個連字號 （-） 或連字號相鄰結尾標記的結尾。|  
|`-->`|必要。 代表 XML 註解的結尾。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XComment> 物件。  
  
## <a name="remarks"></a>備註  
 XML 註解常值不包含文件內容。其中包含文件的相關資訊。 XML 註解區段以序列"-->"結尾。 這表示下列各點：  
  
-   因為內嵌的運算式分隔符號是有效的 XML 註解內容，您無法在 XML 註解常值中使用內嵌的運算式。  
  
-   XML 註解區段不可為巢狀，因為`content`不能用來包含"-->"的值。  
  
 您可以將 XML 註解常值指派給變數，或您可以包含在 XML 元素常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行，而不使用行接續字元。 這項功能可讓您從 XML 文件內容複製並貼上直接在 Visual Basic 程式。  
  
 Visual Basic 編譯器會將 XML 註解常值轉換成呼叫<xref:System.Xml.Linq.XComment.%23ctor%2A>建構函式。  
  
## <a name="example"></a>範例  
 下列範例會建立包含文字的 XML 註解"This is 註解"。  
  
 [!code-vb[VbXMLSamples#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/xml-comment-literal_1.vb)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Xml.Linq.XComment>  
 [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)  
 [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)  
 [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
