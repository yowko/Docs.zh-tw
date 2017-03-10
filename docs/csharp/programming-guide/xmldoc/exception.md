---
title: "&lt;exception&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "exception"
  - "<exception>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<exception> C# XML 標記"
  - "exception C# XML 標記"
ms.assetid: dd73aac5-3c74-4fcf-9498-f11bff3a2f3c
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# &lt;exception&gt; (C# 程式設計手冊)
## 語法  
  
```  
<exception cref="member">description</exception>  
```  
  
#### 參數  
 cref \= "`member`"  
 一個可以用於目前編譯環境例外狀況的參考。  編譯器會檢查特定的例外狀況是否存在，並在輸出 XML 中將 `member` 轉譯為正式的項目名稱。  `member` 須以用雙引號 \(" "\) 括住。  
  
 如需如何建立泛型型別之 cref 參考的詳細資訊，請參閱 [\<see\>](../../../csharp/programming-guide/xmldoc/see.md)。  
  
 `description`  
 例外狀況的描述。  
  
## 備註  
 這個 \<exception\> 標記讓您指定可以擲出哪些例外狀況，  這個標記可以套用至方法、屬性、事件和索引子的定義。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
 如需例外狀況處理的詳細資訊，請參閱[例外狀況和例外狀況處理](../../../csharp/programming-guide/exceptions/exceptions-and-exception-handling.md)。  
  
## 範例  
 [!code-cs[csProgGuideDocComments#4](../../../csharp/programming-guide/xmldoc/codesnippet/csharp/exception_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)