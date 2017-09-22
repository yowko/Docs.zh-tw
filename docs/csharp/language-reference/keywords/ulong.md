---
title: "ulong (C# 參考)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- ulong_CSharpKeyword
- ulong
dev_langs:
- CSharp
helpviewer_keywords:
- ulong keyword [C#]
ms.assetid: f2ece624-837a-40cf-92c5-343e7f33397c
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: c2da253e4da7a5d6cfa71116e4fcba7816441e92
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="ulong-c-reference"></a>ulong (C# 參考)
`ulong` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數類型。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 到 18,446,744,073,709,551,615|不帶正負號的 64 位元整數|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  

您可以針對 `ulong` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7 起)，以將其宣告和初始化。  如果整數常值超出 `ulong` 的範圍 (亦即，如果小於 <xref:System.UInt64.MinValue?displayProperty=fullName> 或大於 <xref:System.UInt64.MaxValue?displayProperty=fullName>)，就會發生編譯錯誤。 

在下列範例中，以十進位、十六進位和二進位常值表示的 7,934,076,125 整數，會指派給 `ulong` 值。  
  
[!code-cs[ulong](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ULong)]  

> [!NOTE] 
> 您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。 十進位常值沒有前置詞。 

自 C# 7 開始，您也可以使用底線字元 `_` 作為數字分隔符號，以提升可讀性，如下列範例所示。

[!code-cs[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 整數常值亦可包含後置詞以表示類型。 `UL` 或 `ul` 後置詞明確地將數值常值識別為 `ulong` 值。 如果常值超出 <xref:System.Int64.MaxValue?displayProperty=fullName>，則 `L` 後置詞表示 `ulong`。 如果常值超出 <xref:System.UInt32.MaxValue?displayProperty=fullName>，則 `U` 或 `u` 後置詞表示 `ulong`。 下列範例會使用 `ul` 後置詞來表示長整數：
 
[!code-cs[ulsuffix](../../../../samples/snippets/csharp/language-reference/keywords/numeric-suffixes.cs#2)]

如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型： 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. [long](long.md)
4. `ulong`

## <a name="compiler-overload-resolution"></a>編譯器多載解析
  
 後置詞的常見用法是搭配呼叫多載方法。 例如，請考慮使用下列使用 `ulong` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(ulong l) {}  
```  
  
 搭配使用後置詞與 `ulong` 參數時，可以保證呼叫正確的類型，例如：  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5UL);  // Calling the method with the ulong parameter  
```  
  
## <a name="conversions"></a>轉換  
 針對從 `ulong` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)，有一項預先定義的隱含轉換。  
  
 沒有從 `ulong` 轉換為任意整數類型的隱含轉換。 例如，下列陳述式會在未明確轉換的情況下產生編譯器錯誤：  
  
```  
long long1 = 8UL;   // Error: no implicit conversion from ulong  
```  
  
 有一項從 [byte](../../../csharp/language-reference/keywords/byte.md)、[ushort](../../../csharp/language-reference/keywords/ushort.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `ulong` 之預先定義的隱含轉換。  
  
 同時，沒有從浮點類型轉換為 `ulong` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```  
// Error -- no implicit conversion from double:  
ulong x = 3.0;  
// OK -- explicit conversion:  
ulong y = (ulong)3.0;    
```  
  
 如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt64>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

