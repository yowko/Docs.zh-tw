---
title: <add> 的 <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: c29e47f688118e34fbdb4deb396c930d478f0582
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673598"
---
# <a name="add-of-scopes"></a><span data-ttu-id="815bb-102">\<add> of \<scopes></span><span class="sxs-lookup"><span data-stu-id="815bb-102">\<add> of \<scopes></span></span>
<span data-ttu-id="815bb-103">加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。</span><span class="sxs-lookup"><span data-stu-id="815bb-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="815bb-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="815bb-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="815bb-105">\<behaviors></span><span class="sxs-lookup"><span data-stu-id="815bb-105">\<behaviors></span></span>  
<span data-ttu-id="815bb-106">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="815bb-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="815bb-107">\<behavior></span><span class="sxs-lookup"><span data-stu-id="815bb-107">\<behavior></span></span>  
<span data-ttu-id="815bb-108">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="815bb-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="815bb-109">\<scopes></span><span class="sxs-lookup"><span data-stu-id="815bb-109">\<scopes></span></span>  
<span data-ttu-id="815bb-110">\<add></span><span class="sxs-lookup"><span data-stu-id="815bb-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="815bb-111">語法</span><span class="sxs-lookup"><span data-stu-id="815bb-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="815bb-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="815bb-112">Attributes and Elements</span></span>  
 <span data-ttu-id="815bb-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="815bb-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="815bb-114">屬性</span><span class="sxs-lookup"><span data-stu-id="815bb-114">Attributes</span></span>  
  
|<span data-ttu-id="815bb-115">屬性</span><span class="sxs-lookup"><span data-stu-id="815bb-115">Attribute</span></span>|<span data-ttu-id="815bb-116">描述</span><span class="sxs-lookup"><span data-stu-id="815bb-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="815bb-117">範圍</span><span class="sxs-lookup"><span data-stu-id="815bb-117">scope</span></span>|<span data-ttu-id="815bb-118">URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="815bb-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="815bb-119">子元素</span><span class="sxs-lookup"><span data-stu-id="815bb-119">Child Elements</span></span>  
 <span data-ttu-id="815bb-120">無。</span><span class="sxs-lookup"><span data-stu-id="815bb-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="815bb-121">父項目</span><span class="sxs-lookup"><span data-stu-id="815bb-121">Parent Elements</span></span>  
  
|<span data-ttu-id="815bb-122">項目</span><span class="sxs-lookup"><span data-stu-id="815bb-122">Element</span></span>|<span data-ttu-id="815bb-123">描述</span><span class="sxs-lookup"><span data-stu-id="815bb-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="815bb-124">\<scopes></span><span class="sxs-lookup"><span data-stu-id="815bb-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="815bb-125">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="815bb-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="815bb-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="815bb-126">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
