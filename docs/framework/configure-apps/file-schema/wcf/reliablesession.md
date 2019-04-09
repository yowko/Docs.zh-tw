---
title: <reliableSession>
ms.date: 03/30/2017
ms.assetid: 129b4a59-37f0-4030-b664-03795d257d29
ms.openlocfilehash: 324c46d88d084605dc2b873c65d2a7e7c7a2c4fb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59188379"
---
# <a name="reliablesession"></a>\<reliableSession>
定義 WS-Reliable 訊息設定。 將這個項目新增至自訂繫結時，產生的通道可支援確實傳送一次保證。  
  
 \<system.serviceModel>  
\<bindings>  
\<customBinding>  
\<binding>  
\<reliableSession>  
  
## <a name="syntax"></a>語法  
  
```xml  
<reliableSession acknowledgementInterval="TimeSpan"
                 flowControlEnabled="Boolean"
                 inactivityTimeout="TimeSpan"
                 maxPendingChannels="Integer"
                 maxRetryCount="Integer"
                 maxTransferWindowSize="Integer"
                 reliableMessagingVersion="Default/WSReliableMessagingFebruary2005/WSReliableMessaging11"
                 ordered="Boolean" />
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|acknowledgementInterval|<xref:System.TimeSpan>，其中包含通道要等待的最大時間間隔；經過這個間隔以後，通道會針對直到該時間點前收到的訊息傳送認可。 預設值為 00:00:0.2。|  
|flowControlEnabled|布林值，指出是否已啟動進階流程控制 (適用於 WS-Reliable 訊息之流程控制的 Microsoft 特定實作)。 預設為 `true`。|  
|inactivityTimeout|<xref:System.TimeSpan>，指定將通道判定為失敗之前可允許另一個通訊方不傳送任何訊息的最長期間。 預設為 00:10:00。<br /><br /> 通道上的活動是定義為接收應用程式或基礎結構訊息。 這個屬性會控制讓非作用中工作階段保持運作的最大時間量。 如果經過更長的一段時間且無任何活動，工作階段會由基礎結構和通道錯誤中止。 **注意：** 應用程式不需要定期傳送訊息來維持連線狀態。|  
|maxPendingChannels|整數，指定可以在接聽程式上等待接受的通道數目上限。 這個值應介於 1 到 16384 之間 (含 1 和 16384)。 預設值為 4。<br /><br /> 通道在等待接受時會暫止。 一旦到達該限制，便不會建立通道。 通道反而會處於暫止模式，直到這個數字藉由接受暫止通道下降為止。 這是一項原廠限制。<br /><br /> 如果到達臨界值，而且遠端應用程式嘗試建立新的可靠工作階段，則要求會被拒絕，提示這個要求的開啟作業也會發生錯誤。 這項限制不適用於暫止傳出通道的數目。|  
|maxRetryCount|整數，藉由針對可靠通道的基礎通道呼叫 Send，指定可靠通道嘗試重新傳輸其未收到認可之訊息的次數上限。<br /><br /> 這個值應大於零。 預設值為 8。<br /><br /> 這個值應為大於零的整數。 如果在最後一次重新傳輸後仍未收到認可，則通道會發生錯誤。<br /><br /> 如果收件者已認可該處的訊息傳遞，則訊息會視為要傳輸的訊息。<br /><br /> 如果在特定一段時間內沒有收到已傳輸之訊息的認可，則基礎結構會自動重新傳輸該訊息。 基礎結構會嘗試重新傳送該訊息達這個屬性所指定的最多次數。 如果在最後一次重新傳輸後仍未收到認可，則通道會發生錯誤。<br /><br /> 基礎結構會使用指數倒退演算法，根據計算出來的平均來回時間決定何時重新傳輸。 經過之後就重新傳輸訊息的時間起初從 1 秒開始，延遲時間也會隨著每次嘗試重新傳輸而加倍，因此第一次重新傳輸嘗試到最後一次重新傳輸嘗試之間會經過約 8.5 分鐘。 第一次嘗試重新傳輸的時間會根據計算出來的來回時間調整，這些嘗試所花費的時間也會因此而有所不同。 如此便可讓重新傳輸時間透過動態的方式適應多變的網路狀況。|  
|maxTransferWindowSize|指定緩衝區大小上限的整數。 有效值為 1 到 4096 (含 1 和 4096)。<br /><br /> 在用戶端上，這個屬性會定義可靠通道用來保留收件者尚未認可之訊息的緩衝區大小上限。 配額是以訊息做為單位計算。 如果緩衝區已滿，則會封鎖其他 SEND 作業。<br /><br /> 在接收者上，這個屬性會定義通道用來存放尚未分派到應用程式之傳入訊息的最大緩衝區大小。 如果緩衝區已滿，接收者會在沒有通知的情況下捨棄其他訊息，而且需要用戶端重新傳輸訊息。|  
|排序|布林值，指定是否保證訊息以傳送時的順序到達。 如果這個設定為 `false`，則訊息可以不按照順序到達。 預設為 `true`。|  
|reliableMessagingVersion|<xref:System.ServiceModel.ReliableMessagingVersion> 中的有效值，指定要使用的 WS-ReliableMessaging 版本。|  
  
### <a name="child-elements"></a>子元素  
 None  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<binding>](../../../../../docs/framework/misc/binding.md)|定義自訂繫結的所有繫結功能。|  
  
## <a name="remarks"></a>備註  
 可靠的工作階段會提供可靠傳訊和工作階段功能。 可靠的傳訊失敗時會重試通訊，而且允許指定傳遞保證，例如訊息依序到達。 工作階段會保持呼叫之間的用戶端狀態。 這個項目還會選擇性地提供排序式的訊息傳遞。 這個實作的工作階段可以跨 SOAP 和傳輸媒介。  
  
 每個繫結項目都代表傳送或接收訊息時的一個處理步驟。 繫結項目會在執行階段建立通道處理站和接聽程式，它們是在傳送和接收訊息時所需要之傳出和傳入通道堆疊的必要建置項目。 `reliableSession` 在堆疊中提供選擇性的層級，而透過該層級可以在端點之間建立可靠工作階段，並設定這個工作階段的行為。  
  
 如需詳細資訊，請參閱 <<c0> [ 可靠工作階段](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)。  
  
## <a name="example"></a>範例  
 以下範例將示範如何使用各種傳輸和訊息編碼項目來設定自訂繫結，尤其是啟用可靠的工作階段，因為這麼做可保持用戶端狀態並指定依序傳遞保證。 這個功能是在用戶端和服務的應用程式組態檔中設定。 該範例會顯示服務組態。  
  
```xml  
<?xml version="1.0" encoding="utf-8" ?>
<configuration>
  <system.serviceModel>
    <services>
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"
               behaviorConfiguration="CalculatorServiceBehavior">
        <!-- This endpoint is exposed at the base address provided by host: http://localhost/servicemodelsamples/service.svc -->
        <!-- specify customBinding binding and a binding configuration to use -->
        <endpoint address=""
                  binding="customBinding"
                  bindingConfiguration="Binding1"
                  contract="Microsoft.ServiceModel.Samples.ICalculator" />
        <!-- The mex endpoint is exposed at http://localhost/servicemodelsamples/service.svc/mex -->
        <endpoint address="mex"
                  binding="mexHttpBinding"
                  contract="IMetadataExchange" />
      </service>
    </services>
    <!-- custom binding configuration - configures HTTP transport, reliable sessions -->
    <bindings>
      <customBinding>
        <binding name="Binding1">
          <reliableSession />
          <security authenticationMode="SecureConversation"
                    requireSecurityContextCancellation="true">
          </security>
          <compositeDuplex />
          <oneWay />
          <textMessageEncoding messageVersion="Soap12WSAddressing10"
                               writeEncoding="utf-8" />
          <httpTransport authenticationScheme="Anonymous"
                         bypassProxyOnLocal="false"
                         hostNameComparisonMode="StrongWildcard"
                         proxyAuthenticationScheme="Anonymous"
                         realm=""
                         useDefaultWebProxy="true" />
        </binding>
      </customBinding>
    </bindings>
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
    <behaviors>
      <serviceBehaviors>
        <behavior name="CalculatorServiceBehavior">
          <serviceMetadata httpGetEnabled="True" />
          <serviceDebug includeExceptionDetailInFaults="False" />
        </behavior>
      </serviceBehaviors>
    </behaviors>
  </system.serviceModel>
</configuration>
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.Configuration.ReliableSessionElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- <xref:System.ServiceModel.Channels.ReliableSessionBindingElement>
- [可靠工作階段](../../../../../docs/framework/wcf/feature-details/reliable-sessions.md)
- [繫結](../../../../../docs/framework/wcf/bindings.md)
- [擴充繫結](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [自訂繫結](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [\<customBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
