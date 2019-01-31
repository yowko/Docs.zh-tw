---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 9c4c7fa4f778642d549deebce6e7476f4da13a0d
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/30/2019
ms.locfileid: "55283682"
---
# <a name="entries"></a><span data-ttu-id="66dcb-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="66dcb-101">\<entries></span></span>
<span data-ttu-id="66dcb-102">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="66dcb-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="66dcb-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="66dcb-103">\<system.serviceModel></span></span>  
<span data-ttu-id="66dcb-104">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="66dcb-104">\<routing></span></span>  
<span data-ttu-id="66dcb-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="66dcb-105">\<routingTables></span></span>  
<span data-ttu-id="66dcb-106">\<table></span><span class="sxs-lookup"><span data-stu-id="66dcb-106">\<table></span></span>  
<span data-ttu-id="66dcb-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="66dcb-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="66dcb-108">語法</span><span class="sxs-lookup"><span data-stu-id="66dcb-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="66dcb-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="66dcb-109">Attributes and Elements</span></span>  
 <span data-ttu-id="66dcb-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="66dcb-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="66dcb-111">屬性</span><span class="sxs-lookup"><span data-stu-id="66dcb-111">Attributes</span></span>  
 <span data-ttu-id="66dcb-112">無。</span><span class="sxs-lookup"><span data-stu-id="66dcb-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="66dcb-113">子元素</span><span class="sxs-lookup"><span data-stu-id="66dcb-113">Child Elements</span></span>  
  
|<span data-ttu-id="66dcb-114">項目</span><span class="sxs-lookup"><span data-stu-id="66dcb-114">Element</span></span>|<span data-ttu-id="66dcb-115">描述</span><span class="sxs-lookup"><span data-stu-id="66dcb-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66dcb-116">\<filters></span><span class="sxs-lookup"><span data-stu-id="66dcb-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="66dcb-117">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="66dcb-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="66dcb-118">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="66dcb-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="66dcb-119">父項目</span><span class="sxs-lookup"><span data-stu-id="66dcb-119">Parent Elements</span></span>  
  
|<span data-ttu-id="66dcb-120">項目</span><span class="sxs-lookup"><span data-stu-id="66dcb-120">Element</span></span>|<span data-ttu-id="66dcb-121">描述</span><span class="sxs-lookup"><span data-stu-id="66dcb-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="66dcb-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="66dcb-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="66dcb-123">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="66dcb-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="66dcb-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="66dcb-124">See also</span></span>
- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
