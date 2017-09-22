---
title: "int (C# 參考)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- int_CSharpKeyword
- int
dev_langs:
- CSharp
helpviewer_keywords:
- int keyword [C#]
ms.assetid: 212447b4-5d2a-41aa-88ab-84fe710bdb52
caps.latest.revision: 19
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
ms.translationtype: HT
ms.sourcegitcommit: 935428cc9442a3e1d15eeb8942176c237bff4e22
ms.openlocfilehash: 6e87893bcd9800b61297e71b782028fec5116479
ms.contentlocale: zh-tw
ms.lasthandoff: 08/22/2017

---
# <a name="int-c-reference"></a>int (C# 參考)
`int` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數型別。  
  
|類型|範圍|大小|.NET Framework 類型|預設值|  
|----------|-----------|----------|-------------------------|-------------------|  
|`int`|-2,147,483,648 至 2,147,483,647|帶正負號的 32 位元整數|<xref:System.Int32?displayProperty=fullName>|0|  
  
## <a name="literals"></a>常值  
 
您可以針對 `int` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。  如果整數常值超出 `int` 的範圍 (亦即，如果小於 <xref:System.Int32.MinValue?displayProperty=fullName> 或大於 <xref:System.Int32.MaxValue?displayProperty=fullName>)，就會發生編譯錯誤。 

在下列範例中，以十進位、十六進位和二進位常值表示的 90,946 整數，會指派給 `int` 值。  
  
```  
  
int i = 123;  
```  
  
 當整數常值沒有後置字元時，其類型會是下列類型中可表示其值的第一個類型：`int`、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、[ulong](../../../csharp/language-reference/keywords/ulong.md)。 在此範例中，它是 `int` 類型。  
  
## <a name="conversions"></a>轉換  
 有一項從 `int` 轉換為 [long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。 例如:   
  
```  
// '123' is an int, so an implicit conversion takes place here:  
float f = 123;  
```  
  
 有一項從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `int` 之預先定義的隱含轉換。 例如，下列指派陳述式會在並未進行轉換的情況下產生編譯錯誤：  
  
```  
long aLong = 22;  
int i1 = aLong;       // Error: no implicit conversion from long.  
int i2 = (int)aLong;  // OK: explicit conversion.  
```  
  
 另請注意，沒有從浮點類型轉換為 `int` 的隱含轉換。 例如，除非使用明確轉換，否則下列陳述式會產生編譯器錯誤：  
  
```  
  
      int x = 3.0;         // Error: no implicit conversion from double.  
int y = (int)3.0;    // OK: explicit conversion.  
```  
  
 如需混合浮點類型和整數型別之算術運算式的詳細資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Int32>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

