---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: dd6513930798e9e1ab263f75c9350511c2dcdcd5
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69935176"
---
# <a name="scopes"></a><span data-ttu-id="7b90c-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="7b90c-101">\<scopes></span></span>
<span data-ttu-id="7b90c-102">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="7b90c-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="7b90c-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="7b90c-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="7b90c-104">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7b90c-104">\<behaviors></span></span>  
<span data-ttu-id="7b90c-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="7b90c-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="7b90c-106">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="7b90c-106">\<behavior></span></span>  
<span data-ttu-id="7b90c-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="7b90c-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="7b90c-108">\<scopes></span><span class="sxs-lookup"><span data-stu-id="7b90c-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7b90c-109">語法</span><span class="sxs-lookup"><span data-stu-id="7b90c-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="7b90c-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="7b90c-110">Attributes and Elements</span></span>  
 <span data-ttu-id="7b90c-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="7b90c-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="7b90c-112">屬性</span><span class="sxs-lookup"><span data-stu-id="7b90c-112">Attributes</span></span>  
 <span data-ttu-id="7b90c-113">無。</span><span class="sxs-lookup"><span data-stu-id="7b90c-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="7b90c-114">子元素</span><span class="sxs-lookup"><span data-stu-id="7b90c-114">Child Elements</span></span>  
  
|<span data-ttu-id="7b90c-115">屬性</span><span class="sxs-lookup"><span data-stu-id="7b90c-115">Attribute</span></span>|<span data-ttu-id="7b90c-116">說明</span><span class="sxs-lookup"><span data-stu-id="7b90c-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="7b90c-117">\<add></span><span class="sxs-lookup"><span data-stu-id="7b90c-117">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="7b90c-118">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="7b90c-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="7b90c-119">父項目</span><span class="sxs-lookup"><span data-stu-id="7b90c-119">Parent Elements</span></span>  
  
|<span data-ttu-id="7b90c-120">項目</span><span class="sxs-lookup"><span data-stu-id="7b90c-120">Element</span></span>|<span data-ttu-id="7b90c-121">描述</span><span class="sxs-lookup"><span data-stu-id="7b90c-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="7b90c-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="7b90c-122">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="7b90c-123">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="7b90c-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="7b90c-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="7b90c-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
