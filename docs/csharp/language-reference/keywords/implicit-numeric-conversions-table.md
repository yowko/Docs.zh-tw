---
title: "隱含數值轉換表 (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "轉換 [C#], 隱含數值"
  - "隱含數值轉換 [C#]"
  - "數值轉換 [C#], 隱含"
  - "類型 [C#], 隱含數值轉換"
ms.assetid: 72eb5a94-0491-48bf-8032-d7ebfdfeb8d8
caps.latest.revision: 12
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 12
---
# 隱含數值轉換表 (C# 參考)
下表顯示預先定義的隱含數值轉換。  隱含轉換可能發生在許多狀況，包括方法叫用和指派陳述式。  
  
|From|若要|  
|----------|--------|  
|[sbyte](../../../csharp/language-reference/keywords/sbyte.md)|`short`、`int`、`long`、`float`、`double` 或 `decimal`|  
|[byte](../../../csharp/language-reference/keywords/byte.md)|`short`、`ushort`、`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[short](../../../csharp/language-reference/keywords/short.md)|`int`、`long`、`float`、`double` 或 `decimal`|  
|[ushort](../../../csharp/language-reference/keywords/ushort.md)|`int`、`uint`、`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[int](../../../csharp/language-reference/keywords/int.md)|`long`、`float`、`double` 或 `decimal`|  
|[uint](../../../csharp/language-reference/keywords/uint.md)|`long`、`ulong`、`float`、`double` 或 `decimal`|  
|[long](../../../csharp/language-reference/keywords/long.md)|`float`、`double` 或 `decimal`|  
|[char](../../../csharp/language-reference/keywords/char.md)|`ushort`、`int`、 `uint`、 `long`、`ulong`、 `float`、 `double` 或 `decimal`|  
|[float](../../../csharp/language-reference/keywords/float.md)|`double`|  
|[ulong](../../../csharp/language-reference/keywords/ulong.md)|`float`、 `double` 或 `decimal`|  
  
## 備註  
  
-   從轉換中，則可能會遺失有效位數，但不是量值`int`， `uint`， `long`，或`ulong`到`float`與`long`或`ulong`到`double`。  
  
-   `char` 型別沒有隱含轉換。  
  
-   浮點型別和 `decimal` 型別之間沒有隱含轉換。  
  
-   如果常數運算式的值是在目的型別的範圍之內，則 `int` 型別的常數運算式可以轉換成 `sbyte`、`byte`、`short`、`ushort`、`uint` 或 `ulong`。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)   
 [轉型和類型轉換](../../../csharp/programming-guide/types/casting-and-type-conversions.md)