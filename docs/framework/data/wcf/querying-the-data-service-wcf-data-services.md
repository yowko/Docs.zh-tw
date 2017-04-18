---
title: "查詢資料服務 (WCF Data Services) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-oob"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "WCF Data Services, 存取資料"
  - "WCF Data Services, 用戶端程式庫"
  - "WCF Data Services, 查詢"
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 查詢資料服務 (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫可讓您使用熟悉的 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 程式設計模式針對資料服務執行查詢，包括使用 Language Integrated Query \(LINQ\)。  用戶端程式庫會將查詢轉譯為 HTTP GET 要求訊息，該查詢在用戶端上已定義為 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別的執行個體。  程式庫會接收回應訊息，並將它轉譯為用戶端資料服務類別的執行個體。  這些類別會由 <xref:System.Data.Services.Client.DataServiceQuery%601> 所屬的 <xref:System.Data.Services.Client.DataServiceContext> 追蹤。  
  
## 資料服務查詢  
 <xref:System.Data.Services.Client.DataServiceQuery%601> 泛型類別表示傳回零個或多個實體型別執行個體之集合的查詢。  資料服務查詢永遠屬於現有的資料服務內容。  此內容會維持撰寫及執行查詢所需的服務 URI 和中繼資料 \(Metadata\) 資訊。  
  
 當您使用 \[**加入服務參考**\] 對話方塊將資料服務加入 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 架構的用戶端應用程式時，會建立繼承自 <xref:System.Data.Services.Client.DataServiceContext> 類別的實體容器類別。  這個類別包含會傳回具型別之 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體的屬性。  每一個實體集都有一個屬性，並由資料服務公開。  這些屬性可以讓具型別 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體的建立作業更為容易。  
  
 以下情況下會執行查詢：  
  
-   結果以隱含方式列舉時，例如：  
  
    -   列舉代表 <xref:System.Data.Services.Client.DataServiceContext> 上的屬性及實體集時，例如 `foreach` \(C\#\) 或 `For Each` \([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]\) 迴圈期間。  
  
    -   查詢已指派至 `List` 集合時。  
  
-   明確呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> 或 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 方法時。  
  
-   當呼叫 LINQ 查詢執行運算子 \(如 <xref:System.Linq.Enumerable.First%2A> 或 <xref:System.Linq.Enumerable.Single%2A>\) 時。  
  
 下列查詢在執行時會傳回 Northwind 資料服務中的所有 `Customers` 實體：  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 如需詳細資訊，請參閱[HOW TO：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)。  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端支援晚期繫結物件的查詢，例如，當您在 C\# 中使用「*動態*」\(Dynamic\) 型別時。  不過，基於效能因素，您應該一律針對資料服務撰寫強型別的查詢。  用戶端不支援 <xref:System.Tuple> 型別和動態物件。  
  
## LINQ 查詢  
 因為 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別會實作由 LINQ 定義之 <xref:System.Linq.IQueryable%601> 介面，因此 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫可以根據實體集資料將 LINQ 查詢轉換為 URI \(其代表針對資料服務資源評估之查詢運算式\)。  下列範例是 LINQ 查詢，其相當於以前的 <xref:System.Data.Services.Client.DataServiceQuery%601>，它會傳回運費成本超過 $30 的 `Orders`，並依運費成本排序結果：  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 此 LINQ 查詢會轉譯為下列查詢 URI，其會針對 Northwind 架構的[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)資料服務執行：  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  可以用 LINQ 語法表示的查詢集合會比在資料服務所使用之具像狀態傳輸 \(REST\) 架構 URI 語法中啟用的查詢集合更廣泛。  當查詢無法對應至目標資料服務中的 URI 時，就會引發 <xref:System.NotSupportedException>。  
  
 如需詳細資訊，請參閱[LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)。  
  
## 加入查詢選項  
 資料服務查詢支援 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供的所有查詢選項。  您可以呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法，將查詢選項附加至 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體。  <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 會傳回新的 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體，其相當於原始的查詢，但使用新的查詢選項集。  下列查詢在執行時會傳回 `Orders`，其係經由 `Freight` 值進行篩選並依 `OrderID` 遞減順序排序：  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 您可以使用 `$orderby` 查詢選項根據單一屬性來排序及篩選查詢，如下列範例根據 `Freight` 屬性的值篩選及排序傳回的 `Orders` 物件：  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 您可以連續呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法來建構複雜的查詢運算式。  如需詳細資訊，請參閱[HOW TO：將查詢選項加入至資料服務查詢](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)。  
  
 查詢選項提供您另一種表示 LINQ 查詢語法元件的方式。  如需詳細資訊，請參閱[LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)。  
  
> [!NOTE]
>  您無法使用 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法，將 `$select` 查詢選項加入至查詢 URI。  建議您使用 LINQ <xref:System.Linq.Enumerable.Select%2A> 方法，讓用戶端在要求 URI 中產生 `$select` 查詢選項。  
  
<a name="executingQueries"></a>   
## 用戶端與伺服器執行的比較  
 用戶端會以兩個部分執行查詢。  如果可能，查詢中的運算式會先在用戶端上進行評估，然後產生 URI 架構的查詢，並將其傳送至資料服務，以便針對服務中的資料進行評估。  請考慮下列 LINQ 查詢：  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 在此範例中，運算式 `(basePrice – (basePrice * discount))` 會在用戶端上進行評估。  因此，傳送至資料服務的實際查詢 URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` 在 filter 子句中，包含已經計算的十進位值 `90`。  篩選運算式的另一個部分 \(包括子字串運算式\)，則由資料服務評估。  在用戶端上評估的運算式會遵循 Common Language Runtime \(CLR\) 語意，而傳送到資料服務的運算式則會依賴 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定的資料服務實作。  您也應該知道這個個別評估的案例可能會造成非預期的結果，例如，當用戶端和服務同時在不同的時區中執行以時間為基礎的評估時。  
  
## 查詢回應  
 執行時，<xref:System.Data.Services.Client.DataServiceQuery%601> 會傳回要求之實體類型的 <xref:System.Collections.Generic.IEnumerable%601>。  此查詢結果可以轉型為 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件，如下列範例：  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 資料服務中代表實體的實體類型執行個體是透過稱為物件具體化的程序，在用戶端上建立的。  如需詳細資訊，請參閱[物件 Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)。  <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件會實作 <xref:System.Collections.Generic.IEnumerable%601> 以提供查詢結果的存取權。  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> 還有下列成員，可讓您存取有關查詢結果的其他資訊：  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> \- 取得作業擲回的錯誤 \(若有發生錯誤的話\)。  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> \- 包含與查詢回應相關聯之 HTTP 回應標頭的集合。  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> \- 取得產生 <xref:System.Data.Services.Client.QueryOperationResponse%601> 的原始 <xref:System.Data.Services.Client.DataServiceQuery%601>。  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> \- 取得查詢回應的 HTTP 回應碼。  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> \- 在 <xref:System.Data.Services.Client.DataServiceQuery%601> 上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 方法時，取得實體集中的實體總數。  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> \- 傳回包含下一頁結果之 URI 的 <xref:System.Data.Services.Client.DataServiceQueryContinuation> 物件。  
  
 根據預設，[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 只會傳回查詢 URI 所明確選取的資料。  它還提供選項可讓您於必要時，從資料服務明確載入其他資料。  每次您從資料服務明確載入資料時，就會傳送一個要求至資料服務。  可以明確載入的資料包括相關實體、分頁的回應資料，以及二進位資料流。  
  
> [!NOTE]
>  因為資料服務可能傳回分頁的回應，我們建議您的應用程式使用程式設計模式來處理分頁的資料服務回應。  如需詳細資訊，請參閱[載入延後的內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
 指定回應中僅傳回特定實體屬性，也可以降低查詢傳回的資料量。  如需詳細資訊，請參閱[查詢投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)。  
  
## 取得集合中實體總數的計數  
 在部分情況下，這麼做有助於得知實體集中的實體總數，且不僅是查詢傳回的數目。  在 <xref:System.Data.Services.Client.DataServiceQuery%601> 上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> 方法，以要求集合中的這項實體總計數包含在查詢結果中。  在此案例中，傳回之 <xref:System.Data.Services.Client.QueryOperationResponse%601> 的 <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> 屬性會傳回集合中的實體總數。  
  
 您也可以分別呼叫 <xref:System.Linq.Enumerable.Count%2A> 或 <xref:System.Linq.Enumerable.LongCount%2A> 方法，藉此只取得集合中的實體總計數，以做為 <xref:System.Int32> 或做為 <xref:System.Int64> 值。  呼叫這些方法時，並未傳回 <xref:System.Data.Services.Client.QueryOperationResponse%601>；只會傳回計數值。  如需詳細資訊，請參閱[HOW TO：判斷查詢傳回的實體數目](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)。  
  
## 本章節內容  
 [查詢投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [物件 Materialization](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [LINQ 考量](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [HOW TO：執行資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [HOW TO：將查詢選項加入至資料服務查詢](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [HOW TO：判斷查詢傳回的實體數目](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [HOW TO：指定資料服務要求的用戶端認證](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [HOW TO：設定用戶端要求中的標頭](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [HOW TO：專案查詢結果](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)