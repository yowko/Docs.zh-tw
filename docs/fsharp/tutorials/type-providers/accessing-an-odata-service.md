---
title: 逐步解說：使用型別提供者存取 OData 服務 (F#)
description: '了解如何使用 F # 3.0 的 F # ODataService 類型提供者來產生 OData 服務的用戶端類型，並提供資料摘要之服務的查詢。'
keywords: Visual F#, F#, 函式程式設計
author: cartermp
ms.author: phcart
ms.date: 05/16/2016
ms.topic: language-reference
ms.prod: .net
ms.technology: devlang-fsharp
ms.devlang: fsharp
ms.assetid: 0adae84c-b0fa-455f-994b-274ecdc6df30
ms.openlocfilehash: 750407c36a989cece30c0c0654ff905c8eee3b33
ms.sourcegitcommit: b750a8e3979749b214e7e10c82efb0a0524dfcb1
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/10/2018
---
# <a name="walkthrough-accessing-an-odata-service-by-using-type-providers"></a>逐步解說：使用型別提供者存取 OData 服務

> [!NOTE]
本指南針對 F # 3.0 所撰寫，而且會更新。  請參閱 [FSharp.Data](https://fsharp.github.io/FSharp.Data/) 以取得最新的跨平台型別提供者。

> [!NOTE]
應用程式開發介面參考連結將帶您到 MSDN。  docs.microsoft.com API 參考不完整。

OData，這表示開放式資料通訊協定，是透過網際網路傳輸資料的通訊協定。 許多資料提供者所發行的 OData web 服務公開其資料的存取權。 您可以從 F # 3.0 中使用的資料類型自動產生的任何 OData 來源存取資料`ODataService`型別提供者。 如需 OData 的詳細資訊，請參閱https://msdn.microsoft.com/library/da3380cc-f6da-4c6c-bdb2-bb86afa59d62。

本逐步解說會示範如何使用 F # ODataService 類型提供者來產生 OData 服務的用戶端類型，並提供資料摘要之服務的查詢。

這個逐步解說將說明下列工作，您應該按照這個逐步解說的順序執行才能成功：


- 設定 OData 服務的用戶端專案
<br />

- 存取 OData 型別
<br />

- 查詢 OData 服務
<br />

- 驗證 OData 要求
<br />


## <a name="configuring-a-client-project-for-an-odata-service"></a>設定 OData 服務的用戶端專案
在此步驟中，您將設定專案使用 OData 型別提供者。


#### <a name="to-configure-a-client-project-for-an-odata-service"></a>若要設定的 OData 服務的用戶端專案

- 開啟 F # 主控台應用程式專案，然後再將參考加入`System.Data.Services.Client`Framework 組件。
<br />

- 在下`Extensions`，將參考加入`FSharp.Data.TypeProviders`組件。
<br />

## <a name="accessing-odata-types"></a>存取 OData 型別
在此步驟中，您可以建立提供 OData 服務的存取權的類型和資料型別提供者。


#### <a name="to-access-odata-types"></a>若要存取 OData 類型

- 在程式碼編輯器中，開啟 F # 原始程式檔，並輸入下列程式碼。
<br />

```fsharp
open Microsoft.FSharp.Data.TypeProviders


type Northwind = ODataService<"https://services.odata.org/Northwind/Northwind.svc/">

let db = Northwind.GetDataContext()
let fullContext = Northwind.ServiceTypes.NorthwindEntities()
```

在此範例中，您已叫用 F # 類型提供者，而且所指示的位置，以便建立一組會根據您指定的 OData URI 的類型。 兩個物件都包含資料; 的相關資訊其中一個是簡化的資料內容，`db`在範例中。 此物件只包含資料類型相關聯的資料庫，包括對於資料表或摘要的型別。 另一個物件，`fullContext`在此範例中，是的執行個體`System.Data.Linq.DataContext`且包含許多其他屬性、 方法和事件。
<br />


## <a name="querying-an-odata-service"></a>查詢 OData 服務
在此步驟中，您可以使用 F # 查詢運算式來查詢 OData 服務。


#### <a name="to-query-an-odata-service"></a>若要查詢的 OData 服務

1. 既然您已經設定類型提供者，您可以查詢 OData 服務。
<br />  OData 支援只有一個可用的查詢作業的子集。 支援下列作業和其相對應的關鍵字：
<br />
  - 投影 (`select`)
<br />

  - 篩選 (`where`、 藉由使用字串和日期的作業)
<br />

  - 分頁 (`skip`， `take`)
<br />

  - 排序 (`orderBy`， `thenBy`)
<br />

  - `AddQueryOption` 和`Expand`，這是 OData 特定作業
<br />

  如需詳細資訊，請參閱[LINQ 考量&#40;WCF Data Services&#41;](https://msdn.microsoft.com/library/ee622463.aspx)。
<br />  如果您想要將所有摘要或資料表中的項目，使用簡單的形式的查詢運算式，如下列程式碼所示：
<br />

```fsharp
query {
  for customer in db.Customers do
  select customer
} |> Seq.iter (fun customer ->
                  printfn "ID: %s\nCompany: %s" customer.CustomerID customer.CompanyName
                  printfn "Contact: %s\nAddress: %s" customer.ContactName customer.Address
                  printfn "         %s, %s %s" customer.City customer.Region customer.PostalCode
                  printfn "%s\n" customer.Phone)
```

2. 指定欄位或資料行，您想要使用的 select 關鍵字後的 tuple。
<br />

```fsharp
  query { 
    for cat in db.Categories do
    select (cat.CategoryID, cat.CategoryName, cat.Description)
  } |> Seq.iter (fun (id, name, description) ->
                    printfn "ID: %d\nCategory: %s\nDescription: %s\n" id name description)
```

3. 使用指定的條件`where`子句。
<br />

```fsharp
query {
  for employee in db.Employees do
  where (employee.EmployeeID = 9)
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

4. 使用指定的子字串條件查詢`System.String.Contains(System.String)`方法。 下列查詢會傳回名稱中有"Chef"的所有產品。 也請注意，使用`System.Nullable<'T>.GetValueOrDefault()`。 `UnitPrice`是可為 null 的值，因此您必須使用來取得值`Value`屬性，或您必須呼叫`System.Nullable<'T>.GetValueOrDefault()`。
<br />

```fsharp
query { 
  for product in db.Products do
  where (product.ProductName.Contains("Chef"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

5. 使用`System.String.EndsWith(System.String)`方法，以指定的字串是以特定子結束。
<br />

```fsharp
query {
  for product in db.Products do
  where (product.ProductName.EndsWith("u"))
  select product
} |> Seq.iter (fun product ->
                  printfn "ID: %d Product: %s" product.ProductID product.ProductName
                  printfn "Price: %M\n" (product.UnitPrice.GetValueOrDefault()))
```

6. 結合條件，在 where 子句使用`&&`運算子。
<br />

```fsharp
// Open this module to use the nullable operators ?> and ?<.
open Microsoft.FSharp.Linq.NullableOperators

let salesIn1997 = query { 
  for sales in db.Category_Sales_for_1997 do
  where (sales.CategorySales ?> 50000.00M && sales.CategorySales ?< 60000.0M)
  select sales }

salesIn1997
|> Seq.iter (fun sales ->
                printfn "Category: %s Sales: %M" sales.CategoryName (sales.CategorySales.GetValueOrDefault()))
```

運算子`?>`和`?<`都是可為 null 的運算子。 您可以使用一組完整的可為 null 的等式和比較運算子。 如需詳細資訊，請參閱[Linq.NullableOperators 模組](https://msdn.microsoft.com/visualfsharpdocs/conceptual/linq.nullableoperators-module-%5bfsharp%5d)。
<br />

7. 使用`sortBy`查詢運算子以指定順序，並且使用`thenBy`指定的順序的另一個層級。 另請注意使用查詢的 select 部分中的 tuple。 因此，查詢具有 tuple 做為項目類型。
<br />

```fsharp
printfn "Freight for some orders: "

query { 
  for order in db.Orders do
  sortBy (order.OrderDate.Value)
  thenBy (order.OrderID)
  select (order.OrderDate, order.OrderID, order.Customer.CompanyName)
} |> Seq.iter (fun (orderDate, orderID, company) ->
                  printfn "OrderDate: %s" (orderDate.GetValueOrDefault().ToString())
                  printfn "OrderID: %d Company: %s\n" orderID company)
```

8. 忽略指定的記錄數目使用 skip 運算子，並使用 take 運算子來指定要傳回的記錄數目。 如此一來，您可以在資料摘要上實作分頁。
<br />

```fsharp
printfn "Get the first page of 2 employees."

query { 
  for employee in db.Employees do
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID)) 

printfn "Get the next 2 employees."

query { 
  for employee in db.Employees do
  skip 2
  take 2
  select employee
} |> Seq.iter (fun employee ->
                  printfn "Name: %s ID: %d" (employee.FirstName + " " + employee.LastName) (employee.EmployeeID))
```

## <a name="verifying-the-odata-request"></a>驗證 OData 要求
每一個 OData 查詢會轉譯成特定的 OData 要求 URI。 您可以確認，URI，可能是用於偵錯用途，加入事件處理常式到`SendingRequest`完整的資料物件上的事件。


#### <a name="to-verify-the-odata-request"></a>若要驗證 OData 要求

- 若要驗證 OData 要求 URI，請使用下列程式碼：
<br />

```fsharp
// The DataContext property returns the full data context.
db.DataContext.SendingRequest.Add (fun eventArgs -> printfn "Requesting %A" eventArgs.Request.RequestUri)
```

先前的程式碼的輸出為：
<br />`requesting https://services.odata.org/Northwind/Northwind.svc/Orders()?$orderby=ShippedDate&amp;$select=OrderID,ShippedDate`


## <a name="see-also"></a>另請參閱
[查詢運算式](../../language-reference/query-expressions.md)

[LINQ 考量 (WCF Data Services)](https://msdn.microsoft.com/library/ee622463.aspx)

[ODataService 類型提供者 （F #）](https://msdn.microsoft.com/visualfsharpdocs/conceptual/odataservice-type-provider-%5bfsharp%5d)
