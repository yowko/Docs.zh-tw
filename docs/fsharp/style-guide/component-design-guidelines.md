---
title: F# 元件設計指導
description: '瞭解撰寫適用于其他呼叫者耗用量之 F # 元件的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 590bda0660d54ea73c590d31e694f3d499e0fd9f
ms.sourcegitcommit: 488aced39b5f374bc0a139a4993616a54d15baf0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/12/2020
ms.locfileid: "83209132"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="2517f-103">F# 元件設計指導</span><span class="sxs-lookup"><span data-stu-id="2517f-103">F# component design guidelines</span></span>

<span data-ttu-id="2517f-104">本檔是 F # 程式設計的一組元件設計方針，以 F # 元件設計方針、v14、Microsoft Research 和 F # Software Foundation 原先策劃並維護的版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="2517f-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="2517f-105">本檔假設您已熟悉 F # 程式設計。</span><span class="sxs-lookup"><span data-stu-id="2517f-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="2517f-106">很多人都感謝 F # 的社區參與本指南各種版本的貢獻和有用的意見反應。</span><span class="sxs-lookup"><span data-stu-id="2517f-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="2517f-107">概觀</span><span class="sxs-lookup"><span data-stu-id="2517f-107">Overview</span></span>

<span data-ttu-id="2517f-108">本檔探討 F # 元件設計和程式碼的一些相關問題。</span><span class="sxs-lookup"><span data-stu-id="2517f-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="2517f-109">元件可以表示下列任何一項：</span><span class="sxs-lookup"><span data-stu-id="2517f-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="2517f-110">F # 專案中的一層，其中包含該專案內的外部取用者。</span><span class="sxs-lookup"><span data-stu-id="2517f-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="2517f-111">一種程式庫，適用于跨元件界限的 F # 程式碼耗用量。</span><span class="sxs-lookup"><span data-stu-id="2517f-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="2517f-112">一種程式庫，適用于跨元件界限的任何 .NET 語言耗用量。</span><span class="sxs-lookup"><span data-stu-id="2517f-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="2517f-113">一種程式庫，用於透過套件存放庫（例如[NuGet](https://nuget.org)）散發。</span><span class="sxs-lookup"><span data-stu-id="2517f-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="2517f-114">本文中所述的技巧會遵循[良好 F # 程式碼的五個原則](index.md#five-principles-of-good-f-code)，因此會適當地使用功能和物件程式設計。</span><span class="sxs-lookup"><span data-stu-id="2517f-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="2517f-115">不論方法為何，元件和程式庫設計工具在嘗試製作最容易由開發人員使用的 API 時，都會面臨一些實際和平凡的問題。</span><span class="sxs-lookup"><span data-stu-id="2517f-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="2517f-116">Conscientious 應用程式的[.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)，會引導您建立一組一致的 api，讓您有愉快的使用。</span><span class="sxs-lookup"><span data-stu-id="2517f-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="2517f-117">一般指導方針</span><span class="sxs-lookup"><span data-stu-id="2517f-117">General guidelines</span></span>

<span data-ttu-id="2517f-118">無論媒體櫃的目標物件為何，都有一些適用于 F # 程式庫的通用指導方針。</span><span class="sxs-lookup"><span data-stu-id="2517f-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="2517f-119">瞭解 .NET 程式庫設計指導方針</span><span class="sxs-lookup"><span data-stu-id="2517f-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="2517f-120">無論您執行的 F # 程式碼種類為何，都必須具備[.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)的實用知識。</span><span class="sxs-lookup"><span data-stu-id="2517f-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="2517f-121">大部分其他的 F # 和 .NET 程式設計人員都將熟悉這些指導方針，並預期 .NET 程式碼符合它們。</span><span class="sxs-lookup"><span data-stu-id="2517f-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="2517f-122">.NET 程式庫設計指導方針提供有關命名、設計類別和介面、成員設計（屬性、方法、事件等）等的一般指引，而且是適用于各種設計指引的實用第一點參考。</span><span class="sxs-lookup"><span data-stu-id="2517f-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="2517f-123">將 XML 檔批註新增至您的程式碼</span><span class="sxs-lookup"><span data-stu-id="2517f-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="2517f-124">公用 Api 上的 XML 檔可確保使用者在使用這些類型和成員時，可以取得絕佳的 Intellisense 和 Quickinfo，並啟用程式庫的檔檔案。</span><span class="sxs-lookup"><span data-stu-id="2517f-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="2517f-125">請參閱[Xml 檔](../language-reference/xml-documentation.md)，以瞭解可用於 xmldoc 批註內其他標記的各種 xml 標記。</span><span class="sxs-lookup"><span data-stu-id="2517f-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="2517f-126">您可以使用簡短形式 XML 批註（ `/// comment` ）或標準 XML 批註（ `///<summary>comment</summary>` ）。</span><span class="sxs-lookup"><span data-stu-id="2517f-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="2517f-127">針對穩定的程式庫和元件 Api，請考慮使用明確的簽章檔案（. fsi.exe）</span><span class="sxs-lookup"><span data-stu-id="2517f-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="2517f-128">在 F # 程式庫中使用明確的簽章檔案，可提供公用 API 的簡潔摘要，協助確保您知道媒體櫃的完整公用介面，並提供公用檔和內部執行詳細資料的清楚分隔。</span><span class="sxs-lookup"><span data-stu-id="2517f-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="2517f-129">簽章檔案會要求在執行檔和簽章檔案中進行變更，藉此增加變更公用 API 的摩擦。</span><span class="sxs-lookup"><span data-stu-id="2517f-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="2517f-130">因此，通常只會在 API 已 solidified，且不再預期變更時，才會引進簽名檔案。</span><span class="sxs-lookup"><span data-stu-id="2517f-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="2517f-131">一律遵循在 .NET 中使用字串的最佳作法</span><span class="sxs-lookup"><span data-stu-id="2517f-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="2517f-132">遵循[在 .net 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md)指引。</span><span class="sxs-lookup"><span data-stu-id="2517f-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="2517f-133">特別是，一律在轉換和比較字串時，明確陳述*文化目的*（如果適用）。</span><span class="sxs-lookup"><span data-stu-id="2517f-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="2517f-134">F # 面向程式庫的指導方針</span><span class="sxs-lookup"><span data-stu-id="2517f-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="2517f-135">本節提供開發公用 F # 面向程式庫的建議;也就是，程式庫會公開可供 F # 開發人員使用的公用 Api。</span><span class="sxs-lookup"><span data-stu-id="2517f-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="2517f-136">有各種不同的程式庫設計建議，特別適用于 F #。</span><span class="sxs-lookup"><span data-stu-id="2517f-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="2517f-137">如果沒有遵循的特定建議，.NET 程式庫設計指導方針就是回溯指引。</span><span class="sxs-lookup"><span data-stu-id="2517f-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="2517f-138">命名慣例</span><span class="sxs-lookup"><span data-stu-id="2517f-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="2517f-139">使用 .NET 命名和大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="2517f-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="2517f-140">下表會遵循 .NET 命名和大小寫慣例。</span><span class="sxs-lookup"><span data-stu-id="2517f-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="2517f-141">另外還有一些小型的新增功能，也包括 F # 結構。</span><span class="sxs-lookup"><span data-stu-id="2517f-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="2517f-142">建構</span><span class="sxs-lookup"><span data-stu-id="2517f-142">Construct</span></span> | <span data-ttu-id="2517f-143">案例</span><span class="sxs-lookup"><span data-stu-id="2517f-143">Case</span></span> | <span data-ttu-id="2517f-144">部分</span><span class="sxs-lookup"><span data-stu-id="2517f-144">Part</span></span> | <span data-ttu-id="2517f-145">範例</span><span class="sxs-lookup"><span data-stu-id="2517f-145">Examples</span></span> | <span data-ttu-id="2517f-146">附註</span><span class="sxs-lookup"><span data-stu-id="2517f-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="2517f-147">具體類型</span><span class="sxs-lookup"><span data-stu-id="2517f-147">Concrete types</span></span> | <span data-ttu-id="2517f-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-148">PascalCase</span></span> | <span data-ttu-id="2517f-149">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="2517f-149">Noun/ adjective</span></span> | <span data-ttu-id="2517f-150">List、Double、Complex</span><span class="sxs-lookup"><span data-stu-id="2517f-150">List, Double, Complex</span></span> | <span data-ttu-id="2517f-151">具體類型包括結構、類別、列舉、委派、記錄和等位。</span><span class="sxs-lookup"><span data-stu-id="2517f-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="2517f-152">雖然類型名稱在 OCaml 中是傳統小寫，但 F # 已採用類型的 .NET 命名配置。</span><span class="sxs-lookup"><span data-stu-id="2517f-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="2517f-153">DLL</span><span class="sxs-lookup"><span data-stu-id="2517f-153">DLLs</span></span>           | <span data-ttu-id="2517f-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-154">PascalCase</span></span> |                 | <span data-ttu-id="2517f-155">Fabrikam. Core .dll</span><span class="sxs-lookup"><span data-stu-id="2517f-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="2517f-156">聯集標記</span><span class="sxs-lookup"><span data-stu-id="2517f-156">Union tags</span></span>     | <span data-ttu-id="2517f-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-157">PascalCase</span></span> | <span data-ttu-id="2517f-158">名詞</span><span class="sxs-lookup"><span data-stu-id="2517f-158">Noun</span></span> | <span data-ttu-id="2517f-159">部分、新增、成功</span><span class="sxs-lookup"><span data-stu-id="2517f-159">Some, Add, Success</span></span> | <span data-ttu-id="2517f-160">請勿在公用 Api 中使用前置詞。</span><span class="sxs-lookup"><span data-stu-id="2517f-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="2517f-161">選擇性使用內部的前置詞，例如`type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="2517f-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="2517f-162">事件</span><span class="sxs-lookup"><span data-stu-id="2517f-162">Event</span></span>          | <span data-ttu-id="2517f-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-163">PascalCase</span></span> | <span data-ttu-id="2517f-164">動詞命令</span><span class="sxs-lookup"><span data-stu-id="2517f-164">Verb</span></span> | <span data-ttu-id="2517f-165">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="2517f-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="2517f-166">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2517f-166">Exceptions</span></span>     | <span data-ttu-id="2517f-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-167">PascalCase</span></span> |      | <span data-ttu-id="2517f-168">WebException</span><span class="sxs-lookup"><span data-stu-id="2517f-168">WebException</span></span> | <span data-ttu-id="2517f-169">名稱的結尾應該是 "Exception"。</span><span class="sxs-lookup"><span data-stu-id="2517f-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="2517f-170">欄位</span><span class="sxs-lookup"><span data-stu-id="2517f-170">Field</span></span>          | <span data-ttu-id="2517f-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-171">PascalCase</span></span> | <span data-ttu-id="2517f-172">名詞</span><span class="sxs-lookup"><span data-stu-id="2517f-172">Noun</span></span> | <span data-ttu-id="2517f-173">CurrentName</span><span class="sxs-lookup"><span data-stu-id="2517f-173">CurrentName</span></span>  | |
| <span data-ttu-id="2517f-174">介面型別</span><span class="sxs-lookup"><span data-stu-id="2517f-174">Interface types</span></span> |  <span data-ttu-id="2517f-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-175">PascalCase</span></span> | <span data-ttu-id="2517f-176">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="2517f-176">Noun/ adjective</span></span> | <span data-ttu-id="2517f-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="2517f-177">IDisposable</span></span> | <span data-ttu-id="2517f-178">名稱的開頭應為 "I"。</span><span class="sxs-lookup"><span data-stu-id="2517f-178">Name should start with "I".</span></span> |
| <span data-ttu-id="2517f-179">方法</span><span class="sxs-lookup"><span data-stu-id="2517f-179">Method</span></span> |  <span data-ttu-id="2517f-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-180">PascalCase</span></span> |  <span data-ttu-id="2517f-181">動詞命令</span><span class="sxs-lookup"><span data-stu-id="2517f-181">Verb</span></span> | <span data-ttu-id="2517f-182">ToString</span><span class="sxs-lookup"><span data-stu-id="2517f-182">ToString</span></span> | |
| <span data-ttu-id="2517f-183">命名空間</span><span class="sxs-lookup"><span data-stu-id="2517f-183">Namespace</span></span> | <span data-ttu-id="2517f-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-184">PascalCase</span></span> | | <span data-ttu-id="2517f-185">Fsharp.core 核心</span><span class="sxs-lookup"><span data-stu-id="2517f-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="2517f-186">通常 `<Organization>.<Technology>[.<Subnamespace>]` 會使用，但如果此技術與組織無關，則會捨棄組織。</span><span class="sxs-lookup"><span data-stu-id="2517f-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="2517f-187">參數</span><span class="sxs-lookup"><span data-stu-id="2517f-187">Parameters</span></span> | <span data-ttu-id="2517f-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="2517f-188">camelCase</span></span> | <span data-ttu-id="2517f-189">名詞</span><span class="sxs-lookup"><span data-stu-id="2517f-189">Noun</span></span> |  <span data-ttu-id="2517f-190">類型名稱、轉換、範圍</span><span class="sxs-lookup"><span data-stu-id="2517f-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="2517f-191">let 值（內部）</span><span class="sxs-lookup"><span data-stu-id="2517f-191">let values (internal)</span></span> | <span data-ttu-id="2517f-192">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-192">camelCase or PascalCase</span></span> | <span data-ttu-id="2517f-193">名詞/動詞</span><span class="sxs-lookup"><span data-stu-id="2517f-193">Noun/ verb</span></span> |  <span data-ttu-id="2517f-194">getValue、myTable</span><span class="sxs-lookup"><span data-stu-id="2517f-194">getValue, myTable</span></span> |
| <span data-ttu-id="2517f-195">let 值（外部）</span><span class="sxs-lookup"><span data-stu-id="2517f-195">let values (external)</span></span> | <span data-ttu-id="2517f-196">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-196">camelCase or PascalCase</span></span> | <span data-ttu-id="2517f-197">名詞/動詞</span><span class="sxs-lookup"><span data-stu-id="2517f-197">Noun/verb</span></span>  | <span data-ttu-id="2517f-198">清單。地圖，日期。今天</span><span class="sxs-lookup"><span data-stu-id="2517f-198">List.map, Dates.Today</span></span> | <span data-ttu-id="2517f-199">遵循傳統的功能設計模式時，let 系結的值通常是公用的。</span><span class="sxs-lookup"><span data-stu-id="2517f-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="2517f-200">不過，當識別碼可以從其他 .NET 語言使用時，通常會使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="2517f-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="2517f-201">屬性</span><span class="sxs-lookup"><span data-stu-id="2517f-201">Property</span></span>  | <span data-ttu-id="2517f-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-202">PascalCase</span></span>  | <span data-ttu-id="2517f-203">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="2517f-203">Noun/ adjective</span></span>  | <span data-ttu-id="2517f-204">IsEndOfFile，背景色彩</span><span class="sxs-lookup"><span data-stu-id="2517f-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="2517f-205">布林值屬性通常是使用，而且應該是肯定，如 IsEndOfFile，not IsNotEndOfFile。</span><span class="sxs-lookup"><span data-stu-id="2517f-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="2517f-206">避免縮寫</span><span class="sxs-lookup"><span data-stu-id="2517f-206">Avoid abbreviations</span></span>

<span data-ttu-id="2517f-207">.NET 指導方針不鼓勵使用縮寫（例如，「使用 `OnButtonClick` 而不是」 `OnBtnClick` ）。</span><span class="sxs-lookup"><span data-stu-id="2517f-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="2517f-208">一般的縮寫（例如 `Async` "非同步"）是容許的。</span><span class="sxs-lookup"><span data-stu-id="2517f-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="2517f-209">功能程式設計有時會忽略這種指導方針;例如，會 `List.iter` 使用「反復執行」的縮寫。</span><span class="sxs-lookup"><span data-stu-id="2517f-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="2517f-210">基於這個理由，使用縮寫傾向于 F # 對 F # 程式設計的程度更高，但在公用元件設計中，通常應該避免。</span><span class="sxs-lookup"><span data-stu-id="2517f-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="2517f-211">避免出現大小寫名稱衝突</span><span class="sxs-lookup"><span data-stu-id="2517f-211">Avoid casing name collisions</span></span>

<span data-ttu-id="2517f-212">.NET 方針表示，不能單獨使用大小寫來區分名稱衝突，因為有些用戶端語言（例如 Visual Basic）不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="2517f-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="2517f-213">適當時使用縮寫</span><span class="sxs-lookup"><span data-stu-id="2517f-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="2517f-214">縮寫（例如 XML）不是縮寫，而且廣泛用於 .NET 程式庫中的 uncapitalized 格式（Xml）。</span><span class="sxs-lookup"><span data-stu-id="2517f-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="2517f-215">您應該只使用知名且廣泛辨識的縮略字。</span><span class="sxs-lookup"><span data-stu-id="2517f-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="2517f-216">針對泛型參數名稱使用 PascalCase</span><span class="sxs-lookup"><span data-stu-id="2517f-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="2517f-217">請在公用 Api 中使用 PascalCase 做為泛型參數名稱，包括 F # 面向的程式庫。</span><span class="sxs-lookup"><span data-stu-id="2517f-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="2517f-218">特別是， `T` `U` 針對任意的泛型參數使用、、、等名稱 `T1` `T2` ，而且當特定名稱合理時，針對 F # 對應的程式庫會使用 `Key` 、 `Value` 、 `Arg` （但不像）之類 `TKey` 的名稱。</span><span class="sxs-lookup"><span data-stu-id="2517f-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="2517f-219">針對公用函式和 F # 模組中的值使用 PascalCase 或 camelCase</span><span class="sxs-lookup"><span data-stu-id="2517f-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="2517f-220">camelCase 適用于設計為不合格的公用函式（例如， `invalidArg` ），以及用於「標準集合函式」（例如，[清單]）的公用函數。</span><span class="sxs-lookup"><span data-stu-id="2517f-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="2517f-221">在這兩種情況下，函式名稱的運作方式非常類似于語言中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="2517f-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="2517f-222">物件、型別和模組設計</span><span class="sxs-lookup"><span data-stu-id="2517f-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="2517f-223">使用命名空間或模組來包含您的類型和模組</span><span class="sxs-lookup"><span data-stu-id="2517f-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="2517f-224">元件中的每個 F # 檔案都應該以命名空間宣告或模組宣告為開頭。</span><span class="sxs-lookup"><span data-stu-id="2517f-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="2517f-225">或</span><span class="sxs-lookup"><span data-stu-id="2517f-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="2517f-226">使用模組和命名空間來組織最上層程式碼的差異如下：</span><span class="sxs-lookup"><span data-stu-id="2517f-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="2517f-227">命名空間可以跨越多個檔案</span><span class="sxs-lookup"><span data-stu-id="2517f-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="2517f-228">命名空間不能包含 F # 函式，除非它們位於內部模組內</span><span class="sxs-lookup"><span data-stu-id="2517f-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="2517f-229">任何指定模組的程式碼都必須包含在單一檔案中</span><span class="sxs-lookup"><span data-stu-id="2517f-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="2517f-230">最上層模組可以包含 F # 函式，而不需要內部模組</span><span class="sxs-lookup"><span data-stu-id="2517f-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="2517f-231">最上層命名空間或模組之間的選擇會影響已編譯的程式碼形式，因此，如果您的 API 最終是在 F # 程式碼之外使用，則會影響其他 .NET 語言的觀點。</span><span class="sxs-lookup"><span data-stu-id="2517f-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="2517f-232">針對物件類型的內部作業使用方法和屬性</span><span class="sxs-lookup"><span data-stu-id="2517f-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="2517f-233">使用物件時，最好能確保可耗用的功能會實作為該類型的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="2517f-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="2517f-234">指定成員的大部分功能不一定要在該成員中執行，但是該功能的可耗用部分應該是。</span><span class="sxs-lookup"><span data-stu-id="2517f-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="2517f-235">使用類別封裝可變動的狀態</span><span class="sxs-lookup"><span data-stu-id="2517f-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="2517f-236">在 F # 中，這只需要在該狀態尚未由另一個語言結構（例如關閉、序列運算式或非同步計算）封裝的情況下完成。</span><span class="sxs-lookup"><span data-stu-id="2517f-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="2517f-237">使用介面將相關的作業分組</span><span class="sxs-lookup"><span data-stu-id="2517f-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="2517f-238">使用介面類別型來代表一組作業。</span><span class="sxs-lookup"><span data-stu-id="2517f-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="2517f-239">這是慣用的其他選項，例如函數的元組或函式的記錄。</span><span class="sxs-lookup"><span data-stu-id="2517f-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T>: preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T>: preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="2517f-240">喜好設定：</span><span class="sxs-lookup"><span data-stu-id="2517f-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="2517f-241">介面是 .NET 中的第一級概念，您可以用它來達到函子通常會提供給您的目標。</span><span class="sxs-lookup"><span data-stu-id="2517f-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="2517f-242">此外，它們可以用來將存在型別編碼到您的程式中，而不能使用哪些函式記錄。</span><span class="sxs-lookup"><span data-stu-id="2517f-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="2517f-243">使用模組將作用於集合的函式群組在一起</span><span class="sxs-lookup"><span data-stu-id="2517f-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="2517f-244">當您定義集合類型時，請考慮提供新集合類型的一組標準作業， `CollectionType.map` `CollectionType.iter` 例如和）。</span><span class="sxs-lookup"><span data-stu-id="2517f-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="2517f-245">如果您包含這類別模組，請遵循 Fsharp.core 中找到之函式的標準命名慣例。</span><span class="sxs-lookup"><span data-stu-id="2517f-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="2517f-246">使用模組將函式群組在一般的標準函式，特別是在數學和 DSL 程式庫中</span><span class="sxs-lookup"><span data-stu-id="2517f-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="2517f-247">例如， `Microsoft.FSharp.Core.Operators` 是由 fsharp.core 所提供的最上層函式的自動開啟集合（例如 `abs` 和 `sin` ）。</span><span class="sxs-lookup"><span data-stu-id="2517f-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="2517f-248">同樣地，統計資料連結庫可能會包含具有函數和的模組 `erf` `erfc` ，其中此模組是設計成明確或自動開啟的。</span><span class="sxs-lookup"><span data-stu-id="2517f-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="2517f-249">請考慮使用 RequireQualifiedAccess 並謹慎套用 AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="2517f-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="2517f-250">將屬性加入模組中， `[<RequireQualifiedAccess>]` 表示模組可能無法開啟，而且對模組元素的參考需要明確限定的存取權。</span><span class="sxs-lookup"><span data-stu-id="2517f-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="2517f-251">例如， `Microsoft.FSharp.Collections.List` 模組具有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="2517f-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="2517f-252">當模組中的函數和值有可能與其他模組中的名稱衝突的名稱時，這會很有用。</span><span class="sxs-lookup"><span data-stu-id="2517f-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="2517f-253">需要限定的存取權可能會大幅增加程式庫的長期維護性和 evolvability。</span><span class="sxs-lookup"><span data-stu-id="2517f-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="2517f-254">將 `[<AutoOpen>]` 屬性新增至模組，表示當包含的命名空間開啟時，將會開啟模組。</span><span class="sxs-lookup"><span data-stu-id="2517f-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="2517f-255">`[<AutoOpen>]`屬性也可以套用至元件，以指示在參考元件時自動開啟的模組。</span><span class="sxs-lookup"><span data-stu-id="2517f-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="2517f-256">例如，統計資料連結庫**MathsHeaven。統計資料**可能包含 `module MathsHeaven.Statistics.Operators` 包含函數 `erf` 和 `erfc` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="2517f-257">將此模組標記為是合理的 `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="2517f-258">這表示 `open MathsHeaven.Statistics` 也會開啟此模組，並將名稱 `erf` 和帶入 `erfc` 範圍中。</span><span class="sxs-lookup"><span data-stu-id="2517f-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="2517f-259">的另一個好用適用 `[<AutoOpen>]` 于包含擴充方法的模組。</span><span class="sxs-lookup"><span data-stu-id="2517f-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="2517f-260">過度 `[<AutoOpen>]` 使用會導致污染命名空間，而屬性應謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="2517f-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="2517f-261">針對特定網域中的特定程式庫，明智的使用 `[<AutoOpen>]` 可能會導致更好的可用性。</span><span class="sxs-lookup"><span data-stu-id="2517f-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="2517f-262">請考慮在適當使用已知運算子的類別上定義運算子成員</span><span class="sxs-lookup"><span data-stu-id="2517f-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="2517f-263">有時候類別是用來建立數學結構（例如向量）的模型。</span><span class="sxs-lookup"><span data-stu-id="2517f-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="2517f-264">當模型化的網域具有已知的運算子時，將其定義為類別內建的成員會很有説明。</span><span class="sxs-lookup"><span data-stu-id="2517f-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="2517f-265">本指導方針對應至這些類型的一般 .NET 指引。</span><span class="sxs-lookup"><span data-stu-id="2517f-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="2517f-266">不過，在 F # 編碼中也可能更重要，因為這可讓這些類型與 F # 函式和方法搭配成員條件約束使用，例如 sumBy。</span><span class="sxs-lookup"><span data-stu-id="2517f-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="2517f-267">請考慮使用 CompiledName 來提供。其他 .NET 語言取用者的網路易記名稱</span><span class="sxs-lookup"><span data-stu-id="2517f-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="2517f-268">有時候，您可能會想要針對 F # 取用者以一種樣式來命名專案（例如小寫的靜態成員，讓它看起來像是模組系結函式），但是在編譯成元件時，名稱的樣式是不同的。</span><span class="sxs-lookup"><span data-stu-id="2517f-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="2517f-269">您可以使用 `[<CompiledName>]` 屬性，為使用元件的非 F # 程式碼提供不同的樣式。</span><span class="sxs-lookup"><span data-stu-id="2517f-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="2517f-270">藉由使用 `[<CompiledName>]` ，您可以對元件的非 F # 取用者使用 .net 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="2517f-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="2517f-271">如果這樣做會提供更簡單的 API，請使用成員函式的方法多載</span><span class="sxs-lookup"><span data-stu-id="2517f-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="2517f-272">方法多載是一種功能強大的工具，可簡化可能需要執行類似功能的 API，但使用不同的選項或引數。</span><span class="sxs-lookup"><span data-stu-id="2517f-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="2517f-273">在 F # 中，多載引數數目，而不是引數的類型。</span><span class="sxs-lookup"><span data-stu-id="2517f-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="2517f-274">如果這些類型的設計可能會進化，則隱藏記錄和聯集類型的標記法</span><span class="sxs-lookup"><span data-stu-id="2517f-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="2517f-275">避免洩漏物件的具體表示。</span><span class="sxs-lookup"><span data-stu-id="2517f-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="2517f-276">例如， <xref:System.DateTime> .net 程式庫設計的外部公用 API 不會顯示值的具體表示。</span><span class="sxs-lookup"><span data-stu-id="2517f-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="2517f-277">在執行時間，通用語言執行平臺會知道將在執行期間使用的已認可的執行。</span><span class="sxs-lookup"><span data-stu-id="2517f-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="2517f-278">不過，已編譯的程式碼本身並不會挑選具體表示的相依性。</span><span class="sxs-lookup"><span data-stu-id="2517f-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="2517f-279">避免使用擴展的執行繼承</span><span class="sxs-lookup"><span data-stu-id="2517f-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="2517f-280">在 F # 中，很少使用執行繼承。</span><span class="sxs-lookup"><span data-stu-id="2517f-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="2517f-281">此外，繼承階層通常很複雜，而且在新的需求抵達時很難變更。</span><span class="sxs-lookup"><span data-stu-id="2517f-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="2517f-282">繼承執行仍然存在於 F # 中，以達到相容性和很罕見的情況，這是問題的最佳解決方案，但在設計多型（例如介面執行）時，應該在 F # 程式中尋找其他技術。</span><span class="sxs-lookup"><span data-stu-id="2517f-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="2517f-283">函式和成員簽章</span><span class="sxs-lookup"><span data-stu-id="2517f-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="2517f-284">傳回少數多個不相關的值時，請使用元組做為傳回值</span><span class="sxs-lookup"><span data-stu-id="2517f-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="2517f-285">以下是在傳回型別中使用元組的絕佳範例：</span><span class="sxs-lookup"><span data-stu-id="2517f-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="2517f-286">對於包含許多元件，或元件與單一可識別實體相關的傳回類型，請考慮使用命名類型，而不是元組。</span><span class="sxs-lookup"><span data-stu-id="2517f-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="2517f-287">用於 `Async<T>` F # API 界限的非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="2517f-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="2517f-288">如果有一個名為的對應同步作業會傳回 `Operation` `T` ，則如果非同步作業傳回，則應該將其命名為 `AsyncOperation` `Async<T>` `OperationAsync` `Task<T>` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="2517f-289">對於公開 Begin/End 方法的常用 .NET 類型，請考慮使用 `Async.FromBeginEnd` 將擴充方法撰寫為外觀，以提供 F # 非同步程式設計模型給這些 .Net api。</span><span class="sxs-lookup"><span data-stu-id="2517f-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

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

### <a name="exceptions"></a><span data-ttu-id="2517f-290">例外狀況</span><span class="sxs-lookup"><span data-stu-id="2517f-290">Exceptions</span></span>

<span data-ttu-id="2517f-291">若要瞭解例外狀況、結果和選項的適當用法，請參閱[錯誤管理](conventions.md#error-management)。</span><span class="sxs-lookup"><span data-stu-id="2517f-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="2517f-292">延伸成員</span><span class="sxs-lookup"><span data-stu-id="2517f-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="2517f-293">在 F #-F # 元件中仔細套用 F # 擴充成員</span><span class="sxs-lookup"><span data-stu-id="2517f-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="2517f-294">F # 延伸模組成員通常僅適用于內建作業關閉時的作業，而該類型與大部分的使用模式相關聯。</span><span class="sxs-lookup"><span data-stu-id="2517f-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="2517f-295">其中一個常見的用法是針對各種 .NET 類型提供更慣用至 F # 的 Api：</span><span class="sxs-lookup"><span data-stu-id="2517f-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="2517f-296">聯集類型</span><span class="sxs-lookup"><span data-stu-id="2517f-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="2517f-297">使用區分聯集，而不是樹狀結構化資料的類別階層</span><span class="sxs-lookup"><span data-stu-id="2517f-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="2517f-298">類似樹狀結構的會以遞迴方式定義。</span><span class="sxs-lookup"><span data-stu-id="2517f-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="2517f-299">這對繼承並不難，但使用區分等位。</span><span class="sxs-lookup"><span data-stu-id="2517f-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="2517f-300">以區分等位來表示類似樹狀結構的資料也可讓您受益于模式比對中的 exhaustiveness。</span><span class="sxs-lookup"><span data-stu-id="2517f-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="2517f-301">`[<RequireQualifiedAccess>]`在其大小寫不是完全唯一的聯集類型上使用</span><span class="sxs-lookup"><span data-stu-id="2517f-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="2517f-302">您可能會發現自己所在的網域，其名稱是不同專案的最佳名稱，例如區分聯集案例。</span><span class="sxs-lookup"><span data-stu-id="2517f-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="2517f-303">您可以使用 `[<RequireQualifiedAccess>]` 來區分大小寫名稱，以避免因為與語句順序相依而觸發混淆的錯誤 `open`</span><span class="sxs-lookup"><span data-stu-id="2517f-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="2517f-304">如果這些類型的設計可能會進化，請隱藏二進位相容 Api 的區分等位的標記法</span><span class="sxs-lookup"><span data-stu-id="2517f-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="2517f-305">等位類型依賴于簡潔程式設計模型的 F # 模式比對表單。</span><span class="sxs-lookup"><span data-stu-id="2517f-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="2517f-306">如先前所述，如果這些類型的設計可能會進化，您應該避免洩漏具體的資料標記法。</span><span class="sxs-lookup"><span data-stu-id="2517f-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="2517f-307">例如，您可以使用私用或內部宣告或使用簽章檔案來隱藏區分聯集的標記法。</span><span class="sxs-lookup"><span data-stu-id="2517f-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="2517f-308">如果您不想要顯示區分的等位，可能會發現您不需要中斷使用者程式碼就能為您的程式庫進行版本。</span><span class="sxs-lookup"><span data-stu-id="2517f-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="2517f-309">相反地，請考慮顯示一或多個現用模式，以允許比類型的值進行模式比對。</span><span class="sxs-lookup"><span data-stu-id="2517f-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="2517f-310">現用模式提供了一種替代方式，可以使用模式比對來提供 F # 取用者，同時避免直接公開 F # 聯集類型。</span><span class="sxs-lookup"><span data-stu-id="2517f-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="2517f-311">內嵌函式和成員條件約束</span><span class="sxs-lookup"><span data-stu-id="2517f-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="2517f-312">使用內嵌函式搭配隱含的成員條件約束和靜態解析的泛型型別來定義泛型數值演算法</span><span class="sxs-lookup"><span data-stu-id="2517f-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="2517f-313">算術成員條件約束和 F # 比較準則約束是 F # 程式設計的標準。</span><span class="sxs-lookup"><span data-stu-id="2517f-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="2517f-314">例如，請參考下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="2517f-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="2517f-315">此函式的類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="2517f-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="2517f-316">在數學程式庫中，這是適用于公用 API 的功能。</span><span class="sxs-lookup"><span data-stu-id="2517f-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="2517f-317">避免使用成員條件約束來模擬型別類別和未類型的輸入</span><span class="sxs-lookup"><span data-stu-id="2517f-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="2517f-318">您可以使用 F # 成員條件約束來模擬「未輸入」。</span><span class="sxs-lookup"><span data-stu-id="2517f-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="2517f-319">不過，使用此功能的成員不應該一般用於 F # 到 F # 程式庫設計。</span><span class="sxs-lookup"><span data-stu-id="2517f-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="2517f-320">這是因為以不熟悉或非標準隱含條件約束為基礎的程式庫設計，往往會使使用者程式碼變得不彈性，並系結至一個特定架構模式。</span><span class="sxs-lookup"><span data-stu-id="2517f-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="2517f-321">此外，以這種方式大量使用成員條件約束很有可能會產生非常長的編譯時間。</span><span class="sxs-lookup"><span data-stu-id="2517f-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="2517f-322">運算子定義</span><span class="sxs-lookup"><span data-stu-id="2517f-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="2517f-323">避免定義自訂符號運算子</span><span class="sxs-lookup"><span data-stu-id="2517f-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="2517f-324">自訂運算子在某些情況下是不可或缺的，而且在大型的實程式碼主體中非常有用的標記裝置。</span><span class="sxs-lookup"><span data-stu-id="2517f-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="2517f-325">針對程式庫的新使用者，命名函數通常較容易使用。</span><span class="sxs-lookup"><span data-stu-id="2517f-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="2517f-326">此外，自訂符號運算子可能難以記載，而且使用者會發現，因為 IDE 和搜尋引擎中現有的限制，而難以查閱運算子的說明。</span><span class="sxs-lookup"><span data-stu-id="2517f-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="2517f-327">因此，最好將您的功能發佈為命名函式和成員，而且只有在標記的優點超過檔和認知成本時，才會針對此功能公開運算子。</span><span class="sxs-lookup"><span data-stu-id="2517f-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="2517f-328">測量單位</span><span class="sxs-lookup"><span data-stu-id="2517f-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="2517f-329">小心使用在 F # 程式碼中新增型別安全的測量單位</span><span class="sxs-lookup"><span data-stu-id="2517f-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="2517f-330">其他 .NET 語言觀看時，會清除測量單位的其他輸入資訊。</span><span class="sxs-lookup"><span data-stu-id="2517f-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="2517f-331">請注意，.NET 元件、工具和反映將會看到類型-[san-單位]。</span><span class="sxs-lookup"><span data-stu-id="2517f-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="2517f-332">例如，c # 取用者會看到， `float` 而不是 `float<kg>` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="2517f-333">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="2517f-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="2517f-334">小心使用類型縮寫來簡化 F # 程式碼</span><span class="sxs-lookup"><span data-stu-id="2517f-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="2517f-335">.NET 元件、工具和反映不會看到類型的縮寫名稱。</span><span class="sxs-lookup"><span data-stu-id="2517f-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="2517f-336">類型縮寫的顯著用法也可以讓定義域比實際的更為複雜，這可能會使取用者混淆。</span><span class="sxs-lookup"><span data-stu-id="2517f-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="2517f-337">避免公用類型的類型縮寫，其成員和屬性本質上應該與要縮寫的類型所提供的不同</span><span class="sxs-lookup"><span data-stu-id="2517f-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="2517f-338">在此情況下，要縮寫的類型會顯示太多關於所定義之實際類型的表示。</span><span class="sxs-lookup"><span data-stu-id="2517f-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="2517f-339">相反地，請考慮將縮寫包裝在類別類型或單一案例的區分等位中（或者，當效能很重要時，請考慮使用結構類型來包裝縮寫）。</span><span class="sxs-lookup"><span data-stu-id="2517f-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="2517f-340">例如，將多個對應定義為 F # 對應的特殊案例很有吸引力，例如：</span><span class="sxs-lookup"><span data-stu-id="2517f-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="2517f-341">不過，此類型上的邏輯點標記法作業與對應上的作業不同，例如，查閱運算子對應是合理的。[key] 如果索引鍵不在字典中，則傳回空白清單，而不是引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2517f-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="2517f-342">從其他 .NET 語言使用之程式庫的指導方針</span><span class="sxs-lookup"><span data-stu-id="2517f-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="2517f-343">設計要從其他 .NET 語言使用的程式庫時，請務必遵守 .Net 連結[庫設計方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="2517f-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="2517f-344">在本檔中，這些程式庫會標記為 vanilla 的 .NET 程式庫，而不是使用 f # 的程式庫，而不受限制。</span><span class="sxs-lookup"><span data-stu-id="2517f-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="2517f-345">設計 vanilla .NET 程式庫表示提供熟悉和慣用的 Api，使其與其余 .NET Framework 一致，方法是將公用 API 中的 F # 特定結構的使用降至最低。</span><span class="sxs-lookup"><span data-stu-id="2517f-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="2517f-346">這些規則會在下列各節中說明。</span><span class="sxs-lookup"><span data-stu-id="2517f-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="2517f-347">命名空間和類型設計（適用于用於其他 .NET 語言的程式庫）</span><span class="sxs-lookup"><span data-stu-id="2517f-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="2517f-348">將 .NET 命名慣例套用至元件的公用 API</span><span class="sxs-lookup"><span data-stu-id="2517f-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="2517f-349">請特別注意使用縮寫名稱和 .NET 大小寫方針。</span><span class="sxs-lookup"><span data-stu-id="2517f-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="2517f-350">使用命名空間、類型和成員做為元件的主要組織結構</span><span class="sxs-lookup"><span data-stu-id="2517f-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="2517f-351">包含公用功能的所有檔案都應該以宣告開頭 `namespace` ，而且命名空間中唯一的公開實體應該是類型。</span><span class="sxs-lookup"><span data-stu-id="2517f-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="2517f-352">請勿使用 F # 模組。</span><span class="sxs-lookup"><span data-stu-id="2517f-352">Do not use F# modules.</span></span>

<span data-ttu-id="2517f-353">使用非公用模組來保存實作為程式碼、公用程式類型和公用程式函式。</span><span class="sxs-lookup"><span data-stu-id="2517f-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="2517f-354">靜態類型應優先于模組，因為它們可讓 API 的未來演變使用多載，以及可能不會在 F # 模組中使用的其他 .NET API 設計概念。</span><span class="sxs-lookup"><span data-stu-id="2517f-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="2517f-355">例如，取代下列公用 API：</span><span class="sxs-lookup"><span data-stu-id="2517f-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="2517f-356">請改為考慮：</span><span class="sxs-lookup"><span data-stu-id="2517f-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="2517f-357">如果類型的設計不會進化，請在 vanilla .NET Api 中使用 F # 記錄類型</span><span class="sxs-lookup"><span data-stu-id="2517f-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="2517f-358">F # 記錄類型會編譯成簡單的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="2517f-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="2517f-359">這些適用于 Api 中的一些簡單、穩定的類型。</span><span class="sxs-lookup"><span data-stu-id="2517f-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="2517f-360">請考慮使用 `[<NoEquality>]` 和 `[<NoComparison>]` 屬性，以隱藏介面的自動產生。</span><span class="sxs-lookup"><span data-stu-id="2517f-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="2517f-361">也請避免在 vanilla .NET Api 中使用可變動的記錄欄位，因為這些會公開公用欄位。</span><span class="sxs-lookup"><span data-stu-id="2517f-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="2517f-362">請務必考慮類別是否會針對 API 的未來演進提供更有彈性的選項。</span><span class="sxs-lookup"><span data-stu-id="2517f-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="2517f-363">例如，下列 F # 程式碼會向 c # 取用者公開公用 API：</span><span class="sxs-lookup"><span data-stu-id="2517f-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="2517f-364">F#：</span><span class="sxs-lookup"><span data-stu-id="2517f-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="2517f-365">C#：</span><span class="sxs-lookup"><span data-stu-id="2517f-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="2517f-366">隱藏 vanilla .NET Api 中的 F # 聯集類型標記法</span><span class="sxs-lookup"><span data-stu-id="2517f-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="2517f-367">F # 聯集類型不常用於整個元件界限，即使是 F # 對 F # 編碼也一樣。</span><span class="sxs-lookup"><span data-stu-id="2517f-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="2517f-368">它們是在元件和程式庫內部使用時的絕佳執行裝置。</span><span class="sxs-lookup"><span data-stu-id="2517f-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="2517f-369">設計 vanilla .NET API 時，請考慮使用私用宣告或簽章檔案來隱藏等位類型的標記法。</span><span class="sxs-lookup"><span data-stu-id="2517f-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="2517f-370">您也可以增強在內部使用聯集標記法的類型，以提供所需的。面向網路的 API。</span><span class="sxs-lookup"><span data-stu-id="2517f-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="2517f-371">使用架構的設計模式設計 GUI 和其他元件</span><span class="sxs-lookup"><span data-stu-id="2517f-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="2517f-372">.NET 中有許多不同的架構可供使用，例如 WinForms、WPF 和 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="2517f-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="2517f-373">如果您要設計要在這些架構中使用的元件，則應該使用每個的命名和設計慣例。</span><span class="sxs-lookup"><span data-stu-id="2517f-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="2517f-374">例如，在 WPF 程式設計中，會針對您要設計的類別採用 WPF 設計模式。</span><span class="sxs-lookup"><span data-stu-id="2517f-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="2517f-375">對於使用者介面程式設計中的模型，請使用像是事件和以通知為基礎的集合之類的設計模式，例如在中找到的 <xref:System.Collections.ObjectModel> 。</span><span class="sxs-lookup"><span data-stu-id="2517f-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="2517f-376">物件和成員設計（適用于從其他 .NET 語言使用的程式庫）</span><span class="sxs-lookup"><span data-stu-id="2517f-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="2517f-377">使用 CLIEvent 屬性來公開 .NET 事件</span><span class="sxs-lookup"><span data-stu-id="2517f-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="2517f-378">`DelegateEvent`使用特定的 .net 委派類型 `EventArgs` （而不是 `Event` 預設使用此類型的）來建立， `FSharpHandler` 以便將事件以熟悉的方式發行至其他 .net 語言。</span><span class="sxs-lookup"><span data-stu-id="2517f-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

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

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="2517f-379">將非同步作業公開為傳回 .NET 工作的方法</span><span class="sxs-lookup"><span data-stu-id="2517f-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="2517f-380">工作會在 .NET 中用來表示使用中的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="2517f-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="2517f-381">工作的複合一般少於 F # `Async<T>` 物件，因為它們代表「已執行」的工作，而且無法以執行平行組合的方式組合在一起，或是隱藏取消信號和其他內容參數的傳播。</span><span class="sxs-lookup"><span data-stu-id="2517f-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="2517f-382">不過，無論如何，傳回工作的方法，都是 .NET 上非同步程式設計的標準標記法。</span><span class="sxs-lookup"><span data-stu-id="2517f-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="2517f-383">您通常也會想要接受明確的取消權杖：</span><span class="sxs-lookup"><span data-stu-id="2517f-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="2517f-384">使用 .NET 委派類型，而不是 F # 函式類型</span><span class="sxs-lookup"><span data-stu-id="2517f-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="2517f-385">此處的 "F # 函式類型" 表示 "箭號" 類型 `int -> int` ，例如。</span><span class="sxs-lookup"><span data-stu-id="2517f-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="2517f-386">而不是：</span><span class="sxs-lookup"><span data-stu-id="2517f-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="2517f-387">執行此動作：</span><span class="sxs-lookup"><span data-stu-id="2517f-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="2517f-388">F # 函式類型會顯示為 `class FSharpFunc<T,U>` 其他 .net 語言，而且較不適合瞭解委派類型的語言功能和工具。</span><span class="sxs-lookup"><span data-stu-id="2517f-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="2517f-389">撰寫以 .NET Framework 3.5 或更高版本為目標的高階方法時， `System.Func` 和 `System.Action` 委派是正確發佈的 api，可讓 .net 開發人員以低摩擦的方式取用這些 api。</span><span class="sxs-lookup"><span data-stu-id="2517f-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="2517f-390">（以 .NET Framework 2.0 為目標時，系統定義的委派類型會受到限制; 請考慮使用預先定義的委派類型，例如 `System.Converter<T,U>` 或定義特定的委派類型）。</span><span class="sxs-lookup"><span data-stu-id="2517f-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="2517f-391">另一方面，對 F # 面向的程式庫而言，.NET 委派並非自然的（請參閱下一節的 F # 面向程式庫）。</span><span class="sxs-lookup"><span data-stu-id="2517f-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="2517f-392">因此，開發 vanilla .NET 程式庫的高階方法時，常見的實行策略是使用 F # 函式型別來撰寫所有的實作者，然後使用委派作為實際 F # 實作為的精簡外觀來建立公用 API。</span><span class="sxs-lookup"><span data-stu-id="2517f-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="2517f-393">使用 TryGetValue 模式，而不是傳回 F # 選項值，而且偏好方法多載，以 F # 選項值做為引數</span><span class="sxs-lookup"><span data-stu-id="2517f-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="2517f-394">在 Api 中使用 F # 選項類型的常見模式，會在使用標準 .NET 設計技術的 vanilla .NET Api 中獲得更好的運用。</span><span class="sxs-lookup"><span data-stu-id="2517f-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="2517f-395">請考慮使用 bool 傳回類型加上 out 參數，而不是傳回 F # 選項值，如同 "TryGetValue" 模式。</span><span class="sxs-lookup"><span data-stu-id="2517f-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="2517f-396">而不是採用 F # 選項值做為參數，請考慮使用方法多載或選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="2517f-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="2517f-397">使用 .NET 集合介面類別型 IEnumerable \< T \> 和 IDictionary 索引 \< 鍵， \> 參數和傳回值的值</span><span class="sxs-lookup"><span data-stu-id="2517f-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="2517f-398">請避免使用具象的集合類型，例如 .NET 陣列 `T[]` 、F # `list<T>` 類型 `Map<Key,Value>` 和 `Set<T>` ，以及 .net 具體集合類型（例如） `Dictionary<Key,Value>` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="2517f-399">.NET 程式庫設計指導方針有關於何時使用各種集合類型（例如）的良好建議 `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="2517f-400">在某些情況下，某些情況下可接受陣列（）的某些使用 `T[]` ，而效能則是。</span><span class="sxs-lookup"><span data-stu-id="2517f-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="2517f-401">請注意 `seq<T>` ，這只是的 F # 別名 `IEnumerable<T>` ，因此 seq 通常是 VANILLA .net API 的適當類型。</span><span class="sxs-lookup"><span data-stu-id="2517f-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="2517f-402">而不是 F # 清單：</span><span class="sxs-lookup"><span data-stu-id="2517f-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="2517f-403">使用 F # 序列：</span><span class="sxs-lookup"><span data-stu-id="2517f-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="2517f-404">使用 unit 類型做為方法的唯一輸入類型，以定義零引數方法，或當做唯一傳回類型來定義傳回 void 的方法</span><span class="sxs-lookup"><span data-stu-id="2517f-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="2517f-405">避免使用單位類型的其他用途。</span><span class="sxs-lookup"><span data-stu-id="2517f-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="2517f-406">這是很好的：</span><span class="sxs-lookup"><span data-stu-id="2517f-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="2517f-407">這是不正確的：</span><span class="sxs-lookup"><span data-stu-id="2517f-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="2517f-408">在 vanilla .NET API 界限上檢查是否有 null 值</span><span class="sxs-lookup"><span data-stu-id="2517f-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="2517f-409">F # 執行程式碼通常會有較少的 null 值，因為不變的設計模式和針對 F # 類型使用 null 常值的限制。</span><span class="sxs-lookup"><span data-stu-id="2517f-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="2517f-410">其他 .NET 語言通常會使用 null 做為值的頻率更高。</span><span class="sxs-lookup"><span data-stu-id="2517f-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="2517f-411">因此，公開 vanilla .NET API 的 F # 程式碼應該在 API 界限檢查參數是否為 null，並防止這些值更深入地轉換成 F # 的執行程式碼。</span><span class="sxs-lookup"><span data-stu-id="2517f-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="2517f-412">您 `isNull` 可以使用模式的函數或模式比對 `null` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="2517f-413">避免使用元組做為傳回值</span><span class="sxs-lookup"><span data-stu-id="2517f-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="2517f-414">相反地，偏好傳回包含匯總資料的已命名類型，或使用 out 參數傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="2517f-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="2517f-415">雖然元組和結構元組存在於 .NET 中（包括結構元組的 c # 語言支援），但它們通常不會為 .NET 開發人員提供理想且預期的 API。</span><span class="sxs-lookup"><span data-stu-id="2517f-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="2517f-416">避免使用 currying 的參數</span><span class="sxs-lookup"><span data-stu-id="2517f-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="2517f-417">請改用 .NET 呼叫慣例 `Method(arg1,arg2,…,argN)` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="2517f-418">提示：如果您要設計可從任何 .NET 語言使用的程式庫，則不會實際進行實驗性 c # 和 Visual Basic 程式設計，以確保您的程式庫能夠從這些語言中「感覺正確」。</span><span class="sxs-lookup"><span data-stu-id="2517f-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="2517f-419">您也可以使用 .NET 反映程式和 Visual Studio 物件瀏覽器等工具，確保程式庫和其檔會如預期般出現給開發人員。</span><span class="sxs-lookup"><span data-stu-id="2517f-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="2517f-420">附錄</span><span class="sxs-lookup"><span data-stu-id="2517f-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="2517f-421">設計可供其他 .NET 語言使用之 F # 程式碼的端對端範例</span><span class="sxs-lookup"><span data-stu-id="2517f-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="2517f-422">請考慮下列類別：</span><span class="sxs-lookup"><span data-stu-id="2517f-422">Consider the following class:</span></span>

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

<span data-ttu-id="2517f-423">此類別的推斷 F # 類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="2517f-423">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="2517f-424">讓我們看看這個 F # 型別如何使用另一個 .NET 語言來呈現給程式設計人員。</span><span class="sxs-lookup"><span data-stu-id="2517f-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="2517f-425">例如，大約的 c # "signature" 如下所示：</span><span class="sxs-lookup"><span data-stu-id="2517f-425">For example, the approximate C# "signature" is as follows:</span></span>

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

<span data-ttu-id="2517f-426">關於 F # 如何代表此處的結構，有一些值得注意的重點。</span><span class="sxs-lookup"><span data-stu-id="2517f-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="2517f-427">例如：</span><span class="sxs-lookup"><span data-stu-id="2517f-427">For example:</span></span>

* <span data-ttu-id="2517f-428">已保留引數名稱之類的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="2517f-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="2517f-429">採用兩個引數的 F # 方法會變成接受兩個引數的 c # 方法。</span><span class="sxs-lookup"><span data-stu-id="2517f-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="2517f-430">函數和清單會變成 F # 程式庫中對應類型的參考。</span><span class="sxs-lookup"><span data-stu-id="2517f-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="2517f-431">下列程式碼示範如何調整此程式碼，以將這些專案納入考慮。</span><span class="sxs-lookup"><span data-stu-id="2517f-431">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="2517f-432">程式碼的推斷 F # 類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="2517f-432">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="2517f-433">C # 簽名現在如下所示：</span><span class="sxs-lookup"><span data-stu-id="2517f-433">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="2517f-434">為了準備此類型做為 vanilla .NET 程式庫的一部分而進行的修正，如下所示：</span><span class="sxs-lookup"><span data-stu-id="2517f-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="2517f-435">已調整數個名稱： `Point1` 、 `n` 、 `l` 和會 `f` `RadialPoint` 分別成為、 `count` 、 `factor` 和 `transform` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="2517f-436">使用的傳回型別， `seq<RadialPoint>` 而不是使用 `RadialPoint list` 來變更清單結構，而不是使用 `[ ... ]` `IEnumerable<RadialPoint>` 。</span><span class="sxs-lookup"><span data-stu-id="2517f-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="2517f-437">使用 .NET 委派類型， `System.Func` 而不是 F # 函式類型。</span><span class="sxs-lookup"><span data-stu-id="2517f-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="2517f-438">這讓它在 c # 程式碼中的更好變得更大。</span><span class="sxs-lookup"><span data-stu-id="2517f-438">This makes it far nicer to consume in C# code.</span></span>
