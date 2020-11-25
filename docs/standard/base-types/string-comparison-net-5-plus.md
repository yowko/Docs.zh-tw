---
title: 比較 .NET 5 + 上的字串時的行為變更
description: 瞭解 Windows 上 .NET 5 和更新版本中的字串比較行為變更。
ms.date: 11/04/2020
ms.openlocfilehash: fa1a1d12f45e5b41877a674d7b8747bb2b2f9658
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95734227"
---
# <a name="behavior-changes-when-comparing-strings-on-net-5"></a><span data-ttu-id="e02ab-103">比較 .NET 5 + 上的字串時的行為變更</span><span class="sxs-lookup"><span data-stu-id="e02ab-103">Behavior changes when comparing strings on .NET 5+</span></span>

<span data-ttu-id="e02ab-104">.NET 5.0 引進了執行時間行為變更，其中的全球化 Api 預設會在所有支援的平臺上 [使用 ICU](../../core/compatibility/globalization/5.0/icu-globalization-api.md) 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-104">.NET 5.0 introduces a runtime behavioral change where globalization APIs [now use ICU by default](../../core/compatibility/globalization/5.0/icu-globalization-api.md) across all supported platforms.</span></span> <span data-ttu-id="e02ab-105">這是舊版 .NET Core 和 .NET Framework 中的一項服務，它會在 Windows 上執行時，利用作業系統的國家語言支援 (NLS) 功能。</span><span class="sxs-lookup"><span data-stu-id="e02ab-105">This is a departure from earlier versions of .NET Core and from .NET Framework, which utilize the operating system's national language support (NLS) functionality when running on Windows.</span></span> <span data-ttu-id="e02ab-106">如需這些變更的詳細資訊，包括可還原行為變更的相容性參數，請參閱 [.net 全球化和 ICU](../globalization-localization/globalization-icu.md)。</span><span class="sxs-lookup"><span data-stu-id="e02ab-106">For more information on these changes, including compatibility switches that can revert the behavior change, see [.NET globalization and ICU](../globalization-localization/globalization-icu.md).</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="e02ab-107">變更的原因</span><span class="sxs-lookup"><span data-stu-id="e02ab-107">Reason for change</span></span>

<span data-ttu-id="e02ab-108">這是為了統一而引進的變更。在所有支援的作業系統上的淨全球化行為。</span><span class="sxs-lookup"><span data-stu-id="e02ab-108">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="e02ab-109">它也能讓應用程式組合自己的全球化程式庫，而不需要依賴作業系統的內建程式庫。</span><span class="sxs-lookup"><span data-stu-id="e02ab-109">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the OS's built-in libraries.</span></span> <span data-ttu-id="e02ab-110">如需詳細資訊，請參閱 [重大變更通知](../../core/compatibility/globalization/5.0/icu-globalization-api.md)。</span><span class="sxs-lookup"><span data-stu-id="e02ab-110">For more information, see [the breaking change notification](../../core/compatibility/globalization/5.0/icu-globalization-api.md).</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="e02ab-111">行為差異</span><span class="sxs-lookup"><span data-stu-id="e02ab-111">Behavioral differences</span></span>

<span data-ttu-id="e02ab-112">如果您在 `string.IndexOf(string)` 不呼叫接受引數的多載的情況下使用像這樣的函 <xref:System.StringComparison> 式，您可能會想要執行 *序數* 搜尋，但您不小心相依于特定文化特性的行為。</span><span class="sxs-lookup"><span data-stu-id="e02ab-112">If you use functions like `string.IndexOf(string)` without calling the overload that takes a <xref:System.StringComparison> argument, you might intend to perform an *ordinal* search, but instead you inadvertently take a dependency on culture-specific behavior.</span></span> <span data-ttu-id="e02ab-113">由於 NLS 和 ICU 在其語言比較子中執行不同的邏輯，因此方法的結果 `string.IndexOf(string)` 可能會傳回非預期的值。</span><span class="sxs-lookup"><span data-stu-id="e02ab-113">Since NLS and ICU implement different logic in their linguistic comparers, the results of methods like `string.IndexOf(string)` can return unexpected values.</span></span>

<span data-ttu-id="e02ab-114">這可能會在您不希望全球化設施處於作用中的地方出現本身的資訊清單。</span><span class="sxs-lookup"><span data-stu-id="e02ab-114">This can manifest itself even in places where you aren't always expecting globalization facilities to be active.</span></span> <span data-ttu-id="e02ab-115">例如，下列程式碼可能會根據目前的執行時間產生不同的答案。</span><span class="sxs-lookup"><span data-stu-id="e02ab-115">For example, the following code can produce a different answer depending on the current runtime.</span></span>

```cs
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);

// The snippet prints:
//
// '6' when running on .NET Framework (Windows)
// '6' when running on .NET Core 2.x - 3.x (Windows)
// '-1' when running on .NET 5 (Windows)
// '-1' when running on .NET Core 2.x - 3.x or .NET 5 (non-Windows)
// '6' when running on .NET Core 2.x or .NET 5 (in invariant mode)
```

## <a name="guard-against-unexpected-behavior"></a><span data-ttu-id="e02ab-116">防止非預期的行為</span><span class="sxs-lookup"><span data-stu-id="e02ab-116">Guard against unexpected behavior</span></span>

<span data-ttu-id="e02ab-117">本節提供兩個選項來處理 .NET 5.0 中非預期的行為變更。</span><span class="sxs-lookup"><span data-stu-id="e02ab-117">This section provides two options for dealing with unexpected behavior changes in .NET 5.0.</span></span>

### <a name="enable-code-analyzers"></a><span data-ttu-id="e02ab-118">啟用程式碼分析器</span><span class="sxs-lookup"><span data-stu-id="e02ab-118">Enable code analyzers</span></span>

<span data-ttu-id="e02ab-119">程式[代碼分析器](../../fundamentals/code-analysis/overview.md)可以偵測到可能有錯誤的呼叫網站。</span><span class="sxs-lookup"><span data-stu-id="e02ab-119">[Code analyzers](../../fundamentals/code-analysis/overview.md) can detect possibly buggy call sites.</span></span> <span data-ttu-id="e02ab-120">為了防止任何令人驚訝的行為，建議您 [將 __CodeAnalysis 將 microsoft.codeanalysis.fxcopanalyzers__ NuGet 套件](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) 安裝到您的專案中。</span><span class="sxs-lookup"><span data-stu-id="e02ab-120">To help guard against any surprising behaviors, we recommend installing [the __Microsoft.CodeAnalysis.FxCopAnalyzers__ NuGet package](https://www.nuget.org/packages/Microsoft.CodeAnalysis.FxCopAnalyzers/) into your project.</span></span> <span data-ttu-id="e02ab-121">此封裝包含程式碼分析規則 [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) 和 [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md)，可協助您旗標可能會在可能預期的序數比較子中使用語言比較子的程式碼。</span><span class="sxs-lookup"><span data-stu-id="e02ab-121">This package includes the code analysis rules [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md), which help flag code that might inadvertently be using a linguistic comparer when an ordinal comparer was likely intended.</span></span>

<span data-ttu-id="e02ab-122">例如：</span><span class="sxs-lookup"><span data-stu-id="e02ab-122">For example:</span></span>

```cs
//
// Potentially incorrect code - answer might vary based on locale.
//
string s = GetString();
// Produces analyzer warning CA1307.
int idx = s.IndexOf(",");
Console.WriteLine(idx);

//
// Corrected code - matches the literal substring ",".
//
string s = GetString();
int idx = s.IndexOf(",", StringComparison.Ordinal);
Console.WriteLine(idx);

//
// Corrected code (alternative) - searches for the literal ',' character.
//
string s = GetString();
int idx = s.IndexOf(',');
Console.WriteLine(idx);
```

<span data-ttu-id="e02ab-123">同樣地，當具現化已排序的字串集合或排序現有的以字串為基礎的集合時，請指定明確的比較子。</span><span class="sxs-lookup"><span data-stu-id="e02ab-123">Similarly, when instantiating a sorted collection of strings or sorting an existing string-based collection, specify an explicit comparer.</span></span>

```cs
//
// Potentially incorrect code - behavior might vary based on locale.
//
SortedSet<string> mySet = new SortedSet<string>();
List<string> list = GetListOfStrings();
list.Sort();

//
// Corrected code - uses ordinal sorting; doesn't vary by locale.
//
SortedSet<string> mySet = new SortedSet<string>(StringComparer.Ordinal);
List<string> list = GetListOfStrings();
list.Sort(StringComparer.Ordinal);
```

<span data-ttu-id="e02ab-124">如需這些程式碼分析器規則的詳細資訊，包括何時可能適合在您自己的程式碼基底中隱藏這些規則，請參閱下列文章：</span><span class="sxs-lookup"><span data-stu-id="e02ab-124">For more information about these code analyzer rules, including when it might be appropriate to suppress these rules in your own code base, see the following articles:</span></span>

* [<span data-ttu-id="e02ab-125">CA1307:指定 StringComparison 以提升明確性</span><span class="sxs-lookup"><span data-stu-id="e02ab-125">CA1307: Specify StringComparison for clarity</span></span>](../../fundamentals/code-analysis/quality-rules/ca1307.md)
* [<span data-ttu-id="e02ab-126">CA1309:使用循序的 StringComparison</span><span class="sxs-lookup"><span data-stu-id="e02ab-126">CA1309: Use ordinal StringComparison</span></span>](../../fundamentals/code-analysis/quality-rules/ca1309.md)

### <a name="revert-back-to-nls-behaviors"></a><span data-ttu-id="e02ab-127">還原回 NLS 行為</span><span class="sxs-lookup"><span data-stu-id="e02ab-127">Revert back to NLS behaviors</span></span>

<span data-ttu-id="e02ab-128">若要在 Windows 上執行時，將 .NET 5 應用程式還原回較舊的 NLS 行為，請依照 [.Net 全球化和 ICU](../globalization-localization/globalization-icu.md)中的步驟執行。</span><span class="sxs-lookup"><span data-stu-id="e02ab-128">To revert .NET 5 applications back to older NLS behaviors when running on Windows, follow the steps in [.NET Globalization and ICU](../globalization-localization/globalization-icu.md).</span></span> <span data-ttu-id="e02ab-129">您必須在應用層級設定此整個應用程式的相容性參數。</span><span class="sxs-lookup"><span data-stu-id="e02ab-129">This application-wide compatibility switch must be set at the application level.</span></span> <span data-ttu-id="e02ab-130">個別程式庫無法加入宣告或退出此行為。</span><span class="sxs-lookup"><span data-stu-id="e02ab-130">Individual libraries cannot opt-in or opt-out of this behavior.</span></span>

> [!TIP]
> <span data-ttu-id="e02ab-131">強烈建議您啟用 [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) 和 [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) 程式碼分析規則，以協助改善程式碼的防護，並探索任何現有的潛在錯誤。</span><span class="sxs-lookup"><span data-stu-id="e02ab-131">We strongly recommend you enable the [CA1307](../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309](../../fundamentals/code-analysis/quality-rules/ca1309.md) code analysis rules to help improve code hygiene and discover any existing latent bugs.</span></span> <span data-ttu-id="e02ab-132">如需詳細資訊，請參閱 [啟用程式碼分析器](#enable-code-analyzers)。</span><span class="sxs-lookup"><span data-stu-id="e02ab-132">For more information, see [Enable code analyzers](#enable-code-analyzers).</span></span>

## <a name="affected-apis"></a><span data-ttu-id="e02ab-133">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="e02ab-133">Affected APIs</span></span>

<span data-ttu-id="e02ab-134">大部分的 .NET 應用程式都不會因為 .NET 5.0 中的變更而遇到任何未預期的行為。</span><span class="sxs-lookup"><span data-stu-id="e02ab-134">Most .NET applications won't encounter any unexpected behaviors due to the changes in .NET 5.0.</span></span> <span data-ttu-id="e02ab-135">不過，由於受影響的 Api 數目以及這些 Api 在更廣泛的 .NET 生態系統中的基礎，您應該瞭解 .NET 5.0 可能會引入不想要的行為，或公開應用程式中已經存在的潛在 bug。</span><span class="sxs-lookup"><span data-stu-id="e02ab-135">However, due to the number of affected APIs and how foundational these APIs are to the wider .NET ecosystem, you should be aware of the potential for .NET 5.0 to introduce unwanted behaviors or to expose latent bugs that already exist in your application.</span></span>

<span data-ttu-id="e02ab-136">受影響的 Api 包括：</span><span class="sxs-lookup"><span data-stu-id="e02ab-136">The affected APIs include:</span></span>

- <xref:System.String.Compare%2A?displayProperty=fullName>
- <xref:System.String.EndsWith%2A?displayProperty=fullName>
- <xref:System.String.IndexOf%2A?displayProperty=fullName>
- <xref:System.String.StartsWith%2A?displayProperty=fullName>
- <xref:System.String.ToLower%2A?displayProperty=fullName>
- <xref:System.String.ToLowerInvariant%2A?displayProperty=fullName>
- <xref:System.String.ToUpper%2A?displayProperty=fullName>
- <xref:System.String.ToUpperInvariant%2A?displayProperty=fullName>
- <span data-ttu-id="e02ab-137"><xref:System.Globalization.TextInfo?displayProperty=fullName> (大部分的成員) </span><span class="sxs-lookup"><span data-stu-id="e02ab-137"><xref:System.Globalization.TextInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="e02ab-138"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (大部分的成員) </span><span class="sxs-lookup"><span data-stu-id="e02ab-138"><xref:System.Globalization.CompareInfo?displayProperty=fullName> (most members)</span></span>
- <span data-ttu-id="e02ab-139"><xref:System.Array.Sort%2A?displayProperty=fullName> 排序字串陣列時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-139"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting arrays of strings)</span></span>
- <span data-ttu-id="e02ab-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> 當清單元素是字串時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-140"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="e02ab-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> 當索引鍵為字串時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-141"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="e02ab-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> 當索引鍵為字串時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-142"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="e02ab-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> 當集合包含字串時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-143"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

> [!NOTE]
> <span data-ttu-id="e02ab-144">這不是受影響 Api 的詳盡清單。</span><span class="sxs-lookup"><span data-stu-id="e02ab-144">This is not an exhaustive list of affected APIs.</span></span>

<span data-ttu-id="e02ab-145">上述所有 Api 預設會使用執行緒 [目前的文化](xref:System.Threading.Thread.CurrentCulture)特性進行 *語言* 字串搜尋和比較。</span><span class="sxs-lookup"><span data-stu-id="e02ab-145">All of the above APIs use *linguistic* string searching and comparison using the thread's [current culture](xref:System.Threading.Thread.CurrentCulture), by default.</span></span> <span data-ttu-id="e02ab-146">*語言* 和 *序數* 搜尋和比較之間的差異會在 [序數與語言搜尋和比較](#ordinal-vs-linguistic-search-and-comparison)中呼叫。</span><span class="sxs-lookup"><span data-stu-id="e02ab-146">The differences between *linguistic* and *ordinal* search and comparison are called out in the [Ordinal vs. linguistic search and comparison](#ordinal-vs-linguistic-search-and-comparison).</span></span>

<span data-ttu-id="e02ab-147">由於 ICU 會以不同于 NLS 的方式來執行語言字串比較，因此從舊版 .NET Core 或 .NET Framework 升級至 .NET 5.0 的 Windows 架構應用程式，以及呼叫其中一個受影響的 Api，可能會注意到 Api 開始出現不同的行為。</span><span class="sxs-lookup"><span data-stu-id="e02ab-147">Because ICU implements linguistic string comparisons differently from NLS, Windows-based applications that upgrade to .NET 5.0 from an earlier version of .NET Core or .NET Framework and that call one of the affected APIs may notice that the APIs begin exhibiting different behaviors.</span></span>

### <a name="exceptions"></a><span data-ttu-id="e02ab-148">例外狀況</span><span class="sxs-lookup"><span data-stu-id="e02ab-148">Exceptions</span></span>

* <span data-ttu-id="e02ab-149">如果 API 接受明確 `StringComparison` 或 `CultureInfo` 參數，該參數會覆寫 API 的預設行為。</span><span class="sxs-lookup"><span data-stu-id="e02ab-149">If an API accepts an explicit `StringComparison` or `CultureInfo` parameter, that parameter overrides the API's default behavior.</span></span>
* <span data-ttu-id="e02ab-150">`System.String` 第一個參數屬於 (類型的成員 `char` ， <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType> 除非呼叫端傳遞明確 `StringComparison` 的引數來指定或，否則) 使用序數搜尋 `CurrentCulture[IgnoreCase]` `InvariantCulture[IgnoreCase]` 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-150">`System.String` members where the first parameter is of type `char` (for example, <xref:System.String.IndexOf(System.Char)?displayProperty=nameWithType>) use ordinal searching, unless the caller passes an explicit `StringComparison` argument that specifies `CurrentCulture[IgnoreCase]` or `InvariantCulture[IgnoreCase]`.</span></span>

<span data-ttu-id="e02ab-151">如需每個 API 預設行為的詳細分析 <xref:System.String> ，請參閱 [預設搜尋和比較類型](#default-search-and-comparison-types) 一節。</span><span class="sxs-lookup"><span data-stu-id="e02ab-151">For a more detailed analysis of the default behavior of each <xref:System.String> API, see the [Default search and comparison types](#default-search-and-comparison-types) section.</span></span>

## <a name="ordinal-vs-linguistic-search-and-comparison"></a><span data-ttu-id="e02ab-152">序數與語言搜尋和比較</span><span class="sxs-lookup"><span data-stu-id="e02ab-152">Ordinal vs. linguistic search and comparison</span></span>

<span data-ttu-id="e02ab-153">*序數* (也稱為 *非語言* 的) 搜尋和比較分解將字串轉換成個別的 `char` 元素，並執行逐字元搜尋或比較。</span><span class="sxs-lookup"><span data-stu-id="e02ab-153">*Ordinal* (also known as *non-linguistic*) search and comparison decomposes a string into its individual `char` elements and performs a char-by-char search or comparison.</span></span> <span data-ttu-id="e02ab-154">例如，在比較子 `"dog"` 下，字串和 `"dog"` 比較為 *相等* `Ordinal` ，因為兩個字串包含的字元順序完全相同。</span><span class="sxs-lookup"><span data-stu-id="e02ab-154">For example, the strings `"dog"` and `"dog"` compare as *equal* under an `Ordinal` comparer, since the two strings consist of the exact same sequence of chars.</span></span> <span data-ttu-id="e02ab-155">但是， `"dog"` 和 `"Dog"` 比較 *不等於* 比較子 `Ordinal` ，因為它們不是由相同的字元序列所組成。</span><span class="sxs-lookup"><span data-stu-id="e02ab-155">However, `"dog"` and `"Dog"` compare as *not equal* under an `Ordinal` comparer, because they don't consist of the exact same sequence of chars.</span></span> <span data-ttu-id="e02ab-156">也就是說，大寫的程式碼 `'D'` 點 `U+0044` 會在小寫 `'d'` 的程式碼點之前發生 `U+0064` ，因此會 `"dog"` 先排序 `"Dog"` 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-156">That is, uppercase `'D'`'s code point `U+0044` occurs before lowercase `'d'`'s code point `U+0064`, resulting in `"dog"` sorting before `"Dog"`.</span></span>

<span data-ttu-id="e02ab-157">`OrdinalIgnoreCase`比較子的運作方式仍是逐字元，但是在執行作業時，它會消除大小寫差異。</span><span class="sxs-lookup"><span data-stu-id="e02ab-157">An `OrdinalIgnoreCase` comparer still operates on a char-by-char basis, but it eliminates case differences while performing the operation.</span></span> <span data-ttu-id="e02ab-158">在比較子下 `OrdinalIgnoreCase` ，char 組 `'d'` 和 `'D'` 比較為 *相等*，與 char 配對 `'á'` 和 `'Á'` 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-158">Under an `OrdinalIgnoreCase` comparer, the char pairs `'d'` and `'D'` compare as *equal*, as do the char pairs `'á'` and `'Á'`.</span></span> <span data-ttu-id="e02ab-159">但是非重音字元 `'a'` 會比較為 *不等於* 重音字元 `'á'` 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-159">But the unaccented char `'a'` compares as *not equal* to the accented char `'á'`.</span></span>

<span data-ttu-id="e02ab-160">下表提供一些範例：</span><span class="sxs-lookup"><span data-stu-id="e02ab-160">Some examples of this are provided in the following table:</span></span>

| <span data-ttu-id="e02ab-161">字串 1</span><span class="sxs-lookup"><span data-stu-id="e02ab-161">String 1</span></span> | <span data-ttu-id="e02ab-162">字串2</span><span class="sxs-lookup"><span data-stu-id="e02ab-162">String 2</span></span> | <span data-ttu-id="e02ab-163">`Ordinal` 比較</span><span class="sxs-lookup"><span data-stu-id="e02ab-163">`Ordinal` comparison</span></span> | <span data-ttu-id="e02ab-164">`OrdinalIgnoreCase` 比較</span><span class="sxs-lookup"><span data-stu-id="e02ab-164">`OrdinalIgnoreCase` comparison</span></span> |
|---|---|---|---|
| `"dog"` | `"dog"` | <span data-ttu-id="e02ab-165">equal</span><span class="sxs-lookup"><span data-stu-id="e02ab-165">equal</span></span> | <span data-ttu-id="e02ab-166">equal</span><span class="sxs-lookup"><span data-stu-id="e02ab-166">equal</span></span> |
| `"dog"` | `"Dog"` | <span data-ttu-id="e02ab-167">不等於</span><span class="sxs-lookup"><span data-stu-id="e02ab-167">not equal</span></span> | <span data-ttu-id="e02ab-168">equal</span><span class="sxs-lookup"><span data-stu-id="e02ab-168">equal</span></span> |
| `"resume"` | `"Resume"` | <span data-ttu-id="e02ab-169">不等於</span><span class="sxs-lookup"><span data-stu-id="e02ab-169">not equal</span></span> | <span data-ttu-id="e02ab-170">equal</span><span class="sxs-lookup"><span data-stu-id="e02ab-170">equal</span></span> |
| `"resume"` | `"résumé"` | <span data-ttu-id="e02ab-171">不等於</span><span class="sxs-lookup"><span data-stu-id="e02ab-171">not equal</span></span> | <span data-ttu-id="e02ab-172">不等於</span><span class="sxs-lookup"><span data-stu-id="e02ab-172">not equal</span></span> |

<span data-ttu-id="e02ab-173">Unicode 也可讓字串擁有數個不同的記憶體內部標記法。</span><span class="sxs-lookup"><span data-stu-id="e02ab-173">Unicode also allows strings to have several different in-memory representations.</span></span> <span data-ttu-id="e02ab-174">例如，您可以使用兩種可能的方式來表示電子銳 (日) ：</span><span class="sxs-lookup"><span data-stu-id="e02ab-174">For example, an e-acute (é) can be represented in two possible ways:</span></span>

* <span data-ttu-id="e02ab-175">單一常值 `'é'` 字元 (也會寫入為 `'\u00E9'`) 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-175">A single literal `'é'` character (also written as `'\u00E9'`).</span></span>
* <span data-ttu-id="e02ab-176">常值的非重音 `'e'` 字元，後面接著結合輔色修飾詞字元 `'\u0301'` 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-176">A literal unaccented `'e'` character, followed by a combining accent modifier character `'\u0301'`.</span></span>

<span data-ttu-id="e02ab-177">這表示，在顯示時，下列 _四個_ 字串都會 `"résumé"` 出現，即使它們的組成片段不同也一樣。</span><span class="sxs-lookup"><span data-stu-id="e02ab-177">This means that the following _four_ strings all result in `"résumé"` when displayed, even though their constituent pieces are different.</span></span> <span data-ttu-id="e02ab-178">字串會使用常值 `'é'` 字元或常值非重音 `'e'` 字元以及合併輔色修飾詞的組合 `'\u0301'` 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-178">The strings use a combination of literal `'é'` characters or literal unaccented `'e'` characters plus the combining accent modifier `'\u0301'`.</span></span>

* `"r\u00E9sum\u00E9"`
* `"r\u00E9sume\u0301"`
* `"re\u0301sum\u00E9"`
* `"re\u0301sume\u0301"`

<span data-ttu-id="e02ab-179">在序數比較子下，這些字串的比較都不會相等。</span><span class="sxs-lookup"><span data-stu-id="e02ab-179">Under an ordinal comparer, none of these strings compare as equal to each other.</span></span> <span data-ttu-id="e02ab-180">這是因為它們都包含不同的基礎 char 序列，雖然它們會在螢幕上呈現時，但全都看起來相同。</span><span class="sxs-lookup"><span data-stu-id="e02ab-180">This is because they all contain different underlying char sequences, even though when they're rendered to the screen, they all look the same.</span></span>

<span data-ttu-id="e02ab-181">執行作業時 `string.IndexOf(..., StringComparison.Ordinal)` ，執行時間會尋找完全相符的子字串。</span><span class="sxs-lookup"><span data-stu-id="e02ab-181">When performing a `string.IndexOf(..., StringComparison.Ordinal)` operation, the runtime looks for an exact substring match.</span></span> <span data-ttu-id="e02ab-182">結果如下所示。</span><span class="sxs-lookup"><span data-stu-id="e02ab-182">The results are as follows.</span></span>

```cs
Console.WriteLine("resume".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("e", StringComparison.Ordinal)); // prints '1'
Console.WriteLine("resume".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '-1'
Console.WriteLine("r\u00E9sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '5'
Console.WriteLine("re\u0301sum\u00E9".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
Console.WriteLine("re\u0301sume\u0301".IndexOf("E", StringComparison.OrdinalIgnoreCase)); // prints '1'
```

<span data-ttu-id="e02ab-183">序數搜尋和比較常式絕不會受到目前線程的文化特性設定影響。</span><span class="sxs-lookup"><span data-stu-id="e02ab-183">Ordinal search and comparison routines are never affected by the current thread's culture setting.</span></span>

<span data-ttu-id="e02ab-184">*語言* 搜尋和比較常式會將字串分解成定 *序元素* ，並對這些元素執行搜尋或比較。</span><span class="sxs-lookup"><span data-stu-id="e02ab-184">*Linguistic* search and comparison routines decompose a string into *collation elements* and perform searches or comparisons on these elements.</span></span> <span data-ttu-id="e02ab-185">字串字元與其組成定序專案之間不一定要有1:1 對應。</span><span class="sxs-lookup"><span data-stu-id="e02ab-185">There's not necessarily a 1:1 mapping between a string's characters and its constituent collation elements.</span></span> <span data-ttu-id="e02ab-186">例如，長度為2的字串只能包含單一定序元素。</span><span class="sxs-lookup"><span data-stu-id="e02ab-186">For example, a string of length 2 may consist of only a single collation element.</span></span> <span data-ttu-id="e02ab-187">當兩個字串以語言感知的方式進行比較時，比較子會檢查兩個字串的定序專案是否具有相同的語義意義，即使字串的常值字元不同也是一樣。</span><span class="sxs-lookup"><span data-stu-id="e02ab-187">When two strings are compared in a linguistic-aware fashion, the comparer checks whether the two strings' collation elements have the same semantic meaning, even if the string's literal characters are different.</span></span>

<span data-ttu-id="e02ab-188">請再次考慮字串 `"résumé"` 和其四種不同的標記法。</span><span class="sxs-lookup"><span data-stu-id="e02ab-188">Consider again the string `"résumé"` and its four different representations.</span></span> <span data-ttu-id="e02ab-189">下表顯示每個標記法細分為其定序元素。</span><span class="sxs-lookup"><span data-stu-id="e02ab-189">The following table shows each representation broken down into its collation elements.</span></span>

| <span data-ttu-id="e02ab-190">String</span><span class="sxs-lookup"><span data-stu-id="e02ab-190">String</span></span> | <span data-ttu-id="e02ab-191">作為定序元素</span><span class="sxs-lookup"><span data-stu-id="e02ab-191">As collation elements</span></span> |
|---|---|
| `"r\u00E9sum\u00E9"` | `"r" + "\u00E9" + "s" + "u" + "m" + "\u00E9"` |
| `"r\u00E9sume\u0301"` | `"r" + "\u00E9" + "s" + "u" + "m" + "e\u0301"` |
| `"re\u0301sum\u00E9"` | `"r" + "e\u0301" + "s" + "u" + "m" + "\u00E9"` |
| `"re\u0301sume\u0301"` | `"r" + "e\u00E9" + "s" + "u" + "m" + "e\u0301"` |

<span data-ttu-id="e02ab-192">定序專案相當於讀取器想要做為單一字元或字元叢集的內容。</span><span class="sxs-lookup"><span data-stu-id="e02ab-192">A collation element corresponds loosely to what readers would think of as a single character or cluster of characters.</span></span> <span data-ttu-id="e02ab-193">它在概念上類似于 [語素簇](character-encoding-introduction.md#grapheme-clusters) 叢集，但包含較大的傘。</span><span class="sxs-lookup"><span data-stu-id="e02ab-193">It's conceptually similar to a [grapheme cluster](character-encoding-introduction.md#grapheme-clusters) but encompasses a somewhat larger umbrella.</span></span>

<span data-ttu-id="e02ab-194">在語言比較子下，不需要完全相符。</span><span class="sxs-lookup"><span data-stu-id="e02ab-194">Under a linguistic comparer, exact matches aren't necessary.</span></span> <span data-ttu-id="e02ab-195">定序專案會根據其語義意義而比較。</span><span class="sxs-lookup"><span data-stu-id="e02ab-195">Collation elements are instead compared based on their semantic meaning.</span></span> <span data-ttu-id="e02ab-196">例如，語言比較子會 tsreat 子字串 `"\u00E9"` 並 `"e\u0301"` 相等，因為它們都是以語義表示 "a 小寫 e with a 銳角修飾詞</span><span class="sxs-lookup"><span data-stu-id="e02ab-196">For example, a linguistic comparer tsreat the substrings `"\u00E9"` and `"e\u0301"` as equal since they both semantically mean "a lowercase e with an acute accent modifier."</span></span> <span data-ttu-id="e02ab-197">這可讓 `IndexOf` 方法 `"e\u0301"` 比對包含語義相等子字串的大型字串中的子字串 `"\u00E9"` ，如下列程式碼範例所示。</span><span class="sxs-lookup"><span data-stu-id="e02ab-197">This allows the `IndexOf` method to match the substring `"e\u0301"` within a larger string that contains the semantically equivalent substring `"\u00E9"`, as shown in the following code sample.</span></span>

```cs
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e")); // prints '-1' (not found)
Console.WriteLine("r\u00E9sum\u00E9".IndexOf("e\u00E9")); // prints '1'
Console.WriteLine("\u00E9".IndexOf("e\u00E9")); // prints '0'
```

<span data-ttu-id="e02ab-198">如此一來，如果使用語言比較，則兩個不同長度的字串可能會比較相等。</span><span class="sxs-lookup"><span data-stu-id="e02ab-198">As a consequence of this, two strings of different lengths may compare as equal if a linguistic comparison is used.</span></span> <span data-ttu-id="e02ab-199">呼叫端應該小心處理在這類案例中處理字串長度的特殊案例邏輯。</span><span class="sxs-lookup"><span data-stu-id="e02ab-199">Callers should take care not to special-case logic that deals with string length in such scenarios.</span></span>

<span data-ttu-id="e02ab-200">*文化特性感知* 搜尋和比較常式是一種特殊形式的語言搜尋和比較常式。</span><span class="sxs-lookup"><span data-stu-id="e02ab-200">*Culture-aware* search and comparison routines are a special form of linguistic search and comparison routines.</span></span> <span data-ttu-id="e02ab-201">在可感知文化特性的比較子中，定序專案的概念會延伸，以包含指定文化特性的特定資訊。</span><span class="sxs-lookup"><span data-stu-id="e02ab-201">Under a culture-aware comparer, the concept of a collation element is extended to include information specific to the specified culture.</span></span>

<span data-ttu-id="e02ab-202">例如， [在匈牙利文的字母中](https://en.wikipedia.org/wiki/Hungarian_alphabet)，當兩個字元 \<dz\> 再次出現時，它們會被視為與或不同的唯一字母 \<d\> \<z\> 。</span><span class="sxs-lookup"><span data-stu-id="e02ab-202">For example, [in the Hungarian alphabet](https://en.wikipedia.org/wiki/Hungarian_alphabet), when the two characters \<dz\> appear back-to-back, they are considered their own unique letter distinct from either \<d\> or \<z\>.</span></span> <span data-ttu-id="e02ab-203">這表示 \<dz\> 在字串中看到時，匈牙利文文化特性感知比較子會將它視為單一定序元素。</span><span class="sxs-lookup"><span data-stu-id="e02ab-203">This means that when \<dz\> is seen in a string, a Hungarian culture-aware comparer treats it as a single collation element.</span></span>

| <span data-ttu-id="e02ab-204">String</span><span class="sxs-lookup"><span data-stu-id="e02ab-204">String</span></span> | <span data-ttu-id="e02ab-205">作為定序元素</span><span class="sxs-lookup"><span data-stu-id="e02ab-205">As collation elements</span></span> | <span data-ttu-id="e02ab-206">備註</span><span class="sxs-lookup"><span data-stu-id="e02ab-206">Remarks</span></span> |
|---|---|---|
| `"endz"` | `"e" + "n" + "d" + "z"` | <span data-ttu-id="e02ab-207">使用標準語言比較子的 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-207">(using a standard linguistic comparer)</span></span> |
| `"endz"` | `"e" + "n" + "dz"` | <span data-ttu-id="e02ab-208"> (使用匈牙利文化特性感知比較子) </span><span class="sxs-lookup"><span data-stu-id="e02ab-208">(using a Hungarian culture-aware comparer)</span></span> |

<span data-ttu-id="e02ab-209">使用匈牙利文化特性感知比較子時，這表示字串不 `"endz"` *會* 以子字串結尾 `"z"` ，因為 < \dz \> 和 < \z \> 視為具有不同語義意義的定序元素。</span><span class="sxs-lookup"><span data-stu-id="e02ab-209">When using a Hungarian culture-aware comparer, this means that the string `"endz"` *does not* end with the substring `"z"`, as <\dz\> and <\z\> are considered collation elements with different semantic meaning.</span></span>

```cs
// Set thread culture to Hungarian
CultureInfo.CurrentCulture = CultureInfo.GetCultureInfo("hu-HU");
Console.WriteLine("endz".EndsWith("z")); // Prints 'False'

// Set thread culture to invariant culture
CultureInfo.CurrentCulture = CultureInfo.InvariantCulture;
Console.WriteLine("endz".EndsWith("z")); // Prints 'True'
```

> [!NOTE]
>
> - <span data-ttu-id="e02ab-210">行為：語言和文化特性感知的比較子可能會在一段時間後進行行為調整。</span><span class="sxs-lookup"><span data-stu-id="e02ab-210">Behavior: Linguistic and culture-aware comparers can undergo behavioral adjustments from time to time.</span></span> <span data-ttu-id="e02ab-211">ICU 和舊版 Windows NLS 設備都會更新，以說明世界語言的變化。</span><span class="sxs-lookup"><span data-stu-id="e02ab-211">Both ICU and the older Windows NLS facility are updated to account for how world languages change.</span></span> <span data-ttu-id="e02ab-212">如需詳細資訊，請參閱 [ (文化特性) 資料](/archive/blogs/shawnste/locale-culture-data-churn)變換的 Blog 文章地區設定。</span><span class="sxs-lookup"><span data-stu-id="e02ab-212">For more information, see the blog post [Locale (culture) data churn](/archive/blogs/shawnste/locale-culture-data-churn).</span></span> <span data-ttu-id="e02ab-213">*序數* 比較子的行為永遠不會變更，因為它會執行精確的位搜尋和比較。</span><span class="sxs-lookup"><span data-stu-id="e02ab-213">The *Ordinal* comparer's behavior will never change since it performs exact bitwise searching and comparison.</span></span> <span data-ttu-id="e02ab-214">不過， *OrdinalIgnoreCase* 比較子的行為可能會隨著 Unicode 的成長而改變，以包含更多的字元集並修正現有大小寫資料中的遺漏。</span><span class="sxs-lookup"><span data-stu-id="e02ab-214">However, the *OrdinalIgnoreCase* comparer's behavior may change as Unicode grows to encompass more character sets and corrects omissions in existing casing data.</span></span>
> - <span data-ttu-id="e02ab-215">使用方式：比較子 `StringComparison.InvariantCulture` 和 `StringComparison.InvariantCultureIgnoreCase` 是不感知文化特性的語言比較子。</span><span class="sxs-lookup"><span data-stu-id="e02ab-215">Usage: The comparers `StringComparison.InvariantCulture` and `StringComparison.InvariantCultureIgnoreCase` are linguistic comparers that are not culture-aware.</span></span> <span data-ttu-id="e02ab-216">也就是說，這些比較子可瞭解概念，像是日有多個可能基礎標記法的重音字元，而且所有這類標記法都應該視為相等。</span><span class="sxs-lookup"><span data-stu-id="e02ab-216">That is, these comparers understand concepts such as the accented character é having multiple possible underlying representations, and that all such representations should be treated equal.</span></span> <span data-ttu-id="e02ab-217">但是，非文化特性感知的語言比較子不會包含 \<dz\> 與或不同的特殊處理 \<d\> \<z\> ，如上所示。</span><span class="sxs-lookup"><span data-stu-id="e02ab-217">But non-culture-aware linguistic comparers won't contain special handling for \<dz\> as distinct from \<d\> or \<z\>, as shown above.</span></span> <span data-ttu-id="e02ab-218">它們也不會有像德文 Eszett (ß) 這類特殊字元。</span><span class="sxs-lookup"><span data-stu-id="e02ab-218">They also won't special-case characters like the German Eszett (ß).</span></span>

<span data-ttu-id="e02ab-219">.NET 也提供不 *變的全球化模式*。</span><span class="sxs-lookup"><span data-stu-id="e02ab-219">.NET also offers the *invariant globalization mode*.</span></span> <span data-ttu-id="e02ab-220">這個加入宣告模式會停用處理語言搜尋和比較常式的程式碼路徑。</span><span class="sxs-lookup"><span data-stu-id="e02ab-220">This opt-in mode disables code paths that deal with linguistic search and comparison routines.</span></span> <span data-ttu-id="e02ab-221">在此模式中，所有作業都會使用 *序數* 或 *OrdinalIgnoreCase* 行為，不論呼叫端提供的是什麼 `CultureInfo` 或 `StringComparison` 引數。</span><span class="sxs-lookup"><span data-stu-id="e02ab-221">In this mode, all operations use *Ordinal* or *OrdinalIgnoreCase* behaviors, regardless of what `CultureInfo` or `StringComparison` argument the caller provides.</span></span> <span data-ttu-id="e02ab-222">如需詳細資訊，請參閱全球化和[.Net Core 全球化不變模式](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md)[的執行時間設定選項](../../core/run-time-config/globalization.md)。</span><span class="sxs-lookup"><span data-stu-id="e02ab-222">For more information, see [Run-time configuration options for globalization](../../core/run-time-config/globalization.md) and [.NET Core Globalization Invariant Mode](https://github.com/dotnet/runtime/blob/master/docs/design/features/globalization-invariant-mode.md).</span></span>

<span data-ttu-id="e02ab-223">如需詳細資訊，請參閱 [在 .net 中比較字串的最佳做法](best-practices-strings.md)。</span><span class="sxs-lookup"><span data-stu-id="e02ab-223">For more information, see [Best practices for comparing strings in .NET](best-practices-strings.md).</span></span>

## <a name="security-implications"></a><span data-ttu-id="e02ab-224">安全性影響</span><span class="sxs-lookup"><span data-stu-id="e02ab-224">Security implications</span></span>

<span data-ttu-id="e02ab-225">如果您的應用程式使用受影響的 API 進行篩選，我們建議您啟用 CA1307 和 CA1309 程式碼分析規則，以協助找出可能不慎使用語言搜尋而非序數搜尋的位置。</span><span class="sxs-lookup"><span data-stu-id="e02ab-225">If your app uses an affected API for filtering, we recommend enabling the CA1307 and CA1309 code analysis rules to help locate places where a linguistic search may have inadvertently been used instead of an ordinal search.</span></span> <span data-ttu-id="e02ab-226">如下所示的程式碼模式可能會受到安全性攻擊。</span><span class="sxs-lookup"><span data-stu-id="e02ab-226">Code patterns like the following may be susceptible to security exploits.</span></span>

```cs
//
// THIS SAMPLE CODE IS INCORRECT.
// DO NOT USE IT IN PRODUCTION.
//
public bool ContainsHtmlSensitiveCharacters(string input)
{
    if (input.IndexOf("<") >= 0) { return true; }
    if (input.IndexOf("&") >= 0) { return true; }
    return false;
}
```

<span data-ttu-id="e02ab-227">因為此 `string.IndexOf(string)` 方法預設會使用語言搜尋，所以字串可能會包含常值 `'<'` 或 `'&'` 字元，而且常式會傳回 `string.IndexOf(string)` `-1` ，表示找不到搜尋子字串。</span><span class="sxs-lookup"><span data-stu-id="e02ab-227">Because the `string.IndexOf(string)` method uses a linguistic search by default, it's possible for a string to contain a literal `'<'` or `'&'` character and for the `string.IndexOf(string)` routine to return `-1`, indicating that the search substring was not found.</span></span> <span data-ttu-id="e02ab-228">程式碼分析規則 CA1307 和 CA1309 旗標，例如呼叫網站，並向開發人員發出潛在問題。</span><span class="sxs-lookup"><span data-stu-id="e02ab-228">Code analysis rules CA1307 and CA1309 flag such call sites and alert the developer that there's a potential problem.</span></span>

## <a name="default-search-and-comparison-types"></a><span data-ttu-id="e02ab-229">預設搜尋和比較類型</span><span class="sxs-lookup"><span data-stu-id="e02ab-229">Default search and comparison types</span></span>

<span data-ttu-id="e02ab-230">下表列出各種字串和類似字串的 Api 之預設搜尋和比較類型。</span><span class="sxs-lookup"><span data-stu-id="e02ab-230">The following table lists the default search and comparison types for various string and string-like APIs.</span></span> <span data-ttu-id="e02ab-231">如果呼叫端提供明確 `CultureInfo` 或 `StringComparison` 參數，則會對任何預設值接受該參數。</span><span class="sxs-lookup"><span data-stu-id="e02ab-231">If the caller provides an explicit `CultureInfo` or `StringComparison` parameter, that parameter will be honored over any default.</span></span>

| <span data-ttu-id="e02ab-232">API</span><span class="sxs-lookup"><span data-stu-id="e02ab-232">API</span></span> | <span data-ttu-id="e02ab-233">預設行為</span><span class="sxs-lookup"><span data-stu-id="e02ab-233">Default behavior</span></span> | <span data-ttu-id="e02ab-234">備註</span><span class="sxs-lookup"><span data-stu-id="e02ab-234">Remarks</span></span> |
|---|---|---|
| `string.Compare` | <span data-ttu-id="e02ab-235">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-235">CurrentCulture</span></span> | |
| `string.CompareTo` | <span data-ttu-id="e02ab-236">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-236">CurrentCulture</span></span> | |
| `string.Contains` | <span data-ttu-id="e02ab-237">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-237">Ordinal</span></span> | |
| `string.EndsWith` | <span data-ttu-id="e02ab-238">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-238">Ordinal</span></span> | <span data-ttu-id="e02ab-239">當第一個參數為) 時 (`char`</span><span class="sxs-lookup"><span data-stu-id="e02ab-239">(when the first parameter is a `char`)</span></span> |
| `string.EndsWith` | <span data-ttu-id="e02ab-240">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-240">CurrentCulture</span></span> | <span data-ttu-id="e02ab-241">當第一個參數為) 時 (`string`</span><span class="sxs-lookup"><span data-stu-id="e02ab-241">(when the first parameter is a `string`)</span></span> |
| `string.Equals` | <span data-ttu-id="e02ab-242">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-242">Ordinal</span></span> | |
| `string.GetHashCode` | <span data-ttu-id="e02ab-243">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-243">Ordinal</span></span> | |
| `string.IndexOf` | <span data-ttu-id="e02ab-244">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-244">Ordinal</span></span> | <span data-ttu-id="e02ab-245">當第一個參數為) 時 (`char`</span><span class="sxs-lookup"><span data-stu-id="e02ab-245">(when the first parameter is a `char`)</span></span> |
| `string.IndexOf` | <span data-ttu-id="e02ab-246">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-246">CurrentCulture</span></span> | <span data-ttu-id="e02ab-247">當第一個參數為) 時 (`string`</span><span class="sxs-lookup"><span data-stu-id="e02ab-247">(when the first parameter is a `string`)</span></span> |
| `string.IndexOfAny` | <span data-ttu-id="e02ab-248">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-248">Ordinal</span></span> | |
| `string.LastIndexOf` | <span data-ttu-id="e02ab-249">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-249">Ordinal</span></span> | <span data-ttu-id="e02ab-250">當第一個參數為) 時 (`char`</span><span class="sxs-lookup"><span data-stu-id="e02ab-250">(when the first parameter is a `char`)</span></span> |
| `string.LastIndexOf` | <span data-ttu-id="e02ab-251">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-251">CurrentCulture</span></span> | <span data-ttu-id="e02ab-252">當第一個參數為) 時 (`string`</span><span class="sxs-lookup"><span data-stu-id="e02ab-252">(when the first parameter is a `string`)</span></span> |
| `string.LastIndexOfAny` | <span data-ttu-id="e02ab-253">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-253">Ordinal</span></span> | |
| `string.Replace` | <span data-ttu-id="e02ab-254">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-254">Ordinal</span></span> | |
| `string.Split` | <span data-ttu-id="e02ab-255">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-255">Ordinal</span></span> | |
| `string.StartsWith` | <span data-ttu-id="e02ab-256">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-256">Ordinal</span></span> | <span data-ttu-id="e02ab-257">當第一個參數為) 時 (`char`</span><span class="sxs-lookup"><span data-stu-id="e02ab-257">(when the first parameter is a `char`)</span></span> |
| `string.StartsWith` | <span data-ttu-id="e02ab-258">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-258">CurrentCulture</span></span> | <span data-ttu-id="e02ab-259">當第一個參數為) 時 (`string`</span><span class="sxs-lookup"><span data-stu-id="e02ab-259">(when the first parameter is a `string`)</span></span> |
| `string.ToLower` | <span data-ttu-id="e02ab-260">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-260">CurrentCulture</span></span> | |
| `string.ToLowerInvariant` | <span data-ttu-id="e02ab-261">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-261">InvariantCulture</span></span> | |
| `string.ToUpper` | <span data-ttu-id="e02ab-262">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-262">CurrentCulture</span></span> | |
| `string.ToUpperInvariant` | <span data-ttu-id="e02ab-263">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-263">InvariantCulture</span></span> | |
| `string.Trim` | <span data-ttu-id="e02ab-264">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-264">Ordinal</span></span> | |
| `string.TrimEnd` | <span data-ttu-id="e02ab-265">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-265">Ordinal</span></span> | |
| `string.TrimStart` | <span data-ttu-id="e02ab-266">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-266">Ordinal</span></span> | |
| `string == string` | <span data-ttu-id="e02ab-267">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-267">Ordinal</span></span> | |
| `string != string` | <span data-ttu-id="e02ab-268">序數</span><span class="sxs-lookup"><span data-stu-id="e02ab-268">Ordinal</span></span> | |

<span data-ttu-id="e02ab-269">與 `string` api 不同的 `MemoryExtensions` 是，所有 api 預設會執行 *序數* 搜尋和比較，但有下列例外狀況。</span><span class="sxs-lookup"><span data-stu-id="e02ab-269">Unlike `string` APIs, all `MemoryExtensions` APIs perform *Ordinal* searches and comparisons by default, with the following exceptions.</span></span>

| <span data-ttu-id="e02ab-270">API</span><span class="sxs-lookup"><span data-stu-id="e02ab-270">API</span></span> | <span data-ttu-id="e02ab-271">預設行為</span><span class="sxs-lookup"><span data-stu-id="e02ab-271">Default behavior</span></span> | <span data-ttu-id="e02ab-272">備註</span><span class="sxs-lookup"><span data-stu-id="e02ab-272">Remarks</span></span> |
|---|---|---|
| `MemoryExtensions.ToLower` | <span data-ttu-id="e02ab-273">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-273">CurrentCulture</span></span> | <span data-ttu-id="e02ab-274">傳遞 null `CultureInfo` 引數時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-274">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToLowerInvariant` | <span data-ttu-id="e02ab-275">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-275">InvariantCulture</span></span> | |
| `MemoryExtensions.ToUpper` | <span data-ttu-id="e02ab-276">CurrentCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-276">CurrentCulture</span></span> | <span data-ttu-id="e02ab-277">傳遞 null `CultureInfo` 引數時 () </span><span class="sxs-lookup"><span data-stu-id="e02ab-277">(when passed a null `CultureInfo` argument)</span></span> |
| `MemoryExtensions.ToUpperInvariant` | <span data-ttu-id="e02ab-278">InvariantCulture</span><span class="sxs-lookup"><span data-stu-id="e02ab-278">InvariantCulture</span></span> | |

<span data-ttu-id="e02ab-279">結果是，將程式碼轉換成取用的程式碼時 `string` `ReadOnlySpan<char>` ，可能會不慎引進行為變更。</span><span class="sxs-lookup"><span data-stu-id="e02ab-279">A consequence is that when converting code from consuming `string` to consuming `ReadOnlySpan<char>`, behavioral changes may be introduced inadvertently.</span></span> <span data-ttu-id="e02ab-280">範例如下所示。</span><span class="sxs-lookup"><span data-stu-id="e02ab-280">An example of this follows.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello")) { /* do something */ } // this is a CULTURE-AWARE (linguistic) comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello")) { /* do something */ } // this is an ORDINAL (non-linguistic) comparison
```

<span data-ttu-id="e02ab-281">建議的解決方法是將明確 `StringComparison` 參數傳遞至這些 api。</span><span class="sxs-lookup"><span data-stu-id="e02ab-281">The recommended way to address this is to pass an explicit `StringComparison` parameter to these APIs.</span></span> <span data-ttu-id="e02ab-282">程式碼分析規則 CA1307 和 CA1309 可以提供協助。</span><span class="sxs-lookup"><span data-stu-id="e02ab-282">The code analysis rules CA1307 and CA1309 can assist with this.</span></span>

```cs
string str = GetString();
if (str.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison

ReadOnlySpan<char> span = s.AsSpan();
if (span.StartsWith("Hello", StringComparison.Ordinal)) { /* do something */ } // ordinal comparison
```

## <a name="see-also"></a><span data-ttu-id="e02ab-283">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e02ab-283">See also</span></span>

- [<span data-ttu-id="e02ab-284">全球化重大變更</span><span class="sxs-lookup"><span data-stu-id="e02ab-284">Globalization breaking changes</span></span>](../../core/compatibility/globalization.md)
- [<span data-ttu-id="e02ab-285">在 .NET 中比較字串的最佳作法</span><span class="sxs-lookup"><span data-stu-id="e02ab-285">Best practices for comparing strings in .NET</span></span>](best-practices-strings.md)
- [<span data-ttu-id="e02ab-286">如何：在 C# 比較字串</span><span class="sxs-lookup"><span data-stu-id="e02ab-286">How to compare strings in C#</span></span>](../../csharp/how-to/compare-strings.md)
- [<span data-ttu-id="e02ab-287">.NET 全球化和 ICU</span><span class="sxs-lookup"><span data-stu-id="e02ab-287">.NET globalization and ICU</span></span>](../globalization-localization/globalization-icu.md)
- [<span data-ttu-id="e02ab-288">序數與區分文化特性的字串作業</span><span class="sxs-lookup"><span data-stu-id="e02ab-288">Ordinal vs. culture-sensitive string operations</span></span>](/dotnet/api/system.string#ordinal-vs-culture-sensitive-operations)
- [<span data-ttu-id="e02ab-289">.NET source 程式碼分析總覽</span><span class="sxs-lookup"><span data-stu-id="e02ab-289">Overview of .NET source code analysis</span></span>](../../fundamentals/code-analysis/overview.md)
