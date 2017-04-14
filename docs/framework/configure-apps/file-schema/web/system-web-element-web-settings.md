---
title: "&lt;system.web&gt; 項目 (Web 設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<system.Web> 項目"
  - "ASP.NET 組態系統"
  - "組態檔 [ASP.NET]"
  - "system.Web 項目"
  - "Web.config 組態檔 [ASP.NET]"
ms.assetid: 24c4cf4f-ad32-42b2-b040-8e4549e2855e
caps.latest.revision: 9
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 9
---
# &lt;system.web&gt; 項目 (Web 設定)
包含 ASP.NET 裝載層如何管理整個處理序行為的相關資訊。  
  
## 語法  
  
```  
<system.web>  
</system.web>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<applicationPool\>](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)|指定 aspnet.config 檔中的 IIS 應用程式集區組態設定。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<configuration\>](../../../../../docs/framework/configure-apps/file-schema/configuration-element.md)|指定 Common Language Runtime 和 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 應用程式所使用之每個組態檔中的根項目。|  
  
## 備註  
 自 [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] 起，已將 `system.web` 項目及其子項目 `applicationPool` 加入至 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)]。  當您在「整合」模式中執行 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] \(含\) 以後版本時，這個項目組合可讓您設定 ASP.NET 管理執行緒的方式，以及在 IIS 應用程式集區中裝載 ASP.NET 時，ASP.NET 佇列要求的方式。  如果您在「傳統」或 ISAPI 模式中執行 [!INCLUDE[iisver](../../../../../includes/iisver-md.md)] \(含\) 以後版本，則會忽略這些設定。  
  
## 範例  
 下列範例示範在 IIS 應用程式集區中裝載 ASP.NET 時，如何在 aspnet.config 檔中設定 ASP.NET 的整個處理序行為。  範例假設 IIS 是在「整合」模型中執行，而且應用程式使用的是 [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] \(含\) 以後版本。  這個行為不會在 [!INCLUDE[net_v35SP1_short](../../../../../includes/net-v35sp1-short-md.md)] 之前的 [!INCLUDE[dnprdnshort](../../../../../includes/dnprdnshort-md.md)] 版本中發生。  範例中的值是預設值。  
  
```  
<configuration>  
  <system.web>  
    <applicationPool   
        maxConcurrentRequestsPerCPU="5000"   
        maxConcurrentThreadsPerCPU="0"   
        requestQueueLimit="5000" />  
  </system.web>  
</configuration>  
```  
  
## 項目資訊  
  
|||  
|-|-|  
|命名空間||  
|結構描述名稱||  
|驗證檔||  
|可以是空白||  
  
## 請參閱  
 [\<applicationPool\> 項目 \(Web 設定\)](../../../../../docs/framework/configure-apps/file-schema/web/applicationpool-element-web-settings.md)