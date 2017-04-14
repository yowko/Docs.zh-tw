---
title: "&lt;requestCaching&gt; 項目 (網路設定) | Microsoft Docs"
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
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching"
  - "http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching"
dev_langs: 
  - "VB"
  - "CSharp"
  - "C++"
  - "jsharp"
helpviewer_keywords: 
  - "<requestCaching> 項目"
  - "requestCaching 項目"
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: 20
author: "mcleblanc"
ms.author: "markl"
manager: "markl"
caps.handback.revision: 20
---
# &lt;requestCaching&gt; 項目 (網路設定)
控制網路要求的快取機制。  
  
## 語法  
  
```  
  
      <requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss""  
  <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
  <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
/>  
```  
  
## 屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|說明|  
|--------|--------|  
|`isPrivateCache`|指定快取是否會在不同使用者的資訊之間提供隔離。  預設值是 `true`。  對於中介層 \(Middle Tier\) 應用程式而言，此值應該是 `false`。|  
|`disableAllCaching`|指定是否針對所有 Web 回應停用快取，並且不能以程式設計的方式覆寫快取。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列舉型別中的其中一個值。  預設值是 `BypassCache`。|  
|`unspecifiedMaximumAge`|指定要在預設時間過後，將內容標示為已過期。|  
  
## policyLevel 屬性  
  
|值|說明|  
|-------|--------|  
|`Default`|如果資源是最新的、內容長度正確，並且有到期、修改和內容長度屬性，則傳回快取的資源。|  
|`BypassCache`|從伺服器傳回資源。|  
|`CacheOnly`|如果內容長度存在，並且符合實體大小，則傳回快取資源。|  
|`CacheIfAvailable`|如果有提供內容長度且其符合項目大小，則傳回快取的資源，否則會從伺服器下載資源並傳回給呼叫端。|  
|`Revalidate`|如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取資源；否則，從伺服器下載資源，並儲存於快取中，然後傳回給呼叫端。|  
|`Reload`|從伺服器下載資源，並儲存於快取中，然後傳回給呼叫端。|  
|`NoCacheNoStore`|如果有快取的資源，則會刪除它。  然後從伺服器下載資源並傳回給呼叫端。|  
|`Revalidate`|如果時間戳記與伺服器上資源的時間戳記相同，則使用資源的快取複本滿足要求；否則，從伺服器下載資源，再呈現給呼叫端，然後儲存於快取中。|  
  
### 子項目  
  
|元素|說明|  
|--------|--------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 HTTP 快取是否使用中，並且描述預設的快取原則。|  
|[\<defaultFtpCachePolicy\> 項目 \(網路設定\)](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 FTP 快取是否使用中，並且描述預設的快取原則。|  
  
### 父項目  
  
|元素|說明|  
|--------|--------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含指定 .NET Framework 如何連接至網路的設定。|  
  
## 範例  
 下列程式碼範例會示範如何停用所有快取。  
  
```  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## 請參閱  
 <xref:System.Net.Cache?displayProperty=fullName>   
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)