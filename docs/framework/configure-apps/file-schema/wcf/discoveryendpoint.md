---
title: '&lt;discoveryEndpoint&gt;'
ms.date: 03/30/2017
ms.assetid: fae2f48b-a635-4e4b-859d-a1432ac37e1c
ms.openlocfilehash: 6a352fbfced08001f76dceaff283d6bca25f56f9
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiscoveryendpointgt"></a>&lt;discoveryEndpoint&gt;

這個組態項目會定義具有固定探索合約的標準端點。 加入至服務組態時，此組態項目會指定接聽探索訊息的位置。 加入至用戶端組態時，此組態項目會指定傳送探索查詢的位置。  
  
\<system.serviceModel>  
\<Kind >  
  
## <a name="syntax"></a>語法

```xml
<system.serviceModel>
  <standardEndpoints>
    <discoveryEndpoint>
      <standardEndpoint discoveryMode="Adhoc/Managed" 
                        discoveryVersion="WSDiscovery11/WSDiscoveryApril2005" 
                        maxResponseDelay="Timespan" 
                        name="String" />
    </discoveryEndpoint>
  </standardEndpoints>
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和元素

下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性

| 屬性        | 描述 |  
| ---------------- | ----------- |  
| discoveryMode    | 字串，這個字串會指定探索通訊協定的模式。 有效值為"Adhoc"和"Managed"。 在 Managed 模式中，通訊協定會依賴探索 Proxy，此 Proxy 的作用是可探索之服務的儲存機制。 Adhoc 模式會要求通訊協定使用 UDP 多點傳送機制尋找可用的服務。 如需有關屬性的詳細資訊，請參閱<xref:System.ServiceModel.Discovery.DiscoveryEndpoint.DiscoveryMode%2A>。 |  
| discoveryVersion | 字串，此字串會指定兩個 WS-Discovery 通訊協定版本的其中之一。 有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。 這個值的型別為 <xref:System.ServiceModel.Discovery.DiscoveryVersion>。 |  
| maxResponseDelay | Timespan 值，這個值指定 Discovery 通訊協定傳送某些訊息 (例如「探查相符」或「解析相符」) 之前會等候的延遲值上限。<br /><br /> 如果所有 ProbeMatches 同時傳送，則會導致網路負荷過大。 為避免發生這種情況，傳送 ProbeMatches 時，兩次 ProbeMatch 傳送之間會有隨機的延遲時間。 隨機的延遲範圍介於 0 到這個屬性所設定的值之間。 如果這個屬性設為 0，則 ProbeMatches 訊息會以緊湊的迴圈傳送，且不會有任何延遲。 否則，ProbeMatches 訊息傳送時會有隨機延遲，而傳送所有 ProbeMatches 訊息花費的總時間不會超過 maxResponseDelay。 這個值只與服務有關，不會由用戶端使用。 |  
| `name`           | 字串，這個字串會指定標準端點之組態的名稱。 這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。 |  
  
### <a name="child-elements"></a>子元素

無。  
  
### <a name="parent-elements"></a>父元素

| 元素 | 描述 |  
| ------- | ----------- |  
| [\<Kind >](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md) | 標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。 |  
  
## <a name="example"></a>範例

下列範例示範透過對等網路多點傳送傳輸接聽探索訊息的服務。 此範例會明確地指定 WS-Discovery April 2005 版本。  
  
標準端點組態是依每個服務定義的，無法跨服務共用。 如果另一個服務想擁有同樣的探索端點，就需要將同樣的組態加入至該服務的區段中。  
  
```xml
<services>  
  <service name="CalculatorService"
           behaviorConfiguration="CalculatorServiceBehavior">
    <endpoint binding="basicHttpBinding" 
              address="calculator" 
              contract="ICalculatorService" />  
    <endpoint name="peerNetDiscovery"  
              binding="peerTcpBinding"  
              address="net.p2p://discoveryMesh/multicast"  
              kind="discoveryEndpoint"  
              endpointConfiguration="peerTcpDiscoveryEndpointConfiguration"  
              bindingConfiguration="discoveryPeerTcpBindingConfig" />      
  </service>  
</services>  
<standardEndpoints>  
  <discoveryEndpoint>  
    <standardEndpoint name="peerTcpDiscoveryEndpointConfiguration"                         
                      version="WSDiscoveryApril2005" />  
  </discoveryEndpoint>  
</standardEndpoints>  
```  
  
## <a name="see-also"></a>另請參閱

<xref:System.ServiceModel.Discovery.DiscoveryEndpoint>
