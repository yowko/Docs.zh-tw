---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 5202e162a7eb5fc4e36d6a6c0a2c18af48872a69
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59130321"
---
# <a name="nameclaimtype"></a><span data-ttu-id="d81f1-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="d81f1-101">\<nameClaimType></span></span>
<span data-ttu-id="d81f1-102">設定指定的宣告型<xref:System.Security.Principal.IIdentity.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d81f1-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d81f1-103">宣告類型用來搜尋<xref:System.Security.Claims.Claim>集合中的<xref:System.Security.Claims.ClaimsIdentity>所傳回的物件<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>此語彙基元處理常式的方法。</span><span class="sxs-lookup"><span data-stu-id="d81f1-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="d81f1-104">比對的宣告的值將做為名稱<xref:System.Security.Principal.IIdentity>產生從這個權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="d81f1-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="d81f1-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="d81f1-105">\<system.identityModel></span></span>  
<span data-ttu-id="d81f1-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="d81f1-106">\<identityConfiguration></span></span>  
<span data-ttu-id="d81f1-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="d81f1-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="d81f1-108">\<add></span><span class="sxs-lookup"><span data-stu-id="d81f1-108">\<add></span></span>  
<span data-ttu-id="d81f1-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d81f1-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="d81f1-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="d81f1-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d81f1-111">語法</span><span class="sxs-lookup"><span data-stu-id="d81f1-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d81f1-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d81f1-112">Attributes and Elements</span></span>  
 <span data-ttu-id="d81f1-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d81f1-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d81f1-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d81f1-114">Attributes</span></span>  
  
|<span data-ttu-id="d81f1-115">屬性</span><span class="sxs-lookup"><span data-stu-id="d81f1-115">Attribute</span></span>|<span data-ttu-id="d81f1-116">描述</span><span class="sxs-lookup"><span data-stu-id="d81f1-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d81f1-117">value</span><span class="sxs-lookup"><span data-stu-id="d81f1-117">value</span></span>|<span data-ttu-id="d81f1-118">字串，指定代表要用於宣告的宣告類型 URI<xref:System.Security.Principal.IIdentity.Name%2A>屬性。</span><span class="sxs-lookup"><span data-stu-id="d81f1-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="d81f1-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="d81f1-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d81f1-120">子元素</span><span class="sxs-lookup"><span data-stu-id="d81f1-120">Child Elements</span></span>  
 <span data-ttu-id="d81f1-121">None</span><span class="sxs-lookup"><span data-stu-id="d81f1-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d81f1-122">父項目</span><span class="sxs-lookup"><span data-stu-id="d81f1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="d81f1-123">項目</span><span class="sxs-lookup"><span data-stu-id="d81f1-123">Element</span></span>|<span data-ttu-id="d81f1-124">描述</span><span class="sxs-lookup"><span data-stu-id="d81f1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d81f1-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="d81f1-125">\<samlSecurityTokenRequirement></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/samlsecuritytokenrequirement.md)|<span data-ttu-id="d81f1-126">提供組態<xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>類別，<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler>類別或其中一個這些類別的衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="d81f1-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d81f1-127">備註</span><span class="sxs-lookup"><span data-stu-id="d81f1-127">Remarks</span></span>  
 <span data-ttu-id="d81f1-128">`<nameClaimType>`項目集<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>屬性時<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="d81f1-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d81f1-129">範例</span><span class="sxs-lookup"><span data-stu-id="d81f1-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="d81f1-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d81f1-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
