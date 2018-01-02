---
title: "&lt;scopes&gt; 的 &lt;add&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 012d86297f75874b57231d7c347c7412ad04aa1f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-of-ltscopesgt"></a><span data-ttu-id="0371b-102">&lt;scopes&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="0371b-102">&lt;add&gt; of &lt;scopes&gt;</span></span>
<span data-ttu-id="0371b-103">加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。</span><span class="sxs-lookup"><span data-stu-id="0371b-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="0371b-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="0371b-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="0371b-105">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0371b-105">\<behaviors></span></span>  
<span data-ttu-id="0371b-106">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="0371b-106">\<endpointBehaviors></span></span>  
<span data-ttu-id="0371b-107">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="0371b-107">\<behavior></span></span>  
<span data-ttu-id="0371b-108">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="0371b-108">\<endpointDiscovery></span></span>  
<span data-ttu-id="0371b-109">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="0371b-109">\<scopes></span></span>  
<span data-ttu-id="0371b-110">\<add></span><span class="sxs-lookup"><span data-stu-id="0371b-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0371b-111">語法</span><span class="sxs-lookup"><span data-stu-id="0371b-111">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI"/>
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0371b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0371b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="0371b-113">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0371b-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0371b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="0371b-114">Attributes</span></span>  
  
|<span data-ttu-id="0371b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="0371b-115">Attribute</span></span>|<span data-ttu-id="0371b-116">描述</span><span class="sxs-lookup"><span data-stu-id="0371b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0371b-117">範圍</span><span class="sxs-lookup"><span data-stu-id="0371b-117">scope</span></span>|<span data-ttu-id="0371b-118">URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="0371b-118">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0371b-119">子元素</span><span class="sxs-lookup"><span data-stu-id="0371b-119">Child Elements</span></span>  
 <span data-ttu-id="0371b-120">無。</span><span class="sxs-lookup"><span data-stu-id="0371b-120">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="0371b-121">父項目</span><span class="sxs-lookup"><span data-stu-id="0371b-121">Parent Elements</span></span>  
  
|<span data-ttu-id="0371b-122">項目</span><span class="sxs-lookup"><span data-stu-id="0371b-122">Element</span></span>|<span data-ttu-id="0371b-123">描述</span><span class="sxs-lookup"><span data-stu-id="0371b-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0371b-124">\<範圍 ></span><span class="sxs-lookup"><span data-stu-id="0371b-124">\<scopes></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/scopes.md)|<span data-ttu-id="0371b-125">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="0371b-125">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0371b-126">請參閱</span><span class="sxs-lookup"><span data-stu-id="0371b-126">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
