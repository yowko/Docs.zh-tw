---
title: "建議的文件註解 (Visual Basic) 的 XML 標記 |Microsoft 文件"
ms.custom: 
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.XmlDocComment
dev_langs:
- VB
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
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
ms.openlocfilehash: c6a47c12bc24864ef6ac9f80054becad98ec97f1
ms.lasthandoff: 03/13/2017

---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建議可用於文件註解的 XML 標記 (Visual Basic)
[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)]編譯器可以處理 XML 檔案的程式碼中的文件註解。 您可以使用其他工具來處理文件的 XML 檔案。  
  
 XML 註解不能使用程式碼建構，例如型別和型別成員。 部分型別，如類型只有一個部分可以有 XML 註解，雖然其成員的註解不受限制。  
  
> [!NOTE]
>  文件註解不能套用至命名空間。 原因是，一個命名空間可以跨越多個組件，且並非所有的組件必須載入一次。  
  
 編譯器會處理任何有效的 XML 標記。 下列標記會提供使用者文件中的常用的功能。  
  
||||  
|---|---|---|  
|[\<c >](../../../visual-basic/language-reference/xmldoc/c.md)|[\<程式碼 >](../../../visual-basic/language-reference/xmldoc/code.md)|[\<範例 >](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<例外狀況 >](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<包含 >](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list>](../../../visual-basic/language-reference/xmldoc/list.md)|  
|[\<並行 >](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref >](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<權限 >](../../../visual-basic/language-reference/xmldoc/permission.md) <sup>1</sup>|[\<註解 >](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<傳回 >](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso >](../../../visual-basic/language-reference/xmldoc/seealso.md) <sup>1</sup>|[\<摘要 >](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam >](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<值 >](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 (<sup>1</sup>編譯器會驗證語法。)  
  
> [!NOTE]
>  如果您想要出現在文件註解文字的角括號時，使用`<`和`>`。 例如，字串`"<text in angle brackets>"`會顯示為`<text in angle``brackets>`。  
  
## <a name="see-also"></a>另請參閱  
 [記錄與 XML 程式碼](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [如何：建立 XML 文件](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)
