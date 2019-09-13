---
title: LINQ 考量 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, LINQ
- querying the data service [WCF Data Services]
- WCF Data Services, querying
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
ms.openlocfilehash: 659e3ba02367feee4539a984b679173ee4544d17
ms.sourcegitcommit: 5ae5a1a9520b8b8b6164ad728d396717f30edafc
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/11/2019
ms.locfileid: "70894310"
---
# <a name="linq-considerations-wcf-data-services"></a>LINQ 考量 (WCF Data Services)
本主題所提供的資訊是關於您要使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端時所撰寫和執行 LINQ 查詢的方式，以及使用 LINQ 查詢實作 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 之資料服務的限制。 如需針對以[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]為基礎的資料服務撰寫和執行查詢的詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
## <a name="composing-linq-queries"></a>撰寫 LINQ 查詢  
 LINQ 可讓您針對實作 <xref:System.Collections.Generic.IEnumerable%601> 之物件的集合，撰寫查詢。 Visual Studio 和 DataSvcUtil 工具中的 [**加入服務參考**] 對話方塊都是用來產生[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]服務的表示，做為繼承自<xref:System.Data.Services.Client.DataServiceContext>的實體容器類別，以及代表的物件。在摘要中傳回的實體。 這些工具也會針對服務公開為摘要的集合，產生實體容器類別的屬性。 封裝資料服務之類別的這些每個屬性都會傳回 <xref:System.Data.Services.Client.DataServiceQuery%601>。 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別會實作 LINQ 所定義的 <xref:System.Linq.IQueryable%601> 介面，因此，您可以針對資料服務所公開的摘要，撰寫 LINQ 查詢，用戶端程式庫會將這些摘要轉譯為執行時傳送至資料服務的查詢要求 URI。  
  
> [!IMPORTANT]
> 可以用 LINQ 語法表示的查詢集合會比在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 資料服務所使用之 URI 語法中啟用的查詢集合更廣泛。 當查詢無法對應至目標資料服務中的 URI 時，就會引發 <xref:System.NotSupportedException>。 如需詳細資訊，請參閱本主題中的[不支援的 LINQ 方法](linq-considerations-wcf-data-services.md#unsupportedMethods)。  
  
 下列範例是 LINQ 查詢，它會傳回運費成本超過美金 $30 元的 `Orders`，並依運送日期排序結果 (從最近的運送日期開始)：  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]    
  
 此 LINQ 查詢會轉譯成下列查詢 URI，並針對以 Northwind 為基礎的[快速入門](quickstart-wcf-data-services.md)資料服務來執行：  
  
```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 如需 LINQ 的一般資訊，請參閱[語言整合式查詢（linq） C# -](../../../csharp/programming-guide/concepts/linq/index.md)或[語言整合式查詢（linq）-Visual Basic](../../../visual-basic/programming-guide/concepts/linq/index.md)。  
  
 LINQ 可讓您同時使用語言專屬的宣告式查詢語法 (如以上範例所示)，以及所謂標準查詢運算子的一組查詢方法來撰寫查詢。 相當於以上範例的查詢僅能使用以方法為基礎的語法撰寫，如以下範例所示：  
  
[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqexpressionspecific)]      
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqExpressionSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqexpressionspecific)]    
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端可以將這兩種撰寫查詢轉譯成查詢 URI，而且您可以藉由將查詢方法附加到查詢運算式，來擴充 LINQ 查詢。 當您藉由將方法語法附加到查詢運算式或 <xref:System.Data.Services.Client.DataServiceQuery%601> 來撰寫 LINQ 查詢時，會以呼叫方法的順序，將運算加入至查詢 URI。 這相當於呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法，將每個查詢選項加入至查詢 URI。  
  
## <a name="executing-linq-queries"></a>執行 LINQ 查詢  
 當 <xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 或 <xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29> 之類的特定 LINQ 查詢方法附加至查詢時，會執行該查詢。 以隱含的方式列舉結果時 (例如在 `foreach` 執行迴圈期間)，或將查詢指派到 `List` 集合時，也會執行查詢。 如需詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
 用戶端會以兩個部分執行 LINQ 查詢。 如果可能，查詢中的 LINQ 運算式會先在用戶端上進行評估，然後產生 URI 架構的查詢，並將其傳送至資料服務，以便針對服務中的資料進行評估。 如需詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)中的[用戶端與伺服器執行](querying-the-data-service-wcf-data-services.md#executingQueries)一節。  
  
 在與 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 相容的查詢 URI 中無法轉譯 LINQ 查詢時，如果嘗試執行，就會引發例外狀況。 如需詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
## <a name="linq-query-examples"></a>LINQ 查詢範例  
 以下各節中的範例會示範可以針對 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務執行的 LINQ 查詢種類。  
  
<a name="filtering"></a>   
### <a name="filtering"></a>篩選  
 本節中的 LINQ 查詢範例會篩選服務所傳回之摘要中的資料。  
  
 下列範例是相當於篩選傳回之 `Orders` 實體的查詢，因此只會傳回運費成本超過 30 美元的訂單：  
  
- 使用 LINQ 查詢語法：  
  
[!code-csharp[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwhereclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwhereclausespecific)]     
  
- 使用 LINQ 查詢方法：  
  
[!code-csharp[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqwheremethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqwheremethodspecific)]       
  
- URI 查詢字串 `$filter` 選項：  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitquerywheremethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryWhereMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitquerywheremethodspecific)]       
  
 先前的所有範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`。  
  
<a name="sorting"></a>   
### <a name="sorting"></a>排序  
 下列範例示範相當於依公司名稱和郵遞區號，以遞減的方式排序傳回之資料的查詢：  
  
- 使用 LINQ 查詢語法：  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbyclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbyclausespecific)]        
  
- 使用 LINQ 查詢方法：  
  
[!code-csharp[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqorderbymethodspecific)]        
  
- URI 查詢字串 `$orderby` 選項：  
  
[!code-csharp[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryorderbymethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQueryOrderByMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryorderbymethodspecific)]         
  
 先前的所有範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`。  
  
<a name="projection"></a>   
### <a name="projection"></a>Projection  
 下列範例示範相當於將傳回的資料投影成較窄之 `CustomerAddress` 類型的查詢：  
  
- 使用 LINQ 查詢語法：  
  
[!code-csharp[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectclausespecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectClauseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectclausespecific)]         
  
- 使用 LINQ 查詢方法：  
  
[!code-csharp[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqselectmethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSelectMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqselectmethodspecific)]         

> [!NOTE]
> 您無法使用 `$select` 方法，將 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 查詢選項加入至查詢 URI。 建議您使用 LINQ <xref:System.Linq.Enumerable.Select%2A> 方法，讓用戶端在要求 URI 中產生 `$select` 查詢選項。  
  
 先前的兩個範例都會轉譯為查詢 URI：`"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`。  
  
<a name="paging"></a>   
### <a name="client-paging"></a>用戶端分頁  
 下列範例示範相當於要求包含 25 個訂單，並略過前 50 個訂單之排序實體頁面的查詢：  
  
- 將查詢方法套用至 LINQ 查詢：  
  
[!code-csharp[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#LinqSkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqskiptakemethodspecific)]     
  
- URI 查詢字串 `$skip` 和 `$top` 選項：  
  
[!code-csharp[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#explicitqueryskiptakemethodspecific)]      
[!code-vb[Astoria Northwind Client#ExplicitQuerySkipTakeMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#explicitqueryskiptakemethodspecific)]     
  
 先前的兩個範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`。  
  
<a name="expand"></a>   
### <a name="expand"></a>Expand  
 當您查詢 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 資料服務時，可以要求與查詢做為目標之實體相關的實體包含傳回的摘要。 系統會針對 LINQ 查詢做為目標的實體集，在 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法，並將相關的實體集名稱當做 `path` 參數提供。 如需詳細資訊，請參閱[載入延](loading-deferred-content-wcf-data-services.md)後的內容。  
  
 下列範例示範相當於在查詢中使用 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法的方式：  
  
- 使用 LINQ 查詢語法：  
  
[!code-csharp[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandspecific)]      
[!code-vb[Astoria Northwind Client#LinqQueryExpandSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandspecific)]  
  
- 使用 LINQ 查詢方法：  

[!code-csharp[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryexpandmethodspecific)]       
[!code-vb[Astoria Northwind Client#LinqQueryExpandMethodSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryexpandmethodspecific)]       

 先前的兩個範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`。  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>不支援的 LINQ 方法  
 下表包含不支援，而且不得包含在針對 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務執行之查詢中的 LINQ 方法類別：  
  
|運算類型|不支援的方法|  
|--------------------|------------------------|  
|設定運算子|針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援所有設定運算子，其中包括：<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>|  
|排序運算子|針對 <xref:System.Collections.Generic.IComparer%601>，不支援需要 <xref:System.Data.Services.Client.DataServiceQuery%601> 的下列排序運算子：<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29>|  
|投影及篩選運算子|針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援接受位置引數的下列投影及篩選運算子：<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29>|  
|群組運算子|針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援所有群組運算子，包括：<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A><br /><br /> 群組運算必須在用戶端上執行。|  
|彙總運算子|針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援所有彙總運算，包括：<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> 彙總運算必須在用戶端上執行，或由服務作業封裝。|  
|分頁運算子|針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援下列分頁運算子：<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A>**注意：** 在空序列上執行的分頁運算子會傳回 null。|  
|其他運算子|針對 <xref:System.Data.Services.Client.DataServiceQuery%601>，不支援下列其他運算子：<br /><br /> 1.  <xref:System.Linq.Enumerable.Empty%2A><br />2.  <xref:System.Linq.Enumerable.Range%2A><br />3.  <xref:System.Linq.Enumerable.Repeat%2A><br />4.  <xref:System.Linq.Enumerable.ToDictionary%2A><br />5.  <xref:System.Linq.Enumerable.ToLookup%2A>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>支援的運算式函數  
 下列 Common Language Runtime (CLR) 方法和屬性可以在查詢運算式中轉譯，以便加入 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務的要求 URI，因此受到支援：  
  
|<xref:System.String>成員國|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
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
  
|<xref:System.DateTime>成員<sup>1</sup>|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
|-------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.DateTime.Day>|`int day(DateTime p0)`|  
|<xref:System.DateTime.Hour>|`int hour(DateTime p0)`|  
|<xref:System.DateTime.Minute>|`int minute(DateTime p0)`|  
|<xref:System.DateTime.Month>|`int month(DateTime p0)`|  
|<xref:System.DateTime.Second>|`int second(DateTime p0)`|  
|<xref:System.DateTime.Year>|`int year(DateTime p0)`|  
  
 <sup>1</sup>也支援中的對等日期<xref:Microsoft.VisualBasic.DateAndTime?displayProperty=nameWithType>和時間屬性，以及<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A> Visual Basic 中的方法。  
  
|<xref:System.Math>成員國|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:System.Linq.Expressions.Expression>成員國|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 用戶端可能也可以評估用戶端上的其他 CLR 函數。 系統會針對無法在用戶端上評估，而且無法轉譯為有效要求 URI 以便在伺服器上進行評估的所有運算式，引發 <xref:System.NotSupportedException>。  
  
## <a name="see-also"></a>另請參閱

- [查詢資料服務](querying-the-data-service-wcf-data-services.md)
- [查詢投影](query-projections-wcf-data-services.md)
- [物件具體化](object-materialization-wcf-data-services.md)
- [ODataURI 慣例](https://go.microsoft.com/fwlink/?LinkID=185564)
