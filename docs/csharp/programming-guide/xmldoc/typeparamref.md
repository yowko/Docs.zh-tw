---
title: "&lt;typeparamref&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "typeparamref"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<typeparamref> C# XML 標記"
  - "typeparamref C# XML 標記"
ms.assetid: 6d8ffc58-12c5-4688-8db6-833a7ded5886
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 15
---
# &lt;typeparamref&gt; (C# 程式設計手冊)
## 語法  
  
```  
<typeparamref name="name"/>  
```  
  
#### 參數  
 `name`  
 型別參數的名稱。  以雙引號 \(" "\) 將名稱括起來。  
  
## 備註  
 如需泛用型別和方法中型別參數的詳細資訊，請參閱[泛型](../../../csharp/programming-guide/generics/index.md)。  
  
 使用這個標記讓文件檔的使用者能夠以某些個別方法 \(例如斜體\) 格式化文字。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 [!code-cs[csProgGuideDocComments#13](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/typeparamref_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)