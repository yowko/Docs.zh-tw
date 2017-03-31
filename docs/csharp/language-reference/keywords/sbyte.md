---
title: "sbyte (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- sbyte_CSharpKeyword
- sbyte
dev_langs:
- CSharp
helpviewer_keywords:
- sbyte keyword [C#]
ms.assetid: 1a9c7b48-73d1-4d33-b485-c4faf0a816bc
caps.latest.revision: 17
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
ms.openlocfilehash: df57296bb285441aeddc596289d82d1e458dc278
ms.lasthandoff: 03/13/2017

---
# <a name="sbyte-c-reference"></a>sbyte (C# 參考)
`sbyte` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數類型。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`sbyte`|-128 到 127|帶正負號的 8 位元整數|<xref:System.SByte?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  
 您可以使用下列方式來宣告並初始化 `sbyte` 變數：  
  
```  
  
sbyte sByte1 = 127;  
```  
  
 在上述宣告中，整數常值 127 會從 [int](../../../csharp/language-reference/keywords/int.md) 隱含地轉換為 `sbyte`。 如果整數常值超出 `sbyte` 範圍，就會發生編譯錯誤。  
  
 呼叫多載的方法時，必須使用轉型。 例如，請考慮使用下列使用 `sbyte` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(sbyte b) {}  
```  
  
 使用 `sbyte` 轉型時，可以保證呼叫正確的類型，例如：  
  
```  
// Calling the method with the int parameter:  
SampleMethod(5);  
// Calling the method with the sbyte parameter:  
SampleMethod((sbyte)5);  
```  
  
## <a name="conversions"></a>轉換  
 有一項從 `sbyte` 轉換為 [short](../../../csharp/language-reference/keywords/short.md)、[int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 您不能將較大儲存大小的非常值數字類型隱含轉換為 `sbyte` (如需整數類型的儲存大小，請參閱[整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md))。 例如，請考慮使用下列兩個 `sbyte` 變數 `x` 和 `y`：  
  
```  
  
sbyte x = 10, y = 20;  
```  
  
 因為指派運算子右側的算術運算式預設會評估為 [int](../../../csharp/language-reference/keywords/int.md)，所以下列指派陳述式將會產生編譯錯誤。  
  
```  
  
sbyte z = x + y;   // Error: conversion from int to sbyte  
```  
  
 若要修正這個問題，請轉型運算式，如下列範例所示︰  
  
```  
  
sbyte z = (sbyte)(x + y);   // OK: explicit conversion  
```  
  
 不過，可以使用目的地變數具有相同或較大儲存大小的下列陳述式：  
  
```  
  
      sbyte x = 10, y = 20;  
int m = x + y;  
long n = x + y;  
```  
  
 另請注意，不會從浮點類型隱含地轉換為 `sbyte`。 例如，下列陳述式會在未使用明確轉型的情況下產生編譯器錯誤：  
  
```  
  
      sbyte x = 3.0;         // Error: no implicit conversion from double  
sbyte y = (sbyte)3.0;  // OK: explicit conversion  
```  
  
 如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.SByte>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
