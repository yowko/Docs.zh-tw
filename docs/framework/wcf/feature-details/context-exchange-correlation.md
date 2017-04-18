---
title: "內容交換相互關聯 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1e2852be-3601-45ae-b507-ccc465d45c60
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# 內容交換相互關聯
內容相互關聯是以 [.NET 內容交換通訊協定規格](http://go.microsoft.com/fwlink/?LinkId=166059)中描述的內容交換機制為基礎。內容相互關聯使用一般熟知的內容標頭或 Cookie，將訊息關聯至正確的執行個體。若要使用內容相互關聯，您必須在提供給 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的端點上使用以內容為基礎的繫結，例如 <xref:System.ServiceModel.BasicHttpContextBinding>、<xref:System.ServiceModel.WSHttpContextBinding> 或 <xref:System.ServiceModel.NetTcpContextBinding>。本主題說明如何在工作流程服務中使用內容相互關聯搭配訊息活動。  
  
## 使用內容相互關聯  
 在用戶端必須重複呼叫某個工作流程服務，而該服務是使用其中一種內容繫結來裝載的時候，就會使用內容相互關聯。這個型別的相互關聯是由工作流程服務中的 <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> 配對進行初始化。內容會與回覆一起傳送回用戶端，然後用戶端會針對服務的後續呼叫，附加這個內容。  
  
### 在工作流程服務中設定內容相互關聯  
 內容相互關聯是使用與回覆初始傳入訊息之 <xref:System.ServiceModel.Activities.SendReply> 活動相關聯的 <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> 初始化。在下列範例中，<xref:System.ServiceModel.Activities.SendReply> 會設定為初始化內容相互關聯。  
  
```csharp  
Variable<string> Item = new Variable<string>();  
Variable<CorrelationHandle> OrderHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IOrderService",  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    CorrelationInitializers =  
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = OrderHandle  
        }  
    }  
};  
```  
  
> [!NOTE]
>  在此範例中，所使用的相互關聯型別實際上有兩種：內容相互關聯與要求\-回覆相互關聯。使用內容相互關聯可將用戶端的呼叫路由傳送至正確的執行個體。<xref:System.ServiceModel.Activities.Receive> 和 <xref:System.ServiceModel.Activities.SendReply> 活動會一起使用要求\-回覆相互關聯來實作這些活動所模型化的雙向作業。在此範例中，只明確設定了內容相互關聯，而且 <xref:System.ServiceModel.Activities.Receive>\/<xref:System.ServiceModel.Activities.SendReply> 配對正在使用預設的要求\-回覆相互關聯，而這項相互關聯是由 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 的隱含 <xref:System.ServiceModel.Activities.CorrelationHandle> 管理提供。在工作流程設計工具中使用 \[**ReceiveAndSendReply**\] 活動範本時，就會明確設定要求\-回覆相互關聯。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]要求\-回覆相互關聯和隱含相互關聯控制代碼管理的詳細資訊，請參閱[要求\-回覆](../../../../docs/framework/wcf/feature-details/request-reply-correlation.md)和[相互關聯概觀](../../../../docs/framework/wcf/feature-details/correlation-overview.md)。[!INCLUDE[crabout](../../../../includes/crabout-md.md)] \[**ReceiveAndSendReply**\] 活動範本的詳細資訊，請參閱 [ReceiveAndSendReply](../Topic/ReceiveAndSendReply%20Template%20Designer.md)。  
  
 工作流程服務中的後續 <xref:System.ServiceModel.Activities.Receive> 活動，可以參考在前一個範例中，由 <xref:System.ServiceModel.Activities.SendReply> 初始化的 <xref:System.ServiceModel.Activities.CorrelationHandle>。  
  
```csharp  
Receive AddItem = new Receive  
{  
    ServiceContractName = "IOrderService",  
    OperationName = "AddItem",  
    CorrelatesWith = OrderHandle  
};  
```  
  
 然後，<xref:System.ServiceModel.Activities.WorkflowServiceHost> 上的端點就會進行設定，並使用以內容為主的繫結，例如 <xref:System.ServiceModel.BasicHttpContextBinding>。  
  
```xml  
<endpoint  
  contract=”IOrderContract”  
  binding = “basicHttpContextBinding”  
  address=”http://localhost:8080/OrderService” />  
```  
  
### 設定工作流程用戶端中的內容相互關聯  
 如果用戶端是另一個工作流程，也必須在用戶端上設定內容相互關聯。在用戶端工作流程上，最初呼叫工作流程服務之 <xref:System.ServiceModel.Activities.Send>\/<xref:System.ServiceModel.Activities.ReceiveReply> 配對的 <xref:System.ServiceModel.Activities.ReceiveReply>，必須利用 <xref:System.ServiceModel.Activities.ContextCorrelationInitializer> 加以設定。  
  
```csharp  
Variable<CorrelationHandle> cchandle = new Variable<CorrelationHandle>();  
Send request = new Send  
{  
    // Activity configuration omitted.  
};  
  
ReceiveReply reply = new ReceiveReply  
{  
    Request = request,  
    CorrelationInitializers =   
    {  
        new ContextCorrelationInitializer  
        {  
            CorrelationHandle = cchandle  
        }  
    }  
};  
```  
  
 初始化相互關聯之後，後續的 <xref:System.ServiceModel.Activities.Send> 活動就可以使用 <xref:System.ServiceModel.Activities.CorrelationHandle> 來叫用同一個服務執行個體上的方法。  
  
```csharp  
Send request2 = new Send  
{  
    CorrelatesWith = cchandle,  
    // Remaining activity configuration omitted.  
};  
```  
  
 請注意，在這些範例中，內容相互關聯已明確設定。如果用戶端工作流程並沒有同時裝載在 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 中，除非這些活動已包含在 <xref:System.ServiceModel.Activities.CorrelationScope> 活動內，否則相互關聯必須明確設定。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]內容相互關聯的詳細資訊，請參閱 [NetContextExchangeCorrelation](http://msdn.microsoft.com/zh-tw/93c74a1a-b9e2-46c6-95c0-c9b0e9472caf) 範例。  
  
 如果正在呼叫工作流程服務的用戶端不是工作流程，只要該用戶端明確傳遞回第一個工作流程服務呼叫傳回的內容，它仍然可以重複呼叫。根據預設，透過在 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 中加入服務參考而產生的 Proxy，將會儲存並傳遞這項內容。