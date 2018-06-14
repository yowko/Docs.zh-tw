---
title: 批次處理作業 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 5284d1a3c2ea95e26eddd9c5617f09f299bda4f3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33357857"
---
# <a name="batching-operations-wcf-data-services"></a>批次處理作業 (WCF 資料服務)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)]支援以批次要求的處理[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]為基礎的服務。 如需詳細資訊，請參閱[OData： 批次處理](http://go.microsoft.com/fwlink/?LinkId=186075)。 在[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]，會使用每個作業<xref:System.Data.Services.Client.DataServiceContext>，例如執行查詢，或儲存變更，正在傳送給資料服務的個別要求的結果。 若要保持作業集的邏輯範圍，您可以明確地定義作業批次。 這可確保批次中的所有作業，會傳送至單一 HTTP 要求中的資料服務，可讓伺服器以不可分割方式，處理作業，並減少往返次數至資料服務。  
  
## <a name="batching-query-operations"></a>批次處理查詢作業  
 若要在單一批次中執行多個查詢，您必須將批次中的每個查詢建立為 <xref:System.Data.Services.Client.DataServiceRequest%601> 類別的個別執行個體。 當您利用這種方式建立查詢要求時，會將查詢本身定義為 URI，而且查詢會遵守定址資源的規則。 如需詳細資訊，請參閱[存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)。 呼叫包含查詢要求物件的 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法時，會將批次的查詢要求傳送至資料服務。 此方法會傳回 <xref:System.Data.Services.Client.DataServiceResponse> 物件，該物件是 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件集合，代表對批次中個別查詢的回應，其中每個物件均包含查詢傳回的物件集合或錯誤訊息。 批次中的任何單一查詢失敗時，該作業的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件中就會傳回與失敗作業相關的錯誤訊息，並且繼續執行其餘作業。 如需詳細資訊，請參閱[如何： 執行查詢批次中](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md)。  
  
 您也可以透過非同步方式執行批次查詢。 如需詳細資訊，請參閱[非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
## <a name="batching-the-savechanges-operation"></a>批次處理 SaveChanges 作業  
 當您呼叫<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>方法，追蹤會轉譯成以 REST 為基礎的作業，用做為傳送內容要求的所有變更[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]服務。 根據預設，這些變更不會在單一要求訊息中傳送。 若需要在單一要求中傳送的所有變更，您必須呼叫<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29>方法，並包含值為<xref:System.Data.Services.Client.SaveChangesOptions.Batch>中<xref:System.Data.Services.Client.SaveChangesOptions>提供給該方法的列舉。  
  
 您也可以透過非同步的方式儲存批次變更。 如需詳細資訊，請參閱[非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
