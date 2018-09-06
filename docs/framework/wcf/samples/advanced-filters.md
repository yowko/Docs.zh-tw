---
title: 進階篩選
ms.date: 03/30/2017
ms.assetid: 8d81590f-e036-4f96-824a-4a187f462764
ms.openlocfilehash: 7022384e8abe93f4276eec48785b3243ed926438
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2018
ms.locfileid: "43805438"
---
# <a name="advanced-filters"></a>進階篩選
這個範例會示範 Windows Communication Foundation (WCF) 的路由服務。 路由服務是一種 WCF 元件，可讓您更輕鬆地在您的應用程式中加入內容為基礎的路由器。 此範例會調整標準的 WCF 計算機範例，以便使用路由服務進行通訊。 此範例示範如何透過訊息篩選與訊息篩選資料表的使用，定義以內容為基礎的路由邏輯。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\RoutingServices\AdvancedFilters`  
  
## <a name="sample-details"></a>範例詳細資料  
 下表顯示加入至路由服務之訊息篩選資料表的訊息篩選。  
  
|篩選器|規則|優先權|  
|------------|----------|--------------|  
|If (有標頭)|四捨五入|2|  
|If (顯示在 Ep2 上)|Regular|1|  
|If (與 Address2 一起顯示)|四捨五入|1|  
|If (RoundRobin1)|Regular|0|  
|If (RoundRobin2)|四捨五入|0|  
  
 您可以透過程式碼或在應用程式組態檔中建立與設定訊息篩選和訊息篩選資料表。 針對這個範例，您可以尋找透過 RoutingService\routing.cs 檔中之程式碼定義的訊息篩選和訊息篩選資料表，或尋找在 RoutingService\App.config 檔中之應用程式組態檔定義的訊息篩選和訊息篩選資料表。 以下段落描述如何透過程式碼建立此範例的訊息篩選和訊息篩選資料表。  
  
 首先，<xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 會尋找自訂標頭。 請注意，<xref:System.ServiceModel.WSHttpBinding> 會導致使用 SOAP 1.2 的封套版本，因此，XPath 陳述式會定義為使用 SOAP 1.2 命名空間。 <xref:System.ServiceModel.Dispatcher.XPathMessageFilter> 的預設命名空間管理員已經為 SOAP 1.2 命名空間定義一個可以使用的前置詞 /s12。 不過，預設命名空間管理員沒有用戶端用來定義實際標頭值的自訂命名空間，因此必須定義該前置詞。 與此標頭一起顯示的任何訊息都符合此篩選。  
  
```  
XPathMessageContext namespaceManager = new XPathMessageContext();  
namespaceManager.AddNamespace("custom", "http://my.custom.namespace/");  
  
XPathMessageFilter xpathFilter = new XPathMessageFilter("/s12:Envelope/s12:Header/custom:RoundingCalculator = 1", namespaceManager);  
```  
  
 第二個篩選是 <xref:System.ServiceModel.Dispatcher.EndpointNameMessageFilter>，這個篩選會比對在 `calculatorEndpoint` 上收到的任何訊息。 建立服務端點物件時，會定義端點名稱。  
  
```  
EndpointNameMessageFilter endpointNameFilter = new EndpointNameMessageFilter("calculatorEndpoint");  
```  
  
 第三個篩選是 <xref:System.ServiceModel.Dispatcher.PrefixEndpointAddressMessageFilter>。 這會比對端點上顯示的任何訊息以及符合提供之位址前置詞 (或前方部分) 的位址。 在此範例中定義的位址前置詞為"http://localhost/routingservice/router/rounding/」。 這表示任何傳入的訊息傳送到 「 http://localhost/routingservice/router/rounding/*"符合此篩選器。 在此情況下，它會顯示在 Rounding Calculator 端點的訊息具有位址"http://localhost/routingservice/router/rounding/calculator」。  
  
```  
PrefixEndpointAddressMessageFilter prefixAddressFilter = new PrefixEndpointAddressMessageFilter(new EndpointAddress("http://localhost/routingservice/router/rounding/"));  
```  
  
 最後兩個訊息篩選是自訂 <xref:System.ServiceModel.Dispatcher.MessageFilter>。 在此範例中，會使用 "RoundRobin" 訊息篩選。 此訊息篩選是在提供的 RoutingService\RoundRobinMessageFilter.cs 檔案中建立的。 設定為相同群組時，這些篩選會輪流報告它們是否符合訊息，因此，一次只有其中一個篩選會回應 `true`。  
  
```  
RoundRobinMessageFilter roundRobinFilter1 = new RoundRobinMessageFilter("group1");  
  
RoundRobinMessageFilter roundRobinFilter2 = new RoundRobinMessageFilter("group1");  
```  
  
 接著，所有這些訊息都會加入到 <xref:System.ServiceModel.Dispatcher.MessageFilterTable%601>。 這樣做時，會指定優先權來影響訊息篩選資料表執行篩選的順序。 優先權越高，執行篩選的順序越前面；優先權越低，執行篩選的順序越後面。 因此，優先權為 2 的篩選會在優先權為 1 的篩選前面執行。 如果未指定優先權層級，則預設優先權層級為 0。 訊息篩選資料表會先在給定的優先權層級執行所有篩選，然後再移到次低的優先權層級。 如果在特定優先權找到相符項目，則訊息篩選資料表不會繼續嘗試在次低優先權尋找相符項目。  
  
> [!NOTE]
>  雖然此範例示範如何使用訊息篩選優先權，但一般而言，設計與設定您的篩選，讓它們不需要排定優先權便可正確運作是更具效能且更好的設計。  
  
 要加入的第一個篩選是 XPath 篩選，且其優先權設定為 2。 這是執行的第一個訊息篩選。 如果此篩選找到自訂標頭，不論其他篩選的結果為何，都會將訊息路由至 Rounding Calculator 端點。  
  
 在優先權 1 會加入兩個篩選。 同樣地，只有在優先權 2 的 XPath 篩選不符合訊息時，才會執行這些篩選。 這兩個篩選會示範兩種不同的方式來判斷訊息顯示時的位址。 由於這兩個篩選會有效地檢查訊息是否到達兩個端點中的一個端點，因此它們可以在相同的優先權層級執行，因為它們不會同時傳回 `true`。  
  
 最後，在優先權 0 (最低的優先權) 會執行 RoundRobin 訊息篩選。 這些篩選是使用相同的群組名稱設定，因此一次只會符合其中一個篩選。 具有自訂標頭的所有訊息都已經路由，而且所有訊息的位址都設定為特定虛擬化端點，因此，RoundRobin 訊息篩選所處理的訊息只有位址為沒有自訂標頭之預設路由器端點的訊息。 這些訊息會針對每個呼叫的訊息切換，因此，一半的作業會前往 Regular Calculator 端點，而另一半的作業則會前往 Rounding Calculator 端點。  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  使用 [!INCLUDE[vs_current_long](../../../../includes/vs-current-long-md.md)] 開啟 AdvancedFilters.sln。  
  
2.  若要開啟 [**方案總管**，選取**方案總管]** 從**檢視**功能表。  
  
3.  在 Visual Studio 中，按下 F5 或 CTRL + SHIFT + B。  
  
    1.  如果您想要按 F5 時自動啟動必要的專案，以滑鼠右鍵按一下方案，然後選取**屬性**。 選取 **啟始專案**下方的節點**通用屬性**的左窗格中。 選取 **多個啟始專案**選項按鈕，並將所有要有的專案設定**開始**動作。  
  
    2.  如果您使用 CTRL+SHIFT+B 來建置專案，就必須啟動下列應用程式：  
  
        1.  計算機用戶端 (./CalculatorClient/bin/client.exe)  
  
        2.  計算機服務 (./CalculatorService/bin/service.exe)  
  
        3.  路由計算機服務 (./RoundingCalcService/bin/service.exe)  
  
        4.  RoutingService (./RoutingService/bin/RoutingService.exe)  
  
4.  在計算機用戶端的主控台視窗中按 ENTER 鍵，以啟動用戶端。 用戶端會傳回一個可從中選擇的目的地端點清單。  
  
5.  輸入端點的對應字母來選擇目的地端點，然後按 ENTER。  
  
6.  接著，用戶端會詢問您是否要加入自訂標頭。 按 Y 表示 [是]；按 N 表示 [否]，然後按 ENTER。  
  
7.  根據您所做的選擇，您應該會看到不同的輸出。  
  
    1.  以下是將自訂標頭加入至訊息時所傳回的輸出。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    2.  以下是選擇沒有自訂標頭之 Rounding Calculator 端點時所傳回的輸出。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.5  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.1  
        ```  
  
    3.  以下是選擇沒有自訂標頭之 Regular Calculator 端點時所傳回的輸出。  
  
        ```Output  
        Add(100,15.99) = 115.99  
        Subtract(145,76.54) = 68. 46  
        Multiply(9,81.25) = 731.25  
        Divide(22,7) = 3.14285714285714  
        ```  
  
    4.  以下是選擇沒有自訂標頭之 Default Router 端點時所傳回的輸出。  
  
        ```Output  
        Add(100,15.99) = 116  
        Subtract(145,76.54) = 68.46  
        Multiply(9,81.25) = 731.3  
        Divide(22,7) = 3.14285714285714  
        ```  
  
8.  計算機服務與四捨五入計算機服務也會列印出針對其個別主控台視窗叫用之作業的記錄檔。  
  
9. 在用戶端主控台視窗中，輸入`quit`按下 ENTER 以結束。  
  
10. 在服務主控台視窗中按 ENTER 鍵，以終止服務。  
  
## <a name="configurable-via-code-or-appconfig"></a>可透過程式碼或 App.config 設定  
 此範例預設為使用 App.config 檔案定義路由器的行為。 您也可以將 RoutingService\App.config 檔案的名稱變更為其他任何名稱，讓其無法辨識，而且可以在 RoutingService\routing.cs 中取消註解對 `ConfigureRouterViaCode()` 的方法呼叫。 任一種方法都會在路由器中導致相同的行為。  
  
### <a name="scenario"></a>情節  
 此範例示範當做以內容為基礎之路由器運作的路由器，此路由器可透過一個端點公開服務的多個類型或實作。  
  
### <a name="real-world-scenario"></a>真實情節  
 Contoso 想要虛擬化其所有服務，僅公開一個端點，透過這個端點可以存取多個不同類型的服務。 在此情況下，它們會利用路由服務以內容為基礎的路由功能，決定應該將傳入要求傳送至何處。  
  
## <a name="see-also"></a>另請參閱  
 [AppFabric 主控與持續性範例](https://go.microsoft.com/fwlink/?LinkId=193961)
