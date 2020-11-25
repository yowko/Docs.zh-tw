---
title: 重大變更： LINQ OrderBy 的複雜度。第一個 {OrDefault} 增加了
description: 瞭解核心 .NET 程式庫中的 .NET 5.0 重大變更，其中的 OrderBy 的執行方式是先變更。
ms.date: 11/01/2020
ms.openlocfilehash: 3c4f8fd0bb2051c3e1ac14eab091be11f10f88b4
ms.sourcegitcommit: d8020797a6657d0fbbdff362b80300815f682f94
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/24/2020
ms.locfileid: "95760714"
---
# <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="26a52-103">LINQ OrderBy 的複雜度。前 {OrDefault} 增加了</span><span class="sxs-lookup"><span data-stu-id="26a52-103">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="26a52-104">的執行 <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 已經變更，因此會增加作業的複雜度。</span><span class="sxs-lookup"><span data-stu-id="26a52-104">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

## <a name="change-description"></a><span data-ttu-id="26a52-105">變更描述</span><span class="sxs-lookup"><span data-stu-id="26a52-105">Change description</span></span>

<span data-ttu-id="26a52-106">在 .NET Core 1.x-3.x 中，呼叫 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A> 接著，或在複雜度的情況下 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 運作 `O(N)` 。</span><span class="sxs-lookup"><span data-stu-id="26a52-106">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="26a52-107">由於只需要第一個 (或預設) 元素，因此只需要一個列舉來尋找它。</span><span class="sxs-lookup"><span data-stu-id="26a52-107">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="26a52-108">不過，提供給或的述詞 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 會精確地叫用 `N` ，其中 `N` 是序列的長度。</span><span class="sxs-lookup"><span data-stu-id="26a52-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="26a52-109">在 .NET 5.0 和更新版本中， [已進行](https://github.com/dotnet/runtime/pull/36643) 一項變更，因此呼叫 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A> 接著會 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 使用 `O(N log N)` 複雜性而不是複雜度來操作 `O(N)` 。</span><span class="sxs-lookup"><span data-stu-id="26a52-109">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="26a52-110">不過，提供給或的述詞 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 可能會叫用 *不* 到的 `N` 時間，這對整體效能較重要。</span><span class="sxs-lookup"><span data-stu-id="26a52-110">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="26a52-111">這項變更符合 .NET Framework 中作業的執行和複雜度。</span><span class="sxs-lookup"><span data-stu-id="26a52-111">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

## <a name="reason-for-change"></a><span data-ttu-id="26a52-112">變更的原因</span><span class="sxs-lookup"><span data-stu-id="26a52-112">Reason for change</span></span>

<span data-ttu-id="26a52-113">叫用述詞的優點較少，因為整體複雜性較低，所以已還原 .NET Core 1.0 中引進的實作為。</span><span class="sxs-lookup"><span data-stu-id="26a52-113">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="26a52-114">如需詳細資訊，請參閱 [此 dotnet/執行時間問題](https://github.com/dotnet/runtime/issues/31554)。</span><span class="sxs-lookup"><span data-stu-id="26a52-114">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

## <a name="version-introduced"></a><span data-ttu-id="26a52-115">引進的版本</span><span class="sxs-lookup"><span data-stu-id="26a52-115">Version introduced</span></span>

<span data-ttu-id="26a52-116">5.0</span><span class="sxs-lookup"><span data-stu-id="26a52-116">5.0</span></span>

## <a name="recommended-action"></a><span data-ttu-id="26a52-117">建議的動作</span><span class="sxs-lookup"><span data-stu-id="26a52-117">Recommended action</span></span>

<span data-ttu-id="26a52-118">開發人員的部分不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="26a52-118">No action is required on the developer's part.</span></span>

## <a name="affected-apis"></a><span data-ttu-id="26a52-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="26a52-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

### Category

Core .NET libraries

### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
