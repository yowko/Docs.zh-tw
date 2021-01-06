---
title: F# 元件設計指導
description: '瞭解撰寫適用于其他呼叫者取用之 F # 元件的指導方針。'
ms.date: 05/14/2018
ms.openlocfilehash: 24be2a422c97b9334f749e3d9dfcccd0feec219b
ms.sourcegitcommit: e395fabeeea5c705d243d246fa64446839ac85b6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/03/2021
ms.locfileid: "97856103"
---
# <a name="f-component-design-guidelines"></a><span data-ttu-id="7cc8e-103">F# 元件設計指導</span><span class="sxs-lookup"><span data-stu-id="7cc8e-103">F# component design guidelines</span></span>

<span data-ttu-id="7cc8e-104">本檔是一組 F # 程式設計的元件設計方針，以 F # 元件設計指導方針、v14、Microsoft Research 以及 F # Software Foundation 原本策劃和維護的版本為基礎。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-104">This document is a set of component design guidelines for F# programming, based on the F# Component Design Guidelines, v14, Microsoft Research, and a version that was originally curated and maintained by the F# Software Foundation.</span></span>

<span data-ttu-id="7cc8e-105">本檔假設您已熟悉 F # 程式設計。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-105">This document assumes you are familiar with F# programming.</span></span> <span data-ttu-id="7cc8e-106">很多人都感謝 F # 團體參與本指南的各種版本的投稿和實用意見反應。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-106">Many thanks to the F# community for their contributions and helpful feedback on various versions of this guide.</span></span>

## <a name="overview"></a><span data-ttu-id="7cc8e-107">總覽</span><span class="sxs-lookup"><span data-stu-id="7cc8e-107">Overview</span></span>

<span data-ttu-id="7cc8e-108">本檔探討一些與 F # 元件設計和程式碼相關的問題。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-108">This document looks at some of the issues related to F# component design and coding.</span></span> <span data-ttu-id="7cc8e-109">元件可以表示下列其中一項：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-109">A component can mean any of the following:</span></span>

* <span data-ttu-id="7cc8e-110">在 F # 專案中，具有該專案內外部取用者的圖層。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-110">A layer in your F# project that has external consumers within that project.</span></span>
* <span data-ttu-id="7cc8e-111">適用于跨元件界限的 F # 程式碼耗用量的程式庫。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-111">A library intended for consumption by F# code across assembly boundaries.</span></span>
* <span data-ttu-id="7cc8e-112">一種程式庫，可供跨元件界限的任何 .NET 語言取用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-112">A library intended for consumption by any .NET language across assembly boundaries.</span></span>
* <span data-ttu-id="7cc8e-113">適用于透過套件存放庫（例如 [NuGet](https://nuget.org)）散發的程式庫。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-113">A library intended for distribution via a package repository, such as [NuGet](https://nuget.org).</span></span>

<span data-ttu-id="7cc8e-114">本文所述的技術會遵循 [良好 F # 程式碼的五個準則](index.md#five-principles-of-good-f-code)，因此會適當地使用功能和物件程式設計。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-114">Techniques described in this article follow the [Five principles of good F# code](index.md#five-principles-of-good-f-code), and thus utilize both functional and object programming as appropriate.</span></span>

<span data-ttu-id="7cc8e-115">無論是哪一種方法，元件和程式庫設計師在嘗試製作最容易使用的 API 時，都面臨許多實際和平凡的問題。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-115">Regardless of the methodology, the component and library designer faces a number of practical and prosaic issues when trying to craft an API that is most easily usable by developers.</span></span> <span data-ttu-id="7cc8e-116">Conscientious 應用程式的 [.net 程式庫設計指導方針](../../standard/design-guidelines/index.md) ，將引導您建立一組一致的 api，以供使用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-116">Conscientious application of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md) will steer you towards creating a consistent set of APIs that are pleasant to consume.</span></span>

## <a name="general-guidelines"></a><span data-ttu-id="7cc8e-117">一般指導方針</span><span class="sxs-lookup"><span data-stu-id="7cc8e-117">General guidelines</span></span>

<span data-ttu-id="7cc8e-118">F # 程式庫有一些適用的通用指導方針，而不考慮程式庫的目標物件。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-118">There are a few universal guidelines that apply to F# libraries, regardless of the intended audience for the library.</span></span>

### <a name="learn-the-net-library-design-guidelines"></a><span data-ttu-id="7cc8e-119">瞭解 .NET 程式庫設計指導方針</span><span class="sxs-lookup"><span data-stu-id="7cc8e-119">Learn the .NET Library Design Guidelines</span></span>

<span data-ttu-id="7cc8e-120">無論您正在進行的 F # 程式碼撰寫種類為何，都有很大的説明，讓您瞭解 [.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-120">Regardless of the kind of F# coding you are doing, it is valuable to have a working knowledge of the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="7cc8e-121">大部分其他 F # 和 .NET 程式設計人員都將熟悉這些指導方針，並預期 .NET 程式碼必須符合這些方針。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-121">Most other F# and .NET programmers will be familiar with these guidelines, and expect .NET code to conform to them.</span></span>

<span data-ttu-id="7cc8e-122">.NET 程式庫設計指導方針提供有關命名、設計類別和介面、成員設計 (屬性、方法、事件等 ) 等等的一般指引，而且是各種設計指導的實用第一個參考重點。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-122">The .NET Library Design Guidelines provide general guidance regarding naming, designing classes and interfaces, member design (properties, methods, events, etc.) and more, and are a useful first point of reference for a variety of design guidance.</span></span>

### <a name="add-xml-documentation-comments-to-your-code"></a><span data-ttu-id="7cc8e-123">將 XML 檔批註新增至您的程式碼</span><span class="sxs-lookup"><span data-stu-id="7cc8e-123">Add XML documentation comments to your code</span></span>

<span data-ttu-id="7cc8e-124">適用于公用 Api 的 XML 檔可確保使用者在使用這些類型和成員時，可以取得絕佳的 Intellisense 和 Quickinfo，並為文件庫啟用建立檔檔。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-124">XML documentation on public APIs ensures that users can get great Intellisense and Quickinfo when using these types and members, and enable building documentation files for the library.</span></span> <span data-ttu-id="7cc8e-125">請參閱 [Xml 檔](../language-reference/xml-documentation.md) ，瞭解可用於 xmldoc 批註內其他標記的各種 xml 標記。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-125">See the [XML Documentation](../language-reference/xml-documentation.md) about various xml tags that can be used for additional markup within xmldoc comments.</span></span>

```fsharp
/// A class for representing (x,y) coordinates
type Point =

    /// Computes the distance between this point and another
    member DistanceTo: otherPoint:Point -> float
```

<span data-ttu-id="7cc8e-126">您可以使用簡短形式的 XML 批註 (`/// comment`) ，或 () 的標準 XML 批註 `///<summary>comment</summary>` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-126">You can use either the short form XML comments (`/// comment`), or standard XML comments (`///<summary>comment</summary>`).</span></span>

### <a name="consider-using-explicit-signature-files-fsi-for-stable-library-and-component-apis"></a><span data-ttu-id="7cc8e-127">請考慮針對穩定的程式庫和元件 Api 使用明確的簽章檔案 ( fsi) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-127">Consider using explicit signature files (.fsi) for stable library and component APIs</span></span>

<span data-ttu-id="7cc8e-128">使用 F # 程式庫中的明確簽章檔案可提供公用 API 的簡潔摘要，這有助於確保您知道媒體櫃的完整公開介面，並提供公開檔和內部實作為詳細資料的清楚分隔。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-128">Using explicit signatures files in an F# library provides a succinct summary of public API, which helps to ensure that you know the full public surface of your library, and provides a clean separation between public documentation and internal implementation details.</span></span> <span data-ttu-id="7cc8e-129">簽章檔案會藉由要求在執行和簽章檔案中進行變更，而增加了變更公用 API 的分歧。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-129">Signature files add friction to changing the public API, by requiring changes to be made in both the implementation and signature files.</span></span> <span data-ttu-id="7cc8e-130">如此一來，通常只會在 API 已 solidified，且不再需要大幅變更時，才會引進簽名檔。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-130">As a result, signature files should typically only be introduced when an API has become solidified and is no longer expected to change significantly.</span></span>

### <a name="always-follow-best-practices-for-using-strings-in-net"></a><span data-ttu-id="7cc8e-131">一律遵循在 .NET 中使用字串的最佳作法</span><span class="sxs-lookup"><span data-stu-id="7cc8e-131">Always follow best practices for using strings in .NET</span></span>

<span data-ttu-id="7cc8e-132">遵循 [在 .net 中使用字串的最佳作法](../../standard/base-types/best-practices-strings.md) 指引。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-132">Follow [Best Practices for Using Strings in .NET](../../standard/base-types/best-practices-strings.md) guidance.</span></span> <span data-ttu-id="7cc8e-133">尤其是，在適當的) 的情況下，一律明確地在字串轉換和比較 (中陳述 *文化意圖* 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-133">In particular, always explicitly state *cultural intent* in the conversion and comparison of strings (where applicable).</span></span>

## <a name="guidelines-for-f-facing-libraries"></a><span data-ttu-id="7cc8e-134">F # 面向程式庫的指導方針</span><span class="sxs-lookup"><span data-stu-id="7cc8e-134">Guidelines for F#-facing libraries</span></span>

<span data-ttu-id="7cc8e-135">本節說明開發公用 F # 面向程式庫的建議;也就是說，程式庫會公開公用 Api，供 F # 開發人員使用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-135">This section presents recommendations for developing public F#-facing libraries; that is, libraries exposing public APIs that are intended to be consumed by F# developers.</span></span> <span data-ttu-id="7cc8e-136">針對 F #，有各種適用的程式庫設計建議。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-136">There are a variety of library-design recommendations applicable specifically to F#.</span></span> <span data-ttu-id="7cc8e-137">如果沒有遵循的特定建議，.NET 程式庫設計指導方針就是回溯指引。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-137">In the absence of the specific recommendations that follow, the .NET Library Design Guidelines are the fallback guidance.</span></span>

### <a name="naming-conventions"></a><span data-ttu-id="7cc8e-138">命名規範</span><span class="sxs-lookup"><span data-stu-id="7cc8e-138">Naming conventions</span></span>

#### <a name="use-net-naming-and-capitalization-conventions"></a><span data-ttu-id="7cc8e-139">使用 .NET 命名和大小寫慣例</span><span class="sxs-lookup"><span data-stu-id="7cc8e-139">Use .NET naming and capitalization conventions</span></span>

<span data-ttu-id="7cc8e-140">下表會遵循 .NET 命名和大小寫慣例。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-140">The following table follows .NET naming and capitalization conventions.</span></span> <span data-ttu-id="7cc8e-141">另外還包含 F # 結構的新增功能。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-141">There are small additions to also include F# constructs.</span></span>

| <span data-ttu-id="7cc8e-142">建構</span><span class="sxs-lookup"><span data-stu-id="7cc8e-142">Construct</span></span> | <span data-ttu-id="7cc8e-143">案例</span><span class="sxs-lookup"><span data-stu-id="7cc8e-143">Case</span></span> | <span data-ttu-id="7cc8e-144">部分</span><span class="sxs-lookup"><span data-stu-id="7cc8e-144">Part</span></span> | <span data-ttu-id="7cc8e-145">範例</span><span class="sxs-lookup"><span data-stu-id="7cc8e-145">Examples</span></span> | <span data-ttu-id="7cc8e-146">注意</span><span class="sxs-lookup"><span data-stu-id="7cc8e-146">Notes</span></span> |
|-----------|------|------|----------|-------|
| <span data-ttu-id="7cc8e-147">具體類型</span><span class="sxs-lookup"><span data-stu-id="7cc8e-147">Concrete types</span></span> | <span data-ttu-id="7cc8e-148">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-148">PascalCase</span></span> | <span data-ttu-id="7cc8e-149">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-149">Noun/ adjective</span></span> | <span data-ttu-id="7cc8e-150">清單、雙重、複雜</span><span class="sxs-lookup"><span data-stu-id="7cc8e-150">List, Double, Complex</span></span> | <span data-ttu-id="7cc8e-151">具體類型是結構、類別、列舉、委派、記錄和等位。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-151">Concrete types are structs, classes, enumerations, delegates, records, and unions.</span></span> <span data-ttu-id="7cc8e-152">雖然型別名稱在 OCaml 中通常是小寫，但 F # 已採用類型的 .NET 命名配置。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-152">Though type names are traditionally lowercase in OCaml, F# has adopted the .NET naming scheme for types.</span></span>
| <span data-ttu-id="7cc8e-153">DLL</span><span class="sxs-lookup"><span data-stu-id="7cc8e-153">DLLs</span></span>           | <span data-ttu-id="7cc8e-154">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-154">PascalCase</span></span> |                 | <span data-ttu-id="7cc8e-155">Fabrikam.Core.dll</span><span class="sxs-lookup"><span data-stu-id="7cc8e-155">Fabrikam.Core.dll</span></span> |  |
| <span data-ttu-id="7cc8e-156">聯集標記</span><span class="sxs-lookup"><span data-stu-id="7cc8e-156">Union tags</span></span>     | <span data-ttu-id="7cc8e-157">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-157">PascalCase</span></span> | <span data-ttu-id="7cc8e-158">名詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-158">Noun</span></span> | <span data-ttu-id="7cc8e-159">部分、新增、成功</span><span class="sxs-lookup"><span data-stu-id="7cc8e-159">Some, Add, Success</span></span> | <span data-ttu-id="7cc8e-160">請勿在公用 Api 中使用前置詞。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-160">Do not use a prefix in public APIs.</span></span> <span data-ttu-id="7cc8e-161">（選擇性）在內部使用前置詞，例如 `type Teams = TAlpha | TBeta | TDelta.`</span><span class="sxs-lookup"><span data-stu-id="7cc8e-161">Optionally use a prefix when internal, such as `type Teams = TAlpha | TBeta | TDelta.`</span></span> |
| <span data-ttu-id="7cc8e-162">事件</span><span class="sxs-lookup"><span data-stu-id="7cc8e-162">Event</span></span>          | <span data-ttu-id="7cc8e-163">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-163">PascalCase</span></span> | <span data-ttu-id="7cc8e-164">動詞命令</span><span class="sxs-lookup"><span data-stu-id="7cc8e-164">Verb</span></span> | <span data-ttu-id="7cc8e-165">ValueChanged/ValueChanging</span><span class="sxs-lookup"><span data-stu-id="7cc8e-165">ValueChanged / ValueChanging</span></span> |  |
| <span data-ttu-id="7cc8e-166">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7cc8e-166">Exceptions</span></span>     | <span data-ttu-id="7cc8e-167">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-167">PascalCase</span></span> |      | <span data-ttu-id="7cc8e-168">WebException</span><span class="sxs-lookup"><span data-stu-id="7cc8e-168">WebException</span></span> | <span data-ttu-id="7cc8e-169">名稱的結尾應該是「例外狀況」。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-169">Name should end with "Exception".</span></span> |
| <span data-ttu-id="7cc8e-170">欄位</span><span class="sxs-lookup"><span data-stu-id="7cc8e-170">Field</span></span>          | <span data-ttu-id="7cc8e-171">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-171">PascalCase</span></span> | <span data-ttu-id="7cc8e-172">名詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-172">Noun</span></span> | <span data-ttu-id="7cc8e-173">CurrentName</span><span class="sxs-lookup"><span data-stu-id="7cc8e-173">CurrentName</span></span>  | |
| <span data-ttu-id="7cc8e-174">介面型別</span><span class="sxs-lookup"><span data-stu-id="7cc8e-174">Interface types</span></span> |  <span data-ttu-id="7cc8e-175">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-175">PascalCase</span></span> | <span data-ttu-id="7cc8e-176">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-176">Noun/ adjective</span></span> | <span data-ttu-id="7cc8e-177">IDisposable</span><span class="sxs-lookup"><span data-stu-id="7cc8e-177">IDisposable</span></span> | <span data-ttu-id="7cc8e-178">名稱應該以 "I" 開頭。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-178">Name should start with "I".</span></span> |
| <span data-ttu-id="7cc8e-179">方法</span><span class="sxs-lookup"><span data-stu-id="7cc8e-179">Method</span></span> |  <span data-ttu-id="7cc8e-180">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-180">PascalCase</span></span> |  <span data-ttu-id="7cc8e-181">動詞命令</span><span class="sxs-lookup"><span data-stu-id="7cc8e-181">Verb</span></span> | <span data-ttu-id="7cc8e-182">ToString</span><span class="sxs-lookup"><span data-stu-id="7cc8e-182">ToString</span></span> | |
| <span data-ttu-id="7cc8e-183">命名空間</span><span class="sxs-lookup"><span data-stu-id="7cc8e-183">Namespace</span></span> | <span data-ttu-id="7cc8e-184">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-184">PascalCase</span></span> | | <span data-ttu-id="7cc8e-185">Fsharp.core 核心</span><span class="sxs-lookup"><span data-stu-id="7cc8e-185">Microsoft.FSharp.Core</span></span> | <span data-ttu-id="7cc8e-186">一般來說 `<Organization>.<Technology>[.<Subnamespace>]` ，如果該技術與組織無關，就會捨棄組織。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-186">Generally use `<Organization>.<Technology>[.<Subnamespace>]`, though drop the organization if the technology is independent of organization.</span></span> |
| <span data-ttu-id="7cc8e-187">參數</span><span class="sxs-lookup"><span data-stu-id="7cc8e-187">Parameters</span></span> | <span data-ttu-id="7cc8e-188">camelCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-188">camelCase</span></span> | <span data-ttu-id="7cc8e-189">名詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-189">Noun</span></span> |  <span data-ttu-id="7cc8e-190">typeName、轉換、範圍</span><span class="sxs-lookup"><span data-stu-id="7cc8e-190">typeName, transform, range</span></span> | |
| <span data-ttu-id="7cc8e-191">let 值 (內部) </span><span class="sxs-lookup"><span data-stu-id="7cc8e-191">let values (internal)</span></span> | <span data-ttu-id="7cc8e-192">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-192">camelCase or PascalCase</span></span> | <span data-ttu-id="7cc8e-193">名詞/動詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-193">Noun/ verb</span></span> |  <span data-ttu-id="7cc8e-194">getValue、myTable</span><span class="sxs-lookup"><span data-stu-id="7cc8e-194">getValue, myTable</span></span> |
| <span data-ttu-id="7cc8e-195">讓值 (外部) </span><span class="sxs-lookup"><span data-stu-id="7cc8e-195">let values (external)</span></span> | <span data-ttu-id="7cc8e-196">camelCase 或 PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-196">camelCase or PascalCase</span></span> | <span data-ttu-id="7cc8e-197">名詞/動詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-197">Noun/verb</span></span>  | <span data-ttu-id="7cc8e-198">List. map，日期. Today</span><span class="sxs-lookup"><span data-stu-id="7cc8e-198">List.map, Dates.Today</span></span> | <span data-ttu-id="7cc8e-199">在遵循傳統的功能設計模式時，let 系結值通常是公用的。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-199">let-bound values are often public when following traditional functional design patterns.</span></span> <span data-ttu-id="7cc8e-200">不過，當識別碼可以從其他 .NET 語言使用時，通常會使用 PascalCase。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-200">However, generally use PascalCase when the identifier can be used from other .NET languages.</span></span> |
| <span data-ttu-id="7cc8e-201">屬性</span><span class="sxs-lookup"><span data-stu-id="7cc8e-201">Property</span></span>  | <span data-ttu-id="7cc8e-202">PascalCase</span><span class="sxs-lookup"><span data-stu-id="7cc8e-202">PascalCase</span></span>  | <span data-ttu-id="7cc8e-203">名詞/形容詞</span><span class="sxs-lookup"><span data-stu-id="7cc8e-203">Noun/ adjective</span></span>  | <span data-ttu-id="7cc8e-204">IsEndOfFile、背景色彩</span><span class="sxs-lookup"><span data-stu-id="7cc8e-204">IsEndOfFile, BackColor</span></span>  | <span data-ttu-id="7cc8e-205">布林值屬性通常使用的是，而且應該是肯定，如同在 IsEndOfFile 中，不會 IsNotEndOfFile。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-205">Boolean properties generally use Is and Can and should be affirmative, as in IsEndOfFile, not IsNotEndOfFile.</span></span>

#### <a name="avoid-abbreviations"></a><span data-ttu-id="7cc8e-206">避免縮寫</span><span class="sxs-lookup"><span data-stu-id="7cc8e-206">Avoid abbreviations</span></span>

<span data-ttu-id="7cc8e-207">.NET 指導方針不鼓勵使用縮寫 (例如「使用 `OnButtonClick` 而非」 `OnBtnClick` ) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-207">The .NET guidelines discourage the use of abbreviations (for example, "use `OnButtonClick` rather than `OnBtnClick`").</span></span> <span data-ttu-id="7cc8e-208">常見的縮寫（例如「 `Async` 非同步」）是容許的。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-208">Common abbreviations, such as `Async` for "Asynchronous", are tolerated.</span></span> <span data-ttu-id="7cc8e-209">這項指導方針有時會被忽略，以進行功能性程式設計;例如，會 `List.iter` 使用 "反覆運算" 的縮寫。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-209">This guideline is sometimes ignored for functional programming; for example, `List.iter` uses an abbreviation for "iterate".</span></span> <span data-ttu-id="7cc8e-210">基於這個理由，使用縮寫通常可以在 F # 對 F # 程式設計中獲得更高的程度，但仍應避免在公用元件設計中使用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-210">For this reason, using abbreviations tends to be tolerated to a greater degree in F#-to-F# programming, but should still generally be avoided in public component design.</span></span>

#### <a name="avoid-casing-name-collisions"></a><span data-ttu-id="7cc8e-211">避免大小寫名稱衝突</span><span class="sxs-lookup"><span data-stu-id="7cc8e-211">Avoid casing name collisions</span></span>

<span data-ttu-id="7cc8e-212">.NET 指導方針表示單獨使用大小寫，因為某些用戶端語言 (例如 Visual Basic) 不區分大小寫。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-212">The .NET guidelines say that casing alone cannot be used to disambiguate name collisions, since some client languages (for example, Visual Basic) are case-insensitive.</span></span>

#### <a name="use-acronyms-where-appropriate"></a><span data-ttu-id="7cc8e-213">適當時使用縮寫</span><span class="sxs-lookup"><span data-stu-id="7cc8e-213">Use acronyms where appropriate</span></span>

<span data-ttu-id="7cc8e-214">XML 之類的縮寫不是縮寫，而是廣泛用於 .NET 程式庫中的 uncapitalized 格式 (Xml) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-214">Acronyms such as XML are not abbreviations and are widely used in .NET libraries in uncapitalized form (Xml).</span></span> <span data-ttu-id="7cc8e-215">只應使用知名且廣泛辨識的縮寫。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-215">Only well-known, widely recognized acronyms should be used.</span></span>

#### <a name="use-pascalcase-for-generic-parameter-names"></a><span data-ttu-id="7cc8e-216">使用 PascalCase 進行泛型參數名稱</span><span class="sxs-lookup"><span data-stu-id="7cc8e-216">Use PascalCase for generic parameter names</span></span>

<span data-ttu-id="7cc8e-217">請在公用 Api 中使用泛型參數名稱的 PascalCase，包括 F # 面向的程式庫。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-217">Do use PascalCase for generic parameter names in public APIs, including for F#-facing libraries.</span></span> <span data-ttu-id="7cc8e-218">尤其是，針對 `T` `U` 任意泛型參數使用、、、等名稱 `T1` `T2` ，而且當特定名稱有意義時，對於 F # 對應的程式庫，請使用如 `Key` 、 `Value` 、 `Arg` (但不是 `TKey`) 的名稱。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-218">In particular, use names like `T`, `U`, `T1`, `T2` for arbitrary generic parameters, and when specific names make sense, then for F#-facing libraries use names like `Key`, `Value`, `Arg` (but not for example, `TKey`).</span></span>

#### <a name="use-either-pascalcase-or-camelcase-for-public-functions-and-values-in-f-modules"></a><span data-ttu-id="7cc8e-219">將 PascalCase 或 camelCase 用於 F # 模組中的公用函式和值</span><span class="sxs-lookup"><span data-stu-id="7cc8e-219">Use either PascalCase or camelCase for public functions and values in F# modules</span></span>

<span data-ttu-id="7cc8e-220">camelCase 適用于設計為使用非限定 (的公用函式，例如 `invalidArg`) ，以及「標準集合函式」 (例如，List. map) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-220">camelCase is used for public functions that are designed to be used unqualified (for example, `invalidArg`), and for the "standard collection functions" (for example, List.map).</span></span> <span data-ttu-id="7cc8e-221">在這兩種情況下，函式名稱的作用相當於語言中的關鍵字。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-221">In both these cases, the function names act much like keywords in the language.</span></span>

### <a name="object-type-and-module-design"></a><span data-ttu-id="7cc8e-222">物件、類型和模組設計</span><span class="sxs-lookup"><span data-stu-id="7cc8e-222">Object, Type, and Module design</span></span>

#### <a name="use-namespaces-or-modules-to-contain-your-types-and-modules"></a><span data-ttu-id="7cc8e-223">使用命名空間或模組來包含您的類型和模組</span><span class="sxs-lookup"><span data-stu-id="7cc8e-223">Use namespaces or modules to contain your types and modules</span></span>

<span data-ttu-id="7cc8e-224">元件中的每個 F # 檔案都應該以命名空間宣告或模組宣告做為開頭。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-224">Each F# file in a component should begin with either a namespace declaration or a module declaration.</span></span>

```fsharp
namespace Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
     ...

module CommonOperations =
    ...
```

<span data-ttu-id="7cc8e-225">或</span><span class="sxs-lookup"><span data-stu-id="7cc8e-225">or</span></span>

```fsharp
module Fabrikam.BasicOperationsAndTypes

type ObjectType1() =
    ...

type ObjectType2() =
    ...

module CommonOperations =
    ...
```

<span data-ttu-id="7cc8e-226">使用模組與命名空間來組織最上層程式碼的差異如下：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-226">The differences between using modules and namespaces to organize code at the top level are as follows:</span></span>

* <span data-ttu-id="7cc8e-227">命名空間可以橫跨多個檔案</span><span class="sxs-lookup"><span data-stu-id="7cc8e-227">Namespaces can span multiple files</span></span>
* <span data-ttu-id="7cc8e-228">命名空間不能包含 F # 函數，除非它們在內部模組內</span><span class="sxs-lookup"><span data-stu-id="7cc8e-228">Namespaces cannot contain F# functions unless they are within an inner module</span></span>
* <span data-ttu-id="7cc8e-229">任何指定模組的程式碼都必須包含在單一檔案中</span><span class="sxs-lookup"><span data-stu-id="7cc8e-229">The code for any given module must be contained within a single file</span></span>
* <span data-ttu-id="7cc8e-230">最上層模組可以包含 F # 函式，而不需要內部模組</span><span class="sxs-lookup"><span data-stu-id="7cc8e-230">Top-level modules can contain F# functions without the need for an inner module</span></span>

<span data-ttu-id="7cc8e-231">最上層命名空間或模組之間的選擇會影響程式碼的編譯格式，因此，如果您的 API 最終是在 F # 程式碼之外使用，則會影響其他 .NET 語言的視圖。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-231">The choice between a top-level namespace or module affects the compiled form of the code, and thus will affect the view from other .NET languages should your API eventually be consumed outside of F# code.</span></span>

#### <a name="use-methods-and-properties-for-operations-intrinsic-to-object-types"></a><span data-ttu-id="7cc8e-232">針對物件類型的作業使用方法和屬性</span><span class="sxs-lookup"><span data-stu-id="7cc8e-232">Use methods and properties for operations intrinsic to object types</span></span>

<span data-ttu-id="7cc8e-233">使用物件時，最好確保取用的功能會實作為該類型上的方法和屬性。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-233">When working with objects, it is best to ensure that consumable functionality is implemented as methods and properties on that type.</span></span>

```fsharp
type HardwareDevice() =

    member this.ID = ...

    member this.SupportedProtocols = ...

type HashTable<'Key,'Value>(comparer: IEqualityComparer<'Key>) =

    member this.Add(key, value) = ...

    member this.ContainsKey(key) = ...

    member this.ContainsValue(value) = ...
```

<span data-ttu-id="7cc8e-234">指定成員的大量功能不一定要在該成員中實作為，但該功能的取用部分應該是。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-234">The bulk of functionality for a given member need not necessarily be implemented in that member, but the consumable piece of that functionality should be.</span></span>

#### <a name="use-classes-to-encapsulate-mutable-state"></a><span data-ttu-id="7cc8e-235">使用類別封裝可變動狀態</span><span class="sxs-lookup"><span data-stu-id="7cc8e-235">Use classes to encapsulate mutable state</span></span>

<span data-ttu-id="7cc8e-236">在 F # 中，這只需要在尚未由另一種語言結構（例如，關閉、序列運算式或非同步計算）封裝的狀態下完成。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-236">In F#, this only needs to be done where that state is not already encapsulated by another language construct, such as a closure, sequence expression, or asynchronous computation.</span></span>

```fsharp
type Counter() =
    // let-bound values are private in classes.
    let mutable count = 0

    member this.Next() =
        count <- count + 1
        count
```

#### <a name="use-interfaces-to-group-related-operations"></a><span data-ttu-id="7cc8e-237">使用介面來分組相關的作業</span><span class="sxs-lookup"><span data-stu-id="7cc8e-237">Use interfaces to group related operations</span></span>

<span data-ttu-id="7cc8e-238">使用介面類別型來代表一組作業。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-238">Use interface types to represent a set of operations.</span></span> <span data-ttu-id="7cc8e-239">這是其他選項的慣用選項，例如函數的元組或函式的記錄。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-239">This is preferred to other options, such as tuples of functions or records of functions.</span></span>

```fsharp
type Serializer =
    abstract Serialize<'T> : preserveRefEq: bool -> value: 'T -> string
    abstract Deserialize<'T> : preserveRefEq: bool -> pickle: string -> 'T
```

<span data-ttu-id="7cc8e-240">依喜好設定：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-240">In preference to:</span></span>

```fsharp
type Serializer<'T> = {
    Serialize: bool -> 'T -> string
    Deserialize: bool -> string -> 'T
}
```

<span data-ttu-id="7cc8e-241">介面是 .NET 中的第一級概念，您可以用來達成函子一般提供的功能。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-241">Interfaces are first-class concepts in .NET, which you can use to achieve what Functors would normally give you.</span></span> <span data-ttu-id="7cc8e-242">此外，它們也可以用來將存在類型編碼到您的程式中，而無法使用哪些功能記錄。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-242">Additionally, they can be used to encode existential types into your program, which records of functions cannot.</span></span>

#### <a name="use-a-module-to-group-functions-that-act-on-collections"></a><span data-ttu-id="7cc8e-243">使用模組將處理集合的函式分組</span><span class="sxs-lookup"><span data-stu-id="7cc8e-243">Use a module to group functions that act on collections</span></span>

<span data-ttu-id="7cc8e-244">當您定義集合類型時，請考慮為新的集合類型提供一組標準的作業，例如 `CollectionType.map` 和 `CollectionType.iter`) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-244">When you define a collection type, consider providing a standard set of operations like `CollectionType.map` and `CollectionType.iter`) for new collection types.</span></span>

```fsharp
module CollectionType =
    let map f c =
        ...
    let iter f c =
        ...
```

<span data-ttu-id="7cc8e-245">如果您包含這類別模組，請遵循 Fsharp.core 中所找到函式的標準命名慣例。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-245">If you include such a module, follow the standard naming conventions for functions found in FSharp.Core.</span></span>

#### <a name="use-a-module-to-group-functions-for-common-canonical-functions-especially-in-math-and-dsl-libraries"></a><span data-ttu-id="7cc8e-246">使用模組來分組一般標準函式的功能，特別是在數學和 DSL 程式庫中</span><span class="sxs-lookup"><span data-stu-id="7cc8e-246">Use a module to group functions for common, canonical functions, especially in math and DSL libraries</span></span>

<span data-ttu-id="7cc8e-247">例如， `Microsoft.FSharp.Core.Operators` 會自動開啟最上層函式的集合 (例如 `abs` 和 FSharp.Core.dll 所 `sin` 提供的) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-247">For example, `Microsoft.FSharp.Core.Operators` is an automatically opened collection of top-level functions (like `abs` and `sin`) provided by FSharp.Core.dll.</span></span>

<span data-ttu-id="7cc8e-248">同樣地，統計資料連結庫可能包含具有函式的模組， `erf` 以及 `erfc` 此模組是設計為明確或自動開啟的。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-248">Likewise, a statistics library might include a module with functions `erf` and `erfc`, where this module is designed to be explicitly or automatically opened.</span></span>

#### <a name="consider-using-requirequalifiedaccess-and-carefully-apply-autoopen-attributes"></a><span data-ttu-id="7cc8e-249">考慮使用 RequireQualifiedAccess 並小心套用 AutoOpen 屬性</span><span class="sxs-lookup"><span data-stu-id="7cc8e-249">Consider using RequireQualifiedAccess and carefully apply AutoOpen attributes</span></span>

<span data-ttu-id="7cc8e-250">將 `[<RequireQualifiedAccess>]` 屬性新增至模組，表示模組可能無法開啟，而且模組的元素參考需要明確的存取權。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-250">Adding the `[<RequireQualifiedAccess>]` attribute to a module indicates that the module may not be opened and that references to the elements of the module require explicit qualified access.</span></span> <span data-ttu-id="7cc8e-251">例如， `Microsoft.FSharp.Collections.List` 模組有這個屬性。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-251">For example, the `Microsoft.FSharp.Collections.List` module has this attribute.</span></span>

<span data-ttu-id="7cc8e-252">當模組中的函式和值有可能與其他模組中的名稱衝突的名稱時，這非常有用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-252">This is useful when functions and values in the module have names that are likely to conflict with names in other modules.</span></span> <span data-ttu-id="7cc8e-253">需要限定存取權可能會大幅增加資源庫的長期維護和 evolvability。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-253">Requiring qualified access can greatly increase the long-term maintainability and evolvability of a library.</span></span>

<span data-ttu-id="7cc8e-254">將 `[<AutoOpen>]` 屬性加入至模組時，表示當包含的命名空間開啟時，將會開啟模組。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-254">Adding the `[<AutoOpen>]` attribute to a module means the module will be opened when the containing namespace is opened.</span></span> <span data-ttu-id="7cc8e-255">`[<AutoOpen>]`屬性也可以套用至元件，以指出參考元件時自動開啟的模組。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-255">The `[<AutoOpen>]` attribute may also be applied to an assembly to indicate a module that is automatically opened when the assembly is referenced.</span></span>

<span data-ttu-id="7cc8e-256">例如，統計資料連結庫 **MathsHeaven。統計資料** 可能包含 `module MathsHeaven.Statistics.Operators` 包含函數 `erf` 和 `erfc` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-256">For example, a statistics library **MathsHeaven.Statistics** might contain a `module MathsHeaven.Statistics.Operators` containing functions `erf` and `erfc`.</span></span> <span data-ttu-id="7cc8e-257">將此模組標示為是合理的 `[<AutoOpen>]` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-257">It is reasonable to mark this module as `[<AutoOpen>]`.</span></span> <span data-ttu-id="7cc8e-258">這表示 `open MathsHeaven.Statistics` 也會開啟此模組，並將名稱 `erf` 和移 `erfc` 至範圍中。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-258">This means `open MathsHeaven.Statistics` will also open this module and bring the names `erf` and `erfc` into scope.</span></span> <span data-ttu-id="7cc8e-259">的另一種用法 `[<AutoOpen>]` 是針對包含擴充方法的模組。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-259">Another good use of `[<AutoOpen>]` is for modules containing extension methods.</span></span>

<span data-ttu-id="7cc8e-260">過度 `[<AutoOpen>]` 使用潛在客戶污染命名空間，而屬性應謹慎使用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-260">Overuse of `[<AutoOpen>]` leads to polluted namespaces, and the attribute should be used with care.</span></span> <span data-ttu-id="7cc8e-261">針對特定網域中的特定程式庫，合理使用 `[<AutoOpen>]` 可能會導致更好的可用性。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-261">For specific libraries in specific domains, judicious use of `[<AutoOpen>]` can lead to better usability.</span></span>

#### <a name="consider-defining-operator-members-on-classes-where-using-well-known-operators-is-appropriate"></a><span data-ttu-id="7cc8e-262">請考慮在適當使用已知運算子的類別上定義運算子成員</span><span class="sxs-lookup"><span data-stu-id="7cc8e-262">Consider defining operator members on classes where using well-known operators is appropriate</span></span>

<span data-ttu-id="7cc8e-263">有時類別會用來建立數學結構（例如向量）的模型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-263">Sometimes classes are used to model mathematical constructs such as Vectors.</span></span> <span data-ttu-id="7cc8e-264">當模型化的網域有已知運算子時，將它們定義為類別內建的成員會很有説明。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-264">When the domain being modeled has well-known operators, defining them as members intrinsic to the class is helpful.</span></span>

```fsharp
type Vector(x: float) =

    member v.X = x

    static member (*) (vector: Vector, scalar: float) = Vector(vector.X * scalar)

    static member (+) (vector1: Vector, vector2: Vector) = Vector(vector1.X + vector2.X)

let v = Vector(5.0)

let u = v * 10.0
```

<span data-ttu-id="7cc8e-265">本指南對應于這些類型的一般 .NET 指引。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-265">This guidance corresponds to general .NET guidance for these types.</span></span> <span data-ttu-id="7cc8e-266">不過，這在 F # 程式碼中可能也很重要，因為這可讓這些型別搭配使用 F # 函式和具有成員條件約束的方法，例如 sumBy。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-266">However, it can be additionally important in F# coding as this allows these types to be used in conjunction with F# functions and methods with member constraints, such as List.sumBy.</span></span>

#### <a name="consider-using-compiledname-to-provide-a-net-friendly-name-for-other-net-language-consumers"></a><span data-ttu-id="7cc8e-267">請考慮使用 CompiledName 來提供。其他 .NET 語言取用者的網路易記名稱</span><span class="sxs-lookup"><span data-stu-id="7cc8e-267">Consider using CompiledName to provide a .NET-friendly name for other .NET language consumers</span></span>

<span data-ttu-id="7cc8e-268">有時您可能會想要為 F # 取用者以一種樣式來命名某個樣式 (例如，以小寫的成員形式出現，使其看起來像是模組系結函式) ，但在編譯成元件時，名稱會有不同的樣式。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-268">Sometimes you may wish to name something in one style for F# consumers (such as a static member in lower case so that it appears as if it were a module-bound function), but have a different style for the name when it is compiled into an assembly.</span></span> <span data-ttu-id="7cc8e-269">您可以使用 `[<CompiledName>]` 屬性，為使用元件的非 F # 程式碼提供不同的樣式。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-269">You can use the `[<CompiledName>]` attribute to provide a different style for non F# code consuming the assembly.</span></span>

```fsharp
type Vector(x:float, y:float) =

    member v.X = x
    member v.Y = y

    [<CompiledName("Create")>]
    static member create x y = Vector (x, y)

let v = Vector.create 5.0 3.0
```

<span data-ttu-id="7cc8e-270">藉由使用 `[<CompiledName>]` ，您可以針對元件的非 F # 取用者使用 .net 命名慣例。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-270">By using `[<CompiledName>]`, you can use .NET naming conventions for non F# consumers of the assembly.</span></span>

#### <a name="use-method-overloading-for-member-functions-if-doing-so-provides-a-simpler-api"></a><span data-ttu-id="7cc8e-271">使用成員函式的方法多載，如果這樣做會提供更簡單的 API</span><span class="sxs-lookup"><span data-stu-id="7cc8e-271">Use method overloading for member functions, if doing so provides a simpler API</span></span>

<span data-ttu-id="7cc8e-272">方法多載是一種功能強大的工具，可簡化可能需要執行類似功能的 API，但使用不同的選項或引數。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-272">Method overloading is a powerful tool for simplifying an API that may need to perform similar functionality, but with different options or arguments.</span></span>

```fsharp
type Logger() =

    member this.Log(message) =
        ...
    member this.Log(message, retryPolicy) =
        ...
```

<span data-ttu-id="7cc8e-273">在 F # 中，在引數數目而非引數類型上多載更為常見。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-273">In F#, it is more common to overload on number of arguments rather than types of arguments.</span></span>

#### <a name="hide-the-representations-of-record-and-union-types-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="7cc8e-274">如果這些類型的設計可能會進化，則隱藏記錄和聯集類型的表示</span><span class="sxs-lookup"><span data-stu-id="7cc8e-274">Hide the representations of record and union types if the design of these types is likely to evolve</span></span>

<span data-ttu-id="7cc8e-275">避免洩漏物件的具體標記法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-275">Avoid revealing concrete representations of objects.</span></span> <span data-ttu-id="7cc8e-276">例如， <xref:System.DateTime> .net 程式庫設計的外部公用 API 不會顯示值的具體標記法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-276">For example, the concrete representation of <xref:System.DateTime> values is not revealed by the external, public API of the .NET library design.</span></span> <span data-ttu-id="7cc8e-277">在執行時間，通用語言執行平臺會知道將在執行期間使用的認可的實作為。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-277">At run time, the Common Language Runtime knows the committed implementation that will be used throughout execution.</span></span> <span data-ttu-id="7cc8e-278">不過，已編譯的程式碼不會自行收取具體標記法的相依性。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-278">However, compiled code doesn't itself pick up dependencies on the concrete representation.</span></span>

#### <a name="avoid-the-use-of-implementation-inheritance-for-extensibility"></a><span data-ttu-id="7cc8e-279">避免使用擴充性的實作為繼承</span><span class="sxs-lookup"><span data-stu-id="7cc8e-279">Avoid the use of implementation inheritance for extensibility</span></span>

<span data-ttu-id="7cc8e-280">在 F # 中，很少使用執行繼承。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-280">In F#, implementation inheritance is rarely used.</span></span> <span data-ttu-id="7cc8e-281">此外，繼承階層通常很複雜，而且在新的需求抵達時很難變更。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-281">Furthermore, inheritance hierarchies are often complex and difficult to change when new requirements arrive.</span></span> <span data-ttu-id="7cc8e-282">在 F # 中，繼承實行仍存在於 F # 中，以提供最適合問題的解決方案，但在設計多型（例如介面執行）時，您應該在 F # 程式中尋找替代的技巧。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-282">Inheritance implementation still exists in F# for compatibility and rare cases where it is the best solution to a problem, but alternative techniques should be sought in your F# programs when designing for polymorphism, such as interface implementation.</span></span>

### <a name="function-and-member-signatures"></a><span data-ttu-id="7cc8e-283">函式和成員特徵標記</span><span class="sxs-lookup"><span data-stu-id="7cc8e-283">Function and member signatures</span></span>

#### <a name="use-tuples-for-return-values-when-returning-a-small-number-of-multiple-unrelated-values"></a><span data-ttu-id="7cc8e-284">傳回少量的多個不相關值時，使用元組來傳回值</span><span class="sxs-lookup"><span data-stu-id="7cc8e-284">Use tuples for return values when returning a small number of multiple unrelated values</span></span>

<span data-ttu-id="7cc8e-285">以下是在傳回型別中使用元組的絕佳範例：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-285">Here is a good example of using a tuple in a return type:</span></span>

```fsharp
val divrem: BigInteger -> BigInteger -> BigInteger * BigInteger
```

<span data-ttu-id="7cc8e-286">針對包含許多元件的傳回型別，或元件與單一可識別實體相關的位置，請考慮使用命名的型別，而不是元組。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-286">For return types containing many components, or where the components are related to a single identifiable entity, consider using a named type instead of a tuple.</span></span>

#### <a name="use-asynct-for-async-programming-at-f-api-boundaries"></a><span data-ttu-id="7cc8e-287">`Async<T>`在 F # API 界限上用於非同步程式設計</span><span class="sxs-lookup"><span data-stu-id="7cc8e-287">Use `Async<T>` for async programming at F# API boundaries</span></span>

<span data-ttu-id="7cc8e-288">如果有一個名為的對應同步作業會傳回 `Operation` `T` ，則非同步作業應命名為， `AsyncOperation` 如果它傳回 `Async<T>` 或傳回 `OperationAsync` `Task<T>` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-288">If there is a corresponding synchronous operation named `Operation` that returns a `T`, then the async operation should be named `AsyncOperation` if it returns `Async<T>` or `OperationAsync` if it returns `Task<T>`.</span></span> <span data-ttu-id="7cc8e-289">對於公開 Begin/End 方法的常用 .NET 型別，請考慮使用 `Async.FromBeginEnd` 將擴充方法撰寫為外觀，以提供 F # 非同步程式設計模型給這些 .Net api。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-289">For commonly used .NET types that expose Begin/End methods, consider using `Async.FromBeginEnd` to write extension methods as a façade to provide the F# async programming model to those .NET APIs.</span></span>

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

### <a name="exceptions"></a><span data-ttu-id="7cc8e-290">例外狀況</span><span class="sxs-lookup"><span data-stu-id="7cc8e-290">Exceptions</span></span>

<span data-ttu-id="7cc8e-291">請參閱 [錯誤管理](conventions.md#error-management) ，以瞭解例外狀況、結果和選項的適當用法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-291">See [Error Management](conventions.md#error-management) to learn about appropriate use of exceptions, results, and options.</span></span>

### <a name="extension-members"></a><span data-ttu-id="7cc8e-292">延伸模組成員</span><span class="sxs-lookup"><span data-stu-id="7cc8e-292">Extension Members</span></span>

#### <a name="carefully-apply-f-extension-members-in-f-to-f-components"></a><span data-ttu-id="7cc8e-293">謹慎地在 F # 到 F # 元件中套用 F # 擴充功能成員</span><span class="sxs-lookup"><span data-stu-id="7cc8e-293">Carefully apply F# extension members in F#-to-F# components</span></span>

<span data-ttu-id="7cc8e-294">F # 延伸模組成員通常只適用于在大部分使用模式中，與型別相關聯之內建作業的封閉作業。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-294">F# extension members should generally only be used for operations that are in the closure of intrinsic operations associated with a type in the majority of its modes of use.</span></span> <span data-ttu-id="7cc8e-295">其中一個常見用途是提供針對各種 .NET 類型更慣用至 F # 的 Api：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-295">One common use is to provide APIs that are more idiomatic to F# for various .NET types:</span></span>

```fsharp
type System.ServiceModel.Channels.IInputChannel with
    member this.AsyncReceive() =
        Async.FromBeginEnd(this.BeginReceive, this.EndReceive)

type System.Collections.Generic.IDictionary<'Key,'Value> with
    member this.TryGet key =
        let ok, v = this.TryGetValue key
        if ok then Some v else None
```

### <a name="union-types"></a><span data-ttu-id="7cc8e-296">聯集類型</span><span class="sxs-lookup"><span data-stu-id="7cc8e-296">Union Types</span></span>

#### <a name="use-discriminated-unions-instead-of-class-hierarchies-for-tree-structured-data"></a><span data-ttu-id="7cc8e-297">針對樹狀結構資料使用差異聯集，而非類別階層</span><span class="sxs-lookup"><span data-stu-id="7cc8e-297">Use discriminated unions instead of class hierarchies for tree-structured data</span></span>

<span data-ttu-id="7cc8e-298">以遞迴方式定義類似樹狀結構的結構。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-298">Tree-like structures are recursively defined.</span></span> <span data-ttu-id="7cc8e-299">這對繼承很麻煩，但是具有差異聯集的優雅。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-299">This is awkward with inheritance, but elegant with Discriminated Unions.</span></span>

```fsharp
type BST<'T> =
    | Empty
    | Node of 'T * BST<'T> * BST<'T>
```

<span data-ttu-id="7cc8e-300">以差異聯集表示類似樹狀結構的資料也可讓您在模式比對中受益于 exhaustiveness。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-300">Representing tree-like data with Discriminated Unions also allows you to benefit from exhaustiveness in pattern matching.</span></span>

#### <a name="use-requirequalifiedaccess-on-union-types-whose-case-names-are-not-sufficiently-unique"></a><span data-ttu-id="7cc8e-301">使用 `[<RequireQualifiedAccess>]` 案例名稱不是足夠唯一的等位類型</span><span class="sxs-lookup"><span data-stu-id="7cc8e-301">Use `[<RequireQualifiedAccess>]` on union types whose case names are not sufficiently unique</span></span>

<span data-ttu-id="7cc8e-302">您可能會發現某個網域中的相同名稱是不同專案的最佳名稱，例如差異聯集案例。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-302">You may find yourself in a domain where the same name is the best name for different things, such as Discriminated Union cases.</span></span> <span data-ttu-id="7cc8e-303">您可以使用 `[<RequireQualifiedAccess>]` 來區分大小寫名稱，以避免因為因遮蔽而相依于語句順序而觸發混淆錯誤 `open`</span><span class="sxs-lookup"><span data-stu-id="7cc8e-303">You can use `[<RequireQualifiedAccess>]` to disambiguate case names in order to avoid triggering confusing errors due to shadowing dependent on the ordering of `open` statements</span></span>

#### <a name="hide-the-representations-of-discriminated-unions-for-binary-compatible-apis-if-the-design-of-these-types-is-likely-to-evolve"></a><span data-ttu-id="7cc8e-304">如果這些類型的設計可能會進化，請隱藏二進位相容性聯集的區分等位表示</span><span class="sxs-lookup"><span data-stu-id="7cc8e-304">Hide the representations of discriminated unions for binary compatible APIs if the design of these types is likely to evolve</span></span>

<span data-ttu-id="7cc8e-305">等位型別依賴 F # 模式比對形式來提供簡潔的程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-305">Unions types rely on F# pattern-matching forms for a succinct programming model.</span></span> <span data-ttu-id="7cc8e-306">如先前所述，如果這些類型的設計可能會進化，您應該避免暴露具體的資料標記法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-306">As mentioned previously, you should avoid revealing concrete data representations if the design of these types is likely to evolve.</span></span>

<span data-ttu-id="7cc8e-307">例如，您可以使用私用或內部宣告或使用簽章檔案來隱藏差異聯集的標記法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-307">For example, the representation of a discriminated union can be hidden using a private or internal declaration, or by using a signature file.</span></span>

```fsharp
type Union =
    private
    | CaseA of int
    | CaseB of string
```

<span data-ttu-id="7cc8e-308">如果您不小心地顯示差異聯集，您可能會發現不需要中斷使用者程式碼就能為您的程式庫進行版本。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-308">If you reveal discriminated unions indiscriminately, you may find it hard to version your library without breaking user code.</span></span> <span data-ttu-id="7cc8e-309">相反地，請考慮公開一或多個使用中的模式，以允許您類型值的模式比對。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-309">Instead, consider revealing one or more active patterns to permit pattern matching over values of your type.</span></span>

<span data-ttu-id="7cc8e-310">現用模式提供了一種替代方式，可提供 F # 取用者與模式比對，同時避免直接公開 F # 等位類型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-310">Active patterns provide an alternate way to provide F# consumers with pattern matching while avoiding exposing F# Union Types directly.</span></span>

### <a name="inline-functions-and-member-constraints"></a><span data-ttu-id="7cc8e-311">內嵌函式和成員條件約束</span><span class="sxs-lookup"><span data-stu-id="7cc8e-311">Inline Functions and Member Constraints</span></span>

#### <a name="define-generic-numeric-algorithms-using-inline-functions-with-implied-member-constraints-and-statically-resolved-generic-types"></a><span data-ttu-id="7cc8e-312">使用具有隱含成員條件約束和靜態解析泛型型別的內嵌函式來定義泛型數值演算法</span><span class="sxs-lookup"><span data-stu-id="7cc8e-312">Define generic numeric algorithms using inline functions with implied member constraints and statically resolved generic types</span></span>

<span data-ttu-id="7cc8e-313">算術成員條件約束和 F # 比較準則約束是 F # 程式設計的標準。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-313">Arithmetic member constraints and F# comparison constraints are a standard for F# programming.</span></span> <span data-ttu-id="7cc8e-314">例如，請參考下列程式碼：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-314">For example, consider the following code:</span></span>

```fsharp
let inline highestCommonFactor a b =
    let rec loop a b =
        if a = LanguagePrimitives.GenericZero<_> then b
        elif a < b then loop a (b - a)
        else loop (a - b) b
    loop a b
```

<span data-ttu-id="7cc8e-315">此函式的類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-315">The type of this function is as follows:</span></span>

```fsharp
val inline highestCommonFactor : ^T -> ^T -> ^T
                when ^T : (static member Zero : ^T)
                and ^T : (static member ( - ) : ^T * ^T -> ^T)
                and ^T : equality
                and ^T : comparison
```

<span data-ttu-id="7cc8e-316">這是適用于數學程式庫中公用 API 的功能。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-316">This is a suitable function for a public API in a mathematical library.</span></span>

#### <a name="avoid-using-member-constraints-to-simulate-type-classes-and-duck-typing"></a><span data-ttu-id="7cc8e-317">避免使用成員條件約束來模擬型別類別和打字型別</span><span class="sxs-lookup"><span data-stu-id="7cc8e-317">Avoid using member constraints to simulate type classes and duck typing</span></span>

<span data-ttu-id="7cc8e-318">您可以使用 F # 成員條件約束來模擬「打字打字」。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-318">It is possible to simulate "duck typing" using F# member constraints.</span></span> <span data-ttu-id="7cc8e-319">不過，使用此功能的成員通常不應該用於 F # 對 F # 程式庫設計中。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-319">However, members that make use of this should not in general be used in F#-to-F# library designs.</span></span> <span data-ttu-id="7cc8e-320">這是因為根據不熟悉或非標準隱含條件約束的程式庫設計，通常會導致使用者的程式碼變差，並系結至一個特定的架構模式。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-320">This is because library designs based on unfamiliar or non-standard implicit constraints tend to cause user code to become inflexible and tied to one particular framework pattern.</span></span>

<span data-ttu-id="7cc8e-321">此外，在這種情況下大量使用成員條件約束很有可能會導致編譯時間很長。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-321">Additionally, there is a good chance that heavy use of member constraints in this manner can result in very long compile times.</span></span>

### <a name="operator-definitions"></a><span data-ttu-id="7cc8e-322">運算子定義</span><span class="sxs-lookup"><span data-stu-id="7cc8e-322">Operator Definitions</span></span>

#### <a name="avoid-defining-custom-symbolic-operators"></a><span data-ttu-id="7cc8e-323">避免定義自訂符號運算子</span><span class="sxs-lookup"><span data-stu-id="7cc8e-323">Avoid defining custom symbolic operators</span></span>

<span data-ttu-id="7cc8e-324">自訂運算子在某些情況下是不可或缺的，而且在大型的實作為程式碼主體內是非常有用的標記裝置。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-324">Custom operators are essential in some situations and are highly useful notational devices within a large body of implementation code.</span></span> <span data-ttu-id="7cc8e-325">針對程式庫的新使用者，命名函式通常更容易使用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-325">For new users of a library, named functions are often easier to use.</span></span> <span data-ttu-id="7cc8e-326">此外，自訂符號運算子可能很難記載，而且使用者發現因為 IDE 和搜尋引擎有現有的限制，所以更難以查閱運算子的說明。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-326">In addition, custom symbolic operators can be hard to document, and users find it more difficult to look up help on operators, due to existing limitations in IDE and search engines.</span></span>

<span data-ttu-id="7cc8e-327">因此，最好以命名函式和成員的形式發行您的功能，並在標記權益超過檔和擁有這些專案的認知成本時，另外公開此功能的運算子。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-327">As a result, it is best to publish your functionality as named functions and members, and additionally expose operators for this functionality only if the notational benefits outweigh the documentation and cognitive cost of having them.</span></span>

### <a name="units-of-measure"></a><span data-ttu-id="7cc8e-328">測量單位</span><span class="sxs-lookup"><span data-stu-id="7cc8e-328">Units of Measure</span></span>

#### <a name="carefully-use-units-of-measure-for-added-type-safety-in-f-code"></a><span data-ttu-id="7cc8e-329">針對 F # 程式碼中新增的型別安全，謹慎使用測量單位</span><span class="sxs-lookup"><span data-stu-id="7cc8e-329">Carefully use units of measure for added type safety in F# code</span></span>

<span data-ttu-id="7cc8e-330">其他 .NET 語言查看時，會清除度量單位的其他輸入資訊。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-330">Additional typing information for units of measure is erased when viewed by other .NET languages.</span></span> <span data-ttu-id="7cc8e-331">請注意，.NET 元件、工具和反映將會看到類型-san 單位。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-331">Be aware that .NET components, tools, and reflection will see types-sans-units.</span></span> <span data-ttu-id="7cc8e-332">例如，c # 取用者會看到 `float` 而不是 `float<kg>` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-332">For example, C# consumers will see `float` rather than `float<kg>`.</span></span>

### <a name="type-abbreviations"></a><span data-ttu-id="7cc8e-333">類型縮寫</span><span class="sxs-lookup"><span data-stu-id="7cc8e-333">Type Abbreviations</span></span>

#### <a name="carefully-use-type-abbreviations-to-simplify-f-code"></a><span data-ttu-id="7cc8e-334">謹慎使用類型縮寫以簡化 F # 程式碼</span><span class="sxs-lookup"><span data-stu-id="7cc8e-334">Carefully use type abbreviations to simplify F# code</span></span>

<span data-ttu-id="7cc8e-335">.NET 元件、工具和反映將不會看到類型的縮寫名稱。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-335">.NET components, tools, and reflection will not see abbreviated names for types.</span></span> <span data-ttu-id="7cc8e-336">類型縮寫的顯著用法也可能使定義域比實際的更複雜，這可能會讓取用者混淆。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-336">Significant usage of type abbreviations can also make a domain appear more complex than it actually is, which could confuse consumers.</span></span>

#### <a name="avoid-type-abbreviations-for-public-types-whose-members-and-properties-should-be-intrinsically-different-to-those-available-on-the-type-being-abbreviated"></a><span data-ttu-id="7cc8e-337">避免其成員和屬性本質上不同于要縮寫之類型上的公用類型的類型縮寫</span><span class="sxs-lookup"><span data-stu-id="7cc8e-337">Avoid type abbreviations for public types whose members and properties should be intrinsically different to those available on the type being abbreviated</span></span>

<span data-ttu-id="7cc8e-338">在此情況下，要縮寫的型別會顯示太多關於所定義之實際型別的標記法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-338">In this case, the type being abbreviated reveals too much about the representation of the actual type being defined.</span></span> <span data-ttu-id="7cc8e-339">相反地，請考慮將縮寫包裝在類別類型或單一案例的差異聯集 (或者，當效能為必要時，請考慮使用結構類型將縮寫) 包裝。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-339">Instead, consider wrapping the abbreviation in a class type or a single-case discriminated union (or, when performance is essential, consider using a struct type to wrap the abbreviation).</span></span>

<span data-ttu-id="7cc8e-340">例如，將多個地圖定義為 F # 地圖的特殊案例很吸引人，例如：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-340">For example, it is tempting to define a multi-map as a special case of an F# map, for example:</span></span>

```fsharp
type MultiMap<'Key,'Value> = Map<'Key,'Value list>
```

<span data-ttu-id="7cc8e-341">不過，這種類型上的邏輯點標記運算與地圖上的作業不同，例如，lookup 運算子對應是合理的。[key] 如果索引鍵不在字典中，則傳回空的清單，而不是引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-341">However, the logical dot-notation operations on this type are not the same as the operations on a Map – for example, it is reasonable that the lookup operator map.[key] return the empty list if the key is not in the dictionary, rather than raising an exception.</span></span>

## <a name="guidelines-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="7cc8e-342">從其他 .NET 語言使用的程式庫指導方針</span><span class="sxs-lookup"><span data-stu-id="7cc8e-342">Guidelines for libraries for Use from other .NET Languages</span></span>

<span data-ttu-id="7cc8e-343">設計用來從其他 .NET 語言使用的程式庫時，請務必遵守 [.net 程式庫設計指導方針](../../standard/design-guidelines/index.md)。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-343">When designing libraries for use from other .NET languages, it is important to adhere to the [.NET Library Design Guidelines](../../standard/design-guidelines/index.md).</span></span> <span data-ttu-id="7cc8e-344">在本檔中，這些程式庫會標示為香草 .NET 程式庫，而非使用 F # 結構的 F # 對應程式庫，而不受限制。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-344">In this document, these libraries are labeled as vanilla .NET libraries, as opposed to F#-facing libraries that use F# constructs without restriction.</span></span> <span data-ttu-id="7cc8e-345">設計香草 .NET 程式庫表示讓熟悉且慣用的 Api 與其余 .NET Framework 保持一致，方法是將在公用 API 中使用 F # 特定的結構降至最低。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-345">Designing vanilla .NET libraries means providing familiar and idiomatic APIs consistent with the rest of the .NET Framework by minimizing the use of F#-specific constructs in the public API.</span></span> <span data-ttu-id="7cc8e-346">下列各節將說明這些規則。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-346">The rules are explained in the following sections.</span></span>

### <a name="namespace-and-type-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="7cc8e-347">適用于程式庫的命名空間和型別設計 (可用於其他 .NET 語言) </span><span class="sxs-lookup"><span data-stu-id="7cc8e-347">Namespace and Type design (for libraries for use from other .NET Languages)</span></span>

#### <a name="apply-the-net-naming-conventions-to-the-public-api-of-your-components"></a><span data-ttu-id="7cc8e-348">將 .NET 命名慣例套用至元件的公用 API</span><span class="sxs-lookup"><span data-stu-id="7cc8e-348">Apply the .NET naming conventions to the public API of your components</span></span>

<span data-ttu-id="7cc8e-349">請特別注意縮寫名稱和 .NET 大寫準則的使用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-349">Pay special attention to the use of abbreviated names and the .NET capitalization guidelines.</span></span>

```fsharp
type pCoord = ...
    member this.theta = ...

type PolarCoordinate = ...
    member this.Theta = ...
```

#### <a name="use-namespaces-types-and-members-as-the-primary-organizational-structure-for-your-components"></a><span data-ttu-id="7cc8e-350">使用命名空間、類型和成員作為元件的主要組織結構</span><span class="sxs-lookup"><span data-stu-id="7cc8e-350">Use namespaces, types, and members as the primary organizational structure for your components</span></span>

<span data-ttu-id="7cc8e-351">所有包含公用功能的檔案都應該以宣告開頭 `namespace` ，且命名空間中的唯一公開實體應該是類型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-351">All files containing public functionality should begin with a `namespace` declaration, and the only public-facing entities in namespaces should be types.</span></span> <span data-ttu-id="7cc8e-352">請勿使用 F # 模組。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-352">Do not use F# modules.</span></span>

<span data-ttu-id="7cc8e-353">使用非公用模組來保存實作為程式碼、公用程式類型和公用程式函式。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-353">Use non-public modules to hold implementation code, utility types, and utility functions.</span></span>

<span data-ttu-id="7cc8e-354">靜態類型應優先于模組，因為它們可讓 API 的未來演進使用多載和其他可能不會在 F # 模組中使用的 .NET API 設計概念。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-354">Static types should be preferred over modules, as they allow for future evolution of the API to use overloading and other .NET API design concepts that may not be used within F# modules.</span></span>

<span data-ttu-id="7cc8e-355">例如，取代下列公用 API：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-355">For example, in place of the following public API:</span></span>

```fsharp
module Fabrikam

module Utilities =
    let Name = "Bob"
    let Add2 x y = x + y
    let Add3 x y z = x + y + z
```

<span data-ttu-id="7cc8e-356">請改為考慮：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-356">Consider instead:</span></span>

```fsharp
namespace Fabrikam

[<AbstractClass; Sealed>]
type Utilities =
    static member Name = "Bob"
    static member Add(x,y) = x + y
    static member Add(x,y,z) = x + y + z
```

#### <a name="use-f-record-types-in-vanilla-net-apis-if-the-design-of-the-types-wont-evolve"></a><span data-ttu-id="7cc8e-357">如果類型的設計不會進化，請在香草 .NET Api 中使用 F # 記錄類型</span><span class="sxs-lookup"><span data-stu-id="7cc8e-357">Use F# record types in vanilla .NET APIs if the design of the types won't evolve</span></span>

<span data-ttu-id="7cc8e-358">F # 記錄類型會編譯成簡單的 .NET 類別。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-358">F# record types compile to a simple .NET class.</span></span> <span data-ttu-id="7cc8e-359">這些適用于 Api 中一些簡單、穩定的類型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-359">These are suitable for some simple, stable types in APIs.</span></span> <span data-ttu-id="7cc8e-360">請考慮使用 `[<NoEquality>]` 和 `[<NoComparison>]` 屬性來抑制自動產生介面。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-360">Consider using the `[<NoEquality>]` and `[<NoComparison>]` attributes to suppress the automatic generation of interfaces.</span></span> <span data-ttu-id="7cc8e-361">也請避免在香草 .NET Api 中使用可變動的記錄欄位，因為這些欄位會公開公用欄位。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-361">Also avoid using mutable record fields in vanilla .NET APIs as these expose a public field.</span></span> <span data-ttu-id="7cc8e-362">請一律考慮類別是否會為未來的 API 演進提供更有彈性的選項。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-362">Always consider whether a class would provide a more flexible option for future evolution of the API.</span></span>

<span data-ttu-id="7cc8e-363">例如，下列 F # 程式碼會向 c # 取用者公開公用 API：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-363">For example, the following F# code exposes the public API to a C# consumer:</span></span>

<span data-ttu-id="7cc8e-364">F#：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-364">F#:</span></span>

```fsharp
[<NoEquality; NoComparison>]
type MyRecord =
    { FirstThing: int
        SecondThing: string }
```

<span data-ttu-id="7cc8e-365">C#：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-365">C#:</span></span>

```csharp
public sealed class MyRecord
{
    public MyRecord(int firstThing, string secondThing);
    public int FirstThing { get; }
    public string SecondThing { get; }
}
```

#### <a name="hide-the-representation-of-f-union-types-in-vanilla-net-apis"></a><span data-ttu-id="7cc8e-366">在香草 .NET Api 中隱藏 F # 聯集類型的標記法</span><span class="sxs-lookup"><span data-stu-id="7cc8e-366">Hide the representation of F# union types in vanilla .NET APIs</span></span>

<span data-ttu-id="7cc8e-367">F # 等位類型通常不會跨元件界限使用，即使是 F # 對 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-367">F# union types are not commonly used across component boundaries, even for F#-to-F# coding.</span></span> <span data-ttu-id="7cc8e-368">它們是在元件和程式庫內部使用的絕佳實作為裝置。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-368">They are an excellent implementation device when used internally within components and libraries.</span></span>

<span data-ttu-id="7cc8e-369">設計香草 .NET API 時，請考慮使用私用宣告或簽章檔案來隱藏聯集類型的表示。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-369">When designing a vanilla .NET API, consider hiding the representation of a union type by using either a private declaration or a signature file.</span></span>

```fsharp
type PropLogic =
    private
    | And of PropLogic * PropLogic
    | Not of PropLogic
    | True
```

<span data-ttu-id="7cc8e-370">您也可以增強在內部使用聯集表示的類型，以提供所需的成員。.NET 面向的 API。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-370">You may also augment types that use a union representation internally with members to provide a desired .NET-facing API.</span></span>

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

#### <a name="design-gui-and-other-components-using-the-design-patterns-of-the-framework"></a><span data-ttu-id="7cc8e-371">使用架構的設計模式來設計 GUI 和其他元件</span><span class="sxs-lookup"><span data-stu-id="7cc8e-371">Design GUI and other components using the design patterns of the framework</span></span>

<span data-ttu-id="7cc8e-372">.NET 中提供許多不同的架構，例如 WinForms、WPF 和 ASP.NET。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-372">There are many different frameworks available within .NET, such as WinForms, WPF, and ASP.NET.</span></span> <span data-ttu-id="7cc8e-373">如果您要設計要在這些架構中使用的元件，則應該使用每個的命名和設計慣例。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-373">Naming and design conventions for each should be used if you are designing components for use in these frameworks.</span></span> <span data-ttu-id="7cc8e-374">例如，針對 WPF 程式設計，採用 WPF 設計模式來設計您所設計的類別。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-374">For example, for WPF programming, adopt WPF design patterns for the classes you are designing.</span></span> <span data-ttu-id="7cc8e-375">針對使用者介面程式設計中的模型，請使用如中所找到的設計模式，例如事件和以通知為基礎的集合 <xref:System.Collections.ObjectModel> 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-375">For models in user interface programming, use design patterns such as events and notification-based collections such as those found in <xref:System.Collections.ObjectModel>.</span></span>

### <a name="object-and-member-design-for-libraries-for-use-from-other-net-languages"></a><span data-ttu-id="7cc8e-376">程式庫的物件和成員設計 (，以供其他 .NET 語言使用) </span><span class="sxs-lookup"><span data-stu-id="7cc8e-376">Object and Member design (for libraries for use from other .NET Languages)</span></span>

#### <a name="use-the-clievent-attribute-to-expose-net-events"></a><span data-ttu-id="7cc8e-377">使用 CLIEvent 屬性來公開 .NET 事件</span><span class="sxs-lookup"><span data-stu-id="7cc8e-377">Use the CLIEvent attribute to expose .NET events</span></span>

<span data-ttu-id="7cc8e-378">`DelegateEvent`使用特定的 .net 委派型別來建立，此型別會採用物件並 `EventArgs` (，而不是 `Event` 使用預設的型別，而是使用 `FSharpHandler` 預設的型別) 讓事件以熟悉的方式發佈到其他 .net 語言。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-378">Construct a `DelegateEvent` with a specific .NET delegate type that takes an object and `EventArgs` (rather than an `Event`, which just uses the `FSharpHandler` type by default) so that the events are published in the familiar way to other .NET languages.</span></span>

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

#### <a name="expose-asynchronous-operations-as-methods-that-return-net-tasks"></a><span data-ttu-id="7cc8e-379">將非同步作業公開為傳回 .NET 工作的方法</span><span class="sxs-lookup"><span data-stu-id="7cc8e-379">Expose asynchronous operations as methods that return .NET tasks</span></span>

<span data-ttu-id="7cc8e-380">工作會在 .NET 中用來代表使用中的非同步計算。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-380">Tasks are used in .NET to represent active asynchronous computations.</span></span> <span data-ttu-id="7cc8e-381">工作通常比 F # 物件的複合少 `Async<T>` ，因為它們代表「已在執行」的工作，而且無法以執行平行組合的方式組合在一起，或隱藏取消信號和其他內容參數的傳播。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-381">Tasks are in general less compositional than F# `Async<T>` objects, since they represent "already executing" tasks and can't be composed together in ways that perform parallel composition, or which hide the propagation of cancellation signals and other contextual parameters.</span></span>

<span data-ttu-id="7cc8e-382">不過，無論如何，傳回工作的方法都是 .NET 上非同步程式設計的標準標記法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-382">However, despite this, methods that return Tasks are the standard representation of asynchronous programming on .NET.</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =

    let compute (x: int): Async<int> = async { ... }

    member this.ComputeAsync(x) = compute x |> Async.StartAsTask
```

<span data-ttu-id="7cc8e-383">您通常也會想要接受明確的解除標記：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-383">You will frequently also want to accept an explicit cancellation token:</span></span>

```fsharp
/// A type in a component designed for use from other .NET languages
type MyType() =
    let compute(x: int): Async<int> = async { ... }
    member this.ComputeAsTask(x, cancellationToken) = Async.StartAsTask(compute x, cancellationToken)
```

#### <a name="use-net-delegate-types-instead-of-f-function-types"></a><span data-ttu-id="7cc8e-384">使用 .NET 委派型別，而非 F # 函式類型</span><span class="sxs-lookup"><span data-stu-id="7cc8e-384">Use .NET delegate types instead of F# function types</span></span>

<span data-ttu-id="7cc8e-385">這裡的「F # 函式類型」表示「箭號」類型 `int -> int` ，例如。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-385">Here "F# function types" mean "arrow" types like `int -> int`.</span></span>

<span data-ttu-id="7cc8e-386">而不是：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-386">Instead of this:</span></span>

```fsharp
member this.Transform(f: int->int) =
    ...
```

<span data-ttu-id="7cc8e-387">執行此動作：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-387">Do this:</span></span>

```fsharp
member this.Transform(f: Func<int,int>) =
    ...
```

<span data-ttu-id="7cc8e-388">F # 函式類型會顯示為 `class FSharpFunc<T,U>` 其他 .net 語言，而且較不適合瞭解委派類型的語言功能和工具。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-388">The F# function type appears as `class FSharpFunc<T,U>` to other .NET languages, and is less suitable for language features and tooling that understands delegate types.</span></span> <span data-ttu-id="7cc8e-389">撰寫以 .NET Framework 3.5 或更高版本為目標的較高順序方法時， `System.Func` 和 `System.Action` 委派是正確發佈的 api，可讓 .net 開發人員以低摩擦的方式取用這些 api。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-389">When authoring a higher-order method targeting .NET Framework 3.5 or higher, the `System.Func` and `System.Action` delegates are the right APIs to publish to enable .NET developers to consume these APIs in a low-friction manner.</span></span> <span data-ttu-id="7cc8e-390"> (以 .NET Framework 2.0 為目標時，系統定義的委派類型會受到更多限制;請考慮使用預先定義的委派類型，例如 `System.Converter<T,U>` 或定義特定的委派類型。 ) </span><span class="sxs-lookup"><span data-stu-id="7cc8e-390">(When targeting .NET Framework 2.0, the system-defined delegate types are more limited; consider using predefined delegate types such as `System.Converter<T,U>` or defining a specific delegate type.)</span></span>

<span data-ttu-id="7cc8e-391">另一方面，.NET 委派不是 F # 面向程式庫的自然 (請參閱下一節的 F # 面向程式庫) 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-391">On the flip side, .NET delegates are not natural for F#-facing libraries (see the next Section on F#-facing libraries).</span></span> <span data-ttu-id="7cc8e-392">因此，開發香草 .NET 程式庫的高階方法時，常見的採用策略是使用 F # 函式類型來撰寫所有的實作者，然後使用委派作為實際 F # 實作為之上的精簡外觀來建立公用 API。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-392">As a result, a common implementation strategy when developing higher-order methods for vanilla .NET libraries is to author all the implementation using F# function types, and then create the public API using delegates as a thin façade atop the actual F# implementation.</span></span>

#### <a name="use-the-trygetvalue-pattern-instead-of-returning-f-option-values-and-prefer-method-overloading-to-taking-f-option-values-as-arguments"></a><span data-ttu-id="7cc8e-393">使用 TryGetValue 模式，而不是傳回 F # 選項值，而且偏好使用方法多載，以 F # 選項值做為引數</span><span class="sxs-lookup"><span data-stu-id="7cc8e-393">Use the TryGetValue pattern instead of returning F# option values, and prefer method overloading to taking F# option values as arguments</span></span>

<span data-ttu-id="7cc8e-394">Api 中 F # 選項類型的常見使用模式，是使用標準 .NET 設計技術，在香草 .NET Api 中進行更好的運用。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-394">Common patterns of use for the F# option type in APIs are better implemented in vanilla .NET APIs using standard .NET design techniques.</span></span> <span data-ttu-id="7cc8e-395">請考慮使用 bool 傳回型別加上 out 參數，如同 "TryGetValue" 模式，而不是傳回 F # 選項值。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-395">Instead of returning an F# option value, consider using the bool return type plus an out parameter as in the "TryGetValue" pattern.</span></span> <span data-ttu-id="7cc8e-396">而不是將 F # 選項值作為參數，而是考慮使用方法多載或選擇性引數。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-396">And instead of taking F# option values as parameters, consider using method overloading or optional arguments.</span></span>

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

#### <a name="use-the-net-collection-interface-types-ienumerablet-and-idictionarykeyvalue-for-parameters-and-return-values"></a><span data-ttu-id="7cc8e-397">使用 .NET 集合介面類別型 IEnumerable \<T\> 和 IDictionary \<Key,Value\> 作為參數和傳回值</span><span class="sxs-lookup"><span data-stu-id="7cc8e-397">Use the .NET collection interface types IEnumerable\<T\> and IDictionary\<Key,Value\> for parameters and return values</span></span>

<span data-ttu-id="7cc8e-398">避免使用具象的集合類型，例如 .NET 陣列、F # 型別和 .NET 具象的 `T[]` `list<T>` `Map<Key,Value>` `Set<T>` 集合類型（例如） `Dictionary<Key,Value>` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-398">Avoid the use of concrete collection types such as .NET arrays `T[]`, F# types `list<T>`, `Map<Key,Value>` and `Set<T>`, and .NET concrete collection types such as `Dictionary<Key,Value>`.</span></span> <span data-ttu-id="7cc8e-399">.NET 程式庫設計指導方針對於使用各種集合類型（例如）有很大的建議 `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-399">The .NET Library Design Guidelines have good advice regarding when to use various collection types like `IEnumerable<T>`.</span></span> <span data-ttu-id="7cc8e-400">在某些情況下，您可以在效能的情況下，使用陣列 () 的某些用途 `T[]` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-400">Some use of arrays (`T[]`) is acceptable in some circumstances, on performance grounds.</span></span> <span data-ttu-id="7cc8e-401">請注意 `seq<T>` ，特別是的 F # 別名 `IEnumerable<T>` ，因此 seq 通常是香草 .net API 的適當類型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-401">Note especially that `seq<T>` is just the F# alias for `IEnumerable<T>`, and thus seq is often an appropriate type for a vanilla .NET API.</span></span>

<span data-ttu-id="7cc8e-402">而非 F # 清單：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-402">Instead of F# lists:</span></span>

```fsharp
member this.PrintNames(names: string list) =
    ...
```

<span data-ttu-id="7cc8e-403">使用 F # 序列：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-403">Use F# sequences:</span></span>

```fsharp
member this.PrintNames(names: seq<string>) =
    ...
```

#### <a name="use-the-unit-type-as-the-only-input-type-of-a-method-to-define-a-zero-argument-method-or-as-the-only-return-type-to-define-a-void-returning-method"></a><span data-ttu-id="7cc8e-404">您可以使用單位類型作為方法的唯一輸入類型來定義零引數方法，或使用唯一的傳回型別來定義 void 傳回方法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-404">Use the unit type as the only input type of a method to define a zero-argument method, or as the only return type to define a void-returning method</span></span>

<span data-ttu-id="7cc8e-405">避免使用單位類型的其他用途。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-405">Avoid other uses of the unit type.</span></span> <span data-ttu-id="7cc8e-406">這些都很好：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-406">These are good:</span></span>

```fsharp
✔ member this.NoArguments() = 3

✔ member this.ReturnVoid(x: int) = ()
```

<span data-ttu-id="7cc8e-407">這是不好的：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-407">This is bad:</span></span>

```fsharp
member this.WrongUnit( x: unit, z: int) = ((), ())
```

#### <a name="check-for-null-values-on-vanilla-net-api-boundaries"></a><span data-ttu-id="7cc8e-408">在香草 .NET API 界限上檢查是否有 null 值</span><span class="sxs-lookup"><span data-stu-id="7cc8e-408">Check for null values on vanilla .NET API boundaries</span></span>

<span data-ttu-id="7cc8e-409">F # 的程式碼通常會有較少的 null 值，因為不可變的設計模式，以及對 F # 類型使用 null 常值的限制。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-409">F# implementation code tends to have fewer null values, due to immutable design patterns and restrictions on use of null literals for F# types.</span></span> <span data-ttu-id="7cc8e-410">其他 .NET 語言通常會使用 null 做為值更頻繁。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-410">Other .NET languages often use null as a value much more frequently.</span></span> <span data-ttu-id="7cc8e-411">因此，公開香草 .NET API 的 F # 程式碼應該在 API 界限上檢查 null 的參數，並防止這些值更深入地流向 F # 程式碼。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-411">Because of this, F# code that is exposing a vanilla .NET API should check parameters for null at the API boundary, and prevent these values from flowing deeper into the F# implementation code.</span></span> <span data-ttu-id="7cc8e-412">您 `isNull` 可以使用模式上的函數或模式比對 `null` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-412">The `isNull` function or pattern matching on the `null` pattern can be used.</span></span>

```fsharp
let checkNonNull argName (arg: obj) =
    match arg with
    | null -> nullArg argName
    | _ -> ()

let checkNonNull` argName (arg: obj) =
    if isNull arg then nullArg argName
    else ()
```

#### <a name="avoid-using-tuples-as-return-values"></a><span data-ttu-id="7cc8e-413">避免使用元組作為傳回值</span><span class="sxs-lookup"><span data-stu-id="7cc8e-413">Avoid using tuples as return values</span></span>

<span data-ttu-id="7cc8e-414">相反地，最好是傳回持有匯總資料的命名型別，或使用 out 參數傳回多個值。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-414">Instead, prefer returning a named type holding the aggregate data, or using out parameters to return multiple values.</span></span> <span data-ttu-id="7cc8e-415">雖然元組和結構元組存在於 .NET (包括結構元組) 的 c # 語言支援，但它們最常不提供適用于 .NET 開發人員的理想和預期 API。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-415">Although tuples and struct tuples exist in .NET (including C# language support for struct tuples), they will most often not provide the ideal and expected API for .NET developers.</span></span>

#### <a name="avoid-the-use-of-currying-of-parameters"></a><span data-ttu-id="7cc8e-416">避免使用參數的 currying</span><span class="sxs-lookup"><span data-stu-id="7cc8e-416">Avoid the use of currying of parameters</span></span>

<span data-ttu-id="7cc8e-417">相反地，請使用 .NET 呼叫慣例 `Method(arg1,arg2,…,argN)` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-417">Instead, use .NET calling conventions `Method(arg1,arg2,…,argN)`.</span></span>

```fsharp
member this.TupledArguments(str, num) = String.replicate num str
```

<span data-ttu-id="7cc8e-418">秘訣：如果您要設計可從任何 .NET 語言使用的程式庫，則不會實際執行一些實驗性 c # 和 Visual Basic 程式設計，以確保您的程式庫能夠從這些語言中「感覺正確」。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-418">Tip: If you're designing libraries for use from any .NET language, then there's no substitute for actually doing some experimental C# and Visual Basic programming to ensure that your libraries "feel right" from these languages.</span></span> <span data-ttu-id="7cc8e-419">您也可以使用 .NET 反映程式和 Visual Studio 物件瀏覽器之類的工具，以確保程式庫及其檔會如預期般出現給開發人員。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-419">You can also use tools such as .NET Reflector and the Visual Studio Object Browser to ensure that libraries and their documentation appear as expected to developers.</span></span>

## <a name="appendix"></a><span data-ttu-id="7cc8e-420">附錄</span><span class="sxs-lookup"><span data-stu-id="7cc8e-420">Appendix</span></span>

### <a name="end-to-end-example-of-designing-f-code-for-use-by-other-net-languages"></a><span data-ttu-id="7cc8e-421">設計其他 .NET 語言使用之 F # 程式碼的端對端範例</span><span class="sxs-lookup"><span data-stu-id="7cc8e-421">End-to-end example of designing F# code for use by other .NET languages</span></span>

<span data-ttu-id="7cc8e-422">請考慮下列類別：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-422">Consider the following class:</span></span>

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

<span data-ttu-id="7cc8e-423">此類別的推斷 F # 類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-423">The inferred F# type of this class is as follows:</span></span>

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

<span data-ttu-id="7cc8e-424">讓我們來看看如何使用另一個 .NET 語言，讓程式設計人員看到 F # 型別。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-424">Let's take a look at how this F# type appears to a programmer using another .NET language.</span></span> <span data-ttu-id="7cc8e-425">例如，大約的 c # "signature" 如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-425">For example, the approximate C# "signature" is as follows:</span></span>

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

<span data-ttu-id="7cc8e-426">關於 F # 如何在這裡表示結構，有一些重要的重點需要注意。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-426">There are some important points to notice about how F# represents constructs here.</span></span> <span data-ttu-id="7cc8e-427">例如：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-427">For example:</span></span>

* <span data-ttu-id="7cc8e-428">中繼資料（例如引數名稱）已保留。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-428">Metadata such as argument names has been preserved.</span></span>

* <span data-ttu-id="7cc8e-429">採用兩個引數的 F # 方法會變成採用兩個引數的 c # 方法。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-429">F# methods that take two arguments become C# methods that take two arguments.</span></span>

* <span data-ttu-id="7cc8e-430">函數和清單會成為 F # 程式庫中對應類型的參考。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-430">Functions and lists become references to corresponding types in the F# library.</span></span>

<span data-ttu-id="7cc8e-431">下列程式碼示範如何調整此程式碼，以將這些專案納入考慮。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-431">The following code shows how to adjust this code to take these things into account.</span></span>

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

<span data-ttu-id="7cc8e-432">程式碼的推斷 F # 類型如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-432">The inferred F# type of the code is as follows:</span></span>

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

<span data-ttu-id="7cc8e-433">C # 簽章現在如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-433">The C# signature is now as follows:</span></span>

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

<span data-ttu-id="7cc8e-434">準備此類型以做為香草 .NET 程式庫一部分的修正，如下所示：</span><span class="sxs-lookup"><span data-stu-id="7cc8e-434">The fixes made to prepare this type for use as part of a vanilla .NET library are as follows:</span></span>

* <span data-ttu-id="7cc8e-435">已調整數個名稱： `Point1` 、 `n` 、 `l` 和會 `f` `RadialPoint` 分別成為、、 `count` `factor` 和 `transform` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-435">Adjusted several names: `Point1`, `n`, `l`, and `f` became `RadialPoint`, `count`, `factor`, and `transform`, respectively.</span></span>

* <span data-ttu-id="7cc8e-436">使用的傳回型別， `seq<RadialPoint>` 而不是藉 `RadialPoint list` 由將使用的清單結構變更 `[ ... ]` 為的順序結構 `IEnumerable<RadialPoint>` 。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-436">Used a return type of `seq<RadialPoint>` instead of `RadialPoint list` by changing a list construction using `[ ... ]` to a sequence construction using `IEnumerable<RadialPoint>`.</span></span>

* <span data-ttu-id="7cc8e-437">使用 .NET 委派型別， `System.Func` 而非 F # 函數類型。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-437">Used the .NET delegate type `System.Func` instead of an F# function type.</span></span>

<span data-ttu-id="7cc8e-438">這使得在 c # 程式碼中使用的更好變得更容易。</span><span class="sxs-lookup"><span data-stu-id="7cc8e-438">This makes it far nicer to consume in C# code.</span></span>
