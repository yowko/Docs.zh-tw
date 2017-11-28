---
title: '&lt;filterTables&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 41f1ac35-f559-473a-b2c3-8cc83a6a3831
caps.latest.revision: "5"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 75e06b0258f2e4f65d441c25b5081cf7a6627518
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="ltfiltertablesgt"></a><span data-ttu-id="0c9cf-102">&lt;filterTables&gt;</span><span class="sxs-lookup"><span data-stu-id="0c9cf-102">&lt;filterTables&gt;</span></span>
<span data-ttu-id="0c9cf-103">代表定義路由表的組態區段，該路由表包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="0c9cf-103">Represents a configuration section for defining routing tables that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>  
  
 <span data-ttu-id="0c9cf-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0c9cf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0c9cf-105">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="0c9cf-105">\<routing></span></span>  
<span data-ttu-id="0c9cf-106">\<routingTables ></span><span class="sxs-lookup"><span data-stu-id="0c9cf-106">\<routingTables></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0c9cf-107">語法</span><span class="sxs-lookup"><span data-stu-id="0c9cf-107">Syntax</span></span>  
  
```xml
   <routing>      <filterTables>        <filterTable name="String">          <entries>            <add backupList="String"                 endpointName="String"                  filterName="String"                  priority="Integer" />          </entries>        </table>      </routingTables></routing>  
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0c9cf-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0c9cf-108">Attributes and Elements</span></span>  
 <span data-ttu-id="0c9cf-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0c9cf-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0c9cf-110">屬性</span><span class="sxs-lookup"><span data-stu-id="0c9cf-110">Attributes</span></span>  
 <span data-ttu-id="0c9cf-111">無。</span><span class="sxs-lookup"><span data-stu-id="0c9cf-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0c9cf-112">子項目</span><span class="sxs-lookup"><span data-stu-id="0c9cf-112">Child Elements</span></span>  
  
|<span data-ttu-id="0c9cf-113">項目</span><span class="sxs-lookup"><span data-stu-id="0c9cf-113">Element</span></span>|<span data-ttu-id="0c9cf-114">說明</span><span class="sxs-lookup"><span data-stu-id="0c9cf-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c9cf-115">\<篩選條件 ></span><span class="sxs-lookup"><span data-stu-id="0c9cf-115">\<filters></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/filters-of-routing.md)|<span data-ttu-id="0c9cf-116">路由表，其中包含當篩選條件符合時，路由篩選條件與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="0c9cf-116">A routing table that contain mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0c9cf-117">父項目</span><span class="sxs-lookup"><span data-stu-id="0c9cf-117">Parent Elements</span></span>  
  
|<span data-ttu-id="0c9cf-118">項目</span><span class="sxs-lookup"><span data-stu-id="0c9cf-118">Element</span></span>|<span data-ttu-id="0c9cf-119">說明</span><span class="sxs-lookup"><span data-stu-id="0c9cf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0c9cf-120">\<路由 ></span><span class="sxs-lookup"><span data-stu-id="0c9cf-120">\<routing></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/routing.md)|<span data-ttu-id="0c9cf-121">組態區段，其中包含路由篩選條件與路由表。</span><span class="sxs-lookup"><span data-stu-id="0c9cf-121">A configuration section that contains routing filters and routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0c9cf-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0c9cf-122">See Also</span></span>  
 <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>       
 <xref:System.ServiceModel.Routing.Configuration.FilterTableCollection?displayProperty=nameWithType>    
