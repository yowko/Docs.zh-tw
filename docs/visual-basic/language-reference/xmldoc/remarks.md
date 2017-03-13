---
title: "&lt;remarks&gt; (Visual Basic) | Microsoft Docs"
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
  - "<remarks> XML tag"
  - "remarks XML tag"
ms.assetid: c6241773-a7ed-41c9-9a8b-9722a0c606a9
caps.latest.revision: 13
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 13
---
# &lt;remarks&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

指定成員的備註區段。  
  
## 語法  
  
```  
<remarks>description</remarks>  
```  
  
#### 參數  
 `description`  
 為成員的描述。  
  
## 備註  
 使用 `<remarks>` 標記 \(Tag\) 可加入型別的相關資訊，補充以 [\<summary\>](../../../visual-basic/language-reference/xmldoc/summary.md) 指定的資訊。  
  
 這項資訊會出現在物件瀏覽器。  如需物件瀏覽器的詳細資訊，請參閱 [檢視程式碼的結構](/visual-studio/ide/viewing-the-structure-of-code)。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<remarks>` 標記來解釋 `UpdateRecord` 方法的執行內容。  
  
 [!code-vb[VbVbcnXmlDocComments#6](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/remarks_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)