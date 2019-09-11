---
title: <filterTable>
ms.date: 03/30/2017
ms.assetid: e9f05441-3ad1-49b9-a267-71724aa094b4
ms.openlocfilehash: 918a365004efea82f4ef4c8868f6821d4bb6da18
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855186"
---
# <a name="filtertable"></a><span data-ttu-id="e2720-101">\<filterTable></span><span class="sxs-lookup"><span data-stu-id="e2720-101">\<filterTable></span></span>
<span data-ttu-id="e2720-102">表示路由表，其中包含用來評估訊息的篩選器清單，以及當篩選準則評估為 true 時，要將訊息路由傳送至其中的用戶端端點。</span><span class="sxs-lookup"><span data-stu-id="e2720-102">Represents a routing table that contains a list of filters to evaluate messages against and the client endpoint to route messages to if the filter evaluates to true.</span></span>  
  
<span data-ttu-id="e2720-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="e2720-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="e2720-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="e2720-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="e2720-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<路由 >** ](routing.md)</span><span class="sxs-lookup"><span data-stu-id="e2720-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<routing>**](routing.md)</span></span>\
<span data-ttu-id="e2720-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<filterTables >** ](filtertables.md)</span><span class="sxs-lookup"><span data-stu-id="e2720-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<filterTables>**](filtertables.md)</span></span>\
<span data-ttu-id="e2720-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<filterTable >**</span><span class="sxs-lookup"><span data-stu-id="e2720-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<filterTable>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e2720-108">語法</span><span class="sxs-lookup"><span data-stu-id="e2720-108">Syntax</span></span>  
  
```xml  
<routing>
  <filterTables>
     name="String">
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e2720-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e2720-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e2720-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e2720-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e2720-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e2720-111">Attributes</span></span>  
  
|<span data-ttu-id="e2720-112">項目</span><span class="sxs-lookup"><span data-stu-id="e2720-112">Element</span></span>|<span data-ttu-id="e2720-113">描述</span><span class="sxs-lookup"><span data-stu-id="e2720-113">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="e2720-114">NAME</span><span class="sxs-lookup"><span data-stu-id="e2720-114">name</span></span>|<span data-ttu-id="e2720-115">字串，包含這個組態項目的唯一名稱。</span><span class="sxs-lookup"><span data-stu-id="e2720-115">A string that contains the unique name of this configuration element.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e2720-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e2720-116">Child Elements</span></span>  
  
|<span data-ttu-id="e2720-117">項目</span><span class="sxs-lookup"><span data-stu-id="e2720-117">Element</span></span>|<span data-ttu-id="e2720-118">描述</span><span class="sxs-lookup"><span data-stu-id="e2720-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2720-119">\<filters></span><span class="sxs-lookup"><span data-stu-id="e2720-119">\<filters></span></span>](filters-of-routing.md)|<span data-ttu-id="e2720-120">當篩選條件相符時，路由篩選器與訊息傳送目標端點之間的對應。</span><span class="sxs-lookup"><span data-stu-id="e2720-120">Mappings between the routing filters and the target endpoints to send messages to when the filter matches.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e2720-121">父項目</span><span class="sxs-lookup"><span data-stu-id="e2720-121">Parent Elements</span></span>  
  
|<span data-ttu-id="e2720-122">項目</span><span class="sxs-lookup"><span data-stu-id="e2720-122">Element</span></span>|<span data-ttu-id="e2720-123">描述</span><span class="sxs-lookup"><span data-stu-id="e2720-123">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e2720-124">\<routing></span><span class="sxs-lookup"><span data-stu-id="e2720-124">\<routing></span></span>](routing.md)|<span data-ttu-id="e2720-125">包含路由表的組態區段。</span><span class="sxs-lookup"><span data-stu-id="e2720-125">A configuration section that contains routing tables.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e2720-126">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e2720-126">See also</span></span>

- <xref:System.ServiceModel.Routing.Configuration.RoutingSection?displayProperty=nameWithType>
