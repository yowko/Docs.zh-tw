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
ms.openlocfilehash: 8b729f588d2195992b231661f7bb718240141fdd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltsessiontokenrequirementgt"></a><span data-ttu-id="f2f47-102">&lt;sessionTokenRequirement&gt;</span><span class="sxs-lookup"><span data-stu-id="f2f47-102">&lt;sessionTokenRequirement&gt;</span></span>
<span data-ttu-id="f2f47-103">提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="f2f47-103">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="f2f47-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="f2f47-104">\<system.identityModel></span></span>  
<span data-ttu-id="f2f47-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="f2f47-105">\<identityConfiguration></span></span>  
<span data-ttu-id="f2f47-106">\<securityTokenHandlers ></span><span class="sxs-lookup"><span data-stu-id="f2f47-106">\<securityTokenHandlers></span></span>  
<span data-ttu-id="f2f47-107">\<add></span><span class="sxs-lookup"><span data-stu-id="f2f47-107">\<add></span></span>  
<span data-ttu-id="f2f47-108">\<sessionTokenRequirement ></span><span class="sxs-lookup"><span data-stu-id="f2f47-108">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f2f47-109">語法</span><span class="sxs-lookup"><span data-stu-id="f2f47-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f2f47-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f2f47-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f2f47-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f2f47-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f2f47-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f2f47-112">Attributes</span></span>  
  
|<span data-ttu-id="f2f47-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f2f47-113">Attribute</span></span>|<span data-ttu-id="f2f47-114">說明</span><span class="sxs-lookup"><span data-stu-id="f2f47-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f2f47-115">存留期</span><span class="sxs-lookup"><span data-stu-id="f2f47-115">lifetime</span></span>|<span data-ttu-id="f2f47-116">指定工作階段權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="f2f47-116">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f2f47-117">子元素</span><span class="sxs-lookup"><span data-stu-id="f2f47-117">Child Elements</span></span>  
 <span data-ttu-id="f2f47-118">無</span><span class="sxs-lookup"><span data-stu-id="f2f47-118">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f2f47-119">父項目</span><span class="sxs-lookup"><span data-stu-id="f2f47-119">Parent Elements</span></span>  
  
|<span data-ttu-id="f2f47-120">項目</span><span class="sxs-lookup"><span data-stu-id="f2f47-120">Element</span></span>|<span data-ttu-id="f2f47-121">描述</span><span class="sxs-lookup"><span data-stu-id="f2f47-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f2f47-122">\<add></span><span class="sxs-lookup"><span data-stu-id="f2f47-122">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="f2f47-123">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="f2f47-123">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f2f47-124">範例</span><span class="sxs-lookup"><span data-stu-id="f2f47-124">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
