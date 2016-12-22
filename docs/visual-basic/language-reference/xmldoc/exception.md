---
title: "&lt;exception&gt; (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "<exception> XML tag"
  - "exception XML tag"
ms.assetid: c0517549-171e-4dae-ab88-a9c1700b6eee
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;exception&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定要擲回的例外狀況。  
  
## 語法  
  
```  
<exception cref="member">description</exception>  
```  
  
#### 參數  
 `member`  
 一個可以用於目前編譯環境例外狀況的參考。  編譯器會檢查特定的例外狀況是否存在，並在輸出 XML 中將 `member` 轉譯為正式的項目名稱。  `member` 須以用雙引號 \(" "\) 括住。  
  
 `description`  
 一段說明文字。  
  
## 備註  
 使用 `<exception>` 標記 \(Tag\)，來指定要擲回的例外狀況。  並套用在方法定義上。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<exception>` 標記，來說明 `IntDivide` 函式能擲回的例外狀況。  
  
 [!code-vb[VbVbcnXmlDocComments#3](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/exception_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)