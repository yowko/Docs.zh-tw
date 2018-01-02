---
title: "&lt;requestCaching&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
caps.latest.revision: "20"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 35665bd79a14b74e192fed439e935936411d85c3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltrequestcachinggt-element-network-settings"></a>&lt;requestCaching&gt;項目 （網路設定）
控制網路要求的快取機制。  
  
 \<configuration>  
\<system.net >  
\<requestCaching >  
  
## <a name="syntax"></a>語法  
  
```xml  
      <requestCaching>  
        isPrivateCache ="true|false"  
        disableAllCaching="true|false"  
        defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
        unspecifiedMaximumAge= "d.hh.mm.ss">  
          <defaultHttpCachePolicy> … </defaultHttpCachePolicy>  
          <defaultFtpCachePolicy> … </defaultFtpCachePolicy>  
      </requestCaching>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`isPrivateCache`|指定是否快取之間提供隔離不同使用者的資訊。 預設值是 `true`。 這個值應該是`false`中介層應用程式。|  
|`disableAllCaching`|指定，快取所有的 Web 回應已停用，而且不能以程式設計方式覆寫。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。 預設值是 `BypassCache`。|  
|`unspecifiedMaximumAge`|指定預設的時間之後的內容標示為已過期。|  
  
## <a name="policylevel-attribute"></a>policyLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是新的內容長度正確無誤，，到期、 修改和內容長度屬性會，傳回快取的資源。|  
|`BypassCache`|從伺服器傳回的資源。|  
|`CacheOnly`|如果內容的長度且相符的項目大小，則傳回快取的資源。|  
|`CacheIfAvailable`|如果已提供的內容長度，而相符的項目大小;，傳回的快取的資源否則，資源會從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果快取資源的時間戳記為相同伺服器上資源的時間戳記會傳回快取的資源否則，資源下載自伺服器，並儲存在快取，並傳回給呼叫者。|  
|`Reload`|從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。|  
|`NoCacheNoStore`|如果快取的資源存在，會將其刪除。 資源從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果時間戳記是相同的時間戳記伺服器; 上的資源使用資源的快取的副本滿足要求否則，會在伺服器上，向呼叫者，從下載資源，以及儲存在快取中，|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 說明 HTTP 快取是否作用中，並且描述預設的快取原則。|  
|[\<defaultFtpCachePolicy > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 FTP 快取是否作用中，並且描述預設的快取原則。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="example"></a>範例  
 下列範例會示範如何停用所有快取。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.Cache?displayProperty=nameWithType>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
