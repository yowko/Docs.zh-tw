---
title: "ushort (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "ushort"
  - "ushort_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "ushort 關鍵字 [C#]"
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 16
---
# ushort (C# 參考)
`ushort` 關鍵字表示一種儲存數值的整數資料型別，其儲存數值所根據的大小與範圍如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`ushort`|0 至 65,535|不帶正負號的 16 位元整數|<xref:System.UInt16?displayProperty=fullName>|  
  
## 常值  
 您可以用以下範例中的做法來宣告和初始化 `ushort` 變數：  
  
```  
  
ushort myShort = 65535;  
```  
  
 在上述宣告中，整數常值 `65535` 從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換為 `ushort`。  如果整數常值超過 `ushort` 的範圍，則會發生編譯錯誤。  
  
 呼叫多載方法時，必須使用轉型。  以下列使用 `ushort` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法為例：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
  
 使用 `ushort` 轉型可保證呼叫正確的型別，例如：  
  
```  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## 轉換  
 有一項從 `ushort` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 有一項從 [byte](../../../csharp/language-reference/keywords/byte.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `ushort` 之預先定義的隱含轉換。  否則執行明確轉換時必須使用轉型。  以下列兩個 `ushort` 變數 `x` 和 `y` 為例：  
  
```  
  
ushort x = 5, y = 12;  
```  
  
 下列指派陳述式會產生編譯錯誤，因為根據預設，指派運算子右邊的算術運算式會評估為 `int`。  
  
```  
  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 若要修正這個問題，請使用轉型：  
  
```  
  
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 當目的地變數有相同或較大的儲存容量時，下列陳述式仍可以使用：  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 請注意，沒有從浮點型別到 `ushort` 的隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數字轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.UInt16>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)