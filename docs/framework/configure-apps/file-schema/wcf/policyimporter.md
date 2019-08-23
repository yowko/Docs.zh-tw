---
title: <policyImporter>
ms.date: 03/30/2017
ms.assetid: b0d03456-546f-44bb-ab12-1b2ce7f98fca
ms.openlocfilehash: 273bd0d5e68a661c639b82264b440b83d8127427
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933797"
---
# <a name="policyimporter"></a><span data-ttu-id="9373b-101">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="9373b-101">\<policyImporter></span></span>
<span data-ttu-id="9373b-102">指定原則匯入工具，此工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="9373b-102">Specifies a policy importer that controls the import of custom policy assertions about bindings.</span></span>  
  
 <span data-ttu-id="9373b-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9373b-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9373b-104">\<用戶端 ></span><span class="sxs-lookup"><span data-stu-id="9373b-104">\<client></span></span>  
<span data-ttu-id="9373b-105">\<中繼資料 ></span><span class="sxs-lookup"><span data-stu-id="9373b-105">\<metadata></span></span>  
<span data-ttu-id="9373b-106">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="9373b-106">\<policyImporters></span></span>  
<span data-ttu-id="9373b-107">\<policyImporter></span><span class="sxs-lookup"><span data-stu-id="9373b-107">\<policyImporter></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9373b-108">語法</span><span class="sxs-lookup"><span data-stu-id="9373b-108">Syntax</span></span>  
  
```xml  
<metadata>
  <policyImporters>
    <policyImporter type="String" />
  </policyImporters>
</metadata>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9373b-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9373b-109">Attributes and Elements</span></span>  
 <span data-ttu-id="9373b-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9373b-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9373b-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9373b-111">Attributes</span></span>  
  
|<span data-ttu-id="9373b-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9373b-112">Attribute</span></span>|<span data-ttu-id="9373b-113">描述</span><span class="sxs-lookup"><span data-stu-id="9373b-113">Description</span></span>|  
|---------------|-----------------|  
|`type`|<span data-ttu-id="9373b-114">此項目的型別。</span><span class="sxs-lookup"><span data-stu-id="9373b-114">The type of this element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9373b-115">子元素</span><span class="sxs-lookup"><span data-stu-id="9373b-115">Child Elements</span></span>  
 <span data-ttu-id="9373b-116">無</span><span class="sxs-lookup"><span data-stu-id="9373b-116">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9373b-117">父項目</span><span class="sxs-lookup"><span data-stu-id="9373b-117">Parent Elements</span></span>  
  
|<span data-ttu-id="9373b-118">項目</span><span class="sxs-lookup"><span data-stu-id="9373b-118">Element</span></span>|<span data-ttu-id="9373b-119">說明</span><span class="sxs-lookup"><span data-stu-id="9373b-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9373b-120">\<policyImporters></span><span class="sxs-lookup"><span data-stu-id="9373b-120">\<policyImporters></span></span>](policyimporters.md)|<span data-ttu-id="9373b-121">指定所有原則匯入工具，這些工具會控制匯入有關繫結的自訂原則判斷提示 (Assertion)。</span><span class="sxs-lookup"><span data-stu-id="9373b-121">Specifies all the policy importers that control the import of custom policy assertions about bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9373b-122">備註</span><span class="sxs-lookup"><span data-stu-id="9373b-122">Remarks</span></span>  
 <span data-ttu-id="9373b-123">原則匯入工具是用來搜尋有關繫結功能的自訂原則判斷提示，以及附加可實作判斷提示所需要功能的自訂繫結項目。</span><span class="sxs-lookup"><span data-stu-id="9373b-123">A policy importer is used to search custom policy assertions about binding features, as well as attach a custom binding element that implements the features the assertion requires.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9373b-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9373b-124">See also</span></span>

- <xref:System.ServiceModel.Configuration.PolicyImporterElementCollection>
- <xref:System.ServiceModel.Configuration.PolicyImporterElement>
- <xref:System.ServiceModel.Configuration.MetadataElement>
- <xref:System.ServiceModel.Description.MetadataImporter>
- [<span data-ttu-id="9373b-125">WCF 用戶端組態</span><span class="sxs-lookup"><span data-stu-id="9373b-125">WCF Client Configuration</span></span>](../../../wcf/feature-details/client-configuration.md)
- [<span data-ttu-id="9373b-126">用戶端</span><span class="sxs-lookup"><span data-stu-id="9373b-126">Clients</span></span>](../../../wcf/feature-details/clients.md)
