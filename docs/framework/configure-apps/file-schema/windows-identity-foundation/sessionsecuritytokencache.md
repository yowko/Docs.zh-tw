---
title: "&lt;sessionSecurityTokenCache&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: d43e676c-0153-485c-ab31-0257a2db7507
caps.latest.revision: 8
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 7
---
# &lt;sessionSecurityTokenCache&gt;
工作階段權杖之快取使用註冊的服務或安全性語彙基元的處理常式集合。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration>  
    <caches>  
      <sessionSecurityTokenCache type=xs:string>  
      </sessionSecurityTokenCache>  
    </caches>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|type|型別衍生自<xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>類別。  如需有關如何指定自訂的`type`，請參閱[Custom Type References](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_CustomTypeReferences)。|  
  
### 子項目  
 None  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊服務或安全性語彙基元的處理常式集合所使用的快取。|  
  
## 範例  
 下列 XML 程式碼會顯示自訂的快取來存放工作階段安全性語彙基元的設定 \(<xref:System.IdentityModel.Tokens.SessionSecurityToken>\)。  組態來自`ClaimsAwareWebFarm`範例。  如需有關這個範例的詳細資訊，請參閱[WIF 程式碼範例索引](../../../../../docs/framework/security/wif-code-sample-index.md)。  
  
```  
<caches>  
  <sessionSecurityTokenCache type="CacheLibrary.SharedSessionSecurityTokenCache, CacheLibrary">  
    <!--cacheServiceAddress points to the centralized session security token cache service running in the web farm.-->  
    <cacheServiceAddress url="http://localhost:4161/SessionSecurityTokenCacheService.svc" />  
  </sessionSecurityTokenCache>  
</caches>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Tokens.SessionSecurityTokenCache>