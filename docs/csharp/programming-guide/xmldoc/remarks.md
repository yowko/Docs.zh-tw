---
title: "&lt;remarks&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "remarks"
  - "<remarks>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<remarks> C# XML 標記"
  - "remarks C# XML 標記"
ms.assetid: f8641391-31f3-4735-af7a-c502a5b6a251
caps.latest.revision: 15
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 13
---
# &lt;remarks&gt; (C# 程式設計手冊)
## 語法  
  
```  
<remarks>description</remarks>  
```  
  
#### 參數  
 `Description`  
 為成員的描述。  
  
## 備註  
 \<remarks\> 標記可用於加入型別的相關資訊，補充以 [\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md) 指定的資訊。  [Object Browser Window](http://msdn.microsoft.com/zh-tw/3c7f1673-1f0d-41b1-94ca-a3dcfcb82cda)會顯示此資訊。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 [!code-cs[csProgGuideDocComments#9](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/remarks_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)