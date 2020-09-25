---
title: <requestCaching> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#requestCaching
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching
helpviewer_keywords:
- requestCaching element
- <requestCaching> element
ms.assetid: 9962a2fe-cbda-41a6-9377-571811eaea84
ms.openlocfilehash: 3eb32b7ae643efdb19892410b669c1e7ff80e0ad
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91174156"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching> 項目 (網路設定)

控制網路要求的快取機制。  
  
[**\<configuration>**](../configuration-element.md)  
&nbsp;&nbsp;[**\<system.net>**](system-net-element-network-settings.md)  
&nbsp;&nbsp;&nbsp;&nbsp;**\<requestCaching>**  
  
## <a name="syntax"></a>Syntax  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh:mm:ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  

 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`isPrivateCache`|指定快取是否提供不同使用者資訊之間的隔離。 預設值是 `true`。 `false`中介層應用程式的這個值應該是。|  
|`disableAllCaching`|指定停用所有 Web 回應的快取，而且無法以程式設計方式覆寫。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。 預設值是 `BypassCache`。|  
|`unspecifiedMaximumAge`|指定將內容標示為已過期的預設時間。|  
  
## <a name="policylevel-attribute"></a>policyLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是最新的，則傳回快取的資源、內容長度正確，而且存在到期、修改和內容長度屬性。|  
|`BypassCache`|從伺服器傳回資源。|  
|`CacheOnly`|如果內容長度存在且符合專案大小，則傳回快取的資源。|  
|`CacheIfAvailable`|如果提供內容長度且符合專案大小，則會傳回快取的資源;否則，就會從伺服器下載資源，並傳回給呼叫端。|  
|`Revalidate`|如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載，儲存在快取中，並傳回給呼叫端。|  
|`Reload`|從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。|  
|`NoCacheNoStore`|如果有快取的資源存在，則會將其刪除。 資源會從伺服器下載，並傳回給呼叫端。|  
|`Revalidate`|如果時間戳記與伺服器上資源的時間戳記相同，請使用資源的快取複本來滿足要求;否則，就會從伺服器下載資源、向呼叫端顯示資源，然後儲存在快取中。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 HTTP 快取是否為作用中，並描述預設的快取原則。|  
|[\<defaultFtpCachePolicy> (網路設定的元素) ](defaultftpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 FTP 快取是否為作用中，並描述預設的快取原則。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[system.net](system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="example"></a>範例  

 下列範例顯示如何停用所有快取。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching  
      disableAllCaching="true"  
    />  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Cache?displayProperty=nameWithType>
- [網路設定結構描述](index.md)
