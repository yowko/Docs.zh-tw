---
title: '使用字串剖析字串。分割（c # 指南）'
description: Split 方法會傳回從一組分隔符號分割的字串陣列。 它容易剖析字串。
ms.date: 01/03/2018
helpviewer_keywords:
- splitting strings [C#]
- Split method [C#]
- strings [C#], splitting
- parse strings
ms.assetid: 729c2923-4169-41c6-9c90-ef176c1e2953
ms.custom: mvc
ms.openlocfilehash: 7c5d8fa462775c6f3a9981693129997dda6c2286
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/24/2020
ms.locfileid: "85324142"
---
# <a name="how-to-parse-strings-using-stringsplit-in-c"></a><span data-ttu-id="b1f5d-104">如何使用字串來剖析字串。在 C 中分割\#</span><span class="sxs-lookup"><span data-stu-id="b1f5d-104">How to parse strings using String.Split in C\#</span></span>

<span data-ttu-id="b1f5d-105"><xref:System.String.Split%2A?displayProperty=nameWithType> 方法會根據一或多個分隔符號來分割輸入字串，以建立子字串陣列。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-105">The <xref:System.String.Split%2A?displayProperty=nameWithType> method creates an array of substrings by splitting the input string based on one or more delimiters.</span></span> <span data-ttu-id="b1f5d-106">這個方法通常是在文字界限上分隔字串的最簡單方式。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-106">This method is often the easiest way to separate a string on word boundaries.</span></span> <span data-ttu-id="b1f5d-107">它也可用來分割其他特定字元或字串的字串。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-107">It's also used to split strings on other specific characters or strings.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="b1f5d-108">下列程式碼將常用詞語分割成每個字組的字串陣列。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-108">The following code splits a common phrase into an array of strings for each word.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet1":::

<span data-ttu-id="b1f5d-109">每個分隔符號字元執行個體都會產生已傳回陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-109">Every instance of a separator character produces a value in the returned array.</span></span> <span data-ttu-id="b1f5d-110">連續分隔符號字元會產生空字串，作為已傳回陣列中的值。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-110">Consecutive separator characters produce the empty string as a value in the returned array.</span></span> <span data-ttu-id="b1f5d-111">在下列範例中，您可以看到空字串的建立方式，其使用空白字元做為分隔符號。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-111">You can see how an empty string is created in the following example, which uses the space character as a separator.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet2":::

<span data-ttu-id="b1f5d-112">這種行為可讓格式類似逗號分隔值（CSV）檔案（代表表格式資料）變得更容易。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-112">This behavior makes it easier for formats like comma-separated values (CSV) files representing tabular data.</span></span> <span data-ttu-id="b1f5d-113">連續的逗號表示空白資料行。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-113">Consecutive commas represent a blank column.</span></span>

<span data-ttu-id="b1f5d-114">您可以傳遞選擇性 <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> 參數，以排除已傳回陣列中的任何空字串。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-114">You can pass an optional <xref:System.StringSplitOptions.RemoveEmptyEntries?displayProperty=nameWithType> parameter to exclude any empty strings in the returned array.</span></span> <span data-ttu-id="b1f5d-115">針對更複雜處理的已傳回集合，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 來操作結果序列。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-115">For more complicated processing of the returned collection, you can use [LINQ](../programming-guide/concepts/linq/index.md) to manipulate the result sequence.</span></span>

<span data-ttu-id="b1f5d-116"><xref:System.String.Split%2A?displayProperty=nameWithType> 可以使用多個分隔符號字元。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-116"><xref:System.String.Split%2A?displayProperty=nameWithType> can use multiple separator characters.</span></span>
<span data-ttu-id="b1f5d-117">下列範例會使用空格、逗號、句號、冒號和索引標籤來分隔字元，並將它們傳遞至 <xref:System.String.Split%2A> 陣列中的。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-117">The following example uses spaces, commas, periods, colons, and tabs as separating characters, which are passed to <xref:System.String.Split%2A> in an array .</span></span>
<span data-ttu-id="b1f5d-118">程式碼底部的迴圈會顯示所傳回陣列中的每個字組。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-118">The loop at the bottom of the code displays each of the words in the returned array.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet3":::

<span data-ttu-id="b1f5d-119">任何分隔符號的連續執行個體都會產生輸出陣列中的空字串：</span><span class="sxs-lookup"><span data-stu-id="b1f5d-119">Consecutive instances of any separator produce the empty string in the output array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet4":::

<span data-ttu-id="b1f5d-120"><xref:System.String.Split%2A?displayProperty=nameWithType> 可以採用字串陣列 (作為分隔符號以剖析目標字串的字元序列，而不是單一字元)。</span><span class="sxs-lookup"><span data-stu-id="b1f5d-120"><xref:System.String.Split%2A?displayProperty=nameWithType> can take an array of strings (character sequences that act as separators for parsing the target string, instead of single characters).</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/ParseStringsUsingSplit.cs" id="Snippet5":::

## <a name="see-also"></a><span data-ttu-id="b1f5d-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b1f5d-121">See also</span></span>

- [<span data-ttu-id="b1f5d-122">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="b1f5d-122">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="b1f5d-123">字串</span><span class="sxs-lookup"><span data-stu-id="b1f5d-123">Strings</span></span>](../programming-guide/strings/index.md)
- [<span data-ttu-id="b1f5d-124">.NET 正則運算式</span><span class="sxs-lookup"><span data-stu-id="b1f5d-124">.NET regular expressions</span></span>](../../standard/base-types/regular-expressions.md)
