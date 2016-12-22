---
title: "Narrowing (Visual Basic) | Microsoft Docs"
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
  - "vb.narrowing"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "conversions, type"
  - "type conversion"
  - "conversions, data type"
  - "Narrowing keyword"
  - "data type conversion"
ms.assetid: a207ee91-aca4-4771-b4e2-713f029bf2bb
caps.latest.revision: 10
caps.handback.revision: 10
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Narrowing (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

指出轉換運算子 \(`CType`\) 是否將類別或結構，轉換成可能無法保留原始類別或結構之部分可能值的型別。  
  
## 以 Narrowing 關鍵字轉換  
 除了 `Narrowing` 之外，轉換程序還必須指定 `Public Shared`。  
  
 在執行階段中進行的縮小轉換不一定會成功，可能會失敗並造成資料遺漏。  範例有將 `Long` 轉換成 `Integer`、將 `String` 轉換成 `Date`，以及將基底型別 \(Base Type\) 轉換成衍生型別 \(Derived Type\)。  最後一個是縮小轉換，因為基底型別可能不包含衍生型別的所有成員，因此不是衍生型別的執行個體。  
  
 如果 `Option Strict` 是 `On`，則使用的程式碼必須使用 `CType` 進行所有的縮小轉換。  
  
 `Narrowing` 關鍵字可用於以下內容中：  
  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
## 請參閱  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Widening](../../../visual-basic/language-reference/modifiers/widening.md)   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)   
 [Option Strict Statement](../../../visual-basic/language-reference/statements/option-strict-statement.md)