---
title: 在匿名和元組類型之間選擇
description: 瞭解何時適合在匿名型別和元組類型之間進行選擇。
author: IEvangelist
ms.author: dapine
ms.date: 07/01/2020
ms.technology: dotnet-standard
ms.openlocfilehash: 9140250ad1f48501bf1d2e53a1c179e6823f19cd
ms.sourcegitcommit: 4ad2f8920251f3744240c3b42a443ffbe0a46577
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/08/2020
ms.locfileid: "86100960"
---
# <a name="choosing-between-anonymous-and-tuple-types"></a>在匿名和元組類型之間選擇

選擇適當的類型牽涉到考慮與其他類型相較之下的可用性、效能和取捨。 自 c # 3.0 開始已提供匿名型別，而泛型 <xref:System.Tuple%602?displayProperty=nameWithType> 類型是在 .NET Framework 4.0 中引進。 自起，已引進語言層級支援的新選項，例如 <xref:System.ValueTuple%602?displayProperty=nameWithType> ，如名稱所示，則提供具有匿名型別彈性的實數值型別。 在本文中，您將瞭解何時適合選擇其中一種類型。

## <a name="usability-and-functionality"></a>可用性和功能

匿名型別是使用語言整合式查詢（LINQ）運算式，在 c # 3.0 中引進。 使用 LINQ 時，開發人員通常會將查詢的結果投影到匿名型別，其中包含所要使用之物件的幾個 select 屬性。 請考慮下列範例，其會具現化 <xref:System.DateTime> 物件的陣列，並逐一查看其投射為具有兩個屬性的匿名型別。

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

匿名型別是使用運算子來具現化 [`new`](../../csharp/language-reference/operators/new-operator.md) ，而屬性名稱和類型則是從宣告推斷而來。 如果相同元件中的兩個或多個匿名物件初始化運算式指定順序相同且具有相同名稱和類型的屬性，則編譯器會將這些物件視為相同類型的實例。 這些物件會共用編譯器產生的相同類型資訊。

先前的 c # 程式碼片段會使用兩個屬性來投射匿名型別，與下列編譯器產生的 c # 類別非常類似：

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

如需詳細資訊，請參閱[匿名](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)型別。 在投射至 LINQ 查詢時，元組也存在相同的功能，您可以選取屬性到元組中。 這些元組會流經查詢，就像匿名型別一樣。 現在請考慮下列使用的範例 `System.Tuple<string, long>` 。

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

使用 <xref:System.Tuple%602?displayProperty=nameWithType> ，實例會公開編號的專案屬性，例如 `Item1` 、和 `Item2` 。 這些屬性名稱可能會讓您更難以瞭解屬性值的用途，因為屬性名稱只會提供序數。 此外， `System.Tuple` 類型是引用 `class` 類型。 <xref:System.ValueTuple%602?displayProperty=nameWithType>不過，是實值 `struct` 型別。 下列 c # 程式碼片段會使用 `ValueTuple<string, long>` 來投影至。 在這麼做的情況下，它會使用常值語法來指派。

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

C # 提供具有類型的元組語言支援 <xref:System.ValueTuple> ，以及的語義：

- [元組指派](../../csharp/tuples.md#assignment-and-tuples)
- [元組解構](../../csharp/deconstruct.md)（不限於元組）
- [元組等號檢查](../../csharp/tuples.md#equality-and-tuples)
- [元組投影初始設定式](../../csharp/tuples.md#tuple-projection-initializers)

不過，上述範例的功能完全相同。其可用性和其基礎的執行方式稍有不同。

## <a name="tradeoffs"></a>權衡取捨

您可能想要一律使用 <xref:System.ValueTuple> over <xref:System.Tuple> 和匿名型別，但您應該考慮一些取捨。 <xref:System.ValueTuple>類型是可變動的，而 <xref:System.Tuple> 是唯讀的。 匿名型別可以在運算式樹狀架構中使用，而元組則不能。 下表概述一些主要差異。

### <a name="key-differences"></a>主要差異

| 名稱                     | 存取修飾詞 | 類型     | 自訂成員名稱 | 解構支援 | 運算式樹狀架構支援 |
|--------------------------|-----------------|----------|----------------------|------------------------|-------------------------|
| 匿名型別          | `internal`      | `class`  | ✔️                   | ❌                     | ✔️                     |
| <xref:System.Tuple>      | `public`        | `class`  | ❌                   | ❌                     | ✔️                     |
| <xref:System.ValueTuple> | `public`        | `struct` | ✔️                   | ✔️                     | ❌                     |

### <a name="serialization"></a>序列化

選擇類型時，有一個重要的考慮，那就是是否需要將它序列化。 序列化是將物件的狀態轉換成可保存或傳輸之形式的程序。 如需詳細資訊，請參閱[序列化](../../csharp/programming-guide/concepts/serialization/index.md)。 當序列化很重要時， `class` `struct` 最好是透過匿名型別或元組類型來建立或。

## <a name="performance"></a>效能

這些類型之間的效能取決於案例。 主要的影響牽涉到配置與複製之間的取捨。 在大部分的情況下，影響很小。 發生重大影響時，應該採取測量來通知決策。

## <a name="conclusion"></a>結論

身為開發人員選擇元組和匿名型別，有幾個因素需要考慮。 一般來說，如果您不是使用[運算式樹狀](../../csharp/expression-trees.md)架構，而且您很熟悉元組語法，請選擇， <xref:System.ValueTuple> 因為它們提供實值型別並具有名稱屬性的彈性。 如果您是使用運算式樹狀架構，而且想要命名屬性，請選擇 [匿名型別]。 否則，使用 <xref:System.Tuple>。

## <a name="see-also"></a>另請參閱

- [匿名型別](../../csharp/programming-guide/classes-and-structs/anonymous-types.md)
- [運算式樹狀架構](../../csharp/expression-trees.md)
- [元組類型](../../csharp/tuples.md)
- [類型設計方針](../design-guidelines/type.md)
