---
title: "Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;, =, &lt;&gt;, &lt;, &lt;=, &gt;, &gt;=, CType, IsTrue, IsFalse | Microsoft Docs"
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
  - "bc33000"
  - "vbc33000"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "BC33000"
ms.assetid: 15c5d8eb-3a8c-4141-8f41-33151afabf97
caps.latest.revision: 12
caps.handback.revision: 12
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# Operator declaration must be one of:  +,-,*,\,/,^, &amp;, Like, Mod, And, Or, Xor, Not, &lt;&lt;, &gt;&gt;, =, &lt;&gt;, &lt;, &lt;=, &gt;, &gt;=, CType, IsTrue, IsFalse
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

您可以只宣告適用於多載化 \(Overloading\) 的運算子。  下表會顯示您可以宣告的運算子。  
  
|型別|運算子|  
|--------|---------|  
|一元|`+`, `-`, `IsFalse`, `IsTrue`, `Not`|  
|Binary|`+`, `-`, `*`, `/`, `\`, `&`, `^`, `>>`, `<<`, `=`, `<>`, `>`, `>=`, `<`, `<=`, `And`, `Like`, `Mod`, `Or`, `Xor`|  
|轉換 \(一元\)|`CType`|  
  
 請注意，二元清單中的 `=` 運算子是比較運算子，而不是指派運算子。  
  
 **錯誤 ID：**BC33000  
  
### 若要更正這個錯誤  
  
1.  從一組可多載的運算子中選取運算子。  
  
2.  如果您需要能多載無法直接多載之運算子的功能，請建立 `Function` 程序以取得適當參數，並傳回適當的值。  
  
## 請參閱  
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)   
 [How to: Define an Operator](../../../visual-basic/programming-guide/language-features/procedures/how-to-define-an-operator.md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [Function Statement](../../../visual-basic/language-reference/statements/function-statement.md)