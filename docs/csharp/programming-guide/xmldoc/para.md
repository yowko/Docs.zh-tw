---
title: "&lt;para&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "<para>"
  - "para"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<para> C# XML 標記"
  - "para C# XML 標記"
ms.assetid: c74b8705-29df-40b1-bff5-237492b0e978
caps.latest.revision: 11
caps.handback.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;para&gt; (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 語法  
  
```  
<para>content</para>  
```  
  
#### 參數  
 `content`  
 為段落內的文字。  
  
## 備註  
 \<para\> 標記是使用於其他的標記內，例如：[\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md)、[\<remarks\>](../../../csharp/programming-guide/xmldoc/remarks.md) 或 [\<returns\>](../../../csharp/programming-guide/xmldoc/returns.md)，因此可以讓您增加結構至文字當中。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 請參閱 [\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md) 中使用 \<para\> 的範例。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)