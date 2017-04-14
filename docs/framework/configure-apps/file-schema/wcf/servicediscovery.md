---
title: "&lt;serviceDiscovery&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: a3c68a4a-fc95-43c5-aacb-785936c0cf39
caps.latest.revision: 4
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 4
---
# &lt;serviceDiscovery&gt;
指定服務端點的探索能力。  
  
## 語法  
  
```  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name=String">  
      <serviceDiscovery>  
        <announcementEndpoints>  
              <endpoint name="String”  
                        kind="Type" />  
        </announcementEndpoints>  
        <discoveryEndpoints>  
              <endpoint name="String”  
                        kind="Type" />  
        </discoveryEndpoints>  
      </serviceDiscovery>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<announcementEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md)|公告端點的集合。  使用此區段指定用於傳送公告訊息的端點。|  
|[\<discoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)|探索端點的集合。  使用此區段指定用於接聽探索訊息的端點。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<行為\>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|指定行為項目。|  
  
## 備註  
 加入至服務的行為組態時，這個組態項目會將該服務的所有端點標示為可探索。  您可以使用 [\<discoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md)[\<announcementEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) 子項目，進一步設定此類端點的探索功能。  使用 [\<announcementEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/announcementendpoint.md) 區段，指定將用於傳送服務公告 \(線上\/Hello 與離線\/Bye\) 的端點組態，以設定公告。  使用 [\<discoveryEndpoint\>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryendpoint.md) 區段手動指定用於接聽探索訊息的端點。  
  
## 範例  
 下列組態範例將 CalculatorService 指定為可探索，並且選擇性地指定要使用的公告端點。  
  
```  
  
<services>  
  <service name="CalculatorService"  
           behaviorConfiguration="CalculatorServiceBehavior">  
  ...  
  </service>  
</services>  
  
<behaviors>  
  <serviceBehaviors>  
    <behavior name="CalculatorServiceBehavior">  
      <serviceDiscovery>  
        <announcementEndpoints>  
              <endpoint name="udpEndpoint"  
                        kind="udpAnnouncementEndpoint" />  
        </announcementEndpoints>  
      </serviceDiscovery>  
    </behavior>  
  </serviceBehaviors>  
</behaviors>  
  
```  
  
## 請參閱  
 <xref:System.ServiceModel.Discovery.ServiceDiscoveryBehavior>