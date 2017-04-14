---
title: "非同步作業 (WCF Data Services) | Microsoft Docs"
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
  - "非同步作業 [WCF Data Services]"
  - "WCF Data Services, 非同步作業"
  - "WCF Data Services, 用戶端程式庫"
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# 非同步作業 (WCF Data Services)
相較於在內部網路中執行的應用程式，Web 應用程式必須可容納用戶端與伺服器之間更高的延遲。  若要最佳化應用程式的效能及使用者經驗，我們建議您在透過 Web 存取 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 伺服器時，使用 <xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別的非同步方法。  
  
 雖然 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 伺服器會非同步處理 HTTP 要求，但是 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫的部分方法還是會同步，而且在繼續執行之前會等候整個要求回應交換完成為止。  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫的非同步方法不會等候此交換完成，且它可讓您的應用程式同一時間維持回應的使用者介面。  
  
 您可以在分別以 *Begin* 和 *End* 開頭的 <xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別使用一組方法執行非同步作業。  *Begin* 方法會註冊服務於作業完成時呼叫的委派。  註冊的委派中應會呼叫 *End* 方法，處理已完成作業所發出的回呼。  當您呼叫 *End* 方法來完成非同步作業時，您必須在用於開始作業的同一個 <xref:System.Data.Services.Client.DataServiceQuery%601> 或 <xref:System.Data.Services.Client.DataServiceContext> 執行個體上執行此步驟。  每個 *Begin* 方法都會使用一個可將狀態物件傳遞至回呼的 `state` 參數。  這個狀態物件擷取自隨回呼提供的 <xref:System.IAsyncResult>，並且用於呼叫對應的 *End* 方法來完成非同步作業。  例如，如果您在執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 方法，提供 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體做為 `state` 參數時，<xref:System.IAsyncResult> 會傳回同一個 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體。  接著會使用這個 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法，以完成查詢作業。  如需詳細資訊，請參閱[HOW TO：執行非同步資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)。  
  
> [!NOTE]
>  .NET Framework for Silverlight 中提供的用戶端程式庫只支援非同步作業。  如需詳細資訊，請參閱 [WCF Data Services \(Silverlight\)](http://go.microsoft.com/fwlink/?LinkID=143149)。  
  
 .NET Framework 用戶端程式庫支援下列非同步作業：  
  
|運算|方法|  
|--------|--------|  
|執行 <xref:System.Data.Services.Client.DataServiceQuery%601>。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行批次查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|將相關實體載入至 <xref:System.Data.Services.Client.DataServiceContext>。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|將物件的變更儲存於 <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## 非同步作業的執行緒考量  
 在多執行緒應用程式中，不一定會在用於呼叫 *Begin* 方法 \(即為建立初始要求的方法\) 的執行緒上叫用註冊為非同步作業回呼的委派。  在必須於特定執行緒上叫用回呼的應用程式中，您必須明確地將 *End* 方法的執行 \(用來處理回應\) 封送至所需的執行緒。  例如，在以 Windows Presentation Foundation \(WPF\) 為基礎的應用程式與以 Silverlight 為基礎的應用程式中，必須在 <xref:System.Windows.Threading.Dispatcher> 物件上使用 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 方法將回應封送回 UI 執行緒。  如需詳細資訊，請參閱[Querying the Data Service \(WCF Data Services\/Silverlight\)](http://msdn.microsoft.com/zh-tw/3a7cdc07-c37e-4da2-b98b-c3763fd0970b)。  
  
## 請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)