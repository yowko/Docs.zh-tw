---
title: '&lt;filterTable&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 96425604fab8f70456ea1e0d97efb2c3bf843224
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltfiltertablegt"></a><span data-ttu-id="90d67-102">&lt;filterTable&gt;</span><span class="sxs-lookup"><span data-stu-id="90d67-102">&lt;filterTable&gt;</span></span>
<span data-ttu-id="90d67-103">表示路由表，包含要評估訊息及將訊息路由至用戶端端點，如果在篩選條件評估為 true 的篩選器清單。</span><span class="sxs-lookup"><span data-stu-id="90d67-103">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
 <span data-ttu-id="90d67-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="90d67-104">\<system.serviceModel></span></span>  
<span data-ttu-id="90d67-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="90d67-105">\<routing></span></span>  
<span data-ttu-id="90d67-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="90d67-106">\<routingTables></span></span>  
<span data-ttu-id="90d67-107">\<資料表 ></span><span class="sxs-lookup"><span data-stu-id="90d67-107">\<table></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="90d67-108">語法</span><span class="sxs-lookup"><span data-stu-id="90d67-108">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="90d67-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="90d67-109">Attributes and Elements</span></span>  
 <span data-ttu-id="90d67-110">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="90d67-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="90d67-111">屬性</span><span class="sxs-lookup"><span data-stu-id="90d67-111">Attributes</span></span>  
  
|<span data-ttu-id="90d67-112">項目</span><span class="sxs-lookup"><span data-stu-id="90d67-112">Element</span></span>|<span data-ttu-id="90d67-113">描述</span><span class="sxs-lookup"><span data-stu-id="90d67-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="90d67-114">name</span><span class="sxs-lookup"><span data-stu-id="90d67-114">name</span></span>|<span data-ttu-id="90d67-115">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="90d67-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="90d67-116">子元素</span><span class="sxs-lookup"><span data-stu-id="90d67-116">Child Elements</span></span>  
  
|<span data-ttu-id="90d67-117">項目</span><span class="sxs-lookup"><span data-stu-id="90d67-117">Element</span></span>|<span data-ttu-id="90d67-118">說明</span><span class="sxs-lookup"><span data-stu-id="90d67-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90d67-119">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="90d67-119">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="90d67-120">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="90d67-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="90d67-121">父項目</span><span class="sxs-lookup"><span data-stu-id="90d67-121">Parent Elements</span></span>  
  
|<span data-ttu-id="90d67-122">項目</span><span class="sxs-lookup"><span data-stu-id="90d67-122">Element</span></span>|<span data-ttu-id="90d67-123">說明</span><span class="sxs-lookup"><span data-stu-id="90d67-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="90d67-124">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="90d67-124">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="90d67-125">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="90d67-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="90d67-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="90d67-126">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>    
