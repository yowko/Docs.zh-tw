---
title: "IsTrue Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.istrue"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "IsTrue operator"
  - "OrElse operator [Visual Basic]"
ms.assetid: b6cec0f2-61b1-4331-a7f0-4d07ee3179d6
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# IsTrue Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

判斷運算式是否為 `True`。  
  
 您無法在程式碼中明確呼叫 `IsTrue`，但 Visual Basic 編譯器 \(Compiler\) 可利用它從 `OrElse` 子句產生程式碼。  如果定義類別或結構，然後在 `OrElse` 子句中使用該型別的變數，則必須在該類別或結構上定義 `IsTrue`。  
  
 編譯器會將 `IsTrue` 和 `IsFalse` 運算子視為「*相符的配對*」。  這表示如果定義其中一個，也必須定義另一個。  
  
## IsTrue 的編譯器用途  
 定義類別或結構後，可在 `For`、`If`、`Else` `If` 或 `While` 陳述式中，或在 `When` 子句中，使用該型別的變數。  如果您這麼做，編譯器會要求運算子將型別轉換成 `Boolean` 值，如此它才能測試條件。  它會依下列順序搜尋適當的運算子：  
  
1.  從類別或結構至 `Boolean` 的擴展轉換運算子。  
  
2.  從類別或結構至 `Boolean?` 的擴展轉換運算子。  
  
3.  類別或結構上的 `IsTrue` 運算子。  
  
4.  不涉及從 `Boolean` 到 `Boolean?` 之轉換的 `Boolean?` 縮小轉換。  
  
5.  從類別或結構至 `Boolean` 的縮小轉換運算子。  
  
 如果您尚未定義任何 `Boolean` 轉換，或 `IsTrue` 運算子，編譯器會發出錯誤信號。  
  
> [!NOTE]
>  `IsTrue` 運算子可以「*多載*」，也就是，當運算元具備類別或結構的類型時，該類別或結構就可以重新定義其行為。  如果您的程式碼在這種類別或結構上使用此運算子，就一定要先瞭解其重新定義的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 範例  
 下列程式碼範例所定義的結構大綱包含 `IsFalse` 和 `IsTrue` 運算子的定義。  
  
 [!code-vb[VbVbalrOperators#28](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/istrue-operator_1.vb)]  
  
## 請參閱  
 [IsFalse Operator](../../../visual-basic/language-reference/operators/isfalse-operator.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [OrElse Operator](../../../visual-basic/language-reference/operators/orelse-operator.md)