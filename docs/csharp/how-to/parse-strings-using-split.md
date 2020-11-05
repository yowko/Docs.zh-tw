---
title: '使用字串分割字串 (c # 指南) '
description: Split 方法會傳回從一組分隔符號分割的字串陣列。 它是從字串中解壓縮子字串的簡單方法。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 5361a3c60905edd19b180c5ddb14064a85f64337
ms.sourcegitcommit: 48466b8fb7332ececff5dc388f19f6b3ff503dd4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/05/2020
ms.locfileid: "93400496"
---
# <a name="how-to-separate-strings-using-stringsplit-in-c"></a><span data-ttu-id="d97c7-104">如何使用字串分隔字串。以 C 分隔\#</span><span class="sxs-lookup"><span data-stu-id="d97c7-104">How to separate strings using String.Split in C\#</span></span>

<span data-ttu-id="d97c7-105"><xref:System.String.Split%2A?displayProperty=nameWithType> 方法會根據一或多個分隔符號來分割輸入字串，以建立子字串陣列。</span><span class="sxs-lookup"><span data-stu-id="d97c7-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="d97c7-106">這種方法通常是在單字邊界上分隔字串的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="d97c7-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="d97c7-107">它也可用來將字串分割成其他特定字元或字串。</span><span class="sxs-lookup"><span data-stu-id="d97c7-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="d97c7-108">下列程式碼將常用詞語分割成每個字組的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="d97c7-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="d97c7-109">每個分隔符號字元執行個體都會產生已傳回陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="d97c7-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="d97c7-110">連續分隔符號字元會產生空字串，作為已傳回陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="d97c7-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="d97c7-111">您可以在下列範例中看到如何建立空字串，此範例會使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="d97c7-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="d97c7-112">這種行為可讓您更輕鬆地格式，像是逗號分隔值 (CSV) 代表表格式資料的檔案。</span><span class="sxs-lookup"><span data-stu-id="d97c7-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="d97c7-113">連續的逗號表示空白資料行。</span><span class="sxs-lookup"><span data-stu-id="d97c7-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="d97c7-114">您可以傳遞選擇性 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 參數，以排除已傳回陣列中的任何空字串。</span><span class="sxs-lookup"><span data-stu-id="d97c7-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="d97c7-115">針對更複雜處理的已傳回集合，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 來操作結果序列。</span><span class="sxs-lookup"><span data-stu-id="d97c7-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="d97c7-116"><xref:System.String.Split%2A?displayProperty=nameWithType> 可以使用多個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="d97c7-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="d97c7-117">下列範例會使用空格、逗號、句號、冒號和定位點來分隔在陣列中傳遞給的字元 <xref:System.String.Split%2A> 。</span><span class="sxs-lookup"><span data-stu-id="d97c7-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="d97c7-118">程式碼底部的迴圈會顯示所傳回陣列中的每個字組。</span><span class="sxs-lookup"><span data-stu-id="d97c7-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="d97c7-119">任何分隔符號的連續執行個體都會產生輸出陣列中的空字串：</span><span class="sxs-lookup"><span data-stu-id="d97c7-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="d97c7-120"><xref:System.String.Split%2A?displayProperty=nameWithType> 可以採用字串陣列 (作為分隔符號以剖析目標字串的字元序列，而不是單一字元)。</span><span class="sxs-lookup"><span data-stu-id="d97c7-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="d97c7-121">請參閱</span><span class="sxs-lookup"><span data-stu-id="d97c7-121">See also</span></span>

- [<span data-ttu-id="d97c7-122">從字串擷取元素</span><span class="sxs-lookup"><span data-stu-id="d97c7-122">Extract elements from a string</span></span>](../../standard/base-types/divide-up-strings.md)
- [<span data-ttu-id="d97c7-123">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="d97c7-123">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="d97c7-124">字串</span><span class="sxs-lookup"><span data-stu-id="d97c7-124">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="d97c7-125">.NET 正則運算式</span><span class="sxs-lookup"><span data-stu-id="d97c7-125">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
