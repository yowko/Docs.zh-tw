---
title: "&lt;seealso&gt; (Visual Basic) | Microsoft Docs"
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
  - "<seealso> XML tag"
  - "seealso XML tag"
ms.assetid: 36050c95-1af2-4284-b9b6-1a70691ed978
caps.latest.revision: 10
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 10
---
# &lt;seealso&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定在＜請參閱＞一節中出現的連結。  
  
## 語法  
  
```  
<seealso cref="member"/>  
```  
  
#### 參數  
 `member`  
 對可以從目前編譯環境呼叫的成員或欄位的參考。  編譯器會檢查特定程式碼項目是否存在，並將 `member` 傳遞給輸出 XML 中的項目名稱。  `member` 須以用雙引號 \(" "\) 括住。  
  
## 備註  
 使用 `<seealso>` 標記 \(Tag\) 來指定想要出現在＜請參閱＞一節中的文字。  使用 [\<see\>](../../../visual-basic/language-reference/xmldoc/see.md) 從文字中指定連結。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會在 `DoesRecordExist` 註解一節中使用 `<seealso>` 標記，以參考 `UpdateRecord` 方法。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/seealso_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)