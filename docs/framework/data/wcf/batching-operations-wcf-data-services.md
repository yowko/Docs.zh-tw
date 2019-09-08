---
title: 批次處理作業 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, client library
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
ms.openlocfilehash: 2a642bdfd6a8891c54c01a07609760bede2f5d5d
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780508"
---
# <a name="batching-operations-wcf-data-services"></a>批次處理作業 (WCF 資料服務)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 支援[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]對服務的要求批次處理。 如需詳細資訊， [請參閱 OData：](https://go.microsoft.com/fwlink/?LinkId=186075)批次處理。 在[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]中，使用的<xref:System.Data.Services.Client.DataServiceContext>每個作業（例如執行查詢或儲存變更）都會導致個別的要求傳送至資料服務。 若要保持作業集的邏輯範圍，您可以明確地定義作業批次。 這可確保批次中的所有作業都會以單一 HTTP 要求傳送至資料服務，讓伺服器以不可部分完成的方式處理作業，並減少資料服務的來回行程次數。  
  
## <a name="batching-query-operations"></a>批次處理查詢作業  
 若要在單一批次中執行多個查詢，您必須將批次中的每個查詢建立為 <xref:System.Data.Services.Client.DataServiceRequest%601> 類別的個別執行個體。 當您利用這種方式建立查詢要求時，會將查詢本身定義為 URI，而且查詢會遵守定址資源的規則。 如需詳細資訊，請參閱[存取資料服務資源](accessing-data-service-resources-wcf-data-services.md)。 呼叫包含查詢要求物件的 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法時，會將批次的查詢要求傳送至資料服務。 此方法會傳回 <xref:System.Data.Services.Client.DataServiceResponse> 物件，該物件是 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件集合，代表對批次中個別查詢的回應，其中每個物件均包含查詢傳回的物件集合或錯誤訊息。 批次中的任何單一查詢失敗時，該作業的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件中就會傳回與失敗作業相關的錯誤訊息，並且繼續執行其餘作業。 如需詳細資訊，請參閱[如何：在批次](how-to-execute-queries-in-a-batch-wcf-data-services.md)中執行查詢。  
  
 您也可以透過非同步方式執行批次查詢。 如需詳細資訊，請參閱[非同步作業](asynchronous-operations-wcf-data-services.md)。  
  
## <a name="batching-the-savechanges-operation"></a>批次處理 SaveChanges 作業  
 當您呼叫<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A>方法時，會將內容追蹤的所有變更轉譯成[!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)]以 REST 為基礎的作業，並以要求的形式傳送至服務。 根據預設，這些變更不會在單一要求訊息中傳送。 若要要求在單一要求中傳送所有變更，您必須呼叫<xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29>方法，並<xref:System.Data.Services.Client.SaveChangesOptions.Batch>在您提供給方法的<xref:System.Data.Services.Client.SaveChangesOptions>列舉中包含的值。  
  
 您也可以透過非同步的方式儲存批次變更。 如需詳細資訊，請參閱[非同步作業](asynchronous-operations-wcf-data-services.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
