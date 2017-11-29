---
title: "&lt;範圍&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
caps.latest.revision: "2"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 6b35696cbecb0badf397d6d48e7c97aae3d0232e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="3845e-102">&lt;範圍&gt;</span><span class="sxs-lookup"><span data-stu-id="3845e-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="3845e-103">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="3845e-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="3845e-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="3845e-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="3845e-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3845e-105">\<behaviors></span></span>  
<span data-ttu-id="3845e-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="3845e-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="3845e-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="3845e-107">\<behavior></span></span>  
<span data-ttu-id="3845e-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="3845e-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="3845e-109">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="3845e-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3845e-110">語法</span><span class="sxs-lookup"><span data-stu-id="3845e-110">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3845e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3845e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="3845e-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3845e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3845e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3845e-113">Attributes</span></span>  
 <span data-ttu-id="3845e-114">無。</span><span class="sxs-lookup"><span data-stu-id="3845e-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="3845e-115">子元素</span><span class="sxs-lookup"><span data-stu-id="3845e-115">Child Elements</span></span>  
  
|<span data-ttu-id="3845e-116">屬性</span><span class="sxs-lookup"><span data-stu-id="3845e-116">Attribute</span></span>|<span data-ttu-id="3845e-117">說明</span><span class="sxs-lookup"><span data-stu-id="3845e-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="3845e-118">\<add></span><span class="sxs-lookup"><span data-stu-id="3845e-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="3845e-119">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="3845e-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="3845e-120">父項目</span><span class="sxs-lookup"><span data-stu-id="3845e-120">Parent Elements</span></span>  
  
|<span data-ttu-id="3845e-121">項目</span><span class="sxs-lookup"><span data-stu-id="3845e-121">Element</span></span>|<span data-ttu-id="3845e-122">說明</span><span class="sxs-lookup"><span data-stu-id="3845e-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3845e-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="3845e-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="3845e-124">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="3845e-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="3845e-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3845e-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
