---
title: "&lt;c&gt; (Visual Basic) | Microsoft Docs"
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
  - "c XML tag"
  - "<c> XML tag"
ms.assetid: 36ad5d1b-11f7-4012-8932-41962ac327d1
caps.latest.revision: 11
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 11
---
# &lt;c&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

表示描述內的文字是程式碼。  
  
## 語法  
  
```  
<c>text</c>  
```  
  
#### 參數  
  
|||  
|-|-|  
|參數|描述|  
|`text`|您要指定為程式碼的文字。|  
  
## 備註  
 `<c>` 標記讓您可以指出描述內的文字應該標記為程式碼。  使用 [\<code\>](../../../visual-basic/language-reference/xmldoc/code.md) 來表示要做為程式碼的多行。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例在摘要區段中使用 `<c>` 標記，表示 `Counter` 是程式碼。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/c_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)