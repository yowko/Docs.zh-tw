---
title: 'F # 元件的設計指導方針'
description: '了解撰寫 F # 預定由其他呼叫端元件的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 7e71710b1bc2fe3e8d7a5a091513a1432650dc04
ms.sourcegitcommit: 43924acbdbb3981d103e11049bbe460457d42073
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/23/2018
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="24275-103">F # 元件的設計指導方針</span><span class="sxs-lookup"><span data-stu-id="24275-103">F# component design guidelines</span></span>

<span data-ttu-id="24275-104">這份文件是一組元件的設計方針 F # 程式，並根據 F # 元件設計指導方針，v14，Microsoft 研究和[另一個版本](https://fsharp.org/specs/component-design-guidelines/)原來 curated 和 F # Software Foundation 所維護。</span><span class="sxs-lookup"><span data-stu-id="24275-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and [another version](https://fsharp.org/specs/component-design-guidelines/) originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="24275-105">本文件假設您熟悉以 F # 的程式設計。</span><span class="sxs-lookup"><span data-stu-id="24275-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="24275-106">非常感謝 F # 社群的參與，很有幫助的意見反應，本指南的各種版本上。</span><span class="sxs-lookup"><span data-stu-id="24275-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="24275-107">總覽</span><span class="sxs-lookup"><span data-stu-id="24275-107">Overview</span></span>

<span data-ttu-id="24275-108">本文件探討某些與 F # 元件設計和編碼相關的問題。</span><span class="sxs-lookup"><span data-stu-id="24275-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="24275-109">元件可能表示下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="24275-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="24275-110">F # 專案中有該專案內外部的取用者層。</span><span class="sxs-lookup"><span data-stu-id="24275-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="24275-111">跨組件界限提供給耗用量 F # 程式碼程式庫。</span><span class="sxs-lookup"><span data-stu-id="24275-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="24275-112">預定由任何.NET 語言跨組件界限文件庫。</span><span class="sxs-lookup"><span data-stu-id="24275-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="24275-113">例如適用於散發的封裝儲存機制，透過文件庫[NuGet](https://nuget.org)。</span><span class="sxs-lookup"><span data-stu-id="24275-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="24275-114">請遵循本文中所述的技巧[良好的 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)，因此利用兩者功能，以及適當地進行程式設計的物件。</span><span class="sxs-lookup"><span data-stu-id="24275-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="24275-115">在方法中，不論元件和程式庫的設計工具時嘗試製作最容易供開發人員的 API 面實際且 prosaic 問題數目。</span><span class="sxs-lookup"><span data-stu-id="24275-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="24275-116">暴增的應用程式的[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)操縱您建立一致的整套愉快取用的 Api。</span><span class="sxs-lookup"><span data-stu-id="24275-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="24275-117">一般方針</span><span class="sxs-lookup"><span data-stu-id="24275-117">General guidelines</span></span>

<span data-ttu-id="24275-118">有幾個通用的指導方針適用於 F # 程式庫，不論程式庫的目標對象。</span><span class="sxs-lookup"><span data-stu-id="24275-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="24275-119">了解.NET 程式庫設計指導方針</span><span class="sxs-lookup"><span data-stu-id="24275-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="24275-120">F # 程式碼撰寫您所執行的類型，不論是非常有用的具備的實用知識[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="24275-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="24275-121">大多數其他 F # 和.NET 程式設計人員會熟悉下列指導方針，並預期以符合它們的.NET 程式碼。</span><span class="sxs-lookup"><span data-stu-id="24275-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="24275-122">.NET 程式庫設計指導方針提供一般指引命名、 設計類別和介面、 成員設計 （屬性、 方法、 事件等） 和詳細資訊，而且很有用的各種不同的設計指導方針的參考第一個點。</span><span class="sxs-lookup"><span data-stu-id="24275-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="24275-123">將 XML 文件註解加入至您的程式碼</span><span class="sxs-lookup"><span data-stu-id="24275-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="24275-124">XML 文件的公用 Api 上可確保使用者可以取得很好的 Intellisense 和 Quickinfo 時使用這些型別和成員，以及啟用建置文件庫的檔案。</span><span class="sxs-lookup"><span data-stu-id="24275-124">XML documentation on public APIs ensure that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="24275-125">請參閱[XML 文件](../language-reference/xml-documentation.md)各種可用於 xmldoc 註解內其他標記的 xml 標記的資訊。</span><span class="sxs-lookup"><span data-stu-id="24275-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo : otherPoint:Point -> float
```

<span data-ttu-id="24275-126">您可以使用任一的簡短形式 XML 註解 (`/// comment`)，或標準 XML 註解 (`///<summary>comment</summary>`)。</span><span class="sxs-lookup"><span data-stu-id="24275-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="24275-127">請考慮使用明確的簽章檔案 (.fsi) 穩定的程式庫和應用程式開發介面的元件</span><span class="sxs-lookup"><span data-stu-id="24275-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="24275-128">使用 F # 程式庫中的明確的簽章檔案提供公用 API，但是這兩個可協助確保您知道您的媒體櫃的完整公用介面以及提供清楚的分隔之間公用文件和內部簡潔的摘要實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="24275-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which both helps to ensure that you know the full public surface of your library, as well as provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="24275-129">請注意，簽章新增檔案人事變更公用 API 中，需要在實作和簽章檔案中進行的變更。</span><span class="sxs-lookup"><span data-stu-id="24275-129">Note that signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="24275-130">如此一來，簽章檔案應該通常只會引進當應用程式開發介面已經成為目的並不會再預期會有重大變更。</span><span class="sxs-lookup"><span data-stu-id="24275-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="24275-131">永遠會接在.NET 中使用字串的最佳作法</span><span class="sxs-lookup"><span data-stu-id="24275-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="24275-132">請遵循[在.NET 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md)指引。</span><span class="sxs-lookup"><span data-stu-id="24275-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="24275-133">特別是，一律明確地陳述*文化特性的意圖*中的轉換和字串的比較 （如果適用的話）。</span><span class="sxs-lookup"><span data-stu-id="24275-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="24275-134">F # 的指導方針-對向程式庫</span><span class="sxs-lookup"><span data-stu-id="24275-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="24275-135">本節提供的建議用於開發公用 F #-對向程式庫。亦即，公開要供 F # 開發人員的公用 Api 的程式庫。</span><span class="sxs-lookup"><span data-stu-id="24275-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="24275-136">沒有為 F # 適用的各種不同的程式庫設計建議。</span><span class="sxs-lookup"><span data-stu-id="24275-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="24275-137">如果沒有遵循特定建議，.NET 程式庫設計指導方針是後援的指引。</span><span class="sxs-lookup"><span data-stu-id="24275-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="24275-138">命名規範</span><span class="sxs-lookup"><span data-stu-id="24275-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="24275-139">使用.NET 命名和大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="24275-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="24275-140">下表依照.NET 命名和大小寫慣例。</span><span class="sxs-lookup"><span data-stu-id="24275-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="24275-141">有小新增項目也包含 F # 建構。</span><span class="sxs-lookup"><span data-stu-id="24275-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="24275-142">建構</span><span class="sxs-lookup"><span data-stu-id="24275-142">Construct</span></span> | <span data-ttu-id="24275-143">案例</span><span class="sxs-lookup"><span data-stu-id="24275-143">Case</span></span> | <span data-ttu-id="24275-144">組件</span><span class="sxs-lookup"><span data-stu-id="24275-144">Part</span></span> | <span data-ttu-id="24275-145">範例</span><span class="sxs-lookup"><span data-stu-id="24275-145">Examples</span></span> | <span data-ttu-id="24275-146">注意</span><span class="sxs-lookup"><span data-stu-id="24275-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="24275-147">具象型別</span><span class="sxs-lookup"><span data-stu-id="24275-147">Concrete types</span></span> | <span data-ttu-id="24275-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-148">PascalCase</span></span> | <span data-ttu-id="24275-149">名詞 / 形容詞</span><span class="sxs-lookup"><span data-stu-id="24275-149">Noun/ adjective</span></span> | <span data-ttu-id="24275-150">清單中，Double，複雜</span><span class="sxs-lookup"><span data-stu-id="24275-150">List, Double, Complex</span></span> | <span data-ttu-id="24275-151">具象型別是結構、 類別、 列舉型別、 委派、 記錄、 和等位。</span><span class="sxs-lookup"><span data-stu-id="24275-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="24275-152">雖然型別名稱是 OCaml 在過去是小寫，F # 已採用類型的.NET 命名配置。</span><span class="sxs-lookup"><span data-stu-id="24275-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="24275-153">DLL</span><span class="sxs-lookup"><span data-stu-id="24275-153">DLLs</span></span>           | <span data-ttu-id="24275-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-154">PascalCase</span></span> |                 | <span data-ttu-id="24275-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="24275-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="24275-156">等位標記</span><span class="sxs-lookup"><span data-stu-id="24275-156">Union tags</span></span>     | <span data-ttu-id="24275-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-157">PascalCase</span></span> | <span data-ttu-id="24275-158">名詞</span><span class="sxs-lookup"><span data-stu-id="24275-158">Noun</span></span> | <span data-ttu-id="24275-159">部分新增成功</span><span class="sxs-lookup"><span data-stu-id="24275-159">Some, Add, Success</span></span> | <span data-ttu-id="24275-160">請勿在公用 Api 中使用前置詞。</span><span class="sxs-lookup"><span data-stu-id="24275-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="24275-161">（選擇性） 使用的前置詞時內部，例如 '' 輸入小組 = TAlpha</span><span class="sxs-lookup"><span data-stu-id="24275-161">Optionally use a prefix when internal, such as \`\`\`type Teams = TAlpha</span></span> | <span data-ttu-id="24275-162">TBeta</span><span class="sxs-lookup"><span data-stu-id="24275-162">TBeta</span></span> | <span data-ttu-id="24275-163">TDelta。 ' '</span><span class="sxs-lookup"><span data-stu-id="24275-163">TDelta.\`\`\`</span></span> |
| <span data-ttu-id="24275-164">Event - 事件</span><span class="sxs-lookup"><span data-stu-id="24275-164">Event</span></span>          | <span data-ttu-id="24275-165">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-165">PascalCase</span></span> | <span data-ttu-id="24275-166">動詞命令</span><span class="sxs-lookup"><span data-stu-id="24275-166">Verb</span></span> | <span data-ttu-id="24275-167">ValueChanged / ValueChanging</span><span class="sxs-lookup"><span data-stu-id="24275-167">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="24275-168">例外狀況</span><span class="sxs-lookup"><span data-stu-id="24275-168">Exceptions</span></span>     | <span data-ttu-id="24275-169">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-169">PascalCase</span></span> |      | <span data-ttu-id="24275-170">WebException</span><span class="sxs-lookup"><span data-stu-id="24275-170">WebException</span></span> | <span data-ttu-id="24275-171">名稱應該以"Exception"為結尾。</span><span class="sxs-lookup"><span data-stu-id="24275-171">Name should end with “Exception”.</span></span> |
| <span data-ttu-id="24275-172">欄位</span><span class="sxs-lookup"><span data-stu-id="24275-172">Field</span></span>          | <span data-ttu-id="24275-173">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-173">PascalCase</span></span> | <span data-ttu-id="24275-174">名詞</span><span class="sxs-lookup"><span data-stu-id="24275-174">Noun</span></span> | <span data-ttu-id="24275-175">CurrentName</span><span class="sxs-lookup"><span data-stu-id="24275-175">CurrentName</span></span>  | |
| <span data-ttu-id="24275-176">介面型別</span><span class="sxs-lookup"><span data-stu-id="24275-176">Interface types</span></span> |  <span data-ttu-id="24275-177">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-177">PascalCase</span></span> | <span data-ttu-id="24275-178">名詞 / 形容詞</span><span class="sxs-lookup"><span data-stu-id="24275-178">Noun/ adjective</span></span> | <span data-ttu-id="24275-179">IDisposable</span><span class="sxs-lookup"><span data-stu-id="24275-179">IDisposable</span></span> | <span data-ttu-id="24275-180">名稱應該以"I"開頭。</span><span class="sxs-lookup"><span data-stu-id="24275-180">Name should start with “I”.</span></span> |
| <span data-ttu-id="24275-181">方法</span><span class="sxs-lookup"><span data-stu-id="24275-181">Method</span></span> |  <span data-ttu-id="24275-182">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-182">PascalCase</span></span> |  <span data-ttu-id="24275-183">動詞命令</span><span class="sxs-lookup"><span data-stu-id="24275-183">Verb</span></span> | <span data-ttu-id="24275-184">ToString</span><span class="sxs-lookup"><span data-stu-id="24275-184">ToString</span></span> | |
| <span data-ttu-id="24275-185">命名空間</span><span class="sxs-lookup"><span data-stu-id="24275-185">Namespace</span></span> | <span data-ttu-id="24275-186">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-186">PascalCase</span></span> | | <span data-ttu-id="24275-187">Microsoft.FSharp.Core</span><span class="sxs-lookup"><span data-stu-id="24275-187">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="24275-188">通常使用`<Organization>.<Technology>[.<Subnamespace>]`，不過卸除組織，如果組織的技術無關。</span><span class="sxs-lookup"><span data-stu-id="24275-188">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="24275-189">參數</span><span class="sxs-lookup"><span data-stu-id="24275-189">Parameters</span></span> | <span data-ttu-id="24275-190">camelCase</span><span class="sxs-lookup"><span data-stu-id="24275-190">camelCase</span></span> | <span data-ttu-id="24275-191">名詞</span><span class="sxs-lookup"><span data-stu-id="24275-191">Noun</span></span> |  <span data-ttu-id="24275-192">類型名稱、 轉換、 範圍</span><span class="sxs-lookup"><span data-stu-id="24275-192">typeName, transform, range</span></span> | |
| <span data-ttu-id="24275-193">讓值 （內部）</span><span class="sxs-lookup"><span data-stu-id="24275-193">let values (internal)</span></span> | <span data-ttu-id="24275-194">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-194">camelCase or PascalCase</span></span> | <span data-ttu-id="24275-195">名詞 / 動詞命令</span><span class="sxs-lookup"><span data-stu-id="24275-195">Noun/ verb</span></span> |  <span data-ttu-id="24275-196">getValue myTable</span><span class="sxs-lookup"><span data-stu-id="24275-196">getValue, myTable</span></span> |
| <span data-ttu-id="24275-197">讓值 （外部）</span><span class="sxs-lookup"><span data-stu-id="24275-197">let values (external)</span></span> | <span data-ttu-id="24275-198">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-198">camelCase or PascalCase</span></span> | <span data-ttu-id="24275-199">名詞/動詞命令</span><span class="sxs-lookup"><span data-stu-id="24275-199">Noun/verb</span></span>  | <span data-ttu-id="24275-200">List.map Dates.Today</span><span class="sxs-lookup"><span data-stu-id="24275-200">List.map, Dates.Today</span></span> | <span data-ttu-id="24275-201">let 繫結值通常是公用的遵循傳統功能的設計模式時。</span><span class="sxs-lookup"><span data-stu-id="24275-201">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="24275-202">不過，通常使用 PascalCase 時可以從其他.NET 語言使用的識別項。</span><span class="sxs-lookup"><span data-stu-id="24275-202">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="24275-203">屬性</span><span class="sxs-lookup"><span data-stu-id="24275-203">Property</span></span>  | <span data-ttu-id="24275-204">PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-204">PascalCase</span></span>  | <span data-ttu-id="24275-205">名詞 / 形容詞</span><span class="sxs-lookup"><span data-stu-id="24275-205">Noun/ adjective</span></span>  | <span data-ttu-id="24275-206">IsEndOfFile，背景色彩</span><span class="sxs-lookup"><span data-stu-id="24275-206">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="24275-207">布林值屬性通常不使用，因為可以而且應該是肯定的如 IsEndOfFile，不 IsNotEndOfFile 所示。</span><span class="sxs-lookup"><span data-stu-id="24275-207">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="24275-208">避免縮寫</span><span class="sxs-lookup"><span data-stu-id="24275-208">Avoid abbreviations</span></span>

<span data-ttu-id="24275-209">.NET 方針不鼓勵使用縮寫 (例如，「 使用`OnButtonClick`而不是`OnBtnClick`")。</span><span class="sxs-lookup"><span data-stu-id="24275-209">The .NET guidelines discourage the use of abbreviations (for example, “use `OnButtonClick` rather than `OnBtnClick`”).</span></span> <span data-ttu-id="24275-210">常用的縮寫，例如`Async`的 「 非同步 」，所容許之。</span><span class="sxs-lookup"><span data-stu-id="24275-210">Common abbreviations, such as `Async` for “Asynchronous”, are tolerated.</span></span> <span data-ttu-id="24275-211">功能性程式設計，有時會忽略這項指導方針例如，`List.iter`用於 「 重複 」 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="24275-211">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for “iterate”.</span></span> <span data-ttu-id="24275-212">基於這個理由，使用縮寫通常會在 F # 中儘可容許-到-F # 的程式設計，但仍通常應該避免在公用元件的設計。</span><span class="sxs-lookup"><span data-stu-id="24275-212">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="24275-213">避免發生名稱衝突的大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="24275-213">Avoid casing name collisions</span></span>

<span data-ttu-id="24275-214">.NET 指導方針會假設，單獨的大小寫慣例不能用來區分名稱發生衝突，因為某些用戶端語言 (例如，Visual Basic) 皆不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="24275-214">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="24275-215">在適當時使用首字母縮略字</span><span class="sxs-lookup"><span data-stu-id="24275-215">Use acronyms where appropriate</span></span>

<span data-ttu-id="24275-216">首字母縮略字，例如 XML 不縮寫，且都廣泛利用 uncapitalized 格式 (Xml) 的.NET 程式庫中。</span><span class="sxs-lookup"><span data-stu-id="24275-216">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="24275-217">只應該使用廣為人知且知名首字母縮略字。</span><span class="sxs-lookup"><span data-stu-id="24275-217">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="24275-218">泛型參數名稱使用 PascalCase</span><span class="sxs-lookup"><span data-stu-id="24275-218">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="24275-219">不要在公用 Api，包括 F # 的泛型參數名稱使用 PascalCase-對向程式庫。</span><span class="sxs-lookup"><span data-stu-id="24275-219">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="24275-220">特別是，使用名稱`T`， `U`， `T1`，`T2`任意的泛型參數，以及特定名稱有意義，然後 F #-向程式庫會使用名稱`Key`， `Value`， `Arg`(但不是例如`TKey`)。</span><span class="sxs-lookup"><span data-stu-id="24275-220">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="24275-221">使用 PascalCase 或 camelCase 公用函式和 F # 模組中的值</span><span class="sxs-lookup"><span data-stu-id="24275-221">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="24275-222">camelCase 用於設計用於的公用函式不合格 (例如， `invalidArg`)，以及 < 標準集合函數 > （例如 List.map）。</span><span class="sxs-lookup"><span data-stu-id="24275-222">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the “standard collection functions” (for example, List.map).</span></span> <span data-ttu-id="24275-223">在這兩個這些情況下，函式名稱像是多語言中關鍵字。</span><span class="sxs-lookup"><span data-stu-id="24275-223">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="24275-224">物件、 類型和模組的設計</span><span class="sxs-lookup"><span data-stu-id="24275-224">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="24275-225">使用命名空間或模組來包含您的類型和模組</span><span class="sxs-lookup"><span data-stu-id="24275-225">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="24275-226">在元件中的每個 F # 檔案應該以命名空間宣告或模組宣告開頭。</span><span class="sxs-lookup"><span data-stu-id="24275-226">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="24275-227">或</span><span class="sxs-lookup"><span data-stu-id="24275-227">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="24275-228">使用模組和命名空間來組織最上層的程式碼之間的差異如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-228">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="24275-229">命名空間可以跨越多個檔案</span><span class="sxs-lookup"><span data-stu-id="24275-229">Namespaces can span multiple files</span></span>
* <span data-ttu-id="24275-230">命名空間不能包含 F # 函式，除非它們是在內部的模組中</span><span class="sxs-lookup"><span data-stu-id="24275-230">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="24275-231">任何給定的模組的程式碼必須包含在單一檔案</span><span class="sxs-lookup"><span data-stu-id="24275-231">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="24275-232">最上層的模組可以包含 F # 函式，而不需要內部的模組</span><span class="sxs-lookup"><span data-stu-id="24275-232">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="24275-233">最上層命名空間或模組之間選擇會影響程式碼的編譯的形式，並因此將會影響其他.NET 語言檢視應該您的 API 最終取用外部 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="24275-233">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="24275-234">使用內建的物件類型的作業的方法和屬性</span><span class="sxs-lookup"><span data-stu-id="24275-234">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="24275-235">當處理物件，所以最好先確保您可以使用的功能會實作為該類型的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="24275-235">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="24275-236">大量的功能，為給定成員需要一定中實作該成員，但應該是您可以使用該功能部分。</span><span class="sxs-lookup"><span data-stu-id="24275-236">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="24275-237">使用類別來封裝可變狀態</span><span class="sxs-lookup"><span data-stu-id="24275-237">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="24275-238">在 F # 中，這只需要進行其中狀態不已封裝的另一個語言建構，例如關閉、 序列運算式中或非同步的計算。</span><span class="sxs-lookup"><span data-stu-id="24275-238">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="24275-239">使用介面來群組相關的作業</span><span class="sxs-lookup"><span data-stu-id="24275-239">Use interfaces to group related operations</span></span>

<span data-ttu-id="24275-240">您可以使用介面型別來代表一組作業。</span><span class="sxs-lookup"><span data-stu-id="24275-240">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="24275-241">這是慣用和其他選項，例如 tuple 的函式或函式的記錄。</span><span class="sxs-lookup"><span data-stu-id="24275-241">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="24275-242">優先以：</span><span class="sxs-lookup"><span data-stu-id="24275-242">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize : bool -> 'T -> string
    Deserialize : bool -> string -> 'T
}
```

<span data-ttu-id="24275-243">介面是在.NET 中，您可用來達成什麼函式通常五月，第一級的概念。</span><span class="sxs-lookup"><span data-stu-id="24275-243">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="24275-244">此外，它們可以用來編碼至您程式中，記錄的函式不能存在的類型。</span><span class="sxs-lookup"><span data-stu-id="24275-244">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-which-act-on-collections"></a><span data-ttu-id="24275-245">使用要處理的群組函式的模組集合</span><span class="sxs-lookup"><span data-stu-id="24275-245">Use a module to group functions which act on collections</span></span>

<span data-ttu-id="24275-246">當您定義集合型別時，請考慮提供一組標準的作業類似`CollectionType.map`和`CollectionType.iter`) 對於新的集合類型。</span><span class="sxs-lookup"><span data-stu-id="24275-246">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="24275-247">如果您包含這類模組，請遵循 FSharp.Core 中找到的函式的標準命名慣例。</span><span class="sxs-lookup"><span data-stu-id="24275-247">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="24275-248">使用適用於通用的標準函式，尤其是在數學和 DSL 程式庫群組函式模組</span><span class="sxs-lookup"><span data-stu-id="24275-248">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="24275-249">例如，`Microsoft.FSharp.Core.Operators`是自動開啟最上層函式的集合 (例如`abs`和`sin`) FSharp.Core.dll 所提供。</span><span class="sxs-lookup"><span data-stu-id="24275-249">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="24275-250">同樣地，統計資料的程式庫可能包含具有函式的模組`erf`和`erfc`、 此模組為了明確或自動開啟。</span><span class="sxs-lookup"><span data-stu-id="24275-250">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="24275-251">請考慮使用 RequireQualifiedAccess 並仔細套用 AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="24275-251">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="24275-252">加入`[<RequireQualifiedAccess>]`模組的屬性表示模組可能未開啟，而且參考的模組項目需要明確限定存取。</span><span class="sxs-lookup"><span data-stu-id="24275-252">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="24275-253">例如，`Microsoft.FSharp.Collections.List`模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="24275-253">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="24275-254">當函式和模組中的值有可能會與其他模組中的名稱發生衝突的名稱，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="24275-254">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="24275-255">需要完整存取權可以大幅增加長期的可維護性和 evolvability 的文件庫。</span><span class="sxs-lookup"><span data-stu-id="24275-255">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="24275-256">加入`[<AutoOpen>]`模組的屬性表示開啟包含命名空間時，就會開啟模組。</span><span class="sxs-lookup"><span data-stu-id="24275-256">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="24275-257">`[<AutoOpen>]`屬性可能也會套用到組件，表示參考組件時就會自動開啟模組。</span><span class="sxs-lookup"><span data-stu-id="24275-257">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="24275-258">例如，統計資料的程式庫**MathsHeaven.Statistics**可能包含`module MathsHeaven.Statistics.Operators`含有函式`erf`和`erfc`。</span><span class="sxs-lookup"><span data-stu-id="24275-258">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="24275-259">它可合理地標示為此模組`[<AutoOpen>]`。</span><span class="sxs-lookup"><span data-stu-id="24275-259">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="24275-260">這表示`open MathsHeaven.Statistics`也會開啟此模組並將名稱`erf`和`erfc`納入範圍。</span><span class="sxs-lookup"><span data-stu-id="24275-260">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="24275-261">使用另一個良好`[<AutoOpen>]`為包含擴充方法的模組。</span><span class="sxs-lookup"><span data-stu-id="24275-261">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="24275-262">過度使用的`[<AutoOpen>]`污染的命名空間和屬性將導致應小心使用。</span><span class="sxs-lookup"><span data-stu-id="24275-262">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="24275-263">針對特定的文件庫中特定網域，明智地使用`[<AutoOpen>]`可能會導致更好的可用性。</span><span class="sxs-lookup"><span data-stu-id="24275-263">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="24275-264">請考慮在則適合使用已知的運算子的類別上定義運算子成員</span><span class="sxs-lookup"><span data-stu-id="24275-264">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="24275-265">有時候類別可用來建立模型數學建構，例如向量。</span><span class="sxs-lookup"><span data-stu-id="24275-265">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="24275-266">正在模型化的網域有已知的運算子，定義為 「 內建函式類別的成員時很有幫助。</span><span class="sxs-lookup"><span data-stu-id="24275-266">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x:float) =

    member v.X = x

    static member (*) (vector:Vector, scalar:float) = Vector(vector.X * scalar)

    static member (+) (vector1:Vector, vector2:Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="24275-267">本指南會對應至這些類型的一般.NET 指引。</span><span class="sxs-lookup"><span data-stu-id="24275-267">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="24275-268">不過，它可能在 F # 程式碼撰寫這可讓這些型別，以用於搭配 F # 函式和方法的成員條件約束，例如 List.sumBy 此外重要。</span><span class="sxs-lookup"><span data-stu-id="24275-268">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="24275-269">請考慮使用 CompiledName 提供。其他.NET 語言取用者的的網路的易記名稱</span><span class="sxs-lookup"><span data-stu-id="24275-269">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="24275-270">有時候您可能想要的 F # 消費者命名樣式中的項目 (例如大小寫，使它顯示在靜態成員就好像模組繫結函式)，但它編譯的組件時，有不同的樣式名稱。</span><span class="sxs-lookup"><span data-stu-id="24275-270">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="24275-271">您可以使用`[<CompiledName>]`非 F # 程式碼使用組件提供不同的樣式屬性。</span><span class="sxs-lookup"><span data-stu-id="24275-271">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="24275-272">使用`[<CompiledName>]`，您可以使用非 F # 組件的取用者的.NET 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="24275-272">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="24275-273">使用方法多載成員函式，如果這麼做可以提供更簡單的應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="24275-273">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="24275-274">方法多載是功能強大的工具，以簡化的 API，可能需要執行類似的功能，不過多了不同的選項或引數。</span><span class="sxs-lookup"><span data-stu-id="24275-274">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="24275-275">在 F # 中，是較常見的引數數目，而不是引數型別多載。</span><span class="sxs-lookup"><span data-stu-id="24275-275">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="24275-276">隱藏記錄和等位型別的表示，如果這些型別的設計可能發展</span><span class="sxs-lookup"><span data-stu-id="24275-276">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="24275-277">避免洩露之物件的實體表示。</span><span class="sxs-lookup"><span data-stu-id="24275-277">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="24275-278">例如的具象表示<xref:System.DateTime>值不會由外部的公用 API 的.NET 程式庫設計。</span><span class="sxs-lookup"><span data-stu-id="24275-278">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="24275-279">在執行階段，Common Language Runtime 知道認可將在整個執行的實作。</span><span class="sxs-lookup"><span data-stu-id="24275-279">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="24275-280">不過，已編譯程式碼不本身挑選的相依性的具象表示法。</span><span class="sxs-lookup"><span data-stu-id="24275-280">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="24275-281">避免使用實作繼承的擴充性</span><span class="sxs-lookup"><span data-stu-id="24275-281">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="24275-282">在 F # 中，很少使用實作繼承。</span><span class="sxs-lookup"><span data-stu-id="24275-282">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="24275-283">此外，繼承階層架構通常是很複雜而難以變更的新要求到達時。</span><span class="sxs-lookup"><span data-stu-id="24275-283">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="24275-284">繼承實作仍然在 F # 的相容性和罕見的情況下，它很最佳解決方案，會造成問題，但設計多型，例如介面實作時，應該在 F # 程式中尋找的替代技術。</span><span class="sxs-lookup"><span data-stu-id="24275-284">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="24275-285">函式和成員的簽章</span><span class="sxs-lookup"><span data-stu-id="24275-285">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="24275-286">傳回少量的多個不相關的值時，使用 tuple 的傳回值</span><span class="sxs-lookup"><span data-stu-id="24275-286">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="24275-287">以下是使用 tuple，傳回型別中的理想範例：</span><span class="sxs-lookup"><span data-stu-id="24275-287">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem : BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="24275-288">傳回型別包含許多元件，或單一識別實體相關的元件，請考慮使用具名型別，而不 tuple。</span><span class="sxs-lookup"><span data-stu-id="24275-288">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="24275-289">使用`Async<T>`進行非同步程式設計，F # 應用程式開發介面界限</span><span class="sxs-lookup"><span data-stu-id="24275-289">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="24275-290">如果沒有對應的同步作業，名為`Operation`傳回`T`，非同步處理作業應該命名為`AsyncOperation`如果它傳回`Async<T>`或`OperationAsync`如果它傳回`Task<T>`。</span><span class="sxs-lookup"><span data-stu-id="24275-290">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="24275-291">常用的.NET 型別公開 Begin/End 方法，請請考慮使用`Async.FromBeginEnd`為外觀提供 F # 非同步程式設計模型的.NET Api 來撰寫擴充方法。</span><span class="sxs-lookup"><span data-stu-id="24275-291">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

```fsharp
type SomeType =
    member this.Compute(x:int) : int =
        ...
    member this.AsyncCompute(x:int) : Async<int> =
        ...

type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        ...
```

### <a name="exceptions"></a><span data-ttu-id="24275-292">例外狀況</span><span class="sxs-lookup"><span data-stu-id="24275-292">Exceptions</span></span>

<span data-ttu-id="24275-293">例外狀況是在.NET; 例外狀況也就是說，它們不應該進行經常在執行階段。</span><span class="sxs-lookup"><span data-stu-id="24275-293">Exceptions are exceptional in .NET; that is, they should not occur frequently at runtime.</span></span> <span data-ttu-id="24275-294">這樣做，所包含的資訊時，有價值。</span><span class="sxs-lookup"><span data-stu-id="24275-294">When they do, the information they contain is valuable.</span></span> <span data-ttu-id="24275-295">例外狀況是核心的第一個類別的.NET; 概念it 因此一部分的元件介面的設計應該使用適當的應用程式的例外狀況，如下所示。</span><span class="sxs-lookup"><span data-stu-id="24275-295">Exceptions are a core first class concept of .NET; it hence follows that appropriate application of the Exceptions should be used as part of the design of the interface of a component.</span></span>

#### <a name="follow-the-net-guidelines-for-exceptions"></a><span data-ttu-id="24275-296">請遵循例外狀況的.NET 方針</span><span class="sxs-lookup"><span data-stu-id="24275-296">Follow the .NET guidelines for exceptions</span></span>

<span data-ttu-id="24275-297">[.NET 程式庫設計方針](../../standard/design-guidelines/exceptions.md)提供絕佳的建議使用的所有.NET 程式設計內容中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24275-297">The [.NET Library Design Guidelines](../../standard/design-guidelines/exceptions.md) give excellent advice on the use of exceptions in the context of all .NET programming.</span></span> <span data-ttu-id="24275-298">部分這些指導方針如下：</span><span class="sxs-lookup"><span data-stu-id="24275-298">Some of these guidelines are as follows:</span></span>

* <span data-ttu-id="24275-299">請勿用於一般控制流程的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24275-299">Do not use exceptions for normal flow of control.</span></span> <span data-ttu-id="24275-300">雖然這項技術通常用於 OCaml 等語言，它會是容易發生錯誤的而且可以是.net 效率不佳。</span><span class="sxs-lookup"><span data-stu-id="24275-300">Although this technique is often used in languages such as OCaml, it is bug-prone and can be inefficient on .NET.</span></span> <span data-ttu-id="24275-301">相反地，請考慮傳回`None`選項值，指出是一般或預期執行一次失敗。</span><span class="sxs-lookup"><span data-stu-id="24275-301">Instead, consider returning a `None` option value to indicate a failure that is a common or expected occurrence.</span></span>

* <span data-ttu-id="24275-302">文件時未正確使用函式的元件擲回的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24275-302">Document exceptions thrown by your components when a function is used incorrectly.</span></span>

* <span data-ttu-id="24275-303">可能的話，會採用現有系統的命名空間中的例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24275-303">Where possible, employ existing exceptions from the System namespaces.</span></span> <span data-ttu-id="24275-304">避免<xref:System.ApplicationException>，但是。</span><span class="sxs-lookup"><span data-stu-id="24275-304">Avoid <xref:System.ApplicationException>, though.</span></span>

* <span data-ttu-id="24275-305">未擲回<xref:System.Exception>時它將逸出，對使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="24275-305">Do not throw <xref:System.Exception> when it will escape to user code.</span></span> <span data-ttu-id="24275-306">這包括避免使用`failwith`， `failwithf`，這是很方便的函式用於指令碼和程式碼開發，但應該從 F # 程式庫程式碼改為擲回特定例外狀況類型中移除。</span><span class="sxs-lookup"><span data-stu-id="24275-306">This includes avoiding the use of `failwith`, `failwithf`, which are handy functions for use in scripting and for code under development, but should be removed from F# library code in favor of throwing a more specific exception type.</span></span>

* <span data-ttu-id="24275-307">使用`nullArg`， `invalidArg`，和`invalidOp`做為擲回的機制<xref:System.ArgumentNullException>， <xref:System.ArgumentException>，和<xref:System.InvalidOperationException>適當的時候。</span><span class="sxs-lookup"><span data-stu-id="24275-307">Use `nullArg`, `invalidArg`, and `invalidOp` as the mechanism to throw <xref:System.ArgumentNullException>, <xref:System.ArgumentException>, and <xref:System.InvalidOperationException> when appropriate.</span></span>

#### <a name="consider-using-option-values-for-return-types-when-failure-is-not-an-exceptional-scenario"></a><span data-ttu-id="24275-308">請考慮使用傳回型別選項的值時失敗不是例外狀況</span><span class="sxs-lookup"><span data-stu-id="24275-308">Consider using option values for return types when failure is not an exceptional scenario</span></span>

<span data-ttu-id="24275-309">例外狀況的.NET 方法是，它們應該是 「 例外 」;也就是說，它們應該進行相對較少。</span><span class="sxs-lookup"><span data-stu-id="24275-309">The .NET approach to exceptions is that they should be “exceptional”; that is, they should occur relatively infrequently.</span></span> <span data-ttu-id="24275-310">不過，某些作業 （例如，搜尋資料表） 可能會經常失敗。</span><span class="sxs-lookup"><span data-stu-id="24275-310">However, some operations (for example, searching a table) may fail frequently.</span></span> <span data-ttu-id="24275-311">F # 選項值是絕佳的方式來表示這些作業的傳回型別。</span><span class="sxs-lookup"><span data-stu-id="24275-311">F# option values are an excellent way to represent the return types of these operations.</span></span> <span data-ttu-id="24275-312">這些作業 signature 開頭的名稱前置詞"try":</span><span class="sxs-lookup"><span data-stu-id="24275-312">These operations conventionally start with the name prefix “try”:</span></span>

```fsharp
// bad: throws exception if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// bad: returns -1 if no element meets criteria
member this.FindFirstIndex(pred : 'T -> bool) : int =
    ...

// good: returns None if no element meets criteria
member this.TryFindFirstIndex(pred : 'T -> bool) : int option =
    ...
```

### <a name="extension-members"></a><span data-ttu-id="24275-313">擴充成員</span><span class="sxs-lookup"><span data-stu-id="24275-313">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="24275-314">請仔細套用 F # 擴充成員在 F #-到-F # 元件</span><span class="sxs-lookup"><span data-stu-id="24275-314">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="24275-315">F # 擴充成員通常只應位於與大部分的其模式的使用中的型別相關聯的內建作業的終止作業。</span><span class="sxs-lookup"><span data-stu-id="24275-315">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="24275-316">一個常見用途就是提供更慣用語 F # 各種不同的.NET 類型的 Api:</span><span class="sxs-lookup"><span data-stu-id="24275-316">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="24275-317">等位型別</span><span class="sxs-lookup"><span data-stu-id="24275-317">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="24275-318">使用差別聯的集而不是類別階層架構樹狀結構的資料</span><span class="sxs-lookup"><span data-stu-id="24275-318">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="24275-319">類似樹狀目錄結構是遞迴定義。</span><span class="sxs-lookup"><span data-stu-id="24275-319">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="24275-320">這是造成不便使用繼承，但精緻的差別等位。</span><span class="sxs-lookup"><span data-stu-id="24275-320">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="24275-321">代表類似樹狀目錄資料的差別等位也可讓您受益於 exhaustiveness 在模式比對。</span><span class="sxs-lookup"><span data-stu-id="24275-321">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="24275-322">使用`[<RequireQualifiedAccess>]`上其大小寫的名稱不是完全唯一的聯集類型</span><span class="sxs-lookup"><span data-stu-id="24275-322">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="24275-323">您可能會發現自己位於網域中相同名稱的不同事物，例如差別聯集的情況下最適當的名稱。</span><span class="sxs-lookup"><span data-stu-id="24275-323">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="24275-324">您可以使用`[<RequireQualifiedAccess>]`要區分大小寫的名稱以避免觸發遮蔽的排序相依的令人困惑錯誤`open`陳述式</span><span class="sxs-lookup"><span data-stu-id="24275-324">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="24275-325">如果這些型別的設計可能發展，隱藏差別聯集的表示如二進位相容的應用程式開發介面</span><span class="sxs-lookup"><span data-stu-id="24275-325">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="24275-326">等位型別依賴 F # 的模式比對的表單簡潔的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="24275-326">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="24275-327">如先前所述，您應該避免洩露具體資料表示法，如果這些型別的設計可能發展。</span><span class="sxs-lookup"><span data-stu-id="24275-327">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="24275-328">例如，差別聯集的表示法可以隱藏使用私用或內部宣告，或使用簽章檔案。</span><span class="sxs-lookup"><span data-stu-id="24275-328">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="24275-329">如果您隨意洩露差別聯的集，您可能會發現很難版本程式庫而不會中斷使用者程式碼。</span><span class="sxs-lookup"><span data-stu-id="24275-329">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="24275-330">相反地，請考慮提供一個或多個作用中的模式，以允許模式比對您的型別值。</span><span class="sxs-lookup"><span data-stu-id="24275-330">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="24275-331">作用中的模式提供的替代方式為 F # 取用者提供的模式比對，同時避免直接公開 F # 聯集類型。</span><span class="sxs-lookup"><span data-stu-id="24275-331">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="24275-332">內嵌函式和成員條件約束</span><span class="sxs-lookup"><span data-stu-id="24275-332">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="24275-333">定義泛型數值的演算法，以統計方式解析的泛型型別與隱含的成員條件約束中使用內嵌函式</span><span class="sxs-lookup"><span data-stu-id="24275-333">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="24275-334">算術成員條件約束和 F # 比較條件約束是標準的 F # 的程式設計。</span><span class="sxs-lookup"><span data-stu-id="24275-334">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="24275-335">例如，請參考下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="24275-335">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="24275-336">此函式的類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-336">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="24275-337">這是適合的函式中的數學程式庫的公用 api。</span><span class="sxs-lookup"><span data-stu-id="24275-337">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="24275-338">請避免使用以模擬型別類別和鴨子輸入成員條件約束</span><span class="sxs-lookup"><span data-stu-id="24275-338">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="24275-339">可以模擬"住輸入 」 使用 F # 成員條件約束。</span><span class="sxs-lookup"><span data-stu-id="24275-339">It is possible to simulate “duck typing” using F# member constraints.</span></span> <span data-ttu-id="24275-340">不過，可讓成員使用這個屬性應該不能在一般用於 F #-到-F # 程式庫設計。</span><span class="sxs-lookup"><span data-stu-id="24275-340">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="24275-341">這是因為不太熟悉或非標準的隱含條件約束為基礎的程式庫設計傾向於使使用者程式碼，使其成為卻往往缺乏彈性並繫結一個特定架構的模式。</span><span class="sxs-lookup"><span data-stu-id="24275-341">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="24275-342">此外，很可能會大量使用這種方式中的成員條件約束導致非常長的編譯時間。</span><span class="sxs-lookup"><span data-stu-id="24275-342">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="24275-343">運算子定義</span><span class="sxs-lookup"><span data-stu-id="24275-343">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="24275-344">應避免定義自訂的符號運算子</span><span class="sxs-lookup"><span data-stu-id="24275-344">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="24275-345">自訂運算子在某些情況下，而非常有用的影響力裝置在大型的主體內的實作程式碼。</span><span class="sxs-lookup"><span data-stu-id="24275-345">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="24275-346">文件庫的新使用者，具名函式通常是容易使用。</span><span class="sxs-lookup"><span data-stu-id="24275-346">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="24275-347">此外，自訂符號運算子就很難文件，而且使用者尋找更難查詢運算子，因為 IDE，並搜尋引擎中的現有限制的說明。</span><span class="sxs-lookup"><span data-stu-id="24275-347">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="24275-348">如此一來，所以最好來發行您的功能，為具名函式和成員，和此外公開運算子，這項功能才影響力的優點勝過文件集和認知讓它們的成本。</span><span class="sxs-lookup"><span data-stu-id="24275-348">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="24275-349">測量單位</span><span class="sxs-lookup"><span data-stu-id="24275-349">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="24275-350">謹慎使用 F # 程式碼中加入的類型安全的測量單位</span><span class="sxs-lookup"><span data-stu-id="24275-350">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="24275-351">檢視由其他.NET 語言時，會清除輸入的其他資訊的單位量值。</span><span class="sxs-lookup"><span data-stu-id="24275-351">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="24275-352">請注意，進行.NET 元件、 工具和反映會看到 san 單位類型。</span><span class="sxs-lookup"><span data-stu-id="24275-352">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="24275-353">例如，C# 取用者將會看見`float`而不是`float<kg>`。</span><span class="sxs-lookup"><span data-stu-id="24275-353">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="24275-354">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="24275-354">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="24275-355">請仔細來簡化 F # 程式碼中使用類型縮寫</span><span class="sxs-lookup"><span data-stu-id="24275-355">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="24275-356">.NET 元件、 工具和反映不會看到類型縮寫的名稱。</span><span class="sxs-lookup"><span data-stu-id="24275-356">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="24275-357">類型縮寫的重要使用方式也可以將出現越複雜，比它實際上是，這可能會感到困惑取用者的網域。</span><span class="sxs-lookup"><span data-stu-id="24275-357">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="24275-358">避免其成員和屬性應該在本質上不同所縮寫類型上的可用的公用類型的類型縮寫</span><span class="sxs-lookup"><span data-stu-id="24275-358">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="24275-359">在此情況下，所縮寫類型會顯示有關所定義的實際類型的表示法太多。</span><span class="sxs-lookup"><span data-stu-id="24275-359">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="24275-360">相反地，請考慮換行中的類別類型或單一案例差別等位的縮寫 （或重要效能時，請考慮使用結構型別包裝縮寫）。</span><span class="sxs-lookup"><span data-stu-id="24275-360">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="24275-361">例如，它會嘗試定義多重對應視為特殊案例的 F # 地圖，例如：</span><span class="sxs-lookup"><span data-stu-id="24275-361">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="24275-362">不過，這個類型上的邏輯點標記法作業不會在地圖上的作業相同 (比方說，是合理 lookup 運算子對應）。[索引鍵] 傳回空的清單，如果索引鍵不在字典中，而非引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="24275-362">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="24275-363">從其他.NET 語言使用的程式庫的指導方針</span><span class="sxs-lookup"><span data-stu-id="24275-363">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="24275-364">在設計為從其他.NET 語言使用的程式庫時，務必遵守[.NET 程式庫設計方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="24275-364">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="24275-365">在本文件中，這些程式庫會標示為香草.NET 程式庫，而不是 F #-面對使用 F # 的程式庫建構不受限制。</span><span class="sxs-lookup"><span data-stu-id="24275-365">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="24275-366">設計香草.NET 程式庫表示藉由減少使用 F # 提供熟悉且慣用語 Api 與.NET Framework 的其餘部分一致-公用 API 中的特定建構。</span><span class="sxs-lookup"><span data-stu-id="24275-366">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="24275-367">下列各節中說明的規則。</span><span class="sxs-lookup"><span data-stu-id="24275-367">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="24275-368">命名空間和類型的設計 （適用於從其他.NET 語言使用的程式庫）</span><span class="sxs-lookup"><span data-stu-id="24275-368">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="24275-369">套用至元件的公用 API 的.NET 命名慣例</span><span class="sxs-lookup"><span data-stu-id="24275-369">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="24275-370">請特別注意，可讓您使用縮寫的名稱和.NET 大小寫方針。</span><span class="sxs-lookup"><span data-stu-id="24275-370">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="24275-371">做為命名空間、 類型和成員的主要組織性結構為您的元件</span><span class="sxs-lookup"><span data-stu-id="24275-371">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="24275-372">包含公用的功能的所有檔案都開頭應該是`namespace`宣告和命名空間中公開的實體應該是型別。</span><span class="sxs-lookup"><span data-stu-id="24275-372">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="24275-373">請勿使用 F # 模組。</span><span class="sxs-lookup"><span data-stu-id="24275-373">Do not use F# modules.</span></span>

<span data-ttu-id="24275-374">使用非公用模組來保存實作程式碼、 公用程式類型和公用程式函式。</span><span class="sxs-lookup"><span data-stu-id="24275-374">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="24275-375">靜態類型應該是慣用的模組，透過它們允許使用多載和其他的.NET API 設計概念，不能使用 F # 模組內未來發展的 api。</span><span class="sxs-lookup"><span data-stu-id="24275-375">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="24275-376">例如，取代下列的公用 API:</span><span class="sxs-lookup"><span data-stu-id="24275-376">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="24275-377">請考慮改用：</span><span class="sxs-lookup"><span data-stu-id="24275-377">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="24275-378">如果類型的設計不會發展，在香草.NET 應用程式開發介面中使用 F # 記錄類型</span><span class="sxs-lookup"><span data-stu-id="24275-378">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="24275-379">F # 記錄類型編譯為一個簡單的.NET 類別。</span><span class="sxs-lookup"><span data-stu-id="24275-379">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="24275-380">這些是適用於應用程式開發介面中的某些簡單、 穩定 」 類型。</span><span class="sxs-lookup"><span data-stu-id="24275-380">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="24275-381">您應該考慮使用`[<NoEquality>]`和`[<NoComparison>]`屬性來隱藏自動產生的介面。</span><span class="sxs-lookup"><span data-stu-id="24275-381">You should consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="24275-382">也請避免使用香草.NET 應用程式開發介面中的可變動的資料錄欄位，這些會公開為公用的欄位。</span><span class="sxs-lookup"><span data-stu-id="24275-382">Also avoid using mutable record fields in vanilla .NET APIs as these exposes a public field.</span></span> <span data-ttu-id="24275-383">務必考慮是否類別會提供 API 的未來發展的更有彈性的選項。</span><span class="sxs-lookup"><span data-stu-id="24275-383">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="24275-384">例如，下列的 F # 程式碼會公開公用 API 的 C# 取用者：</span><span class="sxs-lookup"><span data-stu-id="24275-384">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="24275-385">F # 中：</span><span class="sxs-lookup"><span data-stu-id="24275-385">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing : int
        SecondThing : string }
```

<span data-ttu-id="24275-386">C#: </span><span class="sxs-lookup"><span data-stu-id="24275-386">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="24275-387">隱藏 F # 聯集類型的香草.NET 應用程式開發介面中的表示法</span><span class="sxs-lookup"><span data-stu-id="24275-387">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="24275-388">F # 等位型別不常用於跨元件界限，即使 F #-到-F # 程式碼撰寫。</span><span class="sxs-lookup"><span data-stu-id="24275-388">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="24275-389">它們是絕佳的實作裝置時的內部使用的元件和程式庫。</span><span class="sxs-lookup"><span data-stu-id="24275-389">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="24275-390">設計時香草.NET API，請考慮使用私用宣告或簽章檔案中隱藏聯集類型的表示法。</span><span class="sxs-lookup"><span data-stu-id="24275-390">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="24275-391">您可能也會擴充以提供所需的等位表示在內部使用與成員的類型。網路對向應用程式開發介面。</span><span class="sxs-lookup"><span data-stu-id="24275-391">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="24275-392">設計 GUI 和其他元件使用的架構設計模式</span><span class="sxs-lookup"><span data-stu-id="24275-392">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="24275-393">另外還有許多不同的架構在.NET 中，例如 WinForms、 WPF 和 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="24275-393">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="24275-394">如果您要設計這些架構中使用的元件，則應該使用針對每個命名和設計慣例。</span><span class="sxs-lookup"><span data-stu-id="24275-394">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="24275-395">例如，針對 WPF 程式設計，採用 WPF 設計模式，您要設計的類別。</span><span class="sxs-lookup"><span data-stu-id="24275-395">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="24275-396">在使用者介面的程式設計模型，使用 設計模式，例如事件與通知為基礎的集合，例如位於<xref:System.Collections.ObjectModel>。</span><span class="sxs-lookup"><span data-stu-id="24275-396">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="24275-397">物件和成員設計 （適用於從其他.NET 語言使用的程式庫）</span><span class="sxs-lookup"><span data-stu-id="24275-397">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="24275-398">使用 CLIEvent 屬性公開.NET 事件</span><span class="sxs-lookup"><span data-stu-id="24275-398">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="24275-399">建構`DelegateEvent`與特定的.NET 委派會採用物件的型別和`EventArgs`(而非`Event`，這只是使用`FSharpHandler`預設的型別)，讓事件發行在其他.NET 語言的熟悉方式。</span><span class="sxs-lookup"><span data-stu-id="24275-399">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

```fsharp
type MyBadType() =
    let myEv = new Event<int>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish

type MyEventArgs(x:int) =
    inherit System.EventArgs()
    member this.X = x

    /// A type in a component designed for use from other .NET languages
type MyGoodType() =
    let myEv = new DelegateEvent<EventHandler<MyEventArgs>>()

    [<CLIEvent>]
    member this.MyEvent = myEv.Publish
```

#### <a name="expose-asynchronous-operations-as-methods-which-return-net-tasks"></a><span data-ttu-id="24275-400">公開非同步作業，做為傳回.NET 工作的方法</span><span class="sxs-lookup"><span data-stu-id="24275-400">Expose asynchronous operations as methods which return .NET tasks</span></span>

<span data-ttu-id="24275-401">在.NET 中使用工作來表示使用中的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="24275-401">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="24275-402">工作處於較不撰寫 F # 比一般`Async<T>`物件，因為它們代表 「 執行 」 工作，並且不能執行的平行的組合，或其中隱藏取消信號，以及其他的傳播方式一起構成內容參數。</span><span class="sxs-lookup"><span data-stu-id="24275-402">Tasks are in general less compositional than F# `Async<T>` objects, since they represent “already executing” tasks and can’t be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="24275-403">不過，如果即使如此，傳回工作的方法就是.net 非同步程式設計的標準表示法。</span><span class="sxs-lookup"><span data-stu-id="24275-403">However, despite this, methods which return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int) : Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="24275-404">您會經常也想要接受明確的取消語彙基元：</span><span class="sxs-lookup"><span data-stu-id="24275-404">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x:int) : Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="24275-405">使用.NET 委派型別，而不是 F # 函式類型</span><span class="sxs-lookup"><span data-stu-id="24275-405">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="24275-406">以下 「 F # 函式類型 」 表示"箭號 」 型別想`int -> int`。</span><span class="sxs-lookup"><span data-stu-id="24275-406">Here “F# function types” mean “arrow” types like `int -> int`.</span></span>

<span data-ttu-id="24275-407">而不是下列項目：</span><span class="sxs-lookup"><span data-stu-id="24275-407">Instead of this:</span></span>

```fsharp
member this.Transform(f:int->int) =
    ...
```

<span data-ttu-id="24275-408">請執行：</span><span class="sxs-lookup"><span data-stu-id="24275-408">Do this:</span></span>

```fsharp
member this.Transform(f:Func<int,int>) =
    ...
```

<span data-ttu-id="24275-409">F # 函式類型會顯示為`class FSharpFunc<T,U>`其他.NET 語言，因此較不適合用於語言功能和工具了解委派類型。</span><span class="sxs-lookup"><span data-stu-id="24275-409">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understand delegate types.</span></span> <span data-ttu-id="24275-410">當製作目標為.NET Framework 3.5 或更新版本，較高順序方法`System.Func`和`System.Action`委派是右應用程式開發介面，可讓.NET 開發人員使用這些 Api 以低人事方式發行。</span><span class="sxs-lookup"><span data-stu-id="24275-410">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="24275-411">(系統定義的委派類型時以.NET Framework 2.0 為目標，會更受到限制，請考慮使用預先定義的委派類型，例如`System.Converter<T,U>`或定義特定的委派型別。)</span><span class="sxs-lookup"><span data-stu-id="24275-411">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="24275-412">翻轉一邊.NET 委派不是理所當然的 F #-對向程式庫 (請參閱下一節 F #-對向程式庫)。</span><span class="sxs-lookup"><span data-stu-id="24275-412">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="24275-413">如此一來，開發香草.NET 程式庫的高階方法時的一般實作策略，是以編寫所有使用 F # 函式類型的實作，並建立在實際的 F # 之上的精簡外觀為使用委派的公用 API實作。</span><span class="sxs-lookup"><span data-stu-id="24275-413">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="24275-414">使用 TryGetValue 模式，而不是傳回 F # 選項值，並優先使用方法多載採用 F # 選項值做為引數</span><span class="sxs-lookup"><span data-stu-id="24275-414">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="24275-415">常見的應用程式開發介面中的 F # 選項類型使用的模式是較佳的香草中實作.NET 應用程式開發介面使用標準.NET 設計的技術。</span><span class="sxs-lookup"><span data-stu-id="24275-415">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="24275-416">而不是傳回的 F # 選項值，請考慮使用 bool 的傳回型別加上"TryGetValue 」 模式與 out 參數。</span><span class="sxs-lookup"><span data-stu-id="24275-416">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="24275-417">而不使用 F # 選項值做為參數，請考慮使用方法多載或選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="24275-417">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

```fsharp
member this.ReturnOption() = Some 3

member this.ReturnBoolAndOut(outVal : byref<int>) =
    outVal <- 3
    true

member this.ParamOption(x : int, y : int option) =
    match y with
    | Some y2 -> x + y2
    | None -> x

member this.ParamOverload(x : int) = x

member this.ParamOverload(x : int, y : int) = x + y
```

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="24275-418">使用.NET 集合介面型別 IEnumerable\<T\>和\<索引鍵、 值\>參數和傳回值</span><span class="sxs-lookup"><span data-stu-id="24275-418">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="24275-419">避免使用的具象集合類型，例如.NET 陣列`T[]`，F # 類型`list<T>`，`Map<Key,Value>`和`Set<T>`，與.NET 的具象集合類型，例如`Dictionary<Key,Value>`。</span><span class="sxs-lookup"><span data-stu-id="24275-419">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="24275-420">.NET 程式庫設計方針有關於使用類似的各種集合類型的時機很好的建議`IEnumerable<T>`。</span><span class="sxs-lookup"><span data-stu-id="24275-420">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="24275-421">有些使用的陣列 (`T[]`) 是可接受在某些情況下，效能地面上。</span><span class="sxs-lookup"><span data-stu-id="24275-421">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="24275-422">請注意，特別是`seq<T>`是只 F # 的別名`IEnumerable<T>`，而因此 seq 通常是適當的型別香草.NET API。</span><span class="sxs-lookup"><span data-stu-id="24275-422">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="24275-423">而不是 F # 的清單：</span><span class="sxs-lookup"><span data-stu-id="24275-423">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names : string list) =
    ...
```

<span data-ttu-id="24275-424">使用 F # 順序：</span><span class="sxs-lookup"><span data-stu-id="24275-424">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names : seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="24275-425">做為唯一的方法的輸入類型使用的單位類型，定義零引數的方法，或做為唯一會傳回定義傳回 void 方法的型別</span><span class="sxs-lookup"><span data-stu-id="24275-425">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="24275-426">避免的單位類型的其他用途。</span><span class="sxs-lookup"><span data-stu-id="24275-426">Avoid other uses of the unit type.</span></span> <span data-ttu-id="24275-427">這些是很好的：</span><span class="sxs-lookup"><span data-stu-id="24275-427">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x : int) = ()
```

<span data-ttu-id="24275-428">這是不正確：</span><span class="sxs-lookup"><span data-stu-id="24275-428">This is bad:</span></span>

```fsharp
member this.WrongUnit( x:unit, z:int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="24275-429">檢查有 null 值香草.NET API 界限上</span><span class="sxs-lookup"><span data-stu-id="24275-429">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="24275-430">F # 實作程式碼通常會有較少的 null 值，因為不可變的設計模式，以及使用 F # 型別的 null 常值的限制。</span><span class="sxs-lookup"><span data-stu-id="24275-430">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="24275-431">其他.NET 語言通常會使用 null 做為值更頻繁。</span><span class="sxs-lookup"><span data-stu-id="24275-431">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="24275-432">因為這個緣故，F # 程式碼公開.NET API 的香草應該檢查應用程式開發介面緣 null 的參數，以及更深入流入 F # 實作程式碼時，防止這些值。</span><span class="sxs-lookup"><span data-stu-id="24275-432">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="24275-433">`isNull`函式或模式比對`null`模式可用。</span><span class="sxs-lookup"><span data-stu-id="24275-433">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="24275-434">請避免使用 tuple 做為傳回值</span><span class="sxs-lookup"><span data-stu-id="24275-434">Avoid using tuples as return values</span></span>

<span data-ttu-id="24275-435">相反地，偏好傳回持有的彙總的資料，或使用 out 參數傳回多個值的具名型別。</span><span class="sxs-lookup"><span data-stu-id="24275-435">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="24275-436">雖然.NET 中存在的 tuple 與結構 （包括結構 tuple 的 C# 語言支援），它們通常不會提供理想和預期 API 適用於.NET 開發人員。</span><span class="sxs-lookup"><span data-stu-id="24275-436">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="24275-437">避免使用的參數對</span><span class="sxs-lookup"><span data-stu-id="24275-437">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="24275-438">相反地，使用.NET 呼叫慣例``Method(arg1,arg2,…,argN)``。</span><span class="sxs-lookup"><span data-stu-id="24275-438">Instead, use .NET calling conventions ``Method(arg1,arg2,…,argN)``.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="24275-439">秘訣： 如果您在設計文件庫，從任何.NET 語言使用，就沒有替代執行某些實驗 C# 和 Visual Basic 程式設計，確保您的程式庫 」 操作權限 」 從這些語言項目。</span><span class="sxs-lookup"><span data-stu-id="24275-439">Tip: If you’re designing libraries for use from any .NET language, then there’s no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="24275-440">您也可以使用.NET 反映程式與 Visual Studio 物件瀏覽器之類的工具，以確保文件庫和其文件會出現如預期般對開發人員。</span><span class="sxs-lookup"><span data-stu-id="24275-440">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="24275-441">附錄</span><span class="sxs-lookup"><span data-stu-id="24275-441">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="24275-442">設計 F # 程式碼使用其他.NET 語言的端對端範例</span><span class="sxs-lookup"><span data-stu-id="24275-442">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="24275-443">請考慮下列類別：</span><span class="sxs-lookup"><span data-stu-id="24275-443">Consider the following class:</span></span>

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

<span data-ttu-id="24275-444">推斷的 F # 類型的這個類別如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-444">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="24275-445">讓我們看看這個 F # 型別對程式設計人員使用其他.NET 語言的顯示方式。</span><span class="sxs-lookup"><span data-stu-id="24275-445">Let’s take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="24275-446">例如，大約 C# 「 簽章 」 如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-446">For example, the approximate C# “signature” is as follows:</span></span>

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

<span data-ttu-id="24275-447">有一些重點来注意的 F # 如何表示這裡建構。</span><span class="sxs-lookup"><span data-stu-id="24275-447">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="24275-448">例如: </span><span class="sxs-lookup"><span data-stu-id="24275-448">For example:</span></span>

* <span data-ttu-id="24275-449">已保留中繼資料，例如引數名稱。</span><span class="sxs-lookup"><span data-stu-id="24275-449">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="24275-450">F # 方法會採用兩個引數會變成 C# 方法會採用兩個引數。</span><span class="sxs-lookup"><span data-stu-id="24275-450">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="24275-451">函式和清單會變成對應的型別在 F # 程式庫的參考。</span><span class="sxs-lookup"><span data-stu-id="24275-451">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="24275-452">下列程式碼顯示如何調整這個程式碼以下列項目納入考量。</span><span class="sxs-lookup"><span data-stu-id="24275-452">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="24275-453">推斷的 F # 類型的程式碼如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-453">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="24275-454">C# 簽章現在如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-454">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="24275-455">修正對準備使用這種類型時香草的.NET 程式庫的一部分，如下所示：</span><span class="sxs-lookup"><span data-stu-id="24275-455">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="24275-456">調整數個名稱： `Point1`， `n`， `l`，和`f`變成`RadialPoint`， `count`， `factor`，和`transform`分別。</span><span class="sxs-lookup"><span data-stu-id="24275-456">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="24275-457">使用傳回型別`seq<RadialPoint>`而不是`RadialPoint list`藉由變更清單建構使用`[ ... ]`序列建構使用`IEnumerable<RadialPoint>`。</span><span class="sxs-lookup"><span data-stu-id="24275-457">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="24275-458">使用.NET 委派型別`System.Func`而不是 F # 函式類型。</span><span class="sxs-lookup"><span data-stu-id="24275-458">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="24275-459">這可讓您使用 C# 程式碼中最沒用。</span><span class="sxs-lookup"><span data-stu-id="24275-459">This makes it far nicer to consume in C# code.</span></span>
