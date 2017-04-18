---
title: "&lt;defaultFtpCachePolicy&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<defaultFtpCachePolicy> 項目"
  - "defaultFtpCachePolicy 項目"
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: 13
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 13
---
# &lt;defaultFtpCachePolicy&gt; 項目 (網路設定)
描述 FTP 快取是否使用中，並且描述預設的快取原則。  
  
## 語法  
  
```  
< defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|`policyLevel`|指定 FTP 快取原則。  預設值是 `Default`。|  
  
## policyLevel 屬性  
  
|值|描述|  
|-------|--------|  
|`Default`|如果資源是最新的、內容長度正確，並且有到期、修改和內容長度屬性，則傳回快取的資源。|  
|`BypassCache`|從伺服器傳回資源。|  
|`CacheOnly`|如果內容長度存在，並且符合實體大小，則傳回快取資源。|  
|`CacheIfAvailable`|如果有提供內容長度且其符合項目大小，則傳回快取的資源，否則會從伺服器下載資源並傳回給呼叫端。|  
|`Revalidate`|如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取資源；否則，從伺服器下載資源，並儲存於快取中，然後傳回給呼叫端。|  
|`Reload`|從伺服器下載資源，並儲存於快取中，然後傳回給呼叫端。|  
|`NoCacheNoStore`|如果有快取的資源，則會刪除它。  然後從伺服器下載資源並傳回給呼叫端。|  
|`Revalidate`|如果時間戳記與伺服器上資源的時間戳記相同，則使用資源的快取複本滿足要求，否則，會從伺服器下載該資源，將其呈現給呼叫端，並儲存在快取中。|  
  
### 子項目  
 無。  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
  
## 備註  
  
## 範例  
 下列程式碼範例說明如何指定 `NoCacheNoStore` 的 FTP 快取原則。  
  
```  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        Level="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.Cache>   
 <xref:System.Net.WebRequest>   
 <xref:System.Net.Cache.RequestCacheLevel>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)