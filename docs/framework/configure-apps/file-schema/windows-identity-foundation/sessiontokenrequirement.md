---
title: '&lt;sessionTokenRequirement&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
caps.latest.revision: "3"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 5a141dd83cb7ef1271906871097eb68da174d22f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="1f573-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="1f573-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="1f573-103">提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="1f573-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="1f573-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="1f573-104">\<system.identityModel></span></span>  
<span data-ttu-id="1f573-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="1f573-105">\<identityConfiguration></span></span>  
<span data-ttu-id="1f573-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="1f573-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="1f573-107">\<add></span><span class="sxs-lookup"><span data-stu-id="1f573-107">\<add></span></span>  
<span data-ttu-id="1f573-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="1f573-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1f573-109">語法</span><span class="sxs-lookup"><span data-stu-id="1f573-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1f573-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1f573-110">Attributes and Elements</span></span>  
 <span data-ttu-id="1f573-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="1f573-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1f573-112">屬性</span><span class="sxs-lookup"><span data-stu-id="1f573-112">Attributes</span></span>  
  
|<span data-ttu-id="1f573-113">屬性</span><span class="sxs-lookup"><span data-stu-id="1f573-113">Attribute</span></span>|<span data-ttu-id="1f573-114">描述</span><span class="sxs-lookup"><span data-stu-id="1f573-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="1f573-115">存留期</span><span class="sxs-lookup"><span data-stu-id="1f573-115">lifetime</span></span>|<span data-ttu-id="1f573-116">指定工作階段權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="1f573-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="1f573-117">子元素</span><span class="sxs-lookup"><span data-stu-id="1f573-117">Child Elements</span></span>  
 <span data-ttu-id="1f573-118">無</span><span class="sxs-lookup"><span data-stu-id="1f573-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="1f573-119">父項目</span><span class="sxs-lookup"><span data-stu-id="1f573-119">Parent Elements</span></span>  
  
|<span data-ttu-id="1f573-120">項目</span><span class="sxs-lookup"><span data-stu-id="1f573-120">Element</span></span>|<span data-ttu-id="1f573-121">描述</span><span class="sxs-lookup"><span data-stu-id="1f573-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="1f573-122">\<add></span><span class="sxs-lookup"><span data-stu-id="1f573-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="1f573-123">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="1f573-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="1f573-124">範例</span><span class="sxs-lookup"><span data-stu-id="1f573-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
