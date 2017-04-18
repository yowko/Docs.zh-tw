---
title: "&lt;行為&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 0e5da4e6-1aa5-466c-924e-f10efee57f0b
caps.latest.revision: 13
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 13
---
# &lt;行為&gt;
這個項目會定義兩個名稱為 `endpointBehaviors` 和 `serviceBehaviors` 的子集合。  每個集合會定義分別由端點和服務使用的行為項目。  每個行為項目都由其唯一的 `name` 屬性所識別。  從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。  如需預設組態和無名稱繫結與行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[WCF 服務的簡化組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。  
  
 \<system.ServiceModel\>  
  
## 語法  
  
```  
  
<behaviors>  
   <serviceBehaviors>  
   </serviceBehaviors>  
   <endpointBehaviors>  
   </endpointBehaviors>  
</behaviors>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<endpointBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)|這個組態區段表示為特定端點定義的所有行為。|  
|[\<serviceBehaviors\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicebehaviors.md)|這個組態區段表示為特定服務定義的所有行為。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.serviceModel\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel.md)|所有 Windows Communication Foundation \(WCF\) 組態項目的根項目。|  
  
## 備註  
 您可以使用 `<remove>` 項目移除集合中的特定行為。  若要這麼做，只需在 `<remove>` 項目的 `name` 屬性中提供要移除之行為的名稱。  您也可以使用 `<clear>` 項目來清除行為集合的所有內容，確保該行為集合在啟始時就是空的。  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.BehaviorsSection>   
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.EndpointBehaviorElement>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElementCollection>   
 <xref:System.ServiceModel.Configuration.ServiceBehaviorElement>   
 [使用行為來設定與擴充執行階段](../../../../../docs/framework/wcf/extending/configuring-and-extending-the-runtime-with-behaviors.md)   
 [設定用戶端行為](../../../../../docs/framework/wcf/configuring-client-behaviors.md)   
 [指定用戶端執行階段行為](../../../../../docs/framework/wcf/specifying-client-run-time-behavior.md)   
 [指定服務執行階段行為](../../../../../docs/framework/wcf/specifying-service-run-time-behavior.md)   
 [安全性行為](../../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)