---
title: 在匿名和元組類型之間選擇
description: 瞭解何時適合在匿名型別和元組類型之間進行選擇。
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.openlocfilehash: f8465b2f22ecfafd739355ddd35635e2eee49232
ms.sourcegitcommit: 965a5af7918acb0a3fd3baf342e15d511ef75188
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/18/2020
ms.locfileid: "94823195"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>在匿名和元組類型之間選擇

選擇適當的類型牽涉到考慮其可用性、效能和取捨，相較于其他類型。 自 c # 3.0 起已提供匿名型別，但 <xref:System.Tuple%602?displayProperty=nameWithType> .NET Framework 4.0 引進了泛型型別。 自從起，新選項在語言層級支援上引進，像是 <xref:System.ValueTuple%602?displayProperty=nameWithType> 名稱所暗示的，提供具有匿名型別彈性的實值型別。 在本文中，您將瞭解何時適合選擇另一種類型。

## <a name="usability-and-functionality"></a>可用性和功能

匿名型別是在 c # 3.0 中引進的 Language-Integrated Query (LINQ) 運算式。 使用 LINQ，開發人員通常會將查詢的結果投射至匿名型別，這些型別會從他們正在使用的物件中保存一些 select 屬性。 請看下列範例，它會具現化 <xref:System.DateTime> 物件的陣列，並逐一查看其投射到具有兩個屬性的匿名型別。

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var anonymous in
             dates.Select(
                 date => new { Formatted = $"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks }))
{
    Console.WriteLine($"Ticks: {anonymous.Ticks}, formatted: {anonymous.Formatted}");
}
```

匿名型別是使用運算子來具現化 [`new`](../../csharp/language-reference/operators/new-operator.md) ，而屬性名稱和類型則是從宣告推斷而來。 如果相同元件中有兩個或多個匿名物件初始化運算式指定的屬性順序順序相同，而且具有相同的名稱和類型，則編譯器會將這些物件視為相同型別的實例。 這些物件會共用編譯器產生的相同類型資訊。

先前的 c # 程式碼片段會使用兩個屬性來投影匿名型別，與下列編譯器產生的 c # 類別很類似：

```csharp
internal sealed class f__AnonymousType0
{
    public string Formatted { get; }
    public long Ticks { get; }

    public f__AnonymousType0(string formatted, long ticks)
    {
        Formatted = formatted;
        Ticks = ticks;
    }
}
```

如需詳細資訊，請參閱 [匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)。 當元組投射到 LINQ 查詢時，也會有相同的功能，您可以選取屬性到元組中。 這些元組會流經查詢，就像匿名型別一樣。 現在請考慮使用下列範例 `System.Tuple<string, long>` 。

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var tuple in
            dates.Select(
                date => new Tuple<string, long>($"{date:MMM dd, yyyy hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {tuple.Item2}, formatted: {tuple.Item1}");
}
```

使用時 <xref:System.Tuple%602?displayProperty=nameWithType> ，實例會公開編號的專案屬性，例如 `Item1` 和 `Item2` 。 這些屬性名稱可能會讓您更難以瞭解屬性值的意圖，因為屬性名稱只提供序數。 此外， `System.Tuple` 類型是參考型別 `class` 。 <xref:System.ValueTuple%602?displayProperty=nameWithType>不過，是實值 `struct` 型別。 下列 c # 程式碼片段會使用 `ValueTuple<string, long>` 來投影至。 在這麼做時，它會使用常值語法來指派。

```csharp-interactive
var dates = new[]
{
    DateTime.UtcNow.AddHours(-1),
    DateTime.UtcNow,
    DateTime.UtcNow.AddHours(1),
};

foreach (var (formatted, ticks) in
            dates.Select(
                date => (Formatted: $"{date:MMM dd, yyyy at hh:mm zzz}", date.Ticks)))
{
    Console.WriteLine($"Ticks: {ticks}, formatted: {formatted}");
}
```

如需有關元組的詳細資訊，請參閱 [ (c # 參考) ](../../csharp/language-reference/builtin-types/value-tuples.md) 或 [元組 (Visual Basic) ](../../visual-basic/programming-guide/language-features/data-types/tuples.md)的元組類型。

上述範例的功能相同，但它們的可用性和其基礎執行之間有些微差異。

## <a name="tradeoffs"></a>權衡取捨

您可能會想要一律使用 <xref:System.ValueTuple> over <xref:System.Tuple> 和匿名型別，但您應該考慮一些取捨。 這些 <xref:System.ValueTuple> 類型是可變動的，而 <xref:System.Tuple> 是唯讀的。 匿名型別可在運算式樹狀架構中使用，而元組則無法使用。 下表概述一些主要差異。

### <a name="key-differences"></a>主要差異

| 名稱                     | 存取修飾詞 | 類型     | 自訂成員名稱 | 解構支援 | 運算式樹狀架構支援 |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| 匿名型別          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>序列化

選擇類型時的一個重要考慮是，是否需要將它序列化。 序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。 如需詳細資訊，請參閱 [序列化](../../csharp/programming-guide/concepts/serialization/index.md)。 當序列化很重要時，最好 `class` 透過 `struct` 匿名型別或元組類型來建立或。

## <a name="performance"></a>效能

這些類型之間的效能取決於案例。 主要的影響牽涉到配置和複製之間的取捨。 在大部分的情況下，影響很小。 發生重大影響時，應該採取度量來通知決策。

## <a name="conclusion"></a>結論

當開發人員在元組和匿名型別之間進行選擇時，需要考慮幾個因素。 一般來說，如果您不是使用 [運算式樹狀](../../csharp/expression-trees.md)架構，而且您熟悉元組語法，則請選擇 <xref:System.ValueTuple> 其提供實值型別，而且可以彈性地命名屬性。 如果您是使用運算式樹狀架構，而且想要命名屬性，請選擇 [匿名型別]。 否則，使用 <xref:System.Tuple>。

## <a name="see-also"></a>請參閱

- [匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [運算式樹狀架構](../../csharp/expression-trees.md)
- [元組類型 (c # 參考) ](../../csharp/language-reference/builtin-types/value-tuples.md)
- [元組 (Visual Basic) ](../../visual-basic/programming-guide/language-features/data-types/tuples.md)
- [類型設計方針](../design-guidelines/type.md)
