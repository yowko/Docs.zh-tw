---
title: '&lt;claimTypeRequired&gt;'
ms.date: 03/30/2017
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
author: BrucePerlerMS
ms.openlocfilehash: df4494de6b76943849db2bedef8f43ad894b6bd1
ms.sourcegitcommit: 69229651598b427c550223d3c58aba82e47b3f82
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/04/2018
ms.locfileid: "48780657"
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="c42eb-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="c42eb-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="c42eb-103">指定必要的連入安全性權杖的宣告集。</span><span class="sxs-lookup"><span data-stu-id="c42eb-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="c42eb-104">\<system.identityModel></span><span class="sxs-lookup"><span data-stu-id="c42eb-104">\<system.identityModel></span></span>  
<span data-ttu-id="c42eb-105">\<identityConfiguration></span><span class="sxs-lookup"><span data-stu-id="c42eb-105">\<identityConfiguration></span></span>  
<span data-ttu-id="c42eb-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="c42eb-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c42eb-107">語法</span><span class="sxs-lookup"><span data-stu-id="c42eb-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c42eb-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c42eb-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c42eb-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c42eb-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c42eb-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c42eb-110">Attributes</span></span>  
 <span data-ttu-id="c42eb-111">無</span><span class="sxs-lookup"><span data-stu-id="c42eb-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c42eb-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c42eb-112">Child Elements</span></span>  
  
|<span data-ttu-id="c42eb-113">項目</span><span class="sxs-lookup"><span data-stu-id="c42eb-113">Element</span></span>|<span data-ttu-id="c42eb-114">描述</span><span class="sxs-lookup"><span data-stu-id="c42eb-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c42eb-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="c42eb-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="c42eb-116">指定連入安全性權杖的單一選用或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="c42eb-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c42eb-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c42eb-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c42eb-118">項目</span><span class="sxs-lookup"><span data-stu-id="c42eb-118">Element</span></span>|<span data-ttu-id="c42eb-119">描述</span><span class="sxs-lookup"><span data-stu-id="c42eb-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c42eb-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="c42eb-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="c42eb-121">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="c42eb-121">Specifies service-level identity settings.</span></span>|
