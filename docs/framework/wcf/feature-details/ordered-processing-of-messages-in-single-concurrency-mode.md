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
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>單一並行模式中訊息的已排序處理
WCF 不保證訊息會處理的順序，除非基礎通道具有工作階段。  比方說，WCF 服務使用 MsmqInputChannel，不是工作階段通道，將無法處理訊息順序。 有某些情況下，開發人員可能想要在訂單處理行為，但不是想要使用工作階段。 本主題說明當服務在單一並行模式中執行時，如何設定這種行為。  
  
## <a name="in-order-message-processing"></a>依照順序的訊息處理  
 名為<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 的新屬性已加入至 <xref:System.ServiceModel.ServiceBehaviorAttribute>。 當 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 設為 true 且 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設為 <xref:System.ServiceModel.ConcurrencyMode.Single> 時，將會依照順序處理傳送至服務的訊息。 下列程式碼片段將說明如何設定這些屬性：  
  
```  
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 如果將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為任何其他值，則會擲回 <xref:System.InvalidOperationException>。  
  
## <a name="see-also"></a>另請參閱

- [工作階段、執行個體與並行](../../../../docs/framework/wcf/feature-details/sessions-instancing-and-concurrency.md)
- [並行](../../../../docs/framework/wcf/samples/concurrency.md)
