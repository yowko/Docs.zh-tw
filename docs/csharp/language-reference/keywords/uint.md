---
title: "uint (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- uint
- uint_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- uint keyword [C#]
ms.assetid: e93e42c6-ec72-4b0b-89df-2fd8d36f7a7b
caps.latest.revision: 18
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
ms.openlocfilehash: fe4f7fcbbadee600e0ba6de70508312173d098ff
ms.lasthandoff: 03/13/2017

---
# <a name="uint-c-reference"></a>uint (C# 參考)
`uint` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數型別。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`uint`|0 到 4,294,967,295|不帶正負號的 32 位元整數|<xref:System.UInt32?displayProperty=fullName>|  
  
 **注意** `uint`類型不符合 CLS 規範。 請盡可能使用 `int`。  
  
## <a name="literals"></a>常值  
 您可以宣告並初始化 `uint` 類型的變數，如下列範例所示：  
  
```  
  
uint myUint = 4294967290;  
```  
  
 整數常值沒有後置詞時，其類型會是下列類型中可表示其值的第一個類型：[int](../../../csharp/language-reference/keywords/int.md)、`uint`、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)。 在此範例中，它是 `uint`：  
  
```  
  
uint uInt1 = 123;  
```  
  
 您也可以使用後置詞 u 或 U，如下所示：  
  
```  
  
uint uInt2 = 123U;  
```  
  
 當您使用後置詞 `U` 或 `u` 時，會根據常值的數值，決定常值的類型為 `uint` 或 `ulong`。 例如：  
  
```  
Console.WriteLine(44U.GetType());  
Console.WriteLine(323442434344U.GetType());  
```  
  
 這個程式碼顯示後接 `System.UInt64` 的 `System.UInt32` (分別是 `uint` 和 `ulong` 的基礎類型)，因為第二個常值太大，無法依 `uint` 類型進行排序。  
  
## <a name="conversions"></a>轉換  
 有一項從 `uint` 轉換為 [long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。 例如:   
  
```  
float myFloat = 4294967290;   // OK: implicit conversion to float  
```  
  
 有一項從 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `uint` 之預先定義的隱含轉換。 否則，您必須使用轉換。 例如，下列指派陳述式會在未進行轉換的情況下產生編譯錯誤：  
  
```  
long aLong = 22;  
// Error -- no implicit conversion from long:  
uint uInt1 = aLong;   
// OK -- explicit conversion:  
uint uInt2 = (uint)aLong;  
```  
  
 另請注意，沒有從浮點類型轉換為 `uint` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```  
// Error -- no implicit conversion from double:  
uint x = 3.0;  
// OK -- explicit conversion:  
uint y = (uint)3.0;   
```  
  
 如需混合浮點類型和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt32>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
