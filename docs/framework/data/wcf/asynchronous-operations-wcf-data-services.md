---
title: 非同步作業 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: 5191f3d03facaafc64f6df494ff90cd0ce1c1988
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75346188"
---
# <a name="asynchronous-operations-wcf-data-services"></a>非同步作業 (WCF 資料服務)
相較於在內部網路中執行的應用程式，Web 應用程式必須可容納用戶端與伺服器之間更高的延遲。 若要優化應用程式的效能和使用者體驗，建議您在透過 Web 存取 WCF Data Services 伺服器時，使用 <xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別的非同步方法。  
  
 雖然 WCF Data Services 伺服器會以非同步方式處理 HTTP 要求，但 WCF Data Services 用戶端程式庫的某些方法是同步的，並且會等到整個要求-回應交換完成後，再繼續執行。 WCF Data Services 用戶端程式庫的非同步方法不會等待此交換完成，而且可以讓您的應用程式在同時維護回應式的使用者介面。  
  
 您可以在 <xref:System.Data.Services.Client.DataServiceContext> 上使用一對方法，並分別以*Begin*和*End*開頭的 <xref:System.Data.Services.Client.DataServiceQuery%601> 類別來執行非同步作業。 *Begin*方法會註冊服務在作業完成時所呼叫的委派。 應該在註冊的委派中呼叫*End*方法，以處理已完成之作業的回呼。 當您呼叫*End*方法來完成非同步作業時，您必須從用來開始作業的相同 <xref:System.Data.Services.Client.DataServiceQuery%601> 或 <xref:System.Data.Services.Client.DataServiceContext> 實例執行此作業。 每個*Begin*方法都會採用可將狀態物件傳遞至回呼的 `state` 參數。 此狀態物件會從回呼提供的 <xref:System.IAsyncResult> 中抓取，並用於呼叫對應的*結束*方法以完成非同步作業。 例如，如果您在執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法，提供 `state` 執行個體做為 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 參數時，<xref:System.Data.Services.Client.DataServiceQuery%601> 會傳回同一個 <xref:System.IAsyncResult> 執行個體。 接著會使用這個 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法，以完成查詢作業。 如需詳細資訊，請參閱[如何：執行非同步資料服務查詢](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)。  
  
> [!NOTE]
> .NET Framework for Silverlight 中提供的用戶端程式庫只支援非同步作業。 如需詳細資訊，請參閱[WCF Data Services （Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))。  
  
 .NET Framework 用戶端程式庫支援下列非同步作業：  
  
|運算|方法|  
|---------------|-------------|  
|執行 <xref:System.Data.Services.Client.DataServiceQuery%601>。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行批次查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|將相關實體載入至 <xref:System.Data.Services.Client.DataServiceContext>。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|將物件的變更儲存於 <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>非同步作業的執行緒考量  
 在多執行緒應用程式中，不一定要在用來呼叫*Begin*方法的相同執行緒上叫用註冊為非同步作業回呼的委派，這會建立初始要求。 在必須于特定執行緒上叫用回呼的應用程式中，您必須明確地將*End*方法的執行（處理回應）封送處理至所需的執行緒。 例如，在以 Windows Presentation Foundation (WPF) 為基礎的應用程式與以 Silverlight 為基礎的應用程式中，必須在 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 物件上使用 <xref:System.Windows.Threading.Dispatcher> 方法將回應封送處理回 UI 執行緒。 如需詳細資訊，請參閱[查詢資料服務（WCF Data Services/Silverlight）](https://docs.microsoft.com/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95))。  
  
## <a name="see-also"></a>請參閱

- [WCF Data Services 用戶端程式庫](wcf-data-services-client-library.md)
