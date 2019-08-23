---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 47366c5bb2bd9228268fce3ae6e1fb5ad457dab1
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942612"
---
# <a name="nameclaimtype"></a>\<nameClaimType>
設定指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的宣告類型。 宣告類型是用來搜尋此標記處理<xref:System.Security.Claims.Claim>程式的<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所<xref:System.Security.Claims.ClaimsIdentity>傳回的物件集合中的。 然後, 比對宣告的值會設定為從這個 token 處理<xref:System.Security.Principal.IIdentity>程式產生之的名稱。  
  
 \<system.identityModel>  
\<identityConfiguration>  
\<securityTokenHandlers>  
\<add>  
\<samlSecurityTokenRequirement>  
\<nameClaimType>  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <nameClaimType value=xs:string>  
          </nameClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列各節描述屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|value|指定 URI 的字串, 代表要<xref:System.Security.Principal.IIdentity.Name%2A>用於屬性之宣告的宣告類型。 必要項。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。|  
  
## <a name="remarks"></a>備註  
 元素會在<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>從設定初始化時設定屬性。 `<nameClaimType>`  
  
## <a name="example"></a>範例  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
