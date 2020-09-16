---
title: '如何串連多個字串 (c # 指南) '
description: 以下提供用 C# 串連字串的多種方式。 了解選項及做出不同選擇的原因。
ms.date: 02/20/2018
helpviewer_keywords:
- joining strings [C#]
- concatenating strings [C#]
- strings [C#], concatenation
ms.assetid: 8e16736f-4096-4f3f-be0f-9d4c3ff63520
ms.openlocfilehash: f2aae14deac967a833fb3510acdb32e0971485b5
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90537479"
---
# <a name="how-to-concatenate-multiple-strings-c-guide"></a><span data-ttu-id="4ee78-104">如何串連多個字串 (c # 指南) </span><span class="sxs-lookup"><span data-stu-id="4ee78-104">How to concatenate multiple strings (C# Guide)</span></span>

<span data-ttu-id="4ee78-105">「串連」\*\* 是將一個字串附加至另一個字串結尾的程序。</span><span class="sxs-lookup"><span data-stu-id="4ee78-105">*Concatenation* is the process of appending one string to the end of another string.</span></span> <span data-ttu-id="4ee78-106">使用 `+` 運算子即可串連字串。</span><span class="sxs-lookup"><span data-stu-id="4ee78-106">You concatenate strings by using the `+` operator.</span></span> <span data-ttu-id="4ee78-107">若是字串常值和字串常數，會在編譯時間進行串連；在非編譯時間不會發生串連。</span><span class="sxs-lookup"><span data-stu-id="4ee78-107">For string literals and string constants, concatenation occurs at compile time; no run-time concatenation occurs.</span></span> <span data-ttu-id="4ee78-108">若是字串變數，串連只會發生在執行階段。</span><span class="sxs-lookup"><span data-stu-id="4ee78-108">For string variables, concatenation occurs only at run time.</span></span>

[!INCLUDE[interactive-note](~/includes/csharp-interactive-note.md)]

<span data-ttu-id="4ee78-109">下例使用串連將長字串常值分割成較小的字串，以改善原始程式碼的可讀性。</span><span class="sxs-lookup"><span data-stu-id="4ee78-109">The following example uses concatenation to split a long string literal into smaller strings in order to improve readability in the source code.</span></span> <span data-ttu-id="4ee78-110">這些組件在編譯時期會串連成單一字串。</span><span class="sxs-lookup"><span data-stu-id="4ee78-110">These parts are concatenated into a single string at compile time.</span></span> <span data-ttu-id="4ee78-111">不論範圍涵蓋多少字串，都不會產生執行階段效能成本。</span><span class="sxs-lookup"><span data-stu-id="4ee78-111">There is no run-time performance cost regardless of the number of strings involved.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet1":::

<span data-ttu-id="4ee78-112">若要串連字號串變數，您可以使用 `+` 或 `+=` 運算子、 [字串插補](../language-reference/tokens/interpolated.md) 或 <xref:System.String.Format%2A?displayProperty=nameWithType> 、 <xref:System.String.Concat%2A?displayProperty=nameWithType> <xref:System.String.Join%2A?displayProperty=nameWithType> 或 <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4ee78-112">To concatenate string variables, you can use the `+` or `+=` operators, [string interpolation](../language-reference/tokens/interpolated.md) or the <xref:System.String.Format%2A?displayProperty=nameWithType>, <xref:System.String.Concat%2A?displayProperty=nameWithType>, <xref:System.String.Join%2A?displayProperty=nameWithType> or <xref:System.Text.StringBuilder.Append%2A?displayProperty=nameWithType> methods.</span></span> <span data-ttu-id="4ee78-113">`+` 運算子簡單易用，且容易建立直覺化程式碼。</span><span class="sxs-lookup"><span data-stu-id="4ee78-113">The `+` operator is easy to use and makes for intuitive code.</span></span> <span data-ttu-id="4ee78-114">即使一個陳述式使用數個 `+` 運算子，字串內容也只會複製一次。</span><span class="sxs-lookup"><span data-stu-id="4ee78-114">Even if you use several `+` operators in one statement, the string content is copied only once.</span></span> <span data-ttu-id="4ee78-115">下列程式碼示範使用 `+` 和 `+=` 運算子來串連字串的範例：</span><span class="sxs-lookup"><span data-stu-id="4ee78-115">The following code shows examples of using the `+` and `+=` operators to concatenate strings:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet2":::

<span data-ttu-id="4ee78-116">在某些運算式中，使用字串內插補點會更容易串連字串，如下列程式碼所示：</span><span class="sxs-lookup"><span data-stu-id="4ee78-116">In some expressions, it's easier to concatenate strings using string interpolation, as the following code shows:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet3":::

> [!NOTE]
> <span data-ttu-id="4ee78-117">在字串串連作業中，C# 編譯器會將 null 字串視同空字串。</span><span class="sxs-lookup"><span data-stu-id="4ee78-117">In string concatenation operations, the C# compiler treats a null string the same as an empty string.</span></span>

<span data-ttu-id="4ee78-118"><xref:System.String.Format%2A?displayProperty=nameWithType> 也是串連字串的方法。</span><span class="sxs-lookup"><span data-stu-id="4ee78-118">Other method to concatenate strings is <xref:System.String.Format%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="4ee78-119">當您從少量元件字串建置字串時，此方法能順利執行。</span><span class="sxs-lookup"><span data-stu-id="4ee78-119">This method works well when you are building a string from a small number of component strings.</span></span>

<span data-ttu-id="4ee78-120">在其他情況下，您可能會在迴圈中合併字串，而您不知道要合併多少來源字串，且實際的來源字串數目可能很大。</span><span class="sxs-lookup"><span data-stu-id="4ee78-120">In other cases, you may be combining strings in a loop where you don't know how many source strings you're combining, and the actual number of source strings may be large.</span></span> <span data-ttu-id="4ee78-121"><xref:System.Text.StringBuilder> 類別專為這種案例而設計。</span><span class="sxs-lookup"><span data-stu-id="4ee78-121">The <xref:System.Text.StringBuilder> class was designed for these scenarios.</span></span> <span data-ttu-id="4ee78-122">下列程式碼會使用 <xref:System.Text.StringBuilder> 類別的 <xref:System.Text.StringBuilder.Append%2A> 方法來串連字串。</span><span class="sxs-lookup"><span data-stu-id="4ee78-122">The following code uses the <xref:System.Text.StringBuilder.Append%2A> method of the <xref:System.Text.StringBuilder> class to concatenate strings.</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet4":::

<span data-ttu-id="4ee78-123">您可以閱讀更多有關 [選擇字串串連或 `StringBuilder` 類別的原因](/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types)。</span><span class="sxs-lookup"><span data-stu-id="4ee78-123">You can read more about the [reasons to choose string concatenation or the `StringBuilder` class](/dotnet/api/system.text.stringbuilder#the-string-and-stringbuilder-types).</span></span>

<span data-ttu-id="4ee78-124">從集合加入字串的另一個選項是使用 <xref:System.String.Concat%2A?displayProperty=nameWithType> 方法。</span><span class="sxs-lookup"><span data-stu-id="4ee78-124">Another option to join strings from a collection is to use <xref:System.String.Concat%2A?displayProperty=nameWithType> method.</span></span> <span data-ttu-id="4ee78-125"><xref:System.String.Join%2A?displayProperty=nameWithType>如果來源字串應以分隔符號分隔，請使用方法。</span><span class="sxs-lookup"><span data-stu-id="4ee78-125">Use <xref:System.String.Join%2A?displayProperty=nameWithType> method if source strings should be separated by a delimiter.</span></span> <span data-ttu-id="4ee78-126">下列程式碼會使用這兩種方法來結合文字陣列：</span><span class="sxs-lookup"><span data-stu-id="4ee78-126">The following code combines an array of words using both methods:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet5":::

<span data-ttu-id="4ee78-127">最後，您可以使用 [LINQ](../programming-guide/concepts/linq/index.md) 和 <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> 方法從集合加入字串。</span><span class="sxs-lookup"><span data-stu-id="4ee78-127">At last, you can use [LINQ](../programming-guide/concepts/linq/index.md) and the <xref:System.Linq.Enumerable.Aggregate%2A?displayProperty=nameWithType> method to join strings from a collection.</span></span> <span data-ttu-id="4ee78-128">這個方法使用 Lambda 運算式結合來源字串。</span><span class="sxs-lookup"><span data-stu-id="4ee78-128">This method combines the source strings using a lambda expression.</span></span> <span data-ttu-id="4ee78-129">Lambda 運算式會負責將各個字串新增到目前累積的內容。</span><span class="sxs-lookup"><span data-stu-id="4ee78-129">The lambda expression does the work to add each string to the existing accumulation.</span></span> <span data-ttu-id="4ee78-130">下列範例透過在陣列中的每個字之間新增空格，結合一個陣列的字組：</span><span class="sxs-lookup"><span data-stu-id="4ee78-130">The following example combines an array of words by adding a space between each word in the array:</span></span>

:::code language="csharp" interactive="try-dotnet-method" source="../../../samples/snippets/csharp/how-to/strings/Concatenate.cs" id="Snippet6":::

## <a name="see-also"></a><span data-ttu-id="4ee78-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4ee78-131">See also</span></span>

- <xref:System.String>
- <xref:System.Text.StringBuilder>
- [<span data-ttu-id="4ee78-132">C# 程式設計手冊</span><span class="sxs-lookup"><span data-stu-id="4ee78-132">C# programming guide</span></span>](../programming-guide/index.md)
- [<span data-ttu-id="4ee78-133">字串</span><span class="sxs-lookup"><span data-stu-id="4ee78-133">Strings</span></span>](../programming-guide/strings/index.md)
