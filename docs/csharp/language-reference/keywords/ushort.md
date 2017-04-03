---
title: "ushort (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ushort
- ushort_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- ushort keyword [C#]
ms.assetid: 1a7dbaae-b7a0-4111-872a-c88a6d3981ac
caps.latest.revision: 16
author: BillWagner
ms.author: wiwagn
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d27a7b3b44d91b5b52e82b13fb111d865f851297
ms.lasthandoff: 03/13/2017

---
# <a name="ushort-c-reference"></a>ushort (C# 參考)
`ushort` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料類型。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`ushort`|0 到 65,535|不帶正負號的 16 位元整數|<xref:System.UInt16?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  
 您可以宣告並初始化 `ushort` 變數，如下列範例所示：  
  
```  
  
ushort myShort = 65535;  
```  
  
 在上述宣告中，整數常值 `65535` 會從 [int](../../../csharp/language-reference/keywords/int.md) 隱含地轉換為 `ushort`。 如果整數常值超出 `ushort` 範圍，就會發生編譯錯誤。  
  
 當您呼叫多載方法時，必須使用轉換。 例如，請考慮使用下列使用 `ushort` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ushort s) {}  
```  
  
 使用 `ushort` 轉換時，可以保證呼叫正確的類型，例如：  
  
```  
// Calls the method with the int parameter:  
SampleMethod(5);  
// Calls the method with the ushort parameter:  
SampleMethod((ushort)5);    
```  
  
## <a name="conversions"></a>轉換  
 有一項從 `ushort` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 有一項從 [byte](../../../csharp/language-reference/keywords/byte.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `ushort` 之預先定義的隱含轉換。 否則必須使用轉換來執行明確轉換。 例如，請考慮使用下列兩個 `ushort` 變數 `x` 和 `y`：  
  
```  
  
ushort x = 5, y = 12;  
```  
  
 因為指派運算子右邊的算術運算式預設會評估為 `int`，所以下列指派陳述式將會產生編譯錯誤。  
  
```  
  
ushort z = x + y;   // Error: conversion from int to ushort  
```  
  
 若要修正這個問題，請使用轉換：  
  
```  
  
ushort z = (ushort)(x + y);   // OK: explicit conversion   
```  
  
 不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式：  
  
```  
int m = x + y;  
long n = x + y;  
```  
  
 另請注意，沒有從浮點類型轉換為 `ushort` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```  
// Error -- no implicit conversion from double:  
ushort x = 3.0;   
// OK -- explicit conversion:  
ushort y = (ushort)3.0;  
```  
  
 如需混合浮點類型和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt16>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
