---
title: '&lt;項目&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 8c442990ee736c17b71b625e06d961230a8ceed2
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54146429"
---
# <a name="ltentriesgt"></a><span data-ttu-id="84e21-102">&lt;項目&gt;</span><span class="sxs-lookup"><span data-stu-id="84e21-102">&lt;entries&gt;</span></span>
<span data-ttu-id="84e21-103">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="84e21-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="84e21-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="84e21-104">\<system.serviceModel></span></span>  
<span data-ttu-id="84e21-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="84e21-105">\<routing></span></span>  
<span data-ttu-id="84e21-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="84e21-106">\<routingTables></span></span>  
<span data-ttu-id="84e21-107">\<資料表 ></span><span class="sxs-lookup"><span data-stu-id="84e21-107">\<table></span></span>  
<span data-ttu-id="84e21-108">\<項目 ></span><span class="sxs-lookup"><span data-stu-id="84e21-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="84e21-109">語法</span><span class="sxs-lookup"><span data-stu-id="84e21-109">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
    <filterTable name="String">
      <entries>
        <add backupList="String"
             endpointName="String"
             filterName="String"
             priority="Integer" />
      </entries>
    </filterTable>
  </filterTables>
</routing>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="84e21-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="84e21-110">Attributes and Elements</span></span>  
 <span data-ttu-id="84e21-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="84e21-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="84e21-112">屬性</span><span class="sxs-lookup"><span data-stu-id="84e21-112">Attributes</span></span>  
 <span data-ttu-id="84e21-113">無。</span><span class="sxs-lookup"><span data-stu-id="84e21-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="84e21-114">子元素</span><span class="sxs-lookup"><span data-stu-id="84e21-114">Child Elements</span></span>  
  
|<span data-ttu-id="84e21-115">項目</span><span class="sxs-lookup"><span data-stu-id="84e21-115">Element</span></span>|<span data-ttu-id="84e21-116">描述</span><span class="sxs-lookup"><span data-stu-id="84e21-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84e21-117">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="84e21-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="84e21-118">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="84e21-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="84e21-119">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="84e21-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="84e21-120">父項目</span><span class="sxs-lookup"><span data-stu-id="84e21-120">Parent Elements</span></span>  
  
|<span data-ttu-id="84e21-121">項目</span><span class="sxs-lookup"><span data-stu-id="84e21-121">Element</span></span>|<span data-ttu-id="84e21-122">描述</span><span class="sxs-lookup"><span data-stu-id="84e21-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="84e21-123">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="84e21-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="84e21-124">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="84e21-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="84e21-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="84e21-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
