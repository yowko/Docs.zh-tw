---
title: 不按照順序的訊息處理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 7d908be84f22835bea744de74d278689516f3185
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54698007"
---
# <a name="out-of-order-message-processing"></a><span data-ttu-id="fcabb-102">不按照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="fcabb-102">Out-of-Order Message Processing</span></span>
<span data-ttu-id="fcabb-103">工作流程服務可能取決於訊息以特定順序傳送。</span><span class="sxs-lookup"><span data-stu-id="fcabb-103">Workflow services may depend on messages being sent in a specific order.</span></span> <span data-ttu-id="fcabb-104">工作流程服務包含一個或多個 <xref:System.ServiceModel.Activities.Receive> 活動，各個 <xref:System.ServiceModel.Activities.Receive> 活動會預期某個特定的訊息。</span><span class="sxs-lookup"><span data-stu-id="fcabb-104">A workflow service contains one or more <xref:System.ServiceModel.Activities.Receive> activities and each <xref:System.ServiceModel.Activities.Receive> activity is expecting a specific message.</span></span> <span data-ttu-id="fcabb-105">要是沒有特定的傳輸傳遞保證，用戶端傳送的訊息可能會延遲，因而傳遞的順序可能不符合工作流程服務的預期。</span><span class="sxs-lookup"><span data-stu-id="fcabb-105">Without particular transport delivery guarantees, messages sent by clients may be delayed and therefore delivered in an order the workflow service may not expect.</span></span> <span data-ttu-id="fcabb-106">實作不要求訊息以特定順序傳送的工作流程服務，通常會使用平行活動來完成。</span><span class="sxs-lookup"><span data-stu-id="fcabb-106">Implementing a workflow service that does not require messages be sent in a specific order is normally done using a Parallel activity.</span></span> <span data-ttu-id="fcabb-107">若為更複雜的應用程式通訊協定，工作流程很快就會變得非常複雜。</span><span class="sxs-lookup"><span data-stu-id="fcabb-107">For a more complicated application protocol, the workflow would become very complex very quickly.</span></span>  <span data-ttu-id="fcabb-108">次序不對的訊息處理功能在 Windows Communication Foundation (WCF) 可讓您建立這類工作流程，而不需要所有的巢狀平行活動的複雜度。</span><span class="sxs-lookup"><span data-stu-id="fcabb-108">The out-of-order message processing feature in Windows Communication Foundation (WCF) allows you to create such a workflow without all of the complexity of nested Parallel activities.</span></span> <span data-ttu-id="fcabb-109">次序不對的訊息處理僅適用於支援的通道上<xref:System.ServiceModel.Channels.ReceiveContext>例如 WCF MSMQ 繫結。</span><span class="sxs-lookup"><span data-stu-id="fcabb-109">Out-of-order message processing is only supported on channels that support <xref:System.ServiceModel.Channels.ReceiveContext> such as the WCF MSMQ bindings.</span></span>  
  
## <a name="enabling-out-of-order-message-processing"></a><span data-ttu-id="fcabb-110">啟用不按照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="fcabb-110">Enabling Out-Of-Order Message Processing</span></span>  
 <span data-ttu-id="fcabb-111">若要啟用不按照順序的訊息處理，請將 WorkflowService 上的 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 屬性設定為 `true`。</span><span class="sxs-lookup"><span data-stu-id="fcabb-111">Out-of-order message processing is enabled by setting the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property to `true` on the WorkflowService.</span></span> <span data-ttu-id="fcabb-112">下列範例示範如何利用程式碼設定 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 屬性。</span><span class="sxs-lookup"><span data-stu-id="fcabb-112">The following example shows how to set the <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> property in code.</span></span>  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 <span data-ttu-id="fcabb-113">您也可以利用 XAML，將 `AllowBufferedReceive` 屬性套用到工作流程服務，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="fcabb-113">You can also apply the `AllowBufferedReceive` attribute to a workflow service in XAML as shown in the following example.</span></span>  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a><span data-ttu-id="fcabb-114">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fcabb-114">See also</span></span>
- <xref:System.ServiceModel.Channels.ReceiveContext>
- [<span data-ttu-id="fcabb-115">工作流程服務</span><span class="sxs-lookup"><span data-stu-id="fcabb-115">Workflow Services</span></span>](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [<span data-ttu-id="fcabb-116">佇列和可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="fcabb-116">Queues and Reliable Sessions</span></span>](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
