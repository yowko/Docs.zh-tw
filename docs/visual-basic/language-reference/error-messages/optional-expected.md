---
title: "&#39;Optional&#39; expected | Microsoft Docs"
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
  - "bc30202"
  - "vbc30202"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30202"
ms.assetid: 6f75060c-2db4-4a79-b5d1-5780c09a74cd
caps.latest.revision: 9
caps.handback.revision: 9
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# &#39;Optional&#39; expected
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

程序宣告中的選擇性引數之後加上一個必要的引數。  選擇性引數之後的每個引數必須是選擇性的。  
  
 **錯誤 ID：**BC30202  
  
### 若要更正這個錯誤  
  
1.  如果引數變成是必須的，請將它移動到引數清單的第一個選擇性引數之前。  
  
2.  如果引數是選擇性的，請使用 `Optional` 關鍵字。  
  
## 請參閱  
 [Optional Parameters](../../../visual-basic/programming-guide/language-features/procedures/optional-parameters.md)