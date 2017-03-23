---
title: "&lt;see&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "<see>"
  - "see"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<see> C# XML 標記"
  - "cref [C#], <see> 標記"
  - "交互參考 [C#]"
  - "see C# XML 標記"
ms.assetid: 0200de01-7e2f-45c4-9094-829d61236383
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# &lt;see&gt; (C# 程式設計手冊)
## 語法  
  
```  
<see cref="member"/>  
```  
  
#### 參數  
 cref \= "`member`"  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查特定程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。*member* 需用雙引號 \(" "\) 括住。  
  
## 備註  
 \<see\> 標記讓您指定文字中的連結。   使用 [\<seealso\>](../../../csharp/programming-guide/xmldoc/seealso.md) 以指定要放置於 \[請參閱\] 區段的文字。  使用 [cref Attribute](../../../csharp/programming-guide/xmldoc/cref-attribute.md) 建立程式項目說明頁面的內部超連線。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
 下列範例顯示一個摘要區段中 \<see\> 標記。  
  
 [!code-cs[csProgGuideDocComments#12](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/see_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)