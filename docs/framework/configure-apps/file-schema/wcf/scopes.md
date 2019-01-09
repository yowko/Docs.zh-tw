---
title: '&lt;範圍&gt;'
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 7afab700c2d9eb91ffe57bfefaf5864782a0af5f
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145324"
---
# <a name="ltscopesgt"></a><span data-ttu-id="c1407-102">&lt;範圍&gt;</span><span class="sxs-lookup"><span data-stu-id="c1407-102">&lt;scopes&gt;</span></span>
<span data-ttu-id="c1407-103">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="c1407-103">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="c1407-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="c1407-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="c1407-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c1407-105">\<behaviors></span></span>  
<span data-ttu-id="c1407-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="c1407-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="c1407-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="c1407-107">\<behavior></span></span>  
<span data-ttu-id="c1407-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c1407-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="c1407-109">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="c1407-109">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c1407-110">語法</span><span class="sxs-lookup"><span data-stu-id="c1407-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c1407-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c1407-111">Attributes and Elements</span></span>  
 <span data-ttu-id="c1407-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c1407-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c1407-113">屬性</span><span class="sxs-lookup"><span data-stu-id="c1407-113">Attributes</span></span>  
 <span data-ttu-id="c1407-114">無。</span><span class="sxs-lookup"><span data-stu-id="c1407-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c1407-115">子元素</span><span class="sxs-lookup"><span data-stu-id="c1407-115">Child Elements</span></span>  
  
|<span data-ttu-id="c1407-116">屬性</span><span class="sxs-lookup"><span data-stu-id="c1407-116">Attribute</span></span>|<span data-ttu-id="c1407-117">描述</span><span class="sxs-lookup"><span data-stu-id="c1407-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="c1407-118">\<add></span><span class="sxs-lookup"><span data-stu-id="c1407-118">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="c1407-119">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="c1407-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c1407-120">父項目</span><span class="sxs-lookup"><span data-stu-id="c1407-120">Parent Elements</span></span>  
  
|<span data-ttu-id="c1407-121">項目</span><span class="sxs-lookup"><span data-stu-id="c1407-121">Element</span></span>|<span data-ttu-id="c1407-122">描述</span><span class="sxs-lookup"><span data-stu-id="c1407-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c1407-123">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="c1407-123">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="c1407-124">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="c1407-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c1407-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c1407-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
