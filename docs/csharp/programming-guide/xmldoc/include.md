---
title: "&lt;include&gt; (C# 程式設計手冊) | Microsoft Docs"
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
  - "include"
  - "<include>"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "<include> C# XML 標記"
  - "include C# XML 標記"
ms.assetid: a8a70302-6196-4643-bd09-ef33f411f18f
caps.latest.revision: 19
caps.handback.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# &lt;include&gt; (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

## 語法  
  
```  
<include file='filename' path='tagpath[@name="id"]' />  
```  
  
#### 參數  
 `filename`  
 為含有文件的 XML 檔案名稱。  可將檔案名稱加上路徑。  以單引號 \(' '\) 將 `filename` 括起來。  
  
 `tagpath`  
 `filename` 中導向標記 \(Tag\) `name` 的標記路徑。  以單引號 \(' '\) 將路徑括起來。  
  
 `name`  
 註解前面標記內的名稱規範。`name` 會有一個 `id`。  
  
 `id`  
 註解前面之標記的 ID。  以雙引號 \(" "\) 將 ID 括住。  
  
## 備註  
 \<include\> 標記讓您參考其他檔案內的註解，這些檔案描述了您原始程式碼中的型別以及成員。  除了將文件註解直接放置在您原始程式碼檔案中，您也可以使用這種方法。  將文件放在不同的檔案中，您可以對與原始程式碼分開存放的文件套用原始檔控制。  某人會有簽出的原始程式檔，而其他人則會有簽出的文件檔。  
  
 \<include\> 標記使用了 XML XPath 的語法。  請參閱 XPath 文件，以取得自訂 \<include\> 用途的方法。  
  
## 範例  
 這是多重檔案的範例。  第一個檔案使用 \<include\>，列於下方：  
  
 [!code-cs[csProgGuideDocComments#5](../../../csharp/programming-guide/xmldoc/codesnippet/CSharp/include_1.cs)]  
  
 第二個檔案 \(xml\_include\_tag.doc\) 包含下列的文件註解。  
  
```  
<MyDocs>  
  
<MyMembers name="test">  
<summary>  
The summary for this type.  
</summary>  
</MyMembers>  
  
<MyMembers name="test2">  
<summary>  
The summary for this other type.  
</summary>  
</MyMembers>  
  
</MyDocs>  
```  
  
## 程式輸出  
 當您使用下列命令列編譯 Test 和 Test2 類別時，就會產生下列輸出： `/doc:DocFileName.xml.`。在 Visual Studio 中，您可以在專案設計工具的 \[建置\] 窗格中指定 XML 文件註解選項。  當 C\# 編譯器看見 \<inclue\> 標記時，它會搜尋 xml\_include\_tag.doc 而非目前的來源檔案中的文件註解。  編譯器接著會產生 DocFileName.xml，例如 [Sandcastle](http://go.microsoft.com/fwlink/?LinkId=124061) \(英文\) 等文件工具就是取用這個檔案來產生最終的文件。  
  
```  
<?xml version="1.0"?>   
<doc>   
    <assembly>   
        <name>xml_include_tag</name>   
    </assembly>   
    <members>   
        <member name="T:Test">   
            <summary>   
The summary for this type.   
</summary>   
        </member>   
        <member name="T:Test2">   
            <summary>   
The summary for this other type.   
</summary>   
        </member>   
    </members>   
</doc>   
```  
  
## 請參閱  
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [建議使用的文件註解標籤](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md)