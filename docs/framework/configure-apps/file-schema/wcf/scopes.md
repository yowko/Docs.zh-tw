---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 8bc720238ca3039106345783381cd26134fc46b5
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61670621"
---
# <a name="scopes"></a><span data-ttu-id="9b571-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="9b571-101">\<scopes></span></span>
<span data-ttu-id="9b571-102">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="9b571-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="9b571-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="9b571-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="9b571-104">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="9b571-104">\<behaviors></span></span>  
<span data-ttu-id="9b571-105">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="9b571-105">\<endpointBehaviors></span></span>  
<span data-ttu-id="9b571-106">\<behavior></span><span class="sxs-lookup"><span data-stu-id="9b571-106">\<behavior></span></span>  
<span data-ttu-id="9b571-107">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="9b571-107">\<endpointDiscovery></span></span>  
<span data-ttu-id="9b571-108">\<scopes></span><span class="sxs-lookup"><span data-stu-id="9b571-108">\<scopes></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9b571-109">語法</span><span class="sxs-lookup"><span data-stu-id="9b571-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9b571-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9b571-110">Attributes and Elements</span></span>  
 <span data-ttu-id="9b571-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="9b571-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9b571-112">屬性</span><span class="sxs-lookup"><span data-stu-id="9b571-112">Attributes</span></span>  
 <span data-ttu-id="9b571-113">無。</span><span class="sxs-lookup"><span data-stu-id="9b571-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="9b571-114">子元素</span><span class="sxs-lookup"><span data-stu-id="9b571-114">Child Elements</span></span>  
  
|<span data-ttu-id="9b571-115">屬性</span><span class="sxs-lookup"><span data-stu-id="9b571-115">Attribute</span></span>|<span data-ttu-id="9b571-116">描述</span><span class="sxs-lookup"><span data-stu-id="9b571-116">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="9b571-117">\<add></span><span class="sxs-lookup"><span data-stu-id="9b571-117">\<add></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-scopes.md)|<span data-ttu-id="9b571-118">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="9b571-118">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="9b571-119">父項目</span><span class="sxs-lookup"><span data-stu-id="9b571-119">Parent Elements</span></span>  
  
|<span data-ttu-id="9b571-120">項目</span><span class="sxs-lookup"><span data-stu-id="9b571-120">Element</span></span>|<span data-ttu-id="9b571-121">描述</span><span class="sxs-lookup"><span data-stu-id="9b571-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9b571-122">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="9b571-122">\<endpointDiscovery></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/endpointdiscovery.md)|<span data-ttu-id="9b571-123">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="9b571-123">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="9b571-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="9b571-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
