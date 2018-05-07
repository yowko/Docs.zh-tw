---
title: 橋接及錯誤處理
ms.date: 03/30/2017
ms.assetid: 4ae87d1a-b615-4014-a494-a53f63ff0137
ms.openlocfilehash: f13a55704422e8a958e55c489f6db11108b03c90
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="bridging-and-error-handling"></a>橋接及錯誤處理
這個範例會示範 Windows Communication Foundation (WCF) 路由服務如何用於通訊的用戶端和服務使用不同繫結之間的橋接。 此範例也會示範如何針對容錯移轉情況使用備份服務。 路由服務是一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件，該元件可讓它在應用程式中輕鬆加入內容架構的路由器。 此範例會調整標準 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 計算機範例，以便使用路由服務進行通訊。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\ErrorHandlingAndBridging`  
  
## <a name="sample-details"></a>範例詳細資料  
 在此範例中，計算機用戶端設定為傳送訊息到路由器所公開的端點。 路由服務會設定為接受傳送給它的所有訊息，並將其轉送到對應於計算機服務的端點。 以下幾點描述主要計算機服務的組態、備份計算機服務與計算機用戶端，以及如何使用路由服務進行用戶端與服務之間的通訊：  
  
-   計算機用戶端設定為使用 BasicHttpBinding，而計算機服務設定為使用 NetTcpBinding。 路由服務會在必要時，先自動轉換訊息，然後再將其傳送至計算機服務，而且它也會轉換回應，讓計算機用戶端可以進行存取。  
  
-   路由服務知道兩個計算機服務：主要計算機服務和備份計算機服務。 路由服務會先嘗試與主要計算機服務端點進行通訊。 如果此嘗試因為端點中斷而失敗，則路由服務會嘗試與備份計算機服務端點進行通訊。  
  
 因此，傳送自用戶端的訊息會由路由器接收，然後再重新路由至實際的計算機服務。 如果計算機服務端點中斷，路由服務會將訊息路由至備份計算機服務端點。 來自備份計算機服務的訊息會傳送回服務路由器，接著再將其傳遞回計算機用戶端。  
  
> [!NOTE]
>  備份清單可以定義多個端點。 在此情況下，如果備份服務端點中斷，路由服務會嘗試連接到清單中的下一個備份端點，直到連線成功為止。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 RouterBridgingAndErrorHandling.sln。  
  
2.  在 Visual Studio 中按下 F5 或 CTRL+SHIFT+B。  
  
    1.  如果您想要按下 F5 時自動啟動必要的專案，以滑鼠右鍵按一下方案，請選取**屬性**，然後在**啟始專案**節點下的**的通用屬性**，選取**多個啟始專案**，並將所有專案都設定為**啟動**。  
  
    2.  如果您使用 CTRL+SHIFT+B 來建置專案，請啟動下列應用程式：  
  
        1.  計算機用戶端 (./CalculatorClient/bin/client.exe)  
  
        2.  計算機服務 (./CalculatorService/bin/service.exe)  
  
        3.  路由服務 (./RoutingService/bin/RoutingService.exe)  
  
3.  在計算機用戶端中，按 ENTER 鍵以啟動用戶端。  
  
     您應該會看到下列輸出：  
  
    ```Output  
    Add(100,15.99) = 115.99  
    Subtract(145,76.54) = 68.46  
    Multiply(9,81.25) = 731.25  
    Divide(22,7) = 3.14285714285714  
    ```  
  
## <a name="configurable-via-code-or-appconfig"></a>可透過程式碼或 App.config 設定  
 此範例預設為使用 App.config 檔案定義路由器的行為。 您也可以將 App.config 檔案的名稱變更為其他任何名稱，讓其無法辨識，而且可以取消註解對 `ConfigureRouterViaCode()` 的方法呼叫。 任一種方法都會在路由器中導致相同的行為。  
  
### <a name="scenario"></a>情節  
 此範例示範當做通訊協定橋接器與錯誤處理常式的服務路由器。 在此案例中，沒有發生內容架構的路由；路由服務會當做傳輸 Proxy 節點，而此節點設定為將訊息直接傳遞到一組預先設定的目的地端點。 路由服務也會執行嘗試傳送到設定為與其進行通訊之端點時所發生的其他透明處理錯誤步驟。 路由服務藉由當做路由橋接器使用，可讓使用者為外部通訊定義一個通訊協定，並為內部通訊定義另一個通訊協定。  
  
### <a name="real-world-scenario"></a>真實情節  
 Contoso 想要在內部最佳化效能時，提供互通的服務端點給外界。 因此，它會在內部使用路由服務將該連線橋接到使用其服務所使用之 NetTcpBinding 的端點時，透過端點使用 BasicHttpBinding，向外界公開其服務。 此外，Contoso 希望提供服務時能夠容許其中任何一個實際執行服務暫時中斷，然後使用錯誤處理功能視覺化路由器服務背後的多個端點，以便在需要時，自動容錯移轉到備份端點。  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
