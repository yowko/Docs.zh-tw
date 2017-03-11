---
title: "&lt;seealso&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "cref"
  - "<seealso>"
  - "seealso"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<seealso> C# XML 標記"
  - "cref [C#]"
  - "cref [C#], 請參閱"
  - "交互參考 [C#], 標記"
  - "seealso C# XML 標記"
ms.assetid: 8e157f3f-f220-4fcf-9010-88905b080b18
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# &lt;seealso&gt; (C# 程式設計手冊)
## 語法  
  
```  
<seealso cref="member"/>  
```  
  
#### 參數  
 cref \= "`member`"  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查指定的程式碼項目是否存在，並將 `member` 傳遞給 XML 輸出檔案中的項目名稱。`member` 必須出現在雙引號 \(" "\) 中。  
  
 如需如何建立泛型型別的 cref 參考之詳細資訊，請參閱 [\<see\>](../../../csharp/programming-guide/xmldoc/see.md)。  
  
## 備註  
 \<seealso\> 標記讓您指定在 \[參閱\] 部分要出現的文字。  使用 [\<see\>](../../../csharp/programming-guide/xmldoc/see.md) 從文字中指定連結。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 請參閱 [\<summary\>](../../../csharp/programming-guide/xmldoc/summary.md) 中使用 \<seealso\> 的範例。  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)