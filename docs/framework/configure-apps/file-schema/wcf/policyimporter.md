---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 81f38d2a163163ca7255ca546bbddbbb58fa3a1b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59094173"
---
# <a name="policyimporter"></a><span data-ttu-id="ed4ab-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="ed4ab-101">\<policyImporter></span></span>
<span data-ttu-id="ed4ab-102">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="ed4ab-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="ed4ab-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="ed4ab-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="ed4ab-104">\<client></span><span class="sxs-lookup"><span data-stu-id="ed4ab-104">\<client></span></span>  
<span data-ttu-id="ed4ab-105">\<metadata></span><span class="sxs-lookup"><span data-stu-id="ed4ab-105">\<metadata></span></span>  
<span data-ttu-id="ed4ab-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="ed4ab-106">\<policyImporters></span></span>  
<span data-ttu-id="ed4ab-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="ed4ab-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ed4ab-108">語法</span><span class="sxs-lookup"><span data-stu-id="ed4ab-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ed4ab-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ed4ab-109">Attributes and Elements</span></span>  
 <span data-ttu-id="ed4ab-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ed4ab-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ed4ab-111">屬性</span><span class="sxs-lookup"><span data-stu-id="ed4ab-111">Attributes</span></span>  
  
|<span data-ttu-id="ed4ab-112">屬性</span><span class="sxs-lookup"><span data-stu-id="ed4ab-112">Attribute</span></span>|<span data-ttu-id="ed4ab-113">描述</span><span class="sxs-lookup"><span data-stu-id="ed4ab-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="ed4ab-114">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="ed4ab-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ed4ab-115">子元素</span><span class="sxs-lookup"><span data-stu-id="ed4ab-115">Child Elements</span></span>  
 <span data-ttu-id="ed4ab-116">None</span><span class="sxs-lookup"><span data-stu-id="ed4ab-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="ed4ab-117">父項目</span><span class="sxs-lookup"><span data-stu-id="ed4ab-117">Parent Elements</span></span>  
  
|<span data-ttu-id="ed4ab-118">項目</span><span class="sxs-lookup"><span data-stu-id="ed4ab-118">Element</span></span>|<span data-ttu-id="ed4ab-119">描述</span><span class="sxs-lookup"><span data-stu-id="ed4ab-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ed4ab-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="ed4ab-120">\<policyImporters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/policyimporters.md)|<span data-ttu-id="ed4ab-121">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="ed4ab-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ed4ab-122">備註</span><span class="sxs-lookup"><span data-stu-id="ed4ab-122">Remarks</span></span>  
 <span data-ttu-id="ed4ab-123">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="ed4ab-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="ed4ab-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="ed4ab-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="ed4ab-125">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="ed4ab-125">WCF Client Configuration</span></span>](../../../../../docs/framework/wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="ed4ab-126">用戶端</span><span class="sxs-lookup"><span data-stu-id="ed4ab-126">Clients</span></span>](../../../../../docs/framework/wcf/feature-details/clients.md)
