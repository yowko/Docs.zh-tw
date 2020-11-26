---
title: 單一並行模式中訊息的已排序處理
ms.date: 03/30/2017
ms.assetid: a90f5662-a796-46cd-ae33-30a4072838af
ms.openlocfilehash: d70087a6dc1501f9a7f7ed057eae3dad181761ae
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96248015"
---
# <a name="ordered-processing-of-messages-in-single-concurrency-mode"></a>單一並行模式中訊息的已排序處理

除非會話基礎通道，否則 WCF 不保證處理訊息的順序。  比方說，使用 MsmqInputChannel 的 WCF 服務（不是會話通道）將無法依序處理訊息。 在某些情況下，開發人員可能會想要依序處理行為，但不想使用會話。 本主題說明當服務在單一並行模式中執行時，如何設定這種行為。  
  
## <a name="in-order-message-processing"></a>依照順序的訊息處理  

 名為<xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 的新屬性已加入至 <xref:System.ServiceModel.ServiceBehaviorAttribute>。 當 <xref:System.ServiceModel.ServiceBehaviorAttribute.EnsureOrderedDispatch%2A> 設為 true 且 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設為 <xref:System.ServiceModel.ConcurrencyMode.Single> 時，將會依照順序處理傳送至服務的訊息。 下列程式碼片段將說明如何設定這些屬性：  
  
```csharp
[ServiceBehavior(ConcurrencyMode = ConcurrencyMode.Single, EnsureOrderedDispatch = true )]  
    class Service : IService  
    {  
         // ...  
    }  
```  
  
 如果將 <xref:System.ServiceModel.ServiceBehaviorAttribute.ConcurrencyMode%2A> 設定為任何其他值，則會擲回 <xref:System.InvalidOperationException>。  
  
## <a name="see-also"></a>另請參閱

- [工作階段、執行個體與並行](sessions-instancing-and-concurrency.md)
- [並行](../samples/concurrency.md)
