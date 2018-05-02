---
title: ushort (C# 參考)
ms.date: 03/14/2017
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: ee624433975df79ed5709bf40d146160c5e633b0
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/26/2018
---
# <a name="ushort-c-reference"></a>ushort (C# 參考)

`ushort` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料類型。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 到 65,535|不帶正負號的 16 位元整數|<xref:System.UInt16?displayProperty=nameWithType>|  
  
## <a name="literals"></a>常值  

您可以針對 `ushort` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。 如果整數常值超出 `ushort` 的範圍 (亦即，如果小於 <xref:System.UInt16.MinValue?displayProperty=nameWithType> 或大於 <xref:System.UInt16.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 65,034 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `ushort` 值。    
  
[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShort)]  

> [!NOTE] 
> 您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。 十進位常值沒有前置詞。

從 C# 7.0 開始，已新增一組功能來提升可讀性。 
 - C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。
 - C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。 十進位常值不允許有前置底線。

一些範例如下所示。

[!code-csharp[UShort](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#UShortS)]  
 
## <a name="compiler-overload-resolution"></a>編譯器多載解析
  
 當您呼叫多載方法時，必須使用轉換。 例如，請考慮使用下列使用 `ushort` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
 
 使用 `ushort` 轉型時，可以保證呼叫正確的類型，例如：  
  
```csharp  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>轉換  
 有一項從 `ushort` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 有一項從 [byte](../../../csharp/language-reference/keywords/byte.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `ushort` 之預先定義的隱含轉換。 否則必須使用轉換來執行明確轉換。 例如，請考慮使用下列兩個 `ushort` 變數 `x` 和 `y`：  
  
```csharp 
ushort x = 5, y = 12;  
```  
  
 因為指派運算子右邊的算術運算式預設會評估為 `int`，所以下列指派陳述式將會產生編譯錯誤。  
  
```csharp  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 若要修正這個問題，請使用轉換：  
  
```csharp 
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式：  
  
```csharp
int m = x + y;  
long n = x + y;  
```  
  
 另請注意，不會從浮點類型隱含地轉換為 `ushort`。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```csharp  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.UInt16>  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
