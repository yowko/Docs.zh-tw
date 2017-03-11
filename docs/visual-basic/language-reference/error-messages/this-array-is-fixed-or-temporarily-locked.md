---
title: "This array is fixed or temporarily locked (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID10"
dev_langs: 
  - "VB"
ms.assetid: de6713a6-51d7-4edb-8515-d5fb544e2091
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# This array is fixed or temporarily locked (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

這個錯誤可能由下列原因所致：  
  
-   使用 `ReDim` 來變更固定大小陣列的元素數量。  
  
-   將模組層次動態陣列重新維度化，其中該陣列的一個元素已被當做引數傳遞到程序中。  如果元素已經傳遞，則會鎖定陣列，以防止在程序中為參考參數配置的記憶體遭到解除。  
  
-   嘗試指派某一值至包含陣列的 `Variant` 變數，但該 `Variant` 目前已被鎖定。  
  
### 若要更正這個錯誤  
  
1.  請使用 `ReDim` \(如果陣列是在程序中宣告的\) 宣告原始陣列，而將其設定為動態的而非固定的，或者進行宣告但不指定元素數目 \(如果陣列是在模組層次中宣告的\)。  
  
2.  請判斷您是否真的需要傳遞該元素，因為在模組內所有程序中都可以看到該元素。  
  
3.  請判斷鎖定 `Variant` 的來源並進行修正。  
  
## 請參閱  
 [陣列](../../../visual-basic/programming-guide/language-features/arrays/index.md)