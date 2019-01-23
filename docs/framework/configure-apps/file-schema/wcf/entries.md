---
title: '&lt;entries&gt;'
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 33f98cb4b138307622a14463ce5a3008058b6e31
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54587056"
---
# <a name="ltentriesgt"></a><span data-ttu-id="e97a7-102">&lt;entries&gt;</span><span class="sxs-lookup"><span data-stu-id="e97a7-102">&lt;entries&gt;</span></span>
<span data-ttu-id="e97a7-103">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="e97a7-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="e97a7-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e97a7-104">\<system.serviceModel></span></span>  
<span data-ttu-id="e97a7-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="e97a7-105">\<routing></span></span>  
<span data-ttu-id="e97a7-106">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="e97a7-106">\<routingTables></span></span>  
<span data-ttu-id="e97a7-107">\<table></span><span class="sxs-lookup"><span data-stu-id="e97a7-107">\<table></span></span>  
<span data-ttu-id="e97a7-108">\<entries></span><span class="sxs-lookup"><span data-stu-id="e97a7-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e97a7-109">語法</span><span class="sxs-lookup"><span data-stu-id="e97a7-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e97a7-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e97a7-110">Attributes and Elements</span></span>  
 <span data-ttu-id="e97a7-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e97a7-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e97a7-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e97a7-112">Attributes</span></span>  
 <span data-ttu-id="e97a7-113">無。</span><span class="sxs-lookup"><span data-stu-id="e97a7-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="e97a7-114">子元素</span><span class="sxs-lookup"><span data-stu-id="e97a7-114">Child Elements</span></span>  
  
|<span data-ttu-id="e97a7-115">項目</span><span class="sxs-lookup"><span data-stu-id="e97a7-115">Element</span></span>|<span data-ttu-id="e97a7-116">描述</span><span class="sxs-lookup"><span data-stu-id="e97a7-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e97a7-117">\<filters></span><span class="sxs-lookup"><span data-stu-id="e97a7-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="e97a7-118">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="e97a7-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="e97a7-119">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="e97a7-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e97a7-120">父項目</span><span class="sxs-lookup"><span data-stu-id="e97a7-120">Parent Elements</span></span>  
  
|<span data-ttu-id="e97a7-121">項目</span><span class="sxs-lookup"><span data-stu-id="e97a7-121">Element</span></span>|<span data-ttu-id="e97a7-122">描述</span><span class="sxs-lookup"><span data-stu-id="e97a7-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e97a7-123">\<routing></span><span class="sxs-lookup"><span data-stu-id="e97a7-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="e97a7-124">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="e97a7-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e97a7-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e97a7-125">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
