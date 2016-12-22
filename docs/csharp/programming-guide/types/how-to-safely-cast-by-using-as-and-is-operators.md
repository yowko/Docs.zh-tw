---
title: "如何：使用 as 和 is 運算子進行安全轉型 (C# 程式設計手冊) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "as 運算子 [C#]"
  - "轉型運算子 [C#], as 和 is 運算子"
  - "is 運算子 [C#]"
ms.assetid: c1176cea-1426-4a44-8570-3eadafa58863
caps.latest.revision: 10
caps.handback.revision: 10
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 如何：使用 as 和 is 運算子進行安全轉型 (C# 程式設計手冊)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

由於物件都是多型的，因此可以使用某個基底類別 \(Base Class\) 型別的變數來存放衍生型別 \(Derived Type\)。  若要存取衍生型別的方法，您必須將值轉型回衍生型別。  不過，在這種情況下嘗試進行簡單轉型卻會有擲回 <xref:System.InvalidCastException> 的風險。  這就是 C\# 提供 [is](../../../csharp/language-reference/keywords/is.md) 和 [as](../../../csharp/language-reference/keywords/as.md) 運算子的原因。  您可以使用這兩個運算子測試轉型能否成功，而不會擲回例外狀況 \(Exception\)。  `as` 運算子通常比較有效率，因為如果轉型能夠成功，它實際會傳回轉型值。  `is` 運算子卻只會傳回布林值，  因此它可以用在只是要確定物件的型別而不必實際轉型的情況。  
  
## 範例  
 在下列範例中，會示範如何使用 `is` 和 `as` 運算子，在無擲回例外狀況風險的情況下，從某一個參考型別 \(Reference Type\) 轉型成另一個型別。  此外，還會示範如何使用 `as` 運算子搭配可為 null 的實值型別 \(Nullable Type\)。  
  
 [!CODE [csProgGuideTypes#40](../CodeSnippet/VS_Snippets_VBCSharp/CsProgGuideTypes#40)]  
  
## 請參閱  
 [類型](../../../csharp/programming-guide/types/index.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [可為 Null 的類型](../../../visual-basic/reference/command-line-compiler/index.md)