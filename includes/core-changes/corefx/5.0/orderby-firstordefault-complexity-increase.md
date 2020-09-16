---
ms.openlocfilehash: 950c69199219cca615e403c6515239de8864d35d
ms.sourcegitcommit: d3c09791297f0edc468a4849a5f11ef62e0e90fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/12/2020
ms.locfileid: "88137496"
---
### <a name="complexity-of-linq-orderbyfirstordefault-increased"></a><span data-ttu-id="6b484-101">LINQ OrderBy 的複雜度。前 {OrDefault} 增加了</span><span class="sxs-lookup"><span data-stu-id="6b484-101">Complexity of LINQ OrderBy.First{OrDefault} increased</span></span>

<span data-ttu-id="6b484-102">的執行 <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.OrderBy%2A> `.` <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 已經變更，因此會增加作業的複雜度。</span><span class="sxs-lookup"><span data-stu-id="6b484-102">The implementation of <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> and <xref:System.Linq.Enumerable.OrderBy%2A>`.`<xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> has changed, resulting in increased complexity for the operation.</span></span>

#### <a name="change-description"></a><span data-ttu-id="6b484-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="6b484-103">Change description</span></span>

<span data-ttu-id="6b484-104">在 .NET Core 1.x-3.x 中，呼叫 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A> 接著，或在複雜度的情況下 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 運作 `O(N)` 。</span><span class="sxs-lookup"><span data-stu-id="6b484-104">In .NET Core 1.x - 3.x, calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N)` complexity.</span></span> <span data-ttu-id="6b484-105">由於只需要第一個 (或預設) 元素，因此只需要一個列舉來尋找它。</span><span class="sxs-lookup"><span data-stu-id="6b484-105">Since only the first (or default) element is required, only one enumeration is required to find it.</span></span> <span data-ttu-id="6b484-106">不過，提供給或的述詞 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 會精確地叫用 `N` ，其中 `N` 是序列的長度。</span><span class="sxs-lookup"><span data-stu-id="6b484-106">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> is invoked exactly `N` times, where `N` is the length of the sequence.</span></span>

<span data-ttu-id="6b484-107">在 .NET 5.0 和更新版本中， [已進行](https://github.com/dotnet/runtime/pull/36643) 一項變更，因此呼叫 <xref:System.Linq.Enumerable.OrderBy%2A> 或 <xref:System.Linq.Enumerable.OrderByDescending%2A> 接著會 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 使用 `O(N log N)` 複雜性而不是複雜度來操作 `O(N)` 。</span><span class="sxs-lookup"><span data-stu-id="6b484-107">In .NET 5.0 and later versions, a [change was made](https://github.com/dotnet/runtime/pull/36643) such that calling <xref:System.Linq.Enumerable.OrderBy%2A> or <xref:System.Linq.Enumerable.OrderByDescending%2A> followed by <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> operates with `O(N log N)` complexity instead of `O(N)` complexity.</span></span> <span data-ttu-id="6b484-108">不過，提供給或的述詞 <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> 可能會叫用 *不* 到的 `N` 時間，這對整體效能較重要。</span><span class="sxs-lookup"><span data-stu-id="6b484-108">However, the predicate that's supplied to <xref:System.Linq.Enumerable.First%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> or <xref:System.Linq.Enumerable.FirstOrDefault%60%601(System.Collections.Generic.IEnumerable{%60%600},System.Func{%60%600,System.Boolean})> may be invoked *less* than `N` times, which is more important for overall performance.</span></span>

> [!NOTE]
> <span data-ttu-id="6b484-109">這項變更符合 .NET Framework 中作業的執行和複雜度。</span><span class="sxs-lookup"><span data-stu-id="6b484-109">This change matches the implementation and complexity of the operation in .NET Framework.</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="6b484-110">變更的原因</span><span class="sxs-lookup"><span data-stu-id="6b484-110">Reason for change</span></span>

<span data-ttu-id="6b484-111">叫用述詞的優點較少，因為整體複雜性較低，所以已還原 .NET Core 1.0 中引進的實作為。</span><span class="sxs-lookup"><span data-stu-id="6b484-111">The benefit of invoking the predicate fewer times outweighs a lower overall complexity, so the implementation that was introduced in .NET Core 1.0 was reverted.</span></span> <span data-ttu-id="6b484-112">如需詳細資訊，請參閱 [此 dotnet/執行時間問題](https://github.com/dotnet/runtime/issues/31554)。</span><span class="sxs-lookup"><span data-stu-id="6b484-112">For more information, see [this dotnet/runtime issue](https://github.com/dotnet/runtime/issues/31554).</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="6b484-113">引進的版本</span><span class="sxs-lookup"><span data-stu-id="6b484-113">Version introduced</span></span>

<span data-ttu-id="6b484-114">5.0</span><span class="sxs-lookup"><span data-stu-id="6b484-114">5.0</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="6b484-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="6b484-115">Recommended action</span></span>

<span data-ttu-id="6b484-116">開發人員的部分不需要採取任何動作。</span><span class="sxs-lookup"><span data-stu-id="6b484-116">No action is required on the developer's part.</span></span>

#### <a name="category"></a><span data-ttu-id="6b484-117">類別</span><span class="sxs-lookup"><span data-stu-id="6b484-117">Category</span></span>

<span data-ttu-id="6b484-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="6b484-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="6b484-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="6b484-119">Affected APIs</span></span>

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
