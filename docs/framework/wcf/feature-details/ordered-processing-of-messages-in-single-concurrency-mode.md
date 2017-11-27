---
title: "單一並行模式中訊息的已排序處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: a1acf4c3edb51500c2ead2e4ba33c6d3cc9c953f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="b3811-102">單一並行模式中訊息的已排序處理</span><span class="sxs-lookup"><span data-stu-id="b3811-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="b3811-103">除非基礎通道工作階段，WCF 可讓其訊息的處理的順序，不保證。</span><span class="sxs-lookup"><span data-stu-id="b3811-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="b3811-104">比方說，WCF 服務使用 MsmqInputChannel，不是工作階段通道，將無法處理訊息順序。</span><span class="sxs-lookup"><span data-stu-id="b3811-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="b3811-105">有某些情況下，其中的開發人員可能想要在訂單處理行為，但不是想要使用工作階段。</span><span class="sxs-lookup"><span data-stu-id="b3811-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="b3811-106">本主題說明當服務在單一並行模式中執行時，如何設定這種行為。</span><span class="sxs-lookup"><span data-stu-id="b3811-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="b3811-107">依照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="b3811-107">In-order Message Processing</span></span>  
 <span data-ttu-id="b3811-108">名為<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 的新屬性已加入至 <xref:System.ServiceModel.ServiceBehaviorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="b3811-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="b3811-109">當 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 設為 true 且 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設為 <xref:System.ServiceModel.ConcurrencyMode.Single> 時，將會依照順序處理傳送至服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="b3811-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="b3811-110">下列程式碼片段將說明如何設定這些屬性：</span><span class="sxs-lookup"><span data-stu-id="b3811-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="b3811-111">如果將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為任何其他值，則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="b3811-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b3811-112">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b3811-112">See Also</span></span>  
 [<span data-ttu-id="b3811-113">工作階段中，執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="b3811-113">Sessions, Instancing, and Concurrency</span></span>](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)  
 [<span data-ttu-id="b3811-114">並行</span><span class="sxs-lookup"><span data-stu-id="b3811-114">Concurrency</span></span>](../../../../docs/framework/wcf/samples/concurrency.md)
