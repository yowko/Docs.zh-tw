---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 80f435b52fd7657c5cd44538028d6080beffe0b5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252153"
---
# \<caches>
註冊用於會話權杖和權杖重新執行偵測的快取。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
 無  
  
### <a name="child-elements"></a>子元素  
  
|元素|描述|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|向服務或安全性權杖處理常式集合註冊會話權杖的快取。|  
|[\<tokenReplayCache>](tokenreplaycache.md)|向服務或安全性權杖處理常式集合註冊權杖重新執行快取。|  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  
 `<caches>`元素可以在專案下的服務層級或專案底下 `<identityConfiguration>` 的安全性權杖處理常式集合層級指定 `<securityTokenHandlerConfiguration>` 。 權杖處理常式集合上的設定會覆寫在服務上指定的值。  
  
 `<caches>`元素是由 <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> 類別表示。 設定的快取是由 <xref:System.IdentityModel.Configuration.IdentityModelCaches> 類別表示。  
  
## <a name="example"></a>範例  
 下列 XML 顯示用來保存會話安全性權杖（）的自訂快取設定 <xref:System.IdentityModel.Tokens.SessionSecurityToken> 。 此設定取自 `ClaimsAwareWebFarm` 範例。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
