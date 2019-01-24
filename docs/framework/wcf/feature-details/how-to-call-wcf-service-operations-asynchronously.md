---
title: HOW TO：以非同步方式呼叫 WCF 服務作業
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
ms.openlocfilehash: 19b09c9ec789419f2774207b051b8ee488b6725d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54625545"
---
# <a name="how-to-call-wcf-service-operations-asynchronously"></a>HOW TO：以非同步方式呼叫 WCF 服務作業
本主題涵蓋用戶端如何能夠非同步地存取服務作業。 本主題中的服務會實作 `ICalculator` 介面。 用戶端可以透過使用事件驅動的非同步呼叫模型，以非同步方式在這個介面上呼叫作業。 (如需事件架構非同步呼叫模型的詳細資訊，請參閱[使用 「 事件架構非同步模式的多執行緒程式設計](https://go.microsoft.com/fwlink/?LinkId=248184))。 如需示範如何在服務中以非同步方式實作作業的範例，請參閱[How to:實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。 如需有關同步和非同步作業的詳細資訊，請參閱 <<c0> [ 同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。  
  
> [!NOTE]
>  當使用 <xref:System.ServiceModel.ChannelFactory%601> 時，不支援事件驅動非同步呼叫模型。 如需進行非同步呼叫使用<xref:System.ServiceModel.ChannelFactory%601>，請參閱[How to:呼叫作業以非同步方式使用通道處理站](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)。  
  
## <a name="procedure"></a>程序  
  
#### <a name="to-call-wcf-service-operations-asynchronously"></a>若要以非同步方式呼叫 WCF 服務作業  
  
1.  執行[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具，同時`/async`而`/tcv:Version35`一起命令選項，如下列命令所示。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     這會產生，除了同步作業和標準委派架構非同步作業，WCF 用戶端類別，其中包含：  
  
    -   兩個 <`operationName` > `Async`與事件架構非同步呼叫方法搭配使用的作業。 例如:   
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   作業已完成事件表單的 <`operationName` > `Completed`與事件架構非同步呼叫方法搭配使用。 例如:   
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   <xref:System.EventArgs?displayProperty=nameWithType> 每個作業的類型 (表單的 <`operationName`>`CompletedEventArgs`) 與事件架構非同步呼叫方法搭配使用。 例如:   
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  在呼叫應用程式中，建立要在非同步作業完成時呼叫的回呼方法，如下列範例程式碼所示。  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  在呼叫作業之前, 使用 新的泛型<xref:System.EventHandler%601?displayProperty=nameWithType>類型的 <`operationName` > `EventArgs`將處理常式方法 （在上一個步驟中所建立的） 新增至 <`operationName` > `Completed`事件。 然後呼叫 <`operationName` > `Async`方法。 例如:   
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## <a name="example"></a>範例  
  
> [!NOTE]
>  事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。 這樣做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。如果您要接收訊息物件做為 `Result` 屬性，並讓傳回值做為該物件的屬性，請使用 `/messageContract` 命令選項。 這會產生一個簽章，此簽章會將回應訊息傳回做為 `Result` 物件的 <xref:System.EventArgs> 屬性。 然後，所有的內部傳回值都成為回應訊息物件的屬性。  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## <a name="see-also"></a>另請參閱
- [如何：實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)
