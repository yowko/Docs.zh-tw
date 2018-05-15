---
title: '&lt;entries&gt; 的 &lt;add&gt;'
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: a6960c16c84c13d905f0993ee3cfc1cf67df07fc
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltaddgt-of-ltentriesgt"></a><span data-ttu-id="5c57f-102">&lt;entries&gt; 的 &lt;add&gt;</span><span class="sxs-lookup"><span data-stu-id="5c57f-102">&lt;add&gt; of &lt;entries&gt;</span></span>
<span data-ttu-id="5c57f-103">代表將篩選條件對應至先前定義之用戶端端點的路由項目。</span><span class="sxs-lookup"><span data-stu-id="5c57f-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="5c57f-104">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="5c57f-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="5c57f-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="5c57f-105">\<system.serviceModel></span></span>  
<span data-ttu-id="5c57f-106">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="5c57f-106">\<routing></span></span>  
<span data-ttu-id="5c57f-107">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="5c57f-107">\<routingTables></span></span>  
<span data-ttu-id="5c57f-108">\<資料表 ></span><span class="sxs-lookup"><span data-stu-id="5c57f-108">\<table></span></span>  
<span data-ttu-id="5c57f-109">\<項目 ></span><span class="sxs-lookup"><span data-stu-id="5c57f-109">\<entries></span></span>  
<span data-ttu-id="5c57f-110">\<add></span><span class="sxs-lookup"><span data-stu-id="5c57f-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="5c57f-111">語法</span><span class="sxs-lookup"><span data-stu-id="5c57f-111">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```  
  
```csharp  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="5c57f-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="5c57f-112">Attributes and Elements</span></span>  
 <span data-ttu-id="5c57f-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="5c57f-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="5c57f-114">屬性</span><span class="sxs-lookup"><span data-stu-id="5c57f-114">Attributes</span></span>  
  
|<span data-ttu-id="5c57f-115">屬性</span><span class="sxs-lookup"><span data-stu-id="5c57f-115">Attribute</span></span>|<span data-ttu-id="5c57f-116">描述</span><span class="sxs-lookup"><span data-stu-id="5c57f-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="5c57f-117">backupList</span><span class="sxs-lookup"><span data-stu-id="5c57f-117">backupList</span></span>|<span data-ttu-id="5c57f-118">字串，指定端點備份清單的參考。</span><span class="sxs-lookup"><span data-stu-id="5c57f-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="5c57f-119">endpoint</span><span class="sxs-lookup"><span data-stu-id="5c57f-119">endpoint</span></span>|<span data-ttu-id="5c57f-120">字串，指定對用戶端端點的參考，該端點會接收與 `filterName` 屬性指定之篩選條件相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="5c57f-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="5c57f-121">filterName</span><span class="sxs-lookup"><span data-stu-id="5c57f-121">filterName</span></span>|<span data-ttu-id="5c57f-122">字串，指定對篩選條件項目的參考。</span><span class="sxs-lookup"><span data-stu-id="5c57f-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="5c57f-123">priority</span><span class="sxs-lookup"><span data-stu-id="5c57f-123">priority</span></span>|<span data-ttu-id="5c57f-124">整數，指定這個項目的優先權。</span><span class="sxs-lookup"><span data-stu-id="5c57f-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="5c57f-125">路由表中的項目會根據優先權進行評估，其中 0 表示優先順序最低。</span><span class="sxs-lookup"><span data-stu-id="5c57f-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="5c57f-126">具有特定優先順序的所有項目會同時評估，如果找不到符合目前優先順序的項目，則會評估下一個優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="5c57f-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="5c57f-127">這是選擇性的值。</span><span class="sxs-lookup"><span data-stu-id="5c57f-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="5c57f-128">子項目</span><span class="sxs-lookup"><span data-stu-id="5c57f-128">Child Elements</span></span>  
 <span data-ttu-id="5c57f-129">無。</span><span class="sxs-lookup"><span data-stu-id="5c57f-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="5c57f-130">父項目</span><span class="sxs-lookup"><span data-stu-id="5c57f-130">Parent Elements</span></span>  
  
|<span data-ttu-id="5c57f-131">項目</span><span class="sxs-lookup"><span data-stu-id="5c57f-131">Element</span></span>|<span data-ttu-id="5c57f-132">描述</span><span class="sxs-lookup"><span data-stu-id="5c57f-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="5c57f-133">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="5c57f-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="5c57f-134">包含路由組態項目的組態區段。</span><span class="sxs-lookup"><span data-stu-id="5c57f-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="5c57f-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="5c57f-135">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>      
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType> 
