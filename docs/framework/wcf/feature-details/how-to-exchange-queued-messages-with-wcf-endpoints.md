---
title: "HOW TO：與 WCF 端點交換佇列訊息"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 938e7825-f63a-4c3d-b603-63772fabfdb3
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 4b52fe96bc88f09b807640dedcc54a8468dc26e0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-exchange-queued-messages-with-wcf-endpoints"></a>HOW TO：與 WCF 端點交換佇列訊息
佇列可確保用戶端與 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務之間發生可靠的傳訊，即使服務在通訊時無法使用也一樣。 下列程序顯示如何在實作 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務時，使用標準佇列繫結確保在用戶端與服務間建立永久性通訊。  
  
 此章節解釋如何在 <xref:System.ServiceModel.NetMsmqBinding> 用戶端與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 處理佇列通訊。  
  
### <a name="to-use-queuing-in-a-wcf-service"></a>若要在 WCF 服務中使用佇列  
  
1.  使用以 <xref:System.ServiceModel.ServiceContractAttribute>標記的介面定義服務合約。 在屬於服務合約部分的介面中標示作業為 <xref:System.ServiceModel.OperationContractAttribute> 並指定它們為單向，因為此方法不用傳回任何回應。 下列程式碼提供範例服務合約以及其作業定義。  
  
     [!code-csharp[S_Msmq_Transacted#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#1)]
     [!code-vb[S_Msmq_Transacted#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#1)]  
  
2.  當服務合約通過使用者定義型別，您必須為這些型別定義資料合約。 下列程式碼示範兩份資料合約：`PurchaseOrder` 和 `PurchaseOrderLineItem`。 這兩個型別定義了傳送至服務的資料  (請注意，定義這類資料合約的類別也定義許多方法。 這些方法不被視為資料合約的部分。 只有以 `DataMember` 屬性宣告的成員才屬於資料合約的部分)。  
  
     [!code-csharp[S_Msmq_Transacted#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#2)]
     [!code-vb[S_Msmq_Transacted#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#2)]  
  
3.  實作在類別中之介面所定義的服務合約方法。  
  
     [!code-csharp[S_Msmq_Transacted#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#3)]
     [!code-vb[S_Msmq_Transacted#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#3)]  
  
     請注意，<xref:System.ServiceModel.OperationBehaviorAttribute> 放置在 `SubmitPurchaseOrder` 方法上。 其用意是指定必須在交易內呼叫此作業，而且交易會隨著方法完成而自動完成。  
  
4.  使用 <xref:System.Messaging> 來建立交易式佇列。 您可以選擇使用 Microsoft Message Queuing (MSMQ) Microsoft Management Console (MMC) 建立佇列。 若是這樣，請確定您建立異動式佇列。  
  
     [!code-csharp[S_Msmq_Transacted#4](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#4)]
     [!code-vb[S_Msmq_Transacted#4](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#4)]  
  
5.  在組態中定義 <xref:System.ServiceModel.Description.ServiceEndpoint>，以指定服務位址，並使用標準 <xref:System.ServiceModel.NetMsmqBinding> 繫結。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]使用[!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]組態，請參閱[設定的 Windows Communication Foundation 應用程式](http://msdn.microsoft.com/en-us/13cb368e-88d4-4c61-8eed-2af0361c6d7a)。  
  
  
  
6.  使用從佇列讀取訊息並加以處理的 `OrderProcessing` 建立 <xref:System.ServiceModel.ServiceHost> 服務的主機。 開啟服務主機來提供服務。 顯示一則訊息，指示使用者按任意鍵終止服務。 呼叫 `ReadLine` 以等待按鍵動作，隨後關閉服務。  
  
     [!code-csharp[S_Msmq_Transacted#6](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#6)]
     [!code-vb[S_Msmq_Transacted#6](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#6)]  
  
### <a name="to-create-a-client-for-the-queued-service"></a>若要建立佇列服務的用戶端  
  
1.  下列範例示範如何執行裝載應用程式，以及使用 Svcutil.exe 工具建立 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端。  
  
    ```  
    svcutil http://localhost:8000/ServiceModelSamples/service  
    ```  
  
2.  在組態中定義 <xref:System.ServiceModel.Description.ServiceEndpoint>，藉以指定位址並使用標準 <xref:System.ServiceModel.NetMsmqBinding> 繫結，如下列範例所示。  
  
  
  
3.  建立交易範圍以寫入交易式佇列、呼叫 `SubmitPurchaseOrder` 作業和關閉 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端，如下列範例所示。  
  
     [!code-csharp[S_Msmq_Transacted#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#8)]
     [!code-vb[S_Msmq_Transacted#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#8)]  
  
## <a name="example"></a>範例  
 以下內容顯示本範例所囊括的服務程式碼、裝載應用程式、App.config 檔案和用戶端程式碼。  
  
 [!code-csharp[S_Msmq_Transacted#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/service.cs#9)]
 [!code-vb[S_Msmq_Transacted#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/service.vb#9)]  
  
 [!code-csharp[S_Msmq_Transacted#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/hostapp.cs#10)]
 [!code-vb[S_Msmq_Transacted#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/hostapp.vb#10)]  
  
  
  
 [!code-csharp[S_Msmq_Transacted#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_transacted/cs/client.cs#12)]
 [!code-vb[S_Msmq_Transacted#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_transacted/vb/client.vb#12)]  
  
  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.ServiceModel.NetMsmqBinding>  
 [交易的 MSMQ 繫結](../../../../docs/framework/wcf/samples/transacted-msmq-binding.md)  
 [WCF 中的佇列](../../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)  
 [如何： 與 WCF 端點交換訊息和訊息佇列應用程式](../../../../docs/framework/wcf/feature-details/how-to-exchange-messages-with-wcf-endpoints-and-message-queuing-applications.md)  
 [Windows Communication Foundation 至訊息佇列](../../../../docs/framework/wcf/samples/wcf-to-message-queuing.md)  
 [安裝訊息佇列 (MSMQ)](../../../../docs/framework/wcf/samples/installing-message-queuing-msmq.md)  
 [訊息佇列整合繫結範例](http://msdn.microsoft.com/en-us/997d11cb-f2c5-4ba0-9209-92843d4d0e1a)  
 [訊息佇列至 Windows Communication Foundation](../../../../docs/framework/wcf/samples/message-queuing-to-wcf.md)  
 [透過訊息佇列的訊息安全性](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
