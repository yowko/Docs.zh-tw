---
title: HttpCookieSession
ms.date: 03/30/2017
ms.assetid: 101cb624-8303-448a-a3af-933247c1e109
ms.openlocfilehash: 64a7cba7b1bbc55a4504e3af4784fcb2a84f0fa1
ms.sourcegitcommit: 15109844229ade1c6449f48f3834db1b26907824
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2018
ms.locfileid: "33807224"
---
# <a name="httpcookiesession"></a>HttpCookieSession
這個範例會示範如何建置自訂通訊協定通道，以便在工作階段管理使用 HTTP Cookie。 這個通道可以啟用 Windows Communication Foundation (WCF) 服務和 ASMX 用戶端或 WCF 用戶端與 ASMX 服務之間的通訊。  
  
 當用戶端在工作階段架構 ASMX Web 服務中呼叫 Web 方法時，[!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 引擎會執行下列動作：  
  
-   產生唯一 ID (工作階段 ID)。  
  
-   產生工作階段物件，並使該物件與唯一 ID 產生關聯。  
  
-   將唯一 ID 新增至 Set-Cookie HTTP 回應標頭，並傳送至用戶端。  
  
-   根據傳送至用戶端的工作階段 ID，識別後續呼叫上的用戶端。  
  
 用戶端會在傳送至伺服器的後續要求中，加入這個工作階段 ID。 伺服器則會使用來自用戶端的工作階段 ID，為目前的 HTTP 內容載入適當的工作階段物件。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和適用於.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](http://go.microsoft.com/fwlink/?LinkId=150780)下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Channels\HttpCookieSession`  
  
## <a name="httpcookiesession-channel-message-exchange-pattern"></a>HttpCookieSession 通道訊息交換模式  
 這個範例會對類似 ASMX 的案例啟用工作階段。 在通道堆疊的底部，將會提供支援 <xref:System.ServiceModel.Channels.IRequestChannel> 和 <xref:System.ServiceModel.Channels.IReplyChannel> 的 HTTP 傳輸。 通道的工作就是要對通道堆疊的較高層級提供工作階段。 這個範例會實作兩個支援工作階段的通道 (<xref:System.ServiceModel.Channels.IRequestSessionChannel> 和 <xref:System.ServiceModel.Channels.IReplySessionChannel>)。  
  
## <a name="service-channel"></a>服務通道  
 範例會在 `HttpCookieReplySessionChannelListener` 類別中提供服務通道。 這個類別會實作 <xref:System.ServiceModel.Channels.IChannelListener> 介面，並將通道堆疊中較低的 <xref:System.ServiceModel.Channels.IReplyChannel> 通道轉換為 <xref:System.ServiceModel.Channels.IReplySessionChannel>。 這個處理序可以分成下列幾個部分：  
  
-   通道接聽程式開啟時，會接受來自內部接聽程式的內部通道。 因為內部接聽程式為資料包 (Datagram) 接聽程式，而且所接受通道的時間範圍會少於接聽程式的時間範圍，因此我們可以關閉內部接聽程式而只保留內部通道。  
  
    ```  
                this.innerChannelListener.Open(timeoutHelper.RemainingTime());  
    this.innerChannel = this.innerChannelListener.AcceptChannel(timeoutHelper.RemainingTime());  
    this.innerChannel.Open(timeoutHelper.RemainingTime());  
    this.innerChannelListener.Close(timeoutHelper.RemainingTime());  
    ```  
  
-   完成開啟的處理序時，我們會設定訊息迴圈以接收來自內部通道的訊息。  
  
    ```  
    IAsyncResult result = BeginInnerReceiveRequest();  
    if (result != null && result.CompletedSynchronously)  
    {  
       // do not block the user thread  
       if (this.completeReceiveCallback == null)  
       {  
          this.completeReceiveCallback = new WaitCallback(CompleteReceiveCallback);  
       }  
       ThreadPool.QueueUserWorkItem(this.completeReceiveCallback, result);  
    }  
    ```  
  
-   訊息抵達時，服務通道會檢查工作階段識別碼，並將信號分離至適當的工作階段通道。 通道接聽程式所維護的字典，會將工作階段識別碼對應至工作階段通道執行個體。  
  
    ```  
    Dictionary<string, IReplySessionChannel> channelMapping;  
    ```  
  
 `HttpCookieReplySessionChannel` 類別會實作 <xref:System.ServiceModel.Channels.IReplySessionChannel>。 通道堆疊的較高層級會呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 方法，以讀取此工作階段的要求。 每個工作階段通道都有由服務通道所填入 (Populate) 的私用訊息佇列。  
  
```  
InputQueue<RequestContext> requestQueue;  
```  
  
 在某人呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 方法而且訊息佇列中沒有任何訊息的情況下，通道會先等待指定的時間量，然後才自行關機。 這會清除為非 WCF 用戶端建立的工作階段通道。  
  
 我們會使用 `channelMapping` 來追蹤 `ReplySessionChannels`，而在所有已接受的通道關閉之前，不會關閉基礎 `innerChannel`。 使用這個方法時，`HttpCookieReplySessionChannel` 存在的時間會超過 `HttpCookieReplySessionChannelListener` 的存留期。 我們也不用擔心接聽程式會在執行時進行記憶體回收，因為接受的通道會透過 `OnClosed` 回呼參考其接聽程式。  
  
## <a name="client-channel"></a>用戶端通道  
 對應的用戶端通道位於 `HttpCookieSessionChannelFactory` 類別中。 在通道建立期間，通道處理站會使用 `HttpCookieRequestSessionChannel` 包裝內部要求。 `HttpCookieRequestSessionChannel` 類別則會將呼叫轉寄至基礎要求通道。 當用戶端關閉 Proxy 時，`HttpCookieRequestSessionChannel` 會將訊息傳送至服務，指出通道正在關閉。 因此，服務通道堆疊可順利關閉使用中的工作階段通道。  
  
## <a name="binding-and-binding-element"></a>繫結和繫結項目  
 建立服務與用戶端通道之後, 的下一個步驟是將它們整合到 WCF 執行階段。 通道會透過繫結和繫結項目公開至 WCF。 繫結是由一個或多個繫結元素所組成。 WCF 提供數種具有系統定義的繫結。例如，BasicHttpBinding 或 WSHttpBinding。 `HttpCookieSessionBindingElement` 類別含有繫結項目的實作。 該類別會覆寫通道接聽程式和通道處理站的建立方法，以執行必要的通道接聽程式或通道處理站執行個體化 (Instantiation)。  
  
 範例會在服務描述中使用原則判斷提示。 這可讓範例將其通道需求發行至使用服務的其他用戶端。 例如，這個繫結項目會發行原則判斷提示，讓可能的用戶端清楚繫結項目可支援工作階段。 由於範例會啟用繫結項目組態中的 `ExchangeTerminateMessage` 屬性，因此會新增必要的判斷提示，表示該服務支援額外的訊息交換動作以終止工作階段對話。 接著，用戶端就可以使用此動作。 下列 WSDL 程式碼會顯示從 `HttpCookieSessionBindingElement` 建立的原則判斷提示。  
  
```xml  
<wsp:Policy wsu:Id="HttpCookieSessionBinding_IWcfCookieSessionService_policy" xmlns:wsp="http://schemas.xmlsoap.org/ws/2004/09/policy" xmlns:wsu="http://docs.oasis-open.org/wss/2004/01/oasis-200401-wss-wssecurity-utility-1.0.xsd">  
<wsp:ExactlyOne>  
<wsp:All>  
<wspe:Utf816FFFECharacterEncoding xmlns:wspe="http://schemas.xmlsoap.org/ws/2004/09/policy/encoding"/>  
<mhsc:httpSessionCookie xmlns:mhsc="http://samples.microsoft.com/wcf/mhsc/policy"/>  
</wsp:All>  
</wsp:ExactlyOne>  
</wsp:Policy>  
```  
  
 `HttpCookieSessionBinding` 類別是系統提供的繫結，會使用先前描述的繫結項目。  
  
## <a name="adding-the-channel-to-the-configuration-system"></a>將通道新增至組態系統  
 此範例提供了兩個類別，這兩個類別會透過組態來公開範例通道。 第一個類別為 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement> 的 `HttpCookieSessionBindingElement`。 大量實作會委派至衍生自 `HttpCookieSessionBindingConfigurationElement` 的 <xref:System.ServiceModel.Configuration.StandardBindingElement>。 `HttpCookieSessionBindingConfigurationElement` 的屬性會對應至 `HttpCookieSessionBindingElement` 上的屬性。  
  
### <a name="binding-element-extension-section"></a>繫結項目延伸區段  
 區段 `HttpCookieSessionBindingElementSection` 是 <xref:System.ServiceModel.Configuration.BindingElementExtensionElement>，它會將 `HttpCookieSessionBindingElement` 公開至組態系統。 透過一些覆寫，會定義組態區段名稱、繫結項目的型別，以及如何建立繫結項目。 然後您可以在組態檔中登錄延伸區段，如同下列所示：  
  
```xml  
<configuration>        
    <system.serviceModel>        
      <extensions>          
        <bindingElementExtensions>            
          <add name="httpCookieSession"   
               type=  
"Microsoft.ServiceModel.Samples.HttpCookieSessionBindingElementElement,   
                    HttpCookieSessionExtension, Version=1.0.0.0,   
                    Culture=neutral, PublicKeyToken=null"/>  
        </bindingElementExtensions >  
      </extensions>  
  
      <bindings>  
      <customBinding>  
        <binding name="allowCookiesBinding">  
          <textMessageEncoding messageVersion="Soap11WSAddressing10" />  
          <httpCookieSession sessionTimeout="10" exchangeTerminateMessage="true" />  
          <httpTransport allowCookies="true" />  
        </binding>  
      </customBinding>  
      </bindings>        
    </system.serviceModel>    
</configuration>  
```  
  
## <a name="test-code"></a>測試程式碼  
 您可以在用戶端和服務目錄中，找到使用此範例傳輸的測試程式碼。 它包含兩個測試，一項測試會使用的繫結`allowCookies`設`true`用戶端上。 第二個測試則會在繫結上啟用明確關閉 (使用終止訊息交換)。  
  
 當您執行範例時，您應該會看到下列輸出：  
  
```  
Simple binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
Smart binding:  
AddItem(10000,2): ItemCount=2  
AddItem(10550,5): ItemCount=7  
RemoveItem(10550,2): ItemCount=5  
Items  
10000, 2  
10550, 3  
  
Press <ENTER> to terminate client.  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a>若要安裝、建置及執行範例  
  
1.  使用下列命令安裝 [!INCLUDE[vstecasp](../../../../includes/vstecasp-md.md)] 4.0。  
  
    ```  
    %windir%\Microsoft.NET\Framework\v4.0.XXXXX\aspnet_regiis.exe /i /enable  
    ```  
  
2.  請確定您已執行[的 Windows Communication Foundation 範例的單次安裝程序](../../../../docs/framework/wcf/samples/one-time-setup-procedure-for-the-wcf-samples.md)。  
  
3.  若要建置此方案，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。  
  
4.  若要在單一或跨電腦組態中執行範例時，請依照中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。  
  
## <a name="see-also"></a>另請參閱
