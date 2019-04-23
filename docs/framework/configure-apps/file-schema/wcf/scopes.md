---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59213073"
---
# <a name="scopes"></a><span data-ttu-id="170cf-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="170cf-101">\<scopes></span></span>
<span data-ttu-id="170cf-102">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="170cf-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="170cf-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="170cf-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="170cf-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="170cf-104">\<behaviors></span></span>  
<span data-ttu-id="170cf-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="170cf-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="170cf-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="170cf-106">\<behavior></span></span>  
<span data-ttu-id="170cf-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="170cf-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="170cf-108">\<scopes></span><span class="sxs-lookup"><span data-stu-id="170cf-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="170cf-109">語法</span><span class="sxs-lookup"><span data-stu-id="170cf-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="170cf-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="170cf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="170cf-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="170cf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="170cf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="170cf-112">Attributes</span></span>  
 <span data-ttu-id="170cf-113">無。</span><span class="sxs-lookup"><span data-stu-id="170cf-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="170cf-114">子元素</span><span class="sxs-lookup"><span data-stu-id="170cf-114">Child Elements</span></span>  
  
|<span data-ttu-id="170cf-115">屬性</span><span class="sxs-lookup"><span data-stu-id="170cf-115">Attribute</span></span>|<span data-ttu-id="170cf-116">描述</span><span class="sxs-lookup"><span data-stu-id="170cf-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="170cf-117">\<add></span><span class="sxs-lookup"><span data-stu-id="170cf-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="170cf-118">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="170cf-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="170cf-119">父項目</span><span class="sxs-lookup"><span data-stu-id="170cf-119">Parent Elements</span></span>  
  
|<span data-ttu-id="170cf-120">項目</span><span class="sxs-lookup"><span data-stu-id="170cf-120">Element</span></span>|<span data-ttu-id="170cf-121">描述</span><span class="sxs-lookup"><span data-stu-id="170cf-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="170cf-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="170cf-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="170cf-123">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="170cf-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="170cf-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="170cf-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
