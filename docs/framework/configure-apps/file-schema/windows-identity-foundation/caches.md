---
title: <caches>
ms.date: 03/30/2017
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
author: BrucePerlerMS
ms.openlocfilehash: 791c5be8aa48db2b17a42a216ad2bf5e7b5a4bc1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91189873"
---
# \<caches>

註冊用於會話權杖和權杖重新執行偵測的快取。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<caches>**  
  
## <a name="syntax"></a>Syntax  
  
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
  
|項目|描述|  
|-------------|-----------------|  
|[\<sessionSecurityTokenCache>](sessionsecuritytokencache.md)|使用服務或安全性權杖處理常式集合來註冊會話權杖的快取。|  
|[\<tokenReplayCache>](tokenreplaycache.md)|使用服務或安全性權杖處理常式集合註冊權杖重新執行快取。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
|[\<securityTokenHandlerConfiguration>](securitytokenhandlerconfiguration.md)|提供安全性權杖處理常式集合的設定。|  
  
## <a name="remarks"></a>備註  

 專案 `<caches>` 可以在服務層級的元素底下或在 `<identityConfiguration>` 安全性權杖處理常式集合層級的元素底下指定 `<securityTokenHandlerConfiguration>` 。 權杖處理常式集合上的設定會覆寫服務上指定的設定。  
  
 `<caches>`元素是由 <xref:System.IdentityModel.Configuration.IdentityModelCachesElement> 類別表示。 設定的快取是由 <xref:System.IdentityModel.Configuration.IdentityModelCaches> 類別表示。  
  
## <a name="example"></a>範例  

 下列 XML 會顯示 () 保存會話安全性權杖的自訂快取設定 <xref:System.IdentityModel.Tokens.SessionSecurityToken> 。 設定取自 `ClaimsAwareWebFarm` 範例。  
  
```xml  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```
