---
title: "&lt;udpDiscoveryEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1f485329-2771-43bc-88de-df8f2faa3bb7
caps.latest.revision: 2
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 2
---
# &lt;udpDiscoveryEndpoint&gt;
這個組態項目會定義標準端點，此端點是針對透過 UDP 多點傳送繫結進行探索作業而預先設定的。  此端點具備固定合約，而且支援兩種 WS\-Discovery 通訊協定版本。  此外，它擁有固定的 UDP 繫結和預設位址，如 WS\-Discovery 規格 \(WS\-Discovery 2005 年 4 月或 WS\-Discovery V1.1\) 中所指定。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <discoveryEndpoint>   
          <standardEndpoint  
                  discoveryMode=”Adhoc/Managed”  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxResponseDelay=”Timespan”  
                  multicastAddress=”Uri”   
                  name="String" />  
       </discoveryEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|discoveryMode|字串，這個字串會指定探索通訊協定的模式。  有效值為 “Adhoc” 和 “Managed”。  在 Managed 模式中，通訊協定會依賴探索 Proxy，此 Proxy 的作用是可探索之服務的儲存機制。  Adhoc 模式會要求通訊協定使用 UDP 多點傳送機制尋找可用的服務。  這個值的型別為 <xref:System.Servicemodel.Discovery.DiscoveryMode>。|  
|discoveryVersion|字串，此字串會指定兩個 WS\-Discovery 通訊協定版本的其中之一。  有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。  這個值的型別為 <xref:System.Servicemodel.Discovery.DiscoveryVersion>。|  
|maxResponseDelay|Timespan 值，這個值指定 Discovery 通訊協定傳送某些訊息 \(例如「探查相符」或「解析相符」\) 之前會等候的延遲值上限。<br /><br /> 如果所有 ProbeMatches 同時傳送，則會導致網路負荷過大。  為避免發生這種情況，傳送 ProbeMatches 時，兩次 ProbeMatch 傳送之間會有隨機的延遲時間。  隨機的延遲範圍介於 0 到這個屬性所設定的值之間。  如果這個屬性設為 0，則 ProbeMatches 訊息會以緊湊的迴圈傳送，且不會有任何延遲。  否則，ProbeMatches 訊息傳送時會有隨機延遲，而傳送所有 ProbeMatches 訊息花費的總時間不會超過 maxResponseDelay。  這個值只與服務有關，不會由用戶端使用。|  
|multicastAddress|URI，這個 URI 會指定傳送及接收探索訊息時所使用的多點傳送位址。  預設值是與通訊協定規格一致的多點傳送位址。|  
|`name`|字串，這個字串會指定標準端點之組態的名稱。  這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<udpTransportSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|設定的集合，可讓您設定 UDP 端點的 UDP 傳輸。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 \(位址、繫結、合約\)。|  
  
## 範例  
 下列範例示範透過 UDP 多點傳送傳輸接聽探索訊息的服務。  
  
```  
  
<services>  
    <service name="CalculatorService"  
         behaviorConfiguration="CalculatorServiceBehavior">  
         <endpoint binding="basicHttpBinding"   
           address="calculator" contract="ICalculatorService" />  
         <endpoint name="DiscoveryEndpoint"  
                kind="udpDiscoveryEndpoint" />  
</service>  
<standardEndpoints>  
  <udpDiscoveryEndpoint>  
     <standardEndpoint name="DiscoveryEndpoint"                         
                       version="WSDiscoveryApril2005" />  
   </udpDiscoveryEndpoint>  
</standardEndpoints>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.DiscoveryEndpoint>