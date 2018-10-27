---
title: '&lt;defaultFtpCachePolicy&gt;項目 （網路設定）'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
ms.openlocfilehash: a8c71551adc2b88b5300994134eaec329a083709
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50188283"
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultFtpCachePolicy&gt;項目 （網路設定）
描述 FTP 快取是否作用中，並且描述的預設快取原則。  
  
 \<configuration>  
\<system.net>  
\<Requestcaching> >  
\<defaultFtpCachePolicy >  
  
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
|`policyLevel`|指定 FTP 快取原則。 預設值是 `Default`。|  
  
## <a name="policylevel-attribute"></a>Securityclasses 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是新的、 內容長度正確無誤，且到期、 修改和內容長度屬性都存在，則會傳回快取的資源。|  
|`BypassCache`|從伺服器傳回的資源。|  
|`CacheOnly`|如果內容長度，且符合項目大小，則會傳回快取的資源。|  
|`CacheIfAvailable`|如果內容長度提供，且符合項目大小; 會傳回快取的資源否則，資源從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果快取的資源的時間戳記是伺服器上之資源的時間戳記相同，會傳回快取的資源否則為資源是從伺服器下載、 儲存在快取，並傳回給呼叫端。|  
|`Reload`|從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。|  
|`NoCacheNoStore`|如果快取的資源存在，則會將它刪除。 資源從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果時間戳記伺服器上之資源的時間戳記相同，使用資源的快取的複本滿足要求否則，資源是從伺服器下載、 呈現給呼叫者，和存放在快取。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[Requestcaching>](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
  
## <a name="remarks"></a>備註  
  
## <a name="example"></a>範例  
 下列範例示範如何指定快取原則的 FTP `NoCacheNoStore`。  
  
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
- [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
