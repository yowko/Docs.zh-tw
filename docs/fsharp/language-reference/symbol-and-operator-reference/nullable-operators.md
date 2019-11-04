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
# <a name="nullable-operators"></a><span data-ttu-id="94bfb-103">可為 Null 的運算子</span><span class="sxs-lookup"><span data-stu-id="94bfb-103">Nullable Operators</span></span>

<span data-ttu-id="94bfb-104">可為 null 的運算子為二元算術或比較運算子，可在一或兩側使用可為 null 的算術類型。</span><span class="sxs-lookup"><span data-stu-id="94bfb-104">Nullable operators are binary arithmetic or comparison operators that work with nullable arithmetic types on one or both sides.</span></span> <span data-ttu-id="94bfb-105">當您使用來自來源的資料（例如資料庫），以允許 null 來取代實際的值時，就會經常發生可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="94bfb-105">Nullable types arise frequently when you work with data from sources such as databases that allow nulls in place of actual values.</span></span> <span data-ttu-id="94bfb-106">可為 null 的運算子經常用於查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="94bfb-106">Nullable operators are used frequently in query expressions.</span></span> <span data-ttu-id="94bfb-107">除了適用于算術和比較的可為 null 運算子之外，轉換運算子也可以用來在可為 null 的型別之間轉換。</span><span class="sxs-lookup"><span data-stu-id="94bfb-107">In addition to nullable operators for arithmetic and comparison, conversion operators can be used to convert between nullable types.</span></span> <span data-ttu-id="94bfb-108">某些查詢運算子也有可為 null 的版本。</span><span class="sxs-lookup"><span data-stu-id="94bfb-108">There are also nullable versions of certain query operators.</span></span>

## <a name="table-of-nullable-operators"></a><span data-ttu-id="94bfb-109">可為 Null 之運算子的資料表</span><span class="sxs-lookup"><span data-stu-id="94bfb-109">Table of Nullable Operators</span></span>

<span data-ttu-id="94bfb-110">下表列出語言中支援的F#可為 null 的運算子。</span><span class="sxs-lookup"><span data-stu-id="94bfb-110">The following table lists nullable operators supported in the F# language.</span></span>

|<span data-ttu-id="94bfb-111">左邊為 Nullable</span><span class="sxs-lookup"><span data-stu-id="94bfb-111">Nullable on left</span></span>|<span data-ttu-id="94bfb-112">右邊為 Nullable</span><span class="sxs-lookup"><span data-stu-id="94bfb-112">Nullable on right</span></span>|<span data-ttu-id="94bfb-113">兩邊可為 null</span><span class="sxs-lookup"><span data-stu-id="94bfb-113">Both sides nullable</span></span>|
|---|---|---|
|[<span data-ttu-id="94bfb-114">？ > =</span><span class="sxs-lookup"><span data-stu-id="94bfb-114">?>=</span></span>](https://msdn.microsoft.com/library/94d29e32-a204-4f60-a527-6b0af86268f3)|[<span data-ttu-id="94bfb-115">> =？</span><span class="sxs-lookup"><span data-stu-id="94bfb-115">>=?</span></span>](https://msdn.microsoft.com/library/0a255d8e-8cae-4160-ae61-243a5d96583f)|[<span data-ttu-id="94bfb-116">？ > =？</span><span class="sxs-lookup"><span data-stu-id="94bfb-116">?>=?</span></span>](https://msdn.microsoft.com/library/3051a50f-d276-4c84-9d73-bf2efeddef94)|
|[<span data-ttu-id="94bfb-117">？ ></span><span class="sxs-lookup"><span data-stu-id="94bfb-117">?></span></span>](https://msdn.microsoft.com/library/62dc0021-1312-4ac3-be87-798b60b81bb6)|[<span data-ttu-id="94bfb-118">> 嗎？</span><span class="sxs-lookup"><span data-stu-id="94bfb-118">>?</span></span>](https://msdn.microsoft.com/library/0ad1284b-de48-4a04-83d8-b6f13c9c8936)|[<span data-ttu-id="94bfb-119">？ >？</span><span class="sxs-lookup"><span data-stu-id="94bfb-119">?>?</span></span>](https://msdn.microsoft.com/library/dc18b6fa-30c4-47b0-9057-794439378a05)|
|[<span data-ttu-id="94bfb-120">？ < =</span><span class="sxs-lookup"><span data-stu-id="94bfb-120">?<=</span></span>](https://msdn.microsoft.com/library/56fddf0a-e4ca-4891-a3be-fad1876be3b6)|[<span data-ttu-id="94bfb-121">< =？</span><span class="sxs-lookup"><span data-stu-id="94bfb-121"><=?</span></span>](https://msdn.microsoft.com/library/02454a0f-30ca-4e77-ad84-ee7837461804)|[<span data-ttu-id="94bfb-122">？ < =？</span><span class="sxs-lookup"><span data-stu-id="94bfb-122">?<=?</span></span>](https://msdn.microsoft.com/library/5c37c28c-0b57-4da5-be11-5a123f7e8ee4)|
|[<span data-ttu-id="94bfb-123">？ <</span><span class="sxs-lookup"><span data-stu-id="94bfb-123">?<</span></span>](https://msdn.microsoft.com/library/b71897f0-6e29-4c58-b0a7-a5bfa6f88917)|[<span data-ttu-id="94bfb-124">< 嗎？</span><span class="sxs-lookup"><span data-stu-id="94bfb-124"><?</span></span>](https://msdn.microsoft.com/library/be9ea40f-a67f-4e98-8067-a14046752e8b)|[<span data-ttu-id="94bfb-125">？ <？</span><span class="sxs-lookup"><span data-stu-id="94bfb-125">?<?</span></span>](https://msdn.microsoft.com/library/6f1962c8-5605-468c-94ae-f379ae98e17d)|
|[<span data-ttu-id="94bfb-126">?=</span><span class="sxs-lookup"><span data-stu-id="94bfb-126">?=</span></span>](https://msdn.microsoft.com/library/5cdc8ff6-244b-49cf-9376-69ecf249fd7c)|[<span data-ttu-id="94bfb-127">=?</span><span class="sxs-lookup"><span data-stu-id="94bfb-127">=?</span></span>](https://msdn.microsoft.com/library/d2102894-6a51-475d-890a-735568c31f87)|[<span data-ttu-id="94bfb-128">?=?</span><span class="sxs-lookup"><span data-stu-id="94bfb-128">?=?</span></span>](https://msdn.microsoft.com/library/5f793f29-1084-4570-b1c1-17c1b7ef764b)|
|[<span data-ttu-id="94bfb-129">？ < ></span><span class="sxs-lookup"><span data-stu-id="94bfb-129">?<></span></span>](https://msdn.microsoft.com/library/3643a5a8-2ea5-4ad6-82c4-83927c3884a0)|[<span data-ttu-id="94bfb-130">< > 嗎？</span><span class="sxs-lookup"><span data-stu-id="94bfb-130"><>?</span></span>](https://msdn.microsoft.com/library/3179aace-70c4-4911-9258-619592214976)|[<span data-ttu-id="94bfb-131">< > 嗎？</span><span class="sxs-lookup"><span data-stu-id="94bfb-131">?<>?</span></span>](https://msdn.microsoft.com/library/5da813d8-ee75-45b8-9ef4-146dcb6d394d)|
|[<span data-ttu-id="94bfb-132">?+</span><span class="sxs-lookup"><span data-stu-id="94bfb-132">?+</span></span>](https://msdn.microsoft.com/library/2e8ddd05-b3f3-41b3-9d73-938d9e540f3f)|[<span data-ttu-id="94bfb-133">+?</span><span class="sxs-lookup"><span data-stu-id="94bfb-133">+?</span></span>](https://msdn.microsoft.com/library/74772ea8-f010-493e-bdb5-ba347f2fd4f1)|[<span data-ttu-id="94bfb-134">?+?</span><span class="sxs-lookup"><span data-stu-id="94bfb-134">?+?</span></span>](https://msdn.microsoft.com/library/57f28137-0f42-43d2-92af-cad8c6c9d05f)|
|[<span data-ttu-id="94bfb-135">?-</span><span class="sxs-lookup"><span data-stu-id="94bfb-135">?-</span></span>](https://msdn.microsoft.com/library/f237a7a6-89f2-48b2-a2fe-f0b98a2bedc2)|[<span data-ttu-id="94bfb-136">-?</span><span class="sxs-lookup"><span data-stu-id="94bfb-136">-?</span></span>](https://msdn.microsoft.com/library/4a345c07-314a-48f1-b557-ce072583589c)|[<span data-ttu-id="94bfb-137">?-?</span><span class="sxs-lookup"><span data-stu-id="94bfb-137">?-?</span></span>](https://msdn.microsoft.com/library/e0024142-1d2a-4607-a39c-1eb1e86fa25a)|
|[<span data-ttu-id="94bfb-138">?\*</span><span class="sxs-lookup"><span data-stu-id="94bfb-138">?\*</span></span>](https://msdn.microsoft.com/library/519da708-5ad6-4075-9d74-d00441cd6078)|[<span data-ttu-id="94bfb-139">\*?</span><span class="sxs-lookup"><span data-stu-id="94bfb-139">\*?</span></span>](https://msdn.microsoft.com/library/04c47870-de7b-480d-98a0-f47593b4ffac)|[<span data-ttu-id="94bfb-140">?\*?</span><span class="sxs-lookup"><span data-stu-id="94bfb-140">?\*?</span></span>](https://msdn.microsoft.com/library/e57057ba-9c3a-40ec-8401-150c2b25f75b)|
|[<span data-ttu-id="94bfb-141">?/</span><span class="sxs-lookup"><span data-stu-id="94bfb-141">?/</span></span>](https://msdn.microsoft.com/library/add02a42-f556-40a7-a168-fbf2053322e3)|[<span data-ttu-id="94bfb-142">/?</span><span class="sxs-lookup"><span data-stu-id="94bfb-142">/?</span></span>](https://msdn.microsoft.com/library/1de07646-3778-476d-8c61-5d37495d463c)|[<span data-ttu-id="94bfb-143">?/?</span><span class="sxs-lookup"><span data-stu-id="94bfb-143">?/?</span></span>](https://msdn.microsoft.com/library/b17be0ac-bf98-4590-861d-a4dd6c6fa535)|
|[<span data-ttu-id="94bfb-144">?%</span><span class="sxs-lookup"><span data-stu-id="94bfb-144">?%</span></span>](https://msdn.microsoft.com/library/44297bba-1bd9-4ed2-a848-f1e1e598db87)|[<span data-ttu-id="94bfb-145">%?</span><span class="sxs-lookup"><span data-stu-id="94bfb-145">%?</span></span>](https://msdn.microsoft.com/library/a4c178e5-eec4-42e8-847f-90b24fc609fe)|[<span data-ttu-id="94bfb-146">?%?</span><span class="sxs-lookup"><span data-stu-id="94bfb-146">?%?</span></span>](https://msdn.microsoft.com/library/dd555f20-1be3-4b8d-81f1-bf1921e62fda)|

## <a name="remarks"></a><span data-ttu-id="94bfb-147">備註</span><span class="sxs-lookup"><span data-stu-id="94bfb-147">Remarks</span></span>

<span data-ttu-id="94bfb-148">可為 null 的運算子包含在[fsharp.core](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)命名空間的[NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007)模組中。</span><span class="sxs-lookup"><span data-stu-id="94bfb-148">The nullable operators are included in the [NullableOperators](https://msdn.microsoft.com/library/2c3633c5-3f31-4d62-a9f8-272ad6b19007) module in the namespace [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d).</span></span> <span data-ttu-id="94bfb-149">可為 null 的資料類型為 `System.Nullable<'T>`。</span><span class="sxs-lookup"><span data-stu-id="94bfb-149">The type for nullable data is `System.Nullable<'T>`.</span></span>

<span data-ttu-id="94bfb-150">在查詢運算式中，從允許 null 而非值的資料來源選取資料時，就會發生可為 null 的類型。</span><span class="sxs-lookup"><span data-stu-id="94bfb-150">In query expressions, nullable types arise when selecting data from a data source that allows nulls instead of values.</span></span> <span data-ttu-id="94bfb-151">在 SQL Server 資料庫中，資料表中的每個資料行都有一個屬性，指出是否允許 null。</span><span class="sxs-lookup"><span data-stu-id="94bfb-151">In a SQL Server database, each data column in a table has an attribute that indicates whether nulls are allowed.</span></span> <span data-ttu-id="94bfb-152">如果允許 null，從資料庫傳回的資料可以包含 null，而這些資料類型無法以基本型別（例如 `int`、`float`等等）來表示。</span><span class="sxs-lookup"><span data-stu-id="94bfb-152">If nulls are allowed, the data returned from the database can contain nulls that cannot be represented by a primitive data type such as `int`, `float`, and so on.</span></span> <span data-ttu-id="94bfb-153">因此，資料會以 `System.Nullable<int>` 傳回，而不是 `int`，而是 `System.Nullable<float>`，而不是 `float`。</span><span class="sxs-lookup"><span data-stu-id="94bfb-153">Therefore, the data is returned as a `System.Nullable<int>` instead of `int`, and `System.Nullable<float>` instead of `float`.</span></span> <span data-ttu-id="94bfb-154">您可以使用 `Value` 屬性從 `System.Nullable<'T>` 物件取得實際的值，而且您可以藉由呼叫 `HasValue` 方法，判斷 `System.Nullable<'T>` 物件是否有值。</span><span class="sxs-lookup"><span data-stu-id="94bfb-154">The actual value can be obtained from a `System.Nullable<'T>` object by using the `Value` property, and you can determine if a `System.Nullable<'T>` object has a value by calling the `HasValue` method.</span></span> <span data-ttu-id="94bfb-155">另一個有用的方法是 `System.Nullable<'T>.GetValueOrDefault` 方法，可讓您取得適當類型的值或預設值。</span><span class="sxs-lookup"><span data-stu-id="94bfb-155">Another useful method is the `System.Nullable<'T>.GetValueOrDefault` method, which allows you to get the value or a default value of the appropriate type.</span></span> <span data-ttu-id="94bfb-156">預設值為「零」值的某種形式，例如0、0.0 或 `false`。</span><span class="sxs-lookup"><span data-stu-id="94bfb-156">The default value is some form of "zero" value, such as 0, 0.0, or `false`.</span></span>

<span data-ttu-id="94bfb-157">您可以使用一般轉換運算子（例如 `int` 或 `float`），將可為 null 的類型轉換成不可為 null 的基本類型。</span><span class="sxs-lookup"><span data-stu-id="94bfb-157">Nullable types may be converted to non-nullable primitive types using the usual conversion operators such as `int` or `float`.</span></span> <span data-ttu-id="94bfb-158">您也可以使用可為 null 類型的轉換運算子，從可為 null 的型別轉換成另一個可為 null 的型別。</span><span class="sxs-lookup"><span data-stu-id="94bfb-158">It is also possible to convert from one nullable type to another nullable type by using the conversion operators for nullable types.</span></span> <span data-ttu-id="94bfb-159">適當的轉換運算子具有與標準的相同名稱，但它們位於不同的模組中，也就是[fsharp.core](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d)中的[可為 null](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e)的模組。</span><span class="sxs-lookup"><span data-stu-id="94bfb-159">The appropriate conversion operators have the same name as the standard ones, but they are in a separate module, the [Nullable](https://msdn.microsoft.com/library/e7a4ea13-28cc-462e-bc3a-33131ace976e) module in the [Microsoft.FSharp.Linq](https://msdn.microsoft.com/library/4765b4e8-4006-4d8c-a405-39c218b3c82d) namespace.</span></span> <span data-ttu-id="94bfb-160">一般而言，當您使用查詢運算式時，會開啟此命名空間。</span><span class="sxs-lookup"><span data-stu-id="94bfb-160">Typically, you open this namespace when working with query expressions.</span></span> <span data-ttu-id="94bfb-161">在這種情況下，您可以使用可為 null 的轉換運算子，方法是將前置詞 `Nullable.` 新增至適當的轉換運算子，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="94bfb-161">In that case, you can use the nullable conversion operators by adding the prefix `Nullable.` to the appropriate conversion operator, as shown in the following code.</span></span>

```fsharp
open Microsoft.FSharp.Linq

let nullableInt = new System.Nullable<int>(10)

// Use the Nullable.float conversion operator to convert from one nullable type to another nullable type.
let nullableFloat = Nullable.float nullableInt

// Use the regular non-nullable float operator to convert to a non-nullable float.
printfn "%f" (float nullableFloat)
```

<span data-ttu-id="94bfb-162">輸出為 `10.000000`。</span><span class="sxs-lookup"><span data-stu-id="94bfb-162">The output is `10.000000`.</span></span>

<span data-ttu-id="94bfb-163">可為 null 的資料欄位（例如 `sumByNullable`）上的查詢運算子也存在，以便用於查詢運算式中。</span><span class="sxs-lookup"><span data-stu-id="94bfb-163">Query operators on nullable data fields, such as `sumByNullable`, also exist for use in query expressions.</span></span> <span data-ttu-id="94bfb-164">不可為 null 類型的查詢運算子與可為 null 的類型不相容，因此當您使用可為 null 的資料值時，您必須使用適當查詢運算子的可為 null 版本。</span><span class="sxs-lookup"><span data-stu-id="94bfb-164">The query operators for non-nullable types are not type-compatible with nullable types, so you must use the nullable version of the appropriate query operator when you are working with nullable data values.</span></span> <span data-ttu-id="94bfb-165">如需詳細資訊，請參閱[查詢運算式](../query-expressions.md)。</span><span class="sxs-lookup"><span data-stu-id="94bfb-165">For more information, see [Query Expressions](../query-expressions.md).</span></span>

<span data-ttu-id="94bfb-166">下列範例示範如何在F#查詢運算式中使用可為 null 的運算子。</span><span class="sxs-lookup"><span data-stu-id="94bfb-166">The following example shows the use of nullable operators in an F# query expression.</span></span> <span data-ttu-id="94bfb-167">第一個查詢顯示如何撰寫不含可為 null 運算子的查詢;第二個查詢會顯示使用可為 null 運算子的對等查詢。</span><span class="sxs-lookup"><span data-stu-id="94bfb-167">The first query shows how you would write a query without a nullable operator; the second query shows an equivalent query that uses a nullable operator.</span></span> <span data-ttu-id="94bfb-168">如需完整內容，包括如何設定資料庫以使用此範例程式碼，請參閱[逐步解說：使用型別提供者存取 SQL Database](../../tutorials/type-providers/index.md)。</span><span class="sxs-lookup"><span data-stu-id="94bfb-168">For the full context, including how to set up the database to use this sample code, see [Walkthrough: Accessing a SQL Database by Using Type Providers](../../tutorials/type-providers/index.md).</span></span>

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

## <a name="see-also"></a><span data-ttu-id="94bfb-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="94bfb-169">See also</span></span>

- [<span data-ttu-id="94bfb-170">類型提供者</span><span class="sxs-lookup"><span data-stu-id="94bfb-170">Type Providers</span></span>](../../tutorials/type-providers/index.md)
- [<span data-ttu-id="94bfb-171">查詢運算式</span><span class="sxs-lookup"><span data-stu-id="94bfb-171">Query Expressions</span></span>](../query-expressions.md)
