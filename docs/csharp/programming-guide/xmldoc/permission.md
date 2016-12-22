---
title: "&lt;permission&gt; (C# 程式設計手冊) | Microsoft Docs"
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
  - "permission"
  - "<permission>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<permission> C# XML 標記"
  - "permission C# XML 標記"
ms.assetid: 769e93fe-8404-443f-bf99-577aa42b6a49
caps.latest.revision: 12
caps.handback.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;permission&gt; (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 語法  
  
```  
<permission cref="member">description</permission>  
```  
  
#### 參數  
 cref \= "`member`"  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查給定的程式碼項目是否存在，並在輸出的 XML 檔案中將 `member` 轉譯為 Canonical 項目名稱。 *member* 必須出現在雙引號 \(" "\) 中。  
  
 如需如何建立泛型型別的 cref 參考之詳細資訊，請參閱 [\<see\>](../Topic/%3Csee%3E%20\(C%23%20Programming%20Guide\).md)。  
  
 `description`  
 成員存取的描述。  
  
## 備註  
 \<permission\> 標記讓您記錄成員的存取。  <xref:System.Security.PermissionSet> 類別可讓您指定對成員的存取。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 [!code-cs[csProgGuideDocComments#8](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/permission_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)