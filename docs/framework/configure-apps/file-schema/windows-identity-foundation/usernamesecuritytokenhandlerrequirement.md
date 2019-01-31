---
title: <userNameSecurityTokenHandlerRequirement>
ms.date: 03/30/2017
ms.assetid: 6ec3bac1-b014-49ae-843c-c54518cb709a
author: BrucePerlerMS
ms.openlocfilehash: 18769794da8528f085c567264827db5aa6b214f1
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271885"
---
# <a name="usernamesecuritytokenhandlerrequirement"></a><span data-ttu-id="54359-101">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="54359-101">\<userNameSecurityTokenHandlerRequirement></span></span>
<span data-ttu-id="54359-102">提供組態<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="54359-102">Provides configuration for the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="54359-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="54359-103">\<system.identityModel></span></span>  
<span data-ttu-id="54359-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="54359-104">\<identityConfiguration></span></span>  
<span data-ttu-id="54359-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="54359-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="54359-106">\<add></span><span class="sxs-lookup"><span data-stu-id="54359-106">\<add></span></span>  
<span data-ttu-id="54359-107">\<userNameSecurityTokenHandlerRequirement></span><span class="sxs-lookup"><span data-stu-id="54359-107">\<userNameSecurityTokenHandlerRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="54359-108">語法</span><span class="sxs-lookup"><span data-stu-id="54359-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="54359-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="54359-109">Attributes and Elements</span></span>  
 <span data-ttu-id="54359-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="54359-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="54359-111">屬性</span><span class="sxs-lookup"><span data-stu-id="54359-111">Attributes</span></span>  
  
|<span data-ttu-id="54359-112">屬性</span><span class="sxs-lookup"><span data-stu-id="54359-112">Attribute</span></span>|<span data-ttu-id="54359-113">描述</span><span class="sxs-lookup"><span data-stu-id="54359-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="54359-114">membershipProviderName</span><span class="sxs-lookup"><span data-stu-id="54359-114">membershipProviderName</span></span>|<span data-ttu-id="54359-115">指定<xref:System.Web.Security.MembershipProvider>，應該由安全性權杖處理常式。</span><span class="sxs-lookup"><span data-stu-id="54359-115">Specifies the <xref:System.Web.Security.MembershipProvider> that should be used by the security token handler.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="54359-116">子元素</span><span class="sxs-lookup"><span data-stu-id="54359-116">Child Elements</span></span>  
 <span data-ttu-id="54359-117">無</span><span class="sxs-lookup"><span data-stu-id="54359-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="54359-118">父項目</span><span class="sxs-lookup"><span data-stu-id="54359-118">Parent Elements</span></span>  
  
|<span data-ttu-id="54359-119">項目</span><span class="sxs-lookup"><span data-stu-id="54359-119">Element</span></span>|<span data-ttu-id="54359-120">描述</span><span class="sxs-lookup"><span data-stu-id="54359-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="54359-121">\<add></span><span class="sxs-lookup"><span data-stu-id="54359-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="54359-122">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="54359-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="54359-123">備註</span><span class="sxs-lookup"><span data-stu-id="54359-123">Remarks</span></span>  
 <span data-ttu-id="54359-124">`<userNameSecurityTokenHandlerRequirement>`項目集<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A>屬性時<xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler>物件從組態初始化。</span><span class="sxs-lookup"><span data-stu-id="54359-124">The `<userNameSecurityTokenHandlerRequirement>` element sets the <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler.MembershipProvider%2A> property when a <xref:System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler> object is initialized from configuration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="54359-125">範例</span><span class="sxs-lookup"><span data-stu-id="54359-125">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Services.Tokens.MembershipUserNameSecurityTokenHandler, System.IdentityModel.Services">  
    <userNameSecurityTokenHandlerRequirement membershipProviderName="AspNetSqlProvider/>  
</add>  
```
