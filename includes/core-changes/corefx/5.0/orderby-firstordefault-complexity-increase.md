---
ms.openlocfilehash: 950c69199219cca615e403c6515239de8864d35d
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137496"
---
### <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="7196c-101">LINQ OrderBy 的複雜性。第一個 {OrDefault} 已增加</span><span class="sxs-lookup"><span data-stu-id="7196c-101">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="7196c-102">和的執行 <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 已變更，因而增加了作業的複雜度。</span><span class="sxs-lookup"><span data-stu-id="7196c-102">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

#### <a name="change-description"></a><span data-ttu-id="7196c-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="7196c-103">Change description</span></span>

<span data-ttu-id="7196c-104">在 .NET Core 1.x-3.x 中，呼叫 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A> 後面接著， <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 或 <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 操作 `O(N)` 複雜度。</span><span class="sxs-lookup"><span data-stu-id="7196c-104">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="7196c-105">因為只需要第一個 (或預設) 元素，所以只需要一個列舉就可以找到它。</span><span class="sxs-lookup"><span data-stu-id="7196c-105">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="7196c-106">不過，提供給或的述詞 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 剛好會叫用 `N` 次，其中 `N` 是序列的長度。</span><span class="sxs-lookup"><span data-stu-id="7196c-106">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="7196c-107">在 .NET 5.0 和更新版本中，[進行](https://github.com/dotnet/runtime/pull/36643)了一項變更，讓呼叫 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A> 後面接著 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 或 <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 操作 `O(N log N)` 複雜度，而不是 `O(N)` 複雜度。</span><span class="sxs-lookup"><span data-stu-id="7196c-107">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="7196c-108">不過，提供給或的述詞 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 可能會被叫用次數*少於* `N` 次，這對整體效能更重要。</span><span class="sxs-lookup"><span data-stu-id="7196c-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="7196c-109">這項變更符合作業在 .NET Framework 中的執行和複雜度。</span><span class="sxs-lookup"><span data-stu-id="7196c-109">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="7196c-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="7196c-110">Reason for change</span></span>

<span data-ttu-id="7196c-111">叫用述詞的好處較少，但整體複雜度較低，因此在 .NET Core 1.0 中引進的實作為還原。</span><span class="sxs-lookup"><span data-stu-id="7196c-111">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="7196c-112">如需詳細資訊，請參閱[此 dotnet/執行時間問題](https://github.com/dotnet/runtime/issues/31554)。</span><span class="sxs-lookup"><span data-stu-id="7196c-112">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="7196c-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="7196c-113">Version introduced</span></span>

<span data-ttu-id="7196c-114">5.0</span><span class="sxs-lookup"><span data-stu-id="7196c-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="7196c-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="7196c-115">Recommended action</span></span>

<span data-ttu-id="7196c-116">開發人員的部分不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="7196c-116">No action is required on the developer's part.</span></span>

#### <a name="category"></a><span data-ttu-id="7196c-117">類別</span><span class="sxs-lookup"><span data-stu-id="7196c-117">Category</span></span>

<span data-ttu-id="7196c-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="7196c-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="7196c-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="7196c-119">Affected APIs</span></span>

- <xref:System.Linq.Enumerable.OrderBy%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.OrderByDescending%2A?displayProperty=fullName>
- <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>
- <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})?displayProperty=fullName>

<!--

#### Affected APIs

- `Overload:System.Linq.Enumerable.OrderBy`
- `Overload:System.Linq.Enumerable.OrderByDescending`
- `M:System.Linq.Enumerable.First``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`
- `M:System.Linq.Enumerable.FirstOrDefault``1(System.Collections.Generic.IEnumerable{``0},System.Func{``0,System.Boolean})`

-->
