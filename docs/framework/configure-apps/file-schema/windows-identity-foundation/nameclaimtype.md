---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251944"
---
# <a name="nameclaimtype"></a><span data-ttu-id="b8199-101">\<nameClaimType></span><span class="sxs-lookup"><span data-stu-id="b8199-101">\<nameClaimType></span></span>
<span data-ttu-id="b8199-102">設定指定<xref:System.Security.Principal.IIdentity.Name%2A>屬性的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="b8199-102">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="b8199-103">宣告類型是用來搜尋此標記處理<xref:System.Security.Claims.Claim>程式的<xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所<xref:System.Security.Claims.ClaimsIdentity>傳回的物件集合中的。</span><span class="sxs-lookup"><span data-stu-id="b8199-103">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="b8199-104">然後，比對宣告的值會設定為從這個 token 處理<xref:System.Security.Principal.IIdentity>程式產生之的名稱。</span><span class="sxs-lookup"><span data-stu-id="b8199-104">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
<span data-ttu-id="b8199-105">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="b8199-105">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="b8199-106">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="b8199-106">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="b8199-107">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="b8199-107">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="b8199-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="b8199-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="b8199-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="b8199-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="b8199-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="b8199-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="b8199-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<nameClaimType >**</span><span class="sxs-lookup"><span data-stu-id="b8199-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8199-112">語法</span><span class="sxs-lookup"><span data-stu-id="b8199-112">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b8199-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b8199-113">Attributes and Elements</span></span>  
 <span data-ttu-id="b8199-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="b8199-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b8199-115">屬性</span><span class="sxs-lookup"><span data-stu-id="b8199-115">Attributes</span></span>  
  
|<span data-ttu-id="b8199-116">屬性</span><span class="sxs-lookup"><span data-stu-id="b8199-116">Attribute</span></span>|<span data-ttu-id="b8199-117">說明</span><span class="sxs-lookup"><span data-stu-id="b8199-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="b8199-118">value</span><span class="sxs-lookup"><span data-stu-id="b8199-118">value</span></span>|<span data-ttu-id="b8199-119">指定 URI 的字串，代表要<xref:System.Security.Principal.IIdentity.Name%2A>用於屬性之宣告的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="b8199-119">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="b8199-120">必要項。</span><span class="sxs-lookup"><span data-stu-id="b8199-120">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b8199-121">子元素</span><span class="sxs-lookup"><span data-stu-id="b8199-121">Child Elements</span></span>  
 <span data-ttu-id="b8199-122">無</span><span class="sxs-lookup"><span data-stu-id="b8199-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b8199-123">父項目</span><span class="sxs-lookup"><span data-stu-id="b8199-123">Parent Elements</span></span>  
  
|<span data-ttu-id="b8199-124">項目</span><span class="sxs-lookup"><span data-stu-id="b8199-124">Element</span></span>|<span data-ttu-id="b8199-125">描述</span><span class="sxs-lookup"><span data-stu-id="b8199-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="b8199-126">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="b8199-126">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="b8199-127"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="b8199-127">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8199-128">備註</span><span class="sxs-lookup"><span data-stu-id="b8199-128">Remarks</span></span>  
 <span data-ttu-id="b8199-129">元素會在<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>從設定初始化時設定屬性。 `<nameClaimType>`</span><span class="sxs-lookup"><span data-stu-id="b8199-129">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b8199-130">範例</span><span class="sxs-lookup"><span data-stu-id="b8199-130">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="b8199-131">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b8199-131">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
