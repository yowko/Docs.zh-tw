---
title: "CType 函式 (Visual Basic) | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vb.CType"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "運算式轉換結果"
  - "明確資料類型轉換"
  - "CType 函式"
  - "轉換，運算式"
ms.assetid: dd4b29e7-6fa1-428c-877e-69955420bb72
caps.latest.revision: 22
caps.handback.revision: 22
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# CType 函式 (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

傳回運算式明確轉換成指定資料類型、物件、結構、類別或介面的結果。  
  
## 語法  
  
```  
CType(expression, typename)  
```  
  
## 組件  
 `expression`  
 任何有效的運算式。  如果 `expression` 值在 `typename` 允許的範圍外，Visual Basic 會擲回例外狀況。  
  
 `typename`  
 在 `Dim` 陳述式的 `As` 子句中合法的任何運算式，也就是任何資料類型、物件、結構、類別或介面的名稱。  
  
## 備註  
  
> [!TIP]
>  您也可以使用下列函式來執行類型轉換：  
>   
>  -   類型轉換函式，例如對特定資料類型執行轉換的 `CByte`、`CDbl` 和 `CInt`。  如需詳細資訊，請參閱 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)。  
> -   [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) 或 [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)。  這些運算子要求一個類型必須繼承自另一個類型或實作另一個類型。  與 `Object` 資料類型之間來回進行轉換時，它們可以提供比 `CType` 略微好的效能。  
  
 `CType` 是以內嵌方式編譯的，也就是說，轉換程式碼是評估運算式的部分程式碼。  在某些情況下，因為沒有呼叫程序執行轉換，程式碼執行得更快速。  
  
 如果沒有定義從 `expression` 到 `typename` 的轉換 \(例如，從 `Integer` 轉換為 `Date`\)，Visual Basic 會顯示編譯時期錯誤訊息。  
  
 若在執行階段發生轉換失敗，則擲回適當的例外狀況。  如果縮小轉換失敗，最可能發生 <xref:System.OverflowException> 結果。  如果未定義轉換，則擲回 <xref:System.InvalidCastException>。  例如，如果 `expression` 屬於類型 `Object`，且其執行階段類型並未轉換成 `typename`，就可能發生這種情況。  
  
 如果 `expression` 或 `typename` 的資料類型是已定義的類別或結構，您可以將該類別或結構上的 `CType` 定義為轉換運算子。  這會將 `CType` 當做「*多載運算子*」\(Overloaded Operator\)。  如果執行這個動作，就可以控制與類別或結構之間的轉換行為，包括可能擲回的例外狀況。  
  
## 多載化  
 也可以在程式碼外部所定義的類別或結構上多載 `CType` 運算子。  如果程式碼與此類類別或結構進行轉換，請務必了解其 `CType` 運算子的行為。  如需詳細資訊，請參閱 [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md)。  
  
## 轉換的動態物件  
 動態物件的類型轉換是由使用 <xref:System.Dynamic.DynamicObject.TryConvert%2A> 或 <xref:System.Dynamic.DynamicMetaObject.BindConvert%2A> 方法之使用者定義的動態轉換來執行。  如果您搭配動態物件使用，請使用 <xref:Microsoft.VisualBasic.Conversion.CTypeDynamic%2A> 方法轉換動態物件。  
  
## 範例  
 下列範例會使用 `CType` 函式來將運算式轉換為 `Single` 資料類型。  
  
 [!code-vb[VbVbalrFunctions#24](../../../visual-basic/language-reference/functions/codesnippet/VisualBasic/ctype-function_1.vb)]  
  
 如需其他範例，請參閱 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)。  
  
## 請參閱  
 <xref:System.OverflowException>   
 <xref:System.InvalidCastException>   
 [Type Conversion Functions](../../../visual-basic/language-reference/functions/type-conversion-functions.md)   
 [Conversion Functions](../../../visual-basic/language-reference/functions/conversion-functions.md)   
 [Operator Statement](../../../visual-basic/language-reference/statements/operator-statement.md)   
 [How to: Define a Conversion Operator](../Topic/How%20to:%20Define%20a%20Conversion%20Operator%20\(Visual%20Basic\).md)   
 [.NET Framework 中的類型轉換](../Topic/Type%20Conversion%20in%20the%20.NET%20Framework.md)