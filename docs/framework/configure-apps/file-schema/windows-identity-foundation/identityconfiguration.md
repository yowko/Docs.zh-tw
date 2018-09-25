---
title: '&lt;identityConfiguration&gt;'
ms.date: 03/30/2017
ms.assetid: 1db76253-07da-447b-9e7a-3705c7228cf4
author: BrucePerlerMS
ms.openlocfilehash: 11ba7df79ead1693fc6828aeabde413237680737
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075650"
---
# <a name="ltidentityconfigurationgt"></a>&lt;identityConfiguration&gt;
指定服務層級身分識別設定。  
  
 \<system.identityModel>  
\<identityConfiguration>  
  
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
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|名稱|身分識別組態區段的名稱。 您可以使用此名稱來參考特定的組態區段。 如果沒有`name`屬性指定，則 [] 區段中定義的預設組態。 被動同盟案例的一律使用預設組態。 如需詳細資訊，請參閱 < [ \<Federationconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。|  
|saveBootstrapContext|指定是否應包含啟動程序權杖中的工作階段權杖。 值可能也會在集合上設定權杖處理常式設定`saveBootstrapContext`屬性[ \<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。 權杖處理常式集合上所設定的值會覆寫在服務上設定的值。|  
|maximumClockSkew|A <xref:System.TimeSpan> ，指定最大允許的時鐘誤差。 執行時間緊迫的作業，例如驗證登入工作階段的到期時間時，控制最大允許的時鐘誤差。 預設值為 5 分鐘，"00: 05:00"。 如需有關如何指定<xref:System.TimeSpan>值，請參閱[Timespan 值](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。 最大時鐘誤差可能也會設定權杖處理常式集合上設定`maximumClockSkew`屬性[ \<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。 權杖處理常式集合上所設定的值會覆寫在服務上設定的值。|  
  
### <a name="child-elements"></a>子元素  
  
|項目|描述|  
|-------------|-----------------|  
|[\<快取 >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/caches.md)|註冊用於工作階段權杖和權杖重新執行偵測快取。 可以在服務層級或上指定的安全性權杖處理常式集合。 選擇性。|  
|[\<certificateValidation >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/certificatevalidation.md)|控制權杖處理常式用來驗證憑證的設定。 可以在服務層級或上指定的安全性權杖處理常式集合。 選擇性。|  
|[\<claimsAuthenticationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthenticationmanager.md)|註冊的連入宣告的宣告驗證管理員。 選擇性。|  
|[\<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)|註冊的連入宣告的宣告授權管理員。 選擇性。|  
|[\<claimTypeRequired >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|指定必要的連入安全性權杖的宣告集。 選擇性。|  
|[\<securityTokenHandlers>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlers.md)|指定安全性權杖處理常式的集合。 您可以指定零個或多個安全性權杖處理常式集合。 選擇性。|  
|[\<tokenReplayDetection >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/tokenreplaydetection.md)|啟用權杖重新執行偵測，並指定權杖的到期時間。 可以在服務層級或上指定的安全性權杖處理常式集合。 選擇性。|  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<system.identityModel >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/system-identitymodel.md)|提供啟用應用程式中的 Windows Identity Foundation (WIF) 選項的設定。|  
  
## <a name="remarks"></a>備註  
 多個身分識別可能會定義組態，每個都有唯一的名稱。 的行為如下所示：  
  
1.  如果沒有`<identityConfiguration>`指定項目。 預設的身分識別組態是在執行階段建立並填入預設值。  
  
2.  如果單一`<identityConfiguration>`指定項目。 它是預設的身分識別組態。 它並不重要是還是名為未命名的。  
  
3.  如果有多個`<identityConfiguration>`指定項目。 未命名的項目會指定預設的身分識別組態。 它時，建議您指定多個`<identityConfiguration>`元素，其中一個應該是未命名。  
  
> [!WARNING]
>  如果您指定多個`<identityConfiguration>`元素，其中一個應該是未命名。 未命名的項目將會預設身分識別組態。  
  
 某些設定中指定`<identityConfiguration>`上的安全性權杖處理常式集合的設定，或在個別的安全性權杖處理常式上的設定，可以覆寫項目。  
  
> [!IMPORTANT]
>  使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼所參考的識別組態中的宣告型存取控制`<federationConfiguration>`項目會設定宣告授權管理員和用來進行的原則授權決策。 這是為 true，即使在不是被動的 Web 案例，例如 「 Windows Communication Foundation (WCF) 應用程式 」 或 「 不是以 Web 為基礎的應用程式的案例。 如果應用程式不是被動的 Web 應用程式中， [ \<claimsAuthorizationManager >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimsauthorizationmanager.md)元素 （和其子原則項目，如果有的話） 參考的身分識別組態所套用的唯一設定。 會忽略所有其他設定。 如需詳細資訊，請參閱 < [ \<Federationconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。  
  
 `<identityConfiguration>`項目由<xref:System.IdentityModel.Configuration.IdentityConfigurationElement>類別。 身分識別組態區段表示<xref:System.IdentityModel.Configuration.IdentityConfiguration>類別。  
  
> [!IMPORTANT]
>  指定下列項目作為子項目的`<identityConfiguration>`，也已被取代的項目，雖然行為仍然會支援回溯相容性。 這些項目，相反地，必須指定底下[ \<Securitytokenhandlerconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/securitytokenhandlerconfiguration.md)項目。  
>   
>  -   [\<audienceUris >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/audienceuris.md)  
> -   [\<issuerNameRegistry >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuernameregistry.md)  
> -   [\<issuerTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/issuertokenresolver.md)  
> -   [\<serviceTokenResolver >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/servicetokenresolver.md)  
  
## <a name="example"></a>範例  
 下列範例會建立名為"alternateConfiguration"的身分識別組態。 身分識別組態會指定預設設定。  
  
```xml  
<system.identityModel>  
    <identityConfiguration name="alternateConfiguration"/>  
</system.identityModel>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Configuration.IdentityConfiguration>  
 <xref:System.IdentityModel.Configuration.IdentityConfigurationElement>
