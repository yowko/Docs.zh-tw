---
title: "&lt;defaultFtpCachePolicy&gt;項目 （網路設定）"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#defaultFtpCachePolicy
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.net/requestCaching/defaultFtpCachePolicy
helpviewer_keywords:
- <defaultFtpCachePolicy> element
- defaultFtpCachePolicy element
ms.assetid: 0eb0c5cb-dd97-484d-8614-785e88877abb
caps.latest.revision: "13"
author: mcleblanc
ms.author: markl
manager: markl
ms.workload: dotnet
ms.openlocfilehash: 0c62be73db6d9d0b6ce67dd87021c589502d5fec
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltdefaultftpcachepolicygt-element-network-settings"></a>&lt;defaultFtpCachePolicy&gt;項目 （網路設定）
描述 FTP 快取是否作用中，並且描述預設的快取原則。  
  
 \<configuration>  
\<system.net >  
\<requestCaching >  
\<defaultFtpCachePolicy >  
  
## <a name="syntax"></a>語法  
  
```xml  
<defaultFtpCachePolicy  
  policyLevel="BypassCache|Default|CacheOnly|CacheIfAvailable|Revalidate|Reload|NoCacheNoStore|Revalidate"  
/>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|`policyLevel`|指定 FTP 快取原則。 預設值是 `Default`。|  
  
## <a name="policylevel-attribute"></a>policyLevel 屬性  
  
|值|描述|  
|-----------|-----------------|  
|`Default`|如果資源是新的內容長度正確無誤，，到期、 修改和內容長度屬性會，傳回快取的資源。|  
|`BypassCache`|從伺服器傳回的資源。|  
|`CacheOnly`|如果內容的長度且相符的項目大小，則傳回快取的資源。|  
|`CacheIfAvailable`|如果已提供的內容長度，而相符的項目大小;，傳回的快取的資源否則，資源會從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果快取資源的時間戳記為相同伺服器上資源的時間戳記會傳回快取的資源否則，資源是從伺服器下載、 儲存在快取，並傳回給呼叫者。|  
|`Reload`|從伺服器下載的資源、 將它儲存在快取，並傳回給呼叫端。|  
|`NoCacheNoStore`|如果快取的資源存在，會將其刪除。 資源從伺服器下載，並傳回給呼叫者。|  
|`Revalidate`|如果時間戳記是相同的時間戳記伺服器; 上的資源使用資源的快取的副本滿足要求否則，資源會從伺服器下載，向呼叫者，並儲存在快取。|  
  
### <a name="child-elements"></a>子元素  
 無。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[requestCaching](../../../../../docs/framework/configure-apps/file-schema/network/requestcaching-element-network-settings.md)|控制網路要求的快取機制。|  
  
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
  
## <a name="see-also"></a>請參閱  
 <xref:System.Net.Cache>  
 <xref:System.Net.WebRequest>  
 <xref:System.Net.Cache.RequestCacheLevel>  
 [網路設定結構描述](../../../../../docs/framework/configure-apps/file-schema/network/index.md)
