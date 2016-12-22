---
title: "Recommended XML Tags for Documentation Comments (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.XmlDocComment"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "tags, XML"
  - "XML comments, recommended tags [Visual Basic]"
  - "comments, recommended XML tags"
ms.assetid: 294e0736-ff1e-498e-af83-6db71ed41a72
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Recommended XML Tags for Documentation Comments (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

[!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 編譯器會將您程式碼中的文件註解處理為一個 XML 檔案。  您可以使用其他工具，將 XML 檔案處理成文件。  
  
 程式碼建構 \(例如型別與型別成員\) 上允許 XML 註解。  對於部分型別而言，僅有型別的其中一個部分可以具有 XML 註解，但是在註解成員方面則沒有限制。  
  
> [!NOTE]
>  文件註解不可套用至命名空間。  原因在於一個命名空間可以橫跨多個組件 \(Assembly\)，但不一定需要同時載入所有組件。  
  
 編譯器會處理任何有效的 XML 標記。  下列是在使用者文件中提供常用功能的標記  
  
||||  
|-|-|-|  
|[\<c\>](../../../visual-basic/language-reference/xmldoc/c.md)|[\<code\>](../../../visual-basic/language-reference/xmldoc/code.md)|[\<example\>](../../../visual-basic/language-reference/xmldoc/example.md)|  
|[\<exception\>](../../../visual-basic/language-reference/xmldoc/exception.md) <sup>1</sup>|[\<include\>](../../../visual-basic/language-reference/xmldoc/include.md) <sup>1</sup>|[\<list\>](../Topic/%3Clist%3E%20\(Visual%20Basic\).md)|  
|[\<para\>](../../../visual-basic/language-reference/xmldoc/para.md)|[\<param\>](../../../visual-basic/language-reference/xmldoc/param.md) <sup>1</sup>|[\<paramref\>](../../../visual-basic/language-reference/xmldoc/paramref.md)|  
|[\<permission\>](../Topic/%3Cpermission%3E%20\(Visual%20Basic\).md) <sup>1</sup>|[\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md)|[\<returns\>](../../../visual-basic/language-reference/xmldoc/returns.md)|  
|[\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) <sup>1</sup>|[\<seealso\>](../Topic/%3Cseealso%3E%20\(Visual%20Basic\).md) <sup>1</sup>|[\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md)|  
|[\<typeparam\>](../../../visual-basic/language-reference/xmldoc/typeparam.md) <sup>1</sup>|[\<value\>](../../../visual-basic/language-reference/xmldoc/value.md)||  
  
 \(<sup>1</sup> 編譯器會驗證語法。\)  
  
> [!NOTE]
>  如果您要在文件註解的文字中顯示角括弧，請使用 `<` 和 `>`。  例如，字串 `"<text in angle brackets>"` 會顯示為 `<text in angle` `brackets>`。  
  
## 請參閱  
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)   
 [How to: Create XML Documentation](../../../visual-basic/programming-guide/program-structure/how-to-create-xml-documentation.md)