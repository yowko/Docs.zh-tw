---
title: "&lt;identityConfiguration&gt; | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: 13
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 13
---
# &lt;identityConfiguration&gt;
指定服務層級識別設定。  
  
## 語法  
  
```  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## 屬性和項目  
 下列章節會說明屬性、子項目和父項目。  
  
### 屬性  
  
|屬性|描述|  
|--------|--------|  
|name|識別組態區段的名稱。  您可以使用這個名稱來參考特定的組態區段。  如果沒有`name`屬性指定，則區段會定義預設的設定。  被動聯盟案例中，皆使用預設的設定。  如需詳細資訊，請參閱 [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 項目。|  
|saveBootstrapContext|指定啟動程序載入的語彙基元是否應該包含在工作階段權杖。  可能也設定值對語彙基元的處理常式的集合物件藉由設定`saveBootstrapContext`在[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。  在語彙基元的處理常式集合上所設定的值會覆寫服務上所設定的值。|  
|maximumClockSkew|A <xref:System.TimeSpan> ，指定允許的最大時鐘扭曲。  執行即時作業，例如驗證登入工作階段的到期時間時，控制允許的最大時鐘扭曲。  預設值是 5 分鐘，"00: 05: 00"。  如需有關如何指定<xref:System.TimeSpan>的值，請參閱[Timespan Values](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md#BKMK_TimespanValues)。  最大時鐘扭曲可能也設定對語彙基元的處理常式的集合物件藉由設定`maximumClockSkew`在[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。  在語彙基元的處理常式集合上所設定的值會覆寫服務上所設定的值。|  
  
### 子項目  
  
|項目|描述|  
|--------|--------|  
|[\<caches\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊快取使用的工作階段權杖和語彙基元重新執行偵測。  可以指定在服務層級，或在安全性語彙基元的處理常式集合。  選擇項。|  
|[\<certificateValidation\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制的設定，用來驗證憑證的語彙基元的處理常式。  可以指定在服務層級，或在安全性語彙基元的處理常式集合。  選擇項。|  
|[\<claimsAuthenticationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|註冊連入宣告宣告驗證管理的者。  選擇項。|  
|[\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|註冊連入宣告的宣告授權管理員。  選擇項。|  
|[\<claimTypeRequired\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|指定的連入安全性權杖的必要宣告集合。  選擇項。|  
|[\<securityTokenHandlers\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定安全性語彙基元的處理常式的集合。  您可以指定零個或更多的安全性語彙基元的處理常式的集合。  選擇項。|  
|[\<tokenReplayDetection\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|啟用語彙基元重新執行偵測，並指定語彙基元的到期時間。  可以指定在服務層級，或在安全性語彙基元的處理常式集合。  選擇項。|  
  
### 父項目  
  
|項目|描述|  
|--------|--------|  
|[\<system.identityModel\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|提供組態對於啟用應用程式中的 Windows 識別基礎 \(WIF\) 選項。|  
  
## 備註  
 您可以定義組態，每一個都有唯一的名稱，多個識別。  行為如下所示：  
  
1.  如果沒有`<identityConfiguration>`在指定項目。  預設身分的設定，在執行階段建立並填入預設值。  
  
2.  如果有一個`<identityConfiguration>`在指定項目。  它是預設身分的設定。  它並不重要無論它是具名或未命名的。  
  
3.  如果多個`<identityConfiguration>`所指定的項目。  未命名的項目會指定預設身分的設定。  建議當您指定多個`<identityConfiguration>`元素，其中一人應該是未命名。  
  
> [!WARNING]
>  如果您指定多個`<identityConfiguration>`元素，其中一人應該是未命名。  未命名的項目將會預設身分的設定。  
  
 控制台中的一些`<identityConfiguration>`安全性語彙基元的處理常式集合上的設定，或是在個別的安全性語彙基元的處理常式的設定值，可以覆寫項目。  
  
> [!IMPORTANT]
>  當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別來提供您的程式碼所參考的識別身份組態中的宣告式存取控制`<federationConfiguration>`元素設定了宣告授權管理員和原則，用來製作授權決策。  都是如此，即使是在不是被動 Web 的案例，例如 \[Windows 通訊資格應用程式\] 或 \[不是以 Web 為基礎的應用程式的案例。  如果應用程式不是被動的 Web 應用程式中， [\<claimsAuthorizationManager\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)項目 \(與其子原則項目，如果有的話\) 的參考的識別設定所套用的唯一設定。  會忽略所有其他設定。  如需詳細資訊，請參閱 [\<federationConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md) 項目。  
  
 `<identityConfiguration>`項目會以<xref:System.IdentityModel.Configuration.IdentityConfigurationElement>類別。  已識別的組態區段由<xref:System.IdentityModel.Configuration.IdentityConfiguration>類別。  
  
> [!IMPORTANT]
>  指定下列項目作為子項目的`<identityConfiguration>`項目已過時，不過行為還是支援回溯相容性。  這些項目，相反地，需指定在[\<securityTokenHandlerConfiguration\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。  
>   
>  -   [\<audienceUris\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver\>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## 範例  
 下列範例會建立一個名為"alternateConfiguration"的身分設定。  識別組態會指定預設設定。  
  
```  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## 請參閱  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>   
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>