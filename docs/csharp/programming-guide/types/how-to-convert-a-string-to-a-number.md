---
title: HOW TO：將字串轉換為數值 - C# 程式設計指南
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: a75d6dd5fdb74ca3cb6fe28db7415aeb478e2237
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/11/2018
ms.locfileid: "53243214"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a>HOW TO：將字串轉換為數值 (C# 程式設計指南)
您可以使用 <xref:System.Convert> 類別中的方法，或是使用各種數值類型 (int、long、float 等等) 上找到的 `TryParse` 方法，將[字串](../../../csharp/language-reference/keywords/string.md)轉換為數字。  
  
 如果您有一個字串，呼叫 `TryParse` 方法 (例如，[`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) 相較之下將更有效率且直接。  使用 <xref:System.Convert> 方法比實作 <xref:System.IConvertible> 的一般物件更有用。  
  
 您可以在預期字串包含的數值類型上使用 `Parse` 或 `TryParse` 方法，例如 <xref:System.Int32?displayProperty=nameWithType> 類型。  <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> 方法會在內部使用 <xref:System.Int32.Parse%2A>。  如果字串的格式無效，`Parse` 會擲回例外狀況，而 `TryParse` 會傳回 [false](../../../csharp/language-reference/keywords/false.md)。  
  
## <a name="example"></a>範例  
 `Parse` 和 `TryParse` 方法會忽略字串開頭和結尾的空格，但所有其他字元必須是來自適當數值類型的字元 (int、long、ulong、float、decimal 等等)。  若構成數字的字元內有任何空格，則會造成錯誤。  例如，您可以使用 `decimal.TryParse` 剖析 "10"、"10.3"、"  10  "，但無法使用這個方法來剖析來自 “10X”、“1 0” (請注意空格)、"10 .3" (請注意空格)、"10e1" (`float.TryParse` 在這裡運作) 的 10，依此類推。  
  
 下列範例會示範 `Parse` 和 `TryParse` 成功與不成功的呼叫。  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a>範例  
 下表列出您可以使用的 <xref:System.Convert> 類別的一些方法。  
  
|數字類型|方法|  
|------------------|------------|  
|`decimal`|<xref:System.Convert.ToDecimal%28System.String%29>|  
|`float`|<xref:System.Convert.ToSingle%28System.String%29>|  
|`double`|<xref:System.Convert.ToDouble%28System.String%29>|  
|`short`|<xref:System.Convert.ToInt16%28System.String%29>|  
|`int`|<xref:System.Convert.ToInt32%28System.String%29>|  
|`long`|<xref:System.Convert.ToInt64%28System.String%29>|  
|`ushort`|<xref:System.Convert.ToUInt16%28System.String%29>|  
|`uint`|<xref:System.Convert.ToUInt32%28System.String%29>|  
|`ulong`|<xref:System.Convert.ToUInt64%28System.String%29>|  
  
 這個範例會呼叫 <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> 方法，將輸入[字串](../../../csharp/language-reference/keywords/string.md)轉換為 [int](../../../csharp/language-reference/keywords/int.md)。 程式碼會攔截由這個方法擲回之兩種最常見的例外狀況，分別是 <xref:System.FormatException> 和 <xref:System.OverflowException>。 如果數字可以遞增而不會造成整數儲存位置溢位，那麼程式會將結果增加 1 並列印輸出。  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a>請參閱

- [型別](../../../csharp/programming-guide/types/index.md)  
- [如何：判斷字串是否代表數值](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [.NET Framework 4 格式化公用程式](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
