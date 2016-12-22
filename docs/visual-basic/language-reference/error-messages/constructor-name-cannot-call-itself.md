---
title: "Constructor &#39;&lt;name&gt;&#39; cannot call itself | Microsoft Docs"
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
  - "bc30298"
  - "vbc30298"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC30298"
ms.assetid: 2d77b7f4-0640-4f89-9c65-f101fd2847c0
caps.latest.revision: 8
caps.handback.revision: 8
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Constructor &#39;&lt;name&gt;&#39; cannot call itself
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

類別或結構中的 `Sub New` 程序呼叫它本身。  
  
 建構函式的用途是在第一次建立類別或結構的執行個體時，初始化該執行個體。  一個類別或結構可以有多個建構函式，但前提是它們要具有不同的參數清單。  建構函式可以呼叫其他建構函式，以執行在它本身以外的功能。  不過，讓建構函式呼叫它本身是無意義的事情，事實上，這甚至可能造成無限遞迴 \(Infinite Recursion\)。  
  
 **錯誤 ID︰**BC30298  
  
### 若要更正這個錯誤  
  
1.  檢查要呼叫之建構函式的參數清單。  這個清單應該與發出呼叫之建構函式的參數清單不同。  
  
2.  如果您不想呼叫不同的建構函式，請移除整個 `Sub New` 呼叫。  
  
## 請參閱  
 [Object Lifetime: How Objects Are Created and Destroyed](../../../visual-basic/programming-guide/language-features/objects-and-classes/object-lifetime-how-objects-are-created-and-destroyed.md)