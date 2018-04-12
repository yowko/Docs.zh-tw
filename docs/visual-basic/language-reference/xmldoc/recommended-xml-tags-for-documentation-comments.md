---
title: 建議可用於文件註解的 XML 標記 (Visual Basic)
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 54712deb8bb2a5ed1e7b1f5fb8aa073dcdaf76d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建議可用於文件註解的 XML 標記 (Visual Basic)
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]編譯器可處理為 XML 檔案的程式碼中的文件註解。 您可以使用其他工具處理文件的 XML 檔案。  
  
 XML 註解程式碼建構，例如型別上允許和類型成員。 針對部分類型，只有一個部分的型別可以有 XML 註解，雖然其成員標記為註解不受限制。  
  
> [!NOTE]
>  文件註解不能套用至命名空間。 原因是，一個命名空間可以跨數個組件，而並非所有的組件必須載入在相同的時間。  
  
 編譯器會先處理任何有效的 XML 標記。 下列標記會提供使用者文件中的常用的功能。  
  
||||  
|---|---|---|  
|[\<c>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<例外狀況 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<包含 >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<para>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param >](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<權限 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<remarks>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<請參閱 >](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<另請參閱 >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<summary>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>編譯器會驗證語法。)  
  
> [!NOTE]
>  如果您想要出現在文件註解文字的角括號時，使用`<`和`>`。 例如，字串`"<text in angle brackets>"`將會顯示為`<text in angle``brackets>`。  
  
## <a name="see-also"></a>另請參閱  
 [使用 XML 加入程式碼註解](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)  
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)  
 [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
