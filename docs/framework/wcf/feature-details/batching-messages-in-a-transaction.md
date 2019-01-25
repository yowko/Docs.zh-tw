---
title: 批次處理異動中的訊息
ms.date: 03/30/2017
helpviewer_keywords:
- batching messages [WCF]
ms.assetid: 53305392-e82e-4e89-aedc-3efb6ebcd28c
ms.openlocfilehash: a09cbbe8b77523184a3e75b8fd4301ca956d5cd2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54700545"
---
# <a name="batching-messages-in-a-transaction"></a>批次處理異動中的訊息
佇列的應用程式會使用異動來確保訊息的正確性與可靠的傳遞。 不過，異動是昂貴的作業，而且可能大幅降低訊息的處理能力。 要改善訊息處理能力的其中一種方式，就是讓應用程式在單一交易內讀取和處理多個訊息。 效能與復原之間的取捨：隨著批次中訊息數目的增加，交易復原時所需的復原工作量也會增加。 務必注意的是，在交易和工作階段中批次處理訊息之間的差異。 A*工作階段*是一群相關的訊息會由單一應用程式處理，並以單一單位進行認可。 工作階段通常是在有一組相關訊息必須一併處理時使用。 這類工作的範例為線上購物網站。 *批次*來處理多個，不相關的訊息，以增加訊息輸送量。 如需有關工作階段的詳細資訊，請參閱[的工作階段中群組佇列訊息](../../../../docs/framework/wcf/feature-details/grouping-queued-messages-in-a-session.md)。 批次中的訊息同樣是由單一應用程式處理，並且以單一單位進行認可，但是批次中的訊息可能沒有任何關聯性。 將交易中的訊息批次處理是最佳的方法，而且不會改變應用程式執行的方式。  
  
## <a name="entering-batching-mode"></a>進入批次處理模式  
 <xref:System.ServiceModel.Description.TransactedBatchingBehavior> 端點行為會控制批次處理。 將這個端點行為加入至服務端點，則會在交易中的批次訊息告訴 Windows Communication Foundation (WCF)。 並非所有訊息都需要交易，因此只都需要交易的訊息會放在批次，並傳送作業的唯一訊息標示`TransactionScopeRequired`  =  `true`並`TransactionAutoComplete`  =  `true`是視為一個批次。 如果服務合約上的所有作業會使用都標示`TransactionScopeRequired`  =  `false`並`TransactionAutoComplete`  =  `false`，則永遠不會進入批次處理模式。  
  
## <a name="committing-a-transaction"></a>認可異動  
 批次處理的交易會根據下列原則進行認可：  
  
-   `MaxBatchSize`. <xref:System.ServiceModel.Description.TransactedBatchingBehavior> 行為的屬性。 此屬性會決定放入批次中的訊息數目上限。 當到達此數目時，就會認可批次。 這個值並不是一項嚴格的限制，因此可以在收到此訊息數目之前認可批次。  
  
-   `Transaction Timeout`. 在經過 80% 的異動逾時之後，就會認可批次並且建立新批次。 這表示，如果完成異動的指定時間只剩不到 20%，就會認可異動。  
  
-   `TransactionScopeRequired`. 當處理一批訊息，WCF 會尋找具有`TransactionScopeRequired`  =  `false`，它會認可批次，並重新開啟新的批次與第一個訊息回條上`TransactionScopeRequired`  =  `true`和`TransactionAutoComplete` = `true`.  
  
-   如果佇列中已沒有任何訊息，即使尚未到達 `MaxBatchSize` 或尚未經過交易逾時的 80%，仍會認可目前的批次。  
  
## <a name="leaving-batching-mode"></a>離開批次處理模式  
 如果批次中的訊息造成交易中止，則會發生下列步驟：  
  
1.  整個批次的訊息都會復原。  
  
2.  一次讀取一個訊息，直到已讀取的訊息數目超過最大批次大小的兩倍。  
  
3.  重新進入批次處理模式。  
  
## <a name="choosing-the-batch-size"></a>選擇批次大小  
 批次大小視應用程式而定。 經驗判斷通常是達到應用程式最佳批次大小的最佳方式。 不過務必記得，選擇批次大小時，應根據應用程式的實際部署模型選擇大小。 例如，部署應用程式時，如果需要遠端電腦上 SQL 伺服器，而且需要擴展佇列和 SQL 伺服器的異動，則批次大小最好是經過執行此組態後再決定。  
  
## <a name="concurrency-and-batching"></a>並行處理和批次處理  
 若要提升處理能力，您也可以並行處理多個批次。 您可以藉由設定 `ConcurrencyMode.Multiple` 中的 `ServiceBehaviorAttribute`，啟用並行批次處理。  
  
 *服務節流*是用來指出多少的最大並行呼叫可在服務上的服務行為。 搭配批次處理使用時，這種行為會解譯為可以同時執行的批次數。 如果未設定服務節流，WCF 就會預設為 16 的最大並行呼叫。 因此，如果預設會加入批次處理行為，則最多有 16 個批次可以同時為作用中。 建議您最好根據容量調整服務節流和批次處理。 例如，如果佇列擁有 100 個訊息，而一個批次需要 20 個，那麼將同步呼叫數的上限設為 16 便不實際，因為根據處理能力，可以有 16 個異動是作用中的，所以這相當於是未啟動批次處理。 因此在調整效能時，可選擇不要同步批次處理，或是使用正確的服務節流大小搭配同步批次處理。  
  
## <a name="batching-and-multiple-endpoints"></a>批次處理和多個端點  
 端點是由位址和合約所組成。 因此可能會有多個端點共用同一個繫結。 兩個端點可以共用同一個繫結，並且接聽統一資源識別元 (URI) 或佇列位址。 如果兩個端點從同一個佇列讀取，而且交易的批次處理行為會加入至這兩個端點，則指定的批次大小可能會發生衝突。 這種情況可藉由使用在兩個交易批次處理行為之間所指定的最小批次大小，實作批次處理的方式予以解決。 在此案例中，如果其中一個端點未指定交易的批次處理，則兩個端點都不會使用批次處理。  
  
## <a name="example"></a>範例  
 以下範例將示範如何在組態檔中指定 `TransactedBatchingBehavior`。  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="TransactedBatchingBehavior"
              maxBatchSize="100" />
  </endpointBehaviors>
</behaviors>
```  
  
 以下範例將示範如何在程式碼中指定 <xref:System.ServiceModel.Description.TransactedBatchingBehavior>。  
  
```csharp
using (ServiceHost serviceHost = new ServiceHost(typeof(OrderProcessorService)))
{
     ServiceEndpoint sep = ServiceHost.AddServiceEndpoint(typeof(IOrderProcessor), new NetMsmqBinding(), "net.msmq://localhost/private/ServiceModelSamplesTransacted");
     sep.Behaviors.Add(new TransactedBatchingBehavior(100));
     
     // Open the ServiceHost to create listeners and start listening for messages.
    serviceHost.Open();
  
    // The service can now be accessed.
    Console.WriteLine("The service is ready.");
    Console.WriteLine("Press <ENTER> to terminate service.");
    Console.WriteLine();
    Console.ReadLine();
  
    // Close the ServiceHostB to shut down the service.
    serviceHost.Close();
}  
```  
  
## <a name="see-also"></a>另請參閱
- [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)
- [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
