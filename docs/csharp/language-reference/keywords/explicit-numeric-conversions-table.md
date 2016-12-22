---
title: "明確數值轉換表 (C# 參考) | Microsoft Docs"
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
  - "轉換 [C#], 明確數值"
  - "明確數值轉換 [C#]"
  - "數值轉換 [C#], explicit"
  - "數值資料類型 [C#]"
  - "類型轉換 [C#], 明確數值"
  - "類型 [C#], 明確數值轉換"
ms.assetid: f3bb9e76-6b92-4df7-bc36-f866c24e1dfd
caps.latest.revision: 14
caps.handback.revision: 14
author: "BillWagner"
ms.author: "wiwagn"
manager: "wpickett"
---
# 明確數值轉換表 (C# 參考)
[!INCLUDE[vs2017banner](../../../csharp/includes/vs2017banner.md)]

明確數值轉換是在沒有隱含轉換時，使用型別轉換運算式將任何數字型別轉換成其他任何的數字型別。  下表顯示這些轉換。  
  
 如需轉換的詳細資訊，請參閱 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)。  
  
|From|若要|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`byte`、`ushort`、`uint`、`ulong` 或 `char`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`Sbyte` 或 `char`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`sbyte`、 `byte`、 `ushort`、 `uint`、 `ulong` 或  `char`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`sbyte`、 `byte`、 `short` 或  `char`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`sbyte`  `byte`、 `short`、 `ushort`、 `uint`、 `ulong`、 ``  或  `char`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`sbyte`、`byte`、 `short`、 `ushort`、 `int` 或  `char`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `ulong` 或  `char`。|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `long` 或  `char`。|  
|[char](../../../csharp/language-reference/keywords/char.md)|`sbyte`、`byte` 或  `short`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `long`、 `ulong`、 `char`、 ``  或  `decimal`|  
|[double](../../../csharp/language-reference/keywords/double.md)|`sbyte`、 `byte`、 `short`、 `ushort`, `int`、 `uint`、 `long`、 `ulong`、 `char`、 `float`、 ``  或 `decimal`|  
|[decimal](../../../csharp/language-reference/keywords/decimal.md)|`sbyte`、 `byte`、 `short`、 `ushort`、 `int`、 `uint`、 `long`、 `ulong`、 `char`、 `float` 或  `double`|  
  
## 備註  
  
-   明確數值轉換可能會遺失小數位數或造成擲回例外狀況。  
  
-   當您將 `decimal` 值轉換成整數類資料型別時，這個值會捨入小數點後的數字至零，成為最接近的整數值。  如果產生的整數值是在目的型別的範圍外，就會擲回 <xref:System.OverflowException>。  
  
-   當您從 `double` 或 `float` 值轉換成整數類資料型別時，此值會被截斷。  如果產生的整數值超過目的值的範圍，就會根據溢位檢查內容來決定結果。  在已檢查內容中，則會擲出 `OverflowException`，而在未檢查內容中，則會產生目的型別未指定的值。  
  
-   當您將 `double` 轉換成 `float` 時，`double` 值會捨入為最接近的 `float` 值。  如果 `double` 值太小或太大而不適用於目的型別，結果將會為零或無限大。  
  
-   當您將 `float` 或 `double` 轉換成 `decimal` 時，來源值會轉換為 `decimal` 表示，並捨入至最接近第 28 位小數位置的數字 \(如果需要的話\)。  依據來源值，會發生下列其中一種的結果：  
  
    -   如果來源值太小，無法以 `decimal` 表示，結果就會變成零。  
  
    -   如果來源值是 NaN \(非數字\)、無限大或太大，以致無法以 `decimal` 表示時，就會擲回 `OverflowException`。  
  
-   當您將 `decimal` 轉換成 `float` 或 `double` 時，`decimal` 值會捨入為最接近的 `double` 或 `float` 值。  
  
 如需明確轉換的詳細資訊，請參閱 C\# 語言規格中的 Explicit。  如需如何存取規格的詳細資訊，請參閱 [C\# 語言規格](../../../csharp/language-reference/language-specification.md)。  
  
## 請參閱  
 [C\# 參考](../../../visual-basic/reference/command-line-compiler/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)   
 [\(\) 運算子](../../../csharp/language-reference/operators/invocation-operator.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)