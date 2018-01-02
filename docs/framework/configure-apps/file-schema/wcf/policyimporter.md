---
title: '&lt;policyImporter&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2226b4f55025c9dec3fdeb4f9b4f51016ffd3e8e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="f3a6a-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="f3a6a-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="f3a6a-103">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="f3a6a-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="f3a6a-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="f3a6a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f3a6a-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="f3a6a-105">\<client></span></span>  
<span data-ttu-id="f3a6a-106">\<中繼資料 ></span><span class="sxs-lookup"><span data-stu-id="f3a6a-106">\<metadata></span></span>  
<span data-ttu-id="f3a6a-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="f3a6a-107">\<policyImporters></span></span>  
<span data-ttu-id="f3a6a-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="f3a6a-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3a6a-109">語法</span><span class="sxs-lookup"><span data-stu-id="f3a6a-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3a6a-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f3a6a-110">Attributes and Elements</span></span>  
 <span data-ttu-id="f3a6a-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f3a6a-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3a6a-112">屬性</span><span class="sxs-lookup"><span data-stu-id="f3a6a-112">Attributes</span></span>  
  
|<span data-ttu-id="f3a6a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="f3a6a-113">Attribute</span></span>|<span data-ttu-id="f3a6a-114">描述</span><span class="sxs-lookup"><span data-stu-id="f3a6a-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="f3a6a-115">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="f3a6a-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3a6a-116">子元素</span><span class="sxs-lookup"><span data-stu-id="f3a6a-116">Child Elements</span></span>  
 <span data-ttu-id="f3a6a-117">無</span><span class="sxs-lookup"><span data-stu-id="f3a6a-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3a6a-118">父項目</span><span class="sxs-lookup"><span data-stu-id="f3a6a-118">Parent Elements</span></span>  
  
|<span data-ttu-id="f3a6a-119">項目</span><span class="sxs-lookup"><span data-stu-id="f3a6a-119">Element</span></span>|<span data-ttu-id="f3a6a-120">描述</span><span class="sxs-lookup"><span data-stu-id="f3a6a-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3a6a-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="f3a6a-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="f3a6a-122">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="f3a6a-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="f3a6a-123">備註</span><span class="sxs-lookup"><span data-stu-id="f3a6a-123">Remarks</span></span>  
 <span data-ttu-id="f3a6a-124">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="f3a6a-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f3a6a-125">請參閱</span><span class="sxs-lookup"><span data-stu-id="f3a6a-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="f3a6a-126">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="f3a6a-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="f3a6a-127">用戶端</span><span class="sxs-lookup"><span data-stu-id="f3a6a-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
