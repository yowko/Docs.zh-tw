---
title: "&lt;defaultHttpCachePolicy&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultHttpCachePolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultHttpCachePolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultHttpCachePolicy> 項目"
  - "defaultHttpCachePolicy 項目"
ms.assetid: 2c1247d0-39b0-4c12-919a-a925ce075c79
caps.latest.revision: 19
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 19
---
# &lt;defaultHttpCachePolicy&gt; 項目 (網路設定)
描述 HTTP 快取是否使用中，並且描述預設的快取原則。  
  
## 語法  
  
```  
< defaultHttpCachePolicy  
  policyLevel="BypassCache|Default"  
  minimumFresh="d.hh:mm:ss"|"minValue"  
  maximumAge  ="d.hh:mm:ss"|"maxValue"  
  maximumStale="d.hh:mm:ss"|"maxValue"  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`maximumAge`|指定快取物件標示為過期之前的最大時間間隔。|  
|`maximumStale`|指定快取物件標示為過期之前，超過所計算最近時間的最長時間。|  
|`minimumFresh`|指定快取物件視為是新的之最短時間。|  
|`policyLevel`|指定快取原則是否為自動，或是否略過快取。  預設值是 `BypassCache`。|  
  
### 子項目  
 無  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
  
## 備註  
 `policyLevel` 屬性的值為 `BypassCache` 或 `Default`。  
  
 `maximumAge`項目、`maximumStale` 項目和 `minimumFresh` 項目的值為明確的時間間隔，其格式為 *d*.*hh*:*mm*:*ss*  \(天、小時、分鐘和秒\)，或是依適當的情況選擇常數 :`minValue`或`maxValue`。  
  
## 組態檔  
 這個項目可以用於應用程式組態檔或電腦組態檔 \(Machine.config\)。  
  
## 範例  
 下列程式碼範例說明如何指定最短最新時間為六天、最長歷經時間為兩天，以及最長過時時間為四小時。  
  
```  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultHttpCachePolicy>  
        <set minimumFresh="0.06:00:00" />  
        <set maximumAge  ="2.00:00:00" />  
        <set maximumStale="0.04:00:00" />  
      </defaultHttpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.Cache>   
 <xref:System.Net.WebRequest>   
 <xref:System.Net.Cache.RequestCacheLevel>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)