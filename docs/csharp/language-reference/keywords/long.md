---
title: long - C# 參考
ms.custom: seodec18
ms.date: 03/14/2017
f1_keywords:
- long_CSharpKeyword
- long
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
ms.openlocfilehash: 3085fd9c5f0c379d4a2ef22f4adb0ec157f0b785
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54585506"
---
# <a name="long-c-reference"></a>long (C# 參考)

`long` 表示儲存值的整數型別 (以下表所示的大小和範圍為依據)。  
  
|類型|範圍|大小|.NET 型別|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|帶正負號的 64 位元整數|<xref:System.Int64?displayProperty=nameWithType>|  
  
## <a name="literals"></a>常值 

您可以針對 `long` 變數指派十進位常值、十六進位常值，或二進位常值 (自 C# 7.0 起)，以將其宣告和初始化。 

在下列範例中，如果整數等於 4,294,967,296，即表示 `long` 值指派了十進位、十六進位和二進位常值。  
  
[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Long)]  

> [!NOTE] 
> 您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。 十進位常值沒有前置詞。 

從 C# 7.0 開始，已新增一組功能來提升可讀性。 
 - C# 7.0 允許使用底線字元 (`_`) 作為數字分隔符號。
 - C# 7.2 允許針對二進位或十六進位常值，在前置詞之後使用 `_` 作為數字分隔符號。 十進位常值不允許有前置底線。

一些範例如下所示。

[!code-csharp[long](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#LongS)]  
 
 整數常值亦可包含後置詞以表示類型。 `L` 後置詞表示 `long`。 下列範例會使用 `L` 後置詞來表示長整數：
 
```csharp
long value = 4294967296L;  
```  

> [!NOTE]
>  您也可以使用小寫字母 "l" 作為後置詞。 不過，這會產生編譯器警告，因為字母 "l" 很容易與數字 "1" 混淆。 為了清楚起見，請使用 "L"。  
  
 當您使用 `L` 後置詞時，系統會根據常值整數的大小，判斷其類型為 `long` 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。 在此案例中，其小於 [ulong](../../../csharp/language-reference/keywords/ulong.md) 範圍，因此是 `long`。  
  
 後置詞的常見用法是用來呼叫多載方法。 例如，下列多載方法具有 `long` 和 [int](../../../csharp/language-reference/keywords/int.md) 類型的參數：  
  
```csharp
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 `L` 後置詞可確保呼叫正確的多載：  
  
```csharp  
SampleMethod(5);    // Calls the method with the int parameter  
SampleMethod(5L);   // Calls the method with the long parameter  
```  
如果整數常值沒有後置詞，其類型會是下列類型中可表示其值的第一個類型： 

1. [int](int.md)
2. [uint](../../../csharp/language-reference/keywords/uint.md)
3. `long`
4. [ulong](../../../csharp/language-reference/keywords/ulong.md) 

由於上述範例的 4294967296 常值已超出 [uint](../../../csharp/language-reference/keywords/uint.md) 範圍，因此屬於 `long` 類型 (請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)，以了解整數型別的儲存大小)。  
  
 如果您在相同的運算式中搭配使用 `long` 類型和其他整數型別，則運算式會判斷值為 `long` (若是關聯運算式或布林運算式，則為 [bool](../../../csharp/language-reference/keywords/bool.md))。 例如，下列運算式會判斷值為 `long`：  
  
```csharp  
898L + 88  
```  
  
 如需混合浮點類型和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
## <a name="conversions"></a>轉換  
 針對從 `long` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)，有一項預先定義的隱含轉換。 否則，必須使用轉型。 例如，下列陳述式會在未明確轉換的情況下產生編譯器錯誤：  
  
```csharp  
int x = 8L;        // Error: no implicit conversion from long to int  
int y = (int)8L;   // OK: explicit conversion to int  
```  
  
 針對從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `long`，有一項預先定義的隱含轉換。  
  
 另請注意，沒有從浮點型別轉換為 `long` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```csharp  
long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>C# 語言規格  

如需詳細資訊，請參閱 [C# 語言規格](../language-specification/index.md)的[整數型別](~/_csharplang/spec/types.md#integral-types)。 語言規格是 C# 語法及用法的限定來源。
  
## <a name="see-also"></a>另請參閱

- <xref:System.Int64>
- [C# 參考](../../../csharp/language-reference/index.md)
- [C# 程式設計指南](../../../csharp/programming-guide/index.md)
- [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)
- [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)
- [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)
- [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)
- [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
