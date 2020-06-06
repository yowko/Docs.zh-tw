---
title: <nameClaimType>
ms.date: 03/30/2017
ms.assetid: 17514d95-f0f5-4789-8e28-346640dc227c
author: BrucePerlerMS
ms.openlocfilehash: 4bf8ad2f70499edfc72dd9fcd9a5d8a0aafbbc66
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70251944"
---
# \<nameClaimType>
<span data-ttu-id="9707b-101">設定指定屬性的宣告類型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9707b-101">Sets the claim type that specifies the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="9707b-102">宣告類型是用來搜尋 <xref:System.Security.Claims.Claim> <xref:System.Security.Claims.ClaimsIdentity> <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> 此標記處理常式的方法所傳回的物件集合中的。</span><span class="sxs-lookup"><span data-stu-id="9707b-102">The claim type is used to search for a <xref:System.Security.Claims.Claim> in the collection of <xref:System.Security.Claims.ClaimsIdentity> objects returned by the <xref:System.IdentityModel.Tokens.SecurityTokenHandler.ValidateToken%2A> method of this token handler.</span></span> <span data-ttu-id="9707b-103">然後，比對宣告的值會設定為 <xref:System.Security.Principal.IIdentity> 從這個 token 處理常式產生之的名稱。</span><span class="sxs-lookup"><span data-stu-id="9707b-103">The value of the matching claim is then set as the name of the <xref:System.Security.Principal.IIdentity> generated from this token handler.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<samlSecurityTokenRequirement>**](samlsecuritytokenrequirement.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<nameClaimType>**  
  
## <a name="syntax"></a><span data-ttu-id="9707b-104">語法</span><span class="sxs-lookup"><span data-stu-id="9707b-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9707b-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9707b-105">Attributes and Elements</span></span>  
 <span data-ttu-id="9707b-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9707b-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9707b-107">屬性</span><span class="sxs-lookup"><span data-stu-id="9707b-107">Attributes</span></span>  
  
|<span data-ttu-id="9707b-108">屬性</span><span class="sxs-lookup"><span data-stu-id="9707b-108">Attribute</span></span>|<span data-ttu-id="9707b-109">描述</span><span class="sxs-lookup"><span data-stu-id="9707b-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="9707b-110">value</span><span class="sxs-lookup"><span data-stu-id="9707b-110">value</span></span>|<span data-ttu-id="9707b-111">指定 URI 的字串，代表要用於屬性之宣告的宣告類型 <xref:System.Security.Principal.IIdentity.Name%2A> 。</span><span class="sxs-lookup"><span data-stu-id="9707b-111">A string that specifies the URI that represents the claim type of the claim to use for the <xref:System.Security.Principal.IIdentity.Name%2A> property.</span></span> <span data-ttu-id="9707b-112">必要。</span><span class="sxs-lookup"><span data-stu-id="9707b-112">Required.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9707b-113">子元素</span><span class="sxs-lookup"><span data-stu-id="9707b-113">Child Elements</span></span>  
 <span data-ttu-id="9707b-114">無</span><span class="sxs-lookup"><span data-stu-id="9707b-114">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9707b-115">父項目</span><span class="sxs-lookup"><span data-stu-id="9707b-115">Parent Elements</span></span>  
  
|<span data-ttu-id="9707b-116">元素</span><span class="sxs-lookup"><span data-stu-id="9707b-116">Element</span></span>|<span data-ttu-id="9707b-117">描述</span><span class="sxs-lookup"><span data-stu-id="9707b-117">Description</span></span>|  
|-------------|-----------------|  
|[\<samlSecurityTokenRequirement>](samlsecuritytokenrequirement.md)|<span data-ttu-id="9707b-118">提供 <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> 類別、 <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> 類別或其中任一個類別的衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="9707b-118">Provides configuration for the <xref:System.IdentityModel.Tokens.SamlSecurityTokenHandler> class, the <xref:System.IdentityModel.Tokens.Saml2SecurityTokenHandler> class, or a derived class of either of these classes.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9707b-119">備註</span><span class="sxs-lookup"><span data-stu-id="9707b-119">Remarks</span></span>  
 <span data-ttu-id="9707b-120">`<nameClaimType>`元素 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> 會在物件從設定初始化時設定屬性 <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> 。</span><span class="sxs-lookup"><span data-stu-id="9707b-120">The `<nameClaimType>` element sets the <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A> property when a <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9707b-121">範例</span><span class="sxs-lookup"><span data-stu-id="9707b-121">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SamlSecurityTokenHandler, System.IdentityModel">  
    <samlSecurityTokenRequirement>  
        <nameClaimType value="http://schemas.xmlsoap.org/ws/2005/05/identity/claims/name" />  
    </samlSecurityTokenRequirement>  
</add>  
```  
  
## <a name="see-also"></a><span data-ttu-id="9707b-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9707b-122">See also</span></span>

- <xref:System.IdentityModel.Tokens.SamlSecurityTokenRequirement.NameClaimType%2A>
