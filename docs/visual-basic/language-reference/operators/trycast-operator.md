---
title: "TryCast Operator (Visual Basic) | Microsoft Docs"
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
  - "vb.trycast"
  - "trycast"
dev_langs: 
  - "VB"
helpviewer_keywords: 
  - "TryCast keyword"
ms.assetid: d1ef5d47-fef4-491e-b014-1d910628f65c
caps.latest.revision: 17
caps.handback.revision: 17
author: "stevehoag"
ms.author: "shoag"
manager: "wpickett"
---
# TryCast Operator (Visual Basic)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

引入不會擲回例外狀況的型別轉換作業。  
  
## 備註  
 如果轉換嘗試失敗，`CType` 和 `DirectCast` 兩者會擲回 <xref:System.InvalidCastException> 錯誤。  這樣可能會影響應用程式的效能。  `TryCast` 會傳回 [Nothing](../../../visual-basic/language-reference/nothing.md)，如此您就不需處理可能的例外狀況，只需針對 `Nothing` 測試傳回的結果。  
  
 使用 `TryCast` 關鍵字的方式與使用 [CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md) 和 [DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md) 關鍵字相同。  您提供的第一個引數是運算式，第二個引數則是用來轉換它的型別。  `TryCast` 只能在參考型別上操作，例如類別和介面。  它需要兩個型別之間的繼承或實作 \(Implementation\) 關係。  這表示其中一個型別必須繼承自另一個型別或實作另一個型別。  
  
## 錯誤和失敗  
 如果 `TryCast` 未偵測到繼承或實作關聯性，則會產生編譯器錯誤。  但沒有編譯器錯誤並不保證轉換成功。  如果正在縮小所要的轉換，則在執行階段可能會失敗。  若是這種情況，`TryCast` 會傳回 [Nothing](../../../visual-basic/language-reference/nothing.md)。  
  
## 轉換關鍵字  
 型別轉換關鍵字的比較如下。  
  
|||||  
|-|-|-|-|  
|Keyword|資料型別|引數關聯性|執行階段失敗|  
|[CType 函式](../../../visual-basic/language-reference/functions/ctype-function.md)|任何資料型別|必須在這兩個資料型別間定義擴展或縮小轉換|擲回 <xref:System.InvalidCastException>|  
|[DirectCast Operator](../../../visual-basic/language-reference/operators/directcast-operator.md)|任何資料型別|其中一個型別必須繼承自另一個型別或實作另一個型別|擲回 <xref:System.InvalidCastException>|  
|`TryCast`|僅限參考型別 \(Reference Type\)|其中一個型別必須繼承自另一個型別或實作另一個型別|傳回 [Nothing](../../../visual-basic/language-reference/nothing.md)|  
  
## 範例  
 下列範例顯示如何使用 `TryCast`。  
  
 [!CODE [VbVbalrKeywords#6](../CodeSnippet/VS_Snippets_VBCSharp/VbVbalrKeywords#6)]  
  
## 請參閱  
 [Widening and Narrowing Conversions](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)   
 [Implicit and Explicit Conversions](../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)