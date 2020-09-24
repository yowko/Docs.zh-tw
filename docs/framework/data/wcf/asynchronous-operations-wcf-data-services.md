---
title: 非同步作業 (WCF 資料服務)
ms.date: 03/30/2017
helpviewer_keywords:
- WCF Data Services, asynchronous operations
- asynchronous operations [WCF Data Services]
- WCF Data Services, client library
ms.assetid: 679644c7-e3fc-422c-b14a-b44b683900d0
ms.openlocfilehash: cf3a81914d78e8f08c06602600ce5dcef4f4d35b
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91191641"
---
# <a name="asynchronous-operations-wcf-data-services"></a>非同步作業 (WCF 資料服務)

相較於在內部網路中執行的應用程式，Web 應用程式必須可容納用戶端與伺服器之間更高的延遲。 若要將應用程式的效能和使用者體驗優化，建議您在透過 <xref:System.Data.Services.Client.DataServiceContext> <xref:System.Data.Services.Client.DataServiceQuery%601> Web 存取 WCF Data Services 伺服器時，使用和類別的非同步方法。  
  
 雖然 WCF Data Services 伺服器會以非同步方式處理 HTTP 要求，但 WCF Data Services 用戶端程式庫的某些方法是同步的，並且等到整個要求-回應交換完成後，再繼續執行。 WCF Data Services 用戶端程式庫的非同步方法不會等候這項交換完成，而且可以讓您的應用程式同時維持回應式使用者介面。  
  
 您可以在 <xref:System.Data.Services.Client.DataServiceContext> 和 <xref:System.Data.Services.Client.DataServiceQuery%601> 分別以 *Begin* 和 *End* 開頭的類別上使用一組方法，以執行非同步作業。 *Begin*方法會在作業完成時，註冊服務所呼叫的委派。 您應該在註冊的委派中呼叫 *End* 方法，以處理已完成之作業的回呼。 當您呼叫 *End* 方法來完成非同步作業時，您必須從 <xref:System.Data.Services.Client.DataServiceQuery%601> 用來開始作業的相同或實例執行此作業 <xref:System.Data.Services.Client.DataServiceContext> 。 每一個 *Begin* 方法都採用 `state` 可將狀態物件傳遞至回呼的參數。 此狀態物件是取自 <xref:System.IAsyncResult> 回呼提供的，用來呼叫對應的 *End* 方法來完成非同步作業。 例如，如果您在執行個體上呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601> 方法，提供 `state` 執行個體做為 <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> 參數時，<xref:System.Data.Services.Client.DataServiceQuery%601> 會傳回同一個 <xref:System.IAsyncResult> 執行個體。 接著會使用這個 <xref:System.Data.Services.Client.DataServiceQuery%601> 執行個體呼叫 <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A> 方法，以完成查詢作業。 如需詳細資訊，請參閱 [如何：執行非同步資料服務查詢](how-to-execute-asynchronous-data-service-queries-wcf-data-services.md)。  
  
> [!NOTE]
> .NET Framework for Silverlight 中提供的用戶端程式庫只支援非同步作業。 如需詳細資訊，請參閱 [WCF Data Services (Silverlight) ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc838234(v=vs.95))。  
  
 .NET Framework 用戶端程式庫支援下列非同步作業：  
  
|作業|方法|  
|---------------|-------------|  
|執行 <xref:System.Data.Services.Client.DataServiceQuery%601>。|-   <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceQuery%601.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecute%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecute%2A>|  
|從 <xref:System.Data.Services.Client.DataServiceContext> 執行批次查詢。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginExecuteBatch%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndExecuteBatch%2A>|  
|將相關實體載入至 <xref:System.Data.Services.Client.DataServiceContext>。|-   <xref:System.Data.Services.Client.DataServiceContext.BeginLoadProperty%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndLoadProperty%2A>|  
|將物件的變更儲存於 <xref:System.Data.Services.Client.DataServiceContext>|-   <xref:System.Data.Services.Client.DataServiceContext.BeginSaveChanges%2A><br />-   <xref:System.Data.Services.Client.DataServiceContext.EndSaveChanges%2A>|  
  
## <a name="threading-considerations-for-asynchronous-operations"></a>非同步作業的執行緒考量  

 在多執行緒應用程式中，不一定會在用來呼叫 *Begin* 方法的相同執行緒上叫用註冊為非同步作業回呼的委派，這會建立初始要求。 在必須于特定執行緒上叫用回呼的應用程式中，您必須明確地將處理回應的 *End* 方法執行封送處理至所需的執行緒。 例如，在以 Windows Presentation Foundation (WPF) 為基礎的應用程式與以 Silverlight 為基礎的應用程式中，必須在 <xref:System.Windows.Threading.Dispatcher.BeginInvoke%2A> 物件上使用 <xref:System.Windows.Threading.Dispatcher> 方法將回應封送處理回 UI 執行緒。 如需詳細資訊，請參閱 [ (WCF Data Services/Silverlight) 查詢資料服務 ](/previous-versions/windows/silverlight/dotnet-windows-silverlight/cc903932(v=vs.95))。  
  
## <a name="see-also"></a>另請參閱

- [WCF 資料服務用戶端程式庫](wcf-data-services-client-library.md)
