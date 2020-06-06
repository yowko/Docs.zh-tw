---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 0f651377346b1f14a4226128cd5cf7059543adca
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251917"
---
# \<roleClaimType>
<span data-ttu-id="276d3-101">指定宣告類型，在 <xref:System.Security.Claims.ClaimsIdentity> 權杖處理常式的方法所傳回的物件集合中，定義角色類型宣告 <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 。</span><span class="sxs-lookup"><span data-stu-id="276d3-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="276d3-102">語法</span><span class="sxs-lookup"><span data-stu-id="276d3-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="276d3-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="276d3-103">Attributes and Elements</span></span>  
 <span data-ttu-id="276d3-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="276d3-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="276d3-105">屬性</span><span class="sxs-lookup"><span data-stu-id="276d3-105">Attributes</span></span>  
  
|<span data-ttu-id="276d3-106">屬性</span><span class="sxs-lookup"><span data-stu-id="276d3-106">Attribute</span></span>|<span data-ttu-id="276d3-107">描述</span><span class="sxs-lookup"><span data-stu-id="276d3-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="276d3-108">value</span><span class="sxs-lookup"><span data-stu-id="276d3-108">value</span></span>|<span data-ttu-id="276d3-109">指定 URI 的字串，代表要用於角色宣告類型之宣告的宣告類型。</span><span class="sxs-lookup"><span data-stu-id="276d3-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="276d3-110">子元素</span><span class="sxs-lookup"><span data-stu-id="276d3-110">Child Elements</span></span>  
 <span data-ttu-id="276d3-111">無</span><span class="sxs-lookup"><span data-stu-id="276d3-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="276d3-112">父項目</span><span class="sxs-lookup"><span data-stu-id="276d3-112">Parent Elements</span></span>  
  
|<span data-ttu-id="276d3-113">元素</span><span class="sxs-lookup"><span data-stu-id="276d3-113">Element</span></span>|<span data-ttu-id="276d3-114">描述</span><span class="sxs-lookup"><span data-stu-id="276d3-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="276d3-115">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="276d3-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="276d3-116">備註</span><span class="sxs-lookup"><span data-stu-id="276d3-116">Remarks</span></span>  
 <span data-ttu-id="276d3-117">`<roleClaimType>`元素 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> 會在物件從設定初始化時設定屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="276d3-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="276d3-118">範例</span><span class="sxs-lookup"><span data-stu-id="276d3-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="276d3-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="276d3-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
