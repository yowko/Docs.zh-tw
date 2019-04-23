---
title: <entries>
ms.date: 03/30/2017
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
ms.openlocfilehash: 5561cf61cef2258ec61bd32770538add1c69f5c1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59201789"
---
# <a name="entries"></a><span data-ttu-id="8cbe2-101">\<entries></span><span class="sxs-lookup"><span data-stu-id="8cbe2-101">\<entries></span></span>
<span data-ttu-id="8cbe2-102">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="8cbe2-102">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="8cbe2-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="8cbe2-103">\<system.serviceModel></span></span>  
<span data-ttu-id="8cbe2-104">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="8cbe2-104">\<routing></span></span>  
<span data-ttu-id="8cbe2-105">\<routingTables></span><span class="sxs-lookup"><span data-stu-id="8cbe2-105">\<routingTables></span></span>  
<span data-ttu-id="8cbe2-106">\<table></span><span class="sxs-lookup"><span data-stu-id="8cbe2-106">\<table></span></span>  
<span data-ttu-id="8cbe2-107">\<entries></span><span class="sxs-lookup"><span data-stu-id="8cbe2-107">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8cbe2-108">語法</span><span class="sxs-lookup"><span data-stu-id="8cbe2-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8cbe2-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8cbe2-109">Attributes and Elements</span></span>  
 <span data-ttu-id="8cbe2-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="8cbe2-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8cbe2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="8cbe2-111">Attributes</span></span>  
 <span data-ttu-id="8cbe2-112">無。</span><span class="sxs-lookup"><span data-stu-id="8cbe2-112">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8cbe2-113">子元素</span><span class="sxs-lookup"><span data-stu-id="8cbe2-113">Child Elements</span></span>  
  
|<span data-ttu-id="8cbe2-114">項目</span><span class="sxs-lookup"><span data-stu-id="8cbe2-114">Element</span></span>|<span data-ttu-id="8cbe2-115">描述</span><span class="sxs-lookup"><span data-stu-id="8cbe2-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cbe2-116">\<filters></span><span class="sxs-lookup"><span data-stu-id="8cbe2-116">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="8cbe2-117">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="8cbe2-117">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="8cbe2-118">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="8cbe2-118">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8cbe2-119">父項目</span><span class="sxs-lookup"><span data-stu-id="8cbe2-119">Parent Elements</span></span>  
  
|<span data-ttu-id="8cbe2-120">項目</span><span class="sxs-lookup"><span data-stu-id="8cbe2-120">Element</span></span>|<span data-ttu-id="8cbe2-121">描述</span><span class="sxs-lookup"><span data-stu-id="8cbe2-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="8cbe2-122">\<routing></span><span class="sxs-lookup"><span data-stu-id="8cbe2-122">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="8cbe2-123">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="8cbe2-123">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8cbe2-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8cbe2-124">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
- <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>
