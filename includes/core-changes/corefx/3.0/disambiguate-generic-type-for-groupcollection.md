---
ms.openlocfilehash: 97fab784acac4331894547eea27fc21b485597fb
ms.sourcegitcommit: fcbe432482464b1639decad78cc4dc8387c6269e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/12/2020
ms.locfileid: "97366875"
---
### <a name="passing-groupcollection-to-extension-methods-taking-ienumerablet-requires-disambiguation"></a>將 GroupCollection 傳遞至採用 IEnumerable 的擴充方法需要去除混淆 \<T>

當呼叫採用的擴充方法時 `IEnumerable<T>` <xref:System.Text.RegularExpressions.GroupCollection> ，您必須使用 cast 來區分型別。

#### <a name="change-description"></a>變更描述

從 .NET Core 3.0 開始， <xref:System.Text.RegularExpressions.GroupCollection?displayProperty=nameWithType> `IEnumerable<KeyValuePair<String,Group>>` 除了它所執行的其他類型（包括）之外，還會執行 `IEnumerable<Group>` 。 這會導致呼叫採用的擴充方法時，會造成混淆 <xref:System.Collections.Generic.IEnumerable%601> 。 例如，如果您在實例上呼叫這類擴充方法， <xref:System.Text.RegularExpressions.GroupCollection> <xref:System.Linq.Enumerable.Count%2A?displayProperty=nameWithType> 您會看到下列編譯器錯誤：

**CS1061： ' GroupCollection ' 不包含 ' Count ' 的定義，且找不到任何可接受類型 ' GroupCollection ' 的第一個引數的可存取擴充方法 ' Count ' (您是否遺漏 using 指示詞或元件參考？ )**

在舊版的 .NET 中，並沒有任何明確的編譯器錯誤。

#### <a name="version-introduced"></a>引進的版本

3.0

#### <a name="reason-for-change"></a>變更的原因

這是 [意外的重大變更](https://github.com/dotnet/corefx/pull/30077)。 因為這是一段時間，所以我們不打算將它還原。 此外，這類變更本身也會中斷。

#### <a name="recommended-action"></a>建議的動作

針對 <xref:System.Text.RegularExpressions.GroupCollection> 實例，對接受具有轉換之的擴充方法進行區分 `IEnumerable<T>` 。

```csharp
// Without a cast - causes CS1061.
match.Groups.Count(_ => true)

// With a disambiguating cast.
((IEnumerable<Group>)m.Groups).Count(_ => true);
```

#### <a name="category"></a>類別

Core .NET 程式庫

#### <a name="affected-apis"></a>受影響的 API

任何接受的擴充方法 <xref:System.Collections.Generic.IEnumerable%601> 都會受到影響。 例如：

- <xref:System.Collections.Immutable.ImmutableArray.ToImmutableArray%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableDictionary.ToImmutableDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableHashSet.ToImmutableHashSet%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableList.ToImmutableList%60%601(System.Collections.Generic.IEnumerable{%60%600})?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedDictionary.ToImmutableSortedDictionary%2A?displayProperty=fullName>
- <xref:System.Collections.Immutable.ImmutableSortedSet.ToImmutableSortedSet%2A?displayProperty=fullName>
- <xref:System.Data.DataTableExtensions.CopyToDataTable%2A?displayProperty=fullName>
- 大部分的 `System.Linq.Enumerable` 方法，例如 <xref:System.Linq.Enumerable.Count%2A?displayProperty=fullName>
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
