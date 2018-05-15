---
title: '&lt;ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 94f8586a9ca63b8c1f1128cdda4a74ccfe0f5416
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="157b2-102">&lt;ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="157b2-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="157b2-103">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="157b2-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="157b2-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="157b2-104">\<system.identityModel></span></span>  
<span data-ttu-id="157b2-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="157b2-105">\<identityConfiguration></span></span>  
<span data-ttu-id="157b2-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="157b2-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="157b2-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="157b2-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="157b2-108">語法</span><span class="sxs-lookup"><span data-stu-id="157b2-108">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
      <claimType type=URI optional=xs:boolean >  
      </claimType>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="157b2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="157b2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="157b2-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="157b2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="157b2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="157b2-111">Attributes</span></span>  
  
|<span data-ttu-id="157b2-112">屬性</span><span class="sxs-lookup"><span data-stu-id="157b2-112">Attribute</span></span>|<span data-ttu-id="157b2-113">描述</span><span class="sxs-lookup"><span data-stu-id="157b2-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="157b2-114">類型</span><span class="sxs-lookup"><span data-stu-id="157b2-114">type</span></span>|<span data-ttu-id="157b2-115">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="157b2-115">The claim type.</span></span> <span data-ttu-id="157b2-116">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="157b2-116">Typically a URI.</span></span> <span data-ttu-id="157b2-117">必要。</span><span class="sxs-lookup"><span data-stu-id="157b2-117">Required.</span></span>|  
|<span data-ttu-id="157b2-118">選擇性</span><span class="sxs-lookup"><span data-stu-id="157b2-118">optional</span></span>|<span data-ttu-id="157b2-119">布林值，指定是否為選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="157b2-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="157b2-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="157b2-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="157b2-121">子項目</span><span class="sxs-lookup"><span data-stu-id="157b2-121">Child Elements</span></span>  
 <span data-ttu-id="157b2-122">無</span><span class="sxs-lookup"><span data-stu-id="157b2-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="157b2-123">父項目</span><span class="sxs-lookup"><span data-stu-id="157b2-123">Parent Elements</span></span>  
  
|<span data-ttu-id="157b2-124">項目</span><span class="sxs-lookup"><span data-stu-id="157b2-124">Element</span></span>|<span data-ttu-id="157b2-125">描述</span><span class="sxs-lookup"><span data-stu-id="157b2-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="157b2-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="157b2-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="157b2-127">指定必要的宣告集的連入安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="157b2-127">Specifies the set of required claims for incoming security tokens.</span></span>|
