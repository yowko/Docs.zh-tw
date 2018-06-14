---
title: 在工作階段中群組佇列訊息
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- queues [WCF]. grouping messages
ms.assetid: 63b23b36-261f-4c37-99a2-cc323cd72a1a
ms.openlocfilehash: 62aa269d138d436824d3c825de9f722490d3b5bd
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491897"
---
# <a name="grouping-queued-messages-in-a-session"></a>在工作階段中群組佇列訊息
Windows Communication Foundation (WCF) 提供可讓您將一組一起進行處理的相關訊息的單一接收應用程式的工作階段。 本身是工作階段一部分的訊息，也必須是屬於相同的異動。 由於所有訊息都屬於相同的異動，所以如果有任何一個訊息無法進行處理，就會回復整個工作階段。 工作階段對於寄不出的信件佇列與有害佇列，會採取類似行為。 針對工作階段在佇列繫結上設定的存留時間 (TTL) 屬性會完整地套用到工作階段。 如果工作階段中只有部分訊息在 TTL 到期之前傳送出去，則整個工作階段將置於寄不出的信件佇列中。 同樣地，當工作階段中的訊息無法從應用程式佇列傳送到應用程式的話，則整個工作階段將置於有害佇列 (如果有的話)。  
  
## <a name="message-grouping-example"></a>訊息群組範例  
 其中一個範例是很有幫助群組訊息時，實作訂單處理應用程式做為 WCF 服務。 例如，用戶端將訂單提交給包含一些項目的應用程式。 接著，用戶端針對每個項目向服務進行呼叫，以便分別傳送每個訊息。 情況可能變成：伺服器 A 收到第一個項目，而伺服器 B 則收到第二個項目。 每次新增一個項目時，負責處理該項目的伺服器就必須找到適當的順序，並將該項目附加上去，如此一來就會變得很沒效率。 就算只有一部伺服器在處理所有要求，效率仍舊可能不彰，因為伺服器必須追蹤目前正在處理的所有訂單，並判斷新增的項目歸屬哪個訂單。 將單一訂單上的所有要求加以群組可大幅簡化此類應用程式的實作。 用戶端應用程式將單一訂單的所有項目傳送到工作階段，這樣一來，當服務處理訂單時，就會立即處理整個工作階段。 \  
  
## <a name="procedures"></a>程序  
  
#### <a name="to-set-up-a-service-contract-to-use-sessions"></a>若要設定服務合約使用工作階段  
  
1.  定義需要工作階段的服務合約。 若要這麼做，請使用 <xref:System.ServiceModel.OperationContractAttribute> 屬性並指定：  
  
    ```  
    SessionMode=SessionMode.Required  
    ```  
  
2.  將合約中的作業標示為單向，因為這些方法無法傳回任何東西。 若要這麼做，請使用 <xref:System.ServiceModel.OperationContractAttribute> 屬性並指定：  
  
    ```  
    [OperationContract(IsOneWay = true)]  
    ```  
  
3.  實作服務合約並指定 `InstanceContextMode` 的 `PerSession`。 這樣只會針對每個工作階段產生服務一次。  
  
    ```  
    [ServiceBehavior(InstanceContextMode=InstanceContextMode.PerSession)]  
    ```  
  
4.  每個服務作業都需要一筆交易。 請使用 <xref:System.ServiceModel.OperationBehaviorAttribute> 屬性來加以指定。 完成交易的作業應該同時將 `TransactionAutoComplete` 設為 `true`。  
  
    ```  
    [OperationBehavior(TransactionScopeRequired = true, TransactionAutoComplete = true)]   
    ```  
  
5.  設定使用系統提供之 `NetMsmqBinding` 繫結的端點。  
  
6.  使用 <xref:System.Messaging> 來建立交易式佇列。 您也可以使用訊息佇列 (MSMQ) 或 MMC 來建立佇列。 如果您要這麼做，請建立交易式佇列。  
  
7.  請使用 <xref:System.ServiceModel.ServiceHost> 來建立服務的服務主機。  
  
8.  開啟服務主機來提供服務。  
  
9. 關閉服務主機。  
  
#### <a name="to-set-up-a-client"></a>若要設定用戶端  
  
1.  建立異動範圍以寫入異動式佇列。  
  
2.  建立 WCF 用戶端會使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)工具。  
  
3.  下訂單。  
  
4.  關閉 WCF 用戶端。  
  
## <a name="example"></a>範例  
  
### <a name="description"></a>描述  
 下列範例提供 `IProcessOrder` 服務以及使用此服務之用戶端的程式碼。 它會顯示 WCF 提供的群組行為所使用的佇列工作階段。  
  
### <a name="code-for-the-service"></a>服務的程式碼  
 [!code-csharp[S_Msmq_Session#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/service.cs#1)]
 [!code-vb[S_Msmq_Session#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/service.vb#1)]  
  
  
  
### <a name="code-for-the-client"></a>用戶端的程式碼  
 [!code-csharp[S_Msmq_Session#3](../../../../samples/snippets/csharp/VS_Snippets_CFX/s_msmq_session/cs/client.cs#3)]
 [!code-vb[S_Msmq_Session#3](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/s_msmq_session/vb/client.vb#3)]  
  
  
  
## <a name="see-also"></a>另請參閱  
 [工作階段和佇列](../../../../docs/framework/wcf/samples/sessions-and-queues.md)  
 [佇列概觀](../../../../docs/framework/wcf/feature-details/queues-overview.md)
