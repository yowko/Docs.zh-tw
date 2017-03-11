---
title: "&lt;typeparam&gt; (Visual Basic) | Microsoft Docs"
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
  - "typeparam XML tag"
  - "<typeparam> XML tag"
ms.assetid: 1bb5ba78-f060-478c-905c-77a2e43639af
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# &lt;typeparam&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

定義型別參數名稱和說明。  
  
## 語法  
  
```  
<typeparam name="name">description</typeparam>  
```  
  
#### 參數  
 `name`  
 型別參數的名稱。  以雙引號 \(" "\) 將名稱括起來。  
  
 `description`  
 型別參數的描述。  
  
## 備註  
 在泛型型別或泛型成員宣告的註解中使用 `<typeparam>` 標記，說明其中一個型別參數。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<typeparam>` 標記，說明 `id` 參數。  
  
 [!code-vb[VbVbcnXmlDocComments#8](../../../visual-basic/language-reference/xmldoc/codesnippet/visualbasic/typeparam_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)