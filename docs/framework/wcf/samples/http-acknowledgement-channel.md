---
title: "HTTP 要求認可通道"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 469f3056-5ef2-4753-8acf-b574d23d83cf
caps.latest.revision: "10"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: bf8e62d99ffc0a7296d83685dfeb15993afff934
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="http-acknowledgement-channel"></a>HTTP 要求認可通道
HTTP 確認通道 (HTTP Acknowledgement Channel) 是層次通道的一個範例，此通道可以變更單向訊息模式，讓服務確認或拒絕傳入訊息，而不會在收到後就自動傳送確認。 HTTP 確認通道也會讓服務延遲確認，直到它可以保證商務層級的訊息將經過處理。  
  
## <a name="demonstrates"></a>示範  
 <xref:System.ServiceModel.Channels.ReceiveContext>，層次通道範例 (HTTP 確認通道)。  
  
## <a name="discussion"></a>討論  
 HTTP 確認通道會實作 <xref:System.ServiceModel.Channels.ReceiveContext> 以便將 HTTP 要求-回覆訊息模式重設為具有延遲確認的單向模式。 服務可以使用這個新模式確保在訊息處理完成之前，透過以 HTTP OK 狀態碼 200 的形式傳送確認處理的訊息沒有封鎖用戶端，也可以透過 HTTP 內部伺服器錯誤狀態碼 500 的形式傳送失敗訊息給用戶端。 例如，將訊息寫入佇列之後，服務可以傳送一個確認，然後以非同步方式繼續處理訊息。 在此案例中，如果在用戶端收到來自服務的確認之前重新傳送每個訊息，可以確保其訊息至少處理過一次。 請注意，如果再沒有任何訊息處理保證的情況下，服務需要透過 HTTP 進行快速的非同步訊息處理，則 <xref:System.ServiceModel.Channels.OneWayBindingElement> 是更適當的選擇。  
  
 在確定訊息是否可以在服務進行處理時，<xref:System.ServiceModel.Channels.ReceiveContext> 用來將訊息保存在妥善的位置。 服務是否可以成功處理訊息是透過在傳送 HTTP OK 狀態碼的 <xref:System.ServiceModel.Channels.ReceiveContext> 物件上呼叫 Complete 而定，而服務是否可以處理訊息，則是透過在傳送 HTTP 內部伺服器錯誤狀態碼的 <xref:System.ServiceModel.Channels.ReceiveContext> 物件上呼叫 `Abandon`’s <xref:System.ServiceModel.Channels.ReceiveContext> 方法而定。  
  
 在此範例中，用戶端是透過傳送員工識別碼來要求處理資訊。 如果在伺服器端收到的員工識別碼大於 50，服務會將 HTTP 狀態碼 500 (內部伺服器錯誤) 傳送回用戶端，否則，它會假設處理可以成功完成，然後將 HTTP 狀態碼 200 (成功) 傳送到用戶端。  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  以系統管理員權限開啟 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)]。  
  
2.  開啟**HttpAckChannel**方案。  
  
3.  啟動的新執行個體**服務**專案中的專案上按一下滑鼠右鍵**方案總管 中**，然後選取**偵錯**，**開始新執行個體**從內容功能表。  
  
4.  啟動的新執行個體**用戶端**專案中的專案上按一下滑鼠右鍵**方案總管 中**，然後選取**偵錯**，和**開始新執行個體**從內容功能表。  
  
5.  一旦服務啟動後，按下用戶端視窗中的 ENTER，讓用戶端傳送訊息給服務。  
  
6.  第一個訊息會在服務上進行處理，然後該服務會將 HTTP OK 狀態碼傳送回用戶端。  
  
7.  第二個訊息不成功，因此服務會將 HTTP 內部伺服器錯誤狀態碼傳送回用戶端，然後在用戶端上引發 <xref:System.ServiceModel.CommunicationException>。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpAckChannel`
