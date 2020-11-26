---
title: 要求-回覆相互關聯
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: da7739af7368cd7ebb55ed0ea2511e10f0bcb3f5
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96239064"
---
# <a name="request-reply-correlation"></a>要求-回覆相互關聯

要求-回復相互關聯可搭配使用， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 以在工作流程服務中執行雙向作業，並使用在 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 另一個 Web 服務中叫用雙向作業的配對來執行雙向作業。 當您在 WCF 服務中叫用雙向作業時，服務可以是傳統的命令式程式碼型 Windows Communication Foundation (WCF) 服務，也可以是工作流程服務。 若要使用要求-回覆相互關聯，則必須使用雙向繫結必須，例如 <xref:System.ServiceModel.BasicHttpBinding>。 無論是叫用或實作雙向作業，初始化相互關聯的步驟都很類似，並且涵蓋於本章節中。  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>在雙向作業中搭配 Receive/SendReply 使用相互關聯  

 在 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 工作流程服務中，會使用配對來執行雙向作業。 執行階段會使用要求-回覆相互關聯，確保回覆分派至正確的呼叫端。 如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> (適用於工作流程服務) 裝載工作流程，則預設的相互關聯初始化就已足夠。 在此案例中， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 工作流程會使用配對，而不需要特定的相互關聯設定。  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
### <a name="explicitly-initializing-request-reply-correlation"></a>明確初始化要求-回覆相互關聯  

 如果有其他並行的雙向作業，則應該明確設定相互關聯。 這可以藉由指定和來 <xref:System.ServiceModel.Activities.CorrelationHandle> 完成 <xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer> ，或將放在 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 中 <xref:System.ServiceModel.Activities.CorrelationScope> 。 在此範例中，會對一組設定要求-回復相互關聯 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 。  
  
```csharp  
Variable<CorrelationHandle> RRHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder",  
    CorrelationInitializers =  
    {  
        new RequestReplyCorrelationInitializer  
        {  
            CorrelationHandle = RRHandle  
        }  
    }  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
// Construct a workflow using StartOrder and ReplyToStartOrder.  
```  
  
 除了明確設定相互關聯之外，也可以使用 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。 <xref:System.ServiceModel.Activities.CorrelationScope> 會提供隱含的 <xref:System.ServiceModel.Activities.CorrelationHandle> 給它所包含的訊息傳遞活動。 在此範例中，會包含在中的 <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply> 配對 <xref:System.ServiceModel.Activities.CorrelationScope> 。 不需要明確的相互關聯組態。  
  
```csharp  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = OrderContractName,  
    OperationName = "StartOrder"  
};  
  
SendReply ReplyToStartOrder = new SendReply  
{  
    Request = StartOrder,  
    Content = … // Contains the return value, if any.  
};  
  
CorrelationScope s = new CorrelationScope  
{  
    Body = new Sequence  
    {  
        Activities =
        {  
            StartOrder,  
            // Activities that create the reply.  
            ReplyToStartOrder  
        }  
    }  
};  
  
// Construct a workflow using the CorrelationScope.  
```  
  
 如果需要其他相互關聯，可以使用個別訊息傳遞活動的 <xref:System.ServiceModel.Activities.Send.CorrelationInitializers%2A> 屬性，透過需要的 `CorrelationInitializer` 型別進行設定。  
  
## <a name="using-correlation-in-a-two-way-operation-with-sendreceivereply"></a>在雙向作業中搭配 Send/ReceiveReply 使用相互關聯  

 雖然活動只能在所裝載的 <xref:System.ServiceModel.Activities.Receive> 工作流程服務中使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> ， <xref:System.ServiceModel.Activities.Send> 但該 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 配對可用於任何必須在 Web 服務上叫用方法的工作流程。 如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程，則適用上一節中所述的預設相互關聯，否則必須使用需要的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 和 <xref:System.ServiceModel.Activities.CorrelationHandle> 明確設定相互關聯，或是使用 <xref:System.ServiceModel.Activities.CorrelationScope> 的隱含控制代碼管理設定相互關聯。  
  
 在具有雙向作業的服務上使用 **加入服務參考** 時，會產生會在 <xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply> 內部包裝 a a a a a a a a a a a a a a a a a a a a a a a 的活動
