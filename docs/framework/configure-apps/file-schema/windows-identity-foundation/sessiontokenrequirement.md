---
title: '&lt;sessionTokenRequirement&gt;'
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 4d5d2348f04ace7596a3a513c5106ea612dc17b7
ms.sourcegitcommit: ea00c05e0995dae928d48ead99ddab6296097b4c
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/02/2018
ms.locfileid: "48037166"
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="f86bb-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="f86bb-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="f86bb-103">提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="f86bb-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="f86bb-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="f86bb-104">\<system.identityModel></span></span>  
<span data-ttu-id="f86bb-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="f86bb-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f86bb-106">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="f86bb-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f86bb-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f86bb-107">\<add></span></span>  
<span data-ttu-id="f86bb-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f86bb-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f86bb-109">語法</span><span class="sxs-lookup"><span data-stu-id="f86bb-109">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <securityTokenHandlers>  
      <add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">  
        <sessionTokenRequirement lifetime=TimeSpan >  
        </sessionTokenRequirement>  
      </add>  
    </securityTokenHandlers>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f86bb-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f86bb-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f86bb-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f86bb-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f86bb-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f86bb-112">Attributes</span></span>  
  
|<span data-ttu-id="f86bb-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f86bb-113">Attribute</span></span>|<span data-ttu-id="f86bb-114">描述</span><span class="sxs-lookup"><span data-stu-id="f86bb-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f86bb-115">存留期</span><span class="sxs-lookup"><span data-stu-id="f86bb-115">lifetime</span></span>|<span data-ttu-id="f86bb-116">指定工作階段權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="f86bb-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f86bb-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f86bb-117">Child Elements</span></span>  
 <span data-ttu-id="f86bb-118">無</span><span class="sxs-lookup"><span data-stu-id="f86bb-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f86bb-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f86bb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f86bb-120">項目</span><span class="sxs-lookup"><span data-stu-id="f86bb-120">Element</span></span>|<span data-ttu-id="f86bb-121">描述</span><span class="sxs-lookup"><span data-stu-id="f86bb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f86bb-122">\<add></span><span class="sxs-lookup"><span data-stu-id="f86bb-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="f86bb-123">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f86bb-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f86bb-124">範例</span><span class="sxs-lookup"><span data-stu-id="f86bb-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
