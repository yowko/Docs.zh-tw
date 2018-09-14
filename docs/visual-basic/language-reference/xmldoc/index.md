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
ms.openlocfilehash: 3b2dec4224006d35fb9add11e170b9dcbeeafcf3
ms.sourcegitcommit: 76a304c79a32aa13889ebcf4b9789a4542b48e3e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/14/2018
ms.locfileid: "45583549"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建議可用於文件註解的 XML 標記 (Visual Basic)
Visual Basic 編譯器可以處理 XML 檔案的程式碼中的文件註解。 您可以使用其他工具來處理文件的 XML 檔案。  
  
 XML 註解不能使用的程式碼建構，例如類型和類型成員。 部分型別，只有一個部分的型別可以有 XML 註解，雖然沒有註解成員沒有限制。  
  
> [!NOTE]
>  文件註解不能套用至命名空間。 原因會是一個命名空間可以跨數個組件，而且並非所有的組件需要載入一次。  
  
 編譯器會處理任何標記，來有效的 XML。 下列標記提供使用者文件中的常用的功能。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<例外狀況 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<包含 >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<權限 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<請參閱 >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>編譯器會驗證語法。)  
  
> [!NOTE]
>  如果您想要括弧出現在文件註解文字中，使用`&lt;`和`&gt;`。 例如，字串`"&lt;text in angle brackets&gt;"`會顯示為`<text in angle brackets>`。  
  
## <a name="see-also"></a>另請參閱  
 [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
