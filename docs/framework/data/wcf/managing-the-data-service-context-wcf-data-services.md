---
title: "管理資料服務內容 (WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 15b19d09-7de7-4638-9556-6ef396cc45ec
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c993a4f09a7187b45331f6beb71a9637da87d20f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="managing-the-data-service-context-wcf-data-services"></a>管理資料服務內容 (WCF Data Services)
<xref:System.Data.Services.Client.DataServiceContext> 類別會封裝針對特定資料服務支援的作業。 雖然 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務沒有狀態，但是內容具有狀態。 因此，您可以使用<xref:System.Data.Services.Client.DataServiceContext>類別上的用戶端以支援資料服務互動之間維護狀態的功能變更管理之類。 這個類別也可以管理識別及追蹤變更。  
  
## <a name="merge-options-and-identity-resolution"></a>合併選項和識別解析  
 當執行 <xref:System.Data.Services.Client.DataServiceQuery%601> 時，回應摘要中的實體會具體化成為物件。 如需詳細資訊，請參閱[物件具體化](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)。 回應訊息中的項目具體化成為物件的方式是根據識別解析來執行，而且會取決於執行查詢時所使用的合併選項。 如果在單一 <xref:System.Data.Services.Client.DataServiceContext> 的範圍中執行多個查詢或載入要求，則 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端只會追蹤具有特定索引鍵值之物件的單一執行個體。 用來執行識別解析的這個索引鍵會唯一識別實體。  
  
 根據預設，用戶端只會將回應摘要中的項目具體化成為實體的物件，而這些實體尚未被 <xref:System.Data.Services.Client.DataServiceContext> 所追蹤。 這表示，已經在快取中之物件的變更不會遭到覆寫。 這個行為的控制方式，是針對查詢和載入作業指定 <xref:System.Data.Services.Client.MergeOption> 值。 這個選項的指定方式是在 <xref:System.Data.Services.Client.DataServiceContext.MergeOption%2A> 上設定 <xref:System.Data.Services.Client.DataServiceContext> 屬性。 預設的合併選項值是 <xref:System.Data.Services.Client.MergeOption.AppendOnly>。 這樣只會具體化尚未被追蹤之實體的物件，這表示現有的物件不會遭到覆寫。 有另一個方式可避免用戶端的物件變更遭到資料服務中的更新所覆寫，就是指定 <xref:System.Data.Services.Client.MergeOption.PreserveChanges>。 當您指定 <xref:System.Data.Services.Client.MergeOption.OverwriteChanges> 時，將會使用回應摘要中項目的最新值來取代用戶端的物件值，即使這些物件已有變更亦然。 當使用 <xref:System.Data.Services.Client.MergeOption.NoTracking> 合併選項時，<xref:System.Data.Services.Client.DataServiceContext> 無法將用戶端物件所做的變更傳送給資料服務。 使用這個選項時，一定會使用資料服務中的值來覆寫變更。  
  
## <a name="managing-concurrency"></a>管理並行存取  
 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]支援開放式並行存取，可讓資料服務偵測更新衝突。 可以透過一種方式來設定資料服務提供者，讓資料服務使用並行語彙基元來檢查實體的變更。 這個語彙基元包含實體類型的一個或多個屬性，資料服務會驗證這些屬性以判斷資源是否已變更。 並行語彙基元，包含在要求與從資料服務回應的 eTag 標頭時，會為您所管理[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]用戶端。 如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
 <xref:System.Data.Services.Client.DataServiceContext> 會追蹤使用 <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>、<xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> 和 <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> 或是 <xref:System.Data.Services.Client.DataServiceCollection%601> 所手動提報的物件變更。 當呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，用戶端會將變更傳回資料服務。 當用戶端的資料變更與資料服務的變更衝突時，<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 會失敗。 當發生這個狀況時，您必須再次查詢實體資源，以接收更新資料。 若要覆寫資料服務中的變更，請使用 <xref:System.Data.Services.Client.MergeOption.PreserveChanges> 合併選項執行查詢。 當您再次呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 時，用戶端所保留的變更會保存到資料服務，前提是尚未針對資料服務中的資源進行其他變更。  
  
## <a name="saving-changes"></a>儲存變更  
 變更會在 <xref:System.Data.Services.Client.DataServiceContext> 執行個體中追蹤，但是不會立即傳送至伺服器。 在針對指定的活動完成所需的變更之後，請呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>，將所有變更提交至資料服務。 <xref:System.Data.Services.Client.DataServiceResponse> 作業完成後，會傳回 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 物件。 <xref:System.Data.Services.Client.DataServiceResponse> 物件包含一連串的 <xref:System.Data.Services.Client.OperationResponse> 物件，其中依序包含一連串的 <xref:System.Data.Services.Client.EntityDescriptor> 或 <xref:System.Data.Services.Client.LinkDescriptor> 執行個體，表示持續性或嘗試性的變更。 在資料服務中建立或修改實體時，<xref:System.Data.Services.Client.EntityDescriptor> 會包括已更新實體的參考，其中包含任何伺服器產生的屬性值，例如以上範例中產生的 `ProductID` 值。 用戶端程式庫會自動更新 [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] 物件以便擁有這些新值。  
  
 對於成功插入和更新的作業，與作業相關聯的 <xref:System.Data.Services.Client.EntityDescriptor> 或 <xref:System.Data.Services.Client.LinkDescriptor> 物件之狀態屬性會設定為 <xref:System.Data.Services.Client.EntityStates.Unchanged>，而新值則是使用 <xref:System.Data.Services.Client.MergeOption.OverwriteChanges> 來合併。 當資料服務中的插入、更新或刪除作業失敗時，實體狀態會維持不變，與呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 之前相同，而且 <xref:System.Data.Services.Client.OperationResponse.Error%2A> 的 <xref:System.Data.Services.Client.OperationResponse> 屬性會設定為 <xref:System.Data.Services.Client.DataServiceRequestException>，其中包含與該錯誤有關的資訊。 如需詳細資訊，請參閱[更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)。  
  
### <a name="setting-the-http-method-for-updates"></a>設定更新的 HTTP 方法  
 .NET Framework 用戶端程式庫預設會將更新當做 MERGE 要求，傳送到現有的實體。 MERGE 要求會更新選取的實體屬性，不過在 MERGE 要求中，用戶端永遠會加入所有的屬性 (甚至是尚未變更的屬性)。 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 通訊協定也支援傳送 PUT 要求來更新實體。 在 PUT 要求中，現有的實體基本上會從用戶端取代成具有屬性值的新實體執行個體。 若要使用 PUT 要求，請在呼叫 <xref:System.Data.Services.Client.SaveChangesOptions.ReplaceOnUpdate> 時，設定 <xref:System.Data.Services.Client.SaveChangesOptions> 列舉上的 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 旗標。  
  
> [!NOTE]
>  當用戶端不知道實體的所有屬性時，PUT 要求與 MERGE 要求的行為將會有所不同。 將實體型別投影到用戶端上的新型別時，可能會發生這個情況。 將新屬性加入至服務資料模型中的實體，而且 <xref:System.Data.Services.Client.DataServiceContext.IgnoreMissingProperties%2A> 上的 <xref:System.Data.Services.Client.DataServiceContext> 屬性設為 `true` 來忽略此類用戶端對應錯誤時，也可能會發生這個情況。 在這些情況下，PUT 要求會將用戶端不知道的任何屬性重設為其預設值。  
  
### <a name="post-tunneling"></a>POST 通道  
 預設情況下，用戶端程式庫會使用 POST、GET、PUT/MERGE/PATCH 和 DELETE 的對應 HTTP 方法，將建立、讀取、更新和刪除要求傳送給 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務。 這樣做表示支持代表性狀態傳輸 (Representational State Transfer，REST) 的基本原則。 不過，並不是所有 Web 伺服器實作都會支援完整的 HTTP 方法集。 在某些情況下，支援的方法可能僅限於 GET 和 POST。 像防火牆這樣的媒介透過某些方法阻擋要求時，就可能發生這種情況。 由於 GET 和 POST 方法最常受到支援，[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 會使用 POST 要求來規定任何不受支援之 HTTP 方法的執行方式。 又稱為*方法通道*或*POST 通道*，這可讓用戶端傳送 POST 要求，指定在自訂的實際方法`X-HTTP-Method`標頭。 若要啟用 POST 通道以傳送要求，請將 <xref:System.Data.Services.Client.DataServiceContext.UsePostTunneling%2A> 執行個體上的 <xref:System.Data.Services.Client.DataServiceContext> 屬性設定為 `true`。  
  
## <a name="see-also"></a>請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [更新資料服務](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md)  
 [非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)  
 [批次處理作業](../../../../docs/framework/data/wcf/batching-operations-wcf-data-services.md)
