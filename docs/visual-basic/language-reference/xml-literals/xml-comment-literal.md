---
title: XML 文件常值
ms.date: 07/20/2015
f1_keywords:
- vb.XmlLiteralComment
helpviewer_keywords:
- comment literal [Visual Basic]
- XML comments, adding [Visual Basic]
- XML comment literal [Visual Basic]
- XML literals [Visual Basic], comment
ms.assetid: 634c1cee-5e01-48d0-88d7-2dd55e4a9e52
ms.openlocfilehash: 3272cc0f976d6e8819e51bb5d5fce73066007963
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90875192"
---
# <a name="xml-comment-literal-visual-basic"></a>XML 註解常值 (Visual Basic)

代表物件的常值 <xref:System.Xml.Linq.XComment> 。  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<!-- content -->  
```  
  
## <a name="parts"></a>組件  
  
|詞彙|定義|  
|---|---|  
|`<!--`|必要。 代表 XML 批註的開頭。|  
|`content`|必要。 要出現在 XML 批註中的文字。 不可包含兩個連字號的一連串 (--) 或以結束記號連續的連字號結尾。|  
|`-->`|必要。 代表 XML 批註的結尾。|  
  
## <a name="return-value"></a>傳回值  

 <xref:System.Xml.Linq.XComment> 物件。  
  
## <a name="remarks"></a>備註  

 XML 批註常值不包含檔內容;它們包含檔的相關資訊。 XML 批註區段以「-->」序列結尾。 這表示下列幾點：  
  
- 您無法在 XML 批註常值中使用內嵌運算式，因為內嵌運算式分隔符號是有效的 XML 批註內容。  
  
- XML 批註區段無法進行嵌套，因為 `content` 不能包含值 "-->"。  
  
 您可以將 XML 批註常值指派給變數，也可以將它包含在 XML 元素常值中。  
  
> [!NOTE]
> XML 常值可以跨多行，而不使用行接續字元。 這項功能可讓您從 XML 檔案複製內容，並將它直接貼到 Visual Basic 程式中。  
  
 Visual Basic 編譯器會將 XML 批註常值轉換為函式的呼叫 <xref:System.Xml.Linq.XComment.%23ctor%2A> 。  
  
## <a name="example"></a>範例  

 下列範例會建立包含文字「這是批註」的 XML 批註。  
  
 [!code-vb[VbXMLSamples#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbXMLSamples/VB/XMLSamples4.vb#9)]  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Xml.Linq.XComment>
- [XML 元素常值](xml-element-literal.md)
- [XML 常值](index.md)
- [在 Visual Basic 中建立 XML](../../programming-guide/language-features/xml/creating-xml.md)
