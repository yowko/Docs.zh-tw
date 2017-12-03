---
title: "LINQ 考量 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 2b992cafbc0f8c68cfa695f244b9ec82d9d344af
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="linq-considerations-wcf-data-services"></a><span data-ttu-id="20316-102">LINQ 考量 (WCF Data Services)</span><span class="sxs-lookup"><span data-stu-id="20316-102">LINQ Considerations (WCF Data Services)</span></span>
<span data-ttu-id="20316-103">本主題所提供的資訊是關於您要使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端時所撰寫和執行 LINQ 查詢的方式，以及使用 LINQ 查詢實作 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 之資料服務的限制。</span><span class="sxs-lookup"><span data-stu-id="20316-103">This topic provides information about the way in which LINQ queries are composed and executed when you are using the [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client and limitations of using LINQ to query a data service that implements the [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)].</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="20316-104">撰寫及執行針對查詢[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-基礎資料服務，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20316-104"> composing and executing queries against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-based data service, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="composing-linq-queries"></a><span data-ttu-id="20316-105">撰寫 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="20316-105">Composing LINQ Queries</span></span>  
 <span data-ttu-id="20316-106">LINQ 可讓您針對實作 <xref:System.Collections.Generic.IEnumerable%601> 之物件的集合，撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="20316-106">LINQ enables you to compose queries against a collection of objects that implements <xref:System.Collections.Generic.IEnumerable%601>.</span></span> <span data-ttu-id="20316-107">這兩個**加入服務參考**對話方塊[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]和 DataSvcUtil.exe 工具會用來產生表示[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]服務的實體容器類別繼承自<xref:System.Data.Services.Client.DataServiceContext>，以及代表摘要中傳回的實體物件。</span><span class="sxs-lookup"><span data-stu-id="20316-107">Both the **Add Service Reference** dialog box in [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)] and the DataSvcUtil.exe tool are used to generate a representation of an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service as an entity container class that inherits from <xref:System.Data.Services.Client.DataServiceContext>, as well as objects that represent the entities returned in feeds.</span></span> <span data-ttu-id="20316-108">這些工具也會針對服務公開為摘要的集合，產生實體容器類別的屬性。</span><span class="sxs-lookup"><span data-stu-id="20316-108">These tools also generate properties on the entity container class for the collections that are exposed as feeds by the service.</span></span> <span data-ttu-id="20316-109">封裝資料服務之類別的這些每個屬性都會傳回 <xref:System.Data.Services.Client.DataServiceQuery%601>。</span><span class="sxs-lookup"><span data-stu-id="20316-109">Each of these properties of the class that encapsulates the data service return a <xref:System.Data.Services.Client.DataServiceQuery%601>.</span></span> <span data-ttu-id="20316-110"><xref:System.Data.Services.Client.DataServiceQuery%601> 類別會實作 LINQ 所定義的 <xref:System.Linq.IQueryable%601> 介面，因此，您可以針對資料服務所公開的摘要，撰寫 LINQ 查詢，用戶端程式庫會將這些摘要轉譯為執行時傳送至資料服務的查詢要求 URI。</span><span class="sxs-lookup"><span data-stu-id="20316-110">Because the <xref:System.Data.Services.Client.DataServiceQuery%601> class implements the <xref:System.Linq.IQueryable%601> interface defined by LINQ, you can compose a LINQ query against feeds exposed by the data service, which are translated by the client library into a query request URI that is sent to the data service on execution.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="20316-111">可以用 LINQ 語法表示的查詢集合會比在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 資料服務所使用之 URI 語法中啟用的查詢集合更廣泛。</span><span class="sxs-lookup"><span data-stu-id="20316-111">The set of queries expressible in the LINQ syntax is broader than those enabled in the URI syntax that is used by [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data services.</span></span> <span data-ttu-id="20316-112">當查詢無法對應至目標資料服務中的 URI 時，就會引發 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="20316-112">A <xref:System.NotSupportedException> is raised when the query cannot be mapped to a URI in the target data service.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="20316-113">[不受支援的 LINQ 方法](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods)本主題中。</span><span class="sxs-lookup"><span data-stu-id="20316-113"> the [Unsupported LINQ Methods](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods) in this topic.</span></span>  
  
 <span data-ttu-id="20316-114">下列範例是 LINQ 查詢，它會傳回運費成本超過美金 $30 元的 `Orders`，並依運送日期排序結果 (從最近的運送日期開始)：</span><span class="sxs-lookup"><span data-stu-id="20316-114">The following example is a LINQ query that returns `Orders` that have a freight cost of more than $30 and sorts the results by the shipping date, starting with the latest ship date:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 <span data-ttu-id="20316-115">此 LINQ 查詢會轉譯為下列的查詢執行針對 Northwind 架構的 URI[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)資料服務：</span><span class="sxs-lookup"><span data-stu-id="20316-115">This LINQ query is translated into the following query URI that is executed against the Northwind-based [quickstart](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) data service:</span></span>  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 <span data-ttu-id="20316-116">多個一般 LINQ 的詳細資訊，請參閱[LINQ (Language-Integrated Query ()](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d)。</span><span class="sxs-lookup"><span data-stu-id="20316-116">For more general information about LINQ, see [LINQ (Language-Integrated Query)](http://msdn.microsoft.com/library/a73c4aec-5d15-4e98-b962-1274021ea93d).</span></span>  
  
 <span data-ttu-id="20316-117">LINQ 可讓您同時使用語言專屬的宣告式查詢語法 (如以上範例所示)，以及所謂標準查詢運算子的一組查詢方法來撰寫查詢。</span><span class="sxs-lookup"><span data-stu-id="20316-117">LINQ enables you to compose queries by using both the language-specific declarative query syntax, shown in the previous example, as well as a set of query methods known as standard query operators.</span></span> <span data-ttu-id="20316-118">相當於以上範例的查詢僅能使用以方法為基礎的語法撰寫，如以下範例所示：</span><span class="sxs-lookup"><span data-stu-id="20316-118">An equivalent query to the previous example can be composed by using only the method-based syntax, as shown the following example:</span></span>  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 <span data-ttu-id="20316-119">[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端可以將這兩種撰寫查詢轉譯成查詢 URI，而且您可以藉由將查詢方法附加到查詢運算式，來擴充 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="20316-119">The [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] client is able to translate both kinds of composed queries into a query URI, and you can extend a LINQ query by appending query methods to a query expression.</span></span> <span data-ttu-id="20316-120">當您藉由將方法語法附加到查詢運算式或 <xref:System.Data.Services.Client.DataServiceQuery%601> 來撰寫 LINQ 查詢時，會以呼叫方法的順序，將運算加入至查詢 URI。</span><span class="sxs-lookup"><span data-stu-id="20316-120">When you compose LINQ queries by appending method syntax to a query expression or a <xref:System.Data.Services.Client.DataServiceQuery%601>, the operations are added to the query URI in the order in which methods are called.</span></span> <span data-ttu-id="20316-121">這相當於呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法，將每個查詢選項加入至查詢 URI。</span><span class="sxs-lookup"><span data-stu-id="20316-121">This is equivalent to calling the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method to add each query option to the query URI.</span></span>  
  
## <a name="executing-linq-queries"></a><span data-ttu-id="20316-122">執行 LINQ 查詢</span><span class="sxs-lookup"><span data-stu-id="20316-122">Executing LINQ Queries</span></span>  
 <span data-ttu-id="20316-123">當 <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 或 <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 之類的特定 LINQ 查詢方法附加至查詢時，會執行該查詢。</span><span class="sxs-lookup"><span data-stu-id="20316-123">Certain LINQ query methods, such as <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> or <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>, when appended to the query, cause the query to be executed.</span></span> <span data-ttu-id="20316-124">以隱含的方式列舉結果時 (例如在 `foreach` 執行迴圈期間)，或將查詢指派到 `List` 集合時，也會執行查詢。</span><span class="sxs-lookup"><span data-stu-id="20316-124">A query is also executed when results are enumerated implicitly, such as during a `foreach` loop or when the query is assigned to a `List` collection.</span></span> <span data-ttu-id="20316-125">如需詳細資訊，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20316-125">For more information, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="20316-126">用戶端會以兩個部分執行 LINQ 查詢。</span><span class="sxs-lookup"><span data-stu-id="20316-126">The client executes a LINQ query in two parts.</span></span> <span data-ttu-id="20316-127">如果可能，查詢中的 LINQ 運算式會先在用戶端上進行評估，然後產生 URI 架構的查詢，並將其傳送至資料服務，以便針對服務中的資料進行評估。</span><span class="sxs-lookup"><span data-stu-id="20316-127">Whenever possible, LINQ expressions in a query are first evaluated on the client, and then a URI-based query is generated and sent to the data service for evaluation against data in the service.</span></span> <span data-ttu-id="20316-128">如需詳細資訊，請參閱下節[用戶端與伺服器執行](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries)中[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20316-128">For more information, see the section [Client versus Server Execution](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries) in [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="20316-129">在與 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 相容的查詢 URI 中無法轉譯 LINQ 查詢時，如果嘗試執行，就會引發例外狀況。</span><span class="sxs-lookup"><span data-stu-id="20316-129">When a LINQ query cannot be translated in an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-compliant query URI, an exception is raised when execution is attempted.</span></span> <span data-ttu-id="20316-130">如需詳細資訊，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20316-130">For more information, see [Querying the Data Service](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md).</span></span>  
  
## <a name="linq-query-examples"></a><span data-ttu-id="20316-131">LINQ 查詢範例</span><span class="sxs-lookup"><span data-stu-id="20316-131">LINQ Query Examples</span></span>  
 <span data-ttu-id="20316-132">以下各節中的範例會示範可以針對 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務執行的 LINQ 查詢種類。</span><span class="sxs-lookup"><span data-stu-id="20316-132">The examples in the following sections demonstrate the kinds of LINQ queries that can be executed against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service.</span></span>  
  
<a name="filtering"></a>   
### <a name="filtering"></a><span data-ttu-id="20316-133">篩選</span><span class="sxs-lookup"><span data-stu-id="20316-133">Filtering</span></span>  
 <span data-ttu-id="20316-134">本節中的 LINQ 查詢範例會篩選服務所傳回之摘要中的資料。</span><span class="sxs-lookup"><span data-stu-id="20316-134">The LINQ query examples in this section filter data in the feed returned by the service.</span></span>  
  
 <span data-ttu-id="20316-135">下列範例是相當於篩選傳回之 `Orders` 實體的查詢，因此只會傳回運費成本超過 30 美元的訂單：</span><span class="sxs-lookup"><span data-stu-id="20316-135">The following examples are equivalent queries that filter the returned `Orders` entities so that only orders with a freight cost greater than $30 are returned:</span></span>  
  
-   <span data-ttu-id="20316-136">使用 LINQ 查詢語法：</span><span class="sxs-lookup"><span data-stu-id="20316-136">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwhereclausespecific)]     
  
-   <span data-ttu-id="20316-137">使用 LINQ 查詢方法：</span><span class="sxs-lookup"><span data-stu-id="20316-137">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqwheremethodspecific)]       
  
-   <span data-ttu-id="20316-138">URI 查詢字串 `$filter` 選項：</span><span class="sxs-lookup"><span data-stu-id="20316-138">The URI query string `$filter` option:</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 <span data-ttu-id="20316-139">先前的所有範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`。</span><span class="sxs-lookup"><span data-stu-id="20316-139">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`.</span></span>  
  
<a name="sorting"></a>   
### <a name="sorting"></a><span data-ttu-id="20316-140">排序</span><span class="sxs-lookup"><span data-stu-id="20316-140">Sorting</span></span>  
 <span data-ttu-id="20316-141">下列範例示範相當於依公司名稱和郵遞區號，以遞減的方式排序傳回之資料的查詢：</span><span class="sxs-lookup"><span data-stu-id="20316-141">The following examples show equivalent queries that sort returned data both by the company name and by postal code, descending:</span></span>  
  
-   <span data-ttu-id="20316-142">使用 LINQ 查詢語法：</span><span class="sxs-lookup"><span data-stu-id="20316-142">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbyclausespecific)]        
  
-   <span data-ttu-id="20316-143">使用 LINQ 查詢方法：</span><span class="sxs-lookup"><span data-stu-id="20316-143">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqorderbymethodspecific)]        
  
-   <span data-ttu-id="20316-144">URI 查詢字串 `$orderby` 選項：</span><span class="sxs-lookup"><span data-stu-id="20316-144">URI query string `$orderby` option):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 <span data-ttu-id="20316-145">先前的所有範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`。</span><span class="sxs-lookup"><span data-stu-id="20316-145">All of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`.</span></span>  
  
<a name="projection"></a>   
### <a name="projection"></a><span data-ttu-id="20316-146">Projection</span><span class="sxs-lookup"><span data-stu-id="20316-146">Projection</span></span>  
 <span data-ttu-id="20316-147">下列範例示範相當於將傳回的資料投影成較窄之 `CustomerAddress` 類型的查詢：</span><span class="sxs-lookup"><span data-stu-id="20316-147">The following examples show equivalent queries that project returned data into the narrower `CustomerAddress` type:</span></span>  
  
-   <span data-ttu-id="20316-148">使用 LINQ 查詢語法：</span><span class="sxs-lookup"><span data-stu-id="20316-148">Using LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectclausespecific)]         
  
-   <span data-ttu-id="20316-149">使用 LINQ 查詢方法：</span><span class="sxs-lookup"><span data-stu-id="20316-149">Using LINQ query methods:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqselectmethodspecific)]         
 
  
> [!NOTE]
>  <span data-ttu-id="20316-150">您無法使用 `$select` 方法，將 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 查詢選項加入至查詢 URI。</span><span class="sxs-lookup"><span data-stu-id="20316-150">The `$select` query option cannot be added to a query URI by using the <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> method.</span></span> <span data-ttu-id="20316-151">建議您使用 LINQ <xref:System.Linq.Enumerable.Select%2A> 方法，讓用戶端在要求 URI 中產生 `$select` 查詢選項。</span><span class="sxs-lookup"><span data-stu-id="20316-151">We recommend that you use the LINQ <xref:System.Linq.Enumerable.Select%2A> method to have the client generate the `$select` query option in the request URI.</span></span>  
  
 <span data-ttu-id="20316-152">先前的兩個範例都會轉譯為查詢 URI：`"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`。</span><span class="sxs-lookup"><span data-stu-id="20316-152">Both of the previous examples are translated to the query URI: `"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`.</span></span>  
  
<a name="paging"></a>   
### <a name="client-paging"></a><span data-ttu-id="20316-153">用戶端分頁</span><span class="sxs-lookup"><span data-stu-id="20316-153">Client Paging</span></span>  
 <span data-ttu-id="20316-154">下列範例示範相當於要求包含 25 個訂單，並略過前 50 個訂單之排序實體頁面的查詢：</span><span class="sxs-lookup"><span data-stu-id="20316-154">The following examples show equivalent queries that request a page of sorted order entities that includes 25 orders, skipping the first 50 orders:</span></span>  
  
-   <span data-ttu-id="20316-155">將查詢方法套用至 LINQ 查詢：</span><span class="sxs-lookup"><span data-stu-id="20316-155">Applying query methods to a LINQ query:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqskiptakemethodspecific)]     
  
-   <span data-ttu-id="20316-156">URI 查詢字串 `$skip` 和 `$top` 選項：</span><span class="sxs-lookup"><span data-stu-id="20316-156">URI query string `$skip` and `$top` options):</span></span>  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 <span data-ttu-id="20316-157">先前的兩個範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`。</span><span class="sxs-lookup"><span data-stu-id="20316-157">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`.</span></span>  
  
<a name="expand"></a>   
### <a name="expand"></a><span data-ttu-id="20316-158">展開</span><span class="sxs-lookup"><span data-stu-id="20316-158">Expand</span></span>  
 <span data-ttu-id="20316-159">當您查詢 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 資料服務時，可以要求與查詢做為目標之實體相關的實體包含傳回的摘要。</span><span class="sxs-lookup"><span data-stu-id="20316-159">When you query an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] data service, you can request that entities related to the entity targeted by the query be included the returned feed.</span></span> <span data-ttu-id="20316-160">系統會針對 LINQ 查詢做為目標的實體集，在 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法，並將相關的實體集名稱當做 `path` 參數提供。</span><span class="sxs-lookup"><span data-stu-id="20316-160">The <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method is called on the <xref:System.Data.Services.Client.DataServiceQuery%601> for the entity set targeted by the LINQ query, with the related entity set name supplied as the `path` parameter.</span></span> <span data-ttu-id="20316-161">如需詳細資訊，請參閱[載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。</span><span class="sxs-lookup"><span data-stu-id="20316-161">For more information, see [Loading Deferred Content](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).</span></span>  
  
 <span data-ttu-id="20316-162">下列範例示範相當於在查詢中使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法的方式：</span><span class="sxs-lookup"><span data-stu-id="20316-162">The following examples show equivalent ways to use the <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> method in a query:</span></span>  
  
-   <span data-ttu-id="20316-163">使用 LINQ 查詢語法：</span><span class="sxs-lookup"><span data-stu-id="20316-163">In LINQ query syntax:</span></span>  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandspecific)]  
  
-   <span data-ttu-id="20316-164">使用 LINQ 查詢方法：</span><span class="sxs-lookup"><span data-stu-id="20316-164">With LINQ query methods:</span></span>  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryexpandmethodspecific)]       
  
  
 <span data-ttu-id="20316-165">先前的兩個範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`。</span><span class="sxs-lookup"><span data-stu-id="20316-165">Both of the previous examples are translated to the query URI: `http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`.</span></span>  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a><span data-ttu-id="20316-166">不支援的 LINQ 方法</span><span class="sxs-lookup"><span data-stu-id="20316-166">Unsupported LINQ Methods</span></span>  
 <span data-ttu-id="20316-167">下表包含不支援，而且不得包含在針對 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務執行之查詢中的 LINQ 方法類別：</span><span class="sxs-lookup"><span data-stu-id="20316-167">The following table contains the classes of LINQ methods are not supported and cannot be included in a query executed against an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service:</span></span>  
  
|<span data-ttu-id="20316-168">運算類型</span><span class="sxs-lookup"><span data-stu-id="20316-168">Operation Type</span></span>|<span data-ttu-id="20316-169">不支援的方法</span><span class="sxs-lookup"><span data-stu-id="20316-169">Unsupported Method</span></span>|  
|--------------------|------------------------|  
|<span data-ttu-id="20316-170">設定運算子</span><span class="sxs-lookup"><span data-stu-id="20316-170">Set operators</span></span>|<span data-ttu-id="20316-171">針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援所有設定運算子，其中包括：</span><span class="sxs-lookup"><span data-stu-id="20316-171">All set operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, which included the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|<span data-ttu-id="20316-172">排序運算子</span><span class="sxs-lookup"><span data-stu-id="20316-172">Ordering operators</span></span>|<span data-ttu-id="20316-173">針對 <xref:System.Collections.Generic.IComparer%601>，不支援需要 <xref:System.Data.Services.Client.DataServiceQuery%601> 的下列排序運算子：</span><span class="sxs-lookup"><span data-stu-id="20316-173">The following ordering operators that require <xref:System.Collections.Generic.IComparer%601> are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|<span data-ttu-id="20316-174">投影及篩選運算子</span><span class="sxs-lookup"><span data-stu-id="20316-174">Projection and filtering operators</span></span>|<span data-ttu-id="20316-175">針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援接受位置引數的下列投影及篩選運算子：</span><span class="sxs-lookup"><span data-stu-id="20316-175">The following projection and filtering operators that accept a positional argument are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|<span data-ttu-id="20316-176">群組運算子</span><span class="sxs-lookup"><span data-stu-id="20316-176">Grouping operators</span></span>|<span data-ttu-id="20316-177">針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援所有群組運算子，包括：</span><span class="sxs-lookup"><span data-stu-id="20316-177">All grouping operators are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> <span data-ttu-id="20316-178">群組運算必須在用戶端上執行。</span><span class="sxs-lookup"><span data-stu-id="20316-178">Grouping operations must be performed on the client.</span></span>|  
|<span data-ttu-id="20316-179">彙總運算子</span><span class="sxs-lookup"><span data-stu-id="20316-179">Aggregate operators</span></span>|<span data-ttu-id="20316-180">針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援所有彙總運算，包括：</span><span class="sxs-lookup"><span data-stu-id="20316-180">All aggregate operations are unsupported against a <xref:System.Data.Services.Client.DataServiceQuery%601>, including the following:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> <span data-ttu-id="20316-181">彙總運算必須在用戶端上執行，或由服務作業封裝。</span><span class="sxs-lookup"><span data-stu-id="20316-181">Aggregate operations must either be performed on the client or be encapsulated by a service operation.</span></span>|  
|<span data-ttu-id="20316-182">分頁運算子</span><span class="sxs-lookup"><span data-stu-id="20316-182">Paging operators</span></span>|<span data-ttu-id="20316-183">針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援下列分頁運算子：</span><span class="sxs-lookup"><span data-stu-id="20316-183">The following paging operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br /><span data-ttu-id="20316-184">-   <xref:System.Linq.Enumerable.TakeWhile%2A>**附註：**空序列執行的分頁運算子會傳回 null。</span><span class="sxs-lookup"><span data-stu-id="20316-184">-   <xref:System.Linq.Enumerable.TakeWhile%2A> **Note:**  Paging operators that are executed on an empty sequence return null.</span></span>|  
|<span data-ttu-id="20316-185">其他運算子</span><span class="sxs-lookup"><span data-stu-id="20316-185">Other operators</span></span>|<span data-ttu-id="20316-186">針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援下列其他運算子：</span><span class="sxs-lookup"><span data-stu-id="20316-186">The following other operators are not supported against a <xref:System.Data.Services.Client.DataServiceQuery%601>:</span></span><br /><br /> <span data-ttu-id="20316-187">1.  <xref:System.Linq.Enumerable.Empty%2A></span><span class="sxs-lookup"><span data-stu-id="20316-187">1.  <xref:System.Linq.Enumerable.Empty%2A></span></span><br /><span data-ttu-id="20316-188">2.  <xref:System.Linq.Enumerable.Range%2A></span><span class="sxs-lookup"><span data-stu-id="20316-188">2.  <xref:System.Linq.Enumerable.Range%2A></span></span><br /><span data-ttu-id="20316-189">3.  <xref:System.Linq.Enumerable.Repeat%2A></span><span class="sxs-lookup"><span data-stu-id="20316-189">3.  <xref:System.Linq.Enumerable.Repeat%2A></span></span><br /><span data-ttu-id="20316-190">4.  <xref:System.Linq.Enumerable.ToDictionary%2A></span><span class="sxs-lookup"><span data-stu-id="20316-190">4.  <xref:System.Linq.Enumerable.ToDictionary%2A></span></span><br /><span data-ttu-id="20316-191">5.  <xref:System.Linq.Enumerable.ToLookup%2A></span><span class="sxs-lookup"><span data-stu-id="20316-191">5.  <xref:System.Linq.Enumerable.ToLookup%2A></span></span>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a><span data-ttu-id="20316-192">支援的運算式函數</span><span class="sxs-lookup"><span data-stu-id="20316-192">Supported Expression Functions</span></span>  
 <span data-ttu-id="20316-193">下列 Common Language Runtime (CLR) 方法和屬性可以在查詢運算式中轉譯，以便加入 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務的要求 URI，因此受到支援：</span><span class="sxs-lookup"><span data-stu-id="20316-193">The following common-language runtime (CLR) methods and properties are supported because they can be translated in a query expression for inclusion in the request URI to an [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] service:</span></span>  
  
|<span data-ttu-id="20316-194"><xref:System.String> 成員</span><span class="sxs-lookup"><span data-stu-id="20316-194"><xref:System.String> Member</span></span>|<span data-ttu-id="20316-195">支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數</span><span class="sxs-lookup"><span data-stu-id="20316-195">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|-----------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.String.Concat%28System.String%2CSystem.String%29>|`string concat(string p0, string p1)`|  
|<xref:System.String.Contains%28System.String%29>|`bool substringof(string p0, string p1)`|  
|<xref:System.String.EndsWith%28System.String%29>|`bool endswith(string p0, string p1)`|  
|<xref:System.String.IndexOf%28System.String%2CSystem.Int32%29>|`int indexof(string p0, string p1)`|  
|<xref:System.String.Length>|`int length(string p0)`|  
|<xref:System.String.Replace%28System.String%2CSystem.String%29>|`string replace(string p0, string find, string replace)`|  
|<xref:System.String.Substring%28System.Int32%29>|`string substring(string p0, int pos)`|  
|<xref:System.String.Substring%28System.Int32%2CSystem.Int32%29>|`string substring(string p0, int pos, int length)`|  
|<xref:System.String.ToLower>|`string tolower(string p0)`|  
|<xref:System.String.ToUpper>|`string toupper(string p0)`|  
|<xref:System.String.Trim>|`string trim(string p0)`|  
  
|<span data-ttu-id="20316-196"><xref:System.DateTime>成員<sup>1</sup></span><span class="sxs-lookup"><span data-stu-id="20316-196"><xref:System.DateTime> Member<sup>1</sup></span></span>|<span data-ttu-id="20316-197">支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數</span><span class="sxs-lookup"><span data-stu-id="20316-197">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <span data-ttu-id="20316-198"><sup>1</sup>相等的日期和時間內容的<xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>，並將<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>也支援在 Visual Basic 中的方法。</span><span class="sxs-lookup"><span data-stu-id="20316-198"><sup>1</sup>The equivalent date and time properties of <xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>, as well as the <xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> method in Visual Basic are also supported.</span></span>  
  
|<span data-ttu-id="20316-199"><xref:System.Math> 成員</span><span class="sxs-lookup"><span data-stu-id="20316-199"><xref:System.Math> Member</span></span>|<span data-ttu-id="20316-200">支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數</span><span class="sxs-lookup"><span data-stu-id="20316-200">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<span data-ttu-id="20316-201"><xref:System.Linq.Expressions.Expression> 成員</span><span class="sxs-lookup"><span data-stu-id="20316-201"><xref:System.Linq.Expressions.Expression> Member</span></span>|<span data-ttu-id="20316-202">支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數</span><span class="sxs-lookup"><span data-stu-id="20316-202">Supported [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] Function</span></span>|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 <span data-ttu-id="20316-203">用戶端可能也可以評估用戶端上的其他 CLR 函數。</span><span class="sxs-lookup"><span data-stu-id="20316-203">The client may also be able to evaluate additional CLR functions on the client.</span></span> <span data-ttu-id="20316-204">系統會針對無法在用戶端上評估，而且無法轉譯為有效要求 URI 以便在伺服器上進行評估的所有運算式，引發 <xref:System.NotSupportedException>。</span><span class="sxs-lookup"><span data-stu-id="20316-204">A <xref:System.NotSupportedException> is raised for any expression that cannot be evaluated on the client and cannot be translated into a valid request URI for evaluation on the server.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="20316-205">另請參閱</span><span class="sxs-lookup"><span data-stu-id="20316-205">See Also</span></span>  
 [<span data-ttu-id="20316-206">查詢資料服務</span><span class="sxs-lookup"><span data-stu-id="20316-206">Querying the Data Service</span></span>](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)  
 [<span data-ttu-id="20316-207">查詢投影</span><span class="sxs-lookup"><span data-stu-id="20316-207">Query Projections</span></span>](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
 [<span data-ttu-id="20316-208">物件具體化</span><span class="sxs-lookup"><span data-stu-id="20316-208">Object Materialization</span></span>](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
 [<span data-ttu-id="20316-209">OData: URI 慣例</span><span class="sxs-lookup"><span data-stu-id="20316-209">OData: URI Conventions</span></span>](http://go.microsoft.com/fwlink/?LinkID=185564)
