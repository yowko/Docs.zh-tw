---
title: 更新資料服務 (WCF 資料服務)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, changing data
- WCF Data Services, client library
ms.assetid: 00d993be-ffed-4dea-baf7-6eea982cdb54
ms.openlocfilehash: 42980aa4691d8ecb9868336ecb270c9ad937b5a3
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517105"
---
# <a name="updating-the-data-service-wcf-data-services"></a>更新資料服務 (WCF 資料服務)
當您使用[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端程式庫來取用[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]換行字元、 程式庫會轉譯成用戶端資料服務類別的執行個體摘要中的項目。 這些資料服務類別會使用 <xref:System.Data.Services.Client.DataServiceContext> 所屬的 <xref:System.Data.Services.Client.DataServiceQuery%601> 來追蹤。 用戶端會追蹤您使用 <xref:System.Data.Services.Client.DataServiceContext> 上的方法所報告之實體的變更。 這些方法會讓用戶端追蹤所新增及刪除的實體，以及您對屬性值所做的變更或是您對實體執行個體之間的關聯性所做的變更。 當您呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，這些追蹤的變更會當做 REST 型作業傳回資料服務。  
  
> [!NOTE]
>  當您使用 <xref:System.Data.Services.Client.DataServiceCollection%601> 的執行個體將資料繫結至控制項時，對繫結控制項內的資料所做的變更會自動提報給 <xref:System.Data.Services.Client.DataServiceContext>。 如需詳細資訊，請參閱 <<c0> [ 將資料繫結至控制項](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md)。  
  
## <a name="adding-modifying-and-changing-entities"></a>加入、修改和變更實體  
 當您使用**加入服務參考**在 Visual Studio 中加入參考對話方塊[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]摘要，產生用戶端資料服務類別都有靜態*建立*採用其中一個方法針對每個不可為 null 的實體屬性的參數。 您可以使用這個方法建立實體類型類別的執行個體，如下列範例所示：  
  
 [!code-csharp[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#createnewproduct)]
 [!code-vb[Astoria Northwind Client#CreateNewProduct](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#createnewproduct)]  
  
 若要加入實體執行個體，呼叫適當*AddTo*方法<xref:System.Data.Services.Client.DataServiceContext>所產生的類別**加入服務參考**對話方塊中，如下列範例所示：  
  
 [!code-csharp[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addproductspecific)]
 [!code-vb[Astoria Northwind Client#AddProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addproductspecific)]  
  
 如此會將物件加入內容以及正確的實體集之中。 您也可以呼叫 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>，但是您必須提供實體集的名稱。 如果加入的實體與其他實體有一個以上的關聯性，可以使用 <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> 方法或是上述方法之一，同時也可以明確定義那些連結。 這些作業稍後將在本主題中說明。  
  
 若要修改現有的實體執行個體，請先查詢該實體、針對其屬性進行所需的變更，然後呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 中的 <xref:System.Data.Services.Client.DataServiceContext> 方法，以便讓用戶端程式庫知道它需要傳送該物件的更新，如下列範例所示：  
  
 [!code-csharp[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#modifycustomerspecific)]
 [!code-vb[Astoria Northwind Client#ModifyCustomerSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#modifycustomerspecific)]  
  
 若要刪除實體執行個體，請呼叫 <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> 中的 <xref:System.Data.Services.Client.DataServiceContext> 方法，如下列範例所示：  
  
 [!code-csharp[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#deleteproductspecific)]
 [!code-vb[Astoria Northwind Client#DeleteProductSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#deleteproductspecific)]  
  
 如需詳細資訊，請參閱[如何：新增、 修改及刪除實體](../../../../docs/framework/data/wcf/how-to-add-modify-and-delete-entities-wcf-data-services.md)。  
  
## <a name="attaching-entities"></a>附加實體  
 用戶端程式庫可讓您不需事先執行查詢就可以儲存您對實體所做的更新，然後將實體載入 <xref:System.Data.Services.Client.DataServiceContext>。 使用 <xref:System.Data.Services.Client.DataServiceContext.AttachTo%2A> 方法，將現有的物件附加至 <xref:System.Data.Services.Client.DataServiceContext> 中的特定實體集。 然後您就可以修改物件，並將變更儲存至資料服務。 在下列範例中，有一個已變更的自訂物件已附加至內容，然後在呼叫 <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 之前，先呼叫 <xref:System.Data.Services.Client.EntityStates.Modified>，將附加的物件標示為 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>。  
  
 [!code-csharp[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#attachobjectspecific)]
 [!code-vb[Astoria Northwind Client#AttachObjectSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#attachobjectspecific)]  
  
 下列考量適用於附加物件時：  
  
-   附加的物件處於 <xref:System.Data.Services.Client.EntityStates.Unchanged> 狀態。  
  
-   附加物件時，不會一併附加與該附加物件相關的物件。  
  
-   如果實體已依內容進行追蹤，則無法附加物件。  
  
-   當您附加與 eTag 值一起收到的實體物件時，會使用已採用 <xref:System.Data.Services.Client.DataServiceContext.AttachTo%28System.String%2CSystem.Object%2CSystem.String%29> 參數的 `etag` 方法多載。 當儲存已附加之物件的變更時，這個 eTag 值可用來檢查並行存取。  
  
 如需詳細資訊，請參閱[如何：將現有實體附加至 DataServiceContext](../../../../docs/framework/data/wcf/attach-an-existing-entity-to-dc-wcf-data.md)。  
  
## <a name="creating-and-modifying-relationship-links"></a>建立和修改關聯性連結  
 當您新增新的實體使用其中一種<xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>方法或是適當*AddTo*方法<xref:System.Data.Services.Client.DataServiceContext>類別**加入服務參考**對話方塊會產生的任何關聯性新的實體與相關的實體之間不會自動定義。  
  
 您可以建立和變更實體執行個體之間的關聯性，而且可以讓用戶端程式庫在資料服務中反映這些變更。 實體之間的關聯性會定義為模型中的關聯，而且 <xref:System.Data.Services.Client.DataServiceContext> 會追蹤每一個關聯性，如同內容中的連結物件。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 提供下列方法<xref:System.Data.Services.Client.DataServiceContext>類別來建立、 修改及刪除這些連結：  
  
|方法|描述|  
|------------|-----------------|  
|<xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A>|在兩個相關的實體物件之間建立新連結。 呼叫這個方法相當於呼叫 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> 和  <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> 來建立新物件並定義與現有物件的關聯性。|  
|<xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>|在兩個相關的實體物件之間建立新連結。|  
|<xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>|更新兩個相關實體物件之間的現有連結。 <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> 也用於刪除具有零或一對一 (`0..1:1`) 基數和一對一 (`1:1`) 基數的連結。 您可以將相關的物件設為 `null` 來達到這個目的。|  
|<xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A>|呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，標示內容正在追蹤刪除的連結。 當您刪除相關的物件或是先刪除與現有物件間的連結，然後加入與新相關物件間的連結而變更關聯性時，請使用這個方法。|  
|<xref:System.Data.Services.Client.DataServiceContext.AttachLink%2A>|告知兩個實體物件間之現有連結的內容。 當您呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，內容會假設這個關聯性已存在資料服務之中，而不會嘗試建立連結。 當您將物件附加至內容，而且也需要附加兩者間的連結時，請使用這個方法。 如果您要定義新關聯性，應改用 <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>。|  
|<xref:System.Data.Services.Client.DataServiceContext.DetachLink%2A>|停止追蹤內容中指定的連結。 此方法用來刪除一對多 (`*:*`) 關聯性。 對於基數為一的關聯性連結，您必須改用 <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>。|  
  
 下列範例將示範如何使用 <xref:System.Data.Services.Client.DataServiceContext.AddRelatedObject%2A> 方法，加入與現有 `Order_Detail` 實體相關的新 `Orders`。 由於新的 `Order_Details` 物件現在是由 <xref:System.Data.Services.Client.DataServiceContext> 追蹤，因此，加入之 `Order_Details` 物件與現有 `Products` 實體間的關聯性是透過呼叫 <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> 方法來定義：  
  
 [!code-csharp[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addorderdetailtoorderspecific)]
 [!code-vb[Astoria Northwind Client#AddOrderDetailToOrderSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addorderdetailtoorderspecific)]  
  
 當 <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> 方法定義的連結必須在資料服務中建立時，若要將這些連結反映在內容的物件之中，您也必須設定物件本身的導覽屬性。 在前面的範例中，您應設定的導覽屬性如下所示：  
  
 [!code-csharp[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#setnavprops)]
 [!code-vb[Astoria Northwind Client#SetNavProps](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#setnavprops)]  
  
 如需詳細資訊，請參閱[如何：定義實體關聯性](../../../../docs/framework/data/wcf/how-to-define-entity-relationships-wcf-data-services.md)。  
  
## <a name="saving-changes"></a>儲存變更  
 變更會在 <xref:System.Data.Services.Client.DataServiceContext> 執行個體中追蹤，但是不會立即傳送至伺服器。 在針對指定的活動完成所需的變更之後，請呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>，將所有變更提交至資料服務。 如需詳細資訊，請參閱 <<c0> [ 管理資料服務內容](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)。 您也可以透過 <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A> 和 <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A> 方法，非同步地儲存變更。 如需詳細資訊，請參閱 <<c0> [ 非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [查詢資料服務](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
- [非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)
- [批次處理作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
- [物件具體化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)
- [管理資料服務內容](../../../../docs/framework/data/wcf/managing-the-data-service-context-wcf-data-services.md)
