---
title: 可為 Null 的運算子 (F#)
description: '深入了解 F # 程式語言中可用的可為 null 運算子。'
ms.date: 05/16/2016
ms.openlocfilehash: 63ad7da2d584b96eee8765b57fc671befbcbd38b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="nullable-operators"></a>可為 Null 的運算子

可為 null 的運算子都是一或兩端使用可為 null 的算術類型的二進位算術或比較運算子。 經常在您使用的資料來源 （例如資料庫），允許 null 值，用來取代實際的值時，會引發可為 null 的類型。 可為 null 的運算子經常用於查詢運算式。 可為 null 的算術和比較運算子，除了轉換運算子可以用於可為 null 的類型之間轉換。 也有特定的查詢運算子可為 null 的版本。


## <a name="table-of-nullable-operators"></a>資料表的可為 Null 的運算子
下表列出可為 null 的運算子在 F # 語言支援。

|在左邊的 可為 null|在右邊的 可為 null|雙方可為 null|
|---|---|---|
|[?>=](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[>=?](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[?>=?](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[?>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[>?](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[?>?](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[?<=](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<=?](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[?<=?](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[?<](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<?](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[?<?](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[?=](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[=?](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[?=?](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[?<>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<>?](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[?<>?](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[?+](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[+?](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[?+?](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[?-](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[-?](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[?-?](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[?*](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[*?](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[?*?](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[?/](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[/?](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[?/?](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[?%](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[%?](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[?%?](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a>備註
可為 null 的運算子會包含在[NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007)命名空間中的模組[Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)。 可為 null 的資料類型是`System.Nullable<'T>`。

在查詢運算式中，從允許 null，而不是值的資料來源選取資料時，會引發可為 null 的類型。 在 SQL Server 資料庫中，資料表中的每個資料行具有屬性，指出是否允許 null。 如果允許 null 值，從資料庫傳回的資料可以包含 null 無法表示的基本資料類型例如`int`， `float`，依此類推。 因此，資料會做為傳回`System.Nullable<int>`而不是`int`，和`System.Nullable<float>`而不是`float`。 實際的值可以取自`System.Nullable<'T>`物件使用`Value`屬性，而且您可以判斷如果`System.Nullable<'T>`物件具有值，藉由呼叫`HasValue`方法。 另一個有用的方法是`System.Nullable<'T>.GetValueOrDefault`方法，可讓您取得的值或預設值是適當的型別。 預設值是某種形式的 「 零 」 值，例如 0、 0.0 或`false`。

可為 null 的型別可能會轉換成不可為 null 的基本型別使用的一般轉換運算子，例如`int`或`float`。 它也可將從一種可為 null 的類型轉換成另一種可為 null 的類型使用轉換運算子，可為 null 的類型。 適當的轉換運算子有相同的名稱做為標準的但是可以在不同的模組， [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e)中的模組[Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)命名空間。 一般而言，使用查詢運算式時開啟此命名空間。 在此情況下，您可以使用可為 null 的轉換運算子，加上前置詞`Nullable.`適當的轉換運算子，如下列程式碼所示。

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

輸出為 `10.000000`。

查詢運算子，可為 null 的資料欄位，例如`sumByNullable`，同時存在的查詢運算式中使用。 不可為 null 類型的查詢運算子不是可為 null 的類型，類型相容，因此當您使用可為 null 的資料值時，您必須使用適當的查詢運算子的 null 版本。 如需詳細資訊，請參閱[查詢運算式](../query-expressions.md)。

下列範例會顯示在 F # 查詢運算式中使用可為 null 的運算子。 第一個查詢示範如何撰寫不含可為 null 的運算子; 查詢第二個查詢示範會使用可為 null 的運算子的對等查詢。 完整的內容，包括如何設定資料庫以使用此範例程式碼，請參閱[逐步解說： 存取 SQL 資料庫所使用的型別提供者](../../tutorials/type-providers/accessing-a-sql-database.md)。

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

[類型提供者](../../tutorials/type-providers/index.md)

[查詢運算式](../query-expressions.md)
