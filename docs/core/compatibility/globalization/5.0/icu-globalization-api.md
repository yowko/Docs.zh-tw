---
title: 重大變更：全球化 Api 在 Windows 上使用 ICU 程式庫
description: 瞭解 .NET 5.0 中的全球化重大變更，其中 ICU 程式庫是用於全球化功能，而不是 NLS。
ms.date: 05/19/2020
ms.openlocfilehash: efc20e21969ea4a83c9122e40b262e1dc38e6770
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760795"
---
# <a name="globalization-apis-use-icu-libraries-on-windows"></a><span data-ttu-id="84adc-103">全球化 Api 在 Windows 上使用 ICU 程式庫</span><span class="sxs-lookup"><span data-stu-id="84adc-103">Globalization APIs use ICU libraries on Windows</span></span>

<span data-ttu-id="84adc-104">.NET 5.0 和更新版本會在 Windows 10 2019 年5月更新或更新版本上執行時，使用 [Unicode (ICU) ](http://site.icu-project.org/home) 程式庫的全球化功能。</span><span class="sxs-lookup"><span data-stu-id="84adc-104">.NET 5.0 and later versions use [International Components for Unicode (ICU)](http://site.icu-project.org/home) libraries for globalization functionality when running on Windows 10 May 2019 Update or later.</span></span>

## <a name="change-description"></a><span data-ttu-id="84adc-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="84adc-105">Change description</span></span>

<span data-ttu-id="84adc-106">在 .NET Core 1.0-3.1 和 .NET Framework 4 和更新版本中，.NET 程式庫使用 [國家語言支援 (NLS) ](/windows/win32/intl/national-language-support) api，在 Windows 上提供全球化功能。</span><span class="sxs-lookup"><span data-stu-id="84adc-106">In .NET Core 1.0 - 3.1 and .NET Framework 4 and later, .NET libraries use [National Language Support (NLS)](/windows/win32/intl/national-language-support) APIs for globalization functionality on Windows.</span></span> <span data-ttu-id="84adc-107">例如，NLS 函數是用來比較字串、取得文化特性資訊，以及在適當的文化特性中執行字串大小寫。</span><span class="sxs-lookup"><span data-stu-id="84adc-107">For example, NLS functions were used to compare strings, get culture information, and perform string casing in the appropriate culture.</span></span>

<span data-ttu-id="84adc-108">從 .NET 5.0 開始，如果應用程式在 Windows 10 2019 年5月更新或更新版本上執行，則 .NET 程式庫預設會使用 [ICU](http://site.icu-project.org/home) 全球化 api。</span><span class="sxs-lookup"><span data-stu-id="84adc-108">Starting in .NET 5.0, if an app is running on Windows 10 May 2019 Update or later, .NET libraries use [ICU](http://site.icu-project.org/home) globalization APIs, by default.</span></span>

> [!NOTE]
> <span data-ttu-id="84adc-109">Windows 10 2019 年5月更新和更新版本隨附于 ICU 原生程式庫。</span><span class="sxs-lookup"><span data-stu-id="84adc-109">Windows 10 May 2019 Update and later versions ship with the ICU native library.</span></span> <span data-ttu-id="84adc-110">如果 .NET 執行時間無法載入 ICU，則會改為使用 NLS。</span><span class="sxs-lookup"><span data-stu-id="84adc-110">If the .NET runtime can't load ICU, it uses NLS instead.</span></span>

## <a name="behavioral-differences"></a><span data-ttu-id="84adc-111">行為差異</span><span class="sxs-lookup"><span data-stu-id="84adc-111">Behavioral differences</span></span>

<span data-ttu-id="84adc-112">即使您不知道您使用的是全球化設施，您也可能會在應用程式中看到變更。</span><span class="sxs-lookup"><span data-stu-id="84adc-112">You might see changes in your app even if you don't realize you're using globalization facilities.</span></span> <span data-ttu-id="84adc-113">本節列出您可能會看到的一些行為變更，但也有其他的行為變更。</span><span class="sxs-lookup"><span data-stu-id="84adc-113">This section lists a couple of the behavioral changes you might see, but there are others too.</span></span>

### <a name="stringindexof"></a><span data-ttu-id="84adc-114">String.IndexOf</span><span class="sxs-lookup"><span data-stu-id="84adc-114">String.IndexOf</span></span>

<span data-ttu-id="84adc-115">請考慮下列程式碼，該程式碼會呼叫 <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> 以找出字串中分行符號的索引。</span><span class="sxs-lookup"><span data-stu-id="84adc-115">Consider the following code that calls <xref:System.String.IndexOf(System.String)?displayProperty=nameWithType> to find the index of the newline character in a string.</span></span>

```csharp
string s = "Hello\r\nworld!";
int idx = s.IndexOf("\n");
Console.WriteLine(idx);
```

- <span data-ttu-id="84adc-116">在舊版的 Windows 中，程式碼片段會列印出來 `6` 。</span><span class="sxs-lookup"><span data-stu-id="84adc-116">In previous versions of .NET on Windows, the snippet prints `6`.</span></span>
- <span data-ttu-id="84adc-117">在 Windows 19H1 和更新版本的 .NET 5.0 和更新版本中，程式碼片段會列印 `-1` 。</span><span class="sxs-lookup"><span data-stu-id="84adc-117">In .NET 5.0 and later versions on Windows 19H1 and later versions, the snippet prints `-1`.</span></span>

<span data-ttu-id="84adc-118">若要藉由執行序數搜尋而不是區分文化特性的搜尋來修正此程式碼，請呼叫多載 <xref:System.String.IndexOf(System.String,System.StringComparison)> ，並傳入 <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> 做為引數。</span><span class="sxs-lookup"><span data-stu-id="84adc-118">To fix this code by conducting an ordinal search instead of a culture-sensitive search, call the <xref:System.String.IndexOf(System.String,System.StringComparison)> overload and pass in <xref:System.StringComparison.Ordinal?displayProperty=nameWithType> as an argument.</span></span>

<span data-ttu-id="84adc-119">您可以執行程式碼分析規則 [CA1307：為清楚起見指定 StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) ，以及 [CA1309：使用序數 StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) ，在您的程式碼中尋找這些呼叫位置。</span><span class="sxs-lookup"><span data-stu-id="84adc-119">You can run code analysis rules [CA1307: Specify StringComparison for clarity](../../../../fundamentals/code-analysis/quality-rules/ca1307.md) and [CA1309: Use ordinal StringComparison](../../../../fundamentals/code-analysis/quality-rules/ca1309.md) to find these call sites in your code.</span></span>

<span data-ttu-id="84adc-120">如需詳細資訊，請參閱在 [.net 5 + 上比較字串時的行為變更](../../../../standard/base-types/string-comparison-net-5-plus.md)。</span><span class="sxs-lookup"><span data-stu-id="84adc-120">For more information, see [Behavior changes when comparing strings on .NET 5+](../../../../standard/base-types/string-comparison-net-5-plus.md).</span></span>

### <a name="currency-symbol"></a><span data-ttu-id="84adc-121">貨幣符號</span><span class="sxs-lookup"><span data-stu-id="84adc-121">Currency symbol</span></span>

<span data-ttu-id="84adc-122">請考慮使用貨幣格式規範來格式化字串的下列程式碼 `C` 。</span><span class="sxs-lookup"><span data-stu-id="84adc-122">Consider the following code that formats a string using the currency format specifier `C`.</span></span> <span data-ttu-id="84adc-123">目前線程的文化特性設定為僅包含語言的文化特性，而不是國家/地區。</span><span class="sxs-lookup"><span data-stu-id="84adc-123">The current thread's culture is set to a culture that includes only the language and not the country.</span></span>

```csharp
System.Threading.Thread.CurrentThread.CurrentCulture = new System.Globalization.CultureInfo("de");
string text = string.Format("{0:C}", 100);
```

- <span data-ttu-id="84adc-124">在舊版的 Windows 中，文字的值為 `"100,00 €"` 。</span><span class="sxs-lookup"><span data-stu-id="84adc-124">In previous versions of .NET on Windows, the value of text is `"100,00 €"`.</span></span>
- <span data-ttu-id="84adc-125">在 Windows 19H1 和更新版本的 .NET 5.0 和更新版本中，文字的值是 `"100,00 ¤"` ，它會使用國際貨幣符號而非歐元。</span><span class="sxs-lookup"><span data-stu-id="84adc-125">In .NET 5.0 and later versions on Windows 19H1 and later versions, the value of text is `"100,00 ¤"`, which uses the international currency symbol instead of the euro.</span></span> <span data-ttu-id="84adc-126">在 ICU 中，設計是貨幣是國家或地區的屬性，不是語言。</span><span class="sxs-lookup"><span data-stu-id="84adc-126">In ICU, the design is that a currency is a property of a country or region, not a language.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="84adc-127">變更的原因</span><span class="sxs-lookup"><span data-stu-id="84adc-127">Reason for change</span></span>

<span data-ttu-id="84adc-128">這是為了統一而引進的變更。在所有支援的作業系統上的淨全球化行為。</span><span class="sxs-lookup"><span data-stu-id="84adc-128">This change was introduced to unify .NET's globalization behavior across all supported operating systems.</span></span> <span data-ttu-id="84adc-129">它也能讓應用程式組合自己的全球化程式庫，而不需要依賴作業系統的內建程式庫。</span><span class="sxs-lookup"><span data-stu-id="84adc-129">It also provides the ability for applications to bundle their own globalization libraries rather than depend on the operating system's built-in libraries.</span></span>

## <a name="version-introduced"></a><span data-ttu-id="84adc-130">引進的版本</span><span class="sxs-lookup"><span data-stu-id="84adc-130">Version introduced</span></span>

<span data-ttu-id="84adc-131">.NET 5。0</span><span class="sxs-lookup"><span data-stu-id="84adc-131">.NET 5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="84adc-132">建議的動作</span><span class="sxs-lookup"><span data-stu-id="84adc-132">Recommended action</span></span>

<span data-ttu-id="84adc-133">開發人員不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="84adc-133">No action is required on the part of the developer.</span></span> <span data-ttu-id="84adc-134">但是，如果您想要繼續使用 NLS 全球化 Api，您可以將 [執行時間參數](../../../run-time-config/globalization.md#nls) 設定為還原為該行為。</span><span class="sxs-lookup"><span data-stu-id="84adc-134">However, if you wish to continue using NLS globalization APIs, you can set a [run-time switch](../../../run-time-config/globalization.md#nls) to revert to that behavior.</span></span> <span data-ttu-id="84adc-135">如需可用參數的詳細資訊，請參閱 [.net 全球化和 ICU](../../../../standard/globalization-localization/globalization-icu.md) 文章。</span><span class="sxs-lookup"><span data-stu-id="84adc-135">For more information about the available switches, see the [.NET globalization and ICU](../../../../standard/globalization-localization/globalization-icu.md) article.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="84adc-136">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="84adc-136">Affected APIs</span></span>

- <xref:System.Span%601?displayProperty=fullName>
- <xref:System.String?displayProperty=fullName>
- <span data-ttu-id="84adc-137">命名空間中的大部分類型 <xref:System.Globalization?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="84adc-137">Most types in the <xref:System.Globalization?displayProperty=fullName> namespace</span></span>
- <span data-ttu-id="84adc-138"><xref:System.Array.Sort%2A?displayProperty=fullName> 排序字串陣列時 () </span><span class="sxs-lookup"><span data-stu-id="84adc-138"><xref:System.Array.Sort%2A?displayProperty=fullName> (when sorting an array of strings)</span></span>
- <span data-ttu-id="84adc-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> 當清單元素是字串時 () </span><span class="sxs-lookup"><span data-stu-id="84adc-139"><xref:System.Collections.Generic.List%601.Sort?displayProperty=fullName> (when the list elements are strings)</span></span>
- <span data-ttu-id="84adc-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> 當索引鍵為字串時 () </span><span class="sxs-lookup"><span data-stu-id="84adc-140"><xref:System.Collections.Generic.SortedDictionary%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="84adc-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> 當索引鍵為字串時 () </span><span class="sxs-lookup"><span data-stu-id="84adc-141"><xref:System.Collections.Generic.SortedList%602?displayProperty=fullName> (when the keys are strings)</span></span>
- <span data-ttu-id="84adc-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> 當集合包含字串時 () </span><span class="sxs-lookup"><span data-stu-id="84adc-142"><xref:System.Collections.Generic.SortedSet%601?displayProperty=fullName> (when the set contains strings)</span></span>

<!--

### Affected APIs

- ``T:System.Span`1``
- `T:System.String`
- `N:System.Globalization`
- `Overload:System.Array.Sort`
- ``M:System.Collections.Generic.List`1.Sort``
- ``T:System.Collections.Generic.SortedDictionary`2``
- ``T:System.Collections.Generic.SortedList`2``
- ``T:System.Collections.Generic.SortedSet`1``

### Category

- Core .NET libraries
- Globalization

-->
