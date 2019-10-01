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
ms.openlocfilehash: f0979d2e0caeb0b22b90572aef0ad53235020f1d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71697831"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching> 項目 (網路設定)
控制網路要求的快取機制。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 **\<requestCaching >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<requestCaching  
  isPrivateCache ="true|false"  
  disableAllCaching="true|false"  
  defaultPolicyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
  unspecifiedMaximumAge= "d.hh.mm.ss">  
    <defaultHttpCachePolicy>...</defaultHttpCachePolicy>  
    <defaultFtpCachePolicy>...</defaultFtpCachePolicy>  
</requestCaching>
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`isPrivateCache`|指定快取是否在不同使用者的資訊之間提供隔離。 預設值為 `true`。 中介層應用程式的這個值應該 `false`。|  
|`disableAllCaching`|指定停用所有 Web 回應的快取，而且無法以程式設計方式覆寫。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。 預設值為 `BypassCache`。|  
|`unspecifiedMaximumAge`|指定將內容標示為過期的預設時間。|  
  
## <a name="policylevel-attribute"></a>policyLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是最新的，則會傳回快取的資源、內容長度是正確的，而且會顯示到期、修改和內容長度屬性。|  
|`BypassCache`|傳回伺服器的資源。|  
|`CacheOnly`|如果內容長度存在且符合專案大小，則傳回快取的資源。|  
|`CacheIfAvailable`|如果提供內容長度且符合專案大小，則傳回快取的資源;否則，資源會從伺服器下載並傳回給呼叫端。|  
|`Revalidate`|如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載並儲存在快取中，並傳回給呼叫端。|  
|`Reload`|從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。|  
|`NoCacheNoStore`|如果快取的資源已存在，則會予以刪除。 資源會從伺服器下載，並傳回給呼叫端。|  
|`Revalidate`|如果時間戳記與伺服器上資源的時間戳記相同，請使用資源的快取複本來滿足要求;否則，資源會從伺服器下載、呈現給呼叫端，並儲存在快取中。|  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](defaulthttpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 HTTP 快取是否作用中，並描述預設的快取原則。|  
|[@no__t 1defaultFtpCachePolicy > 元素（網路設定）](defaultftpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 FTP 快取是否作用中，並描述預設的快取原則。|  
  
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
