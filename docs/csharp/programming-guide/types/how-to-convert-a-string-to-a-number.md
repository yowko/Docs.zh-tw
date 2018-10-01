---
title: 如何：將字串轉換為數值 (C# 程式設計手冊)
ms.date: 07/20/2015
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 1f11ba3981b219d3b3a7817afd75fa78f2ccf78a
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2018
ms.locfileid: "43521749"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="8d5f4-102">如何：將字串轉換為數值 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="8d5f4-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="8d5f4-103">您可以使用 <xref:System.Convert> 類別中的方法，或是使用各種數值類型 (int、long、float 等等) 上找到的 `TryParse` 方法，將[字串](../../../csharp/language-reference/keywords/string.md)轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="8d5f4-104">如果您有一個字串，呼叫 `TryParse` 方法 (例如，[`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) 相較之下將更有效率且直接。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)).</span></span>  <span data-ttu-id="8d5f4-105">使用 <xref:System.Convert> 方法比實作 <xref:System.IConvertible> 的一般物件更有用。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-105">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="8d5f4-106">您可以在預期字串包含的數值類型上使用 `Parse` 或 `TryParse` 方法，例如 <xref:System.Int32?displayProperty=nameWithType> 類型。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="8d5f4-107"><xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> 方法會在內部使用 <xref:System.Int32.Parse%2A>。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="8d5f4-108">如果字串的格式無效，`Parse` 會擲回例外狀況，而 `TryParse` 會傳回 [false](../../../csharp/language-reference/keywords/false.md)。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="8d5f4-109">範例</span><span class="sxs-lookup"><span data-stu-id="8d5f4-109">Example</span></span>  
 <span data-ttu-id="8d5f4-110">`Parse` 和 `TryParse` 方法會忽略字串開頭和結尾的空格，但所有其他字元必須是來自適當數值類型的字元 (int、long、ulong、float、decimal 等等)。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-110">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="8d5f4-111">若構成數字的字元內有任何空格，則會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-111">Any white space within the characters that form the number cause an error.</span></span>  <span data-ttu-id="8d5f4-112">例如，您可以使用 `decimal.TryParse` 剖析 "10"、"10.3"、"  10  "，但無法使用這個方法來剖析來自 “10X”、“1 0” (請注意空格)、"10 .3" (請注意空格)、"10e1" (`float.TryParse` 在這裡運作) 的 10，依此類推。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="8d5f4-113">下列範例會示範 `Parse` 和 `TryParse` 成功與不成功的呼叫。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]  
[!code-csharp[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]  
[!code-csharp[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]  
[!code-csharp[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]  
[!code-csharp[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]  
  
## <a name="example"></a><span data-ttu-id="8d5f4-114">範例</span><span class="sxs-lookup"><span data-stu-id="8d5f4-114">Example</span></span>  
 <span data-ttu-id="8d5f4-115">下表列出您可以使用的 <xref:System.Convert> 類別的一些方法。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-115">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="8d5f4-116">數字類型</span><span class="sxs-lookup"><span data-stu-id="8d5f4-116">Numeric Type</span></span>|<span data-ttu-id="8d5f4-117">方法</span><span class="sxs-lookup"><span data-stu-id="8d5f4-117">Method</span></span>|  
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
  
 <span data-ttu-id="8d5f4-118">這個範例會呼叫 <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> 方法，將輸入[字串](../../../csharp/language-reference/keywords/string.md)轉換為 [int](../../../csharp/language-reference/keywords/int.md)。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-118">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="8d5f4-119">程式碼會攔截由這個方法擲回之兩種最常見的例外狀況，分別是 <xref:System.FormatException> 和 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-119">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="8d5f4-120">如果數字可以遞增而不會造成整數儲存位置溢位，那麼程式會將結果增加 1 並列印輸出。</span><span class="sxs-lookup"><span data-stu-id="8d5f4-120">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 [!code-csharp[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]  
[!code-csharp[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="8d5f4-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="8d5f4-121">See Also</span></span>

- [<span data-ttu-id="8d5f4-122">型別</span><span class="sxs-lookup"><span data-stu-id="8d5f4-122">Types</span></span>](../../../csharp/programming-guide/types/index.md)  
- [<span data-ttu-id="8d5f4-123">如何：判斷字串是否表示數值</span><span class="sxs-lookup"><span data-stu-id="8d5f4-123">How to: Determine Whether a String Represents a Numeric Value</span></span>](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)  
- [<span data-ttu-id="8d5f4-124">.NET Framework 4 格式化公用程式</span><span class="sxs-lookup"><span data-stu-id="8d5f4-124">.NET Framework 4 Formatting Utility</span></span>](https://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)
