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
# <a name="nameclaimtype"></a><span data-ttu-id="0a353-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="0a353-101">\<nameClaimType></span></span>
<span data-ttu-id="0a353-102">設定指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="0a353-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="0a353-103">宣告類型是用來搜尋此標記處理<xref:System.Security.Claims.Claim>程式的<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所<xref:System.Security.Claims.ClaimsIdentity>傳回的物件集合中的。</span><span class="sxs-lookup"><span data-stu-id="0a353-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="0a353-104">然後, 比對宣告的值會設定為從這個 token 處理<xref:System.Security.Principal.IIdentity>程式產生之的名稱。</span><span class="sxs-lookup"><span data-stu-id="0a353-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
 <span data-ttu-id="0a353-105">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="0a353-105">\<system.identityModel></span></span>  
<span data-ttu-id="0a353-106">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="0a353-106">\<identityConfiguration></span></span>  
<span data-ttu-id="0a353-107">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="0a353-107">\<securityTokenHandlers></span></span>  
<span data-ttu-id="0a353-108">\<add></span><span class="sxs-lookup"><span data-stu-id="0a353-108">\<add></span></span>  
<span data-ttu-id="0a353-109">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="0a353-109">\<samlSecurityTokenRequirement></span></span>  
<span data-ttu-id="0a353-110">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="0a353-110">\<nameClaimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0a353-111">語法</span><span class="sxs-lookup"><span data-stu-id="0a353-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0a353-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0a353-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0a353-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0a353-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0a353-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0a353-114">Attributes</span></span>  
  
|<span data-ttu-id="0a353-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0a353-115">Attribute</span></span>|<span data-ttu-id="0a353-116">描述</span><span class="sxs-lookup"><span data-stu-id="0a353-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0a353-117">value</span><span class="sxs-lookup"><span data-stu-id="0a353-117">value</span></span>|<span data-ttu-id="0a353-118">指定 URI 的字串, 代表要<xref:System.Security.Principal.IIdentity.Name%2A>用於屬性之宣告的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="0a353-118">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="0a353-119">必要項。</span><span class="sxs-lookup"><span data-stu-id="0a353-119">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0a353-120">子元素</span><span class="sxs-lookup"><span data-stu-id="0a353-120">Child Elements</span></span>  
 <span data-ttu-id="0a353-121">無</span><span class="sxs-lookup"><span data-stu-id="0a353-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0a353-122">父項目</span><span class="sxs-lookup"><span data-stu-id="0a353-122">Parent Elements</span></span>  
  
|<span data-ttu-id="0a353-123">項目</span><span class="sxs-lookup"><span data-stu-id="0a353-123">Element</span></span>|<span data-ttu-id="0a353-124">說明</span><span class="sxs-lookup"><span data-stu-id="0a353-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0a353-125">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="0a353-125">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="0a353-126"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="0a353-126">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0a353-127">備註</span><span class="sxs-lookup"><span data-stu-id="0a353-127">Remarks</span></span>  
 <span data-ttu-id="0a353-128">元素會在<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>從設定初始化時設定屬性。 `<nameClaimType>`</span><span class="sxs-lookup"><span data-stu-id="0a353-128">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0a353-129">範例</span><span class="sxs-lookup"><span data-stu-id="0a353-129">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="0a353-130">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0a353-130">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
