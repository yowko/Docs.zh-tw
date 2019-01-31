---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 6bc185572528d4229ee53f1421eaa5bf27b053e6
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55267231"
---
# <a name="claimtype"></a><span data-ttu-id="858c6-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="858c6-101">\<claimType></span></span>
<span data-ttu-id="858c6-102">指定連入安全性權杖的單一選用或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="858c6-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="858c6-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="858c6-103">\<system.identityModel></span></span>  
<span data-ttu-id="858c6-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="858c6-104">\<identityConfiguration></span></span>  
<span data-ttu-id="858c6-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="858c6-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="858c6-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="858c6-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="858c6-107">語法</span><span class="sxs-lookup"><span data-stu-id="858c6-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="858c6-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="858c6-108">Attributes and Elements</span></span>  
 <span data-ttu-id="858c6-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="858c6-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="858c6-110">屬性</span><span class="sxs-lookup"><span data-stu-id="858c6-110">Attributes</span></span>  
  
|<span data-ttu-id="858c6-111">屬性</span><span class="sxs-lookup"><span data-stu-id="858c6-111">Attribute</span></span>|<span data-ttu-id="858c6-112">描述</span><span class="sxs-lookup"><span data-stu-id="858c6-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="858c6-113">類型</span><span class="sxs-lookup"><span data-stu-id="858c6-113">type</span></span>|<span data-ttu-id="858c6-114">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="858c6-114">The claim type.</span></span> <span data-ttu-id="858c6-115">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="858c6-115">Typically a URI.</span></span> <span data-ttu-id="858c6-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="858c6-116">Required.</span></span>|  
|<span data-ttu-id="858c6-117">選擇性</span><span class="sxs-lookup"><span data-stu-id="858c6-117">optional</span></span>|<span data-ttu-id="858c6-118">指定的宣告型別是否為選擇性的布林值。</span><span class="sxs-lookup"><span data-stu-id="858c6-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="858c6-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="858c6-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="858c6-120">子元素</span><span class="sxs-lookup"><span data-stu-id="858c6-120">Child Elements</span></span>  
 <span data-ttu-id="858c6-121">無</span><span class="sxs-lookup"><span data-stu-id="858c6-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="858c6-122">父項目</span><span class="sxs-lookup"><span data-stu-id="858c6-122">Parent Elements</span></span>  
  
|<span data-ttu-id="858c6-123">項目</span><span class="sxs-lookup"><span data-stu-id="858c6-123">Element</span></span>|<span data-ttu-id="858c6-124">描述</span><span class="sxs-lookup"><span data-stu-id="858c6-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="858c6-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="858c6-125">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="858c6-126">指定必要的連入安全性權杖的宣告集。</span><span class="sxs-lookup"><span data-stu-id="858c6-126">Specifies the set of required claims for incoming security tokens.</span></span>|
