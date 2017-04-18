---
title: "&lt;udpAnnoucementEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 5b3fa9c5-f372-4df9-a9d6-1e426063b721
caps.latest.revision: 3
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 3
---
# &lt;udpAnnoucementEndpoint&gt;
這個組態項目會定義標準端點，服務會使用此端點透過 UDP 繫結傳送公告訊息。  此端點具備固定合約，而且支援兩種探索版本。  此外，它擁有固定的 UDP 繫結和預設位址值，如 WS\-Discovery 規格 \(WS\-Discovery 2005 年 4 月或 WS\-Discovery 1.1 版\) 中所指定。  您可以指定傳送及接收公告訊息時所使用的多點傳送位址。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <announcementEndpoint>   
          <standardEndpoint  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxAnnouncementDelay=”Timespan”   
                  multicastAddress=”Uri”  
                  name="String" />   
       </announcementEndpoint>          
    </standardEndpoints>  
</system.serviceModel>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|discoveryVersion|字串，此字串會指定兩個 WS\-Discovery 通訊協定版本的其中之一。  有效的值為 WSDiscovery11 和 WSDiscoveryApril2005。  這個值的型別為 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryVersion>。|  
|maxAnnouncementDelay|Timespan 值，這個值指定 Discovery 通訊協定傳送 Hello 訊息之前會等候的延遲值上限。  系統會等候一段隨機時間值 \(介於 0 和此屬性的值之間\)，之後才傳送訊息。  這個屬性用於設定一小段隨機的延遲，避免網路關閉而所有服務同時再次上線時網路負荷過大。|  
|multicastAddress|URI，這個 URI 會指定傳送及接收探索訊息時所使用的多點傳送位址。  預設值是與通訊協定規格一致的多點傳送位址。|  
|name|字串，這個字串會指定標準端點之組態的名稱。  這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<udpTransportSettings\>](../../../../../docs/framework/configure-apps/file-schema/wcf/udptransportsettings.md)|設定的集合，可讓您設定 UDP 端點的 UDP 傳輸。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 \(位址、繫結、合約\)。|  
  
## 範例  
 下列範例示範透過具預設多點傳送位址的 UDP 多點傳送傳輸與具指定多點傳送位址的 UDP 多點傳送傳輸接聽公告的用戶端。  
  
```  
  
<services>  
  <service name="ServiceAnnouncementListener">  
      <endpoint name="udpAnnouncementEndpointStandard"  
                kind="udpAnnouncementEndpoint"  
                bindingConfiguration="..." />  
      <endpoint name="udpAnnouncementEndpoint2"  
                kind="udpAnnouncementEndpoint"  
                endpointConfiguration="AnnouncementConfiguration3702"  
                bindingConfiguration="..." />  
...  
  </service>  
</services>  
<standardEndpoints>  
  <udpAnnouncementEndpoint>  
     <standardEndpoint name="AnnouncementConfiguration2"   
          version="WSDiscoveryApril2005"   
          multicastAddress="soap.udp://239.255.255.250:3703"/>          
  </udpAnnouncementEndpoint>  
</standardEndpoints>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.UdpAnnouncementEndpoint>