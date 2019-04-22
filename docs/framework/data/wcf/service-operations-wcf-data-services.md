---
title: 服務作業 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- service operations [WCF Data Services]
- WCF Data Services, service operations
ms.assetid: 583a690a-e60f-4990-8991-d6efce069d76
ms.openlocfilehash: c5514bf32bfe03a65d7d171a500dd5d4cfde35ff
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59517404"
---
# <a name="service-operations-wcf-data-services"></a>服務作業 (WCF 資料服務)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 可以讓您定義資料服務上的服務作業，以公開伺服器上的方法。 如同其他資料服務資源，服務作業依 URI 定址。 服務作業可讓您公開資料服務中的業務邏輯，例如實作驗證邏輯、套用以角色為基礎的安全性，或公開特殊的查詢功能。 服務作業是加入至資料服務類別的方法，衍生自 <xref:System.Data.Services.DataService%601>。 如同所有其他資料服務資源，您可以將參數提供給服務作業方法。 例如，下列服務作業 URI (根據[快速入門](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md)資料服務) 會將值傳遞`London`到`city`參數：  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'  
```  
  
 此服務作業的定義如下：  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationdef)]
 [!code-vb[Astoria Northwind Service#ServiceOperationDef](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationdef)]  
  
 您可以使用 <xref:System.Data.Services.DataService%601.CurrentDataSource%2A> 的 <xref:System.Data.Services.DataService%601>，直接存取資料服務所使用的資料來源。 如需詳細資訊，請參閱[如何：定義服務作業](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)。  
  
 如需如何從.NET Framework 用戶端應用程式呼叫服務作業的資訊，請參閱[呼叫服務作業](../../../../docs/framework/data/wcf/calling-service-operations-wcf-data-services.md)。  
  
## <a name="service-operation-requirements"></a>服務作業需求  
 定義資料服務的服務作業時，適用下列需求。 如果方法不符合這些需求，就不會公開成資料服務的服務作業。  
  
-   該作業必須是屬於資料服務類別成員的公開執行個體方法。  
  
-   該作業方法只能接受輸入參數。 資料服務無法存取訊息主體中傳送的資料。  
  
-   如果定義了參數，每個參數的類型都必須是基本類型。 非基本類型的任何資料都必須先序列化，然後再傳遞到字串參數中。  
  
-   該方法必須傳回下列其中一項：  
  
    -   `void` (在 Visual Basic 中為 `Nothing`)  
  
    -   <xref:System.Collections.Generic.IEnumerable%601>  
  
    -   <xref:System.Linq.IQueryable%601>  
  
    -   資料服務在資料模型中所公開的實體類型。  
  
    -   基本類別，例如整數或字串。  
  
-   為了支援排序、分頁和篩選等查詢選項，服務作業方法應該傳回 <xref:System.Linq.IQueryable%601>。 只傳回 <xref:System.Collections.Generic.IEnumerable%601> 的作業會拒絕對服務作業的要求 (包括查詢選項)。  
  
-   服務作業必須傳回 <xref:System.Linq.IQueryable%601>，才能支援使用，導覽屬性存取相關實體。  
  
-   此方法必須以 `[WebGet]` 或 `[WebInvoke]` 屬性標註。  
  
    -   `[WebGet]` 可讓您使用 GET 要求來叫用方法。  
  
    -   `[WebInvoke(Method = "POST")]` 可讓您使用 POST 要求來叫用方法。 不支援其他 <xref:System.ServiceModel.Web.WebInvokeAttribute> 方法。  
  
-   服務作業可能會以 <xref:System.Data.Services.SingleResultAttribute> 加上附註，以便指定此方法的傳回值是單一實體而非實體的集合。 此項差異表示 URI 中會顯示所產生的回應序列化，以及其他導覽屬性周遊的方法。 例如，使用 AtomPub 序列化時，單一資源類型執行個體會表示成 entry 項目，而一組執行個體則表示成 feed 項目。  
  
## <a name="addressing-service-operations"></a>定址服務作業  
 您可以將方法的名稱放入 URI 的第一個路徑區段中，以定址服務作業。 例如，下列 URI 會存取傳回 `GetOrdersByState` 物件之 <xref:System.Linq.IQueryable%601> 集合的 `Orders` 作業。  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByState?state='CA'&includeItems=true  
```  
  
 呼叫服務作業時，系統會將參數當做查詢選項提供。 先前的服務作業會同時接受字串參數 `state` 和布林值參數 `includeItems`，以指出是否在回應中包含相關的 `Order_Detail` 物件。  
  
 以下是服務作業的有效傳回型別：  
  
|有效傳回類型|URI 規則|  
|------------------------|---------------|  
|`void` (在 Visual Basic 中為 `Nothing`)<br /><br /> -或-<br /><br /> 實體類型<br /><br /> -或-<br /><br /> 基本類型|URI 必須是單一路徑區段，且為服務作業的名稱。 不允許使用查詢選項。|  
|<xref:System.Collections.Generic.IEnumerable%601>|URI 必須是單一路徑區段，且為服務作業的名稱。 因為結果類型不是 <xref:System.Linq.IQueryable%601> 類型，因此不允許查詢選項。|  
|<xref:System.Linq.IQueryable%601>|除了為服務作業名稱的路徑外，允許查詢其他路徑區段。 亦允許使用查詢選項。|  
  
 此外，您可以將其他路徑區段或查詢選項加入至 URI，端視服務作業的傳回類型而定。 例如，下列 URI 會存取傳回 `GetOrdersByCity` 物件之 <xref:System.Linq.IQueryable%601> 集合的 `Orders` 作業 (以 `RequiredDate` 遞減方式排序) 以及相關的 `Order_Details` 物件：  
  
```  
http://localhost:12345/Northwind.svc/GetOrdersByCity?city='London'&$expand=Order_Details&$orderby=RequiredDate desc  
```  
  
## <a name="service-operations-access-control"></a>服務作業存取控制  
 服務作業的服務範圍可視性由 <xref:System.Data.Services.IDataServiceConfiguration.SetServiceOperationAccessRule%2A> 類別的 <xref:System.Data.Services.IDataServiceConfiguration> 方法控制，與使用 <xref:System.Data.Services.IDataServiceConfiguration.SetEntitySetAccessRule%2A> 方法控制實體集可視性的方式非常相似。 例如，資料服務定義中的下列程式碼行可讓您存取 `CustomersByCity` 服務作業。  
  
 [!code-csharp[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#serviceoperationconfig)]
 [!code-vb[Astoria Northwind Service#ServiceOperationConfig](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#serviceoperationconfig)]  
  
> [!NOTE]
>  如果服務作業具有已透過現制存取基礎實體集隱藏的傳回型別，則用戶端應用程式就無法使用服務作業。  
  
 如需詳細資訊，請參閱[如何：定義服務作業](../../../../docs/framework/data/wcf/how-to-define-a-service-operation-wcf-data-services.md)。  
  
## <a name="raising-exceptions"></a>引發例外狀況  
 每當您在資料服務執行中引發例外狀況時，建議您使用 <xref:System.Data.Services.DataServiceException> 類別。 這是因為資料服務執行階段知道如何將此例外狀況物件的屬性正確對應到 HTTP 回應訊息。 當您在服務作業中引發 <xref:System.Data.Services.DataServiceException> 時，傳回的例外狀況會以 <xref:System.Reflection.TargetInvocationException> 包裝。 若要傳回沒有以 <xref:System.Data.Services.DataServiceException> 括住的基礎 <xref:System.Reflection.TargetInvocationException>，您必須覆寫 <xref:System.Data.Services.DataService%601.HandleException%2A> 中的 <xref:System.Data.Services.DataService%601> 方法、從 <xref:System.Data.Services.DataServiceException> 擷取 <xref:System.Reflection.TargetInvocationException>，然後將其當做最上層錯誤傳回，如以下範例所示：  
  
 [!code-csharp[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind2.svc.cs#handleexceptions)]
 [!code-vb[Astoria Northwind Service#HandleExceptions](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind2.svc.vb#handleexceptions)]  
  
## <a name="see-also"></a>另請參閱

- [攔截器](../../../../docs/framework/data/wcf/interceptors-wcf-data-services.md)
