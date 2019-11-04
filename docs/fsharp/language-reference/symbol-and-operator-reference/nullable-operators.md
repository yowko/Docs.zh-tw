---
title: 可為 Null 的運算子
description: 瞭解程式F#設計語言中可為 null 的運算子。
ms.date: 05/16/2016
ms.openlocfilehash: 9c747cf5c2e07ca9f80cef741d71d892fb437b3a
ms.sourcegitcommit: 14ad34f7c4564ee0f009acb8bfc0ea7af3bc9541
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2019
ms.locfileid: "73424049"
---
# <a name="nullable-operators"></a>可為 Null 的運算子

可為 null 的運算子為二元算術或比較運算子，可在一或兩側使用可為 null 的算術類型。 當您使用來自來源的資料（例如資料庫），以允許 null 來取代實際的值時，就會經常發生可為 null 的類型。 可為 null 的運算子經常用於查詢運算式中。 除了適用于算術和比較的可為 null 運算子之外，轉換運算子也可以用來在可為 null 的型別之間轉換。 某些查詢運算子也有可為 null 的版本。

## <a name="table-of-nullable-operators"></a>可為 Null 之運算子的資料表

下表列出語言中支援的F#可為 null 的運算子。

|左邊為 Nullable|右邊為 Nullable|兩邊可為 null|
|---|---|---|
|[？ > =](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[> =？](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[？ > =？](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[？ >](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[> 嗎？](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[？ >？](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[？ < =](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[< =？](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[？ < =？](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[？ <](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[< 嗎？](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[？ <？](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[？ < >](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[< > 嗎？](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[< > 嗎？](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>備註

可為 null 的運算子包含在[fsharp.core](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)命名空間的[NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007)模組中。 可為 null 的資料類型為 `System.Nullable<'T>`。

在查詢運算式中，從允許 null 而非值的資料來源選取資料時，就會發生可為 null 的類型。 在 SQL Server 資料庫中，資料表中的每個資料行都有一個屬性，指出是否允許 null。 如果允許 null，從資料庫傳回的資料可以包含 null，而這些資料類型無法以基本型別（例如 `int`、`float`等等）來表示。 因此，資料會以 `System.Nullable<int>` 傳回，而不是 `int`，而是 `System.Nullable<float>`，而不是 `float`。 您可以使用 `Value` 屬性從 `System.Nullable<'T>` 物件取得實際的值，而且您可以藉由呼叫 `HasValue` 方法，判斷 `System.Nullable<'T>` 物件是否有值。 另一個有用的方法是 `System.Nullable<'T>.GetValueOrDefault` 方法，可讓您取得適當類型的值或預設值。 預設值為「零」值的某種形式，例如0、0.0 或 `false`。

您可以使用一般轉換運算子（例如 `int` 或 `float`），將可為 null 的類型轉換成不可為 null 的基本類型。 您也可以使用可為 null 類型的轉換運算子，從可為 null 的型別轉換成另一個可為 null 的型別。 適當的轉換運算子具有與標準的相同名稱，但它們位於不同的模組中，也就是[fsharp.core](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)中的[可為 null](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e)的模組。 一般而言，當您使用查詢運算式時，會開啟此命名空間。 在這種情況下，您可以使用可為 null 的轉換運算子，方法是將前置詞 `Nullable.` 新增至適當的轉換運算子，如下列程式碼所示。

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

輸出為 `10.000000`。

可為 null 的資料欄位（例如 `sumByNullable`）上的查詢運算子也存在，以便用於查詢運算式中。 不可為 null 類型的查詢運算子與可為 null 的類型不相容，因此當您使用可為 null 的資料值時，您必須使用適當查詢運算子的可為 null 版本。 如需詳細資訊，請參閱[查詢運算式](../query-expressions.md)。

下列範例示範如何在F#查詢運算式中使用可為 null 的運算子。 第一個查詢顯示如何撰寫不含可為 null 運算子的查詢;第二個查詢會顯示使用可為 null 運算子的對等查詢。 如需完整內容，包括如何設定資料庫以使用此範例程式碼，請參閱[逐步解說：使用型別提供者存取 SQL Database](../../tutorials/type-providers/index.md)。

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

## <a name="see-also"></a>請參閱

- [類型提供者](../../tutorials/type-providers/index.md)
- [查詢運算式](../query-expressions.md)
