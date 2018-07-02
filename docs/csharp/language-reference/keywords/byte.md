---
title: byte (C# 參考)
ms.date: 03/14/2017
f1_keywords:
- byte
- byte_CSharpKeyword
helpviewer_keywords:
- byte keyword [C#]
ms.assetid: 111f1db9-ca32-4f0e-b497-4783517eda47
ms.openlocfilehash: 28acbe67b85637550fdb1f5e290a9abb60bf5c65
ms.sourcegitcommit: f9e38d31288fe5962e6be5b0cc286da633482873
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/27/2018
ms.locfileid: "37027885"
---
# <a name="byte-c-reference"></a>byte (C# 參考)

`byte` 表示用來儲存下表所指出值的整數型別。  
  
|類型|範圍|大小|.NET 型別|  
|----------|-----------|----------|-------------------------|  
|`byte`|0 到 255|不帶正負號的 8 位元整數|<xref:System.Byte?displayProperty=nameWithType>|  
  
## <a name="literals"></a>常值  

 您可以針對 `byte` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。 如果整數常值超出 `byte` 的範圍 (亦即，如果小於 <xref:System.Byte.MinValue?displayProperty=nameWithType> 或大於 <xref:System.Byte.MaxValue?displayProperty=nameWithType>)，就會發生編譯錯誤。

在下列範例中，以十進位、十六進位和二進位常值表示的 201 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `byte` 值。    
  
[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Byte)]  

> [!NOTE] 
> 您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。 十進位常值沒有前置詞。

從 C# 7.0 開始，已新增一組功能來提升可讀性。 
 - C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。
 - C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。 十進位常值不允許有前置底線。

一些範例如下所示。

[!code-csharp[Byte](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ByteS)]  
 
## <a name="conversions"></a>轉換  
 有一項從 `byte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 您無法將較大儲存大小的非常值數字類型隱含轉換為 `byte`。 如需整數型別儲存大小的詳細資訊，請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)。 例如，請考慮使用下列兩個 `byte` 變數 `x` 和 `y`：  
  
```csharp  
byte x = 10, y = 20;  
```  
  
 因為指派運算子右側的算術運算式預設會評估為 `int`，所以下列指派陳述式將會產生編譯錯誤。  
  
```csharp  
// Error: conversion from int to byte:  
byte z = x + y;  
```  
  
 若要修正這個問題，請使用轉換：  
  
```csharp  
// OK: explicit conversion:  
byte z = (byte)(x + y);  
```  
  
 不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式︰  
  
```csharp  
int x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 同時，沒有從浮點類型轉換為 `byte` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```csharp  
// Error: no implicit conversion from double:  
byte x = 3.0;   
// OK: explicit conversion:  
byte y = (byte)3.0;  
```  
  
 呼叫多載的方法時，必須使用轉型。 例如，請考慮使用下列使用 `byte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(byte b) {}  
```  
  
 使用 `byte` 轉型時，可以保證呼叫正確的類型，例如：  
  
```csharp  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the byte parameter:  
SampleMethod((byte)5);  
```  
  
 如需混合浮點類型和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Byte>  
 [C# 參考](../../../csharp/language-reference/index.md)  
 [C# 程式設計指南](../../../csharp/programming-guide/index.md)  
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)  
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)  
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)  
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)  
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
