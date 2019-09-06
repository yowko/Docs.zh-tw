---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252062"
---
# <a name="claimtype"></a><span data-ttu-id="252fa-101">\<claimType></span><span class="sxs-lookup"><span data-stu-id="252fa-101">\<claimType></span></span>
<span data-ttu-id="252fa-102">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="252fa-102">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
<span data-ttu-id="252fa-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="252fa-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="252fa-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="252fa-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="252fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="252fa-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="252fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<claimTypeRequired >** ](claimtyperequired.md)</span><span class="sxs-lookup"><span data-stu-id="252fa-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)</span></span>\  
<span data-ttu-id="252fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimType >**</span><span class="sxs-lookup"><span data-stu-id="252fa-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="252fa-108">語法</span><span class="sxs-lookup"><span data-stu-id="252fa-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="252fa-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="252fa-109">Attributes and Elements</span></span>  
 <span data-ttu-id="252fa-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="252fa-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="252fa-111">屬性</span><span class="sxs-lookup"><span data-stu-id="252fa-111">Attributes</span></span>  
  
|<span data-ttu-id="252fa-112">屬性</span><span class="sxs-lookup"><span data-stu-id="252fa-112">Attribute</span></span>|<span data-ttu-id="252fa-113">描述</span><span class="sxs-lookup"><span data-stu-id="252fa-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="252fa-114">型別</span><span class="sxs-lookup"><span data-stu-id="252fa-114">type</span></span>|<span data-ttu-id="252fa-115">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="252fa-115">The claim type.</span></span> <span data-ttu-id="252fa-116">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="252fa-116">Typically a URI.</span></span> <span data-ttu-id="252fa-117">必要項。</span><span class="sxs-lookup"><span data-stu-id="252fa-117">Required.</span></span>|  
|<span data-ttu-id="252fa-118">選擇性</span><span class="sxs-lookup"><span data-stu-id="252fa-118">optional</span></span>|<span data-ttu-id="252fa-119">指定宣告類型是否為選擇性的布林值。</span><span class="sxs-lookup"><span data-stu-id="252fa-119">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="252fa-120">選擇性。</span><span class="sxs-lookup"><span data-stu-id="252fa-120">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="252fa-121">子元素</span><span class="sxs-lookup"><span data-stu-id="252fa-121">Child Elements</span></span>  
 <span data-ttu-id="252fa-122">無</span><span class="sxs-lookup"><span data-stu-id="252fa-122">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="252fa-123">父項目</span><span class="sxs-lookup"><span data-stu-id="252fa-123">Parent Elements</span></span>  
  
|<span data-ttu-id="252fa-124">項目</span><span class="sxs-lookup"><span data-stu-id="252fa-124">Element</span></span>|<span data-ttu-id="252fa-125">描述</span><span class="sxs-lookup"><span data-stu-id="252fa-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="252fa-126">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="252fa-126">\<claimTypeRequired></span></span>](claimtyperequired.md)|<span data-ttu-id="252fa-127">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="252fa-127">Specifies the set of required claims for incoming security tokens.</span></span>|
