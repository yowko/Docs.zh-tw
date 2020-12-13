---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366875"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a><span data-ttu-id="32c51-101">將 GroupCollection 傳遞至採用 IEnumerable 的擴充方法需要去除混淆 \<T></span><span class="sxs-lookup"><span data-stu-id="32c51-101">Passing GroupCollection to extension methods taking IEnumerable\<T> requires disambiguation</span></span>

<span data-ttu-id="32c51-102">當呼叫採用的擴充方法時 `IEnumerable<T>` <xref:System.Text.RegularExpressions.GroupCollection> ，您必須使用 cast 來區分型別。</span><span class="sxs-lookup"><span data-stu-id="32c51-102">When calling an extension method that takes an `IEnumerable<T>` on a <xref:System.Text.RegularExpressions.GroupCollection>, you must disambiguate the type using a cast.</span></span>

#### <a name="change-description"></a><span data-ttu-id="32c51-103">變更描述</span><span class="sxs-lookup"><span data-stu-id="32c51-103">Change description</span></span>

<span data-ttu-id="32c51-104">從 .NET Core 3.0 開始， <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> `IEnumerable<KeyValuePair<String,Group>>` 除了它所執行的其他類型（包括）之外，還會執行 `IEnumerable<Group>` 。</span><span class="sxs-lookup"><span data-stu-id="32c51-104">Starting in .NET Core 3.0, <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> implements `IEnumerable<KeyValuePair<String,Group>>` in addition to the other types it implements, including `IEnumerable<Group>`.</span></span> <span data-ttu-id="32c51-105">這會導致呼叫採用的擴充方法時，會造成混淆 <xref:System.Collections.Generic.IEnumerable%601> 。</span><span class="sxs-lookup"><span data-stu-id="32c51-105">This results in ambiguity when calling an extension method that takes an <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="32c51-106">例如，如果您在實例上呼叫這類擴充方法， <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> 您會看到下列編譯器錯誤：</span><span class="sxs-lookup"><span data-stu-id="32c51-106">If you call such an extension method on a <xref:System.Text.RegularExpressions.GroupCollection> instance, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType>, you'll see the following compiler error:</span></span>

<span data-ttu-id="32c51-107">**CS1061： ' GroupCollection ' 不包含 ' Count ' 的定義，且找不到任何可接受類型 ' GroupCollection ' 的第一個引數的可存取擴充方法 ' Count ' (您是否遺漏 using 指示詞或元件參考？ )**</span><span class="sxs-lookup"><span data-stu-id="32c51-107">**CS1061: 'GroupCollection' does not contain a definition for 'Count' and no accessible extension method 'Count' accepting a first argument of type 'GroupCollection' could be found (are you missing a using directive or an assembly reference?)**</span></span>

<span data-ttu-id="32c51-108">在舊版的 .NET 中，並沒有任何明確的編譯器錯誤。</span><span class="sxs-lookup"><span data-stu-id="32c51-108">In previous versions of .NET, there was no ambiguity and no compiler error.</span></span>

#### <a name="version-introduced"></a><span data-ttu-id="32c51-109">引進的版本</span><span class="sxs-lookup"><span data-stu-id="32c51-109">Version introduced</span></span>

<span data-ttu-id="32c51-110">3.0</span><span class="sxs-lookup"><span data-stu-id="32c51-110">3.0</span></span>

#### <a name="reason-for-change"></a><span data-ttu-id="32c51-111">變更的原因</span><span class="sxs-lookup"><span data-stu-id="32c51-111">Reason for change</span></span>

<span data-ttu-id="32c51-112">這是 [意外的重大變更](https://github.com/dotnet/corefx/pull/30077)。</span><span class="sxs-lookup"><span data-stu-id="32c51-112">This was an [unintentional breaking change](https://github.com/dotnet/corefx/pull/30077).</span></span> <span data-ttu-id="32c51-113">因為這是一段時間，所以我們不打算將它還原。</span><span class="sxs-lookup"><span data-stu-id="32c51-113">Because it has been like this for some time, we don't plan to revert it.</span></span> <span data-ttu-id="32c51-114">此外，這類變更本身也會中斷。</span><span class="sxs-lookup"><span data-stu-id="32c51-114">In addition, such a change would itself be breaking.</span></span>

#### <a name="recommended-action"></a><span data-ttu-id="32c51-115">建議的動作</span><span class="sxs-lookup"><span data-stu-id="32c51-115">Recommended action</span></span>

<span data-ttu-id="32c51-116">針對 <xref:System.Text.RegularExpressions.GroupCollection> 實例，對接受具有轉換之的擴充方法進行區分 `IEnumerable<T>` 。</span><span class="sxs-lookup"><span data-stu-id="32c51-116">For <xref:System.Text.RegularExpressions.GroupCollection> instances, disambiguate calls to extension methods that accept an `IEnumerable<T>` with a cast.</span></span>

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a><span data-ttu-id="32c51-117">類別</span><span class="sxs-lookup"><span data-stu-id="32c51-117">Category</span></span>

<span data-ttu-id="32c51-118">Core .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="32c51-118">Core .NET libraries</span></span>

#### <a name="affected-apis"></a><span data-ttu-id="32c51-119">受影響的 API</span><span class="sxs-lookup"><span data-stu-id="32c51-119">Affected APIs</span></span>

<span data-ttu-id="32c51-120">任何接受的擴充方法 <xref:System.Collections.Generic.IEnumerable%601> 都會受到影響。</span><span class="sxs-lookup"><span data-stu-id="32c51-120">Any extension method that accepts an <xref:System.Collections.Generic.IEnumerable%601> is affected.</span></span> <span data-ttu-id="32c51-121">例如：</span><span class="sxs-lookup"><span data-stu-id="32c51-121">For example:</span></span>

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- <span data-ttu-id="32c51-122">大部分的 `System.Linq.Enumerable` 方法，例如 <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span><span class="sxs-lookup"><span data-stu-id="32c51-122">Most of the `System.Linq.Enumerable` methods, for example, <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName></span></span>
- <xref:System.Linq.ParallelEnumerable.AsParallel%2A?displayProperty=fullName>
- <xref:System.Linq.Queryable.AsQueryable%2A?displayProperty=fullName>

<!--

#### Affected APIs

- ``M:System.Collections.Immutable.ImmutableArray.ToImmutableArray``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary`
- `Overload:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet`
- ``M:System.Collections.Immutable.ImmutableList.ToImmutableList``1(System.Collections.Generic.IEnumerable{``0})``
- `Overload:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary`
- `Overload:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet`
- `Overload:System.Data.DataTableExtensions.CopyToDataTable`
- `Overload:System.Linq.Enumerable.Count`
- `Overload:System.Linq.ParallelEnumerable.AsParallel`
- `Overload:System.Linq.Queryable.AsQueryable`

-->
