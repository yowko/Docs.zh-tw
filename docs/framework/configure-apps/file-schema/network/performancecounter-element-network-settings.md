---
title: "&lt;performanceCounter&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/settings/performanceCounters"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#performanceCounters"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<performanceCounter> 項目"
  - "performanceCounter 項目"
ms.assetid: 3afa1586-e1b8-473d-8985-c3fc90cf561b
caps.latest.revision: 11
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 11
---
# &lt;performanceCounter&gt; 項目 (網路設定)
啟用或停用網路效能計數器。  
  
## 語法  
  
```  
<performanceCounters  
  enabled="true|false"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`enabled`|指定是否啟用網路效能計數器。  預設值是 `false`。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[設定](../../../../../docs/framework/configure-apps/file-schema/network/settings-element-network-settings.md)|為 <xref:System.Net> 命名空間設定基本的網路選項。|  
  
## 備註  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
 在要使用的組態檔中必須啟用網路效能計數器。  所有的網路效能計數器都是使用組態檔中的單一設定來啟用或停用。  無法啟用或停用個別的網路效能計數器。  如需特定網路效能計數器的詳細資訊，請參閱[Networking Performance Counters](http://msdn.microsoft.com/zh-tw/d1860235-f643-46ae-846c-ff0ed8b0e3cd)。  
  
 預設值為該網路效能計數器為停用。  
  
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=fullName> 屬性可用來從適用的組態檔中取得 **enabled** 屬性的目前值。  
  
## 範例  
 下列程式碼範例示範如何設定 <xref:System.Net> 和相關的命名空間，以啟用網路效能計數器。  
  
```  
<configuration>  
  <system.net>  
    <settings>  
      <performanceCounters  
        enabled="true"  
      />  
    </settings>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.Configuration.PerformanceCountersElement?displayProperty=fullName>   
 <xref:System.Net.Configuration.PerformanceCountersElement.Enabled%2A?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)   
 [Networking Performance Counters](http://msdn.microsoft.com/zh-tw/d1860235-f643-46ae-846c-ff0ed8b0e3cd)