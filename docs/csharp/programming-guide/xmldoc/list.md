---
title: "&lt;list&gt; (C# 程式設計手冊) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "list"
  - "<list>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<item> C# XML 標記"
  - "<list> C# XML 標記"
  - "<listheader> C# XML 標記"
  - "item C# XML 標記"
  - "list C# XML 標記"
  - "listheader C# XML 標記"
ms.assetid: c9620b1b-c2e6-43f1-ab88-8ab47308ffec
caps.latest.revision: 11
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 11
---
# &lt;list&gt; (C# 程式設計手冊)
## 語法  
  
```  
<list type="bullet" | "number" | "table">  
    <listheader>  
        <term>term</term>  
        <description>description</description>  
    </listheader>  
    <item>  
        <term>term</term>  
        <description>description</description>  
    </item>  
</list>  
```  
  
#### 參數  
 `term`  
 將定義於 `description` 中的詞彙。  
  
 `description`  
 為項目符號、編號清單中的項目或 `term` 的定義其中之一。  
  
## 備註  
 \<listheader\> 區塊用於定義表格或定義清單的標題列。  在定義表格時，您只需要提供一個詞彙項目做為標題。  
  
 清單中的每個項目都以 \<item\> 區塊來指定。  當建立定義清單時，您必須指定 `term` 和 `description`。  但是對於表格、項目符號清單或編號清單，則只需提供 `description` 的項目。  
  
 在清單或表格中可以有全部需要的 \<item\> 區塊。  
  
 使用 [\/doc](../../../csharp/language-reference/compiler-options/doc-compiler-option.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 [!code-cs[csProgGuideDocComments#6](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/list_1.cs)]  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)