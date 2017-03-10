---
title: "byte (C# 參考) | Microsoft Docs"
ms.date: "2015-07-20"
ms.prod: ".net"
ms.technology: 
  - "devlang-csharp"
ms.topic: "article"
f1_keywords: 
  - "byte"
  - "byte_CSharpKeyword"
dev_langs: 
  - "CSharp"
helpviewer_keywords: 
  - "byte 關鍵字 [C#]"
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
caps.latest.revision: 19
author: "BillWagner"
ms.author: "wiwagn"
caps.handback.revision: 19
---
# byte (C# 參考)
`byte` 關鍵字代表一種整數型別，可儲存的值如下表所示。  
  
|型別|Range|Size|.NET Framework 型別|  
|--------|-----------|----------|-----------------------|  
|`byte`|0 至 255|不帶正負號的 8 位元整數|<xref:System.Byte?displayProperty=fullName>|  
  
## 常值  
 您可以採用以下範例中同時宣告和初始化 `byte` 型別變數的做法：  
  
```  
byte myByte = 255;  
```  
  
 在上述宣告裡，整數常值 `255` 隱含地從 [int](../../../csharp/language-reference/keywords/int.md) 轉換成 `byte`。  如果整數常值超過 `byte` 的範圍，則會發生編譯錯誤。  
  
## 轉換  
 這是從 `byte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 需要較大儲存空間的非常值數字型別不能隱含轉換成 `byte`。  如需整數類資料型別儲存空間的詳細資訊，請參閱[整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)。  以下列兩個 `byte` 變數 `x` 和 `y` 為例：  
  
```  
  
byte x = 10, y = 20;  
```  
  
 下列指派陳述式 \(Assignment Statement\) 會產生編譯錯誤，因為根據預設，指派運算子右邊的算術運算式會評估為 `int`。  
  
```  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 若要修正這個問題，請使用轉型：  
  
```  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 當目的變數有相同或較大的儲存空間時，下列陳述式仍可以使用：  
  
```  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 此外也沒有從浮點型別到 `byte` 的隱含轉換。  例如，下列陳述式必須使用明確轉換，否則會產生編譯器錯誤：  
  
```  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 呼叫多載方法時，必須使用型別轉換。  以下列使用 `byte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法為例：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 使用 `byte` 轉型可以保證呼叫到正確的型別，例如：  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 如需混合浮點型別和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數字轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## C\# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec-md.md)]  
  
## 請參閱  
 <xref:System.Byte>   
 [C\# 參考](../../../csharp/language-reference/index.md)   
 [C\# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C\# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類資料類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型資料表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)