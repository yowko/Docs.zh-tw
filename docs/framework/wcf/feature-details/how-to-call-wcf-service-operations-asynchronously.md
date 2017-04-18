---
title: "HOW TO：以非同步方式呼叫 WCF 服務作業 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0face17f-43ca-417b-9b33-737c0fc360df
caps.latest.revision: 18
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 18
---
# HOW TO：以非同步方式呼叫 WCF 服務作業
本主題涵蓋用戶端如何能夠非同步地存取服務作業。本主題中的服務會實作 `ICalculator` 介面。用戶端可以透過使用事件驅動的非同步呼叫模型，以非同步方式在這個介面上呼叫作業。\(如需事件架構的非同步呼叫模型的詳細資訊，請參閱[使用事件架構非同步模式設計多執行緒程式](http://go.microsoft.com/fwlink/?LinkId=248184)\)。如需示範如何在服務中以非同步方式實作作業的範例，請參閱 [HOW TO：實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)。如需同步與非同步作業的詳細資訊，請參閱[同步和非同步作業](../../../../docs/framework/wcf/synchronous-and-asynchronous-operations.md)。  
  
> [!NOTE]
>  當使用 <xref:System.ServiceModel.ChannelFactory%601> 時，不支援事件驅動非同步呼叫模型。如需使用 <xref:System.ServiceModel.ChannelFactory%601> 進行非同步呼叫的詳細資訊，請參閱 [HOW TO：使用通道處理站以非同步方式呼叫作業](../../../../docs/framework/wcf/feature-details/how-to-call-operations-asynchronously-using-a-channel-factory.md)。  
  
## 程序  
  
#### 若要以非同步方式呼叫 WCF 服務作業  
  
1.  配合 `/async` 和 `/tcv:Version35` 命令選項執行 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 工具，如下列命令所示。  
  
    ```  
    svcutil /n:http://Microsoft.ServiceModel.Samples,Microsoft.ServiceModel.Samples http://localhost:8000/servicemodelsamples/service/mex /a /tcv:Version35  
    ```  
  
     除了同步作業和標準委派架構非同步作業外，這還會產生包含下列內容的 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端類別：  
  
    -   兩個 \<`operationName`\>`Async` 作業，可與事件架構非同步呼叫方法一起使用。例如：  
  
         [!code-csharp[EventAsync#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#1)]
         [!code-vb[EventAsync#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#1)]  
  
    -   \<`operationName`\>`Completed` 格式的作業完成事件，可與事件架構非同步呼叫方法一起使用。例如：  
  
         [!code-csharp[EventAsync#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#2)]
         [!code-vb[EventAsync#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#2)]  
  
    -   每個作業的 <xref:System.EventArgs?displayProperty=fullName> 型別 \(格式為 \<`operationName`\>`CompletedEventArgs`\)，可與事件架構非同步呼叫方法一起使用。例如：  
  
         [!code-csharp[EventAsync#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/generatedclient.cs#3)]
         [!code-vb[EventAsync#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/generatedclient.vb#3)]  
  
2.  在呼叫應用程式中，建立要在非同步作業完成時呼叫的回呼方法，如下列範例程式碼所示。  
  
     [!code-csharp[EventAsync#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#4)]
     [!code-vb[EventAsync#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#4)]  
  
3.  在呼叫作業之前，先使用型別為 \<`operationName`\>`EventArgs` 的新泛型 <xref:System.EventHandler%601?displayProperty=fullName>，將處理常式方法 \(在上述步驟中建立\) 加入至 \<`operationName`\>`Completed` 事件。接著，呼叫 \<`operationName`\>`Async` 方法。例如：  
  
     [!code-csharp[EventAsync#5](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#5)]
     [!code-vb[EventAsync#5](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#5)]  
  
## 範例  
  
> [!NOTE]
>  事件架構非同步模型的設計方針指出，如果傳回多個值，則其中一個值會傳回做為 `Result` 屬性，其他值則傳回做為 <xref:System.EventArgs> 物件上的屬性。這樣做的結果就是，如果用戶端使用事件架構非同步命令選項匯入中繼資料，且作業傳回多個值，則預設 <xref:System.EventArgs> 物件會傳回一個值做為 `Result` 屬性，而其餘則做為 <xref:System.EventArgs> 物件的屬性。如果您要接收訊息物件做為 `Result` 屬性，並讓傳回值做為該物件的屬性，請使用 `/messageContract` 命令選項。這會產生一個簽章，此簽章會將回應訊息傳回做為 <xref:System.EventArgs> 物件的 `Result` 屬性。然後，所有的內部傳回值都成為回應訊息物件的屬性。  
  
 [!code-csharp[EventAsync#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/eventasync/cs/client.cs#6)]
 [!code-vb[EventAsync#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/eventasync/vb/client.vb#6)]  
  
## 請參閱  
 [HOW TO：實作非同步服務作業](../../../../docs/framework/wcf/how-to-implement-an-asynchronous-service-operation.md)