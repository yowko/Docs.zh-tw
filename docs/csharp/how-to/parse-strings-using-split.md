---
title: 如何使用 String.Split(C# 指南)分析字串
description: String.Split 會傳回從一組分隔符號分割的字串陣列。 它容易剖析字串。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: cf8307517213b54041b272843232eb595660b2e9
ms.sourcegitcommit: c91110ef6ee3fedb591f3d628dc17739c4a7071e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/15/2020
ms.locfileid: "81389510"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="0b91f-104">如何使用 String.分割在 C 中分析字串\#</span><span class="sxs-lookup"><span data-stu-id="0b91f-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="0b91f-105"><xref:System.String.Split%2A?displayProperty=nameWithType> 方法會根據一或多個分隔符號來分割輸入字串，以建立子字串陣列。</span><span class="sxs-lookup"><span data-stu-id="0b91f-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="0b91f-106">這通常是分隔字組界限上字串的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="0b91f-106">It is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="0b91f-107">它也用來分割其他特定字元或字串上的字串。</span><span class="sxs-lookup"><span data-stu-id="0b91f-107">It is also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="0b91f-108">下列程式碼將常用詞語分割成每個字組的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="0b91f-108">The following code splits a common phrase into an array of strings for each word.</span></span>

[!code-csharp-interactive[split strings on word boundaries](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#1)]

<span data-ttu-id="0b91f-109">每個分隔符號字元執行個體都會產生已傳回陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="0b91f-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="0b91f-110">連續分隔符號字元會產生空字串，作為已傳回陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="0b91f-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="0b91f-111">您可以在下面的範例中查看如何建立空字串,該示例使用空格字元作為分隔符。</span><span class="sxs-lookup"><span data-stu-id="0b91f-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

[!code-csharp-interactive[split strings with repeated separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#2)]

<span data-ttu-id="0b91f-112">此行為使表示表格數據的逗號分隔值 (CSV) 檔等格式更容易。</span><span class="sxs-lookup"><span data-stu-id="0b91f-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="0b91f-113">連續的逗號表示空白資料行。</span><span class="sxs-lookup"><span data-stu-id="0b91f-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="0b91f-114">您可以傳遞選擇性 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 參數，以排除已傳回陣列中的任何空字串。</span><span class="sxs-lookup"><span data-stu-id="0b91f-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="0b91f-115">針對更複雜處理的已傳回集合，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 來操作結果序列。</span><span class="sxs-lookup"><span data-stu-id="0b91f-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="0b91f-116"><xref:System.String.Split%2A?displayProperty=nameWithType> 可以使用多個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="0b91f-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="0b91f-117">下列範例會使用空格、逗號、句號、冒號和定位點，全部以包含這些分隔符號的陣列傳遞至 <xref:System.String.Split%2A>。</span><span class="sxs-lookup"><span data-stu-id="0b91f-117">The following example uses spaces, commas, periods, colons, and tabs, all passed in an array containing these separating characters, to <xref:System.String.Split%2A>.</span></span>
<span data-ttu-id="0b91f-118">程式碼底部的迴圈會顯示所傳回陣列中的每個字組。</span><span class="sxs-lookup"><span data-stu-id="0b91f-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>  

[!code-csharp-interactive[split strings using multiple separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#3)]

<span data-ttu-id="0b91f-119">任何分隔符號的連續執行個體都會產生輸出陣列中的空字串：</span><span class="sxs-lookup"><span data-stu-id="0b91f-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

[!code-csharp-interactive[split strings using multiple consecutive separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#4)]

<span data-ttu-id="0b91f-120"><xref:System.String.Split%2A?displayProperty=nameWithType> 可以採用字串陣列 (作為分隔符號以剖析目標字串的字元序列，而不是單一字元)。</span><span class="sxs-lookup"><span data-stu-id="0b91f-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>  
  
[!code-csharp-interactive[split strings using strings as separators](../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs#5)]

<span data-ttu-id="0b91f-121">您可以通過查看[GitHub 儲存庫](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings)中的代碼來嘗試這些範例。</span><span class="sxs-lookup"><span data-stu-id="0b91f-121">You can try these samples by looking at the code in our [GitHub repository](https://github.com/dotnet/docs/tree/master/samples/snippets/csharp/how-to/strings).</span></span> <span data-ttu-id="0b91f-122">或者，您可以將範例下載[為 ZIP 檔案](../../../samples/snippets/csharp/how-to/strings.zip)。</span><span class="sxs-lookup"><span data-stu-id="0b91f-122">Or you can download the samples [as a zip file](../../../samples/snippets/csharp/how-to/strings.zip).</span></span>

## <a name="see-also"></a><span data-ttu-id="0b91f-123">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0b91f-123">See also</span></span>

- [<span data-ttu-id="0b91f-124">C# 編程指南</span><span class="sxs-lookup"><span data-stu-id="0b91f-124">C# Programming Guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="0b91f-125">字串</span><span class="sxs-lookup"><span data-stu-id="0b91f-125">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="0b91f-126">.NET 規則運算式</span><span class="sxs-lookup"><span data-stu-id="0b91f-126">.NET Regular Expressions</span></span>](../../standard/base-types/regular-expressions.md)
