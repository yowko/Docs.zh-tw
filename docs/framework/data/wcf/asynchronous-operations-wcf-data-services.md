---
title: 非同步作業 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 665e424ada24e5e2990eccde7193a91dc039b265
ms.sourcegitcommit: a885cc8c3e444ca6471348893d5373c6e9e49a47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "44038562"
---
# <a name="asynchronous-operations-wcf-data-services"></a>非同步作業 (WCF 資料服務)
相較於在內部網路中執行的應用程式，Web 應用程式必須可容納用戶端與伺服器之間更高的延遲。 若要最佳化應用程式的效能及使用者經驗，我們建議您在透過 Web 存取 <xref:System.Data.Services.Client.DataServiceContext> 伺服器時，使用 <xref:System.Data.Services.Client.DataServiceQuery%601> 和 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 類別的非同步方法。  
  
 雖然 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 伺服器會非同步處理 HTTP 要求，但是 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫的部分方法還是會同步，而且在繼續執行之前會等候整個要求回應交換完成為止。 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] 用戶端程式庫的非同步方法不會等候此交換完成，且它可讓您的應用程式同一時間維持回應的使用者介面。  
  
 您可以使用上的一組方法來執行非同步作業<xref:System.Data.Services.Client.DataServiceContext>並<xref:System.Data.Services.Client.DataServiceQuery%601>開頭的類別*開始*並*結束*分別。 *開始*方法會註冊服務在作業完成時所呼叫的委派。 *結束*方法應該呼叫在已註冊為處理已完成作業的回呼委派。 當您呼叫*結束*方法來完成非同步作業時，您必須從同一個進行<xref:System.Data.Services.Client.DataServiceQuery%601>或<xref:System.Data.Services.Client.DataServiceContext>您用來開始作業的執行個體。 每個*開始*方法會採用`state`可以將狀態物件傳遞至回呼的參數。 這個狀態物件會從<xref:System.IAsyncResult>，與回呼一起提供，而且用來呼叫對應*端*方法來完成非同步作業。 例如，如果您在執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法，提供 `state` 執行個體做為 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 參數時，<xref:System.Data.Services.Client.DataServiceQuery%601> 會傳回同一個 <xref:System.IAsyncResult> 執行個體。 接著會使用這個 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法，以完成查詢作業。 如需詳細資訊，請參閱 <<c0> [ 如何： 執行非同步資料服務查詢](../../../../docs/framework/data/wcf/how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)。  
  
> [!NOTE]
>  .NET Framework for Silverlight 中提供的用戶端程式庫只支援非同步作業。 如需詳細資訊，請參閱 < [WCF Data Services (Silverlight)](https://go.microsoft.com/fwlink/?LinkID=143149)。  
  
 .NET Framework 用戶端程式庫支援下列非同步作業：  
  
|運算|方法|  
|---------------|-------------|  
|執行 <xref:System.Data.Services.Client.DataServiceQuery%601>。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行批次查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|將相關實體載入至 <xref:System.Data.Services.Client.DataServiceContext>。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|將物件的變更儲存於 <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>非同步作業的執行緒考量  
 在多執行緒應用程式中，叫用委派註冊為非同步作業的回呼時不一定用來呼叫相同執行緒上*開始*方法，以建立初始要求。 應用程式中，回呼必須叫用在特定執行緒上，您必須明確封送處理的執行*結束*方法，用來處理回應，以所需的執行緒。 例如，在以 Windows Presentation Foundation (WPF) 為基礎的應用程式與以 Silverlight 為基礎的應用程式中，必須在 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 物件上使用 <xref:System.Windows.Threading.Dispatcher> 方法將回應封送回 UI 執行緒。 如需詳細資訊，請參閱 <<c0> [ 查詢資料服務 (WCF Data Services/Silverlight)](https://msdn.microsoft.com/library/3a7cdc07-c37e-4da2-b98b-c3763fd0970b)。  
  
## <a name="see-also"></a>另請參閱  
 [WCF Data Services 用戶端程式庫](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
