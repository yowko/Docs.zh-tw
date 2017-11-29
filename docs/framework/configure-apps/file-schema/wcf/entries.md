---
title: "&lt;項目&gt;"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 202e430c-c1b9-4343-abe2-ac78c181a3b7
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 9b6d8d1c3797d60b26443e07cc527ea8b86f526e
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltentriesgt"></a><span data-ttu-id="01aa4-102">&lt;項目&gt;</span><span class="sxs-lookup"><span data-stu-id="01aa4-102">&lt;entries&gt;</span></span>
<span data-ttu-id="01aa4-103">這個路由項目會包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="01aa4-103">A routing entry that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="01aa4-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="01aa4-104">\<system.serviceModel></span></span>  
<span data-ttu-id="01aa4-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="01aa4-105">\<routing></span></span>  
<span data-ttu-id="01aa4-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="01aa4-106">\<routingTables></span></span>  
<span data-ttu-id="01aa4-107">\<資料表 ></span><span class="sxs-lookup"><span data-stu-id="01aa4-107">\<table></span></span>  
<span data-ttu-id="01aa4-108">\<項目 ></span><span class="sxs-lookup"><span data-stu-id="01aa4-108">\<entries></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="01aa4-109">語法</span><span class="sxs-lookup"><span data-stu-id="01aa4-109">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="01aa4-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="01aa4-110">Attributes and Elements</span></span>  
 <span data-ttu-id="01aa4-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="01aa4-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="01aa4-112">屬性</span><span class="sxs-lookup"><span data-stu-id="01aa4-112">Attributes</span></span>  
 <span data-ttu-id="01aa4-113">無。</span><span class="sxs-lookup"><span data-stu-id="01aa4-113">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="01aa4-114">子項目</span><span class="sxs-lookup"><span data-stu-id="01aa4-114">Child Elements</span></span>  
  
|<span data-ttu-id="01aa4-115">項目</span><span class="sxs-lookup"><span data-stu-id="01aa4-115">Element</span></span>|<span data-ttu-id="01aa4-116">說明</span><span class="sxs-lookup"><span data-stu-id="01aa4-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01aa4-117">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="01aa4-117">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="01aa4-118">將篩選條件對應至先前定義的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="01aa4-118">Maps a filter to a client endpoint that was previously defined.</span></span> <span data-ttu-id="01aa4-119">將符合此篩選條件的訊息傳送至這個目的地。</span><span class="sxs-lookup"><span data-stu-id="01aa4-119">Messages matching this filter will be sent to this destination.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="01aa4-120">父項目</span><span class="sxs-lookup"><span data-stu-id="01aa4-120">Parent Elements</span></span>  
  
|<span data-ttu-id="01aa4-121">項目</span><span class="sxs-lookup"><span data-stu-id="01aa4-121">Element</span></span>|<span data-ttu-id="01aa4-122">說明</span><span class="sxs-lookup"><span data-stu-id="01aa4-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="01aa4-123">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="01aa4-123">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="01aa4-124">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="01aa4-124">A configuration section that contains a routing table.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="01aa4-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="01aa4-125">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableEntryElement?displayProperty=nameWithType>    
