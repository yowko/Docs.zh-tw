---
title: '&lt;claimTypeRequired&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: c469d71f-6c77-4a24-97aa-53efa126ceef
caps.latest.revision: "5"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.workload: dotnet
ms.openlocfilehash: 491277e39b29d7c3e0a0d69ec8745b2c6718a91e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltclaimtyperequiredgt"></a><span data-ttu-id="d1245-102">&lt;claimTypeRequired&gt;</span><span class="sxs-lookup"><span data-stu-id="d1245-102">&lt;claimTypeRequired&gt;</span></span>
<span data-ttu-id="d1245-103">指定必要的宣告集的連入安全性權杖。</span><span class="sxs-lookup"><span data-stu-id="d1245-103">Specifies the set of required claims for incoming security tokens.</span></span>  
  
 <span data-ttu-id="d1245-104">\<system.identityModel ></span><span class="sxs-lookup"><span data-stu-id="d1245-104">\<system.identityModel></span></span>  
<span data-ttu-id="d1245-105">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d1245-105">\<identityConfiguration></span></span>  
<span data-ttu-id="d1245-106">\<claimTypeRequired ></span><span class="sxs-lookup"><span data-stu-id="d1245-106">\<claimTypeRequired></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d1245-107">語法</span><span class="sxs-lookup"><span data-stu-id="d1245-107">Syntax</span></span>  
  
```xml  
<system.identityModel>  
  <identityConfiguration>  
    <claimTypeRequired>  
    </claimTypeRequired>  
  </identityConfiguration>  
</system.identityModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d1245-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d1245-108">Attributes and Elements</span></span>  
 <span data-ttu-id="d1245-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d1245-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d1245-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d1245-110">Attributes</span></span>  
 <span data-ttu-id="d1245-111">無</span><span class="sxs-lookup"><span data-stu-id="d1245-111">None</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="d1245-112">子元素</span><span class="sxs-lookup"><span data-stu-id="d1245-112">Child Elements</span></span>  
  
|<span data-ttu-id="d1245-113">項目</span><span class="sxs-lookup"><span data-stu-id="d1245-113">Element</span></span>|<span data-ttu-id="d1245-114">描述</span><span class="sxs-lookup"><span data-stu-id="d1245-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1245-115">\<claimType ></span><span class="sxs-lookup"><span data-stu-id="d1245-115">\<claimType></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/claimtype.md)|<span data-ttu-id="d1245-116">指定連入安全性權杖的單一選擇性或必要宣告。</span><span class="sxs-lookup"><span data-stu-id="d1245-116">Specifies a single optional or required claim for incoming security tokens.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="d1245-117">父項目</span><span class="sxs-lookup"><span data-stu-id="d1245-117">Parent Elements</span></span>  
  
|<span data-ttu-id="d1245-118">項目</span><span class="sxs-lookup"><span data-stu-id="d1245-118">Element</span></span>|<span data-ttu-id="d1245-119">描述</span><span class="sxs-lookup"><span data-stu-id="d1245-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d1245-120">\<identityConfiguration ></span><span class="sxs-lookup"><span data-stu-id="d1245-120">\<identityConfiguration></span></span>](../../../../../docs/framework/configure-apps/file-schema/windows-identity-foundation/identityconfiguration.md)|<span data-ttu-id="d1245-121">指定服務層級身分識別設定。</span><span class="sxs-lookup"><span data-stu-id="d1245-121">Specifies service-level identity settings.</span></span>|
