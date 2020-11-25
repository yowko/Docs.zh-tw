---
title: 重大變更： System.globalization.stringinfo> 和 TextElementEnumerator 現在已 UAX29 相容
description: 瞭解 .NET 5.0 中的全球化重大變更，其中 System.globalization.stringinfo> 和 TextElementEnumerator 會根據 Unicode 標準的最新版本來語素簇叢集。
ms.date: 04/07/2020
ms.openlocfilehash: cd5ae5a3eb9f2dd9c02bc179a40d454d24101199
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760450"
---
# <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="42dd2-103">System.globalization.stringinfo> 和 TextElementEnumerator 現在已 UAX29 相容</span><span class="sxs-lookup"><span data-stu-id="42dd2-103">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="42dd2-104">在此變更之前，不會 <xref:System.Globalization.StringInfo?displayProperty=fullName> <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> 正確處理所有語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="42dd2-104">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="42dd2-105">有些 graphemes 已分割成其組成元件，而不是保持在一起。</span><span class="sxs-lookup"><span data-stu-id="42dd2-105">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="42dd2-106">現在， <xref:System.Globalization.StringInfo> 並 <xref:System.Globalization.TextElementEnumerator> 根據 Unicode 標準的最新版本處理語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="42dd2-106">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="42dd2-107">此外，方法會將 <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 字串中的字元反轉 Visual Basic，現在也會遵循語素簇叢集的 Unicode 標準。</span><span class="sxs-lookup"><span data-stu-id="42dd2-107">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

## <a name="change-description"></a><span data-ttu-id="42dd2-108">變更描述</span><span class="sxs-lookup"><span data-stu-id="42dd2-108">Change description</span></span>

<span data-ttu-id="42dd2-109">[語素簇](https://www.unicode.org/glossary/#grapheme)或[extended 語素簇](https://www.unicode.org/glossary/#extended_grapheme_cluster)叢集是由多個 Unicode 程式碼點組成的單一使用者感知字元。</span><span class="sxs-lookup"><span data-stu-id="42dd2-109">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="42dd2-110">例如，包含泰文字元 "kam" (:::no-loc text="กำ":::) 包含下列兩個字元的字串：</span><span class="sxs-lookup"><span data-stu-id="42dd2-110">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="42dd2-111">:::no-loc text="ก"::: (= ' \u0e01 ' ) 泰文字元 KO KAI</span><span class="sxs-lookup"><span data-stu-id="42dd2-111">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="42dd2-112">:::no-loc text=" ำ"::: (= ' \u0e33 ' ) 泰文字元 SARA AM</span><span class="sxs-lookup"><span data-stu-id="42dd2-112">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="42dd2-113">向使用者顯示時，作業系統會結合兩個字元來形成單一顯示字元 (或語素簇) "kam" 或 :::no-loc text="กำ"::: 。</span><span class="sxs-lookup"><span data-stu-id="42dd2-113">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="42dd2-114">表情也可以包含多個合併以供顯示的字元。</span><span class="sxs-lookup"><span data-stu-id="42dd2-114">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="42dd2-115">.NET 檔在參考語素簇時，有時會使用「文字元素」一詞。</span><span class="sxs-lookup"><span data-stu-id="42dd2-115">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="42dd2-116"><xref:System.Globalization.StringInfo>和 <xref:System.Globalization.TextElementEnumerator> 類別會檢查字串，並傳回它們所包含之 graphemes 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="42dd2-116">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="42dd2-117">在 .NET Framework () 和 .NET Core 3.x 及更早版本的所有版本，這兩個類別會使用自訂邏輯來處理一些合併類別，但不完全符合 [Unicode 標準](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)。</span><span class="sxs-lookup"><span data-stu-id="42dd2-117">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="42dd2-118">例如， <xref:System.Globalization.StringInfo> 和類別會 <xref:System.Globalization.TextElementEnumerator> 錯誤地將單一泰文字元 "kam" 分割回其構成元件，而不是將它們保持在一起。</span><span class="sxs-lookup"><span data-stu-id="42dd2-118">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="42dd2-119">這些類別也會錯誤地將表情字元 "🤷🏽♀️" 分割成四個叢集 (person shrugging、膚色修飾詞、性別修飾詞和不可見的結合器) ，而不是將它們保持在一起成為單一語素簇叢集。</span><span class="sxs-lookup"><span data-stu-id="42dd2-119">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="42dd2-120">從 .NET 5 開始， <xref:System.Globalization.StringInfo> 和類別會依照 <xref:System.Globalization.TextElementEnumerator> [unicode 標準附錄 \# 29、rev. 35、sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html)的定義來執行 unicode 標準。</span><span class="sxs-lookup"><span data-stu-id="42dd2-120">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="42dd2-121">尤其是，它們現在會傳回所有合併類別的 [擴充語素簇](https://www.unicode.org/glossary/#extended_grapheme_cluster) 叢集。</span><span class="sxs-lookup"><span data-stu-id="42dd2-121">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="42dd2-122">請考慮下列 c # 程式碼：</span><span class="sxs-lookup"><span data-stu-id="42dd2-122">Consider the following C# code:</span></span>

```csharp
using System.Globalization;

static void Main(string[] args)
{
    PrintGraphemes("กำ");
    PrintGraphemes("🤷🏽‍♀️");
}

static void PrintGraphemes(string str)
{
    Console.WriteLine($"Printing graphemes of \"{str}\"...");
    int i = 0;

    TextElementEnumerator enumerator = StringInfo.GetTextElementEnumerator(str);
    while (enumerator.MoveNext())
    {
        Console.WriteLine($"Grapheme {++i}: \"{enumerator.Current}\"");
    }

    Console.WriteLine($"({i} grapheme(s) total.)");
    Console.WriteLine();
}
```

<span data-ttu-id="42dd2-123">在 .NET Framework 和 .NET Core 3.x 及更早版本中，graphemes 會進行分割，主控台輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="42dd2-123">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "ก"
Grapheme 2: "ำ"
(2 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷"
Grapheme 2: "🏽"
Grapheme 3: "‍"
Grapheme 4: "♀️"
(4 grapheme(s) total.)
```

<span data-ttu-id="42dd2-124">在 .NET 5 和更新版本中，graphemes 會保持在一起，而主控台輸出如下所示：</span><span class="sxs-lookup"><span data-stu-id="42dd2-124">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="42dd2-125">此外，從 .NET 5 開始，方法會將 <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> 字串中的字元反轉 Visual Basic 的 Unicode 標準，現在也會遵循語素簇叢集的 Unicode 標準。</span><span class="sxs-lookup"><span data-stu-id="42dd2-125">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="42dd2-126">這些變更是 .NET 中一組更廣泛的 Unicode 和 UTF-8 增強功能的一部分，包括擴充的語素簇叢集列舉 API，以補充 <xref:System.Text.Rune?displayProperty=fullName> .Net Core 3.0 中的類型所引進的 unicode 純量值列舉 api。</span><span class="sxs-lookup"><span data-stu-id="42dd2-126">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="42dd2-127">引進的版本</span><span class="sxs-lookup"><span data-stu-id="42dd2-127">Version introduced</span></span>

<span data-ttu-id="42dd2-128">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="42dd2-128">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="42dd2-129">建議的動作</span><span class="sxs-lookup"><span data-stu-id="42dd2-129">Recommended action</span></span>

<span data-ttu-id="42dd2-130">您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="42dd2-130">You don't need to take any action.</span></span> <span data-ttu-id="42dd2-131">在各種全球化相關案例中，您的應用程式會以更符合標準的方式自動運作。</span><span class="sxs-lookup"><span data-stu-id="42dd2-131">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="42dd2-132">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="42dd2-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

### Affected APIs

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

### Category

Globalization

-->
