---
title: 單一並行模式中訊息的已排序處理
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: baba75fe398d974f989acfda7ef7366986f6813b
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598732"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a><span data-ttu-id="4f698-102">單一並行模式中訊息的已排序處理</span><span class="sxs-lookup"><span data-stu-id="4f698-102">Ordered Processing of Messages in Single Concurrency Mode</span></span>
<span data-ttu-id="4f698-103">除非會話基礎通道，否則 WCF 不會保證處理訊息的順序。</span><span class="sxs-lookup"><span data-stu-id="4f698-103">WCF makes no guarantees about the order in which messages are processed, unless the underlying channel is sessionful.</span></span>  <span data-ttu-id="4f698-104">例如，使用 MsmqInputChannel （不是會話通道）的 WCF 服務將無法依序處理訊息。</span><span class="sxs-lookup"><span data-stu-id="4f698-104">For instance, a WCF service that uses MsmqInputChannel, which is not a sessionful channel, will fail to process messages in order.</span></span> <span data-ttu-id="4f698-105">在某些情況下，開發人員可能會想要進行訂單處理行為，但不想使用會話。</span><span class="sxs-lookup"><span data-stu-id="4f698-105">There are some circumstances where a developer may want the in order processing behavior but not want to use sessions.</span></span> <span data-ttu-id="4f698-106">本主題說明當服務在單一並行模式中執行時，如何設定這種行為。</span><span class="sxs-lookup"><span data-stu-id="4f698-106">This topic describes how to configure this behavior when a service is running in Single Concurrency Mode.</span></span>  
  
## <a name="in-order-message-processing"></a><span data-ttu-id="4f698-107">依照順序的訊息處理</span><span class="sxs-lookup"><span data-stu-id="4f698-107">In-order Message Processing</span></span>  
 <span data-ttu-id="4f698-108">名為<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 的新屬性已加入至 <xref:System.ServiceModel.ServiceBehaviorAttribute>。</span><span class="sxs-lookup"><span data-stu-id="4f698-108">A new attribute called <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> has been added to the <xref:System.ServiceModel.ServiceBehaviorAttribute>.</span></span> <span data-ttu-id="4f698-109">當 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 設為 true 且 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設為 <xref:System.ServiceModel.ConcurrencyMode.Single> 時，將會依照順序處理傳送至服務的訊息。</span><span class="sxs-lookup"><span data-stu-id="4f698-109">When <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> is set to true and <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to <xref:System.ServiceModel.ConcurrencyMode.Single> messages sent to the service will be processed in order.</span></span> <span data-ttu-id="4f698-110">下列程式碼片段將說明如何設定這些屬性：</span><span class="sxs-lookup"><span data-stu-id="4f698-110">The following code snippet illustrates how to set these attributes.</span></span>  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 <span data-ttu-id="4f698-111">如果將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為任何其他值，則會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="4f698-111">If <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> is set to any other value, an <xref:System.InvalidOperationException> is thrown.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f698-112">請參閱</span><span class="sxs-lookup"><span data-stu-id="4f698-112">See also</span></span>

- [<span data-ttu-id="4f698-113">工作階段、執行個體與並行</span><span class="sxs-lookup"><span data-stu-id="4f698-113">Sessions, Instancing, and Concurrency</span></span>](sessions-instancing-and-concurrency.md)
- [<span data-ttu-id="4f698-114">並行</span><span class="sxs-lookup"><span data-stu-id="4f698-114">Concurrency</span></span>](../samples/concurrency.md)
