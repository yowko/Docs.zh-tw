---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 812d44ef947d27b0f73d9dc2172494e89ee56d72
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55270863"
---
# <a name="roleclaimtype"></a><span data-ttu-id="82bf0-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="82bf0-101">\<roleClaimType></span></span>
<span data-ttu-id="82bf0-102">指定的集合中定義的角色類型宣告的宣告類型<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>的權杖處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="82bf0-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="82bf0-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="82bf0-103">\<system.identityModel></span></span>  
<span data-ttu-id="82bf0-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="82bf0-104">\<identityConfiguration></span></span>  
<span data-ttu-id="82bf0-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="82bf0-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="82bf0-106">\<add></span><span class="sxs-lookup"><span data-stu-id="82bf0-106">\<add></span></span>  
<span data-ttu-id="82bf0-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="82bf0-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="82bf0-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="82bf0-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82bf0-109">語法</span><span class="sxs-lookup"><span data-stu-id="82bf0-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82bf0-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="82bf0-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82bf0-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="82bf0-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82bf0-112">屬性</span><span class="sxs-lookup"><span data-stu-id="82bf0-112">Attributes</span></span>  
  
|<span data-ttu-id="82bf0-113">屬性</span><span class="sxs-lookup"><span data-stu-id="82bf0-113">Attribute</span></span>|<span data-ttu-id="82bf0-114">描述</span><span class="sxs-lookup"><span data-stu-id="82bf0-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82bf0-115">value</span><span class="sxs-lookup"><span data-stu-id="82bf0-115">value</span></span>|<span data-ttu-id="82bf0-116">字串，指定代表要用於角色宣告類型宣告的宣告類型的 URI。</span><span class="sxs-lookup"><span data-stu-id="82bf0-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82bf0-117">子元素</span><span class="sxs-lookup"><span data-stu-id="82bf0-117">Child Elements</span></span>  
 <span data-ttu-id="82bf0-118">無</span><span class="sxs-lookup"><span data-stu-id="82bf0-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="82bf0-119">父項目</span><span class="sxs-lookup"><span data-stu-id="82bf0-119">Parent Elements</span></span>  
  
|<span data-ttu-id="82bf0-120">項目</span><span class="sxs-lookup"><span data-stu-id="82bf0-120">Element</span></span>|<span data-ttu-id="82bf0-121">描述</span><span class="sxs-lookup"><span data-stu-id="82bf0-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82bf0-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="82bf0-122">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="82bf0-123">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="82bf0-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="82bf0-124">備註</span><span class="sxs-lookup"><span data-stu-id="82bf0-124">Remarks</span></span>  
 <span data-ttu-id="82bf0-125">`<roleClaimType>`項目集<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>屬性時<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="82bf0-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="82bf0-126">範例</span><span class="sxs-lookup"><span data-stu-id="82bf0-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="82bf0-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82bf0-127">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
