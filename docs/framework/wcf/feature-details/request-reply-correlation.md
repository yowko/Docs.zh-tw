---
title: 要求-回覆相互關聯
ms.date: 03/30/2017
ms.assetid: cf4379bf-2d08-43f3-9584-dfa30ffcb1f6
ms.openlocfilehash: 34a41a149e740faf0f3816bba2c9bd9b47d4996e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184550"
---
# <a name="request-reply-correlation"></a>要求-回覆相互關聯
請求<xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply>-答覆關聯與一對一起使用，用於在工作流服務中實現雙向操作，以及在另一個<xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>Web 服務中調用雙向操作的對。 在 WCF 服務中調用雙向操作時，該服務可以是傳統的基於命令碼的 Windows 通信基礎 （WCF） 服務，也可以是工作流服務。 若要使用要求-回覆相互關聯，則必須使用雙向繫結必須，例如 <xref:System.ServiceModel.BasicHttpBinding>。 無論是叫用或實作雙向作業，初始化相互關聯的步驟都很類似，並且涵蓋於本章節中。  
  
## <a name="using-correlation-in-a-two-way-operation-with-receivesendreply"></a>在雙向作業中搭配 Receive/SendReply 使用相互關聯  
 <xref:System.ServiceModel.Activities.Receive> /對<xref:System.ServiceModel.Activities.SendReply>用於在工作流服務中實現雙向操作。 執行階段會使用要求-回覆相互關聯，確保回覆分派至正確的呼叫端。 如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> (適用於工作流程服務) 裝載工作流程，則預設的相互關聯初始化就已足夠。 在這種情況下，<xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply>工作流使用對，不需要特定的相關配置。  
  
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
 如果有其他並行的雙向作業，則應該明確設定相互關聯。 這可以通過<xref:System.ServiceModel.Activities.CorrelationHandle>指定 和<xref:System.ServiceModel.Activities.RequestReplyCorrelationInitializer>或 放置<xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply>的內部 來實現。 <xref:System.ServiceModel.Activities.CorrelationScope> 在此示例中，請求-答覆相關性在<xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply>一對上配置。  
  
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
  
 除了明確設定相互關聯之外，也可以使用 <xref:System.ServiceModel.Activities.CorrelationScope> 活動。 <xref:System.ServiceModel.Activities.CorrelationScope> 會提供隱含的 <xref:System.ServiceModel.Activities.CorrelationHandle> 給它所包含的訊息傳遞活動。 在此示例中<xref:System.ServiceModel.Activities.Receive>/<xref:System.ServiceModel.Activities.SendReply>，一對包含在 中<xref:System.ServiceModel.Activities.CorrelationScope>。 不需要明確的相互關聯組態。  
  
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
 雖然活動<xref:System.ServiceModel.Activities.Receive>只能在 託管<xref:System.ServiceModel.Activities.WorkflowServiceHost>的工作流服務中使用，<xref:System.ServiceModel.Activities.Send><xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>並且對可以在必須在 Web 服務上調用方法的任何工作流中使用。 如果使用 <xref:System.ServiceModel.Activities.WorkflowServiceHost> 裝載工作流程，則適用上一節中所述的預設相互關聯，否則必須使用需要的 <xref:System.ServiceModel.Activities.CorrelationInitializer> 和 <xref:System.ServiceModel.Activities.CorrelationHandle> 明確設定相互關聯，或是使用 <xref:System.ServiceModel.Activities.CorrelationScope> 的隱含控制代碼管理設定相互關聯。  
  
 在具有雙向操作的服務中使用 **"添加服務引用"** 時，將組建活動，在內部使用<xref:System.ServiceModel.Activities.Send>/<xref:System.ServiceModel.Activities.ReceiveReply>顯式指定的請求/回復關聯包裝對活動。
