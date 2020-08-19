---
title: 可為 Null 的運算子
description: '瞭解 F # 程式設計語言中可用的可為 null 運算子。'
ms.date: 05/16/2016
ms.openlocfilehash: 951692ba22781f7f9e759c55bc708fc24f7a5014
ms.sourcegitcommit: 8bfeb5930ca48b2ee6053f16082dcaf24d46d221
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/18/2020
ms.locfileid: "88559137"
---
# <a name="nullable-operators"></a>可為 Null 的運算子

可為 null 的運算子是二元算術或比較運算子，可在一或兩個邊使用可為 null 的算術類型。 當您使用來自來源的資料（例如允許 null 來取代實際值的資料庫）時，就會經常發生可為 null 的類型。 可為 null 的運算子經常用於查詢運算式中。 除了算術和比較可為 null 的運算子之外，轉換運算子也可以用來在可為 null 的類型之間轉換。 某些查詢運算子也有可為 null 的版本。

## <a name="table-of-nullable-operators"></a>可為 Null 運算子的資料表

下表列出 F # 語言支援的可為 null 運算子。

|左邊可為 null|右邊可為 null|兩端都可為 null|
|---|---|---|
|[？ >=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=%20))|[>=？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E=?%20))|[？ >=？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E=?%20))|
|[？ >](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E%20))|[>？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3E?%20))|[？ > 嗎？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3E?%20))|
|[？ <=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=%20))|[<=？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C=?%20))|[？ <=？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C=?%20))|
|[？ <](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%20))|[<？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C?%20))|[？ < 嗎？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C?%20))|
|[?=](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=%20))|[=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20=?%20))|[?=?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?=?%20))|
|[？ <>](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E%20))|[<>？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%3C%3E?%20))|[？ <> 嗎？](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%3C%3E?%20))|
|[?+](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+%20))|[+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20+?%20))|[?+?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?+?%20))|
|[?-](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-%20))|[-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20-?%20))|[?-?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?-?%20))|
|[?*](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*%20))|[*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20*?%20))|[?*?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?*?%20))|
|[?/](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/%20))|[/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20/?%20))|[?/?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?/?%20))|
|[?%](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%%20))|[%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20%?%20))|[?%?](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html#(%20?%?%20))|

## <a name="remarks"></a>備註

可為 null 的運算子會包含在命名空間[fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html)的[NullableOperators](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullableoperators.html)模組中。 可為 null 的資料類型為 `System.Nullable<'T>` 。

在查詢運算式中，從允許 null 而非值的資料來源中選取資料時，就會產生可為 null 的類型。 在 SQL Server 資料庫中，資料表中的每個資料行都有一個屬性，指出是否允許 null。 如果允許 null，則從資料庫傳回的資料可以包含無法以基本資料類型（例如、等）表示的 null `int` `float` 。 因此，資料會以 `System.Nullable<int>` 取代，而不是傳回 `int` `System.Nullable<float>` `float` 。 您可以使用屬性從物件取得實際值 `System.Nullable<'T>` `Value` ，而且您可以藉 `System.Nullable<'T>` 由呼叫方法來判斷物件是否具有值 `HasValue` 。 另一個實用的方法是 `System.Nullable<'T>.GetValueOrDefault` 方法，可讓您取得適當類型的值或預設值。 預設值是某種形式的「零」值，例如0、0.0 或 `false` 。

可為 null 的型別可以使用一般的轉換運算子（例如或）轉換成不可為 null 的基本類型 `int` `float` 。 您也可以使用可為 null 型別的轉換運算子，從一個可為 null 的型別轉換為另一個可為 null 的型別。 適當的轉換運算子具有與標準名稱相同的名稱，但它們位於不同的模組中，也就是[fsharp.core](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq.html)命名空間中的[可為 null](https://fsharp.github.io/fsharp-core-docs/reference/fsharp-linq-nullablemodule.html)模組。 一般而言，您會在使用查詢運算式時開啟此命名空間。 在這種情況下，您可以將前置詞加入至適當的轉換運算子，以使用可為 null 的轉換運算子 `Nullable.` ，如下列程式碼所示。

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

輸出為 `10.000000`。

可為 null 的資料欄位（例如）的查詢運算子 `sumByNullable` 也存在於查詢運算式中。 非 nullable 型別的查詢運算子與可為 null 的型別不相容，因此當您使用可為 null 的資料值時，您必須使用適當查詢運算子的可為 null 版本。 如需詳細資訊，請參閱 [查詢運算式](../query-expressions.md)。

下列範例示範如何在 F # 查詢運算式中使用可為 null 的運算子。 第一個查詢顯示如何撰寫沒有可為 null 運算子的查詢;第二個查詢顯示使用可為 null 運算子的對等查詢。 如需完整的內容，包括如何設定資料庫以使用此範例程式碼，請參閱 [逐步解說：使用類型提供者存取 SQL Database](../../tutorials/type-providers/index.md)。

```fsharp
open System
open System.Data
open System.Data.Linq
open Microsoft.FSharp.Data.TypeProviders
open Microsoft.FSharp.Linq

[<Generate>]
type dbSchema = SqlDataConnection<"Data Source=MYSERVER\INSTANCE;Initial Catalog=MyDatabase;Integrated Security=SSPI;">

let db = dbSchema.GetDataContext()

query {
    for row in db.Table2 do
    where (row.TestData1.HasValue && row.TestData1.Value > 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" row.TestData1.Value row.Name)

query {
    for row in db.Table2 do
    // Use a nullable operator ?>
    where (row.TestData1 ?> 2)
    select row
} |> Seq.iter (fun row -> printfn "%d %s" (row.TestData1.GetValueOrDefault()) row.Name)
```

## <a name="see-also"></a>另請參閱

- [型別提供者](../../tutorials/type-providers/index.md)
- [查詢運算式](../query-expressions.md)
