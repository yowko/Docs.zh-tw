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
ms.openlocfilehash: af290e4b9258a08425a15e297ff538502edea916
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59164849"
---
# <a name="requestcaching-element-network-settings"></a>\<requestCaching> 項目 (網路設定)
控制網路要求的快取機制。  
  
 \<configuration>  
\<system.net>  
\<requestCaching>  
  
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
|`isPrivateCache`|指定是否快取之間提供隔離不同使用者的資訊。 預設值為 `true`。 這個值應該是`false`中介層應用程式。|  
|`disableAllCaching`|指定，快取已停用所有的 Web 回應，而且不能以程式設計方式覆寫。|  
|`defaultPolicyLevel`|<xref:System.Net.Cache.RequestCacheLevel> 列舉中的其中一個值。 預設值為 `BypassCache`。|  
|`unspecifiedMaximumAge`|指定預設的時間之後，內容會標示為已過期。|  
  
## <a name="policylevel-attribute"></a>Securityclasses 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是新的、 內容長度正確無誤，且到期、 修改和內容長度屬性都存在，則會傳回快取的資源。|  
|`BypassCache`|從伺服器傳回的資源。|  
|`CacheOnly`|如果內容長度，且符合項目大小，則會傳回快取的資源。|  
|`CacheIfAvailable`|如果內容長度提供，且符合項目大小; 會傳回快取的資源否則，資源從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果快取的資源的時間戳記是伺服器上之資源的時間戳記相同，會傳回快取的資源否則資源下載自伺服器，並儲存在快取，並傳回給呼叫者。|  
|`Reload`|從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。|  
|`NoCacheNoStore`|如果快取的資源存在，則會將它刪除。 資源從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果時間戳記伺服器上之資源的時間戳記相同，使用資源的快取的複本滿足要求否則資源下載自伺服器，向呼叫端，並會儲存在快取中，|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[defaultHttpCachePolicy](../../../../../docs/framework/configure-apps/file-schema/network/defaulthttpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 HTTP 快取是否作用中，並且描述的預設快取原則。|  
|[\<defaultFtpCachePolicy > 項目 （網路設定）](../../../../../docs/framework/configure-apps/file-schema/network/defaultftpcachepolicy-element-network-settings.md)|選擇性項目。<br /><br /> 描述 FTP 快取是否作用中，並且描述的預設快取原則。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[system.net](../../../../../docs/framework/configure-apps/file-schema/network/system-net-element-network-settings.md)|包含會指定 .NET Framework 如何連接至網路的設定。|  
  
## <a name="example"></a>範例  
 下列範例示範如何停用所有快取。  
  
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
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
