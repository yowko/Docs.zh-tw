---
title: '&lt;claimsAuthorizationManager&gt;'
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: a745339cffdada56a9b7f27f3f879b9d437c2da2
ms.sourcegitcommit: c93fd5139f9efcf6db514e3474301738a6d1d649
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/27/2018
ms.locfileid: "50195550"
---
# <a name="ltclaimsauthorizationmanagergt"></a>&lt;claimsAuthorizationManager&gt;
註冊的連入宣告的宣告授權管理員。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<claimsAuthorizationManager >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimsAuthorizationManager type = xs:string>  
      <optionalConfigurationElements />  
    </claimsAuthorizationManager>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|類型|自訂型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別。 如需有關如何指定`type`屬性，請參閱[自訂型別參考](../../../../../docs/framework/configure-apps/file-schema/windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  
 如果沒有任何`type`屬性，或如果`type`屬性參考<xref:System.Security.Claims.ClaimsAuthenticationManager>類別`<claimsAuthorizationManager>`項目不會子項目; 不過，類別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>可以定義子組態項目。  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|指定服務層級身分識別設定。|  
  
## <a name="remarks"></a>備註  
 透過所提供的預設行為<xref:System.Security.Claims.ClaimsAuthorizationManager>類別一律會授與的連入宣告。 如果沒有`type`指定屬性或如果`type`屬性會指定<xref:System.Security.Claims.ClaimsAuthorizationManager>類別，`<claimsAuthorizationManager>`項目未採用子元素。 您可以指定`type`屬性來註冊型別衍生自<xref:System.Security.Claims.ClaimsAuthorizationManager>類別來實作自訂行為。 在衍生的類別可支援透過子項目的設定`<claimsAuthorizationManager>`藉由覆寫的項目<xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>方法來處理這些項目。 子項目定義的結構描述是由設計工具的類別。  
  
> [!IMPORTANT]
>  使用時<xref:System.IdentityModel.Services.ClaimsPrincipalPermission>或<xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>類別，以提供您的程式碼所參考的識別組態中的宣告型存取控制`<federationConfiguration>`項目會設定宣告授權管理員和用來進行的原則授權決策。 這是為 true，即使在不是被動的 Web 案例，例如 「 Windows Communication Foundation (WCF) 應用程式 」 或 「 不是以 Web 為基礎的應用程式的案例。 如果應用程式不是被動的 Web 應用程式，`<claimsAuthorizationManager>`元素 （和其子原則項目，如果有的話） 參考的身分識別組態所套用的唯一設定。 會忽略所有其他設定。 如需詳細資訊，請參閱 < [ \<Federationconfiguration> >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/federationconfiguration.md)項目。  
  
 這個項目設定<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>屬性。  
  
## <a name="example"></a>範例  
 下列 XML 顯示宣告授權的組態管理員，它會實作的原則資源 / 動作配對所組成的每一個都會指定要求者必須擁有在資源上執行動作的宣告布林值的組合。 實作宣告授權管理員能夠使用此原則的程式碼可在`ClaimsBasedAuthorization`範例。  
  
```xml  
<system.identityModel>  
    <identityConfiguration>  
      <claimsAuthorizationManager type="ClaimsAuthorizationLibrary.MyClaimsAuthorizationManager, ClaimsAuthorizationLibrary">  
        <policy resource="http://localhost:28491/Developers.aspx" action="GET">  
          <or>  
            <claim claimType="http://schemas.microsoft.com/ws/2008/06/identity/claims/role" claimValue="developer" />  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
          </or>  
        </policy>  
        <policy resource="http://localhost:28491/Administrators.aspx" action="GET">  
          <and>  
            <claim claimType="http://schemas.xmlsoap.org/claims/Group" claimValue="Administrator" />  
            <claim claimType="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/country" claimValue="USA" />  
          </and>  
        </policy>  
        <policy resource="http://localhost:28491/Default.aspx" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/" action="GET">  
        </policy>  
        <policy resource="http://localhost:28491/Claims.aspx" action="GET">  
        </policy>  
      </claimsAuthorizationManager>  
    <identityConfiguration>  
<system.identityModel>  
```
