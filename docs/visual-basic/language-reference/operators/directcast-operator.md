---
title: "DirectCast Operator (Visual Basic) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-visual-basic"
ms.topic: "article"
f1_keywords: 
  - "vb.directCast"
  - "directCast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "DirectCast keyword"
ms.assetid: 63e5a1d0-4d9e-4732-bf8f-e90c0c8784b8
caps.latest.revision: 23
author: "stevehoag"
ms.author: "shoag"
caps.handback.revision: 23
---
# DirectCast Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../visual-basic/includes/vs2017banner.md)]

依據繼承或實作引入型別轉換作業。  
  
## 備註  
 `DirectCast` 不會將 Visual Basic 執行階段 Helper 常式用於轉換，因此在資料型別 `Object` 間進行轉換時，它可提供的效能比 `CType` 還好。  
  
 使用 `DirectCast` 關鍵字的方式與使用 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md) 和 [TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md) 關鍵字的方式相同。  您提供的第一個引數是運算式，第二個引數則是用來轉換它的型別。  `DirectCast` 需要這兩個引數之資料型別之間的繼承或實作關聯性。  這表示其中一個型別必須繼承自另一個型別或實作另一個型別。  
  
## 錯誤和失敗  
 如果 `DirectCast` 偵測到沒有繼承或實作關聯性存在，則會產生編譯器錯誤。  但沒有編譯器錯誤並不保證轉換成功。  如果正在縮小所要的轉換，則在執行階段可能會失敗。  如果發生這種情況，執行階段會擲回 <xref:System.InvalidCastException> 錯誤。  
  
## 轉換關鍵字  
 型別轉換關鍵字的比較如下。  
  
|||||  
|-|-|-|-|  
|Keyword|資料型別|引數關聯性|執行階段失敗|  
|[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)|任何資料型別|必須在這兩個資料型別間定義擴展或縮小轉換|擲回 <xref:System.InvalidCastException>|  
|`DirectCast`|任何資料型別|其中一個型別必須繼承自另一個型別或實作另一個型別|擲回 <xref:System.InvalidCastException>|  
|[TryCast Operator](../../../visual-basic/language-reference/operators/trycast-operator.md)|僅限參考型別 \(Reference Type\)|其中一個型別必須繼承自另一個型別或實作另一個型別|傳回 [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## 範例  
 下列範例會示範 `DirectCast` 的兩種使用方法，其中一個會在執行階段失敗，而另一個會成功。  
  
 [!code-vb[VbVbalrKeywords#1](../../../visual-basic/language-reference/codesnippet/visualbasic/directcast-operator_1.vb)]  
  
 在先前的範例中，`q` 的執行階段型別為 `Double`。  `CType` 會成功，因為 `Double` 可以轉換為 `Integer`。  不過，第一個 `DirectCast` 會在執行階段失敗，原因是 `Double` 的執行階段型別與 `Integer` 間沒有繼承關聯性，即使轉換存在也一樣。  第二個 `DirectCast` 會成功，原因是它會從型別 <xref:System.Windows.Forms.Form> 轉換成型別 <xref:System.Windows.Forms.Control> \(<xref:System.Windows.Forms.Form> 是由此繼承\)。  
  
## 請參閱  
 <xref:System.Convert.ChangeType%2A?displayProperty=fullName>   
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)