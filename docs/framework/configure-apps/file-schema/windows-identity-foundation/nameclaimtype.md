---
title: '&lt;nameClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 502fc5dd14d7bc3d979153607e1eeeb9354031bb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54737425"
---
# <a name="ltnameclaimtypegt"></a><span data-ttu-id="e4fb4-102">&lt;nameClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="e4fb4-102">&lt;nameClaimType&gt;</span></span>
<span data-ttu-id="e4fb4-103">設定指定的宣告型<xref:System.Security.Principal.IIdentity.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-103">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e4fb4-104">宣告類型用來搜尋<xref:System.Security.Claims.Claim>集合中的<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>此語彙基元處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-104">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="e4fb4-105">比對的宣告的值將做為名稱<xref:System.Security.Principal.IIdentity>產生從這個權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-105">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="e4fb4-106">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="e4fb4-106">\<system.identityModel></span></span>  
<span data-ttu-id="e4fb4-107">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="e4fb4-107">\<identityConfiguration></span></span>  
<span data-ttu-id="e4fb4-108">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="e4fb4-108">\<securityTokenHandlers></span></span>  
<span data-ttu-id="e4fb4-109">\<add></span><span class="sxs-lookup"><span data-stu-id="e4fb4-109">\<add></span></span>  
<span data-ttu-id="e4fb4-110">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e4fb4-110">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="e4fb4-111">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="e4fb4-111">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e4fb4-112">語法</span><span class="sxs-lookup"><span data-stu-id="e4fb4-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4fb4-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4fb4-113">Attributes and Elements</span></span>  
 <span data-ttu-id="e4fb4-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4fb4-115">屬性</span><span class="sxs-lookup"><span data-stu-id="e4fb4-115">Attributes</span></span>  
  
|<span data-ttu-id="e4fb4-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e4fb4-116">Attribute</span></span>|<span data-ttu-id="e4fb4-117">描述</span><span class="sxs-lookup"><span data-stu-id="e4fb4-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4fb4-118">value</span><span class="sxs-lookup"><span data-stu-id="e4fb4-118">value</span></span>|<span data-ttu-id="e4fb4-119">字串，指定代表要用於宣告的宣告類型 URI<xref:System.Security.Principal.IIdentity.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e4fb4-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4fb4-121">子元素</span><span class="sxs-lookup"><span data-stu-id="e4fb4-121">Child Elements</span></span>  
 <span data-ttu-id="e4fb4-122">無</span><span class="sxs-lookup"><span data-stu-id="e4fb4-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e4fb4-123">父項目</span><span class="sxs-lookup"><span data-stu-id="e4fb4-123">Parent Elements</span></span>  
  
|<span data-ttu-id="e4fb4-124">項目</span><span class="sxs-lookup"><span data-stu-id="e4fb4-124">Element</span></span>|<span data-ttu-id="e4fb4-125">描述</span><span class="sxs-lookup"><span data-stu-id="e4fb4-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e4fb4-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="e4fb4-126">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="e4fb4-127">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e4fb4-128">備註</span><span class="sxs-lookup"><span data-stu-id="e4fb4-128">Remarks</span></span>  
 <span data-ttu-id="e4fb4-129">`<nameClaimType>`項目集<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>屬性時<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="e4fb4-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e4fb4-130">範例</span><span class="sxs-lookup"><span data-stu-id="e4fb4-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e4fb4-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e4fb4-131">See also</span></span>
- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
