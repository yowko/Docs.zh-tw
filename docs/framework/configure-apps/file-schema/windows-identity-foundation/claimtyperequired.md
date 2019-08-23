---
title: <claimTypeRequired>
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: 85f3954514fa8b532311b1fbfc34f32ebefa4099
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69942822"
---
# <a name="claimtyperequired"></a><span data-ttu-id="ea13b-101">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="ea13b-101">\<claimTypeRequired></span></span>
<span data-ttu-id="ea13b-102">指定傳入安全性權杖的必要宣告集合。</span><span class="sxs-lookup"><span data-stu-id="ea13b-102">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="ea13b-103">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="ea13b-103">\<system.identityModel></span></span>  
<span data-ttu-id="ea13b-104">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ea13b-104">\<identityConfiguration></span></span>  
<span data-ttu-id="ea13b-105">\<claimTypeRequired></span><span class="sxs-lookup"><span data-stu-id="ea13b-105">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea13b-106">語法</span><span class="sxs-lookup"><span data-stu-id="ea13b-106">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ea13b-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ea13b-107">Attributes and Elements</span></span>  
 <span data-ttu-id="ea13b-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ea13b-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ea13b-109">屬性</span><span class="sxs-lookup"><span data-stu-id="ea13b-109">Attributes</span></span>  
 <span data-ttu-id="ea13b-110">None</span><span class="sxs-lookup"><span data-stu-id="ea13b-110">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="ea13b-111">子元素</span><span class="sxs-lookup"><span data-stu-id="ea13b-111">Child Elements</span></span>  
  
|<span data-ttu-id="ea13b-112">項目</span><span class="sxs-lookup"><span data-stu-id="ea13b-112">Element</span></span>|<span data-ttu-id="ea13b-113">描述</span><span class="sxs-lookup"><span data-stu-id="ea13b-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea13b-114">\<claimType></span><span class="sxs-lookup"><span data-stu-id="ea13b-114">\<claimType></span></span>](claimtype.md)|<span data-ttu-id="ea13b-115">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="ea13b-115">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ea13b-116">父項目</span><span class="sxs-lookup"><span data-stu-id="ea13b-116">Parent Elements</span></span>  
  
|<span data-ttu-id="ea13b-117">項目</span><span class="sxs-lookup"><span data-stu-id="ea13b-117">Element</span></span>|<span data-ttu-id="ea13b-118">描述</span><span class="sxs-lookup"><span data-stu-id="ea13b-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ea13b-119">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="ea13b-119">\<identityConfiguration></span></span>](identityconfiguration.md)|<span data-ttu-id="ea13b-120">指定服務層級的身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="ea13b-120">Specifies service-level identity settings.</span></span>|
