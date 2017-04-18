---
title: "批次作業 (WCF Data Services) | Microsoft Docs"
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
  - "WCF Data Services, 用戶端程式庫"
ms.assetid: 962a49d1-cc11-4b96-bc7d-071dd6607d6c
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# 批次作業 (WCF Data Services)
[!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] 支援以批次方式處理 [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 型服務的要求。  如需詳細資訊，請參閱 [OData：批次處理](http://go.microsoft.com/fwlink/?LinkId=186075)。在 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 中，使用 <xref:System.Data.Services.Client.DataServiceContext> 的每個作業 \(例如，執行查詢或儲存變更\) 都會導致個別的要求傳送至資料服務。  若要保持作業集的邏輯範圍，您可以明確地定義作業批次。  這樣可確保在單一 HTTP 要求中，將批次當中的所有作業傳送至資料服務，讓伺服器能夠以分割方式處理作業，並且減少往返於資料服務的次數。  
  
## 批次處理查詢作業  
 若要在單一批次中執行多個查詢，您必須將批次中的每個查詢建立為 <xref:System.Data.Services.Client.DataServiceRequest%601> 類別的個別執行個體。  當您利用這種方式建立查詢要求時，會將查詢本身定義為 URI，而且查詢會遵守定址資源的規則。  如需詳細資訊，請參閱[存取資料服務資源](../../../../docs/framework/data/wcf/accessing-data-service-resources-wcf-data-services.md)。  呼叫包含查詢要求物件的 <xref:System.Data.Services.Client.DataServiceContext.ExecuteBatch%2A> 方法時，會將批次的查詢要求傳送至資料服務。  此方法會傳回 <xref:System.Data.Services.Client.DataServiceResponse> 物件，該物件是 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件集合，代表對批次中個別查詢的回應，其中每個物件均包含查詢傳回的物件集合或錯誤訊息。  批次中的任何單一查詢失敗時，該作業的 <xref:System.Data.Services.Client.QueryOperationResponse%601> 物件中就會傳回與失敗作業相關的錯誤訊息，並且繼續執行其餘作業。  如需詳細資訊，請參閱[HOW TO：在批次中執行查詢](../../../../docs/framework/data/wcf/how-to-execute-queries-in-a-batch-wcf-data-services.md)。  
  
 您也可以透過非同步方式執行批次查詢。  如需詳細資訊，請參閱[非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
## 批次處理 SaveChanges 作業  
 當您呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%2A> 方法時，會將內容追蹤的所有變更轉譯成以 REST 為基礎的作業，並以要求的形式傳送至  [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] 服務。  根據預設，這些變更不會在單一要求訊息中傳送。  若要在單一要求中傳送所有變更，您必須呼叫 <xref:System.Data.Services.Client.DataServiceContext.SaveChanges%28System.Data.Services.Client.SaveChangesOptions%29> 方法，並在您提供給該方法的 <xref:System.Data.Services.Client.SaveChangesOptions> 列舉中包含 <xref:System.Data.Services.Client.SaveChangesOptions> 的值。  
  
 您也可以透過非同步的方式儲存批次變更。  如需詳細資訊，請參閱[非同步作業](../../../../docs/framework/data/wcf/asynchronous-operations-wcf-data-services.md)。  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)