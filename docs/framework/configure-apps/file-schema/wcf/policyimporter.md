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
ms.openlocfilehash: b56c431c0e8dbab7bd4680a6e692d9b4f6e0eec4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltpolicyimportergt"></a><span data-ttu-id="dda26-102">&lt;policyImporter&gt;</span><span class="sxs-lookup"><span data-stu-id="dda26-102">&lt;policyImporter&gt;</span></span>
<span data-ttu-id="dda26-103">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="dda26-103">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="dda26-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="dda26-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="dda26-105">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="dda26-105">\<client></span></span>  
<span data-ttu-id="dda26-106">\<中繼資料 ></span><span class="sxs-lookup"><span data-stu-id="dda26-106">\<metadata></span></span>  
<span data-ttu-id="dda26-107">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="dda26-107">\<policyImporters></span></span>  
<span data-ttu-id="dda26-108">\<policyImporter ></span><span class="sxs-lookup"><span data-stu-id="dda26-108">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="dda26-109">語法</span><span class="sxs-lookup"><span data-stu-id="dda26-109">Syntax</span></span>  
  
```xml  
<metadata>  
   <policyImporters>  
      <policyImporter type="string" />  
   </policyImporters>  
</metadata>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="dda26-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="dda26-110">Attributes and Elements</span></span>  
 <span data-ttu-id="dda26-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="dda26-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="dda26-112">屬性</span><span class="sxs-lookup"><span data-stu-id="dda26-112">Attributes</span></span>  
  
|<span data-ttu-id="dda26-113">屬性</span><span class="sxs-lookup"><span data-stu-id="dda26-113">Attribute</span></span>|<span data-ttu-id="dda26-114">描述</span><span class="sxs-lookup"><span data-stu-id="dda26-114">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="dda26-115">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="dda26-115">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="dda26-116">子元素</span><span class="sxs-lookup"><span data-stu-id="dda26-116">Child Elements</span></span>  
 <span data-ttu-id="dda26-117">無</span><span class="sxs-lookup"><span data-stu-id="dda26-117">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="dda26-118">父項目</span><span class="sxs-lookup"><span data-stu-id="dda26-118">Parent Elements</span></span>  
  
|<span data-ttu-id="dda26-119">項目</span><span class="sxs-lookup"><span data-stu-id="dda26-119">Element</span></span>|<span data-ttu-id="dda26-120">說明</span><span class="sxs-lookup"><span data-stu-id="dda26-120">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="dda26-121">\<policyImporters ></span><span class="sxs-lookup"><span data-stu-id="dda26-121">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="dda26-122">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="dda26-122">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="dda26-123">備註</span><span class="sxs-lookup"><span data-stu-id="dda26-123">Remarks</span></span>  
 <span data-ttu-id="dda26-124">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="dda26-124">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="dda26-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="dda26-125">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>  
 <xref:System.ServiceModel.Configuration.PolicyImporterElement>  
 <xref:System.ServiceModel.Configuration.MetadataElement>  
 <xref:System.ServiceModel.Description.MetadataImporter>  
 [<span data-ttu-id="dda26-126">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="dda26-126">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)  
 [<span data-ttu-id="dda26-127">用戶端</span><span class="sxs-lookup"><span data-stu-id="dda26-127">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
