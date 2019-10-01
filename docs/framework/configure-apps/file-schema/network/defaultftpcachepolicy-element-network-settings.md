---
title: <defaultFtpCachePolicy> 項目 (網路設定)
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: fd1649edbf7a2c8546992019df667f27df68e02c
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/01/2019
ms.locfileid: "71698322"
---
# <a name="defaultftpcachepolicy-element-network-settings"></a>@no__t 0defaultFtpCachePolicy > 元素（網路設定）
描述 FTP 快取是否作用中，並描述預設的快取原則。  
  
[ **\<configuration>** ](../configuration-element.md)  
&nbsp; @ no__t-1[ **\<system. net >** ](system-net-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3[ **\<requestCaching >** ](requestcaching-element-network-settings.md)  
&nbsp; @ no__t-1 @ no__t-2 @ no__t-3 @ no__t-4 @ no__t-5 **\<defaultFtpCachePolicy >**  
  
## <a name="syntax"></a>語法  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`policyLevel`|指定 FTP 快取原則。 預設值為 `Default`。|  
  
## <a name="policylevel-attribute"></a>policyLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是最新的，則會傳回快取的資源、內容長度是正確的，而且會顯示到期、修改和內容長度屬性。|  
|`BypassCache`|傳回伺服器的資源。|  
|`CacheOnly`|如果內容長度存在且符合專案大小，則傳回快取的資源。|  
|`CacheIfAvailable`|如果提供內容長度且符合專案大小，則傳回快取的資源;否則，資源會從伺服器下載並傳回給呼叫端。|  
|`Revalidate`|如果快取資源的時間戳記與伺服器上資源的時間戳記相同，則傳回快取的資源;否則，資源會從伺服器下載、儲存在快取中，然後傳回給呼叫者。|  
|`Reload`|從伺服器下載資源、將它儲存在快取中，然後將資源傳回給呼叫者。|  
|`NoCacheNoStore`|如果快取的資源已存在，則會予以刪除。 資源會從伺服器下載，並傳回給呼叫端。|  
|`Revalidate`|如果時間戳記與伺服器上資源的時間戳記相同，請使用資源的快取複本來滿足要求;否則，資源會從伺服器下載、呈現給呼叫端，並儲存在快取中。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[requestCaching](requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例顯示如何指定 `NoCacheNoStore` 的 FTP 快取原則。  
  
```xml  
<configuration>  
  <system.net>  
    <requestCaching>  
      <defaultFtpCachePolicy  
        policyLevel="NoCacheNoStore">  
      </defaultFtpCachePolicy>  
    </requestCaching>  
  </system.net>  
</configuration>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.Net.Cache>
- <xref:System.Net.WebRequest>
- <xref:System.Net.Cache.RequestCacheLevel>
- [網路設定結構描述](index.md)
