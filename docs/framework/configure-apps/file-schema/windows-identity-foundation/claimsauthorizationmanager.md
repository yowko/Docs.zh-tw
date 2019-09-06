---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252076"
---
# <a name="claimsauthorizationmanager"></a>\<claimsAuthorizationManager>
為傳入宣告註冊宣告授權管理員。  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimsAuthorizationManager >**  
  
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
|型別|衍生<xref:System.Security.Claims.ClaimsAuthorizationManager>自類別的自訂類型。 如需如何指定屬性的`type`詳細資訊，請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  
 <xref:System.Security.Claims.ClaimsAuthenticationManager> `<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager>如果沒有`type`屬性，或屬性參考類別，則專案不會採用子項目; 不過，衍生自的類別可以定義子設定元素。 `type`  
  
### <a name="parent-elements"></a>父項目  
  
|項目|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  
 透過<xref:System.Security.Claims.ClaimsAuthorizationManager>類別提供的預設行為一律會授權傳入宣告。 如果未`type`指定任何屬性，或`type`屬性指定了<xref:System.Security.Claims.ClaimsAuthorizationManager>類別，則`<claimsAuthorizationManager>`專案不會採用子項目。 您可以指定`type`屬性來註冊衍生自類別的<xref:System.Security.Claims.ClaimsAuthorizationManager>型別，以執行自訂行為。 衍生類別可以藉由覆`<claimsAuthorizationManager>` <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A>寫方法來處理這些專案，藉以支援透過專案的子專案進行設定。 為子專案定義的架構是由類別的設計工具所組成。  
  
> [!IMPORTANT]
> 當使用<xref:System.IdentityModel.Services.ClaimsPrincipalPermission> <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute>或類別在您的程式碼中提供宣告型存取控制時， `<federationConfiguration>`元素所參考的身分識別設定會設定宣告授權管理員和原則，以用來進行授權決策。 這也適用于非被動 Web 案例的情況，例如 Windows Communication Foundation （WCF）應用程式或不是以 Web 為基礎的應用程式。 如果應用程式不是被動的 Web 應用程式， `<claimsAuthorizationManager>`則會套用所參考身分識別設定的專案（及其子原則元素（如果有的話））。 所有其他設定都會被忽略。 如需詳細資訊，請參閱[ \<federationConfiguration >](federationconfiguration.md)元素。  
  
 這個元素會設定<xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType>屬性。  
  
## <a name="example"></a>範例  
 下列 XML 顯示宣告授權管理員的設定，其會執行由資源動作配對組成的原則，其中每個都指定要求者必須擁有才能在資源上執行動作的宣告的布林組合。 `ClaimsBasedAuthorization`範例中可以找到可使用此原則來執行宣告授權管理員的程式碼。  
  
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
