---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 5863c01e97e7f5fb6fe07c43174c0d6cb7a0a25d
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70251740"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="c9ab4-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="c9ab4-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="c9ab4-102"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>提供類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="c9ab4-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
<span data-ttu-id="c9ab4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c9ab4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c9ab4-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="c9ab4-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="c9ab4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="c9ab4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="c9ab4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<securityTokenHandlers >** ](securitytokenhandlers.md)</span><span class="sxs-lookup"><span data-stu-id="c9ab4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<securityTokenHandlers>**](securitytokenhandlers.md)</span></span>\
<span data-ttu-id="c9ab4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<新增 >** ](add.md)</span><span class="sxs-lookup"><span data-stu-id="c9ab4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<add>**](add.md)</span></span>\
<span data-ttu-id="c9ab4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<userNameSecurityTokenHandlerRequirement >**</span><span class="sxs-lookup"><span data-stu-id="c9ab4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<userNameSecurityTokenHandlerRequirement>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c9ab4-109">語法</span><span class="sxs-lookup"><span data-stu-id="c9ab4-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
        <userNameSecurityTokenHandlerRequirement membershipProviderName=xs:string >  
        </userNameSecurityTokenHandlerRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c9ab4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c9ab4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c9ab4-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c9ab4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c9ab4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c9ab4-112">Attributes</span></span>  
  
|<span data-ttu-id="c9ab4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c9ab4-113">Attribute</span></span>|<span data-ttu-id="c9ab4-114">說明</span><span class="sxs-lookup"><span data-stu-id="c9ab4-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c9ab4-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="c9ab4-115">membershipProviderName</span></span>|<span data-ttu-id="c9ab4-116"><xref:System.Web.Security.MembershipProvider>指定安全性權杖處理常式應該使用的。</span><span class="sxs-lookup"><span data-stu-id="c9ab4-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c9ab4-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c9ab4-117">Child Elements</span></span>  
 <span data-ttu-id="c9ab4-118">None</span><span class="sxs-lookup"><span data-stu-id="c9ab4-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c9ab4-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c9ab4-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c9ab4-120">項目</span><span class="sxs-lookup"><span data-stu-id="c9ab4-120">Element</span></span>|<span data-ttu-id="c9ab4-121">描述</span><span class="sxs-lookup"><span data-stu-id="c9ab4-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c9ab4-122">\<add></span><span class="sxs-lookup"><span data-stu-id="c9ab4-122">\<add></span></span>](add.md)|<span data-ttu-id="c9ab4-123">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="c9ab4-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c9ab4-124">備註</span><span class="sxs-lookup"><span data-stu-id="c9ab4-124">Remarks</span></span>  
 <span data-ttu-id="c9ab4-125">元素會在<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>物件<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A>從設定初始化時設定屬性。 `<userNameSecurityTokenHandlerRequirement>`</span><span class="sxs-lookup"><span data-stu-id="c9ab4-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9ab4-126">範例</span><span class="sxs-lookup"><span data-stu-id="c9ab4-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
