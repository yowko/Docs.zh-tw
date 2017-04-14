---
title: "LINQ 考量 (WCF Data Services) | Microsoft Docs"
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
  - "WCF 資料服務、 LINQ"
  - "查詢資料服務 [WCF 資料服務]"
  - "WCF 資料服務查詢"
ms.assetid: cc4ec9e9-348f-42a6-a78e-1cd40e370656
caps.latest.revision: 5
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 5
---
# LINQ 考量 (WCF Data Services)
本主題所提供的資訊是關於您要使用 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端時所撰寫和執行 LINQ 查詢的方式，以及使用 LINQ 查詢實作 [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 之資料服務的限制。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]撰寫及執行查詢[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]-型資料服務，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。  
  
## <a name="composing-linq-queries"></a>撰寫 LINQ 查詢  
 LINQ 可讓您針對實作的物件集合撰寫查詢<xref:System.Collections.Generic.IEnumerable%601>。 這兩個**加入服務參考**對話方塊中的 [!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]和 DataSvcUtil.exe 工具會用來產生一種[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]服務做為實體容器類別繼承自<xref:System.Data.Services.Client.DataServiceContext>，以及的表示摘要中傳回之實體的物件。 這些工具也會針對服務公開為摘要的集合，產生實體容器類別的屬性。 每個封裝資料服務傳回之類別的這些屬性<xref:System.Data.Services.Client.DataServiceQuery%601>。 因為<xref:System.Data.Services.Client.DataServiceQuery%601>類別會實作<xref:System.Linq.IQueryable%601>介面定義 linq，您可以撰寫 LINQ 查詢，針對摘要資料服務所公開的用戶端程式庫轉譯為查詢要求傳送至資料服務上執行的 URI。  
  
> [!IMPORTANT]
>  可以用 LINQ 語法表示的查詢集合會比在 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 資料服務所使用之 URI 語法中啟用的查詢集合更廣泛。 A <xref:System.NotSupportedException>查詢無法對應至目標資料服務中的 URI 時引發。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][不支援的 LINQ 方法](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md#unsupportedMethods)本主題中。  
  
 下列範例是 LINQ 查詢，它會傳回運費成本超過美金 $30 元的 `Orders`，並依運送日期排序結果 (從最近的運送日期開始)：  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqSpecific)]  
  
 此 LINQ 查詢轉譯成下列查詢 URI 執行針對 Northwind 架構[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)資料服務︰  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
 關於 LINQ 的一般資訊，請參閱[LINQ （語言整合式查詢）](../Topic/LINQ%20\(Language-Integrated%20Query\).md)。  
  
 LINQ 可讓您同時使用語言專屬的宣告式查詢語法 (如以上範例所示)，以及所謂標準查詢運算子的一組查詢方法來撰寫查詢。 相當於以上範例的查詢僅能使用以方法為基礎的語法撰寫，如以下範例所示：  
  
  [Astoria NorthwindClient #AddQueryOptionsLinqExpressionSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#AddQueryOptionsLinqExpressionSpecific)]  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端可以將這兩種撰寫查詢轉譯成查詢 URI，而且您可以藉由將查詢方法附加到查詢運算式，來擴充 LINQ 查詢。 當您撰寫 LINQ 查詢藉由將方法語法附加到查詢運算式或<xref:System.Data.Services.Client.DataServiceQuery%601>，將運算加入至查詢 URI 中呼叫方法的順序。 這就相當於呼叫<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>方法，將每個查詢選項加入至查詢 URI。  
  
## <a name="executing-linq-queries"></a>執行 LINQ 查詢  
 特定 LINQ 查詢方法，例如<xref:System.Linq.Enumerable.First%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>或<xref:System.Linq.Enumerable.Single%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%29>附加至查詢時導致執行查詢。 以隱含的方式列舉結果時 (例如在 `foreach` 執行迴圈期間)，或將查詢指派到 `List` 集合時，也會執行查詢。 如需詳細資訊，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。  
  
 用戶端會以兩個部分執行 LINQ 查詢。 如果可能，查詢中的 LINQ 運算式會先在用戶端上進行評估，然後產生 URI 架構的查詢，並將其傳送至資料服務，以便針對服務中的資料進行評估。 如需詳細資訊，請參閱[用戶端與伺服器執行](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md#executingQueries)中[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。  
  
 在與 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 相容的查詢 URI 中無法轉譯 LINQ 查詢時，如果嘗試執行，就會引發例外狀況。 如需詳細資訊，請參閱[查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)。  
  
## <a name="linq-query-examples"></a>LINQ 查詢範例  
 以下各節中的範例會示範可以針對 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務執行的 LINQ 查詢種類。  
  
<a name="filtering"></a>   
### <a name="filtering"></a>篩選  
 本節中的 LINQ 查詢範例會篩選服務所傳回之摘要中的資料。  
  
 下列範例是相當於篩選傳回之 `Orders` 實體的查詢，因此只會傳回運費成本超過&30; 美元的訂單：  
  
-   使用 LINQ 查詢語法：  
  
      [Astoria NorthwindClient #LinqWhereClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereClauseSpecific)]  
  
-   使用 LINQ 查詢方法：  
  
      [Astoria NorthwindClient #LinqWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqWhereMethodSpecific)]  
  
-   URI 查詢字串 `$filter` 選項：  
  
      [Astoria NorthwindClient #ExplicitQueryWhereMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryWhereMethodSpecific)]  
  
 先前的所有範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$filter=Freight gt 30M`。  
  
<a name="sorting"></a>   
### <a name="sorting"></a>排序  
 下列範例示範相當於依公司名稱和郵遞區號，以遞減的方式排序傳回之資料的查詢：  
  
-   使用 LINQ 查詢語法：  
  
      [Astoria NorthwindClient #LinqOrderByClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByClauseSpecific)]  
  
-   使用 LINQ 查詢方法：  
  
      [Astoria NorthwindClient #LinqOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqOrderByMethodSpecific)]  
  
-   URI 查詢字串 `$orderby` 選項：  
  
      [Astoria NorthwindClient #ExplicitQueryOrderByMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQueryOrderByMethodSpecific)]  
  
 先前的所有範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Customers()?$orderby=CompanyName,PostalCode desc`。  
  
<a name="projection"></a>   
### <a name="projection"></a>Projection  
 下列範例示範相當於將傳回的資料投影成較窄之 `CustomerAddress` 類型的查詢：  
  
-   使用 LINQ 查詢語法：  
  
      [Astoria NorthwindClient #LinqSelectClauseSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectClauseSpecific)]  
  
-   使用 LINQ 查詢方法：  
  
      [Astoria NorthwindClient #LinqSelectMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSelectMethodSpecific)]  
  
> [!NOTE]
>  `$select`查詢選項無法使用加入至查詢 URI <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>方法。 我們建議您使用 LINQ<xref:System.Linq.Enumerable.Select%2A>方法，讓用戶端產生`$select`查詢要求 URI 中的選項。\</TSource, TResult>  
  
 先前的兩個範例都會轉譯為查詢 URI：`"http://localhost:12345/northwind.svc/Customers()?$filter=Country eq 'GerGerm'&$select=CustomerID,Address,City,Region,PostalCode,Country"`。  
  
<a name="paging"></a>   
### <a name="client-paging"></a>用戶端分頁  
 下列範例示範相當於要求包含 25 個訂單，並略過前 50 個訂單之排序實體頁面的查詢：  
  
-   將查詢方法套用至 LINQ 查詢：  
  
      [Astoria NorthwindClient #LinqSkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqSkipTakeMethodSpecific)]  
  
-   URI 查詢字串 `$skip` 和 `$top` 選項：  
  
      [Astoria NorthwindClient #ExplicitQuerySkipTakeMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#ExplicitQuerySkipTakeMethodSpecific)]  
  
 先前的兩個範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$orderby=OrderDate desc&$skip=50&$top=25`。  
  
<a name="expand"></a>   
### <a name="expand"></a>展開  
 當您查詢 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 資料服務時，可以要求與查詢做為目標之實體相關的實體包含傳回的摘要。 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>上呼叫方法<xref:System.Data.Services.Client.DataServiceQuery%601> LINQ 查詢為目標之實體集，與相關的實體設定為使用者提供名稱`path`參數。 如需詳細資訊，請參閱[載入延後內容](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md)。  
  
 下列範例顯示對等的方式使用<xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A>方法在查詢中︰  
  
-   使用 LINQ 查詢語法：  
  
      [Astoria NorthwindClient #LinqQueryExpandSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandSpecific)]  
  
-   使用 LINQ 查詢方法：  
  
      [Astoria NorthwindClient #LinqQueryExpandMethodSpecific](../../../../amples/snippets/xml/VS_Snippets_Misc/astoria northwind service/astoria.vsmdi NorthwindClient#LinqQueryExpandMethodSpecific)]  
  
 先前的兩個範例都會轉譯為查詢 URI：`http://localhost:12345/northwind.svc/Orders()?$filter=CustomerID eq 'ALFKI'&$expand=Order_Details`。  
  
<a name="unsupportedMethods"></a>   
## <a name="unsupported-linq-methods"></a>不支援的 LINQ 方法  
 下表包含不支援，而且不得包含在針對 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務執行之查詢中的 LINQ 方法類別：  
  
|運算類型|不支援的方法|  
|--------------------|------------------------|  
|設定運算子|所有設定運算子都不支援對<xref:System.Data.Services.Client.DataServiceQuery%601>，其中包括︰<br /><br /> -   <xref:System.Linq.Enumerable.All%2A><br />-   <xref:System.Linq.Enumerable.Any%2A><br />-   <xref:System.Linq.Enumerable.Concat%2A><br />-   <xref:System.Linq.Enumerable.DefaultIfEmpty%2A><br />-   <xref:System.Linq.Enumerable.Distinct%2A><br />-   <xref:System.Linq.Enumerable.Except%2A><br />-   <xref:System.Linq.Enumerable.Intersect%2A><br />-   <xref:System.Linq.Enumerable.Union%2A><br />-   <xref:System.Linq.Enumerable.Zip%2A>\</TFirst, TSecond, TResult>|  
|排序運算子|需要的下列排序運算子<xref:System.Collections.Generic.IComparer%601>不支援對<xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.OrderBy%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.OrderByDescending%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenBy%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> </TSource, TKey> </TSource, TKey><br />-   <xref:System.Linq.Enumerable.ThenByDescending%60%602%28System.Linq.IOrderedEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2C%60%601%7D%2CSystem.Collections.Generic.IComparer%7B%60%601%7D%29> \</TSource, TKey> \</TSource, TKey>|  
|投影及篩選運算子|下列投影及篩選運算子可接受位置引數不支援對<xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.Join%60%604%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%2CSystem.Func%7B%60%600%2C%60%602%7D%2CSystem.Func%7B%60%601%2C%60%602%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%603%7D%2CSystem.Collections.Generic.IEqualityComparer%7B%60%602%7D%29> </TOuter, TInner, TResult> </TInner, TKey> </TOuter, TKey> </TOuter, TInner, TKey, TResult><br />-   <xref:System.Linq.Enumerable.Select%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2C%60%601%7D%29> </TSource, Int32, TResult> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%602%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%29> </TSource, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> \</TSource, TCollection, TResult> \</TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.SelectMany%60%603%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Collections.Generic.IEnumerable%7B%60%601%7D%7D%2CSystem.Func%7B%60%600%2C%60%601%2C%60%602%7D%29> </TSource, TCollection, TResult> </TSource, TCollection, TResult><br />-   <xref:System.Linq.Enumerable.Where%60%601%28System.Collections.Generic.IEnumerable%7B%60%600%7D%2CSystem.Func%7B%60%600%2CSystem.Int32%2CSystem.Boolean%7D%29> \</TSource, Int32, Boolean>|  
|群組運算子|所有群組運算子不都支援對<xref:System.Data.Services.Client.DataServiceQuery%601>，包括下列︰<br /><br /> -   <xref:System.Linq.Enumerable.GroupBy%2A>\</TSource, TKey><br />-   <xref:System.Linq.Enumerable.GroupJoin%2A>\</TOuter, TInner, TKey, TResult><br /><br /> 群組運算必須在用戶端上執行。|  
|彙總運算子|針對不支援所有的彙總運算<xref:System.Data.Services.Client.DataServiceQuery%601>，包括下列︰<br /><br /> -   <xref:System.Linq.Enumerable.Aggregate%2A><br />-   <xref:System.Linq.Enumerable.Average%2A><br />-   <xref:System.Linq.Enumerable.Count%2A><br />-   <xref:System.Linq.Enumerable.LongCount%2A><br />-   <xref:System.Linq.Enumerable.Max%2A><br />-   <xref:System.Linq.Enumerable.Min%2A><br />-   <xref:System.Linq.Enumerable.Sum%2A><br /><br /> 彙總運算必須在用戶端上執行，或由服務作業封裝。|  
|分頁運算子|針對不支援下列分頁運算子<xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> -   <xref:System.Linq.Enumerable.ElementAt%2A><br />-   <xref:System.Linq.Enumerable.Last%2A><br />-   <xref:System.Linq.Enumerable.LastOrDefault%2A><br />-   <xref:System.Linq.Enumerable.SkipWhile%2A><br />-   <xref:System.Linq.Enumerable.TakeWhile%2A> **附註︰**空序列執行的分頁運算子會傳回 null。|  
|其他運算子|下列其他運算子不支援對<xref:System.Data.Services.Client.DataServiceQuery%601>:<br /><br /> 1.<xref:System.Linq.Enumerable.Empty%2A><br />2.<xref:System.Linq.Enumerable.Range%2A><br />3.<xref:System.Linq.Enumerable.Repeat%2A><br />4.<xref:System.Linq.Enumerable.ToDictionary%2A></TSource, TKey><br />5.<xref:System.Linq.Enumerable.ToLookup%2A>\</TSource, TKey>|  
  
<a name="supportedExpressions"></a>   
## <a name="supported-expression-functions"></a>支援的運算式函數  
 下列 Common Language Runtime (CLR) 方法和屬性可以在查詢運算式中轉譯，以便加入 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務的要求 URI，因此受到支援：  
  
|<xref:System.String>成員|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
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
  
 <sup>1</sup>相等的日期和時間內容的<xref:Microsoft.VisualBasic.DateAndTime?displayProperty=fullName>，並將<xref:Microsoft.VisualBasic.DateAndTime.DatePart%2A>也支援在 Visual Basic 中的方法。  
  
|<xref:System.Math>成員|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
|---------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Math.Ceiling%28System.Decimal%29>|`decimal ceiling(decimal p0)`|  
|<xref:System.Math.Ceiling%28System.Double%29>|`double ceiling(double p0)`|  
|<xref:System.Math.Floor%28System.Decimal%29>|`decimal floor(decimal p0)`|  
|<xref:System.Math.Floor%28System.Double%29>|`double floor(double p0)`|  
|<xref:System.Math.Round%28System.Decimal%29>|`decimal round(decimal p0)`|  
|<xref:System.Math.Round%28System.Double%29>|`double round(double p0)`|  
  
|<xref:> System.Linq.Expressions.Expression?qualifyHint=False&autoUpgrade=True成員|支援的 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 函數|  
|---------------------------------------------------------------------------------------------------------------------------------------------------------|-------------------------------------------------------------------------------------|  
|<xref:System.Linq.Expressions.Expression.TypeIs%28System.Linq.Expressions.Expression%2CSystem.Type%29>|`bool isof(type p0)`|  
  
 用戶端可能也可以評估用戶端上的其他 CLR 函數。 A <xref:System.NotSupportedException>無法在用戶端上評估，而且無法轉譯為有效要求 URI 以便評估伺服器上的任何運算式，就會引發。  
  
## <a name="see-also"></a>另請參閱  
 [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)   
 [查詢投影](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)   
 [物件具體化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)   
 [OData: URI 慣例](http://go.microsoft.com/fwlink/?LinkID=185564)