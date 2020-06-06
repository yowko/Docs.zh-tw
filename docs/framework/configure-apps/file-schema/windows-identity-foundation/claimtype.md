---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: a46e9129bd27319abb4d7519444568af622170fc
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70252062"
---
# \<claimType>
<span data-ttu-id="c0fe5-101">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="c0fe5-102">語法</span><span class="sxs-lookup"><span data-stu-id="c0fe5-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0fe5-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0fe5-103">Attributes and Elements</span></span>  
 <span data-ttu-id="c0fe5-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0fe5-105">屬性</span><span class="sxs-lookup"><span data-stu-id="c0fe5-105">Attributes</span></span>  
  
|<span data-ttu-id="c0fe5-106">屬性</span><span class="sxs-lookup"><span data-stu-id="c0fe5-106">Attribute</span></span>|<span data-ttu-id="c0fe5-107">描述</span><span class="sxs-lookup"><span data-stu-id="c0fe5-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="c0fe5-108">type</span><span class="sxs-lookup"><span data-stu-id="c0fe5-108">type</span></span>|<span data-ttu-id="c0fe5-109">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-109">The claim type.</span></span> <span data-ttu-id="c0fe5-110">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-110">Typically a URI.</span></span> <span data-ttu-id="c0fe5-111">必要。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-111">Required.</span></span>|  
|<span data-ttu-id="c0fe5-112">選用</span><span class="sxs-lookup"><span data-stu-id="c0fe5-112">optional</span></span>|<span data-ttu-id="c0fe5-113">指定宣告類型是否為選擇性的布林值。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="c0fe5-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="c0fe5-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c0fe5-115">Child Elements</span></span>  
 <span data-ttu-id="c0fe5-116">無</span><span class="sxs-lookup"><span data-stu-id="c0fe5-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="c0fe5-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c0fe5-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c0fe5-118">元素</span><span class="sxs-lookup"><span data-stu-id="c0fe5-118">Element</span></span>|<span data-ttu-id="c0fe5-119">描述</span><span class="sxs-lookup"><span data-stu-id="c0fe5-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="c0fe5-120">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="c0fe5-120">Specifies the set of required claims for incoming security tokens.</span></span>|
