---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0ce2e06ee895d09de193bac1fe7038e71794dda4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942546"
---
# <a name="roleclaimtype"></a><span data-ttu-id="1ff3b-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="1ff3b-101">\<roleClaimType></span></span>
<span data-ttu-id="1ff3b-102">指定宣告類型, 在權杖處理常式的<xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所傳回的物件集合中, 定義角色類型宣告。</span><span class="sxs-lookup"><span data-stu-id="1ff3b-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
 <span data-ttu-id="1ff3b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="1ff3b-103">\<system.identityModel></span></span>  
<span data-ttu-id="1ff3b-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="1ff3b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="1ff3b-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="1ff3b-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1ff3b-106">\<add></span><span class="sxs-lookup"><span data-stu-id="1ff3b-106">\<add></span></span>  
<span data-ttu-id="1ff3b-107">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="1ff3b-107">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="1ff3b-108">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="1ff3b-108">\<roleClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1ff3b-109">語法</span><span class="sxs-lookup"><span data-stu-id="1ff3b-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1ff3b-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1ff3b-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1ff3b-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1ff3b-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1ff3b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1ff3b-112">Attributes</span></span>  
  
|<span data-ttu-id="1ff3b-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1ff3b-113">Attribute</span></span>|<span data-ttu-id="1ff3b-114">說明</span><span class="sxs-lookup"><span data-stu-id="1ff3b-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1ff3b-115">value</span><span class="sxs-lookup"><span data-stu-id="1ff3b-115">value</span></span>|<span data-ttu-id="1ff3b-116">指定 URI 的字串, 代表要用於角色宣告類型之宣告的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="1ff3b-116">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1ff3b-117">子元素</span><span class="sxs-lookup"><span data-stu-id="1ff3b-117">Child Elements</span></span>  
 <span data-ttu-id="1ff3b-118">無</span><span class="sxs-lookup"><span data-stu-id="1ff3b-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1ff3b-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1ff3b-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1ff3b-120">項目</span><span class="sxs-lookup"><span data-stu-id="1ff3b-120">Element</span></span>|<span data-ttu-id="1ff3b-121">描述</span><span class="sxs-lookup"><span data-stu-id="1ff3b-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1ff3b-122">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="1ff3b-122">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="1ff3b-123"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="1ff3b-123">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="1ff3b-124">備註</span><span class="sxs-lookup"><span data-stu-id="1ff3b-124">Remarks</span></span>  
 <span data-ttu-id="1ff3b-125">元素會在<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>從設定初始化時設定屬性。 `<roleClaimType>`</span><span class="sxs-lookup"><span data-stu-id="1ff3b-125">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1ff3b-126">範例</span><span class="sxs-lookup"><span data-stu-id="1ff3b-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="1ff3b-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1ff3b-127">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
