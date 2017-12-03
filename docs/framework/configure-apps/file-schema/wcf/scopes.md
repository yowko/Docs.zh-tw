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
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 9f198811483edb8a7be882588c38b1f3942f8bb4
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltscopesgt"></a><span data-ttu-id="e64b3-102">&lt;範圍&gt;</span><span class="sxs-lookup"><span data-stu-id="e64b3-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="e64b3-103">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="e64b3-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="e64b3-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="e64b3-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="e64b3-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e64b3-105">\<behaviors></span></span>  
<span data-ttu-id="e64b3-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="e64b3-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="e64b3-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="e64b3-107">\<behavior></span></span>  
<span data-ttu-id="e64b3-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="e64b3-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="e64b3-109">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="e64b3-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e64b3-110">語法</span><span class="sxs-lookup"><span data-stu-id="e64b3-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e64b3-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e64b3-111">Attributes and Elements</span></span>  
 <span data-ttu-id="e64b3-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e64b3-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e64b3-113">屬性</span><span class="sxs-lookup"><span data-stu-id="e64b3-113">Attributes</span></span>  
 <span data-ttu-id="e64b3-114">無。</span><span class="sxs-lookup"><span data-stu-id="e64b3-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e64b3-115">子元素</span><span class="sxs-lookup"><span data-stu-id="e64b3-115">Child Elements</span></span>  
  
|<span data-ttu-id="e64b3-116">屬性</span><span class="sxs-lookup"><span data-stu-id="e64b3-116">Attribute</span></span>|<span data-ttu-id="e64b3-117">說明</span><span class="sxs-lookup"><span data-stu-id="e64b3-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="e64b3-118">\<add></span><span class="sxs-lookup"><span data-stu-id="e64b3-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="e64b3-119">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="e64b3-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e64b3-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e64b3-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e64b3-121">項目</span><span class="sxs-lookup"><span data-stu-id="e64b3-121">Element</span></span>|<span data-ttu-id="e64b3-122">說明</span><span class="sxs-lookup"><span data-stu-id="e64b3-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e64b3-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="e64b3-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="e64b3-124">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e64b3-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e64b3-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e64b3-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
