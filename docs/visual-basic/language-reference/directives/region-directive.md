---
title: "#Region Directive | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.Region"
  - "vb.#Region"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "Visual Basic compiler, compiler directives"
  - "#region directive"
  - "region directive (#region)"
  - "#Region keyword"
ms.assetid: 90a6a104-3cbf-47d0-bdc4-b585d0921b87
caps.latest.revision: 14
caps.handback.revision: 14
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# #Region Directive
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

摺疊並隱藏 Visual Basic 檔案中的程式碼區段。  
  
## 語法  
  
```  
  
        #Region "identifier_string"  
#End Region  
```  
  
## 組件  
  
|||  
|-|-|  
|詞彙|定義|  
|`identifier_string`|必要項。  做為摺疊區域標題的字串。  區域預設會摺疊。|  
|`#End Region`|終止 `#Region` 區塊。|  
  
## 備註  
 使用 `#Region` 指示詞來指定程式碼區段，以在使用 Visual Studio 程式碼編輯器的大綱功能時展開或摺疊。  您可以將區域放在其他區域內 \(或 *巢狀化*\)，將類似的區域群組起來。  
  
## 範例  
 此範例使用 `#Region` 指示詞。  
  
 [!code-vb[VbVbalrConditionalComp#4](../../../visual-basic/language-reference/directives/codesnippet/VisualBasic/region-directive_1.vb)]  
  
## 請參閱  
 [\#If...Then...\#Else Directives](../../../visual-basic/language-reference/directives/if-then-else-directives.md)   
 [大綱](/visual-studio/ide/outlining)   
 [How to: Collapse and Hide Sections of Code](../../../visual-basic/programming-guide/program-structure/how-to-collapse-and-hide-sections-of-code.md)