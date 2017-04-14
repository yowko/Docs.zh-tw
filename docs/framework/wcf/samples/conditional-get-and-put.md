---
title: "條件式 Get 和 Put | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 3d22067f-57b8-4e0f-a571-a694512187ae
caps.latest.revision: 8
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 8
---
# 條件式 Get 和 Put
此範例示範如何針對 WCF REST 程式設計模型使用新的條件式擷取和更新應用程式開發介面。條件式擷取和更新最適合資源導向的服務與 REST 服務，因此，此範例會延伸[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例。此範例著重在使用 [!INCLUDE[netfx40_long](../../../../includes/netfx40-long-md.md)] 中引進的新應用程式開發介面，對[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例增加條件式擷取和更新的支援。  
  
## 示範  
 條件式擷取和更新  
  
## 討論  
 此範例中的 WCF 服務會以資源導向和 REST 的方式公開客戶的集合。如需服務實作的詳細描述，請參閱[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例。  
  
 此範例會對[基本資源服務](../../../../docs/framework/wcf/samples/basic-resource-service.md)範例增加條件式擷取和更新功能的支援。條件式擷取和更新使用 HTTP 實體標記與 HTTP If\-None\-Match 和 If\-Match 標頭驗證用戶端是否擁有給定資源的最新實體。不過，實作程式碼以正確剖析 HTTP If\-None\-Match 和 If\-Match 標頭可能很費時而且容易產生錯誤。因此，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 和 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 方法已經加入至可以使用目前 <xref:System.ServiceModel.Web.WebOperationContext> 執行個體存取的 <xref:System.ServiceModel.Web.IncomingWebRequestContext>。此外，`SetETag` 方法已經加入至 <xref:System.ServiceModel.Web.OutgoingWebRequestContext>，讓其更容易傳回有效的實體標記。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 方法可搭配 \[WebGet\] 作業使用。它會採用給定資源的目前實體標記做為 `entityTag` 參數，這個參數可以是 `string`、`int`、`long` 或 `Guid`。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 方法會針對要求的 HTTP If\-None\-Match 標頭，檢查實體標記。如果實體標記存在於 HTTP If\-None\-Match 標頭中，則會擲回狀態碼為「未修改 \(304\)」的 <xref:System.ServiceModel.Web.WebFaultException>，否則會傳回方法。條件式擷取機制可讓用戶端告知伺服器它擁有這個實體，如果用戶端還未擁有這個實體，則僅傳送目前的實體。在服務的 `GetCustomer` 和 `GetCustomers` 作業中，可以看到 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 方法的使用範例。請務必注意，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 的呼叫可能不會傳回。開發人員應該實作此作業，如此可在執行 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 的呼叫之前，就已經知道要求成功，因此，如果 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 的呼叫不存在，服務就會傳送一個具有成功狀態碼的回應。  
  
 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 方法類似於 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 方法。它也會採用給定資源的目前實體標記。不過，在方法設定為 “PUT” 或 “DELETE” 的情況下，它才可以搭配 \[WebInvoke\] 作業使用。<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 方法會針對要求的 HTTP If\-Match 標頭，檢查實體標記。如果實體標記不存在於 HTTP If\-Match 標頭中，則會擲回狀態碼為「前置條件失敗 \(412\)」的 <xref:System.ServiceModel.Web.WebFaultException>。條件式更新機制可讓用戶端告知伺服器它擁有資源的這個實體，如果它所擁有的實體是最新的，則僅允許用戶端變更資源。在服務的 `UpdateCustomer` 和 `DeleteCustomer` 作業中，可以看到 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 方法的使用範例。請務必注意，如同 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalRetrieve%2A> 般，<xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 的呼叫可能不會傳回。開發人員應該實作此作業，如此可在執行 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 的呼叫之前，就已經知道要求成功，因此，如果 <xref:System.ServiceModel.Web.IncomingWebRequestContext.CheckConditionalUpdate%2A> 的呼叫不存在，服務就會以成功狀態碼回應。  
  
 此範例包含在主控台應用程式中執行的自我裝載服務和用戶端。當主控台應用程式執行時，用戶端會對服務發出要求，然後將相關的資訊從回應寫入至主控台視窗。  
  
#### 若要執行範例  
  
1.  開啟「條件式 Get 和 Put」範例的方案。啟動 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 時，您必須以系統管理員身分執行，才能成功執行範例。方法是，以滑鼠右鍵按一下 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 圖示，然後選擇內容功能表中的 \[**以系統管理員身分執行**\]。  
  
2.  按下 CTRL\+SHIFT\+B 建置方案，然後按下 CTRL\+F5 執行主控台應用程式專案。如果在執行此專案時啟用偵錯 \(按下 F5 而非 CTRL\+F5\)，則偵錯工具會在條件式 GET 和 PUT 檢查擲回例外狀況時停止。發生這個狀況時，按下 F5 可繼續執行範例。  
  
3.  主控台視窗隨即出現，並提供執行中服務的 URI，以及執行中服務之 HTML 說明頁的 URI。  
  
4.  當範例執行時，用戶端會對服務傳送要求，然後將回應寫入至主控台視窗。  
  
5.  按下任何按鍵可終止此範例。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。請先檢查下列 \(預設\) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[用於 .NET Framework 4 的 Windows Communication Foundation \(WCF\) 與 Windows Workflow Foundation \(WF\) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Web\ConditionalGetAndPut`