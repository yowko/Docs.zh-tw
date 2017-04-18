---
title: "&lt;settings&gt; 項目 (網路設定) | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#settings"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<settings> 項目"
  - "settings 項目"
ms.assetid: 189ce989-c39b-427d-b004-6b82a668b931
caps.latest.revision: 21
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 21
---
# &lt;settings&gt; 項目 (網路設定)
為 <xref:System.Net?displayProperty=fullName> 命名空間設定基本的網路選項。  
  
## 語法  
  
```  
  
      <settings>  
..<httpListener> … </httpListener>  
..<httpWebRequest> … </httpWebRequest>  
..<ipv6> … </ipv6>  
..<performanceCounters> … </performanceCounters>  
  <servicePointManager> … </servicePointManager>  
..<socket> … </socket>  
..<webProxyScript> … </webProxyScript>  
</settings>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
 無。  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[httpListener](../../../../../docs/framework/configure-apps/file-schema/network/httplistener-element-network-settings.md)|自訂 <xref:System.Net.HttpListener> 類別所使用的參數。|  
|[httpWebRequest](../../../../../docs/framework/configure-apps/file-schema/network/httpwebrequest-element-network-settings.md)|自訂 Web 要求參數。|  
|[ipv6](../../../../../docs/framework/configure-apps/file-schema/network/ipv6-element-network-settings.md)|啟用網際網路通訊協定第 6 版 \(IPv6\) 支援。|  
|[\<performanceCounter\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/performancecounter-element-network-settings.md)|啟用網路效能計數器。|  
|[servicePointManager](../../../../../docs/framework/configure-apps/file-schema/network/servicepointmanager-element-network-settings.md)|設定網路資源連線。|  
|[通訊端](../../../../../docs/framework/configure-apps/file-schema/network/socket-element-network-settings.md)|指定通訊端操作是否使用完成通訊埠。|  
|[\<webProxyScript\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/webproxyscript-element-network-settings.md)|設定用來探索 Web Proxy 的指令碼的特性。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何連接至網路的設定。|  
  
## 備註  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 請參閱  
 <xref:System.Net?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)