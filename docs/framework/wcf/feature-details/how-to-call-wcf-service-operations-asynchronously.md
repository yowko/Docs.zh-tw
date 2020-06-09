---
title: HOW TO：以非同步方式呼叫 WCF 服務作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 400ed8e5ee8b236e9d0f843f27b7c2112ec28861
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601253"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>HOW TO：以非同步方式呼叫 WCF 服務作業

本文涵蓋用戶端如何以非同步方式存取服務作業。 本文中的服務會實行 `ICalculator` 介面。 用戶端可以透過使用事件驅動的非同步呼叫模型，以非同步方式在這個介面上呼叫作業。 （如需事件架構非同步呼叫模型的詳細資訊，請參閱[使用以事件為基礎的非同步模式進行多執行緒程式設計](../../../standard/asynchronous-programming-patterns/event-based-asynchronous-pattern-eap.md)）。 如需示範如何在服務中以非同步方式執行作業的範例，請參閱[如何：執行非同步服務](../how-to-implement-an-asynchronous-service-operation.md)作業。 如需同步和非同步作業的詳細資訊，請參閱[同步和非同步作業](../synchronous-and-asynchronous-operations.md)。  
  
> [!NOTE]
> 當使用 <xref:System.ServiceModel.ChannelFactory%601> 時，不支援事件驅動非同步呼叫模型。 如需使用進行非同步呼叫的詳細資訊 <xref:System.ServiceModel.ChannelFactory%601> ，請參閱[如何：使用通道處理站以非同步方式呼叫作業](how-to-call-operations-asynchronously-using-a-channel-factory.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>若要以非同步方式呼叫 WCF 服務作業  
  
1. 同時執行[System.servicemodel 中繼資料公用程式工具（Svcutil）](../servicemodel-metadata-utility-tool-svcutil-exe.md)工具與 `/async` 和 `/tcv:Version35` 命令選項，如下列命令所示。  
  
    ```console
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     除了同步和標準委派架構非同步作業之外，這也會產生包含下列各項的 WCF 用戶端類別：  
  
    - 兩個 <`operationName` > `Async` 作業用於以事件為基礎的非同步呼叫方法。 例如：  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    - <表單的作業已完成事件， `operationName` > `Completed` 以用於以事件為基礎的非同步呼叫方法。 例如：  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    - <xref:System.EventArgs?displayProperty=nameWithType>適用于每個作業的類型（格式 <），以 `operationName` > `CompletedEventArgs` 與事件架構非同步呼叫方法搭配使用。 例如：  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2. 在呼叫應用程式中，建立要在非同步作業完成時呼叫的回呼方法，如下列範例程式碼所示。  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3. 在呼叫作業之前，請使用類型 <的新泛型，將 <xref:System.EventHandler%601?displayProperty=nameWithType> `operationName` > `EventArgs` 處理常式方法（在上一個步驟中建立）新增至 <`operationName` > `Completed` 事件。 然後呼叫 <`operationName` > `Async` 方法。 例如：  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>範例  
  
> [!NOTE]
> 事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。 這樣做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。如果您要接收訊息物件做為 `Result` 屬性，並讓傳回值做為該物件的屬性，請使用 `/messageContract` 命令選項。 這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。 然後，所有的內部傳回值都成為回應訊息物件的屬性。  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>請參閱

- [如何：實作非同步服務作業](../how-to-implement-an-asynchronous-service-operation.md)
