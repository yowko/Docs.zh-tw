---
title: <claimType>
ms.date: 03/30/2017
ms.assetid: d17b5831-9a2c-45c4-b0d1-68f48e72e861
author: BrucePerlerMS
ms.openlocfilehash: 1b5427210142c70c31c5f736c9b5e281dca53f33
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91150865"
---
# \<claimType>

<span data-ttu-id="a3921-101">針對傳入的安全性權杖，指定單一選用或必要的宣告。</span><span class="sxs-lookup"><span data-stu-id="a3921-101">Specifies a single optional or required claim for incoming security tokens.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<claimTypeRequired>**](claimtyperequired.md)\  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimType>**  
  
## <a name="syntax"></a><span data-ttu-id="a3921-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="a3921-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a3921-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a3921-103">Attributes and Elements</span></span>  

 <span data-ttu-id="a3921-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a3921-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a3921-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a3921-105">Attributes</span></span>  
  
|<span data-ttu-id="a3921-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a3921-106">Attribute</span></span>|<span data-ttu-id="a3921-107">描述</span><span class="sxs-lookup"><span data-stu-id="a3921-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="a3921-108">type</span><span class="sxs-lookup"><span data-stu-id="a3921-108">type</span></span>|<span data-ttu-id="a3921-109">宣告類型。</span><span class="sxs-lookup"><span data-stu-id="a3921-109">The claim type.</span></span> <span data-ttu-id="a3921-110">通常是 URI。</span><span class="sxs-lookup"><span data-stu-id="a3921-110">Typically a URI.</span></span> <span data-ttu-id="a3921-111">必要。</span><span class="sxs-lookup"><span data-stu-id="a3921-111">Required.</span></span>|  
|<span data-ttu-id="a3921-112">選用</span><span class="sxs-lookup"><span data-stu-id="a3921-112">optional</span></span>|<span data-ttu-id="a3921-113">指定宣告類型是否為選擇性的布林值。</span><span class="sxs-lookup"><span data-stu-id="a3921-113">A boolean value that specifies whether the claim type is optional.</span></span> <span data-ttu-id="a3921-114">選擇性。</span><span class="sxs-lookup"><span data-stu-id="a3921-114">Optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a3921-115">子元素</span><span class="sxs-lookup"><span data-stu-id="a3921-115">Child Elements</span></span>  

 <span data-ttu-id="a3921-116">無</span><span class="sxs-lookup"><span data-stu-id="a3921-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a3921-117">父項目</span><span class="sxs-lookup"><span data-stu-id="a3921-117">Parent Elements</span></span>  
  
|<span data-ttu-id="a3921-118">項目</span><span class="sxs-lookup"><span data-stu-id="a3921-118">Element</span></span>|<span data-ttu-id="a3921-119">描述</span><span class="sxs-lookup"><span data-stu-id="a3921-119">Description</span></span>|  
|-------------|-----------------|  
|[\<claimTypeRequired>](claimtyperequired.md)|<span data-ttu-id="a3921-120">指定傳入安全性權杖所需的宣告集。</span><span class="sxs-lookup"><span data-stu-id="a3921-120">Specifies the set of required claims for incoming security tokens.</span></span>|
