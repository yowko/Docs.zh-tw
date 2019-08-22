---
title: <add> 的 <entries>
ms.date: 03/30/2017
ms.assetid: 3af4805b-dc72-4f68-b168-da4fba8c6170
ms.openlocfilehash: 3052a7570d1d93836603454817be921b37d26060
ms.sourcegitcommit: cdf67135a98a5a51913dacddb58e004a3c867802
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/21/2019
ms.locfileid: "69658830"
---
# <a name="add-of-entries"></a><span data-ttu-id="01030-102">\<新增專案的\<> ></span><span class="sxs-lookup"><span data-stu-id="01030-102">\<add> of \<entries></span></span>
<span data-ttu-id="01030-103">代表將篩選條件對應至先前定義之用戶端端點的路由項目。</span><span class="sxs-lookup"><span data-stu-id="01030-103">Represents a routing entry that maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="01030-104">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="01030-104">Messages matching this filter will be sent to this destination.</span></span>  
  
 <span data-ttu-id="01030-105">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="01030-105">\<system.serviceModel></span></span>  
<span data-ttu-id="01030-106">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="01030-106">\<routing></span></span>  
<span data-ttu-id="01030-107">\<filterTables></span><span class="sxs-lookup"><span data-stu-id="01030-107">\<filterTables></span></span>  
<span data-ttu-id="01030-108">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="01030-108">\<filterTable></span></span>  
<span data-ttu-id="01030-109">\<專案 ></span><span class="sxs-lookup"><span data-stu-id="01030-109">\<entries></span></span>  
<span data-ttu-id="01030-110">\<add></span><span class="sxs-lookup"><span data-stu-id="01030-110">\<add></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01030-111">語法</span><span class="sxs-lookup"><span data-stu-id="01030-111">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="01030-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01030-112">Attributes and Elements</span></span>  
 <span data-ttu-id="01030-113">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="01030-113">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01030-114">屬性</span><span class="sxs-lookup"><span data-stu-id="01030-114">Attributes</span></span>  
  
|<span data-ttu-id="01030-115">屬性</span><span class="sxs-lookup"><span data-stu-id="01030-115">Attribute</span></span>|<span data-ttu-id="01030-116">說明</span><span class="sxs-lookup"><span data-stu-id="01030-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="01030-117">backupList</span><span class="sxs-lookup"><span data-stu-id="01030-117">backupList</span></span>|<span data-ttu-id="01030-118">字串，指定端點備份清單的參考。</span><span class="sxs-lookup"><span data-stu-id="01030-118">A string that specifies a reference to a backup list of endpoints.</span></span>|  
|<span data-ttu-id="01030-119">端點</span><span class="sxs-lookup"><span data-stu-id="01030-119">endpoint</span></span>|<span data-ttu-id="01030-120">字串，指定對用戶端端點的參考，該端點會接收與 `filterName` 屬性指定之篩選條件相符的訊息。</span><span class="sxs-lookup"><span data-stu-id="01030-120">A string that specifies a reference to a client endpoint that will receive messages that match the filter specified by the `filterName` attribute.</span></span>|  
|<span data-ttu-id="01030-121">filterName</span><span class="sxs-lookup"><span data-stu-id="01030-121">filterName</span></span>|<span data-ttu-id="01030-122">字串，指定對篩選條件項目的參考。</span><span class="sxs-lookup"><span data-stu-id="01030-122">A string that specifies a reference to a filter element.</span></span>|  
|<span data-ttu-id="01030-123">priority</span><span class="sxs-lookup"><span data-stu-id="01030-123">priority</span></span>|<span data-ttu-id="01030-124">整數，指定這個項目的優先權。</span><span class="sxs-lookup"><span data-stu-id="01030-124">An integer that specifies the priority of this entry.</span></span><br /><br /> <span data-ttu-id="01030-125">路由表中的項目會根據優先權進行評估，其中 0 表示優先順序最低。</span><span class="sxs-lookup"><span data-stu-id="01030-125">Entries in the routing table will be evaluated based on priority, with 0 being the lowest priority.</span></span> <span data-ttu-id="01030-126">具有特定優先順序的所有項目會同時評估，如果找不到符合目前優先順序的項目，則會評估下一個優先順序層級。</span><span class="sxs-lookup"><span data-stu-id="01030-126">All entries for a specific priority are evaluated simultaneously, if no matching entry is found for the current priority, the next priority level will be evaluated.</span></span><br /><br /> <span data-ttu-id="01030-127">這是選擇性的值。</span><span class="sxs-lookup"><span data-stu-id="01030-127">This value is optional.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="01030-128">子元素</span><span class="sxs-lookup"><span data-stu-id="01030-128">Child Elements</span></span>  
 <span data-ttu-id="01030-129">無。</span><span class="sxs-lookup"><span data-stu-id="01030-129">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="01030-130">父項目</span><span class="sxs-lookup"><span data-stu-id="01030-130">Parent Elements</span></span>  
  
|<span data-ttu-id="01030-131">項目</span><span class="sxs-lookup"><span data-stu-id="01030-131">Element</span></span>|<span data-ttu-id="01030-132">描述</span><span class="sxs-lookup"><span data-stu-id="01030-132">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01030-133">\<routing></span><span class="sxs-lookup"><span data-stu-id="01030-133">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="01030-134">包含路由組態項目的組態區段。</span><span class="sxs-lookup"><span data-stu-id="01030-134">A configuration section that contains routing mapping entries.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01030-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01030-135">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
