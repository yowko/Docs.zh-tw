---
title: 建議可用於文件註解的 XML 標記 (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 2d6519af8ca1a0e2d59131eec4d63646dce7318b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913510"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建議可用於文件註解的 XML 標記 (Visual Basic)
Visual Basic 編譯器可以將程式碼中的檔批註處理成 XML 檔案。 您可以使用其他工具, 將 XML 檔案處理成檔。  
  
 程式碼結構 (例如類型和類型成員) 允許 XML 批註。 對於部分類型, 只有類型的一個部分可以有 XML 批註, 雖然對其成員的批註沒有任何限制。  
  
> [!NOTE]
> 檔批註無法套用至命名空間。 原因是一個命名空間可以跨越數個元件, 而不是所有的元件都必須同時載入。  
  
 編譯器會處理任何有效的 XML 標記。 下列標記提供使用者檔中常用的功能。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission>](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|請參閱 > <sup>1</sup> [ \< ](../../../visual-basic/language-reference/xmldoc/see.md)|[\<seealso>](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>編譯器會驗證語法)。  
  
> [!NOTE]
> 如果您想要在檔批註的文字中出現角括弧, 請使用`&lt;`和`&gt;`。 例如, 字串`"&lt;text in angle brackets&gt;"`會顯示為`<text in angle brackets>`。  
  
## <a name="see-also"></a>另請參閱

- [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)
- [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)
- [如何：建立 XML 檔](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
