---
title: "進階的錯誤處理"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: ed54b687-78af-4eda-8507-9fd081bdea1a
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7771b9a4d5a6c0fb4349894afd348e9dece27fd9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="advanced-error-handling"></a>進階的錯誤處理
此範例示範 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 路由服務。 路由服務是一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件，該元件可讓它在應用程式中輕鬆加入內容架構的路由器。 此範例示範路由服務如何使用交易和其他更複雜的訊息處理概念，例如多點傳送，以聰明的方式從錯誤中復原。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至 [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4  (適用於 .NET Framework 4 的 Windows Communication Foundation (WCF) 與 Windows Workflow Foundation (WF) 範例)](http://go.microsoft.com/fwlink/?LinkId=150780) ，以下載所有 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 和 [!INCLUDE[wf1](../../../../includes/wf1-md.md)] 範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedErrorHandling`  
  
## <a name="sample-details"></a>範例詳細資料  
 在此範例中，路由服務會設定為從 MSMQ 佇列讀取訊息，並且將此訊息多點傳送至兩個佇列清單。 其中一個清單用於服務佇列，另一個用於記錄佇列。  
  
 根據預設，由於設定路由服務使用的 MSMQ 繫結支援使用交易，因此路由服務會先確保訊息為交易式並且由每個清單的至少一個佇列接收，再向傳入佇列 (`InQ`) 回報訊息已成功路由傳送。 因此，在兩個服務佇列或兩個記錄佇列都無法使用的情況下，路由服務會回報訊息無法路由傳送，且傳入佇列應採取動作。 這個動作包括將訊息移至系統寄不出的信件佇列。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  > [!IMPORTANT]
    >  請先安裝 MSMQ，再執行此範例。 如果未安裝 MSMQ，則會在執行範例時傳回例外狀況訊息。 安裝 MSMQ 的指示，請參閱[安裝訊息佇列 (MSMQ)](http://go.microsoft.com/fwlink/?LinkId=166437)。  
  
     使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 AdvancedErrorHandling.sln。  
  
2.  按**F5**或**CTRL + SHIFT + B**中[!INCLUDE[vs_current_short](../../../../includes/vs-current-short-md.md)]。  
  
    1.  如果您使用 CTRL+SHIFT+B 來建置應用程式，就必須啟動位於 ./RoutingService/bin/debug/RoutingService.exe 的應用程式。  
  
3.  在主控台視窗中按 ENTER 鍵，以啟動用戶端。  
  
4.  用戶端會分別為每個案例的佇列傳回不同的統計資料。  
  
    1.  以下是針對案例 1 傳回的輸出 (沒有錯誤)。  
  
        ```Output  
        The inbound queue has 0 messages.  
        The primary service queue has 1 messages.   
        The backup service queue has 0 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <Enter> to continue  
        ```  
  
    2.  以下是針對案例 3 傳回的輸出 (主要服務和記錄佇列發生錯誤)。  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.   
        The backup service queue has 1 messages.   
        The primary logging queue does not exist.   
        The backup logging queue has 1 messages.   
        Press <ENTER> to continue.  
        ```  
  
    3.  以下是針對案例 4 傳回的輸出 (主要服務佇列及主要和備份記錄佇列發生錯誤)。  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 0 messages.   
        The primary logging queue does not exist.   
        The backup logging queue does not exist.   
        The System Dead Letter queue has 1 messages.   
        Press <ENTER> to Quit.  
        ```  
  
    4.  以下是針對案例 2 傳回的輸出 (主要服務佇列發生錯誤)。  
  
        ```Output  
        The inbound queue has 0 messages.   
        The primary service queue does not exist.  
        The backup service queue has 1 messages.   
        The primary logging queue has 1 messages.   
        The backup logging queue has 0 messages.   
        Press <ENTER> to continue.  
        ```  
  
## <a name="configurable-via-code-or-appconfig"></a>可透過程式碼或 App.config 設定  
 此範例預設為使用 App.config 檔案定義路由器的行為。 您也可以將 RoutingService\App.config 檔案的名稱變更為其他名稱，使其無法辨識，並且將 RoutingService\Program.cs 中 `configDriven` 欄位的值變更為 `false`，以使用程式碼中定義的組態。 任一種方法都會在路由器中導致相同的行為。  
  
### <a name="scenario"></a>情節  
 這個範例示範路由服務可以處理進階訊息處理功能，例如交易和接收內容，以及在正確處理錯誤案例中示範路由服務可以利用這些功能。  
  
### <a name="real-world-scenario"></a>真實情節  
 Contoso 想要透過路由服務使用交易式接收，確保即使在錯誤情況下，所有必要的服務都能接收資訊。 除此之外，他們還希望能夠正確地自動處理錯誤，並且在使用錯誤處理邏輯時，於訊息無法傳遞的情況下回報錯誤。 基於這個目的，他們設定讓路由服務依預期容錯移轉至特定端點，且路由服務會處理錯誤情況，包括在必要時建立、完成和復原/中止異動/接收內容。  
  
## <a name="see-also"></a>請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
