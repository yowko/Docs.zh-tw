---
title: 組態範例
ms.date: 03/30/2017
ms.assetid: 75515b4a-8d70-44c8-99e0-7423df41380e
ms.openlocfilehash: ae1b98d4afcc4a7bc97a4668ef7d974b27cafed9
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2018
ms.locfileid: "43862075"
---
# <a name="configuration-sample"></a>組態範例
此範例示範如何使用組態檔讓服務變成可搜尋的。  
  
> [!NOTE]
>  這個範例會在組態中實作探索。 如需在程式碼中實作探索的範例，請參閱 <<c0> [ 基本](../../../../docs/framework/wcf/samples/basic-sample.md)。  
  
> [!IMPORTANT]
>  這些範例可能已安裝在您的電腦上。 請先檢查下列 (預設) 目錄，然後再繼續。  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。 此範例位於下列目錄。  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Basic\Discovery\Configuration`  
  
## <a name="service-configuration"></a>服務組態  
 此範例中的組態檔示範兩種功能：  
  
-   透過標準的 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 讓服務變成可搜尋的。  
  
-   針對服務的應用程式端點調整與探索相關的資訊，以及針對標準端點調整部分與探索相關的設定。  
  
 若要啟用探索，您必須在服務的應用程式組態檔中進行少數變更：  
  
-   探索端點必須加入至 `<service>` 項目中。 這是標準的 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 端點。 這是執行階段與探索服務產生關聯的系統端點。 探索服務會接聽此端點上的訊息。  
  
-   `<serviceDiscovery>` 行為會加入至 `<serviceBehaviors>` 區段。 如此可在執行階段探索服務，並使用先前提到的探索端點接聽探索 `Probe` 和 `Resolve` 訊息。 加入這兩個項目之後，就可以在指定的探索端點搜尋服務。  
  
 下列組態程式碼片段顯示啟用應用程式端點和探索端點的服務：  
  
```xml
<services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
          <endpoint name="udpDiscovery"   
                    kind="udpDiscoveryEndpoint"   
                endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
```  
  
 若要利用公告，您必須加入公告端點。 若要這樣做，請依照下列程式碼所示，修改組態檔。  
  
```xml  
<serviceDiscovery>  
            <announcementEndpoints>  
              <endpoint kind="udpAnnouncementEndpoint"/>  
            </announcementEndpoints>  
          </serviceDiscovery>  
```  
  
 將公告端點加入至探索服務行為會建立服務的預設公告用戶端。 這樣做可確保在開啟與關閉服務時，服務會分別傳送線上與離線公告。  
  
 此組態檔並不僅止於這些修改額外行為的簡單步驟而已。 您可以使用特定的端點控制與探索相關的資訊。 亦即，使用者可以控制是否能夠探索端點，而且使用者也可以使用 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior.Scopes%2A> 和自訂 XML 中繼資料標示該端點。 若要這樣做，使用者必須將 `behaviorConfiguration` 屬性加入至應用程式端點。 在此情況下，下列屬性會加入至應用程式端點。  
  
```  
behaviorConfiguration="endpointBehaviorConfiguration"  
```  
  
 現在，您可以透過行為組態項目控制與探索相關的屬性。 在此情況下，有兩個範圍會加入至應用程式端點。  
  
```xml  
<endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
```  
  
 如需有關範圍的詳細資訊，請參閱 <<c0> [ 探索尋找與尋找準則](../../../../docs/framework/wcf/feature-details/discovery-find-and-findcriteria.md)。  
  
 您也可以控制探索端點的特定詳細資料。 這是透過 <xref:System.ServiceModel.Configuration.StandardEndpointsSection> 達成。 在此範例中，所使用的通訊協定版本會經過修改，而且會加入 `maxResponseDelay` 屬性，如下列程式碼範例所示。  
  
```xml  
<standardEndpoints>  
   <udpDiscoveryEndpoint>  
      <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
```  
  
 下面是用於此範例的完整組態檔：  
  
```xml  
<configuration>  
    <system.serviceModel>  
  
      <services>  
        <service name="Microsoft.Samples.Discovery.CalculatorService"  
                 behaviorConfiguration="calculatorServiceBehavior">  
          <endpoint address=""  
                    binding="wsHttpBinding"  
                    contract="Microsoft.Samples.Discovery.ICalculatorService"  
                    behaviorConfiguration="endpointBehaviorConfiguration" />  
         <!-- Define the discovery endpoint -->            
<endpoint name="udpDiscovery" kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration"/>        </service>  
      </services>  
  
      <behaviors>  
  
        <serviceBehaviors>  
          <behavior name="calculatorServiceBehavior">  
  
            <!-- Add an announcement endpoint -->  
            <serviceDiscovery>  
              <announcementEndpoints>  
                <endpoint kind="udpAnnouncementEndpoint"/>  
              </announcementEndpoints>  
            </serviceDiscovery>  
          </behavior>  
        </serviceBehaviors>  
  
        <endpointBehaviors>  
          <behavior name="endpointBehaviorConfiguration">  
            <!-- Add scopes used to identify the service -->  
            <endpointDiscovery>  
              <scopes>  
                <add scope="http://www.example.com/calculator"/>  
                <add scope="ldap:///ou=engineering,o=examplecom,c=us"/>  
              </scopes>  
            </endpointDiscovery>  
  
          </behavior>            
        </endpointBehaviors>  
  
      </behaviors>  
  
      <standardEndpoints>  
        <udpDiscoveryEndpoint>  
         <!-- Configure the UDP discovery endpoint -->  
          <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11" maxResponseDelay="00:00:00.600" />    
        </udpDiscoveryEndpoint>  
      </standardEndpoints>  
  
    </system.serviceModel>  
</configuration>  
```  
  
## <a name="client-configuration"></a>用戶端組態  
 在用戶端的應用程式組態檔中，`standardEndpoint` 型別的 `dynamicEndpoint` 會用來使用探索，如下列組態程式碼片段所示。  
  
```xml  
<client>  
   <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
   <endpoint name="calculatorEndpoint"  
             binding="wsHttpBinding"  
             contract="ICalculatorService"  
             kind ="dynamicEndpoint"  
             endpointConfiguration="dynamicEndpointConfiguration">  
   </endpoint>  
</client>  
```  
  
 當用戶端正在使用 `dynamicEndpoint` 時，執行階段會自動執行探索。 系統會在探索期間使用各種設定，例如 `discoveryClientSettings` 區段中定義的設定，而該區段會指定要使用的探索端點型別：  
  
```xml  
<endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
```  
  
 用來搜尋服務的尋找準則：  
  
```xml  
<!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
<findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
   <scopes>  
      <add scope="http://www.microsoft.com/building42/floor1"/>  
   </scopes>  
   <!-- These extensions are sent from the client to the service as part of the probe message -->  
   <extensions>  
      <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
   </extensions>  
</findCriteria>  
```  
  
 此範例會延伸這個功能，並修改用戶端所使用的 <xref:System.ServiceModel.Discovery.FindCriteria>，以及用於探索之標準 `updDiscoveryEndpoint` 的部分屬性。 <xref:System.ServiceModel.Discovery.FindCriteria> 會修改為使用範圍與特定的 `scopeMatchBy` 演算法，以及自訂終止準則。 此外，此範例也會示範用戶端如何使用 `Probe` 訊息傳送 XML 項目。 最後，您必須對 <xref:System.ServiceModel.Discovery.UdpDiscoveryEndpoint> 進行某些變更，例如所使用的通訊協定版本以及 UDP 專屬設定，如下列組態檔所示。  
  
```xml  
<udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
```  
  
 下面是用於此範例的完整用戶端組態。  
  
```xml  
<configuration>  
  <system.serviceModel>  
  
    <client>  
      <!--  Create an endpoint, make kind="dynamicEndpoint" and use the endpointConfiguration to change settings of DynamicEndpoint -->  
      <endpoint name="calculatorEndpoint"  
                binding="wsHttpBinding"  
                contract="ICalculatorService"  
                kind ="dynamicEndpoint"  
                endpointConfiguration="dynamicEndpointConfiguration">  
      </endpoint>  
    </client>  
  
    <standardEndpoints>  
  
      <dynamicEndpoint>        
        <standardEndpoint name="dynamicEndpointConfiguration">  
          <discoveryClientSettings>  
            <!-- Controls where the discovery happens. In this case, Probe message is sent over UdpDiscoveryEndpoint. -->  
            <endpoint kind="udpDiscoveryEndpoint" endpointConfiguration="adhocDiscoveryEndpointConfiguration" />  
  
            <!-- Add Scopes, ScopeMatchBy, Extensions and termination criteria in FindCriteria -->  
            <findCriteria scopeMatchBy="http://schemas.microsoft.com/ws/2008/06/discovery/rfc" duration="00:00:10" maxResults="1">  
              <scopes>  
                <add scope="http://www.microsoft.com/building42/floor1"/>  
              </scopes>  
              <!-- These extensions are sent from the client to the service as part of the probe message -->  
              <extensions>  
                <CustomMetadata>This is custom metadata that is sent to the service along with the client's find request.</CustomMetadata>  
              </extensions>  
            </findCriteria>  
          </discoveryClientSettings>  
        </standardEndpoint>     
      </dynamicEndpoint>  
  
      <udpDiscoveryEndpoint>    
        <!-- Specify the discovery protocol version and UDP transport settings. -->   
        <standardEndpoint name="adhocDiscoveryEndpointConfiguration" discoveryVersion="WSDiscovery11">  
          <transportSettings duplicateMessageHistoryLength="2048"  
                             maxPendingMessageCount="5"  
                             maxReceivedMessageSize="8192"  
                             maxBufferPoolSize="262144"/>  
        </standardEndpoint>        
      </udpDiscoveryEndpoint>  
  
    </standardEndpoints>  
  
  </system.serviceModel>  
```  
  
#### <a name="to-use-this-sample"></a>若要使用這個範例  
  
1.  此範例使用 HTTP 端點，若要執行這個範例，適當的 URL Acl 必須加入，請參閱[設定 HTTP 和 HTTPS](https://go.microsoft.com/fwlink/?LinkId=70353)如需詳細資訊。 以更高的權限執行下列命令應該就能加入適當的 ACL。 如果命令未正確執行，您可能要將 Domain 和 Username 替換成下列引數。 `netsh http add urlacl url=http://+:8000/ user=%DOMAIN%\%UserName%`  
  
2.  建置方案。  
  
3.  從組建目錄執行服務的可執行檔。  
  
4.  執行用戶端可執行檔。 請注意，用戶端可以尋找服務。  
  
## <a name="see-also"></a>另請參閱
