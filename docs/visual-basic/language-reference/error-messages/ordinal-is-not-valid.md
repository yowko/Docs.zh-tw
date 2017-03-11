---
title: "Ordinal is not valid | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vbrID452"
dev_langs: 
  - "VB"
ms.assetid: 7459562b-cd4f-4590-95e0-6126ae3589a5
caps.latest.revision: 8
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 8
---
# Ordinal is not valid
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

您呼叫動態連結程式庫 \(DLL\)，表示要使用 `#num` 語法來使用數字而非程序名稱。  這個錯誤可能由下列原因所致：  
  
-   嘗試將 `#num` 運算式轉換為序數時失敗。  
  
-   指定的 `#num` 並沒有指定 DLL 中的任何函式。  
  
-   型別程式庫有一項無效的宣告，導致於內部使用無效的序數編號。  
  
### 若要更正這個錯誤  
  
1.  請確定運算式代表有效數字，或者以名稱呼叫程序。  
  
2.  請確定 `#num` 可識別 DLL 中的有效函式。  
  
3.  請以程式碼註解的方式，來隔離導致問題的程序呼叫。  為程序撰寫 `Declare` 陳述式，並且向型別程式庫廠商報告該問題。  
  
## 請參閱  
 [Declare Statement](../../../visual-basic/language-reference/statements/declare-statement.md)