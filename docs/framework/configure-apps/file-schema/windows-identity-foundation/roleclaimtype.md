---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251917"
---
# <a name="roleclaimtype"></a><span data-ttu-id="262b4-101">\<roleClaimType></span><span class="sxs-lookup"><span data-stu-id="262b4-101">\<roleClaimType></span></span>
<span data-ttu-id="262b4-102">指定宣告類型, 在權杖處理常式的<xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A>方法所傳回的物件集合中, 定義角色類型宣告。</span><span class="sxs-lookup"><span data-stu-id="262b4-102">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
<span data-ttu-id="262b4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="262b4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="262b4-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="262b4-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="262b4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="262b4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="262b4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="262b4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="262b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="262b4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="262b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<samlSecurityTokenRequirement >** ](samlsecuritytokenrequirement.md)</span><span class="sxs-lookup"><span data-stu-id="262b4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)</span></span>\
<span data-ttu-id="262b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<roleClaimType >**</span><span class="sxs-lookup"><span data-stu-id="262b4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="262b4-110">語法</span><span class="sxs-lookup"><span data-stu-id="262b4-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="262b4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="262b4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="262b4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="262b4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="262b4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="262b4-113">Attributes</span></span>  
  
|<span data-ttu-id="262b4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="262b4-114">Attribute</span></span>|<span data-ttu-id="262b4-115">描述</span><span class="sxs-lookup"><span data-stu-id="262b4-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="262b4-116">value</span><span class="sxs-lookup"><span data-stu-id="262b4-116">value</span></span>|<span data-ttu-id="262b4-117">指定 URI 的字串, 代表要用於角色宣告類型之宣告的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="262b4-117">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="262b4-118">子元素</span><span class="sxs-lookup"><span data-stu-id="262b4-118">Child Elements</span></span>  
 <span data-ttu-id="262b4-119">None</span><span class="sxs-lookup"><span data-stu-id="262b4-119">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="262b4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="262b4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="262b4-121">項目</span><span class="sxs-lookup"><span data-stu-id="262b4-121">Element</span></span>|<span data-ttu-id="262b4-122">說明</span><span class="sxs-lookup"><span data-stu-id="262b4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="262b4-123">\<samlSecurityTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="262b4-123">\<samlSecurityTokenRequirement></span></span>](samlsecuritytokenrequirement.md)|<span data-ttu-id="262b4-124"><xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler>提供類別<xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 、類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="262b4-124">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="262b4-125">備註</span><span class="sxs-lookup"><span data-stu-id="262b4-125">Remarks</span></span>  
 <span data-ttu-id="262b4-126">元素會在<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement>物件<xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>從設定初始化時設定屬性。 `<roleClaimType>`</span><span class="sxs-lookup"><span data-stu-id="262b4-126">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="262b4-127">範例</span><span class="sxs-lookup"><span data-stu-id="262b4-127">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="262b4-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="262b4-128">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
