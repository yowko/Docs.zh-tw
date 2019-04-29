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
ms.openlocfilehash: 149bbac6d301a9c2f166d05698e3780171126cb3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61938641"
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
|`<!--`|必要項。 代表 XML 註解的開始。|  
|`content`|必要項。 XML 註解中所顯示的文字。 不能包含一系列的兩個連字號 （-） 或連字號結尾標記相鄰的結尾。|  
|`-->`|必要項。 代表 XML 註解的結尾。|  
  
## <a name="return-value"></a>傳回值  
 <xref:System.Xml.Linq.XComment> 物件。  
  
## <a name="remarks"></a>備註  
 XML 註解常值不包含文件內容;它們包含文件的相關資訊。 XML 註解區段結尾序列 」-->"。 這表示下列各點：  
  
- 因為內嵌的運算式分隔符號是有效的 XML 註解內容，您無法在 XML 註解常值中使用內嵌的運算式。  
  
- XML 註解區段不可為巢狀，因為`content`不能包含值"-->"。  
  
 您可以將 XML 註解常值指派給變數，或將它包含在 XML 元素常值。  
  
> [!NOTE]
>  XML 常值可以跨越多行，而不使用行接續字元。 這項功能可讓您從 XML 文件複製內容，並將它貼到 Visual Basic 程式直接。  
  
 Visual Basic 編譯器會將 XML 註解常值轉換成呼叫<xref:System.Xml.Linq.XComment.%23ctor%2A>建構函式。  
  
## <a name="example"></a>範例  
 下列範例會建立 XML 註解包含文字 「 這是註解 」。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XComment>
- [XML 項目常值](../../../visual-basic/language-reference/xml-literals/xml-element-literal.md)
- [XML 常值](../../../visual-basic/language-reference/xml-literals/index.md)
- [在 Visual Basic 中建立 XML](../../../visual-basic/programming-guide/language-features/xml/creating-xml.md)
