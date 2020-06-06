---
title: <claimsAuthorizationManager>
ms.date: 03/30/2017
ms.assetid: 9354eee3-f692-4ad6-8427-3169686b8bcc
author: BrucePerlerMS
ms.openlocfilehash: ddbe8a862940272e4192a3f4c0abdc1f9e8b5d48
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252076"
---
# \<claimsAuthorizationManager>
為傳入宣告註冊宣告授權管理員。  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimsAuthorizationManager>**  
  
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
 下列章節說明屬性、子元素和父元素。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|type|衍生自類別的自訂類型 <xref:System.Security.Claims.ClaimsAuthorizationManager> 。 如需如何指定屬性的詳細資訊 `type` ，請參閱[自訂類型參考](../windows-workflow-foundation/index.md)。|  
  
### <a name="child-elements"></a>子元素  
 如果沒有 `type` 屬性，或 `type` 屬性參考 <xref:System.Security.Claims.ClaimsAuthenticationManager> 類別，則專案不會 `<claimsAuthorizationManager>` 採用子項目; 不過，衍生自的類別 <xref:System.Security.Claims.ClaimsAuthorizationManager> 可以定義子設定元素。  
  
### <a name="parent-elements"></a>父項目  
  
|元素|描述|  
|-------------|-----------------|  
|[\<identityConfiguration>](identityconfiguration.md)|指定服務層級的身分識別設定。|  
  
## <a name="remarks"></a>備註  
 透過類別提供的預設行為 <xref:System.Security.Claims.ClaimsAuthorizationManager> 一律會授權傳入宣告。 如果未 `type` 指定任何屬性 `type` ，或屬性指定了 <xref:System.Security.Claims.ClaimsAuthorizationManager> 類別，則專案不會 `<claimsAuthorizationManager>` 採用子項目。 您可以指定 `type` 屬性來註冊衍生自類別的型別 <xref:System.Security.Claims.ClaimsAuthorizationManager> ，以執行自訂行為。 衍生類別可以藉 `<claimsAuthorizationManager>` 由覆寫 <xref:System.Security.Claims.ClaimsAuthorizationManager.LoadCustomConfiguration%2A> 方法來處理這些專案，藉以支援透過專案的子專案進行設定。 為子專案定義的架構是由類別的設計工具所組成。  
  
> [!IMPORTANT]
> 當使用 <xref:System.IdentityModel.Services.ClaimsPrincipalPermission> 或 <xref:System.IdentityModel.Services.ClaimsPrincipalPermissionAttribute> 類別在您的程式碼中提供宣告型存取控制時，元素所參考的身分識別設定會設定 `<federationConfiguration>` 宣告授權管理員和原則，以用來進行授權決策。 這也適用于非被動 Web 案例的情況，例如 Windows Communication Foundation （WCF）應用程式或不是以 Web 為基礎的應用程式。 如果應用程式不是被動的 Web 應用程式，則會套用所 `<claimsAuthorizationManager>` 參考身分識別設定的專案（及其子原則元素（如果有的話））。 其他所有設定都會被略過。 如需詳細資訊，請參閱 [\<federationConfiguration>](federationconfiguration.md) 元素。  
  
 這個元素會設定 <xref:System.IdentityModel.Configuration.IdentityConfiguration.ClaimsAuthorizationManager%2A?displayProperty=nameWithType> 屬性。  
  
## <a name="example"></a>範例  
 下列 XML 顯示宣告授權管理員的設定，其會執行由資源動作配對組成的原則，其中每個都指定要求者必須擁有才能在資源上執行動作的宣告的布林組合。 範例中可以找到可使用此原則來執行宣告授權管理員的程式碼 `ClaimsBasedAuthorization` 。  
  
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
