---
title: '&lt;userNameSecurityTokenHandlerRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: dfcaad8b150321fda2a86e601bf57204cbdc1a0e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47075027"
---
# <a name="ltusernamesecuritytokenhandlerrequirementgt"></a><span data-ttu-id="8042d-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="8042d-102">&lt;userNameSecurityTokenHandlerRequirement&gt;</span></span>
<span data-ttu-id="8042d-103">提供組態<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="8042d-103">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="8042d-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="8042d-104">\<system.identityModel></span></span>  
<span data-ttu-id="8042d-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="8042d-105">\<identityConfiguration></span></span>  
<span data-ttu-id="8042d-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="8042d-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="8042d-107">\<add></span><span class="sxs-lookup"><span data-stu-id="8042d-107">\<add></span></span>  
<span data-ttu-id="8042d-108">\<userNameSecurityTokenHandlerRequirement ></span><span class="sxs-lookup"><span data-stu-id="8042d-108">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8042d-109">語法</span><span class="sxs-lookup"><span data-stu-id="8042d-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8042d-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8042d-110">Attributes and Elements</span></span>  
 <span data-ttu-id="8042d-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8042d-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8042d-112">屬性</span><span class="sxs-lookup"><span data-stu-id="8042d-112">Attributes</span></span>  
  
|<span data-ttu-id="8042d-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8042d-113">Attribute</span></span>|<span data-ttu-id="8042d-114">描述</span><span class="sxs-lookup"><span data-stu-id="8042d-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8042d-115">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="8042d-115">membershipProviderName</span></span>|<span data-ttu-id="8042d-116">指定<xref:System.Web.Security.MembershipProvider>，應該由安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="8042d-116">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8042d-117">子元素</span><span class="sxs-lookup"><span data-stu-id="8042d-117">Child Elements</span></span>  
 <span data-ttu-id="8042d-118">無</span><span class="sxs-lookup"><span data-stu-id="8042d-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8042d-119">父項目</span><span class="sxs-lookup"><span data-stu-id="8042d-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8042d-120">項目</span><span class="sxs-lookup"><span data-stu-id="8042d-120">Element</span></span>|<span data-ttu-id="8042d-121">描述</span><span class="sxs-lookup"><span data-stu-id="8042d-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8042d-122">\<add></span><span class="sxs-lookup"><span data-stu-id="8042d-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="8042d-123">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="8042d-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="8042d-124">備註</span><span class="sxs-lookup"><span data-stu-id="8042d-124">Remarks</span></span>  
 <span data-ttu-id="8042d-125">`<userNameSecurityTokenHandlerRequirement>`項目集<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A>屬性時<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>物件從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="8042d-125">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="8042d-126">範例</span><span class="sxs-lookup"><span data-stu-id="8042d-126">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
