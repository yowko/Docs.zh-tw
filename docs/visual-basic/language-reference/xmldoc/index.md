---
title: 建議用於檔批註的 XML 標記
ms.date: 07/20/2015
f1_keywords:
- vb.XmlDocComment
helpviewer_keywords:
- tags, XML
- XML comments, recommended tags [Visual Basic]
- comments, recommended XML tags
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
ms.openlocfilehash: 9f877ee3fc9d616dc1e946293489a8aab96ac2e1
ms.sourcegitcommit: d2db216e46323f73b32ae312c9e4135258e5d68e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/22/2020
ms.locfileid: "90872789"
---
# <a name="recommended-xml-tags-for-documentation-comments-visual-basic"></a>建議可用於文件註解的 XML 標記 (Visual Basic)

Visual Basic 編譯器可以將程式碼中的檔批註處理成 XML 檔案。 您可以使用其他工具將 XML 檔案處理成檔。  
  
 XML 批註可在程式碼結構（例如類型和類型成員）上使用。 針對部分類型，只有類型的其中一個部分可以有 XML 批註，雖然批註其成員沒有任何限制。  
  
> [!NOTE]
> 檔批註無法套用至命名空間。 原因是某個命名空間可以跨越數個元件，而不是所有的元件都必須同時載入。  
  
 編譯器會處理任何有效 XML 的標記。 下列標記提供使用者檔中常用的功能。  
  
||||  
|---|---|---|  
|[\<c>](c.md)|[\<code>](code.md)|[\<example>](example.md)|  
|[\<exception>](exception.md)<sup>1</sup>|[\<include>](include.md)<sup>1</sup>|[\<list>](list.md)|  
|[\<para>](para.md)|[\<param>](param.md)<sup>1</sup>|[\<paramref>](paramref.md)|  
|[\<permission>](permission.md)<sup>1</sup>|[\<remarks>](remarks.md)|[\<returns>](returns.md)|  
|[\<see>](see.md)<sup>1</sup>|[\<seealso>](seealso.md)<sup>1</sup>|[\<summary>](summary.md)|  
|[\<typeparam>](typeparam.md)<sup>1</sup>|[\<value>](value.md)||  
  
  (<sup>1</sup> ：編譯器會驗證語法。 )   
  
> [!NOTE]
> 如果您想要讓角括弧出現在檔批註的文字中，請使用 `&lt;` 和 `&gt;` 。 例如，字串將會 `"&lt;text in angle brackets&gt;"` 顯示為 `<text in angle brackets>` 。  
  
## <a name="see-also"></a>另請參閱

- [使用 XML 加入程式碼註解](../../programming-guide/program-structure/documenting-your-code-with-xml.md)
- [-doc](../../reference/command-line-compiler/doc.md)
- [如何：建立 XML 文件](../../programming-guide/program-structure/how-to-create-xml-documentation.md)
