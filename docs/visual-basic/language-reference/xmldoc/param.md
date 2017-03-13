---
title: "&lt;param&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "param XML tag"
  - "<param> XML tag"
ms.assetid: 4e32e86f-f6f3-4301-b7fc-2f321fb54368
caps.latest.revision: 14
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 14
---
# &lt;param&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

定義參數名稱和描述。  
  
## 語法  
  
```  
<param name="name">description</param>  
```  
  
#### 參數  
 `name`  
 為方法參數的名稱。  以雙引號 \(" "\) 將名稱括起來。  
  
 `description`  
 參數的描述。  
  
## 備註  
 `<param>` 標記 \(Tag\) 應使用於方法宣告的註解中，以描述該方法的其中一個參數。  
  
 `<param>` 標記的文字便會出現於下列位置:  
  
-   參數 IntelliSense 資訊。  如需詳細資訊，請參閱[使用 IntelliSense](/visual-studio/ide/using-intellisense)。  
  
-   物件瀏覽器。  如需詳細資訊，請參閱[檢視程式碼的結構](/visual-studio/ide/viewing-the-structure-of-code)。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<param>` 標記來描述 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/param_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)