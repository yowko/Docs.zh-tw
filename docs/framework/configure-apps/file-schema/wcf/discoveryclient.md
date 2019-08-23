---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: f9d7e3a4957d2a8f30724f0bfc04e58a57fc5f7d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919256"
---
# <a name="discoveryclient"></a><span data-ttu-id="588e8-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="588e8-101">\<discoveryClient></span></span>
<span data-ttu-id="588e8-102">組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="588e8-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="588e8-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="588e8-103">\<system.serviceModel></span></span>  
<span data-ttu-id="588e8-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="588e8-104">\<bindings></span></span>  
<span data-ttu-id="588e8-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="588e8-105">\<customBinding></span></span>  
<span data-ttu-id="588e8-106">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="588e8-106">\<binding></span></span>  
<span data-ttu-id="588e8-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="588e8-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="588e8-108">語法</span><span class="sxs-lookup"><span data-stu-id="588e8-108">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String">
  <findCriteria duration="TimeSpan"
                maxResults="Integer"
                scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String"
           namespace="String" />
    </contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="588e8-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="588e8-109">Attributes and Elements</span></span>  
 <span data-ttu-id="588e8-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="588e8-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="588e8-111">屬性</span><span class="sxs-lookup"><span data-stu-id="588e8-111">Attributes</span></span>  
  
|<span data-ttu-id="588e8-112">屬性</span><span class="sxs-lookup"><span data-stu-id="588e8-112">Attribute</span></span>|<span data-ttu-id="588e8-113">描述</span><span class="sxs-lookup"><span data-stu-id="588e8-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="588e8-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="588e8-114">discoveryEndpoint</span></span>|<span data-ttu-id="588e8-115">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="588e8-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="588e8-116">子元素</span><span class="sxs-lookup"><span data-stu-id="588e8-116">Child Elements</span></span>  
  
|<span data-ttu-id="588e8-117">項目</span><span class="sxs-lookup"><span data-stu-id="588e8-117">Element</span></span>|<span data-ttu-id="588e8-118">描述</span><span class="sxs-lookup"><span data-stu-id="588e8-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="588e8-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="588e8-119">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="588e8-120">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="588e8-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="588e8-121">準則可以分組為搜尋準則 (指定您要尋找的服務), 並尋找終止準則 (搜尋應持續的時間長度)。</span><span class="sxs-lookup"><span data-stu-id="588e8-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="588e8-122">父項目</span><span class="sxs-lookup"><span data-stu-id="588e8-122">Parent Elements</span></span>  
  
|<span data-ttu-id="588e8-123">項目</span><span class="sxs-lookup"><span data-stu-id="588e8-123">Element</span></span>|<span data-ttu-id="588e8-124">說明</span><span class="sxs-lookup"><span data-stu-id="588e8-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="588e8-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="588e8-125">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="588e8-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="588e8-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="588e8-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="588e8-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
