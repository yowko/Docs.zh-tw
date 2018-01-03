---
title: '&lt;identityConfiguration&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
caps.latest.revision: "13"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 48f9eef329f5d2e0e751fd2a03b0d3af9ddc355c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
指定服務層級身分識別設定。  
  
 \<system.identityModel >  
\<identityConfiguration >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration  
      name=xs:string  
      saveBootstrapContext=xs:boolean>  
      maximumClockSkew=TimeSpan >  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|name|身分識別組態區段的名稱。 您可以使用此名稱來參考特定的組態區段。 如果沒有`name`屬性指定，則 [] 區段中定義的預設組態。 被動同盟案例的一律使用預設組態。 如需詳細資訊，請參閱[ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。|  
|saveBootstrapContext|指定啟動程序的語彙基元是否應該包含在工作階段權杖。 值可能也會設定權杖處理常式集合的設定`saveBootstrapContext`屬性[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。 權杖處理常式集合上設定的值會覆寫在服務上設定的值。|  
|maximumClockSkew|A <xref:System.TimeSpan> ，指定最大允許的時鐘誤差。 執行時間緊迫的作業，例如先驗證登入工作階段的到期時間時，控制允許的最大時鐘誤差。 預設值是 5 分鐘，"00: 05:00"。 如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。 最大時鐘誤差可能也會設定權杖處理常式集合的設定`maximumClockSkew`屬性[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。 權杖處理常式集合上設定的值會覆寫在服務上設定的值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<會快取 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊用於工作階段權杖，權杖重新執行偵測的快取。 可以指定在服務層級，或在安全性權杖處理常式集合。 選擇性。|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制權杖處理常式用來驗證憑證的設定。 可以指定在服務層級，或在安全性權杖處理常式集合。 選擇性。|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|註冊的連入宣告的宣告驗證管理員。 選擇性。|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|註冊的連入宣告的宣告授權管理員。 選擇性。|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|指定必要的宣告集的連入安全性權杖。 選擇性。|  
|[\<securityTokenHandlers >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定安全性權杖處理常式的集合。 您可以指定零或多個安全性權杖處理常式集合。 選擇性。|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|啟用權杖重新執行偵測，並指定權杖的到期時間。 可以指定在服務層級，或在安全性權杖處理常式集合。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|提供用於啟用應用程式中的 Windows Identity Foundation (WIF) 選項的設定。|  
  
## <a name="remarks"></a>備註  
 多個身分識別可能會定義組態，每個都有唯一的名稱。 的行為如下所示：  
  
1.  如果沒有`<identityConfiguration>`指定項目。 預設身分識別設定為在執行階段建立並填入預設值。  
  
2.  如果單一`<identityConfiguration>`指定項目。 它是預設身分識別組態。 並不重要它是具名或未命名的。  
  
3.  若為多個`<identityConfiguration>`元素來指定。 未命名的項目會指定預設身分識別組態。 建議當您指定多個`<identityConfiguration>`項目，其中一個應該是未命名。  
  
> [!WARNING]
>  如果您指定多個`<identityConfiguration>`項目，其中一個應該是未命名。 未命名的項目將會預設身分識別組態。  
  
 某些設定中指定`<identityConfiguration>`由安全性權杖處理常式集合上的設定或個別的安全性權杖處理常式上的設定，可以覆寫項目。  
  
> [!IMPORTANT]
>  當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼所參考的身分識別組態中的宣告型存取控制`<federationConfiguration>`項目會設定用來建立原則與 claims authorization manager 授權授權決策。 這是為 true，即使在不是被動 Web 案例，例如 Windows Communication Foundation (WCF) 應用程式或不是以 Web 為基礎的應用程式的案例。 如果應用程式不是被動的 Web 應用程式， [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)元素 （和其子原則項目，如果有的話） 的參考的識別組態所套用的唯一設定。 會忽略所有其他設定。 如需詳細資訊，請參閱[ \<federationConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。  
  
 `<identityConfiguration>`項目由<xref:System.IdentityModel.Configuration.IdentityConfigurationElement>類別。 已識別的組態區段由<xref:System.IdentityModel.Configuration.IdentityConfiguration>類別。  
  
> [!IMPORTANT]
>  指定下列項目為子項目的`<identityConfiguration>`，也已被取代的項目，雖然行為仍支援回溯相容性。 相反地，應該下指定這些項目[ \<securityTokenHandlerConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>範例  
 下列範例會建立名為"alternateConfiguration 「 身分識別組態。 身分識別組態指定預設設定。  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>請參閱  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
