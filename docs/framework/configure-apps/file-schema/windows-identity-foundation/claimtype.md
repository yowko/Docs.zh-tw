---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 4253aec961b812b6893ee201861d2ab38048032a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942872"
---
# <a name="claimtype"></a><span data-ttu-id="4d8a7-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="4d8a7-101">\<claimType></span></span>
<span data-ttu-id="4d8a7-102">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="4d8a7-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="4d8a7-103">\<system.identityModel></span></span>  
<span data-ttu-id="4d8a7-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="4d8a7-104">\<identityConfiguration></span></span>  
<span data-ttu-id="4d8a7-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="4d8a7-105">\<claimTypeRequired></span></span>  
<span data-ttu-id="4d8a7-106">\<claimType></span><span class="sxs-lookup"><span data-stu-id="4d8a7-106">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4d8a7-107">語法</span><span class="sxs-lookup"><span data-stu-id="4d8a7-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4d8a7-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4d8a7-108">Attributes and Elements</span></span>  
 <span data-ttu-id="4d8a7-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4d8a7-110">屬性</span><span class="sxs-lookup"><span data-stu-id="4d8a7-110">Attributes</span></span>  
  
|<span data-ttu-id="4d8a7-111">屬性</span><span class="sxs-lookup"><span data-stu-id="4d8a7-111">Attribute</span></span>|<span data-ttu-id="4d8a7-112">描述</span><span class="sxs-lookup"><span data-stu-id="4d8a7-112">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4d8a7-113">型別</span><span class="sxs-lookup"><span data-stu-id="4d8a7-113">type</span></span>|<span data-ttu-id="4d8a7-114">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-114">The claim type.</span></span> <span data-ttu-id="4d8a7-115">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-115">Typically a URI.</span></span> <span data-ttu-id="4d8a7-116">必要項。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-116">Required.</span></span>|  
|<span data-ttu-id="4d8a7-117">選擇性</span><span class="sxs-lookup"><span data-stu-id="4d8a7-117">optional</span></span>|<span data-ttu-id="4d8a7-118">指定宣告類型是否為選擇性的布林值。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-118">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="4d8a7-119">選擇性。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-119">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4d8a7-120">子元素</span><span class="sxs-lookup"><span data-stu-id="4d8a7-120">Child Elements</span></span>  
 <span data-ttu-id="4d8a7-121">無</span><span class="sxs-lookup"><span data-stu-id="4d8a7-121">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="4d8a7-122">父項目</span><span class="sxs-lookup"><span data-stu-id="4d8a7-122">Parent Elements</span></span>  
  
|<span data-ttu-id="4d8a7-123">項目</span><span class="sxs-lookup"><span data-stu-id="4d8a7-123">Element</span></span>|<span data-ttu-id="4d8a7-124">描述</span><span class="sxs-lookup"><span data-stu-id="4d8a7-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="4d8a7-125">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="4d8a7-125">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="4d8a7-126">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="4d8a7-126">Specifies the set of required claims for incoming security tokens.</span></span>|
