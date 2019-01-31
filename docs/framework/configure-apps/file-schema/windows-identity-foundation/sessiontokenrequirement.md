---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 0c575e02862884e8f7ecf062138c36fe731f8e19
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55271898"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="898e1-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="898e1-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="898e1-102">提供組態<xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>類別或衍生的類別。</span><span class="sxs-lookup"><span data-stu-id="898e1-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="898e1-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="898e1-103">\<system.identityModel></span></span>  
<span data-ttu-id="898e1-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="898e1-104">\<identityConfiguration></span></span>  
<span data-ttu-id="898e1-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="898e1-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="898e1-106">\<add></span><span class="sxs-lookup"><span data-stu-id="898e1-106">\<add></span></span>  
<span data-ttu-id="898e1-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="898e1-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="898e1-108">語法</span><span class="sxs-lookup"><span data-stu-id="898e1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="898e1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="898e1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="898e1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="898e1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="898e1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="898e1-111">Attributes</span></span>  
  
|<span data-ttu-id="898e1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="898e1-112">Attribute</span></span>|<span data-ttu-id="898e1-113">描述</span><span class="sxs-lookup"><span data-stu-id="898e1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="898e1-114">存留期</span><span class="sxs-lookup"><span data-stu-id="898e1-114">lifetime</span></span>|<span data-ttu-id="898e1-115">指定工作階段權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="898e1-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="898e1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="898e1-116">Child Elements</span></span>  
 <span data-ttu-id="898e1-117">無</span><span class="sxs-lookup"><span data-stu-id="898e1-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="898e1-118">父項目</span><span class="sxs-lookup"><span data-stu-id="898e1-118">Parent Elements</span></span>  
  
|<span data-ttu-id="898e1-119">項目</span><span class="sxs-lookup"><span data-stu-id="898e1-119">Element</span></span>|<span data-ttu-id="898e1-120">描述</span><span class="sxs-lookup"><span data-stu-id="898e1-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="898e1-121">\<add></span><span class="sxs-lookup"><span data-stu-id="898e1-121">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/add.md)|<span data-ttu-id="898e1-122">將指定的安全性權杖處理常式加入至 權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="898e1-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="898e1-123">範例</span><span class="sxs-lookup"><span data-stu-id="898e1-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
