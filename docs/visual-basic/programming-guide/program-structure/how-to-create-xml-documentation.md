---
title: "How to: Create XML Documentation in Visual Basic | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
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
  - "XML comments"
  - "XML documentation, creating"
ms.assetid: 27b5b06c-09b9-496a-8245-f9542d846230
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# How to: Create XML Documentation in Visual Basic
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

這個範例會顯示如何將 XML 文件註解加入至程式碼。  
  
 [!INCLUDE[note_settings_general](../../../csharp/language-reference/compiler-messages/includes/note_settings_general_md.md)]  
  
### 若要建立型別或成員的 XML 文件  
  
1.  在 \[**程式碼編輯器**\] 中，將游標置於要為其建立文件之型別或成員的上面一行。  
  
2.  輸入 `'''` \(三個單引號\)。  
  
     \[**程式碼編輯器**\] 中隨即會加入型別或成員的 XML 基本架構。  
  
3.  在適當的標記之間加入描述性資訊。  
  
    > [!NOTE]
    >  若要在 XML 文件區塊中加入多行文字，則每一行的開頭必須是 `'''`。  
  
4.  加入使用具有新 XML 文件註解之型別或成員的其他程式碼。  
  
     IntelliSense 會顯示型別或成員之 \<summary\> 標記內的文字。  
  
5.  編譯程式碼以產生包含文件註解的 XML 檔案。  如需詳細資訊，請參閱 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)。  
  
## 請參閱  
 [Documenting Your Code with XML](../../../visual-basic/programming-guide/program-structure/documenting-your-code-with-xml.md)   
 [XML Comment Tags](../../../visual-basic/language-reference/xmldoc/recommended-xml-tags-for-documentation-comments.md)   
 [\/doc](../../../visual-basic/reference/command-line-compiler/doc.md)