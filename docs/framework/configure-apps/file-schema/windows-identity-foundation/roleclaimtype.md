---
title: '&lt;RoleClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 565bf30d334c62c8132c60f411e89f7b260c54f1
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47206172"
---
# <a name="ltroleclaimtypegt"></a><span data-ttu-id="2cc42-102">&lt;RoleClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="2cc42-102">&lt;roleClaimType&gt;</span></span>
<span data-ttu-id="2cc42-103">指定的集合中定義的角色類型宣告的宣告類型<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>的權杖處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="2cc42-103">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="2cc42-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="2cc42-104">\<system.identityModel></span></span>  
<span data-ttu-id="2cc42-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="2cc42-105">\<identityConfiguration></span></span>  
<span data-ttu-id="2cc42-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="2cc42-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="2cc42-107">\<add></span><span class="sxs-lookup"><span data-stu-id="2cc42-107">\<add></span></span>  
<span data-ttu-id="2cc42-108">\<samlSecurityTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="2cc42-108">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="2cc42-109">\<roleClaimType ></span><span class="sxs-lookup"><span data-stu-id="2cc42-109">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2cc42-110">語法</span><span class="sxs-lookup"><span data-stu-id="2cc42-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2cc42-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2cc42-111">Attributes and Elements</span></span>  
 <span data-ttu-id="2cc42-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2cc42-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2cc42-113">屬性</span><span class="sxs-lookup"><span data-stu-id="2cc42-113">Attributes</span></span>  
  
|<span data-ttu-id="2cc42-114">屬性</span><span class="sxs-lookup"><span data-stu-id="2cc42-114">Attribute</span></span>|<span data-ttu-id="2cc42-115">描述</span><span class="sxs-lookup"><span data-stu-id="2cc42-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="2cc42-116">value</span><span class="sxs-lookup"><span data-stu-id="2cc42-116">value</span></span>|<span data-ttu-id="2cc42-117">字串，指定代表要用於角色宣告類型宣告的宣告類型的 URI。</span><span class="sxs-lookup"><span data-stu-id="2cc42-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="2cc42-118">子元素</span><span class="sxs-lookup"><span data-stu-id="2cc42-118">Child Elements</span></span>  
 <span data-ttu-id="2cc42-119">無</span><span class="sxs-lookup"><span data-stu-id="2cc42-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="2cc42-120">父項目</span><span class="sxs-lookup"><span data-stu-id="2cc42-120">Parent Elements</span></span>  
  
|<span data-ttu-id="2cc42-121">項目</span><span class="sxs-lookup"><span data-stu-id="2cc42-121">Element</span></span>|<span data-ttu-id="2cc42-122">描述</span><span class="sxs-lookup"><span data-stu-id="2cc42-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2cc42-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="2cc42-123">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="2cc42-124">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="2cc42-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="2cc42-125">備註</span><span class="sxs-lookup"><span data-stu-id="2cc42-125">Remarks</span></span>  
 <span data-ttu-id="2cc42-126">`<roleClaimType>`項目集<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>屬性時<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="2cc42-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="2cc42-127">範例</span><span class="sxs-lookup"><span data-stu-id="2cc42-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2cc42-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2cc42-128">See Also</span></span>  
 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
