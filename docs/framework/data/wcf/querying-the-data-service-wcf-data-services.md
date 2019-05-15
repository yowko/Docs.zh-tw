---
title: 查詢資料服務 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: c2eb6d8f8bb7886e4615438e463aeea3c3825662
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/14/2019
ms.locfileid: "65582637"
---
# <a name="querying-the-data-service-wcf-data-services"></a>查詢資料服務 (WCF 資料服務)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫可讓您使用熟悉的 .NET Framework 程式設計模式針對資料服務執行查詢，包括使用 Language Integrated Query (LINQ)。 用戶端程式庫會將查詢轉譯為 HTTP GET 要求訊息，該查詢在用戶端上已定義為 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別的執行個體。 程式庫會接收回應訊息，並將它轉譯成用戶端資料服務類別的執行個體。 這些類別會由 <xref:System.Data.Services.Client.DataServiceContext> 所屬的 <xref:System.Data.Services.Client.DataServiceQuery%601> 追蹤。

## <a name="data-service-queries"></a>資料服務查詢

<xref:System.Data.Services.Client.DataServiceQuery%601> 泛型類別表示傳回零個或多個實體型別執行個體之集合的查詢。 資料服務查詢永遠屬於現有的資料服務內容。 此內容會維持撰寫及執行查詢所需的服務 URI 和中繼資料 (Metadata) 資訊。

當您使用**加入服務參考**對話方塊，即可將資料服務加入至.NET Framework 為基礎的用戶端應用程式的實體容器類別建立繼承自<xref:System.Data.Services.Client.DataServiceContext>類別。 這個類別包含會傳回具型別之 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體的屬性。 每一個實體集都有一個屬性，並由資料服務公開。 這些屬性可以讓具型別 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體的建立作業更為容易。

以下情況下會執行查詢：

- 結果以隱含方式列舉時，例如：

  - 列舉代表 <xref:System.Data.Services.Client.DataServiceContext> 上的屬性及實體集時，例如 `foreach` (C#) 或 `For Each` (Visual Basic) 迴圈期間。

  - 查詢已指派至 `List` 集合時。

- 明確呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> 或 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 方法時。

- 當呼叫 LINQ 查詢執行運算子 (如 <xref:System.Linq.Enumerable.First%2A> 或 <xref:System.Linq.Enumerable.Single%2A>) 時。

下列查詢在執行時會傳回 Northwind 資料服務中的所有 `Customers` 實體：

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

如需詳細資訊，請參閱[如何：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)。

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端支援晚期繫結物件，例如當您使用查詢*動態*輸入C#。 不過，基於效能因素，您應該一律針對資料服務撰寫強型別的查詢。 用戶端不支援 <xref:System.Tuple> 型別和動態物件。

## <a name="linq-queries"></a>LINQ 查詢

因為<xref:System.Data.Services.Client.DataServiceQuery%601>類別會實作<xref:System.Linq.IQueryable%601>由 LINQ 定義的介面[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫是能夠將針對實體集資料的 LINQ 查詢轉換成表示查詢運算式，評估針對資料服務的 URI資源。 下列範例是 LINQ 查詢，其相當於以前的 <xref:System.Data.Services.Client.DataServiceQuery%601>，它會傳回運費成本超過 $30 的 `Orders`，並依運費成本排序結果：

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

此 LINQ 查詢轉譯為下列查詢會針對以 Northwind 為基礎執行的 URI[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)資料服務：

```
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> 可以用 LINQ 語法表示的查詢集合會比在資料服務所使用之具像狀態傳輸 (REST) 架構 URI 語法中啟用的查詢集合更廣泛。 當查詢無法對應至目標資料服務中的 URI 時，就會引發 <xref:System.NotSupportedException>。

如需詳細資訊，請參閱 < [LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)。

## <a name="adding-query-options"></a>加入查詢選項

資料服務查詢支援 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供的所有查詢選項。 您可以呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法，將查詢選項附加至 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體。 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 會傳回新的 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體，其相當於原始的查詢，但使用新的查詢選項集。 下列查詢在執行時會傳回 `Orders`，其係經由 `Freight` 值進行篩選並依 `OrderID` 遞減順序排序：

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

您可以使用 `$orderby` 查詢選項根據單一屬性來排序及篩選查詢，如下列範例根據 `Orders` 屬性的值篩選及排序傳回的 `Freight` 物件：

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

您可以連續呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法來建構複雜的查詢運算式。 如需詳細資訊，請參閱[如何：將查詢選項加入至資料服務查詢](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)。

查詢選項提供您另一種表示 LINQ 查詢語法元件的方式。 如需詳細資訊，請參閱 < [LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)。

> [!NOTE]
>  您無法使用 `$select` 方法，將 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 查詢選項加入至查詢 URI。 建議您使用 LINQ <xref:System.Linq.Enumerable.Select%2A> 方法，讓用戶端在要求 URI 中產生 `$select` 查詢選項。

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>用戶端與伺服器執行的比較

用戶端會以兩個部分執行查詢。 如果可能，查詢中的運算式會先在用戶端上進行評估，然後產生 URI 架構的查詢，並將其傳送至資料服務，以便針對服務中的資料進行評估。 請考慮下列 LINQ 查詢：

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

在此範例中，運算式 `(basePrice – (basePrice * discount))` 會在用戶端上進行評估。 因此，傳送至資料服務的實際查詢 URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` 在 filter 子句中，包含已經計算的十進位值 `90`。 篩選運算式的另一個部分 (包括子字串運算式)，則由資料服務評估。 在用戶端上評估的運算式會遵循 Common Language Runtime (CLR) 語意，而傳送到資料服務的運算式則會依賴 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定的資料服務實作。 您也應該知道這個個別評估的案例可能會造成非預期的結果，例如，當用戶端和服務同時在不同的時區中執行以時間為基礎的評估時。

## <a name="query-responses"></a>查詢回應

執行時，<xref:System.Data.Services.Client.DataServiceQuery%601> 會傳回要求之實體類型的 <xref:System.Collections.Generic.IEnumerable%601>。 此查詢結果可以轉型為 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件，如下列範例：

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

資料服務中代表實體的實體類型執行個體是透過稱為物件具體化的程序，在用戶端上建立的。 如需詳細資訊，請參閱 <<c0> [ 物件具體化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)。 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件會實作 <xref:System.Collections.Generic.IEnumerable%601> 以提供查詢結果的存取權。

<xref:System.Data.Services.Client.QueryOperationResponse%601> 還有下列成員，可讓您存取有關查詢結果的其他資訊：

- <xref:System.Data.Services.Client.OperationResponse.Error%2A> - 取得作業擲回的錯誤 (若有發生錯誤的話)。

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A> - 包含與查詢回應相關聯之 HTTP 回應標頭的集合。

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> - 取得產生 <xref:System.Data.Services.Client.DataServiceQuery%601> 的原始 <xref:System.Data.Services.Client.QueryOperationResponse%601>。

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> - 取得查詢回應的 HTTP 回應碼。

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> - 在 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法時，取得實體集中的實體總數。

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> - 傳回包含下一頁結果之 URI 的 <xref:System.Data.Services.Client.DataServiceQueryContinuation> 物件。

根據預設，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]只會傳回查詢 URI 所明確選取的資料。 它還提供選項可讓您於必要時，從資料服務明確載入其他資料。 每次您從資料服務明確載入資料時，就會傳送一個要求至資料服務。 可以明確載入的資料包括相關實體、分頁的回應資料，以及二進位資料流。

> [!NOTE]
> 因為資料服務可能傳回分頁的回應，我們建議您的應用程式使用程式設計模式來處理分頁的資料服務回應。 如需詳細資訊，請參閱 <<c0> [ 載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。

指定回應中僅傳回特定實體屬性，也可以降低查詢傳回的資料量。 如需詳細資訊，請參閱 <<c0> [ 查詢投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)。

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>取得集合中實體總數的計數

在部分情況下，這麼做有助於得知實體集中的實體總數，且不僅是查詢傳回的數目。 在 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法，以要求集合中的這項實體總計數包含在查詢結果中。 在此案例中，傳回之 <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> 的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 屬性會傳回集合中的實體總數。

您也可以分別呼叫 <xref:System.Int32> 或 <xref:System.Int64> 方法，藉此只取得集合中的實體總計數，以做為 <xref:System.Linq.Enumerable.Count%2A> 或做為 <xref:System.Linq.Enumerable.LongCount%2A> 值。 呼叫這些方法時，並未傳回 <xref:System.Data.Services.Client.QueryOperationResponse%601>；只會傳回計數值。 如需詳細資訊，請參閱[如何：判斷查詢所傳回的實體數目](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)。

## <a name="in-this-section"></a>本節內容

- [查詢投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

- [物件具體化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)

- [LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [如何：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [如何：將查詢選項加入至資料服務查詢](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [如何：判斷查詢所傳回的實體數目](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)

- [如何：指定資料服務的用戶端認證要求](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)

- [如何：設定用戶端要求中的標頭](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [如何：專案查詢結果](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
