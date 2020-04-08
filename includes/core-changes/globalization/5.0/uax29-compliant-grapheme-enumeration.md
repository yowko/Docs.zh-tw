---
ms.openlocfilehash: f131933f3cf7890939854c46f115e8deb8da1cc2
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888162"
---
### <a name="stringinfo-and-textelementenumerator-are-now-uax29-compliant"></a><span data-ttu-id="38053-101">StringInfo 與文字元素的手舉器現在符合 UAX29 標準</span><span class="sxs-lookup"><span data-stu-id="38053-101">StringInfo and TextElementEnumerator are now UAX29-compliant</span></span>

<span data-ttu-id="38053-102">在此更改之前,<xref:System.Globalization.StringInfo?displayProperty=fullName><xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>並沒有 正確處理所有石墨星系團。</span><span class="sxs-lookup"><span data-stu-id="38053-102">Prior to this change, <xref:System.Globalization.StringInfo?displayProperty=fullName> and <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName> didn't properly handle all grapheme clusters.</span></span> <span data-ttu-id="38053-103">一些石墨烯被分割成其組成成分,而不是放在一起。</span><span class="sxs-lookup"><span data-stu-id="38053-103">Some graphemes were split into their constituent components instead of being kept together.</span></span> <span data-ttu-id="38053-104">現在,<xref:System.Globalization.StringInfo>並<xref:System.Globalization.TextElementEnumerator>根據最新版本的 Unicode 標準處理石墨組。</span><span class="sxs-lookup"><span data-stu-id="38053-104">Now, <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> process grapheme clusters according to the latest version of the Unicode Standard.</span></span>

<span data-ttu-id="38053-105">此外,<xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>該方法在 Visual Basic 中反轉字串中的字元,現在也遵循圖目組中的 Unicode 標準。</span><span class="sxs-lookup"><span data-stu-id="38053-105">In addition, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

#### <a name="change-description"></a><span data-ttu-id="38053-106">變更描述</span><span class="sxs-lookup"><span data-stu-id="38053-106">Change description</span></span>

<span data-ttu-id="38053-107">[圖目或](https://www.unicode.org/glossary/#grapheme)[擴展圖目組](https://www.unicode.org/glossary/#extended_grapheme_cluster)是單個使用者感知的字元,可能由多個 Unicode 代碼點組成。</span><span class="sxs-lookup"><span data-stu-id="38053-107">A [grapheme](https://www.unicode.org/glossary/#grapheme) or [extended grapheme cluster](https://www.unicode.org/glossary/#extended_grapheme_cluster) is a single user-perceived character that may be made up of multiple Unicode code points.</span></span> <span data-ttu-id="38053-108">例如,包含泰語字元「kam」:::no-loc text="กำ":::( ) 的字串由以下兩個字元組成:</span><span class="sxs-lookup"><span data-stu-id="38053-108">For example, the string containing the Thai character "kam" (:::no-loc text="กำ":::) consists of the following two characters:</span></span>

- <span data-ttu-id="38053-109">:::no-loc text="ก":::(= "\u0e01")泰語人物 KO KAI</span><span class="sxs-lookup"><span data-stu-id="38053-109">:::no-loc text="ก"::: (= '\u0e01') THAI CHARACTER KO KAI</span></span>
- <span data-ttu-id="38053-110">:::no-loc text=" ำ":::(= "\u0e33")泰國字元 SARA AM</span><span class="sxs-lookup"><span data-stu-id="38053-110">:::no-loc text=" ำ"::: (= '\u0e33') THAI CHARACTER SARA AM</span></span>

<span data-ttu-id="38053-111">將使用者顯示時,作業系統會兩個字符合並,以形成單個顯示字元(或石墨)"kam'或:::no-loc text="กำ":::。</span><span class="sxs-lookup"><span data-stu-id="38053-111">When displayed to the user, the operating system combines the two characters to form the single display character (or grapheme) "kam" or :::no-loc text="กำ":::.</span></span> <span data-ttu-id="38053-112">表情符號還可以由多個字元組成,這些字元組合起來以類似方式顯示。</span><span class="sxs-lookup"><span data-stu-id="38053-112">Emoji can also consist of multiple characters that are combined for display in a similar way.</span></span>

> [!TIP]
> <span data-ttu-id="38053-113">.NET 文件有時在引用石墨時使用術語"文本元素"。</span><span class="sxs-lookup"><span data-stu-id="38053-113">The .NET documentation sometimes uses the term "text element" when referring to a grapheme.</span></span>

<span data-ttu-id="38053-114"><xref:System.Globalization.StringInfo>和<xref:System.Globalization.TextElementEnumerator>類檢查字串並返回有關它們包含的圖目關係的資訊。</span><span class="sxs-lookup"><span data-stu-id="38053-114">The <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes inspect strings and return information about the graphemes they contain.</span></span> <span data-ttu-id="38053-115">在 .NET 框架 (所有版本)和 .NET Core 3.x 及更早版本中,這兩個類使用自訂邏輯來處理某些組合類,但並不完全符合[Unicode 標準](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries)。</span><span class="sxs-lookup"><span data-stu-id="38053-115">In .NET Framework (all versions) and .NET Core 3.x and earlier, these two classes use custom logic that handles some combining classes but doesn't fully comply with the [Unicode Standard](https://www.unicode.org/reports/tr29/tr29-35.html#Grapheme_Cluster_Boundaries).</span></span> <span data-ttu-id="38053-116">例如,<xref:System.Globalization.StringInfo><xref:System.Globalization.TextElementEnumerator>和 類錯誤地將單個泰語字元"kam"拆分回其組成元件,而不是將它們保留在一起。</span><span class="sxs-lookup"><span data-stu-id="38053-116">For example, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes incorrectly split the single Thai character "kam" back into its constituent components instead of keeping them together.</span></span> <span data-ttu-id="38053-117">這些類還錯誤地將表情符號字元「🤷🏽♀️」拆分為四個群集(人聳肩、膚色修飾器、性別修飾符和不可見的組合器),而不是將它們作為單個圖形學聚類保留在一起。</span><span class="sxs-lookup"><span data-stu-id="38053-117">These classes also incorrectly split the emoji character "🤷🏽‍♀️" into four clusters (person shrugging, skin tone modifier, gender modifier, and an invisible combiner) instead of keeping them together as a single grapheme cluster.</span></span>

<span data-ttu-id="38053-118">從 .NET<xref:System.Globalization.StringInfo><xref:System.Globalization.TextElementEnumerator>5 開始 ,和 類別實現 Unicode 標準定義的 Unicode 標準,由[Unicode\#標準附件 29,第 35,第 3 秒 。](https://www.unicode.org/reports/tr29/tr29-35.html)</span><span class="sxs-lookup"><span data-stu-id="38053-118">Starting with .NET 5, the <xref:System.Globalization.StringInfo> and <xref:System.Globalization.TextElementEnumerator> classes implement the Unicode standard as defined by [Unicode Standard Annex \#29, rev. 35, sec. 3](https://www.unicode.org/reports/tr29/tr29-35.html).</span></span> <span data-ttu-id="38053-119">特別是,它們現在返回所有組合類的[擴展石墨姆群集](https://www.unicode.org/glossary/#extended_grapheme_cluster)。</span><span class="sxs-lookup"><span data-stu-id="38053-119">In particular, they now return [extended grapheme clusters](https://www.unicode.org/glossary/#extended_grapheme_cluster) for all combining classes.</span></span>

<span data-ttu-id="38053-120">請考慮以下 C# 程式碼:</span><span class="sxs-lookup"><span data-stu-id="38053-120">Consider the following C# code:</span></span>

```cs
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

<span data-ttu-id="38053-121">在 .NET 框架和 .NET Core 3.x 和早期版本中,圖形圖姆被拆分,控制台輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="38053-121">In .NET Framework and .NET Core 3.x and earlier versions, the graphemes are split up, and the console output is as follows:</span></span>

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

<span data-ttu-id="38053-122">在 .NET 5 和更高版本中,圖目數保持在一起,控制台輸出如下所示:</span><span class="sxs-lookup"><span data-stu-id="38053-122">In .NET 5 and later versions, the graphemes are kept together, and the console output is as follows:</span></span>

```txt
Printing graphemes of "กำ"...
Grapheme 1: "กำ"
(1 grapheme(s) total.)

Printing graphemes of "🤷🏽‍♀️"...
Grapheme 1: "🤷🏽‍♀️"
(1 grapheme(s) total.)
```

<span data-ttu-id="38053-123">此外,從 .NET<xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>5 開始 ,該方法在 Visual Basic 中反轉字串中的字元,現在也遵循圖目組中的 Unicode 標準。</span><span class="sxs-lookup"><span data-stu-id="38053-123">In addition, starting in .NET 5, the <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName> method, which reverses the characters in a string in Visual Basic, now also follows the Unicode standard for grapheme clusters.</span></span>

<span data-ttu-id="38053-124">這些更改是 .NET 中更廣泛的 Unicode 和 UTF-8 改進集的一部分,包括擴展的圖目組枚舉 API,以補充使用<xref:System.Text.Rune?displayProperty=fullName>.NET Core 3.0 中的類型引入的 Unicode scalar 值枚舉 API。</span><span class="sxs-lookup"><span data-stu-id="38053-124">These changes are part of a wider set of Unicode and UTF-8 improvements in .NET, including an extended grapheme cluster enumeration API to complement the Unicode scalar-value enumeration APIs that were introduced with the <xref:System.Text.Rune?displayProperty=fullName> type in .NET Core 3.0.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="38053-125">介紹的版本</span><span class="sxs-lookup"><span data-stu-id="38053-125">Version introduced</span></span>

<span data-ttu-id="38053-126">.NET 5.0 預覽 1</span><span class="sxs-lookup"><span data-stu-id="38053-126">.NET 5.0 Preview 1</span></span>

### <a name="recommended-action"></a><span data-ttu-id="38053-127">建議的動作</span><span class="sxs-lookup"><span data-stu-id="38053-127">Recommended action</span></span>

<span data-ttu-id="38053-128">您不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="38053-128">You don't need to take any action.</span></span> <span data-ttu-id="38053-129">在各種與全球化相關的方案中,您的應用將自動以更符合標準的方式運行。</span><span class="sxs-lookup"><span data-stu-id="38053-129">Your apps will automatically behave in a more standards-compliant manner in a variety of globalization-related scenarios.</span></span>

### <a name="category"></a><span data-ttu-id="38053-130">類別</span><span class="sxs-lookup"><span data-stu-id="38053-130">Category</span></span>

<span data-ttu-id="38053-131">全球化</span><span class="sxs-lookup"><span data-stu-id="38053-131">Globalization</span></span>

### <a name="affected-apis"></a><span data-ttu-id="38053-132">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="38053-132">Affected APIs</span></span>

- <xref:System.Globalization.StringInfo?displayProperty=fullName>
- <xref:System.Globalization.TextElementEnumerator?displayProperty=fullName>
- <xref:Microsoft.VisualBasic.Strings.StrReverse%2A?displayProperty=fullName>

<!--

- `T:System.Globalization.StringInfo`
- `T:System.Globalization.TextElementEnumerator`
- `Overload:Microsoft.VisualBasic.Strings.StrReverse`

-->
