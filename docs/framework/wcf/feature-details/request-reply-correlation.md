---
title: 要求-回覆相互關聯
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: c38854ad42ad4dddce5171482f3ddcfe5bd16b61
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="request-reply-correlation"></a>要求-回覆相互關聯
要求-回覆相互關聯會搭配<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組用來實作雙向作業，在工作流程服務與<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>叫用雙向作業中另一個 Web 組服務。 當叫用雙向作業中的 WCF 服務，服務可以是任一個傳統命令式程式碼為基礎的 Windows Communication Foundation (WCF) 服務，或是可以是工作流程服務。 若要使用要求-回覆相互關聯，則必須使用雙向繫結必須，例如 <xref:System.ServiceModel.BasicHttpBinding>。 無論是叫用或實作雙向作業，初始化相互關聯的步驟都很類似，並且涵蓋於本章節中。  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>在雙向作業中搭配 Receive/SendReply 使用相互關聯  
 A <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組用來在工作流程服務中實作雙向作業。 執行階段會使用要求-回覆相互關聯，確保回覆分派至正確的呼叫端。 如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> (適用於工作流程服務) 裝載工作流程，則預設的相互關聯初始化就已足夠。 在此案例中， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組由工作流程，並不需要任何特定相互關聯組態。  
  
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
 如果有其他並行的雙向作業，則應該明確設定相互關聯。 這可藉由指定<xref:System.ServiceModel.Activities.CorrelationHandle>和<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>，或是藉由將<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>內<xref:System.ServiceModel.Activities.CorrelationScope>。 在此範例中，設定要求-回覆相互關聯上<xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組。  
  
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
  
 除了明確設定相互關聯之外，也可以使用 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。 <xref:System.ServiceModel.Activities.CorrelationScope> 會提供隱含的 <xref:System.ServiceModel.Activities.CorrelationHandle> 給它所包含的訊息傳遞活動。 在此範例中， <xref:System.ServiceModel.Activities.Receive> / <xref:System.ServiceModel.Activities.SendReply>組包含在<xref:System.ServiceModel.Activities.CorrelationScope>。 不需要明確的相互關聯組態。  
  
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
 雖然<xref:System.ServiceModel.Activities.Receive>活動只能在裝載的工作流程服務<xref:System.ServiceModel.Activities.WorkflowServiceHost>，<xref:System.ServiceModel.Activities.Send>和<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>組可用於任何必須叫用 Web 服務方法的工作流程。 如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程，則適用上一節中所述的預設相互關聯，否則必須使用需要的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 和 <xref:System.ServiceModel.Activities.CorrelationHandle> 明確設定相互關聯，或是使用 <xref:System.ServiceModel.Activities.CorrelationScope> 的隱含控制代碼管理設定相互關聯。  
  
 當使用**加入服務參考**活動會產生含雙向作業的服務，在該換行<xref:System.ServiceModel.Activities.Send> / <xref:System.ServiceModel.Activities.ReceiveReply>組在內部利用要求/回覆相互關聯的活動，明確指定。
