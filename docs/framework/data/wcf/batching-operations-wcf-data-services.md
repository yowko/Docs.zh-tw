---
title: 批次處理作業 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 95524c1397172e645d682a6ef3f03b17bb3a639d
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166062"
---
# <a name="batching-operations-wcf-data-services"></a>批次處理作業 (WCF 資料服務)

開放式資料通訊協定 (OData) 支援將要求批次處理至 OData 型服務。 如需詳細資訊，請參閱 [OData：批次處理](https://www.odata.org/documentation/odata-version-2-0/batch-processing/)。 在 WCF Data Services 中，使用的每個作業 <xref:System.Data.Services.Client.DataServiceContext> （例如執行查詢或儲存變更）都會產生個別的要求以傳送至資料服務。 若要保持作業集的邏輯範圍，您可以明確地定義作業批次。 這樣可確保在單一 HTTP 要求中，將批次當中的所有作業傳送至資料服務，讓伺服器能夠以分割方式處理作業，並且減少往返於資料服務的次數。  
  
## <a name="batching-query-operations"></a>批次處理查詢作業  

 若要在單一批次中執行多個查詢，您必須將批次中的每個查詢建立為 <xref:System.Data.Services.Client.DataServiceRequest%601> 類別的個別執行個體。 當您利用這種方式建立查詢要求時，會將查詢本身定義為 URI，而且查詢會遵守定址資源的規則。 如需詳細資訊，請參閱 [存取資料服務資源](accessing-data-service-resources-wcf-data-services.md)。 呼叫包含查詢要求物件的 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法時，會將批次的查詢要求傳送至資料服務。 此方法會傳回 <xref:System.Data.Services.Client.DataServiceResponse> 物件，該物件是 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件集合，代表對批次中個別查詢的回應，其中每個物件均包含查詢傳回的物件集合或錯誤訊息。 批次中的任何單一查詢失敗時，該作業的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件中就會傳回與失敗作業相關的錯誤訊息，並且繼續執行其餘作業。 如需詳細資訊，請參閱 [如何：在批次中執行查詢](how-to-execute-queries-in-a-batch-wcf-data-services.md)。  
  
 您也可以透過非同步方式執行批次查詢。 如需詳細資訊，請參閱 [非同步作業](asynchronous-operations-wcf-data-services.md)。  
  
## <a name="batching-the-savechanges-operation"></a>批次處理 SaveChanges 作業  

 當您呼叫方法時，會將 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 內容追蹤的所有變更轉譯成以 REST 為基礎的作業，並以要求的形式傳送至 OData 服務。 根據預設，這些變更不會在單一要求訊息中傳送。 若要要求所有變更都必須在單一要求中傳送，您必須呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> 方法，並 <xref:System.Data.Services.Client.SaveChangesOptions.Batch> 在 <xref:System.Data.Services.Client.SaveChangesOptions> 您提供給方法的列舉中包含值。  
  
 您也可以透過非同步的方式儲存批次變更。 如需詳細資訊，請參閱 [非同步作業](asynchronous-operations-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
