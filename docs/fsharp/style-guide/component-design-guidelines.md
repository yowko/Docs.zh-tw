---
title: F#元件設計方針
description: 了解進行寫入的指導方針F#是供取用，其他呼叫端的元件。
ms.date: 05/14/2018
ms.openlocfilehash: d72bfac1de5a57d5cce86f996f144af4bc181463
ms.sourcegitcommit: b56d59ad42140d277f2acbd003b74d655fdbc9f1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/19/2019
ms.locfileid: "54415633"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="ae2ca-103">F#元件設計方針</span><span class="sxs-lookup"><span data-stu-id="ae2ca-103">F# component design guidelines</span></span>

<span data-ttu-id="ae2ca-104">這份文件是一組元件的設計指導方針F#進行程式設計，根據F#元件的設計指導方針、 v14，Microsoft Research 和[另一個版本](https://fsharp.org/specs/component-design-guidelines/)原來策劃和維護的F#Software Foundation。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="ae2ca-105">本文件假設您已熟悉F#程式設計。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="ae2ca-106">多感謝對F#社群貢獻的有用的回饋，本指南的不同版本。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="ae2ca-107">總覽</span><span class="sxs-lookup"><span data-stu-id="ae2ca-107">Overview</span></span>

<span data-ttu-id="ae2ca-108">本文件探討某些與相關的問題F#元件的設計和撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="ae2ca-109">元件可以代表下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="ae2ca-110">層，以在您F#專案具有該專案內的外部取用者。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="ae2ca-111">適用於所使用的程式庫F#跨組件界限的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="ae2ca-112">跨組件界限是供取用任何.NET 語言程式庫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="ae2ca-113">例如適用於透過套件存放庫發佈的程式庫[NuGet](https://nuget.org)。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="ae2ca-114">請遵循本文中所述的技巧[良好的五個原則F#程式碼](index.md#five-principles-of-good-f-code)，因此利用兩者的功能，以及物件視程式設計。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="ae2ca-115">方法，不論元件和程式庫的設計工具嘗試製作最容易供開發人員的 API 時面臨的一些實用又 prosaic 的問題。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="ae2ca-116">暴增的應用程式的[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)引導您建立一組一致的使用愉快的 Api。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="ae2ca-117">一般方針</span><span class="sxs-lookup"><span data-stu-id="ae2ca-117">General guidelines</span></span>

<span data-ttu-id="ae2ca-118">有幾個通用的指導方針適用於F#程式庫，不論程式庫的目標對象。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="ae2ca-119">了解.NET 程式庫設計方針</span><span class="sxs-lookup"><span data-stu-id="ae2ca-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="ae2ca-120">不論類型的F#撰寫程式碼執行，就有的知識有價值[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="ae2ca-121">大多數其他F#.NET 程式設計人員會先熟悉下列指導方針，並且預期.NET 程式碼，以符合它們。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="ae2ca-122">.NET 程式庫設計方針提供有關命名、 設計類別和介面、 成員 （屬性、 方法、 事件等） 的設計和等等的一般指導方針，並會很有用的第一個點的各種不同的設計指引的參考。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="ae2ca-123">將 XML 文件註解新增至您的程式碼</span><span class="sxs-lookup"><span data-stu-id="ae2ca-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="ae2ca-124">公用 Api 上的 XML 文件確保使用者可以取得絕佳的 Intellisense 和 Quickinfo 時使用這些類型和成員，以及啟用建置文件庫的檔案。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="ae2ca-125">請參閱[XML 文件](../language-reference/xml-documentation.md)有關各種可用 xmldoc 註解內的其他標記的 xml 標記。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="ae2ca-126">您可以使用其中一個的簡短形式 XML 註解 (`/// comment`)，或標準的 XML 註解 (`///<summary>comment</summary>`)。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="ae2ca-127">請考慮使用明確的簽章檔 (.fsi) 穩定的程式庫和元件的 Api</span><span class="sxs-lookup"><span data-stu-id="ae2ca-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="ae2ca-128">使用明確的簽章中的檔案F#程式庫提供簡潔的公用 API，這兩個可協助確保您知道完整的公用介面的程式庫，以及提供清楚的分隔，公開文件之間和內部摘要實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="ae2ca-129">請注意，簽章檔案會新增摩擦，在變更公用 API 中，需要在實作和簽章檔案中進行的變更。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="ae2ca-130">如此一來，簽章檔案時，應該通常只有引進 API 已成為目的並不會再預期有顯著的變更。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="ae2ca-131">一律遵循 在.NET 中使用字串的最佳作法</span><span class="sxs-lookup"><span data-stu-id="ae2ca-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="ae2ca-132">請遵循[在.NET 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md)指引。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="ae2ca-133">特別是，一律明確地陳述*文化特性的意圖*中轉換字串的比較 （如果適用的話）。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="ae2ca-134">指導方針F#-面向的程式庫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="ae2ca-135">此章節提供建議，用於開發公用F#-面向的程式庫;也就是公開要使用的公用 Api 的程式庫F#開發人員。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="ae2ca-136">有各種不同的程式庫設計建議特別適用於F#。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="ae2ca-137">如果沒有遵循的特定建議事項，.NET 程式庫設計方針會是後援的指引。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="ae2ca-138">命名規範</span><span class="sxs-lookup"><span data-stu-id="ae2ca-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="ae2ca-139">使用.NET 名稱和大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="ae2ca-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="ae2ca-140">下表會遵循.NET 命名和大小寫慣例。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="ae2ca-141">有小型的新增項目也包含F#建構。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="ae2ca-142">建構</span><span class="sxs-lookup"><span data-stu-id="ae2ca-142">Construct</span></span> | <span data-ttu-id="ae2ca-143">案例</span><span class="sxs-lookup"><span data-stu-id="ae2ca-143">Case</span></span> | <span data-ttu-id="ae2ca-144">組件</span><span class="sxs-lookup"><span data-stu-id="ae2ca-144">Part</span></span> | <span data-ttu-id="ae2ca-145">範例</span><span class="sxs-lookup"><span data-stu-id="ae2ca-145">Examples</span></span> | <span data-ttu-id="ae2ca-146">注意</span><span class="sxs-lookup"><span data-stu-id="ae2ca-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="ae2ca-147">具象類型</span><span class="sxs-lookup"><span data-stu-id="ae2ca-147">Concrete types</span></span> | <span data-ttu-id="ae2ca-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-148">PascalCase</span></span> | <span data-ttu-id="ae2ca-149">名詞 / 形容詞</span><span class="sxs-lookup"><span data-stu-id="ae2ca-149">Noun/ adjective</span></span> | <span data-ttu-id="ae2ca-150">清單、 Double、 複雜</span><span class="sxs-lookup"><span data-stu-id="ae2ca-150">List, Double, Complex</span></span> | <span data-ttu-id="ae2ca-151">具象型別是結構、 類別、 列舉、 委派、 記錄、 和等位。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="ae2ca-152">雖然傳統上在 OCaml，小寫類型名稱F#已採用類型的.NET 命名配置。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="ae2ca-153">DLL</span><span class="sxs-lookup"><span data-stu-id="ae2ca-153">DLLs</span></span>           | <span data-ttu-id="ae2ca-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-154">PascalCase</span></span> |                 | <span data-ttu-id="ae2ca-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="ae2ca-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="ae2ca-156">等位標記</span><span class="sxs-lookup"><span data-stu-id="ae2ca-156">Union tags</span></span>     | <span data-ttu-id="ae2ca-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-157">PascalCase</span></span> | <span data-ttu-id="ae2ca-158">名詞</span><span class="sxs-lookup"><span data-stu-id="ae2ca-158">Noun</span></span> | <span data-ttu-id="ae2ca-159">部分新增成功</span><span class="sxs-lookup"><span data-stu-id="ae2ca-159">Some, Add, Success</span></span> | <span data-ttu-id="ae2ca-160">請勿使用公用 Api 中的前置詞。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="ae2ca-161">（選擇性） 使用的前置詞，當內部，例如 \`輸入小組 = TAlpha</span><span class="sxs-lookup"><span data-stu-id="ae2ca-161">Optionally use a prefix when internal, such as \`type Teams = TAlpha</span></span> | <span data-ttu-id="ae2ca-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="ae2ca-162">TBeta</span></span> | <span data-ttu-id="ae2ca-163">TDelta\`</span><span class="sxs-lookup"><span data-stu-id="ae2ca-163">TDelta.\`</span></span> |
| <span data-ttu-id="ae2ca-164">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="ae2ca-164">Event</span></span>          | <span data-ttu-id="ae2ca-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-165">PascalCase</span></span> | <span data-ttu-id="ae2ca-166">動詞命令</span><span class="sxs-lookup"><span data-stu-id="ae2ca-166">Verb</span></span> | <span data-ttu-id="ae2ca-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="ae2ca-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="ae2ca-168">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ae2ca-168">Exceptions</span></span>     | <span data-ttu-id="ae2ca-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-169">PascalCase</span></span> |      | <span data-ttu-id="ae2ca-170">WebException</span><span class="sxs-lookup"><span data-stu-id="ae2ca-170">WebException</span></span> | <span data-ttu-id="ae2ca-171">名稱應該以"Exception"結尾。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="ae2ca-172">欄位</span><span class="sxs-lookup"><span data-stu-id="ae2ca-172">Field</span></span>          | <span data-ttu-id="ae2ca-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-173">PascalCase</span></span> | <span data-ttu-id="ae2ca-174">名詞</span><span class="sxs-lookup"><span data-stu-id="ae2ca-174">Noun</span></span> | <span data-ttu-id="ae2ca-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="ae2ca-175">CurrentName</span></span>  | |
| <span data-ttu-id="ae2ca-176">介面型別</span><span class="sxs-lookup"><span data-stu-id="ae2ca-176">Interface types</span></span> |  <span data-ttu-id="ae2ca-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-177">PascalCase</span></span> | <span data-ttu-id="ae2ca-178">名詞 / 形容詞</span><span class="sxs-lookup"><span data-stu-id="ae2ca-178">Noun/ adjective</span></span> | <span data-ttu-id="ae2ca-179">IDisposable</span><span class="sxs-lookup"><span data-stu-id="ae2ca-179">IDisposable</span></span> | <span data-ttu-id="ae2ca-180">名稱應該以"I"開頭。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="ae2ca-181">方法</span><span class="sxs-lookup"><span data-stu-id="ae2ca-181">Method</span></span> |  <span data-ttu-id="ae2ca-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-182">PascalCase</span></span> |  <span data-ttu-id="ae2ca-183">動詞命令</span><span class="sxs-lookup"><span data-stu-id="ae2ca-183">Verb</span></span> | <span data-ttu-id="ae2ca-184">ToString</span><span class="sxs-lookup"><span data-stu-id="ae2ca-184">ToString</span></span> | |
| <span data-ttu-id="ae2ca-185">命名空間</span><span class="sxs-lookup"><span data-stu-id="ae2ca-185">Namespace</span></span> | <span data-ttu-id="ae2ca-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-186">PascalCase</span></span> | | <span data-ttu-id="ae2ca-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="ae2ca-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="ae2ca-188">通常會使用`<Organization>.<Technology>[.<Subnamespace>]`，不過卸除的組織，如果組織的技術無關。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="ae2ca-189">參數</span><span class="sxs-lookup"><span data-stu-id="ae2ca-189">Parameters</span></span> | <span data-ttu-id="ae2ca-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-190">camelCase</span></span> | <span data-ttu-id="ae2ca-191">名詞</span><span class="sxs-lookup"><span data-stu-id="ae2ca-191">Noun</span></span> |  <span data-ttu-id="ae2ca-192">類型名稱、 轉換、 範圍</span><span class="sxs-lookup"><span data-stu-id="ae2ca-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="ae2ca-193">讓值 （內部）</span><span class="sxs-lookup"><span data-stu-id="ae2ca-193">let values (internal)</span></span> | <span data-ttu-id="ae2ca-194">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-194">camelCase or PascalCase</span></span> | <span data-ttu-id="ae2ca-195">名詞 / 動詞命令</span><span class="sxs-lookup"><span data-stu-id="ae2ca-195">Noun/ verb</span></span> |  <span data-ttu-id="ae2ca-196">getValue myTable</span><span class="sxs-lookup"><span data-stu-id="ae2ca-196">getValue, myTable</span></span> |
| <span data-ttu-id="ae2ca-197">讓值 （外部）</span><span class="sxs-lookup"><span data-stu-id="ae2ca-197">let values (external)</span></span> | <span data-ttu-id="ae2ca-198">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-198">camelCase or PascalCase</span></span> | <span data-ttu-id="ae2ca-199">名詞/動詞命令</span><span class="sxs-lookup"><span data-stu-id="ae2ca-199">Noun/verb</span></span>  | <span data-ttu-id="ae2ca-200">List.map, Dates.Today</span><span class="sxs-lookup"><span data-stu-id="ae2ca-200">List.map, Dates.Today</span></span> | <span data-ttu-id="ae2ca-201">let 繫結值通常是公用的遵循傳統的功能性設計模式時。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="ae2ca-202">不過，通常使用 PascalCase 的識別碼可以使用其他.NET 語言時。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="ae2ca-203">屬性</span><span class="sxs-lookup"><span data-stu-id="ae2ca-203">Property</span></span>  | <span data-ttu-id="ae2ca-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-204">PascalCase</span></span>  | <span data-ttu-id="ae2ca-205">名詞 / 形容詞</span><span class="sxs-lookup"><span data-stu-id="ae2ca-205">Noun/ adjective</span></span>  | <span data-ttu-id="ae2ca-206">IsEndOfFile，背景色彩</span><span class="sxs-lookup"><span data-stu-id="ae2ca-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="ae2ca-207">布林值屬性通常不使用，因為可以且應該是肯定的如同 IsEndOfFile，不 IsNotEndOfFile。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="ae2ca-208">避免縮寫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-208">Avoid abbreviations</span></span>

<span data-ttu-id="ae2ca-209">.NET 指導方針不鼓勵使用縮寫 (例如，「 使用`OnButtonClick`而非`OnBtnClick`")。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="ae2ca-210">常用的縮寫，例如`Async`所容許的 「 非同步 」、。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="ae2ca-211">函式程式設計，有時候會忽略此指導方針比方說，`List.iter`用於 「 逐一查看 」 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="ae2ca-212">基於這個理由，使用縮寫傾向於容許更高的程度上，在F#對F#進行程式設計，但仍通常應該避免在公用元件設計中。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="ae2ca-213">避免名稱衝突的大小寫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-213">Avoid casing name collisions</span></span>

<span data-ttu-id="ae2ca-214">.NET 指導方針會假設，單獨的大小寫不能用來釐清發生名稱衝突，因為某些用戶端語言 (例如，Visual Basic) 都不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="ae2ca-215">在適當時使用縮寫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="ae2ca-216">首字母縮略字，例如 XML 不縮寫，且廣泛用於 uncapitalized 格式 (Xml) 的.NET 程式庫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="ae2ca-217">只應該使用已知且眾所公認的縮寫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="ae2ca-218">對泛型參數名稱使用 PascalCase</span><span class="sxs-lookup"><span data-stu-id="ae2ca-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="ae2ca-219">請勿使用 PascalCase 公用 Api，包括中的泛型參數名稱F#-面向的程式庫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="ae2ca-220">特別的是，使用名稱，例如`T`， `U`， `T1`，`T2`任意的泛型參數，以及特定名稱合理，則F#-面向的程式庫會使用名稱，例如`Key`， `Value`，`Arg` (但不是例如`TKey`)。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="ae2ca-221">使用 PascalCase 或 camelCase 公用函式和中的值F#模組</span><span class="sxs-lookup"><span data-stu-id="ae2ca-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="ae2ca-222">camelCase 用於專為使用的公用函式不合格 (比方說， `invalidArg`)，以及 「 標準集合函式 」 （例如，List.map）。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="ae2ca-223">在這兩種情況，函式名稱做為許多語言的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="ae2ca-224">物件、 類型和模組的設計</span><span class="sxs-lookup"><span data-stu-id="ae2ca-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="ae2ca-225">使用命名空間或模組來包含您的類型和模組</span><span class="sxs-lookup"><span data-stu-id="ae2ca-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="ae2ca-226">每個F#元件中的檔案的開頭必須為命名空間宣告或模組宣告。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="ae2ca-227">或</span><span class="sxs-lookup"><span data-stu-id="ae2ca-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="ae2ca-228">使用模組與命名空間來組織程式碼在最上層的差異如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="ae2ca-229">命名空間可以跨多個檔案</span><span class="sxs-lookup"><span data-stu-id="ae2ca-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="ae2ca-230">命名空間不能包含F#函式，除非它們是在內部的模組中</span><span class="sxs-lookup"><span data-stu-id="ae2ca-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="ae2ca-231">任何指定的模組的程式碼必須包含在單一檔案</span><span class="sxs-lookup"><span data-stu-id="ae2ca-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="ae2ca-232">最上層模組可以包含F#函式，而不需要內部的模組</span><span class="sxs-lookup"><span data-stu-id="ae2ca-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="ae2ca-233">之間的最上層命名空間或模組的選擇會影響已編譯的形式的程式碼，並因此會影響其他.NET 語言檢視應您的 API 最終取用外部F#程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="ae2ca-234">使用內建函式物件類型的作業的方法和屬性</span><span class="sxs-lookup"><span data-stu-id="ae2ca-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="ae2ca-235">當處理物件，最好是確定可取用的功能都實作為方法和屬性，該型別上。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="ae2ca-236">大量的功能，為給定成員需要不一定會實作在該成員，但應該是可取用的一項，該功能。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="ae2ca-237">使用類別來封裝可變動狀態</span><span class="sxs-lookup"><span data-stu-id="ae2ca-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="ae2ca-238">在F#，這只需要完成，狀態未已封裝的另一個語言建構，例如關閉、 序列運算式中或非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="ae2ca-239">使用介面來群組的相關作業</span><span class="sxs-lookup"><span data-stu-id="ae2ca-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="ae2ca-240">您可以使用介面型別來代表一組作業。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="ae2ca-241">這是慣用的其他選項，例如 tuple 的函式或函式的記錄。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="ae2ca-242">在到：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="ae2ca-243">介面是在.NET 中，您可用來達成什麼函式會正常提供您的第一級概念。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="ae2ca-244">此外，它們可以用來編碼您的程式，記錄的函式不能存在的類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="ae2ca-245">在集合上使用群組函式，處理模組</span><span class="sxs-lookup"><span data-stu-id="ae2ca-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="ae2ca-246">當您定義集合型別時，請考慮提供一組標準的作業要`CollectionType.map`和`CollectionType.iter`) 新的集合類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="ae2ca-247">如果您包含這類模組，請遵循 FSharp.Core 中找到的函式的標準命名慣例。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="ae2ca-248">使用群組函式模組通用的標準函式，尤其是在數學與 DSL 程式庫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="ae2ca-249">比方說，`Microsoft.FSharp.Core.Operators`是最上層函式會自動開啟的集合 (例如`abs`和`sin`) 提供 FSharp.Core.dll。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="ae2ca-250">同樣地，統計資料的程式庫可能包含具有函式的模組`erf`和`erfc`，此模組可明確或自動開啟。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="ae2ca-251">請考慮使用 RequireQualifiedAccess 並仔細套用 AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="ae2ca-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="ae2ca-252">新增`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="ae2ca-253">比方說，`Microsoft.FSharp.Collections.List`模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="ae2ca-254">當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="ae2ca-255">需要完整存取權可能會大幅增加的長期維護性和可演化性程式庫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="ae2ca-256">新增`[<AutoOpen>]`至模組的屬性表示開啟包含命名空間時，將會開啟模組。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="ae2ca-257">`[<AutoOpen>]`屬性可能也會套用到組件，表示當組件參考時，會自動開啟模組。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="ae2ca-258">比方說，統計資料的媒體櫃**MathsHeaven.Statistics**可能會包含`module MathsHeaven.Statistics.Operators`包含函式`erf`和`erfc`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="ae2ca-259">它是合理的作法是將標示為此模組`[<AutoOpen>]`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="ae2ca-260">這表示`open MathsHeaven.Statistics`也會開啟此模組並將名稱`erf`和`erfc`進入範圍內。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="ae2ca-261">使用另一個良好`[<AutoOpen>]`會包含擴充方法的模組。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="ae2ca-262">過度使用的`[<AutoOpen>]`污染的命名空間和屬性的潛在客戶應該小心使用。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="ae2ca-263">針對特定的程式庫中特定網域，審慎使用`[<AutoOpen>]`可能會導致更好的可用性。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="ae2ca-264">請考慮在其中使用已知的運算子是適當的類別上定義運算子的成員</span><span class="sxs-lookup"><span data-stu-id="ae2ca-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="ae2ca-265">有時候類別用來建立模型的數學建構，例如向量。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="ae2ca-266">正在模型化的網域有已知的運算子，定義為 「 內建函式類別的成員時，很有幫助。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="ae2ca-267">本指南會對應至這些類型的一般.NET 指導方針。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="ae2ca-268">不過，它可以是另外很重要的F#編碼，因為這可讓這些型別可以用於搭配F#函式和成員的條件約束，例如 List.sumBy 方法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="ae2ca-269">請考慮使用 CompiledName 來提供。其他.NET 語言取用者的 NET 的易記名稱</span><span class="sxs-lookup"><span data-stu-id="ae2ca-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="ae2ca-270">有時您可能想要指定一種樣式中的名稱，F#取用者 (例如大小寫，使它顯示在靜態成員函式模組繫結一樣)，但有不同的樣式名稱，編譯成組件時。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="ae2ca-271">您可以使用`[<CompiledName>]`屬性來提供不同的樣式，用於非F#使用組件的程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="ae2ca-272">藉由使用`[<CompiledName>]`，您可以使用的.NET 命名慣例非F#的組件的取用者。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="ae2ca-273">使用方法多載成員函式，如果這麼做可以提供更簡單的 API</span><span class="sxs-lookup"><span data-stu-id="ae2ca-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="ae2ca-274">方法多載是功能強大的工具簡化的 API，可能需要執行類似的功能，但使用不同的選項或引數。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="ae2ca-275">在F#，它是較常見的引數數目，而不是引數型別多載。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="ae2ca-276">隱藏記錄和聯集類型的表示，如果這些類型的設計都可能發展</span><span class="sxs-lookup"><span data-stu-id="ae2ca-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="ae2ca-277">以免洩露物件的具象表示法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="ae2ca-278">比方說，具象表示法的<xref:System.DateTime>值不會揭露外部、 公用 API 的.NET 程式庫設計。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="ae2ca-279">在執行階段，Common Language Runtime 會知道將會在整個執行的認可的實作。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="ae2ca-280">不過，已編譯程式碼不本身挑選的相依性的實體表示法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="ae2ca-281">避免使用實作繼承的擴充性</span><span class="sxs-lookup"><span data-stu-id="ae2ca-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="ae2ca-282">在F#，實作繼承很少使用。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="ae2ca-283">此外，繼承階層架構通常是複雜且難以變更的新要求到達時。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="ae2ca-284">繼承實作仍然存在於F#的相容性和罕見的情況下，它是問題，最佳的解決方案，但應該要搜尋的替代技術，在您F#程式時為多型，例如介面設計實作。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="ae2ca-285">函式和成員的簽章</span><span class="sxs-lookup"><span data-stu-id="ae2ca-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="ae2ca-286">使用傳回值的 tuple，傳回一小部分的多個不相關的值時</span><span class="sxs-lookup"><span data-stu-id="ae2ca-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="ae2ca-287">以下是使用 tuple，傳回的型別中的理想範例：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="ae2ca-288">傳回類型，而且包含許多元件，或在單一的識別實體相關的元件，請考慮使用具名型別，而不 tuple。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="ae2ca-289">使用`Async<T>`如需非同步程式設計在F#API 界限</span><span class="sxs-lookup"><span data-stu-id="ae2ca-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="ae2ca-290">如果沒有對應的同步作業，名為`Operation`，會傳回`T`，則應命名為非同步作業`AsyncOperation`如果它傳回`Async<T>`或`OperationAsync`如果它傳回`Task<T>`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="ae2ca-291">常用的.NET 型別公開 Begin/End 方法，請考慮使用針對`Async.FromBeginEnd`撰寫擴充方法提供一個外觀為F#的.NET Api 的非同步程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int): int =
        ...
    member this.AsyncCompute(x:int): Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="ae2ca-292">例外狀況</span><span class="sxs-lookup"><span data-stu-id="ae2ca-292">Exceptions</span></span>

<span data-ttu-id="ae2ca-293">請參閱[錯誤管理](conventions.md#error-management)若要了解例外狀況、 結果和選項的適當用法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-293">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="ae2ca-294">擴充成員</span><span class="sxs-lookup"><span data-stu-id="ae2ca-294">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="ae2ca-295">請仔細套用F#中的擴充成員F#對F#元件</span><span class="sxs-lookup"><span data-stu-id="ae2ca-295">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="ae2ca-296">F#擴充成員通常只應位於與大多數的其模式的使用中的型別相關聯的內建作業的結束的作業。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-296">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="ae2ca-297">一個常見用法是提供到較慣用的 ApiF#各種不同的.NET 類型：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-297">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="ae2ca-298">等位型別</span><span class="sxs-lookup"><span data-stu-id="ae2ca-298">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="ae2ca-299">而不是類別階層架構的差別聯的集用於樹狀結構的資料</span><span class="sxs-lookup"><span data-stu-id="ae2ca-299">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="ae2ca-300">類似樹狀目錄結構是以遞迴方式定義。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-300">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="ae2ca-301">這是很冗長，因此具有繼承，但差別聯集與雅緻。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-301">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="ae2ca-302">表示差別等位類似樹狀目錄中的資料也可讓您受益於 exhaustiveness 在模式比對。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-302">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="ae2ca-303">使用`[<RequireQualifiedAccess>]`上其大小寫的名稱不是夠唯一的聯集類型</span><span class="sxs-lookup"><span data-stu-id="ae2ca-303">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="ae2ca-304">您可能會發現自己位於網域中相同名稱的不同項目，例如差異等位的情況下最適當的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-304">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="ae2ca-305">您可以使用`[<RequireQualifiedAccess>]`若要區分大小寫的名稱，以避免觸發令人困惑所造成的錯誤，以遮蔽相依的排序`open`陳述式</span><span class="sxs-lookup"><span data-stu-id="ae2ca-305">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="ae2ca-306">如果這些類型的設計都可能發展，隱藏差別聯集的表示二進位相容的 api</span><span class="sxs-lookup"><span data-stu-id="ae2ca-306">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="ae2ca-307">等位類型均依賴F#模式比對的簡明的程式設計模型的表單。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-307">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="ae2ca-308">如先前所述，您應該避免洩漏具體資料表示法，如果這些類型的設計都可能發展。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-308">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="ae2ca-309">例如，已區分的聯集的表示法可能會隱藏使用私用或內部的宣告，或使用簽章檔案。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-309">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="ae2ca-310">如果您廣泛地顯示差別聯的集，您可能會發現很難版本您的程式庫而不會中斷使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-310">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="ae2ca-311">相反地，請考慮顯示一或多個作用中的模式，以允許進行模式比對您類型的值。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-311">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="ae2ca-312">作用中的模式提供替代方式來提供F#模式比對，同時避免公開使用的取用者F#直接等位型別。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-312">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="ae2ca-313">內嵌函式和成員的條件約束</span><span class="sxs-lookup"><span data-stu-id="ae2ca-313">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="ae2ca-314">定義泛型的數值演算法與隱含的成員條件約束和以統計方式解析的泛型型別使用內嵌函式</span><span class="sxs-lookup"><span data-stu-id="ae2ca-314">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="ae2ca-315">算術成員條件約束和F#比較的條件約束是標準的F#程式設計。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-315">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="ae2ca-316">例如，請參考下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-316">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="ae2ca-317">此函式的類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-317">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="ae2ca-318">這是適合的函式，如需數學程式庫中的公用 API。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-318">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="ae2ca-319">請避免使用成員條件約束，以模擬型別類別和鴨子類型</span><span class="sxs-lookup"><span data-stu-id="ae2ca-319">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="ae2ca-320">就可以模擬"duck typing 」 使用F#成員的條件約束。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-320">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="ae2ca-321">不過，可讓成員使用這個屬性不在一般應在F#對F#程式庫設計。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-321">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="ae2ca-322">這是因為在不熟悉或非標準隱含的條件約束為基礎的程式庫設計很容易導致使用者程式碼變得不具彈性且繫結至一個特定的架構模式。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-322">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="ae2ca-323">此外，很可能會大量使用這種方式中的成員條件約束導致非常長的編譯時間。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-323">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="ae2ca-324">運算子定義</span><span class="sxs-lookup"><span data-stu-id="ae2ca-324">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="ae2ca-325">應避免定義自訂的符號運算子</span><span class="sxs-lookup"><span data-stu-id="ae2ca-325">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="ae2ca-326">自訂運算子是不可或缺，在某些情況下，非常有用的影響力裝置極為龐大的實作程式碼內。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-326">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="ae2ca-327">程式庫的新使用者，通常是容易使用具名函式。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-327">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="ae2ca-328">此外，自訂的符號運算子可能很難文件，而且使用者尋找更難查詢運算子，因為 IDE 和搜尋引擎中的現有限制的說明。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-328">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="ae2ca-329">如此一來，最好是發佈您的功能，為具名函式和成員，和此外公開 （expose） 運算子，這項功能只有當影響力的優點勝的文件和認知的成本來保留它們。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-329">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="ae2ca-330">測量單位</span><span class="sxs-lookup"><span data-stu-id="ae2ca-330">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="ae2ca-331">謹慎使用的測量單位中加入的型別安全F#程式碼</span><span class="sxs-lookup"><span data-stu-id="ae2ca-331">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="ae2ca-332">檢視其他.NET 語言時，會清除輸入的其他資訊的單位量值。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-332">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="ae2ca-333">請注意，.NET 元件、 工具和反映將會看到 san-單元的類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-333">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="ae2ca-334">例如，C# 取用者會看到`float`而非`float<kg>`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-334">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="ae2ca-335">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-335">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="ae2ca-336">小心使用類型縮寫來簡化F#程式碼</span><span class="sxs-lookup"><span data-stu-id="ae2ca-336">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="ae2ca-337">.NET 元件、 工具和反映不會看到類型縮寫的名稱。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-337">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="ae2ca-338">類型縮寫的重要使用方式也可以讓出現越複雜，比它實際上是，這可能會感到困惑的取用者的網域。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-338">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="ae2ca-339">避免其成員和屬性應該在縮寫的型別上的可用本質上不同的公用類型的類型縮寫</span><span class="sxs-lookup"><span data-stu-id="ae2ca-339">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="ae2ca-340">在此情況下，在縮寫的類型會顯示太多有關所定義的實際類型的表示法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-340">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="ae2ca-341">相反地，包裝在類別類型或單一案例的已區分聯集的縮寫，請考慮 （或者，當效能很重要時，請考慮使用結構型別來包裝縮寫）。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-341">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="ae2ca-342">比方說，您會嘗試定義多重對應的特殊案例為F#對應，例如：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-342">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="ae2ca-343">不過，這個型別上的邏輯的點標記法作業不是在地圖上的作業相同，比方說，是合理的 lookup 運算子對應。[索引鍵] 傳回空的清單，如果索引鍵不在字典中，而不是引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-343">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ae2ca-344">使用其他.NET 語言的程式庫的指導方針</span><span class="sxs-lookup"><span data-stu-id="ae2ca-344">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="ae2ca-345">在設計時使用其他.NET 語言的程式庫，請務必遵守[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-345">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="ae2ca-346">本文件中，這些程式庫會標示為普通的.NET 程式庫，而不是F#-面向的程式庫，使用F#建構不受任何限制。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-346">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="ae2ca-347">設計開啟了香草的.NET 程式庫表示提供熟悉且慣用的 Api 與.NET Framework 的其餘部分一致的使用降至最低F#-在公用 API 中的特定建構。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-347">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="ae2ca-348">下列各節中說明的規則。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-348">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ae2ca-349">命名空間和類型的設計 （適用於讓您使用其他.NET 語言的程式庫）</span><span class="sxs-lookup"><span data-stu-id="ae2ca-349">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="ae2ca-350">套用至您的元件的公用 API 的.NET 命名慣例</span><span class="sxs-lookup"><span data-stu-id="ae2ca-350">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="ae2ca-351">請特別注意使用縮寫的名稱和.NET 的大小寫方針。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-351">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="ae2ca-352">針對您元件的主要組織性結構為使用命名空間、 類型和成員</span><span class="sxs-lookup"><span data-stu-id="ae2ca-352">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="ae2ca-353">包含公開功能的所有檔案的都開頭`namespace`宣告，並只公開實體命名空間中的應該是類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-353">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="ae2ca-354">請勿使用F#模組。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-354">Do not use F# modules.</span></span>

<span data-ttu-id="ae2ca-355">您可以使用非公用模組來保存實作程式碼、 公用程式類型和公用程式函式。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-355">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="ae2ca-356">靜態類型應比模組，因為它們允許未來發展的 api 使用多載和其他的.NET API 設計概念，不能使用在F#模組。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-356">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="ae2ca-357">比方說，取代下列的公用 API:</span><span class="sxs-lookup"><span data-stu-id="ae2ca-357">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="ae2ca-358">請改為考慮：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-358">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="ae2ca-359">使用F#記錄 vanilla.NET Api 中的類型，如果將不會演化設計的類型</span><span class="sxs-lookup"><span data-stu-id="ae2ca-359">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="ae2ca-360">F#記錄類型編譯為一個簡單的.NET 類別。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-360">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="ae2ca-361">這些是適用於 Api 中的一些簡單的穩定類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-361">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="ae2ca-362">您應該考慮使用`[<NoEquality>]`和`[<NoComparison>]`屬性來隱藏自動產生的介面。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-362">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="ae2ca-363">也請避免使用 vanilla.NET Api 中的可變動的記錄欄位，這些會公開為公用欄位。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-363">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="ae2ca-364">請務必考慮是否類別會提供 API 的未來發展更具彈性的選項。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-364">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="ae2ca-365">例如，下列F#的程式碼公開至公用 APIC#取用者：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-365">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="ae2ca-366">F#：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-366">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="ae2ca-367">C#: </span><span class="sxs-lookup"><span data-stu-id="ae2ca-367">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="ae2ca-368">隱藏的表示法F#vanilla.NET Api 的聯集類型</span><span class="sxs-lookup"><span data-stu-id="ae2ca-368">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="ae2ca-369">F#等位型別並不常使用跨元件界限，即使是針對F#對F#撰寫程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-369">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="ae2ca-370">也就是絕佳的實作裝置時在元件和程式庫內部使用。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-370">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="ae2ca-371">在設計一種普通的.NET API 時，請考慮隱藏使用私用宣告或簽章檔案的聯集類型的表示法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-371">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="ae2ca-372">您可能也會擴充以提供所需的等位的表示法在內部使用與成員的類型.NET 後端 API。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-372">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True

    /// A public member for use from C#
    member x.Evaluate =
        match x with
        | And(a,b) -> a.Evaluate && b.Evaluate
        | Not a -> not a.Evaluate
        | True -> true

    /// A public member for use from C#
    static member CreateAnd(a,b) = And(a,b)
```

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="ae2ca-373">設計 GUI 和其他元件使用的 framework 的設計模式</span><span class="sxs-lookup"><span data-stu-id="ae2ca-373">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="ae2ca-374">另外還有許多不同的架構在.NET 內，例如 WinForms、 WPF 和 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-374">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="ae2ca-375">如果您要設計用於這些架構的元件，則應該使用命名與設計慣例，每個。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-375">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="ae2ca-376">例如，針對 WPF 程式設計，採用 WPF 設計模式，您要設計的類別。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-376">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="ae2ca-377">在使用者介面程式設計模型，使用 設計模式，例如事件和通知為基礎的集合，例如位於<xref:System.Collections.ObjectModel>。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-377">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="ae2ca-378">物件和成員的設計 （適用於讓您使用其他.NET 語言的程式庫）</span><span class="sxs-lookup"><span data-stu-id="ae2ca-378">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="ae2ca-379">若要公開.NET 事件使用 CLIEvent 屬性</span><span class="sxs-lookup"><span data-stu-id="ae2ca-379">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="ae2ca-380">建構`DelegateEvent`與特定的.NET 委派接受物件的型別和`EventArgs`(而非`Event`，這只是使用`FSharpHandler`預設的型別)，讓事件發佈在其他.NET 語言的熟悉方式。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-380">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x: int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="ae2ca-381">傳回.NET 工作方法公開非同步作業</span><span class="sxs-lookup"><span data-stu-id="ae2ca-381">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="ae2ca-382">在.NET 中使用工作來代表使用中的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-382">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="ae2ca-383">工作處於較不複合比一般F#`Async<T>`物件，因為它們表示 「 已經執行 」 工作，而無法建構在一起時，執行平行的組合，或其中隱藏取消訊號的傳播方式和其他內容相關的參數。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-383">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="ae2ca-384">不過，儘管如此，傳回工作的方法是在.NET 上的非同步程式設計的標準表示法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-384">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="ae2ca-385">您會經常也要接受明確取消語彙基元：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-385">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="ae2ca-386">使用.NET 的委派類型，而不是F#函式類型</span><span class="sxs-lookup"><span data-stu-id="ae2ca-386">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="ae2ca-387">這裡 」F#函式類型 」 表示 「 箭頭 」 類型喜歡`int -> int`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-387">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="ae2ca-388">而不是這個：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-388">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="ae2ca-389">請執行：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-389">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="ae2ca-390">F#函式類型會顯示為`class FSharpFunc<T,U>`用於其他.NET 語言，因此較不適合用於語言功能和工具，了解委派類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-390">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="ae2ca-391">撰寫目標設為.NET Framework 3.5 或更新版本，較高順序方法時`System.Func`和`System.Action`委派是正確的 Api，可讓.NET 開發人員使用這些 Api 以低摩擦方式發行。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-391">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="ae2ca-392">(系統定義的委派類型時以.NET Framework 2.0 為目標，會更受到限制，請考慮使用預先定義的委派類型，例如`System.Converter<T,U>`或特定的委派型別定義。)</span><span class="sxs-lookup"><span data-stu-id="ae2ca-392">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="ae2ca-393">相反地，.NET 委派不自然的F#-面向的程式庫 (請參閱下一節F#-面向的程式庫)。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-393">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="ae2ca-394">如此一來，常見的實作策略開發 vanilla.NET 程式庫的高階方法時是撰寫所有實作使用F#函式類型，然後再建立 實際F#實作。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-394">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="ae2ca-395">使用 TryGetValue 模式，而不是傳回F#選項值，並想要採取的方法多載F#選項做為引數的值</span><span class="sxs-lookup"><span data-stu-id="ae2ca-395">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="ae2ca-396">常見的模式所用的F#Api 中的選項類型是較佳 vanilla 中實作使用標準的.NET 的.NET Api 設計的技術。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-396">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="ae2ca-397">而不是傳回F#選項值，請考慮使用 bool 傳回型別，再加上"TryGetValue 」 模式與 out 參數。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-397">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="ae2ca-398">而不是採用F#選項做為參數的值，請考慮使用方法多載或選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-398">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal: byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x: int, y: int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x: int) = x

member this.ParamOverload(x: int, y: int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="ae2ca-399">使用.NET 集合介面型別 IEnumerable\<T\>和 IDictionary\<索引鍵、 值\>參數和傳回值</span><span class="sxs-lookup"><span data-stu-id="ae2ca-399">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="ae2ca-400">避免使用的具象集合類型，例如.NET 陣列`T[]`，F#型別`list<T>`，`Map<Key,Value>`並`Set<T>`，以及.NET 的具象集合類型，例如`Dictionary<Key,Value>`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-400">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="ae2ca-401">.NET 程式庫設計方針有很好的建議，有關何時使用各種集合類型，例如`IEnumerable<T>`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-401">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="ae2ca-402">某些使用陣列 (`T[]`) 是可接受在某些情況下，效能地面上。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-402">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="ae2ca-403">請注意，特別`seq<T>`是只F#別名，以供`IEnumerable<T>`，並因此 seq 通常是一種普通的.NET API 的適當類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-403">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="ae2ca-404">而不是F#會列出：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-404">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="ae2ca-405">使用F#序列：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-405">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="ae2ca-406">作為唯一的輸入類型的方法中的單位類型，定義零引數的方法，或作為唯一會傳回型別定義傳回 void 的方法</span><span class="sxs-lookup"><span data-stu-id="ae2ca-406">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="ae2ca-407">避免的單位類型的其他用途。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-407">Avoid other uses of the unit type.</span></span> <span data-ttu-id="ae2ca-408">這些是很好：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-408">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="ae2ca-409">這是不正確：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-409">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="ae2ca-410">檢查開啟了香草的.NET API 界限上的 null 值</span><span class="sxs-lookup"><span data-stu-id="ae2ca-410">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="ae2ca-411">F#實作程式碼通常會有較少 null 值的詳細資訊，所以不可變的設計模式，以及使用 null 常值的限制F#類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-411">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="ae2ca-412">其他.NET 語言通常會使用 null 值更為頻繁。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-412">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="ae2ca-413">因為這個緣故，F#所公開的一種普通的.NET API 的程式碼應該檢查參數為 null 的 API 界限上，並防止這些值傳送到更深入F#的實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-413">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="ae2ca-414">`isNull`函式 」 或 「 模式比對`null`模式可用。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-414">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="ae2ca-415">請避免使用當做傳回值的 tuple</span><span class="sxs-lookup"><span data-stu-id="ae2ca-415">Avoid using tuples as return values</span></span>

<span data-ttu-id="ae2ca-416">相反地，想傳回保留彙總的資料，或使用 out 參數傳回多個值的具名型別。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-416">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="ae2ca-417">雖然在.NET 中存在的 tuple 和結構元組 （包括結構元組 C# 語言支援），它們通常不會提供理想的和預期的 API 適用於.NET 開發人員。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-417">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="ae2ca-418">避免使用調用的參數</span><span class="sxs-lookup"><span data-stu-id="ae2ca-418">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="ae2ca-419">請改用.NET 呼叫慣例``Method(arg1,arg2,…,argN)``。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-419">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="ae2ca-420">提示：如果您在設計程式庫，讓您使用任何.NET 語言，則無法取代的其實是一些實驗性C#和 Visual Basic，請確認您的程式庫 」 操作權限 」 的這些語言的程式設計。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-420">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="ae2ca-421">您也可以使用.NET 反射程式和 Visual Studio 物件瀏覽器之類的工具，以確保程式庫和其文件會出現如預期般對開發人員。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-421">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="ae2ca-422">附錄</span><span class="sxs-lookup"><span data-stu-id="ae2ca-422">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="ae2ca-423">設計的端對端範例F#以供其他.NET 語言的程式碼</span><span class="sxs-lookup"><span data-stu-id="ae2ca-423">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="ae2ca-424">請考慮下列類別：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-424">Consider the following class:</span></span>

```fsharp
open System

type Point1(angle,radius) =
    new() = Point1(angle=0.0, radius=0.0)
    member x.Angle = angle
    member x.Radius = radius
    member x.Stretch(l) = Point1(angle=x.Angle, radius=x.Radius * l)
    member x.Warp(f) = Point1(angle=f(x.Angle), radius=x.Radius)
    static member Circle(n) =
        [ for i in 1..n -> Point1(angle=2.0*Math.PI/float(n), radius=1.0) ]
```

<span data-ttu-id="ae2ca-425">推斷F#此類別類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-425">The inferred F# type of this class is as follows:</span></span>

```fsharp
type Point1 =
    new : unit -> Point1
    new : angle:double * radius:double -> Point1
    static member Circle : n:int -> Point1 list
    member Stretch : l:double -> Point1
    member Warp : f:(double -> double) -> Point1
    member Angle : double
    member Radius : double
```

<span data-ttu-id="ae2ca-426">讓我們看看這個F#類型會顯示使用另一種.NET 語言的程式設計人員。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-426">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="ae2ca-427">例如，大約 C# 「 簽章 」 如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-427">For example, the approximate C# “signature” is as follows:</span></span>

```csharp
// C# signature for the unadjusted Point1 class
public class Point1
{
    public Point1();

    public Point1(double angle, double radius);

    public static Microsoft.FSharp.Collections.List<Point1> Circle(int count);

    public Point1 Stretch(double factor);

    public Point1 Warp(Microsoft.FSharp.Core.FastFunc<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="ae2ca-428">有幾個重點来注意有關如何F#表示的建構如下。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-428">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="ae2ca-429">例如: </span><span class="sxs-lookup"><span data-stu-id="ae2ca-429">For example:</span></span>

* <span data-ttu-id="ae2ca-430">已保留中繼資料，例如引數名稱。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-430">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="ae2ca-431">F#方法接受兩個引數，成為C#兩個引數的方法。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-431">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="ae2ca-432">函式和清單會變成參考中的對應類型F#程式庫。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-432">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="ae2ca-433">下列程式碼示範如何調整此程式碼以納入考量的這些項目。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-433">The following code shows how to adjust this code to take these things into account.</span></span>

```fsharp
namespace SuperDuperFSharpLibrary.Types

type RadialPoint(angle:double, radius:double) =

    /// Return a point at the origin
    new() = RadialPoint(angle=0.0, radius=0.0)

    /// The angle to the point, from the x-axis
    member x.Angle = angle

    /// The distance to the point, from the origin
    member x.Radius = radius

    /// Return a new point, with radius multiplied by the given factor
    member x.Stretch(factor) =
        RadialPoint(angle=angle, radius=radius * factor)

    /// Return a new point, with angle transformed by the function
    member x.Warp(transform:Func<_,_>) =
        RadialPoint(angle=transform.Invoke angle, radius=radius)

    /// Return a sequence of points describing an approximate circle using
    /// the given count of points
    static member Circle(count) =
        seq { for i in 1..count ->
                RadialPoint(angle=2.0*Math.PI/float(count), radius=1.0) }
```

<span data-ttu-id="ae2ca-434">推斷F#類型的程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-434">The inferred F# type of the code is as follows:</span></span>

```fsharp
type RadialPoint =
    new : unit -> RadialPoint
    new : angle:double * radius:double -> RadialPoint
    static member Circle : count:int -> seq<RadialPoint>
    member Stretch : factor:double -> RadialPoint
    member Warp : transform:System.Func<double,double> -> RadialPoint
    member Angle : double
    member Radius : double
```

<span data-ttu-id="ae2ca-435">C# 簽章現在如下所示：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-435">The C# signature is now as follows:</span></span>

```csharp
public class RadialPoint
{
    public RadialPoint();

    public RadialPoint(double angle, double radius);

    public static System.Collections.Generic.IEnumerable<RadialPoint> Circle(int count);

    public RadialPoint Stretch(double factor);

    public RadialPoint Warp(System.Func<double,double> transform);

    public double Angle { get; }

    public double Radius { get; }
}
```

<span data-ttu-id="ae2ca-436">若要準備使用這個型別因為 vanilla 的.NET 程式庫的一部分，如下所示，進行修正：</span><span class="sxs-lookup"><span data-stu-id="ae2ca-436">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="ae2ca-437">調整數個名稱： `Point1`， `n`， `l`，和`f`成為`RadialPoint`， `count`， `factor`，以及`transform`分別。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-437">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="ae2ca-438">使用傳回型別`seq<RadialPoint>`而非`RadialPoint list`藉由變更清單建構 using`[ ... ]`序列建構使用`IEnumerable<RadialPoint>`。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-438">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="ae2ca-439">使用.NET 的委派型別`System.Func`而不是F#函式類型。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-439">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="ae2ca-440">這可讓您使用 C# 程式碼到目前為止還棒。</span><span class="sxs-lookup"><span data-stu-id="ae2ca-440">This makes it far nicer to consume in C# code.</span></span>
