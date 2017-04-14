---
title: "&lt;transportConfigurationTypes&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 929c8b0a-5460-4f66-a098-2cb8d4e10b69
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# &lt;transportConfigurationTypes&gt;
代表組態項目的集合，這些項目會識別特定傳輸的類型。  這可以用來加入自訂 WAS 通訊協定。  
  
## 語法  
  
```  
  
<serviceHostingEnvironment>   
   <transportConfigurationTypes>  
      <add name="String"  
               transportConfigurationType="String"/>   
   </transportConfigurationTypes>  
</serviceHostingEnvironment>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|傳輸的名稱|  
|transportConfigurationType|實作傳輸的型別|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<add\>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-transportconfigurationtype.md)|新增組態項目，此項目會識別特定傳輸的類型。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<serviceHostingEnvironment\>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicehostingenvironment.md)|定義服務裝載環境為特定傳輸產生的類型。|  
  
## 請參閱  
 <xref:System.ServiceModel.Configuration.ServiceHostingEnvironmentSection>   
 <xref:System.ServiceModel.ServiceHostingEnvironment>   
 <xref:System.ServiceModel.Configuration.TransportConfigurationTypeElementCollection>   
 [裝載](../../../../../docs/framework/wcf/feature-details/hosting.md)