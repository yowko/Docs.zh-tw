---
title: "啟用的 &lt;diagnostics&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1486e0eb-fe2a-46c3-b584-c924889477dd
caps.latest.revision: 7
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 7
---
# 啟用的 &lt;diagnostics&gt;
設定 [!INCLUDE[indigo1](../../../../../includes/indigo1-md.md)] 接聽程式的診斷功能。  
  
## 語法  
  
```  
  
<configuration>  
   <system.serviceModel.activation>  
       <diagnostics performanceCountersEnabled="Boolean" />  
   </system.serviceModel.activation>  
</configuration>  
```  
  
## 類型  
 `Type`  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`performanceCountersEnabled`|布林值，指出是否啟用效能計數器以供診斷用途。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.serviceModel.activation\>](../../../../../docs/framework/configure-apps/file-schema/wcf/system-servicemodel-activation.md)|包含 SMSvcHost.exe 接聽程式處理序的組態設定。|  
  
## 請參閱  
 <xref:System.ServiceModel.Activation.Configuration.DiagnosticSection>