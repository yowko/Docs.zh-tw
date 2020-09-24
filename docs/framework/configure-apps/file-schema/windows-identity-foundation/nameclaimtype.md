---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4ffc19366d91e4a14ee0f931d7009ede390cc097
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165022"
---
# \<nameClaimType>

<span data-ttu-id="e5b9a-101">設定指定屬性的宣告類型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e5b9a-102">宣告類型是用來 <xref:System.Security.Claims.Claim> 在 <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 此 token 處理常式的方法所傳回的物件集合中搜尋。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="e5b9a-103">然後，比對宣告的值會設定為從此 <xref:System.Security.Principal.IIdentity> token 處理常式產生的名稱。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="e5b9a-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5b9a-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e5b9a-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e5b9a-105">Attributes and Elements</span></span>  

 <span data-ttu-id="e5b9a-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e5b9a-107">屬性</span><span class="sxs-lookup"><span data-stu-id="e5b9a-107">Attributes</span></span>  
  
|<span data-ttu-id="e5b9a-108">屬性</span><span class="sxs-lookup"><span data-stu-id="e5b9a-108">Attribute</span></span>|<span data-ttu-id="e5b9a-109">描述</span><span class="sxs-lookup"><span data-stu-id="e5b9a-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e5b9a-110">value</span><span class="sxs-lookup"><span data-stu-id="e5b9a-110">value</span></span>|<span data-ttu-id="e5b9a-111">字串，指定代表要用於屬性之宣告的宣告類型的 URI <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="e5b9a-112">必要。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e5b9a-113">子元素</span><span class="sxs-lookup"><span data-stu-id="e5b9a-113">Child Elements</span></span>  

 <span data-ttu-id="e5b9a-114">無</span><span class="sxs-lookup"><span data-stu-id="e5b9a-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="e5b9a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="e5b9a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="e5b9a-116">項目</span><span class="sxs-lookup"><span data-stu-id="e5b9a-116">Element</span></span>|<span data-ttu-id="e5b9a-117">描述</span><span class="sxs-lookup"><span data-stu-id="e5b9a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="e5b9a-118">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、類別或其中一個類別的 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="e5b9a-119">備註</span><span class="sxs-lookup"><span data-stu-id="e5b9a-119">Remarks</span></span>  

 <span data-ttu-id="e5b9a-120">`<nameClaimType>` <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> 當物件從設定初始化時，元素會設定屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="e5b9a-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e5b9a-121">範例</span><span class="sxs-lookup"><span data-stu-id="e5b9a-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="e5b9a-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5b9a-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
