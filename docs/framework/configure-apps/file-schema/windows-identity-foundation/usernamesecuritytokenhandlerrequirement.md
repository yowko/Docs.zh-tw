---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: fed8964e03b80e365fdc5eafd45b4fc372a6e352
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69944258"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="85632-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="85632-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="85632-102"><xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>提供類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="85632-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="85632-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="85632-103">\<system.identityModel></span></span>  
<span data-ttu-id="85632-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="85632-104">\<identityConfiguration></span></span>  
<span data-ttu-id="85632-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="85632-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="85632-106">\<add></span><span class="sxs-lookup"><span data-stu-id="85632-106">\<add></span></span>  
<span data-ttu-id="85632-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="85632-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85632-108">語法</span><span class="sxs-lookup"><span data-stu-id="85632-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85632-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85632-109">Attributes and Elements</span></span>  
 <span data-ttu-id="85632-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="85632-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85632-111">屬性</span><span class="sxs-lookup"><span data-stu-id="85632-111">Attributes</span></span>  
  
|<span data-ttu-id="85632-112">屬性</span><span class="sxs-lookup"><span data-stu-id="85632-112">Attribute</span></span>|<span data-ttu-id="85632-113">描述</span><span class="sxs-lookup"><span data-stu-id="85632-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85632-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="85632-114">membershipProviderName</span></span>|<span data-ttu-id="85632-115"><xref:System.Web.Security.MembershipProvider>指定安全性權杖處理常式應該使用的。</span><span class="sxs-lookup"><span data-stu-id="85632-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85632-116">子元素</span><span class="sxs-lookup"><span data-stu-id="85632-116">Child Elements</span></span>  
 <span data-ttu-id="85632-117">無</span><span class="sxs-lookup"><span data-stu-id="85632-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85632-118">父項目</span><span class="sxs-lookup"><span data-stu-id="85632-118">Parent Elements</span></span>  
  
|<span data-ttu-id="85632-119">項目</span><span class="sxs-lookup"><span data-stu-id="85632-119">Element</span></span>|<span data-ttu-id="85632-120">描述</span><span class="sxs-lookup"><span data-stu-id="85632-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="85632-121">\<add></span><span class="sxs-lookup"><span data-stu-id="85632-121">\<add></span></span>](add.md)|<span data-ttu-id="85632-122">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="85632-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="85632-123">備註</span><span class="sxs-lookup"><span data-stu-id="85632-123">Remarks</span></span>  
 <span data-ttu-id="85632-124">元素會在<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>物件<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A>從設定初始化時設定屬性。 `<userNameSecurityTokenHandlerRequirement>`</span><span class="sxs-lookup"><span data-stu-id="85632-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="85632-125">範例</span><span class="sxs-lookup"><span data-stu-id="85632-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
