---
title: '&lt;快取&gt;'
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 2a9766b826eb7a708b4b4e99b6bd984f9fc76812
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32755210"
---
# <a name="ltcachesgt"></a>&lt;快取&gt;
註冊用於工作階段權杖，權杖重新執行偵測的快取。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<會快取 >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|使用的服務或安全性權杖處理常式集合中註冊一份快取工作階段權杖。|  
|[\<tokenReplayCache >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|使用的服務或安全性權杖處理常式集合中註冊權杖重新執行快取。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
|[\<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性權杖處理常式。|  
  
## <a name="remarks"></a>備註  
 A`<caches>`元素可以指定在服務層級下`<identityConfiguration>`項目或安全性權杖處理常式集合層級下`<securityTokenHandlerConfiguration>`項目。 權杖處理常式集合上的設定會覆寫在服務上指定。  
  
 `<caches>`項目由<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>類別。 設定快取都由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別。  
  
## <a name="example"></a>範例  
 下列 XML 會說明用於保存工作階段安全性權杖的自訂快取的組態 (<xref:System.IdentityModel.Tokens.SessionSecurityToken>)。 組態取自`ClaimsAwareWebFarm`範例。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
