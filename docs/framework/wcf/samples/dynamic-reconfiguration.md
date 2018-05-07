---
title: 動態重新組態
ms.date: 03/30/2017
ms.assetid: b20786ae-cce6-4f91-b6cb-9cae116faf8b
ms.openlocfilehash: 3783dd79918dc42a5ad6567bb4f3d2d0fe8bc1e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="dynamic-reconfiguration"></a>動態重新組態
這個範例會示範 Windows Communication Foundation (WCF) 路由服務。 路由服務是一個 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 元件，該元件可讓它在應用程式中輕鬆加入內容架構的路由器。 此範例會調整標準 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 計算機範例，以便使用路由服務進行通訊。 此範例示範如何在執行階段以動態方式重新設定路由服務。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\DynamicReconfiguration`  
  
## <a name="sample-details"></a>範例詳細資料  
 為了在執行階段期間以動態方式重新設定路由服務，此範例會每五秒引發一個建立新 <xref:System.ServiceModel.Routing.RoutingConfiguration> 物件的計時器並進行套用。 這個組態會參考 Regular Calculator 端點或 Rounding Calculator 端點。 計算機用戶端應用程式會根據當時路由服務設定為路由到哪個服務而定，從該服務傳回其訊息。  
  
 系統會使用路由服務透過自訂行為以動態方式重新設定的功能。 這個自訂行為會附加一個服務延伸，其中包含每五秒引發的簡易執行緒計時器，這個計時器會導致回呼 `UpdateRules` 方法。 此回呼會建立並套用新的路由組態。 在實際部署中，這個回呼可能會當做其他某些類型事件的結果達成，例如 SQL-Event 通知或 WS-Discovery 公告。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 DynamicReconfiguration.sln。  
  
2.  若要開啟**方案總管 中**，選取**方案總管 中**從**檢視**功能表。  
  
3.  按**F5**或**CTRL + SHIFT + B** Visual Studio 中。  
  
    1.  如果您想要自動啟動必要的專案時按下**F5**，以滑鼠右鍵按一下方案，然後選取**屬性**。 選取**啟始專案**節點下的**通用屬性**的左窗格中。 選取**多個啟始專案**選項按鈕，並將所有的專案設定**啟動**動作。  
  
    2.  如果您使用建置專案**CTRL + SHIFT + B**，您必須啟動下列應用程式：  
  
        1.  計算機用戶端 (./CalculatorClient/bin/client.exe)  
  
        2.  計算機服務 (./CalculatorService/bin/service.exe)  
  
        3.  路由計算機服務 (./RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (./RoutingService/bin/RoutingService.exe)  
  
4.  在計算機用戶端的主控台視窗中，按下 ENTER 啟動用戶端並呼叫計算機服務作業。  
  
     路由服務會將訊息輪流路由至 Rounding Calculator 和 Regular Calculator，因為路由組態每五秒便會動態變更一次。 根據路由服務設定將訊息傳送到哪個端點而定，在用戶端主控台視窗中會有不同的輸出。  
  
5.  重複持續按下 ENTER 超過五秒，然後從服務的結果中觀察變更。  
  
    1.  以下是路由器服務設定為將訊息路由至 Rounding Calculator 服務時所傳回的輸出。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.2  
        Divide(22,7) = 3.1  
        ```  
  
    2.  以下是路由服務設定為將訊息路由至 Regular Calculator 服務時所傳回的輸出。  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
6.  計算機服務與四捨五入計算機服務也會列印出針對其個別主控台視窗叫用之作業的記錄檔。  
  
7.  在用戶端主控台視窗中，輸入"quit"，然後按 ENTER 以結束。  
  
8.  在服務主控台視窗中按 ENTER 鍵，以終止服務。  
  
## <a name="scenario"></a>情節  
 此範例示範當做以內容為基礎之路由器運作的路由器，此路由器可透過一個端點公開服務的多個類型或實作。  
  
### <a name="real-world-scenario"></a>真實情節  
 Contoso 想要虛擬化其所有服務，僅公開一個端點，透過這個端點可以存取多個不同類型的服務。 在此情況下，它們會利用路由服務以內容為基礎的路由功能，決定應該將傳入要求傳送至何處。  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](http://go.microsoft.com/fwlink/?LinkId=193961)
