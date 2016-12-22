---
title: "&lt;summary&gt; (Visual Basic) | Microsoft Docs"
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
  - "<summary> XML tag"
  - "summary XML tag"
ms.assetid: 861c847d-dd94-478a-aa23-bf4899cdc848
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &lt;summary&gt; (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指定成員的摘要。  
  
## 語法  
  
```  
<summary>description</summary>  
```  
  
#### 參數  
 `description`  
 為物件的摘要。  
  
## 備註  
 使用 `<summary>` 標記 \(Tag\)，來描述型別或型別成員。  使用 [\<remarks\>](../../../visual-basic/language-reference/xmldoc/remarks.md)，將補充資訊加入至型別描述。  
  
 `<summary>` 標記的文字是唯一的資訊來源有關型別和 IntelliSense 中也會顯示在物件瀏覽器。  如需物件瀏覽器的詳細資訊，請參閱 [檢視程式碼的結構](/visual-studio/ide/viewing-the-structure-of-code)。  
  
 使用 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md) 進行編譯，將文件註解處理為檔案。  
  
## 範例  
 這個範例會使用 `<summary>` 標記，來描述 `ResetCounter` 方法和 `Counter` 屬性。  
  
 [!code-vb[VbVbcnXmlDocComments#1](../../../visual-basic/language-reference/xmldoc/codesnippet/VisualBasic/summary_1.vb)]  
  
## 請參閱  
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)