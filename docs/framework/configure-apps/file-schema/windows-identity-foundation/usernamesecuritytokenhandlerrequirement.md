---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 31e0c2cf10b8bc93ade0d417763075c4419ac19f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="c8b35-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="c8b35-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="c8b35-103">提供組態<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="c8b35-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="c8b35-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="c8b35-104">\<system.identityModel></span></span>  
<span data-ttu-id="c8b35-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c8b35-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c8b35-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="c8b35-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="c8b35-107">\<add></span><span class="sxs-lookup"><span data-stu-id="c8b35-107">\<add></span></span>  
<span data-ttu-id="c8b35-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="c8b35-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c8b35-109">語法</span><span class="sxs-lookup"><span data-stu-id="c8b35-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c8b35-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c8b35-110">Attributes and Elements</span></span>  
 <span data-ttu-id="c8b35-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c8b35-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c8b35-112">屬性</span><span class="sxs-lookup"><span data-stu-id="c8b35-112">Attributes</span></span>  
  
|<span data-ttu-id="c8b35-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c8b35-113">Attribute</span></span>|<span data-ttu-id="c8b35-114">描述</span><span class="sxs-lookup"><span data-stu-id="c8b35-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c8b35-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="c8b35-115">membershipProviderName</span></span>|<span data-ttu-id="c8b35-116">指定<xref:System.Web.Security.MembershipProvider>，應由安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="c8b35-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c8b35-117">子元素</span><span class="sxs-lookup"><span data-stu-id="c8b35-117">Child Elements</span></span>  
 <span data-ttu-id="c8b35-118">無</span><span class="sxs-lookup"><span data-stu-id="c8b35-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c8b35-119">父項目</span><span class="sxs-lookup"><span data-stu-id="c8b35-119">Parent Elements</span></span>  
  
|<span data-ttu-id="c8b35-120">項目</span><span class="sxs-lookup"><span data-stu-id="c8b35-120">Element</span></span>|<span data-ttu-id="c8b35-121">描述</span><span class="sxs-lookup"><span data-stu-id="c8b35-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c8b35-122">\<add></span><span class="sxs-lookup"><span data-stu-id="c8b35-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="c8b35-123">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="c8b35-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c8b35-124">備註</span><span class="sxs-lookup"><span data-stu-id="c8b35-124">Remarks</span></span>  
 <span data-ttu-id="c8b35-125">`<userNameSecurityTokenHandlerRequirement>`項目集合<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A>屬性時<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>從設定初始化物件。</span><span class="sxs-lookup"><span data-stu-id="c8b35-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c8b35-126">範例</span><span class="sxs-lookup"><span data-stu-id="c8b35-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
