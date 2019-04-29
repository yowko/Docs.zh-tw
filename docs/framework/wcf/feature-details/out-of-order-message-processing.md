---
title: 不按照順序的訊息處理
ms.date: 03/30/2017
ms.assetid: 33fc62a5-5d59-461c-a37a-0e1b51ac763d
ms.openlocfilehash: 4e1864b25a4dbe8192cd5c692c75645bebbb92d2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701238"
---
# <a name="out-of-order-message-processing"></a>不按照順序的訊息處理
工作流程服務可能取決於訊息以特定順序傳送。 工作流程服務包含一個或多個 <xref:System.ServiceModel.Activities.Receive> 活動，各個 <xref:System.ServiceModel.Activities.Receive> 活動會預期某個特定的訊息。 要是沒有特定的傳輸傳遞保證，用戶端傳送的訊息可能會延遲，因而傳遞的順序可能不符合工作流程服務的預期。 實作不要求訊息以特定順序傳送的工作流程服務，通常會使用平行活動來完成。 若為更複雜的應用程式通訊協定，工作流程很快就會變得非常複雜。  次序不對的訊息處理功能在 Windows Communication Foundation (WCF) 可讓您建立這類工作流程，而不需要所有的巢狀平行活動的複雜度。 次序不對的訊息處理僅適用於支援的通道上<xref:System.ServiceModel.Channels.ReceiveContext>例如 WCF MSMQ 繫結。  
  
## <a name="enabling-out-of-order-message-processing"></a>啟用不按照順序的訊息處理  
 若要啟用不按照順序的訊息處理，請將 WorkflowService 上的 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 屬性設定為 `true`。 下列範例示範如何利用程式碼設定 <xref:System.ServiceModel.Activities.WorkflowService.AllowBufferedReceive%2A> 屬性。  
  
```csharp  
// Code: Opt-in to Buffered Receive processing...  
WorkflowService service = new WorkflowService  
{  
    Name="MyService",  
    Body = workflow,  
    AllowBufferedReceive = true  
};  
```  
  
 您也可以利用 XAML，將 `AllowBufferedReceive` 屬性套用到工作流程服務，如下列範例所示。  
  
```xaml  
// Xaml: Opt-in to Buffered Receive processing...  
<WorkflowService AllowBufferedReceive="True">  
   <!--the actual children activities -->  
</Sequence>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Channels.ReceiveContext>
- [工作流程服務](../../../../docs/framework/wcf/feature-details/workflow-services.md)
- [佇列和可靠工作階段](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)
