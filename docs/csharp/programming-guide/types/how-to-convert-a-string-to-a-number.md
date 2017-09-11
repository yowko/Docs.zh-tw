---
title: "如何：將字串轉換為數值 (C# 程式設計手冊)"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
dev_langs:
- CSharp
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
caps.latest.revision: 34
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
ms.openlocfilehash: 08d13e40a385ce8e9011b508b04361b2e050f904
ms.contentlocale: zh-tw
ms.lasthandoff: 07/28/2017

---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="6c094-102">如何：將字串轉換為數值 (C# 程式設計手冊)</span><span class="sxs-lookup"><span data-stu-id="6c094-102">How to: Convert a String to a Number (C# Programming Guide)</span></span>
<span data-ttu-id="6c094-103">您可以使用 <xref:System.Convert> 類別中的方法，或是使用各種數值類型 (int、long、float 等等) 上找到的 `TryParse` 方法，將[字串](../../../csharp/language-reference/keywords/string.md)轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="6c094-103">You can convert a [string](../../../csharp/language-reference/keywords/string.md) to a number by using methods in the <xref:System.Convert> class or by using the `TryParse` method found on the various numeric types (int, long, float, etc.).</span></span>  
  
 <span data-ttu-id="6c094-104">如果您有一個字串，則呼叫 `TryParse` 方法會稍微更有效率且直接 (例如，`int.TryParse("11")`)。</span><span class="sxs-lookup"><span data-stu-id="6c094-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, `int.TryParse("11")`).</span></span>  <span data-ttu-id="6c094-105">使用 `Convert` 方法比實作 <xref:System.IConvertible> 的一般物件更有用。</span><span class="sxs-lookup"><span data-stu-id="6c094-105">Using a `Convert` method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="6c094-106">您可以在預期字串包含的數值類型上使用 `Parse` 或 `TryParse` 方法，例如 <xref:System.Int32?displayProperty=fullName> 類型。</span><span class="sxs-lookup"><span data-stu-id="6c094-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=fullName> type.</span></span>  <span data-ttu-id="6c094-107"><xref:System.Convert.ToUInt32%2A?displayProperty=fullName> 方法會在內部使用 <xref:System.Int32.Parse%2A>。</span><span class="sxs-lookup"><span data-stu-id="6c094-107">The <xref:System.Convert.ToUInt32%2A?displayProperty=fullName> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="6c094-108">如果字串的格式無效，`Parse` 會擲回例外狀況，而 `TryParse` 會傳回 [false](../../../csharp/language-reference/keywords/false.md)。</span><span class="sxs-lookup"><span data-stu-id="6c094-108">If the string is not in a valid format, `Parse` throws an exception whereas `TryParse` returns [false](../../../csharp/language-reference/keywords/false.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c094-109">範例</span><span class="sxs-lookup"><span data-stu-id="6c094-109">Example</span></span>  
 <span data-ttu-id="6c094-110">`Parse` 和 `TryParse` 方法會忽略字串開頭和結尾的空格，但所有其他字元必須是來自適當數值類型的字元 (int、long、ulong、float、decimal 等等)。</span><span class="sxs-lookup"><span data-stu-id="6c094-110">The `Parse` and `TryParse` methods ignore whitespace at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (int, long, ulong, float, decimal, etc.).</span></span>  <span data-ttu-id="6c094-111">若構成數字的字元內有任何空格，則會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="6c094-111">Any whitespace within the characters that form the number cause an error.</span></span>  <span data-ttu-id="6c094-112">例如，您可以使用 `decimal.TryParse` 剖析 "10"、"10.3"、"  10  "，但無法使用這個方法來剖析來自 “10X”、“1 0” (請注意空格)、"10 .3" (請注意空格)、"10e1" (`float.TryParse` 在這裡運作) 的 10，依此類推。</span><span class="sxs-lookup"><span data-stu-id="6c094-112">For example, you can use `decimal.TryParse` to parse "10", "10.3", "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note space), "10 .3" (note space), "10e1" (`float.TryParse` works here), and so on.</span></span>  
  
 <span data-ttu-id="6c094-113">下列範例會示範 `Parse` 和 `TryParse` 成功與不成功的呼叫。</span><span class="sxs-lookup"><span data-stu-id="6c094-113">The examples below demonstrate both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
 <span data-ttu-id="6c094-114">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-114">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span></span>  
<span data-ttu-id="6c094-115">[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-115">[!code-cs[csProgGuideTypes#25](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_2.cs)]</span></span>  
<span data-ttu-id="6c094-116">[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-116">[!code-cs[csProgGuideTypes#26](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_3.cs)]</span></span>  
<span data-ttu-id="6c094-117">[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-117">[!code-cs[csProgGuideTypes#27](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_4.cs)]</span></span>  
<span data-ttu-id="6c094-118">[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-118">[!code-cs[csProgGuideTypes#28](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_5.cs)]</span></span>  
<span data-ttu-id="6c094-119">[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-119">[!code-cs[csProgGuideTypes#100](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_6.cs)]</span></span>  
  
## <a name="example"></a><span data-ttu-id="6c094-120">範例</span><span class="sxs-lookup"><span data-stu-id="6c094-120">Example</span></span>  
 <span data-ttu-id="6c094-121">下表列出您可以使用的 <xref:System.Convert> 類別的一些方法。</span><span class="sxs-lookup"><span data-stu-id="6c094-121">The following table lists some of the methods from the <xref:System.Convert> class that you can use.</span></span>  
  
|<span data-ttu-id="6c094-122">數字類型</span><span class="sxs-lookup"><span data-stu-id="6c094-122">Numeric Type</span></span>|<span data-ttu-id="6c094-123">方法</span><span class="sxs-lookup"><span data-stu-id="6c094-123">Method</span></span>|  
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
  
 <span data-ttu-id="6c094-124">這個範例會呼叫 <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> 方法，將輸入[字串](../../../csharp/language-reference/keywords/string.md)轉換為 [int](../../../csharp/language-reference/keywords/int.md)。</span><span class="sxs-lookup"><span data-stu-id="6c094-124">This example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=fullName> method to convert an input [string](../../../csharp/language-reference/keywords/string.md) to an [int](../../../csharp/language-reference/keywords/int.md) .</span></span> <span data-ttu-id="6c094-125">程式碼會攔截由這個方法擲回之兩種最常見的例外狀況，分別是 <xref:System.FormatException> 和 <xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="6c094-125">The code catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="6c094-126">如果數字可以遞增而不會造成整數儲存位置溢位，那麼程式會將結果增加 1 並列印輸出。</span><span class="sxs-lookup"><span data-stu-id="6c094-126">If the number can be incremented without overflowing the integer storage location, the program adds 1 to the result and prints the output.</span></span>  
  
 <span data-ttu-id="6c094-127">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-127">[!code-cs[csProgGuideTypes#5555](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_1.cs)]</span></span>  
<span data-ttu-id="6c094-128">[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]</span><span class="sxs-lookup"><span data-stu-id="6c094-128">[!code-cs[csProgGuideTypes#24](../../../csharp/programming-guide/nullable-types/codesnippet/CSharp/how-to-convert-a-string-to-a-number_7.cs)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6c094-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6c094-129">See Also</span></span>  
 <span data-ttu-id="6c094-130">[類型](../../../csharp/programming-guide/types/index.md) </span><span class="sxs-lookup"><span data-stu-id="6c094-130">[Types](../../../csharp/programming-guide/types/index.md) </span></span>  
 <span data-ttu-id="6c094-131">[如何：判斷字串是否表示數值](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md) </span><span class="sxs-lookup"><span data-stu-id="6c094-131">[How to: Determine Whether a String Represents a Numeric Value](../../../csharp/programming-guide/strings/how-to-determine-whether-a-string-represents-a-numeric-value.md) </span></span>  
 [<span data-ttu-id="6c094-132">.NET Framework 4 格式化公用程式</span><span class="sxs-lookup"><span data-stu-id="6c094-132">.NET Framework 4 Formatting Utility</span></span>](http://code.msdn.microsoft.com/NET-Framework-4-Formatting-9c4dae8d)

