---
title: "sbyte (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "sbyte_CSharpKeyword"
  - "sbyte"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "sbyte 關鍵字 [C#]"
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 17
---
# sbyte (C# 參考)
`sbyte` 關鍵字表示一種儲存數值的整數型別，其儲存數值所根據的大小與範圍如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`sbyte`|\-128 至 127|帶正負號的 8 位元整數|<xref:System.SByte?displayProperty=fullName>|  
  
## 常值  
 您可以用這種方式宣告和初始化 `sbyte` 變數：  
  
```  
  
sbyte sByte1 = 127;  
```  
  
 在上述宣告中，整數常值 127 是從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換為 `sbyte`。  如果整數常值超過 `sbyte` 容許的範圍，則會發生編譯錯誤。  
  
 呼叫多載方法時必須使用轉換。  以下列使用 `sbyte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法為例：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 使用 `sbyte` 轉換可保證呼叫正確的型別，例如：  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## 轉換  
 有一項從 `sbyte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 您不能將儲存容量較大的非常值數字型別隱含轉換成 `sbyte` \(如需整數類資料型別儲存大小的詳細資訊，請參閱[整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)\)。  以下列兩個 `sbyte` 變數 `x` 和 `y` 為例：  
  
```  
  
sbyte x = 10, y = 20;  
```  
  
 下列指派陳述式會產生編譯錯誤，因為根據預設，指派運算子右邊的算術運算式會評估為 [int](../../../csharp/language-reference/keywords/int.md)。  
  
```  
  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 若要修正這個問題，請依照下列範例所示轉換運算式：  
  
```  
  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 當目的地變數有相同或較大的儲存容量時，下列陳述式仍可以使用：  
  
```  
  
        sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 請注意，沒有從浮點型別到 `sbyte` 的隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
  
        sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數字轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.SByte>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)