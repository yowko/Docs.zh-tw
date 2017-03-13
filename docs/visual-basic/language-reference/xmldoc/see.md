---
title: "&lt;see&gt; (Visual Basic) | Microsoft Docs"
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
  - "see XML tag"
  - "<see> XML tag"
ms.assetid: 7e18f60b-ef4a-4678-a797-5eb918635ca9
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;see&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定至另一個成員的連結。  
  
## 語法  
  
```  
<see cref="member"/>  
```  
  
#### 參數  
 `member`  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查特定程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。  `member` 須以用雙引號 \(" "\) 括住。  
  
## 備註  
 使用 `<see>` 標記 \(Tag\)，從文字中指定連結。  使用 [\<seealso\>](../../../visual-basic/language-reference/xmldoc/seealso.md)，來表示 \[請參閱\] 區段中所要出現的文字。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會在 `UpdateRecord` 註解區段中使用 `<see>` 標記，以參考 `DoesRecordExist` 方法。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/see_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)