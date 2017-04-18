---
title: "&lt;caches&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 4651091b-3a20-40d8-b293-4408c0710143
caps.latest.revision: 7
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;caches&gt;
註冊快取使用的工作階段權杖和語彙基元重新執行偵測。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
 None  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<sessionSecurityTokenCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/sessionsecuritytokencache.md)|工作階段權杖之快取使用註冊的服務或安全性語彙基元的處理常式集合。|  
|[\<tokenReplayCache\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaycache.md)|語彙基元重新顯示快取使用註冊的服務或安全性語彙基元的處理常式集合。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<identityConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級識別設定。|  
|[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)|提供組態集合的安全性語彙基元的處理常式。|  
  
## 備註  
 A `<caches>`項目可以指定在服務層級下`<identityConfiguration>`項目或之下的安全性語彙基元的處理常式集合層級上`<securityTokenHandlerConfiguration>`項目。  在語彙基元的處理常式集合上的設定會覆寫所指定的服務。  
  
 `<caches>`項目會以<xref:System.IdentityModel.Configuration.IdentityModelCachesElement>類別。  已設定的快取原則由<xref:System.IdentityModel.Configuration.IdentityModelCaches>類別。  
  
## 範例  
 下列 XML 程式碼會顯示自訂的快取來存放工作階段安全性語彙基元的設定 \(<xref:System.IdentityModel.Tokens.SessionSecurityToken>\)。  組態來自`ClaimsAwareWebFarm`範例。  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```