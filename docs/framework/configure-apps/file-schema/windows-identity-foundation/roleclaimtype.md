---
title: '&lt;roleClaimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: 8a5de30d60478b6601781ac34fd481a6167462e0
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltroleclaimtypegt"></a>&lt;roleClaimType&gt;
指定的集合中定義的角色類型宣告的宣告類型<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>語彙基元處理常式的方法。  
  
 \<system.identityModel >  
\<identityConfiguration >  
\<securityTokenHandlers >  
\<add>  
\<samlSecurityTokenRequirement >  
\<roleClaimType >  
  
## <a name="syntax"></a>語法  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add>  
        <samlSecurityTokenRequirement>  
          <roleClaimType value=xs:string>  
          </roleClaimType>  
        </samlSecurityTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a>屬性和項目  
 下列章節說明屬性、子項目和父項目。  
  
### <a name="attributes"></a>屬性  
  
|屬性|描述|  
|---------------|-----------------|  
|值|字串，指定代表要用於角色宣告類型宣告的宣告類型的 URI。|  
  
### <a name="child-elements"></a>子元素  
 無  
  
### <a name="parent-elements"></a>父項目  
  
|項目|說明|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement >](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或衍生的類別中的這些類別的其中一個。|  
  
## <a name="remarks"></a>備註  
 `<roleClaimType>`項目集合<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>屬性時<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>從設定初始化物件。  
  
## <a name="example"></a>範例  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a>另請參閱  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
