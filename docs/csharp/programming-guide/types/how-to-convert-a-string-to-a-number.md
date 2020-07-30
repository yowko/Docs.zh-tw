---
title: '如何將字串轉換成數位-c # 程式設計手冊'
description: '瞭解如何藉由呼叫 Parse、TryParse 或 Convert 類別方法，將字串轉換成 c # 中的數位。'
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 8c46117579a5b787e5d9f3f317296d33bdd1cce1
ms.sourcegitcommit: 552b4b60c094559db9d8178fa74f5bafaece0caf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/29/2020
ms.locfileid: "87381966"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="cdfce-103">如何將字串轉換成數位（c # 程式設計手冊）</span><span class="sxs-lookup"><span data-stu-id="cdfce-103">How to convert a string to a number (C# Programming Guide)</span></span>

<span data-ttu-id="cdfce-104">您可以藉由[string](../../language-reference/builtin-types/reference-types.md)呼叫在 `Parse` `TryParse` 各種數數值型別（、、等）上找到的或方法 `int` `long` `double` ，或使用類別中的方法， <xref:System.Convert?displayProperty=nameWithType> 將字串轉換成數位。</span><span class="sxs-lookup"><span data-stu-id="cdfce-104">You can convert a [string](../../language-reference/builtin-types/reference-types.md) to a number by calling the `Parse` or `TryParse` method found on the various numeric types (`int`, `long`, `double`, etc.), or by using methods in the <xref:System.Convert?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="cdfce-105">如果您有一個字串，呼叫 `TryParse` 方法（例如， [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A) ）或 `Parse` 方法（例如）會稍微提高效率和直接 [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A) 。</span><span class="sxs-lookup"><span data-stu-id="cdfce-105">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) or `Parse` method (for example, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).</span></span>  <span data-ttu-id="cdfce-106">使用 <xref:System.Convert> 方法比實作 <xref:System.IConvertible> 的一般物件更有用。</span><span class="sxs-lookup"><span data-stu-id="cdfce-106">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="cdfce-107">您可以在預期字串包含的數值類型上使用 `Parse` 或 `TryParse` 方法，例如 <xref:System.Int32?displayProperty=nameWithType> 類型。</span><span class="sxs-lookup"><span data-stu-id="cdfce-107">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="cdfce-108"><xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> 方法會在內部使用 <xref:System.Int32.Parse%2A>。</span><span class="sxs-lookup"><span data-stu-id="cdfce-108">The <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="cdfce-109">`Parse`方法會傳回已轉換的數位; 此 `TryParse` 方法會傳回 <xref:System.Boolean> 值，指出轉換是否成功，並在[ `out` 參數](../../language-reference/keywords/out.md)中傳回已轉換的數位。</span><span class="sxs-lookup"><span data-stu-id="cdfce-109">The `Parse` method returns the converted number; the `TryParse` method returns a <xref:System.Boolean> value that indicates whether the conversion succeeded, and returns the converted number in an [`out` parameter](../../language-reference/keywords/out.md).</span></span> <span data-ttu-id="cdfce-110">如果字串的格式無效，則會擲回 `Parse` 例外狀況，而會 `TryParse` 傳回 `false` 。</span><span class="sxs-lookup"><span data-stu-id="cdfce-110">If the string is not in a valid format, `Parse` throws an exception, whereas `TryParse` returns `false`.</span></span> <span data-ttu-id="cdfce-111">呼叫 `Parse` 方法時，您必須一律使用例外狀況處理在剖析作業失敗時捕捉 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="cdfce-111">When calling a `Parse` method, you should always use exception handling to catch a <xref:System.FormatException> in the event that the parse operation fails.</span></span>  
  
## <a name="calling-the-parse-and-tryparse-methods"></a><span data-ttu-id="cdfce-112">呼叫 Parse 與 TryParse 方法</span><span class="sxs-lookup"><span data-stu-id="cdfce-112">Calling the Parse and TryParse methods</span></span>

<span data-ttu-id="cdfce-113">`Parse` 與 `TryParse` 方法會忽略字串開頭和結尾的空格，但所有其他字元必須是來自適當數值型別 (`int`、`long`、`ulong`、`float`、`decimal` 等) 的字元。</span><span class="sxs-lookup"><span data-stu-id="cdfce-113">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (`int`, `long`, `ulong`, `float`, `decimal`, etc.).</span></span>  <span data-ttu-id="cdfce-114">若構成數字的字串內有任何空格，則會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="cdfce-114">Any white space within the string that forms the number causes an error.</span></span>  <span data-ttu-id="cdfce-115">例如，您可以使用 `decimal.TryParse` 來剖析 "10"、"10.3" 或 "  10  "，但您無法使用此方法來從 "10X"、"1 0" (注意內嵌的空格)、"10 .3" (注意內嵌的空格)、"10e1" (`float.TryParse` 在這裡可以運作) 剖析 10 等。</span><span class="sxs-lookup"><span data-stu-id="cdfce-115">For example, you can use `decimal.TryParse` to parse "10", "10.3", or "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note the embedded space), "10 .3" (note the embedded space), "10e1" (`float.TryParse` works here), and so on.</span></span> <span data-ttu-id="cdfce-116">此外，無法成功剖析值為 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> 的字串。</span><span class="sxs-lookup"><span data-stu-id="cdfce-116">In addition, a string whose value is `null` or <xref:System.String.Empty?displayProperty=nameWithType> fails to parse successfully.</span></span> <span data-ttu-id="cdfce-117">您可以透過呼叫 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法，在嘗試剖析 Null 或空字串之前先進行檢查。</span><span class="sxs-lookup"><span data-stu-id="cdfce-117">You can check for a null or empty string before attempting to parse it by calling the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="cdfce-118">下列範例示範對 `Parse` 與 `TryParse` 的成功呼叫與不成功的呼叫。</span><span class="sxs-lookup"><span data-stu-id="cdfce-118">The following example demonstrates both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

<span data-ttu-id="cdfce-119">下列範例示範的方法可剖析預期應該包含前置數字字元 (包括十六進位字元) 與結尾非數字字元的字串。</span><span class="sxs-lookup"><span data-stu-id="cdfce-119">The following example illustrates one a approach to parsing a string that is expected to include leading numeric characters (including hexadecimal characters) and trailing non-numeric characters.</span></span> <span data-ttu-id="cdfce-120">在呼叫 <xref:System.Int32.TryParse%2A> 方法之前，它會將字串開頭的有效字元指派到新字串。</span><span class="sxs-lookup"><span data-stu-id="cdfce-120">It assigns valid characters from the beginning of a string to a new string before calling the <xref:System.Int32.TryParse%2A> method.</span></span> <span data-ttu-id="cdfce-121">因為要剖析的字串包含一些字元，範例會呼叫 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法以將有效字元指派到新字串。</span><span class="sxs-lookup"><span data-stu-id="cdfce-121">Because the strings to be parsed contain a small number of characters, the example calls the <xref:System.String.Concat%2A?displayProperty=nameWithType> method to assign valid characters to a new string.</span></span> <span data-ttu-id="cdfce-122">針對較大的字串，可以改為使用 <xref:System.Text.StringBuilder> 類別。</span><span class="sxs-lookup"><span data-stu-id="cdfce-122">For a larger string, the <xref:System.Text.StringBuilder> class can be used instead.</span></span>
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a><span data-ttu-id="cdfce-123">呼叫轉換方法</span><span class="sxs-lookup"><span data-stu-id="cdfce-123">Calling the Convert methods</span></span>

<span data-ttu-id="cdfce-124">下表列出您可以用來將字串轉換為數字的一些方法 (來自 <xref:System.Convert> 類別)。</span><span class="sxs-lookup"><span data-stu-id="cdfce-124">The following table lists some of the methods from the <xref:System.Convert> class that you can use to convert a string to a number.</span></span>  
  
|<span data-ttu-id="cdfce-125">數字類型</span><span class="sxs-lookup"><span data-stu-id="cdfce-125">Numeric Type</span></span>|<span data-ttu-id="cdfce-126">方法</span><span class="sxs-lookup"><span data-stu-id="cdfce-126">Method</span></span>|  
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
  
 <span data-ttu-id="cdfce-127">下列範例會呼叫 <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> 方法，將輸入字串轉換為[int](../../language-reference/builtin-types/integral-numeric-types.md)。此範例會攔截可由這個方法擲回的兩個最常見的例外狀況： <xref:System.FormatException> 和 <xref:System.OverflowException> 。</span><span class="sxs-lookup"><span data-stu-id="cdfce-127">The following example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input string to an [int](../../language-reference/builtin-types/integral-numeric-types.md). The example catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="cdfce-128">若產生的數字可在不超過 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的情況下遞增，範例會增加 1 到結果並顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="cdfce-128">If the resulting number can be incremented without exceeding <xref:System.Int32.MaxValue?displayProperty=nameWithType>, the example adds 1 to the result and displays the output.</span></span>  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="cdfce-129">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cdfce-129">See also</span></span>

- [<span data-ttu-id="cdfce-130">類型</span><span class="sxs-lookup"><span data-stu-id="cdfce-130">Types</span></span>](./index.md)
- [<span data-ttu-id="cdfce-131">如何判斷字串是否表示數值</span><span class="sxs-lookup"><span data-stu-id="cdfce-131">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- <span data-ttu-id="cdfce-132">[Sample: .NET Core WinForms Formatting Utility (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs) (範例：.NET Core WinForms 格式化公用程式 (C#))</span><span class="sxs-lookup"><span data-stu-id="cdfce-132">[Sample: .NET Core WinForms Formatting Utility (C#)](https://docs.microsoft.com/samples/dotnet/samples/windowsforms-formatting-utility-cs)</span></span>
