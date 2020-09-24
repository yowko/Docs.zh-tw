---
title: <roleClaimType>
ms.date: 03/30/2017
ms.assetid: 69a49deb-6369-41ba-806b-ae8d21fac64b
author: BrucePerlerMS
ms.openlocfilehash: 36d727f97597df816779da1c1f7ed5da1a1697f2
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91164931"
---
# \<roleClaimType>

<span data-ttu-id="4bb70-101">指定宣告類型，定義 <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 權杖處理常式方法所傳回的物件集合中的角色類型宣告。</span><span class="sxs-lookup"><span data-stu-id="4bb70-101">Specifies the claim type that defines the role type claims in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of the token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<roleClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="4bb70-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="4bb70-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4bb70-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4bb70-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4bb70-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4bb70-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4bb70-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4bb70-105">Attributes</span></span>  
  
|<span data-ttu-id="4bb70-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4bb70-106">Attribute</span></span>|<span data-ttu-id="4bb70-107">描述</span><span class="sxs-lookup"><span data-stu-id="4bb70-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4bb70-108">value</span><span class="sxs-lookup"><span data-stu-id="4bb70-108">value</span></span>|<span data-ttu-id="4bb70-109">字串，指定代表要用於角色宣告類型之宣告的宣告類型的 URI。</span><span class="sxs-lookup"><span data-stu-id="4bb70-109">A string that specifies the URI that represents the claim type of the claim to use for the role claim type.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4bb70-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4bb70-110">Child Elements</span></span>  

 <span data-ttu-id="4bb70-111">無</span><span class="sxs-lookup"><span data-stu-id="4bb70-111">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4bb70-112">父項目</span><span class="sxs-lookup"><span data-stu-id="4bb70-112">Parent Elements</span></span>  
  
|<span data-ttu-id="4bb70-113">項目</span><span class="sxs-lookup"><span data-stu-id="4bb70-113">Element</span></span>|<span data-ttu-id="4bb70-114">描述</span><span class="sxs-lookup"><span data-stu-id="4bb70-114">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="4bb70-115">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、類別或其中一個類別的 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="4bb70-115">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="4bb70-116">備註</span><span class="sxs-lookup"><span data-stu-id="4bb70-116">Remarks</span></span>  

 <span data-ttu-id="4bb70-117">`<roleClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> 當物件從設定初始化時，元素會設定屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="4bb70-117">The `<roleClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bb70-118">範例</span><span class="sxs-lookup"><span data-stu-id="4bb70-118">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <roleClaimType value="schemas.microsoft.com/ws/2006/04/identity/claims/role" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="4bb70-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4bb70-119">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.RoleClaimType%2A>
