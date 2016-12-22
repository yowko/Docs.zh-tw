---
title: "Out of stack space (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/15/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vbrID28"
dev_langs: 
  - "VB"
ms.assetid: bfcd792b-ac29-4158-81fc-ea0c13f4ffa2
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Out of stack space (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

堆疊是記憶體工作區域，會隨著執行程式的需求量而動態地成長或縮小。  已超過堆疊的限制。  
  
### 若要更正這個錯誤  
  
1.  請檢查程序的巢狀結構是否太深。  
  
2.  確定遞迴程序會正確地終止。  
  
3.  如果區域變數需要的區域變數空間，比實際上可用的空間更大，請嘗試於模組層級中宣告部分變數。  您也可以在 `Property`、`Sub` 或 `Function` 等關鍵字前面加上 `Static`，以便於程序靜態中宣告所有變數。  或者您可以使用 `Static` 陳述式，於程序中宣告個別靜態變數。  
  
4.  請將某些固定長度字串重新定義為可變長度字串，因為固定長度字串使用的堆疊空間比可變長度字串來得多。  您也可以在不需要堆疊空間模組層級中定義字串。  
  
5.  請使用 \[`Calls`\] 對話方塊來檢視堆疊上有哪些現用程序，藉以查看巢狀 `DoEvents` 函式呼叫的數目。  
  
6.  請確定您並未藉由觸發某事件 \(該事件會呼叫堆疊上現有事件程序\)，而造成「事件串聯」\(Event Cascade\)。  事件串聯與未結束的遞迴程序呼叫相似，但較不明顯，因為是由 [!INCLUDE[vbprvb](../../../csharp/programming-guide/concepts/linq/includes/vbprvb_md.md)] 進行呼叫，而不是在程式碼中明確呼叫。  使用 \[`Calls`\] 對話方塊來檢視堆疊上有哪些作用中的程序。  
  
## 請參閱  
 [記憶體視窗](/visual-studio/debugger/memory-windows)