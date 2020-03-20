---
title: 呼叫服務作業 (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 1767f3a7-29d2-4834-a763-7d169693fa8b
ms.openlocfilehash: 41aac38cec97ae1afdd3c3c051d04ff242e7729d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79174351"
---
# <a name="calling-service-operations-wcf-data-services"></a>呼叫服務作業 (WCF Data Services)
開放資料協定 （OData） 定義資料服務的服務操作。 WCF 資料服務使您能夠將此類操作定義為數據服務上的方法。 就像其他資料服務資源，這些服務作業會使用 URI 來定址。 服務作業可以傳回實體類型集合、單一實體類型執行個體以及整數和字串等基本類型。 服務作業還可以傳回 `null` (在 Visual Basic 中為 `Nothing`)。 WCF 資料服務用戶端庫可用於訪問支援 HTTP GET 請求的服務操作。 這些服務作業類型是定義為已套用 <xref:System.ServiceModel.Web.WebGetAttribute> 的方法。 有關詳細資訊，請參閱[服務操作](service-operations-wcf-data-services.md)。  
  
 服務操作在實現 OData 的資料服務返回的中繼資料中公開。 在中繼資料中，服務作業會以 `FunctionImport` 元素來表示。 產生強型別 <xref:System.Data.Services.Client.DataServiceContext> 時，[加入服務參考] 和 DataSvcUtil.exe 工具會忽略此元素。 因此，您在內容上找不到可用來直接呼叫服務作業的方法。 但是，您仍可以使用 WCF 資料服務用戶端以以下兩種方式之一調用服務操作：  
  
- 提供服務作業的 URI 並搭配任何參數，以呼叫 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 上的 <xref:System.Data.Services.Client.DataServiceContext> 方法。 此方法用於呼叫任何 GET 服務作業。  
  
- 在 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 上使用 <xref:System.Data.Services.Client.DataServiceContext> 方法，以建立 <xref:System.Data.Services.Client.DataServiceQuery%601> 物件。 呼叫 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 時，要將服務作業的名稱提供給 `entitySetName` 參數。 列舉時或呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法時，此方法會傳回呼叫服務作業的 <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> 物件。 此方法用於呼叫傳回集合的 GET 服務作業。 可以使用 <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法提供單一參數。 此方法傳回的 <xref:System.Data.Services.Client.DataServiceQuery%601> 物件就像任何查詢物件一樣，可以進一步加以撰寫。 有關詳細資訊，請參閱[查詢資料服務](querying-the-data-service-wcf-data-services.md)。  
  
## <a name="considerations-for-calling-service-operations"></a>呼叫服務作業的考量  
 使用 WCF 資料服務用戶端調用服務操作時，請考慮以下事項。  
  
- 非同步訪問<xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>資料服務時，必須在 上<xref:System.Data.Services.Client.DataServiceContext>或使用等效非同步方法或在<xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>/<xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>上 使用<xref:System.Data.Services.Client.DataServiceQuery%601>方法。  
  
- WCF 資料服務用戶端庫無法實現返回基元類型集合的服務操作的結果。  
  
- WCF 資料服務用戶端庫不支援調用 POST 服務操作。 HTTP POST 呼叫的服務作業是使用 <xref:System.ServiceModel.Web.WebInvokeAttribute> 搭配 `Method="POST"` 參數所定義。 若要使用 HTTP POST 要求呼叫服務作業，您必須改用 <xref:System.Net.HttpWebRequest>。  
  
- 您不能使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 來呼叫傳回實體或基本類型單一結果或需要多個輸入參數的 GET 服務作業。 您必須改為呼叫 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 方法。  
  
- 如果在工具產生的強型別 <xref:System.Data.Services.Client.DataServiceContext> 部分類別上建立擴充方法，這個方法使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 或 <xref:System.Data.Services.Client.DataServiceContext.Execute%2A> 方法來呼叫服務作業。 這可讓您直接從內容中呼叫服務作業。 有關詳細資訊，請參閱博客文章"[服務操作"和 WCF 資料服務用戶端](https://docs.microsoft.com/archive/blogs/astoriateam/service-operations-and-the-wcf-data-services-client)。  
  
- 當您用於<xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>調用服務操作時，用戶端庫通過執行保留字元的百分比編碼（如<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>ampersand（&）和字串中單引號轉義來自動轉義提供給 的字元。 但是，當您調用其中一個*Execute*方法來調用服務操作時，必須記住執行任何使用者提供的字串值的此轉義。 URI 中的單引號是以一對單引號的形式來逸出。  
  
## <a name="examples-of-calling-service-operations"></a>呼叫服務作業的範例  
 本節包含以下示例，說明如何使用 WCF 資料服務用戶端庫調用服務操作：  
  
- [調用執行&lt; &gt; T 返回實體集合](calling-service-operations-wcf-data-services.md#ExecuteIQueryable)  
  
- [使用&lt;CreateQuery&gt; T 返回實體集合](calling-service-operations-wcf-data-services.md#CreateQueryIQueryable)  
  
- [調用執行&lt; &gt; T 返回單個實體](calling-service-operations-wcf-data-services.md#ExecuteSingleEntity)  
  
- [調用執行&lt; &gt; T 返回基元值的集合](calling-service-operations-wcf-data-services.md#ExecutePrimitiveCollection)  
  
- [調用執行&lt; &gt; T 返回單個基元值](calling-service-operations-wcf-data-services.md#ExecutePrimitiveValue)  
  
- [呼叫不傳回任何資料的服務作業](calling-service-operations-wcf-data-services.md#ExecuteVoid)  
  
- [非同步呼叫服務作業](calling-service-operations-wcf-data-services.md#ExecuteAsync)  
  
<a name="ExecuteIQueryable"></a>
### <a name="calling-executet-to-return-a-collection-of-entities"></a>調用執行\<T> 以返回實體集合  
 下列範例會呼叫名為 GetOrdersByCity 的服務作業，這項作業接受字串參數 `city` 並傳回 <xref:System.Linq.IQueryable%601>：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationiqueryable)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationIQueryable](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationiqueryable)]  
  
 在此範例中，服務作業會傳回 `Order` 物件集合與相關的 `Order_Detail` 物件。  
  
<a name="CreateQueryIQueryable"></a>
### <a name="using-createqueryt-to-return-a-collection-of-entities"></a>使用 createQuery\<T>返回實體集合  
 下列範例會使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A> 傳回用來呼叫相同 GetOrdersByCity 服務作業的 <xref:System.Data.Services.Client.DataServiceQuery%601>：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationcreatequery)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationCreateQuery](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationcreatequery)]  
  
 在此範例中，<xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> 方法用於將參數加入至查詢中，而 <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> 方法則用於將相關的 Order_Details 物件包含在結果中。  
  
<a name="ExecuteSingleEntity"></a>
### <a name="calling-executet-to-return-a-single-entity"></a>調用執行\<T> 返回單個實體  
 下列範例會呼叫名為 GetNewestOrder 的服務作業，這項作業只傳回單一 Order 實體：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleentity)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleEntity](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleentity)]  
  
 此範例會使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法，在執行時只要求單一 Order 實體。  
  
<a name="ExecutePrimitiveCollection"></a>
### <a name="calling-executet-to-return-a-collection-of-primitive-values"></a>調用執行\<T> 返回基元值的集合  
 下列範例會呼叫傳回字串值集合的服務作業：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationEnumString](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationenumstring)]  
  
<a name="ExecutePrimitiveValue"></a>
### <a name="calling-executet-to-return-a-single-primitive-value"></a>調用執行\<T> 以返回單個基元值  
 下列範例會呼叫傳回單一字串值的服務作業：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationsingleint)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationSingleInt](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationsingleint)]  
  
 此範例又一次使用 <xref:System.Linq.Enumerable.FirstOrDefault%2A> 方法，在執行時只要求單一整數值。  
  
<a name="ExecuteVoid"></a>
### <a name="calling-a-service-operation-that-returns-no-data"></a>呼叫不傳回任何資料的服務作業  
 下列範例會呼叫不傳回任何資料的服務作業：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationvoid)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationVoid](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationvoid)]  
  
 由於不傳回資料，因此沒有指派執行的值。 指出要求已成功的唯一表示就是沒有引發 <xref:System.Data.Services.Client.DataServiceQueryException>。  
  
<a name="ExecuteAsync"></a>
### <a name="calling-a-service-operation-asynchronously"></a>非同步呼叫服務作業  
 下列範例會藉由呼叫 <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A> 和 <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>，非同步呼叫服務作業：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncexecutioncomplete)]  
  
 由於不傳回資料，因此沒有指派執行傳回的值。 指出要求已成功的唯一表示就是沒有引發 <xref:System.Data.Services.Client.DataServiceQueryException>。  
  
 下列範例會使用 <xref:System.Data.Services.Client.DataServiceContext.CreateQuery%2A>，非同步呼叫相同的服務作業：  
  
 [!code-csharp[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#callserviceoperationqueryasync)]
 [!code-vb[Astoria Northwind Client#CallServiceOperationQueryAsync](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#callserviceoperationqueryasync)]  
  
 [!code-csharp[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#onasyncqueryexecutioncomplete)]
 [!code-vb[Astoria Northwind Client#OnAsyncQueryExecutionComplete](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#onasyncqueryexecutioncomplete)]  
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
