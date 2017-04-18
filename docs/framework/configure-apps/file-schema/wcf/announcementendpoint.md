---
title: "&lt;announcementEndpoint&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 034b7c69-a770-4502-8cef-38007bbcd025
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;announcementEndpoint&gt;
這個組態項目會定義具有固定公告合約的標準端點。  服務可以選擇性地公告其可用性，方法是分別在開啟與關閉該服務時傳送線上及離線公告訊息。  [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 服務會在 [\<serviceDiscovery\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicediscovery.md) 項目中指定公告端點，並且使用 AnnouncementClient 來執行公告。  希望接聽來自其他服務之公告的用戶端，實際上的作用是 [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 服務，因此，您必須在 [\<服務\>](../../../../../docs/framework/configure-apps/file-schema/wcf/services.md) 區段中設定該用戶端的公告端點。  
  
## 語法  
  
```  
  
<system.serviceModel>  
    <standardEndpoints>  
       <announcementEndpoint>   
          <standardEndpoint  
                  discoveryVersion=”WSDiscovery11/WSDiscoveryApril2005”  
                  maxAnnouncementDelay=”Timespan”   
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
|name|字串，這個字串會指定標準端點之組態的名稱。  這個名稱用於服務端點的 `endpointConfiguration` 屬性中，可將標準端點連結至其組態。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<standardEndpoints\>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 \(位址、繫結、合約\)。|  
  
## 範例  
 下列範例示範透過 http 及 peernet 接聽公告訊息的用戶端。  
  
```  
  
<services>  
  <service name="ServiceAnnouncementListener">  
              <endpoint name="httpAnnouncementEndpoint"  
                        kind="announcementEndpoint"  
                        binding="basicHttpBinding"  
                        address="announcements" />  
              <endpoint name="peerNetAnnouncementEndpoint"  
                        kind="announcementEndpoint"  
                        binding="peerTcpBinding"  
                        address="net.p2p://discoveryMesh/multicast"  
                        bindingConfiguration="discoveryPeerTcpBindingConfig" />  
  ...  
  </service>  
</services>  
  
<standardEndpoints>  
  <announcementEndpoint>  
     <standardEndpoint name="httpAnnouncementEndpoint"                         
                       version="WSDiscoveryApril2005" />  
     <standardEndpoint name="peerNetAnnouncementEndpoint"                         
                       version="WSDiscoveryApril2005" />  
   </announcementEndpoint>  
</standardEndpoints>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.AnnouncementEndpoint>