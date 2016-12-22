---
title: "No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39; | Microsoft Docs"
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
  - "bc30737"
  - "vbc30737"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30737"
ms.assetid: 3f40bacd-3fac-4741-b204-852f693d4340
caps.latest.revision: 11
caps.handback.revision: 11
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# No accessible &#39;Main&#39; method with an appropriate signature was found in &#39;&lt;name&gt;&#39;
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

命令列應用程式必須定義 `Sub Main`。  如果 `Main` 是在類別中定義，就必須宣告為 `Public Shared`；如果是在模組中定義，則宣告為 `Public`。  
  
 如需 `Main` 的詳細資訊，請參閱 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/zh-tw/9d030b60-e148-4366-a462-69532f02294c)。  
  
 **錯誤 ID︰**BC30737  
  
### 若要更正這個錯誤  
  
-   請為專案定義 `Public Sub Main` 程序。  只有在類別中定義時，才能將它宣告為 `Shared`。  
  
## 請參閱  
 [NIB: Visual Basic Version of Hello, World](http://msdn.microsoft.com/zh-tw/9d030b60-e148-4366-a462-69532f02294c)   
 [Structure of a Visual Basic Program](../../../visual-basic/programming-guide/program-structure/structure-of-a-visual-basic-program.md)   
 [Procedures](../../../visual-basic/programming-guide/language-features/procedures/index.md)