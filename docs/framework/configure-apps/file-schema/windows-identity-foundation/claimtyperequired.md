---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
manager: mbaldwin
ms.openlocfilehash: 6fb600aac46b3ee5cb54fa904d35ac7b7ed90719
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
ms.locfileid: "32754950"
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="7b182-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="7b182-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="7b182-103">指定必要的宣告集的連入安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="7b182-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="7b182-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="7b182-104">\<system.identityModel></span></span>  
<span data-ttu-id="7b182-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="7b182-105">\<identityConfiguration></span></span>  
<span data-ttu-id="7b182-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="7b182-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b182-107">語法</span><span class="sxs-lookup"><span data-stu-id="7b182-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b182-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b182-108">Attributes and Elements</span></span>  
 <span data-ttu-id="7b182-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7b182-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b182-110">屬性</span><span class="sxs-lookup"><span data-stu-id="7b182-110">Attributes</span></span>  
 <span data-ttu-id="7b182-111">無</span><span class="sxs-lookup"><span data-stu-id="7b182-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b182-112">子項目</span><span class="sxs-lookup"><span data-stu-id="7b182-112">Child Elements</span></span>  
  
|<span data-ttu-id="7b182-113">項目</span><span class="sxs-lookup"><span data-stu-id="7b182-113">Element</span></span>|<span data-ttu-id="7b182-114">描述</span><span class="sxs-lookup"><span data-stu-id="7b182-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b182-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="7b182-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="7b182-116">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="7b182-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b182-117">父項目</span><span class="sxs-lookup"><span data-stu-id="7b182-117">Parent Elements</span></span>  
  
|<span data-ttu-id="7b182-118">項目</span><span class="sxs-lookup"><span data-stu-id="7b182-118">Element</span></span>|<span data-ttu-id="7b182-119">描述</span><span class="sxs-lookup"><span data-stu-id="7b182-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b182-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="7b182-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="7b182-121">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="7b182-121">Specifies service-level identity settings.</span></span>|
