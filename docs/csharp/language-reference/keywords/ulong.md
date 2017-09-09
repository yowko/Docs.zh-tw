---
title: "ulong (C# 參考) | Microsoft Docs"
ms.date: 2015-07-20
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 36de0add1d7fdf58745c65d231f3789c532ab69f
ms.lasthandoff: 03/13/2017

---
# <a name="ulong-c-reference"></a>ulong (C# 參考)
`ulong` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數類型。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`ulong`|0 到 18,446,744,073,709,551,615|不帶正負號的 64 位元整數|<xref:System.UInt64?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  
 您可以宣告並初始化 `ulong` 變數，如下列範例所示：  
  
```  
  
ulong uLong = 9223372036854775808;  
```  
  
 整數常值沒有後置詞時，其類型會是下列類型中可表示其值的第一個類型：[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、[long](../../../csharp/language-reference/keywords/long.md)、`ulong`。 在上述範例中，它是 `ulong` 類型。  
  
 您也可以使用後置詞，以根據下列規則來指定常值的類型︰  
  
-   如果您使用 L 或 l，則根據常值整數的大小，常值整數的類型為 [long](../../../csharp/language-reference/keywords/long.md) 或 `ulong`。  
  
    > [!NOTE]
    >  您可以使用小寫字母 "l" 作為後置詞。 不過，因為字母 "l" 很容易與數字 "1" 混淆，所以這會產生編譯器警告。 為了清楚起見，請使用 "L"。  
  
-   如果您使用 `U` 或 `u`，則根據常值整數的大小，常值整數的類型為 [uint](../../../csharp/language-reference/keywords/uint.md) 或 `ulong`。  
  
-   如果您使用 UL、ul、Ul、uL、LU、lu、Lu 或 lU，則常值整數的類型會是 `ulong`。  
  
     例如，下列三個陳述式的輸出會是系統類型 `UInt64`，其對應至別名 `ulong`：  
  
    ```  
    Console.WriteLine(9223372036854775808L.GetType());  
    Console.WriteLine(123UL.GetType());  
    Console.WriteLine((123UL + 456).GetType());  
    ```  
  
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
 [!INCLUDE[CSharplangspec](../../../csharp/language-reference/keywords/includes/csharplangspec_md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.UInt64>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數類型表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建類型表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)
