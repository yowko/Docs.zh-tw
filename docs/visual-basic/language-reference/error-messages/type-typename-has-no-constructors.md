---
title: "Type &#39;&lt;typename&gt;&#39; has no constructors | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "bc30251"
  - "vbc30251"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30251"
ms.assetid: aff3e1df-abe6-4bc0-9abc-a1e70514c561
caps.latest.revision: 9
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 9
---
# Type &#39;&lt;typename&gt;&#39; has no constructors
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

類型不支援呼叫 `Sub New()`。  一個可能原因是編譯器或二進位檔案損毀。  
  
 **錯誤 ID︰**BC30251  
  
### 更正這個錯誤  
  
1.  如果類型是在不同專案中，或是在參考的檔案中，請重新安裝專案或檔案。  
  
2.  如果類型是在相同專案中，請重新編譯包含類型的組件。  
  
3.  如果問題重複發生，請重新安裝 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb-md.md)] 編譯器。  
  
4.  如果錯誤持續發生，請收集情況的相關資訊，並通知 Microsoft 產品支援服務。  
  
## 請參閱  
 [Objects and Classes](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)   
 [告訴我們](/visual-studio/ide/talk-to-us)