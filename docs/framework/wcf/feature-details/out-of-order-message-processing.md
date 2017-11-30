---
title: "不按照順序的訊息處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 2ffd220babe99661d8b6aaf271a566d415af5eb1
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="a5402-102">不按照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="a5402-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="a5402-103">工作流程服務可能取決於訊息以特定順序傳送。</span><span class="sxs-lookup"><span data-stu-id="a5402-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="a5402-104">工作流程服務包含一個或多個 <xref:System.ServiceModel.Activities.Receive> 活動，各個 <xref:System.ServiceModel.Activities.Receive> 活動會預期某個特定的訊息。</span><span class="sxs-lookup"><span data-stu-id="a5402-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="a5402-105">要是沒有特定的傳輸傳遞保證，用戶端傳送的訊息可能會延遲，因而傳遞的順序可能不符合工作流程服務的預期。</span><span class="sxs-lookup"><span data-stu-id="a5402-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="a5402-106">實作不要求訊息以特定順序傳送的工作流程服務，通常會使用平行活動來完成。</span><span class="sxs-lookup"><span data-stu-id="a5402-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="a5402-107">若為更複雜的應用程式通訊協定，工作流程很快就會變得非常複雜。</span><span class="sxs-lookup"><span data-stu-id="a5402-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="a5402-108">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的不按照順序的訊息處理功能可讓您建立這類工作流程，避免巢狀平行活動的複雜度。</span><span class="sxs-lookup"><span data-stu-id="a5402-108">The out-of-order message processing feature in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="a5402-109">只有在支援 <xref:System.ServiceModel.Channels.ReceiveContext> 的通道 (例如 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ 繫結) 上，才支援不按照順序的訊息處理。</span><span class="sxs-lookup"><span data-stu-id="a5402-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="a5402-110">啟用不按照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="a5402-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="a5402-111">若要啟用不按照順序的訊息處理，請將 WorkflowService 上的 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="a5402-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="a5402-112">下列範例示範如何利用程式碼設定 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="a5402-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="a5402-113">您也可以利用 XAML，將 `AllowBufferedReceive` 屬性套用到工作流程服務，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a5402-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!—the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="a5402-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a5402-114">See Also</span></span>  
 <xref:System.ServiceModel.Channels.ReceiveContext>  
 [<span data-ttu-id="a5402-115">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="a5402-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)  
 [<span data-ttu-id="a5402-116">佇列和可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="a5402-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
