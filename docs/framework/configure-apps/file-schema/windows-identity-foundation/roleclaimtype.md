---
title: '&lt;roleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 909df1bd6054d9737f91c30c3c6b2d68b932281c
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="9c1b2-102">&lt;roleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="9c1b2-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="9c1b2-103">指定的集合中定義的角色類型宣告的宣告類型<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>語彙基元處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="9c1b2-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="9c1b2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="9c1b2-104">\<system.identityModel></span></span>  
<span data-ttu-id="9c1b2-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="9c1b2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="9c1b2-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="9c1b2-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="9c1b2-107">\<add></span><span class="sxs-lookup"><span data-stu-id="9c1b2-107">\<add></span></span>  
<span data-ttu-id="9c1b2-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="9c1b2-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="9c1b2-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="9c1b2-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9c1b2-110">語法</span><span class="sxs-lookup"><span data-stu-id="9c1b2-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9c1b2-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9c1b2-111">Attributes and Elements</span></span>  
 <span data-ttu-id="9c1b2-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9c1b2-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9c1b2-113">屬性</span><span class="sxs-lookup"><span data-stu-id="9c1b2-113">Attributes</span></span>  
  
|<span data-ttu-id="9c1b2-114">屬性</span><span class="sxs-lookup"><span data-stu-id="9c1b2-114">Attribute</span></span>|<span data-ttu-id="9c1b2-115">描述</span><span class="sxs-lookup"><span data-stu-id="9c1b2-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9c1b2-116">value</span><span class="sxs-lookup"><span data-stu-id="9c1b2-116">value</span></span>|<span data-ttu-id="9c1b2-117">字串，指定代表要用於角色宣告類型宣告的宣告類型的 URI。</span><span class="sxs-lookup"><span data-stu-id="9c1b2-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9c1b2-118">子項目</span><span class="sxs-lookup"><span data-stu-id="9c1b2-118">Child Elements</span></span>  
 <span data-ttu-id="9c1b2-119">無</span><span class="sxs-lookup"><span data-stu-id="9c1b2-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9c1b2-120">父項目</span><span class="sxs-lookup"><span data-stu-id="9c1b2-120">Parent Elements</span></span>  
  
|<span data-ttu-id="9c1b2-121">項目</span><span class="sxs-lookup"><span data-stu-id="9c1b2-121">Element</span></span>|<span data-ttu-id="9c1b2-122">描述</span><span class="sxs-lookup"><span data-stu-id="9c1b2-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9c1b2-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="9c1b2-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="9c1b2-124">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或衍生的類別中的這些類別的其中一個。</span><span class="sxs-lookup"><span data-stu-id="9c1b2-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9c1b2-125">備註</span><span class="sxs-lookup"><span data-stu-id="9c1b2-125">Remarks</span></span>  
 <span data-ttu-id="9c1b2-126">`<roleClaimType>`項目集合<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>屬性時<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>從設定初始化物件。</span><span class="sxs-lookup"><span data-stu-id="9c1b2-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9c1b2-127">範例</span><span class="sxs-lookup"><span data-stu-id="9c1b2-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9c1b2-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9c1b2-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
