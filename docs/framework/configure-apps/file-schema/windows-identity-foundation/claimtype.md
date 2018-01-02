---
title: '&lt;claimType&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
caps.latest.revision: "4"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: ae572ff3a8a2335a4259bdce2af5f6922fb0596f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtypegt"></a><span data-ttu-id="05b45-102">&lt;claimType&gt;</span><span class="sxs-lookup"><span data-stu-id="05b45-102">&lt;claimType&gt;</span></span>
<span data-ttu-id="05b45-103">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="05b45-103">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
 <span data-ttu-id="05b45-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="05b45-104">\<system.identityModel></span></span>  
<span data-ttu-id="05b45-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="05b45-105">\<identityConfiguration></span></span>  
<span data-ttu-id="05b45-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="05b45-106">\<claimTypeRequired></span></span>  
<span data-ttu-id="05b45-107">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="05b45-107">\<claimType></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="05b45-108">語法</span><span class="sxs-lookup"><span data-stu-id="05b45-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="05b45-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="05b45-109">Attributes and Elements</span></span>  
 <span data-ttu-id="05b45-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="05b45-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="05b45-111">屬性</span><span class="sxs-lookup"><span data-stu-id="05b45-111">Attributes</span></span>  
  
|<span data-ttu-id="05b45-112">屬性</span><span class="sxs-lookup"><span data-stu-id="05b45-112">Attribute</span></span>|<span data-ttu-id="05b45-113">描述</span><span class="sxs-lookup"><span data-stu-id="05b45-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="05b45-114">類型</span><span class="sxs-lookup"><span data-stu-id="05b45-114">type</span></span>|<span data-ttu-id="05b45-115">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="05b45-115">The claim type.</span></span> <span data-ttu-id="05b45-116">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="05b45-116">Typically a URI.</span></span> <span data-ttu-id="05b45-117">必要。</span><span class="sxs-lookup"><span data-stu-id="05b45-117">Required.</span></span>|  
|<span data-ttu-id="05b45-118">選擇性</span><span class="sxs-lookup"><span data-stu-id="05b45-118">optional</span></span>|<span data-ttu-id="05b45-119">布林值，指定是否為選擇性宣告型別。</span><span class="sxs-lookup"><span data-stu-id="05b45-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="05b45-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="05b45-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="05b45-121">子元素</span><span class="sxs-lookup"><span data-stu-id="05b45-121">Child Elements</span></span>  
 <span data-ttu-id="05b45-122">無</span><span class="sxs-lookup"><span data-stu-id="05b45-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="05b45-123">父項目</span><span class="sxs-lookup"><span data-stu-id="05b45-123">Parent Elements</span></span>  
  
|<span data-ttu-id="05b45-124">項目</span><span class="sxs-lookup"><span data-stu-id="05b45-124">Element</span></span>|<span data-ttu-id="05b45-125">描述</span><span class="sxs-lookup"><span data-stu-id="05b45-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="05b45-126">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="05b45-126">\<claimTypeRequired></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtyperequired.md)|<span data-ttu-id="05b45-127">指定必要的宣告集的連入安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="05b45-127">Specifies the set of required claims for incoming security tokens.</span></span>|
