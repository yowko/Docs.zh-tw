---
title: 單一並行模式中訊息的已排序處理
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: 785c2953e57eaf967209b0d9e52ab85a3a99c450
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59229715"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="11e8d-102">單一並行模式中訊息的已排序處理</span><span class="sxs-lookup"><span data-stu-id="11e8d-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="11e8d-103">WCF 不保證訊息會處理的順序，除非基礎通道具有工作階段。</span><span class="sxs-lookup"><span data-stu-id="11e8d-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="11e8d-104">比方說，WCF 服務使用 MsmqInputChannel，不是工作階段通道，將無法處理訊息順序。</span><span class="sxs-lookup"><span data-stu-id="11e8d-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="11e8d-105">有某些情況下，開發人員可能想要在訂單處理行為，但不是想要使用工作階段。</span><span class="sxs-lookup"><span data-stu-id="11e8d-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="11e8d-106">本主題說明當服務在單一並行模式中執行時，如何設定這種行為。</span><span class="sxs-lookup"><span data-stu-id="11e8d-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="11e8d-107">依照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="11e8d-107">In-order Message Processing</span></span>  
 <span data-ttu-id="11e8d-108">名為<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 的新屬性已加入至 <xref:System.ServiceModel.ServiceBehaviorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="11e8d-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="11e8d-109">當 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 設為 true 且 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設為 <xref:System.ServiceModel.ConcurrencyMode.Single> 時，將會依照順序處理傳送至服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="11e8d-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="11e8d-110">下列程式碼片段將說明如何設定這些屬性：</span><span class="sxs-lookup"><span data-stu-id="11e8d-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="11e8d-111">如果將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為任何其他值，則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="11e8d-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="11e8d-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="11e8d-112">See also</span></span>

- [<span data-ttu-id="11e8d-113">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="11e8d-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="11e8d-114">並行</span><span class="sxs-lookup"><span data-stu-id="11e8d-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
