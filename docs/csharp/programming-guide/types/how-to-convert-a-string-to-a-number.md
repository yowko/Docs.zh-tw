---
title: 如何將字串轉換為數字 - C# 程式設計指南
ms.date: 02/11/2019
helpviewer_keywords:
- conversions [C#]
- conversions [C#], string to int
- converting strings to int [C#]
- strings [C#], converting to int
ms.assetid: 467b9979-86ee-4afd-b734-30299cda91e3
ms.openlocfilehash: 54a4562a5cc493fc287bdf2f6bcf9723557f2a05
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "79157035"
---
# <a name="how-to-convert-a-string-to-a-number-c-programming-guide"></a><span data-ttu-id="7556e-102">如何將字串轉換為數字（C# 程式設計指南）</span><span class="sxs-lookup"><span data-stu-id="7556e-102">How to convert a string to a number (C# Programming Guide)</span></span>

<span data-ttu-id="7556e-103">可以通過調用 在各種數數值型別（、、、`int``long``double`等`Parse`）`TryParse`上找到 的 或 方法，或者通過在<xref:System.Convert?displayProperty=nameWithType>類中使用方法將[字串](../../language-reference/builtin-types/reference-types.md)轉換為數字。</span><span class="sxs-lookup"><span data-stu-id="7556e-103">You can convert a [string](../../language-reference/builtin-types/reference-types.md) to a number by calling the `Parse` or `TryParse` method found on the various numeric types (`int`, `long`, `double`, etc.), or by using methods in the <xref:System.Convert?displayProperty=nameWithType> class.</span></span>  
  
 <span data-ttu-id="7556e-104">`TryParse`如果您有字串，則調用方法（例如[`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)）或`Parse`方法（例如， [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)） 稍微更有效和簡單。</span><span class="sxs-lookup"><span data-stu-id="7556e-104">If you have a string, it is slightly more efficient and straightforward to call a `TryParse` method (for example, [`int.TryParse("11", out number)`](xref:System.Int32.TryParse%2A)) or `Parse` method (for example, [`var number = int.Parse("11")`](xref:System.Int32.Parse%2A)).</span></span>  <span data-ttu-id="7556e-105">使用 <xref:System.Convert> 方法比實作 <xref:System.IConvertible> 的一般物件更有用。</span><span class="sxs-lookup"><span data-stu-id="7556e-105">Using a <xref:System.Convert> method is more useful for general objects that implement <xref:System.IConvertible>.</span></span>  
  
 <span data-ttu-id="7556e-106">您可以在預期字串包含的數值類型上使用 `Parse` 或 `TryParse` 方法，例如 <xref:System.Int32?displayProperty=nameWithType> 類型。</span><span class="sxs-lookup"><span data-stu-id="7556e-106">You can use `Parse` or `TryParse` methods on the numeric type you expect the string contains, such as the <xref:System.Int32?displayProperty=nameWithType> type.</span></span>  <span data-ttu-id="7556e-107"><xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> 方法會在內部使用 <xref:System.Int32.Parse%2A>。</span><span class="sxs-lookup"><span data-stu-id="7556e-107">The <xref:System.Convert.ToInt32%2A?displayProperty=nameWithType> method uses <xref:System.Int32.Parse%2A> internally.</span></span>  <span data-ttu-id="7556e-108">該方法`Parse`返回轉換後的數位;`TryParse`該方法返回指示<xref:System.Boolean>轉換是否成功的值，並在[`out`參數](../../language-reference/keywords/out.md)中返回轉換的數位。</span><span class="sxs-lookup"><span data-stu-id="7556e-108">The `Parse` method returns the converted number; the `TryParse` method returns a <xref:System.Boolean> value that indicates whether the conversion succeeded, and returns the converted number in an [`out` parameter](../../language-reference/keywords/out.md).</span></span> <span data-ttu-id="7556e-109">如果字串不是有效格式，則`Parse`引發異常，而`TryParse`返回`false`。</span><span class="sxs-lookup"><span data-stu-id="7556e-109">If the string is not in a valid format, `Parse` throws an exception, whereas `TryParse` returns `false`.</span></span> <span data-ttu-id="7556e-110">呼叫 `Parse` 方法時，您必須一律使用例外狀況處理在剖析作業失敗時捕捉 <xref:System.FormatException>。</span><span class="sxs-lookup"><span data-stu-id="7556e-110">When calling a `Parse` method, you should always use exception handling to catch a <xref:System.FormatException> in the event that the parse operation fails.</span></span>  
  
## <a name="calling-the-parse-and-tryparse-methods"></a><span data-ttu-id="7556e-111">呼叫 Parse 與 TryParse 方法</span><span class="sxs-lookup"><span data-stu-id="7556e-111">Calling the Parse and TryParse methods</span></span>

<span data-ttu-id="7556e-112">`Parse` 與 `TryParse` 方法會忽略字串開頭和結尾的空格，但所有其他字元必須是來自適當數值型別 (`int`、`long`、`ulong`、`float`、`decimal` 等) 的字元。</span><span class="sxs-lookup"><span data-stu-id="7556e-112">The `Parse` and `TryParse` methods ignore white space at the beginning and at the end of the string, but all other characters must be characters that form the appropriate numeric type (`int`, `long`, `ulong`, `float`, `decimal`, etc.).</span></span>  <span data-ttu-id="7556e-113">若構成數字的字串內有任何空格，則會造成錯誤。</span><span class="sxs-lookup"><span data-stu-id="7556e-113">Any white space within the string that forms the number causes an error.</span></span>  <span data-ttu-id="7556e-114">例如，您可以使用 `decimal.TryParse` 來剖析 "10"、"10.3" 或 "  10  "，但您無法使用此方法來從 "10X"、"1 0" (注意內嵌的空格)、"10 .3" (注意內嵌的空格)、"10e1" (`float.TryParse` 在這裡可以運作) 剖析 10 等。</span><span class="sxs-lookup"><span data-stu-id="7556e-114">For example, you can use `decimal.TryParse` to parse "10", "10.3", or "  10  ", but you cannot use this method to parse 10 from "10X", "1 0" (note the embedded space), "10 .3" (note the embedded space), "10e1" (`float.TryParse` works here), and so on.</span></span> <span data-ttu-id="7556e-115">此外，無法成功剖析值為 `null` 或 <xref:System.String.Empty?displayProperty=nameWithType> 的字串。</span><span class="sxs-lookup"><span data-stu-id="7556e-115">In addition, a string whose value is `null` or <xref:System.String.Empty?displayProperty=nameWithType> fails to parse successfully.</span></span> <span data-ttu-id="7556e-116">您可以透過呼叫 <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> 方法，在嘗試剖析 Null 或空字串之前先進行檢查。</span><span class="sxs-lookup"><span data-stu-id="7556e-116">You can check for a null or empty string before attempting to parse it by calling the <xref:System.String.IsNullOrEmpty%2A?displayProperty=nameWithType> method.</span></span>

<span data-ttu-id="7556e-117">下列範例示範對 `Parse` 與 `TryParse` 的成功呼叫與不成功的呼叫。</span><span class="sxs-lookup"><span data-stu-id="7556e-117">The following example demonstrates both successful and unsuccessful calls to `Parse` and `TryParse`.</span></span>  
  
[!code-csharp[Parse and TryParse](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse/program.cs)]  

<span data-ttu-id="7556e-118">下列範例示範的方法可剖析預期應該包含前置數字字元 (包括十六進位字元) 與結尾非數字字元的字串。</span><span class="sxs-lookup"><span data-stu-id="7556e-118">The following example illustrates one a approach to parsing a string that is expected to include leading numeric characters (including hexadecimal characters) and trailing non-numeric characters.</span></span> <span data-ttu-id="7556e-119">在呼叫 <xref:System.Int32.TryParse%2A> 方法之前，它會將字串開頭的有效字元指派到新字串。</span><span class="sxs-lookup"><span data-stu-id="7556e-119">It assigns valid characters from the beginning of a string to a new string before calling the <xref:System.Int32.TryParse%2A> method.</span></span> <span data-ttu-id="7556e-120">因為要剖析的字串包含一些字元，範例會呼叫 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法以將有效字元指派到新字串。</span><span class="sxs-lookup"><span data-stu-id="7556e-120">Because the strings to be parsed contain a small number of characters, the example calls the <xref:System.String.Concat%2A?displayProperty=nameWithType> method to assign valid characters to a new string.</span></span> <span data-ttu-id="7556e-121">針對較大的字串，可以改為使用 <xref:System.Text.StringBuilder> 類別。</span><span class="sxs-lookup"><span data-stu-id="7556e-121">For a larger string, the <xref:System.Text.StringBuilder> class can be used instead.</span></span>
  
[!code-csharp[Removing invalid characters](~/samples/snippets/csharp/programming-guide/string-to-number/parse-tryparse2/program.cs)]  

## <a name="calling-the-convert-methods"></a><span data-ttu-id="7556e-122">呼叫轉換方法</span><span class="sxs-lookup"><span data-stu-id="7556e-122">Calling the Convert methods</span></span>

<span data-ttu-id="7556e-123">下表列出您可以用來將字串轉換為數字的一些方法 (來自 <xref:System.Convert> 類別)。</span><span class="sxs-lookup"><span data-stu-id="7556e-123">The following table lists some of the methods from the <xref:System.Convert> class that you can use to convert a string to a number.</span></span>  
  
|<span data-ttu-id="7556e-124">數字類型</span><span class="sxs-lookup"><span data-stu-id="7556e-124">Numeric Type</span></span>|<span data-ttu-id="7556e-125">方法</span><span class="sxs-lookup"><span data-stu-id="7556e-125">Method</span></span>|  
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
  
 <span data-ttu-id="7556e-126">下面的示例調用<xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType>方法將輸入字串轉換為[int](../../language-reference/builtin-types/integral-numeric-types.md)。該示例捕獲此方法可以引發的兩個最常見的異常，<xref:System.FormatException>和<xref:System.OverflowException>。</span><span class="sxs-lookup"><span data-stu-id="7556e-126">The following example calls the <xref:System.Convert.ToInt32%28System.String%29?displayProperty=nameWithType> method to convert an input string to an [int](../../language-reference/builtin-types/integral-numeric-types.md). The example catches the two most common exceptions that can be thrown by this method, <xref:System.FormatException> and <xref:System.OverflowException>.</span></span> <span data-ttu-id="7556e-127">若產生的數字可在不超過 <xref:System.Int32.MaxValue?displayProperty=nameWithType> 的情況下遞增，範例會增加 1 到結果並顯示輸出。</span><span class="sxs-lookup"><span data-stu-id="7556e-127">If the resulting number can be incremented without exceeding <xref:System.Int32.MaxValue?displayProperty=nameWithType>, the example adds 1 to the result and displays the output.</span></span>  
  
[!code-csharp[Parsing with Convert methods](~/samples/snippets/csharp/programming-guide/string-to-number/convert/program.cs)]  
  
## <a name="see-also"></a><span data-ttu-id="7556e-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7556e-128">See also</span></span>

- [<span data-ttu-id="7556e-129">型別</span><span class="sxs-lookup"><span data-stu-id="7556e-129">Types</span></span>](./index.md)
- [<span data-ttu-id="7556e-130">如何判斷字串是否表示數值</span><span class="sxs-lookup"><span data-stu-id="7556e-130">How to determine whether a string represents a numeric value</span></span>](../strings/how-to-determine-whether-a-string-represents-a-numeric-value.md)
- <span data-ttu-id="7556e-131">[Sample: .NET Core WinForms Formatting Utility (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs) (範例：.NET Core WinForms 格式化公用程式 (C#))</span><span class="sxs-lookup"><span data-stu-id="7556e-131">[Sample: .NET Core WinForms Formatting Utility (C#)](https://docs.microsoft.com/samples/dotnet/samples/winforms-formatting-utility-cs)</span></span>
