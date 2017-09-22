---
title: "long (C# 參考)"
ms.date: 2017-03-14
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- long_CSharpKeyword
- long
dev_langs:
- CSharp
helpviewer_keywords:
- long keyword [C#]
ms.assetid: f9b24319-1f39-48be-a42b-d528ee28a7fd
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
ms.translationtype: HT
ms.sourcegitcommit: 306c608dc7f97594ef6f72ae0f5aaba596c936e1
ms.openlocfilehash: 5f7d2d6a3d5781b4e120b8399c7206d4429dd98e
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="long-c-reference"></a>long (C# 參考)
`long` 關鍵字表示根據下表所示的大小和範圍來儲存值的整數型別。  
  
|類型|範圍|大小|.NET Framework 類型|  
|----------|-----------|----------|-------------------------|  
|`long`|-9,223,372,036,854,775,808 到 9,223,372,036,854,775,807|帶正負號的 64 位元整數|<xref:System.Int64?displayProperty=fullName>|  
  
## <a name="literals"></a>常值  
 您可以宣告並初始化 `long` 變數，如下列範例所示：  
  
```  
  
long long1 = 4294967296;  
```  
  
 當整數常值沒有後置詞時，其型別會是下列型別中可表示其值的第一個型別：[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md)、`long`、[ulong](../../../csharp/language-reference/keywords/ulong.md)。 在上述範例中，因為它超出 [uint](../../../csharp/language-reference/keywords/uint.md) 範圍，所以是型別 `long` (請參閱[整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)，以了解整數型別的儲存體大小)。  
  
 您也可以搭配使用後置詞 L 與 `long` 型別，如下所示：  
  
```  
  
long long2 = 4294967296L;  
```  
  
 當您使用後置詞 L 時，會根據常值整數的大小，決定型別為 `long` 或 [ulong](../../../csharp/language-reference/keywords/ulong.md)。 在此案例中，其小於 [ulong](../../../csharp/language-reference/keywords/ulong.md) 範圍，因此是 `long`。  
  
 後置詞的常見用法是搭配呼叫多載方法。 例如，假設下列使用 `long` 和 [int](../../../csharp/language-reference/keywords/int.md) 參數的多載方法：  
  
```  
public static void SampleMethod(int i) {}  
public static void SampleMethod(long l) {}  
```  
  
 使用後置詞 L 時，可以保證呼叫正確的型別，例如：  
  
```  
SampleMethod(5);    // Calling the method with the int parameter  
SampleMethod(5L);   // Calling the method with the long parameter  
```  
  
 您可以在相同的運算式中搭配使用 `long` 型別和其他數值整數型別；在這種情況下，運算式會判斷值為 `long` (若是關聯運算式或布林運算式，則為 [bool](../../../csharp/language-reference/keywords/bool.md))。 例如，下列運算式會判斷值為 `long`：  
  
```  
898L + 88  
```  
  
> [!NOTE]
>  您也可以使用小寫字母 "l" 作為後置詞。 不過，這會產生編譯器警告，因為字母 "l" 很容易與數字 "1" 混淆。 為了清楚起見，請使用 "L"。  
  
 如需混合浮點型別和整數型別之算術運算式的資訊，請參閱 [float](../../../csharp/language-reference/keywords/float.md) 和 [double](../../../csharp/language-reference/keywords/double.md)。  
  
## <a name="conversions"></a>轉換  
 針對從 `long` 轉換為 [float](../../../csharp/language-reference/keywords/float.md)、[double](../../../csharp/language-reference/keywords/double.md) 或 [decimal](../../../csharp/language-reference/keywords/decimal.md)，有一項預先定義的隱含轉換。 否則，必須使用轉型。 例如，下列陳述式會在未明確轉換的情況下產生編譯器錯誤：  
  
```  
int x = 8L;        // Error: no implicit conversion from long to int  
int x = (int)8L;   // OK: explicit conversion to int  
```  
  
 針對從 [sbyte](../../../csharp/language-reference/keywords/sbyte.md)、[byte](../../../csharp/language-reference/keywords/byte.md)、[short](../../../csharp/language-reference/keywords/short.md)、 [ushort](../../../csharp/language-reference/keywords/ushort.md)、[int](../../../csharp/language-reference/keywords/int.md)、[uint](../../../csharp/language-reference/keywords/uint.md) 或 [char](../../../csharp/language-reference/keywords/char.md) 轉換為 `long`，有一項預先定義的隱含轉換。  
  
 另請注意，沒有從浮點型別轉換為 `long` 的隱含轉換。 例如，下列陳述式會在未使用明確轉換的情況下產生編譯器錯誤：  
  
```  
  
      long x = 3.0;         // Error: no implicit conversion from double  
long y = (long)3.0;   // OK: explicit conversion  
```  
  
## <a name="c-language-specification"></a>C# 語言規格  
 [!INCLUDE[CSharplangspec](~/includes/csharplangspec-md.md)]  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.Int64>   
 [C# 參考](../../../csharp/language-reference/index.md)   
 [C# 程式設計手冊](../../../csharp/programming-guide/index.md)   
 [C# 關鍵字](../../../csharp/language-reference/keywords/index.md)   
 [整數型別表](../../../csharp/language-reference/keywords/integral-types-table.md)   
 [內建型別表](../../../csharp/language-reference/keywords/built-in-types-table.md)   
 [隱含數值轉換表](../../../csharp/language-reference/keywords/implicit-numeric-conversions-table.md)   
 [明確數值轉換表](../../../csharp/language-reference/keywords/explicit-numeric-conversions-table.md)

