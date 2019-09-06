---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 1c40c5e4b4a24a3c1bbd6e096f12b7b044331c88
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/04/2019
ms.locfileid: "70252056"
---
# <a name="claimtyperequired"></a><span data-ttu-id="3eff2-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="3eff2-101">\<claimTypeRequired></span></span>
<span data-ttu-id="3eff2-102">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="3eff2-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
<span data-ttu-id="3eff2-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="3eff2-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="3eff2-104">&nbsp;&nbsp;[ **\<Microsoft.identitymodel >** ](system-identitymodel.md)</span><span class="sxs-lookup"><span data-stu-id="3eff2-104">&nbsp;&nbsp;[**\<system.identityModel>**](system-identitymodel.md)</span></span>\
<span data-ttu-id="3eff2-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<identityConfiguration >** ](identityconfiguration.md)</span><span class="sxs-lookup"><span data-stu-id="3eff2-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<identityConfiguration>**](identityconfiguration.md)</span></span>\
<span data-ttu-id="3eff2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<claimTypeRequired >**</span><span class="sxs-lookup"><span data-stu-id="3eff2-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<claimTypeRequired>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3eff2-107">語法</span><span class="sxs-lookup"><span data-stu-id="3eff2-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3eff2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3eff2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="3eff2-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3eff2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3eff2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="3eff2-110">Attributes</span></span>  
 <span data-ttu-id="3eff2-111">無</span><span class="sxs-lookup"><span data-stu-id="3eff2-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3eff2-112">子元素</span><span class="sxs-lookup"><span data-stu-id="3eff2-112">Child Elements</span></span>  
  
|<span data-ttu-id="3eff2-113">項目</span><span class="sxs-lookup"><span data-stu-id="3eff2-113">Element</span></span>|<span data-ttu-id="3eff2-114">說明</span><span class="sxs-lookup"><span data-stu-id="3eff2-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eff2-115">\<claimType></span><span class="sxs-lookup"><span data-stu-id="3eff2-115">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="3eff2-116">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="3eff2-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3eff2-117">父項目</span><span class="sxs-lookup"><span data-stu-id="3eff2-117">Parent Elements</span></span>  
  
|<span data-ttu-id="3eff2-118">項目</span><span class="sxs-lookup"><span data-stu-id="3eff2-118">Element</span></span>|<span data-ttu-id="3eff2-119">描述</span><span class="sxs-lookup"><span data-stu-id="3eff2-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3eff2-120">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="3eff2-120">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="3eff2-121">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="3eff2-121">Specifies service-level identity settings.</span></span>|
