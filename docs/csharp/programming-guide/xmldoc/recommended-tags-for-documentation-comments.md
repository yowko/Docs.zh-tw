---
title: "建議使用的文件註解標籤 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "XML [C#]，標記"
  - "XML 文件 [C#]，標記"
ms.assetid: 6e98f7a9-38f4-4d74-b644-1ff1b23320fd
caps.latest.revision: 20
caps.handback.revision: 20
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 建議使用的文件註解標籤 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

C\# 編譯器會處理程式碼中的文件註解，並且以 XML 的格式將這些註解儲存在檔案中，而該檔案的名稱會可以在 **\/doc** 命令列選項中指定。  若要根據編譯器產生的檔案中最後一個檔案，您可以建立自訂工具，或使用一類工具 [沙堡](http://shfb.codeplex.com/)。  
  
 標記在程式碼建構 \(例如：型別與型別成員\) 上處理。  
  
> [!NOTE]
>  命名空間不能使用文件註解。  
  
 編譯器會處理任何合法的 XML 標記。  下列是在使用者文件中提供常用功能的標記。  
  
## 標記  
  
||||  
|-|-|-|  
|[\<c\>](../../../csharp/programming-guide/xmldoc/code-inline.md)|[\<para\>](../../../csharp/programming-guide/xmldoc/para.md)|[\<see\>](../Topic/%3Csee%3E%20\(C%23%20Programming%20Guide\).md)\*|  
|[\<code\>](../../../csharp/programming-guide/xmldoc/code.md)|[\<param\>](../../../csharp/programming-guide/xmldoc/param.md)\*|[\<seealso\>](../Topic/%3Cseealso%3E%20\(C%23%20Programming%20Guide\).md)\*|  
|[\<example\>](../../../csharp/programming-guide/xmldoc/example.md)|[\<paramref\>](../../../csharp/programming-guide/xmldoc/paramref.md)|[\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md)|  
|[\<exception\>](../../../csharp/programming-guide/xmldoc/exception.md)\*|[\<permission\>](../../../csharp/programming-guide/xmldoc/permission.md)\*|[\<typeparam\>](../../../csharp/programming-guide/xmldoc/typeparam.md)\*|  
|[\<include\>](../../../csharp/programming-guide/xmldoc/include.md)\*|[\<remarks\>](../../../csharp/programming-guide/xmldoc/remarks.md)|[\<typeparamref\>](../../../csharp/programming-guide/xmldoc/typeparamref.md)|  
|[\<list\>](../../../csharp/programming-guide/xmldoc/list.md)|[\<returns\>](../../../csharp/programming-guide/xmldoc/returns.md)|[\<value\>](../Topic/%3Cvalue%3E%20\(C%23%20Programming%20Guide\).md)|  
  
 \(\* 表示編譯器會驗證語法\)。  
  
 如果您要在文件註解的文字中顯示角括弧，請使用 `<` 和 `>`，如下列範例所示。  
  
```xml  
/// <summary cref="C < T >">  
/// </summary>  
```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [\/doc \(Process Documentation Comments\)](../../../csharp/language-reference/compiler-options/doc-compiler-option.md)   
 [XML 文件註解](../../../csharp/programming-guide/xmldoc/xml-documentation-comments.md)