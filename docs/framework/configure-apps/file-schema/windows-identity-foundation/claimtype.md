---
title: '&lt;ClaimType&gt;'
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 805377565b6e835fd9ffba915a003bc56529a3b6
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47084211"
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="58096-102">&lt;ClaimType&gt;</span><span class="sxs-lookup"><span data-stu-id="58096-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="58096-103">指定連入安全性權杖的單一選用或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="58096-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="58096-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="58096-104">\<system.identityModel></span></span>  
<span data-ttu-id="58096-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="58096-105">\<identityConfiguration></span></span>  
<span data-ttu-id="58096-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="58096-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="58096-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="58096-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="58096-108">語法</span><span class="sxs-lookup"><span data-stu-id="58096-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="58096-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="58096-109">Attributes and Elements</span></span>  
 <span data-ttu-id="58096-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="58096-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="58096-111">屬性</span><span class="sxs-lookup"><span data-stu-id="58096-111">Attributes</span></span>  
  
|<span data-ttu-id="58096-112">屬性</span><span class="sxs-lookup"><span data-stu-id="58096-112">Attribute</span></span>|<span data-ttu-id="58096-113">描述</span><span class="sxs-lookup"><span data-stu-id="58096-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="58096-114">類型</span><span class="sxs-lookup"><span data-stu-id="58096-114">type</span></span>|<span data-ttu-id="58096-115">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="58096-115">The claim type.</span></span> <span data-ttu-id="58096-116">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="58096-116">Typically a URI.</span></span> <span data-ttu-id="58096-117">必要。</span><span class="sxs-lookup"><span data-stu-id="58096-117">Required.</span></span>|  
|<span data-ttu-id="58096-118">選擇性</span><span class="sxs-lookup"><span data-stu-id="58096-118">optional</span></span>|<span data-ttu-id="58096-119">指定的宣告型別是否為選擇性的布林值。</span><span class="sxs-lookup"><span data-stu-id="58096-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="58096-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="58096-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="58096-121">子元素</span><span class="sxs-lookup"><span data-stu-id="58096-121">Child Elements</span></span>  
 <span data-ttu-id="58096-122">無</span><span class="sxs-lookup"><span data-stu-id="58096-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="58096-123">父項目</span><span class="sxs-lookup"><span data-stu-id="58096-123">Parent Elements</span></span>  
  
|<span data-ttu-id="58096-124">項目</span><span class="sxs-lookup"><span data-stu-id="58096-124">Element</span></span>|<span data-ttu-id="58096-125">描述</span><span class="sxs-lookup"><span data-stu-id="58096-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="58096-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="58096-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="58096-127">指定必要的連入安全性權杖的宣告集。</span><span class="sxs-lookup"><span data-stu-id="58096-127">Specifies the set of required claims for incoming security tokens.</span></span>|
