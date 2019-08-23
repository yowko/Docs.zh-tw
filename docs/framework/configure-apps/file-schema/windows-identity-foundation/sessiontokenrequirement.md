---
title: <sessionTokenRequirement>
ms.date: 03/30/2017
ms.assetid: 496a1735-cbb7-49d5-a6aa-dd5550462073
author: BrucePerlerMS
ms.openlocfilehash: 254d34149892abeaf31b9227f7567eb0a66ec0b6
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69943670"
---
# <a name="sessiontokenrequirement"></a><span data-ttu-id="ab7e8-101">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ab7e8-101">\<sessionTokenRequirement></span></span>
<span data-ttu-id="ab7e8-102"><xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler>提供類別或衍生類別的設定。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-102">Provides configuration for the <xref:System.IdentityModel.Tokens.SessionSecurityTokenHandler> class or derived classes.</span></span>  
  
 <span data-ttu-id="ab7e8-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ab7e8-103">\<system.identityModel></span></span>  
<span data-ttu-id="ab7e8-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ab7e8-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ab7e8-105">\<securityTokenHandlers></span><span class="sxs-lookup"><span data-stu-id="ab7e8-105">\<securityTokenHandlers></span></span>  
<span data-ttu-id="ab7e8-106">\<add></span><span class="sxs-lookup"><span data-stu-id="ab7e8-106">\<add></span></span>  
<span data-ttu-id="ab7e8-107">\<sessionTokenRequirement></span><span class="sxs-lookup"><span data-stu-id="ab7e8-107">\<sessionTokenRequirement></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ab7e8-108">語法</span><span class="sxs-lookup"><span data-stu-id="ab7e8-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ab7e8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ab7e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ab7e8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ab7e8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ab7e8-111">Attributes</span></span>  
  
|<span data-ttu-id="ab7e8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ab7e8-112">Attribute</span></span>|<span data-ttu-id="ab7e8-113">描述</span><span class="sxs-lookup"><span data-stu-id="ab7e8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ab7e8-114">存留期</span><span class="sxs-lookup"><span data-stu-id="ab7e8-114">lifetime</span></span>|<span data-ttu-id="ab7e8-115">指定會話權杖的存留期。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-115">Specifies the lifetime of session tokens.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ab7e8-116">子元素</span><span class="sxs-lookup"><span data-stu-id="ab7e8-116">Child Elements</span></span>  
 <span data-ttu-id="ab7e8-117">None</span><span class="sxs-lookup"><span data-stu-id="ab7e8-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ab7e8-118">父項目</span><span class="sxs-lookup"><span data-stu-id="ab7e8-118">Parent Elements</span></span>  
  
|<span data-ttu-id="ab7e8-119">項目</span><span class="sxs-lookup"><span data-stu-id="ab7e8-119">Element</span></span>|<span data-ttu-id="ab7e8-120">說明</span><span class="sxs-lookup"><span data-stu-id="ab7e8-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ab7e8-121">\<add></span><span class="sxs-lookup"><span data-stu-id="ab7e8-121">\<add></span></span>](add.md)|<span data-ttu-id="ab7e8-122">將指定的安全性權杖處理常式加入至權杖處理常式集合。</span><span class="sxs-lookup"><span data-stu-id="ab7e8-122">Adds the specified security token handler to the token handler collection.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="ab7e8-123">範例</span><span class="sxs-lookup"><span data-stu-id="ab7e8-123">Example</span></span>  
  
```xml  
<add type="System.IdentityModel.Tokens.SessionSecurityTokenHandler, System.IdentityModel">           
    <sessionTokenRequirement lifetime="10:00" />  
</add>  
```
