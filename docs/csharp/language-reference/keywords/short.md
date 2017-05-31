---
title: "short (C# 參考) | Microsoft Docs"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- short
- short_CSharpKeyword
dev_langs:
- CSharp
helpviewer_keywords:
- short keyword [C#]
ms.assetid: 04c10688-e51a-4a87-bfec-83f7fb42ff11
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
ms.translationtype: Human Translation
ms.sourcegitcommit: 400dfda51d978f35c3995f90840643aaff1b9c13
ms.openlocfilehash: 14f9c66bb620e2ad35513abeeba77372904cc1f3
ms.contentlocale: zh-tw
ms.lasthandoff: 03/24/2017

---
# <a name="short-c-reference"></a>short (C# 參考)

`short` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數資料型別。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`short`|-32,768 到 32,767|帶正負號的 16 位元整數|<xref:System.Int16?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  

您可以將十進位常值、十六進位常值，或二進位常值 (自 C# 7 起) 指派給 `short` 變數，以將其宣告和初始化。  如果整數常值超出 `short` 範圍 (也就是說，如果它小於 <xref:System.Int16.MinValue?displayProperty=fullName> 或大於 <xref:System.Int16.MaxValue?displayProperty=fullName>)，就會發生編譯錯誤。 

在下列範例中，以十進位、十六進位和二進位常值表示的 1,034 整數，從 [int](../../../csharp/language-reference/keywords/int.md) 隱含轉換成 `short` 值。  
  
[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#Short)]  

> [!NOTE] 
> 您可以使用 `0x` 或 `0X` 前置詞來表示十六進位常值，以 `0b` 或 `0B` 前置詞來表示二進位常值。 十進位常值沒有前置詞。

自 C# 7 開始，您也可以使用底線字元 `_` 作為數字分隔符號，以提升可讀性，如下列範例所示。

[!code-cs[Short](../../../../samples/snippets/csharp/language-reference/keywords/numeric-literals.cs#ShortS)]  
 
## <a name="compiler-overload-resolution"></a>編譯器多載解析

 呼叫多載的方法時，必須使用轉型。 例如，請考慮使用下列使用 `short` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```csharp  
public static void SampleMethod(int i) {}  
public static void SampleMethod(short s) {}  
```  
  
 使用 `short` 轉型時，可以保證呼叫正確的類型，例如：  
  
```csharp  
SampleMethod(5);         // Calling the method with the int parameter  
SampleMethod((short)5);  // Calling the method with the short parameter  
```  
  
## <a name="conversions"></a>轉換  

 有一項從 `short` 轉換為 [int](../../../csharp/language-reference/keywords/int.md)、[long](../../../csharp/language-reference/keywords/long.md)、[float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md) 之預先定義的隱含轉換。  
  
 您不能將較大儲存大小的非常值數字類型隱含轉換為 `short` (如需整數類型的儲存大小，請參閱[整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md))。 例如，請考慮使用下列兩個 `short` 變數 `x` 和 `y`：  
  
```csharp  
short x = 5, y = 12;  
```  
  
 因為指派運算子右側的算術運算式預設會評估為 [int](../../../csharp/language-reference/keywords/int.md)，所以下列指派陳述式會產生編譯錯誤。  
  
```csharp
short z  = x + y;        // Compiler error CS0266: no conversion from int to short
```

 若要修正這個問題，請使用轉型：  
  
```csharp
short z  = (short)(x + y);   // Explicit conversion
```
  
 不過，也可以使用目的地變數具有相同或較大儲存大小的下列陳述式：  
  
```csharp  
int m = x + y;  
long n = x + y;  
```  
  
 不會從浮點類型隱含地轉換為 `short`。 例如，下列陳述式會在未使用明確轉型的情況下產生編譯器錯誤：  
  
```csharp  
short x = 3.0;          // Error: no implicit conversion from double  
short y = (short)3.0;   // OK: explicit conversion  
```  
  
 如需混合浮點類型和整數類型之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
 如需隱含數值轉換規則的詳細資訊，請參閱[隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)。  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Int16>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
