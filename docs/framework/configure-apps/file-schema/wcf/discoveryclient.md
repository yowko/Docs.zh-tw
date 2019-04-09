---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: a5ea10601732021af578c17d4f5c5ab69c98f17a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59128423"
---
# <a name="discoveryclient"></a><span data-ttu-id="e93f1-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="e93f1-101">\<discoveryClient></span></span>
<span data-ttu-id="e93f1-102">組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="e93f1-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="e93f1-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="e93f1-103">\<system.serviceModel></span></span>  
<span data-ttu-id="e93f1-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="e93f1-104">\<bindings></span></span>  
<span data-ttu-id="e93f1-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="e93f1-105">\<customBinding></span></span>  
<span data-ttu-id="e93f1-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="e93f1-106">\<binding></span></span>  
<span data-ttu-id="e93f1-107">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="e93f1-107">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="e93f1-108">語法</span><span class="sxs-lookup"><span data-stu-id="e93f1-108">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e93f1-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e93f1-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e93f1-110">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="e93f1-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e93f1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e93f1-111">Attributes</span></span>  
  
|<span data-ttu-id="e93f1-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e93f1-112">Attribute</span></span>|<span data-ttu-id="e93f1-113">描述</span><span class="sxs-lookup"><span data-stu-id="e93f1-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e93f1-114">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="e93f1-114">discoveryEndpoint</span></span>|<span data-ttu-id="e93f1-115">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="e93f1-115">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e93f1-116">子元素</span><span class="sxs-lookup"><span data-stu-id="e93f1-116">Child Elements</span></span>  
  
|<span data-ttu-id="e93f1-117">項目</span><span class="sxs-lookup"><span data-stu-id="e93f1-117">Element</span></span>|<span data-ttu-id="e93f1-118">描述</span><span class="sxs-lookup"><span data-stu-id="e93f1-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e93f1-119">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="e93f1-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="e93f1-120">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="e93f1-120">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="e93f1-121">準則可以分組為搜尋準則 （指定您要尋找的服務），以及尋找終止準則 （搜尋應持續多久）。</span><span class="sxs-lookup"><span data-stu-id="e93f1-121">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e93f1-122">父項目</span><span class="sxs-lookup"><span data-stu-id="e93f1-122">Parent Elements</span></span>  
  
|<span data-ttu-id="e93f1-123">項目</span><span class="sxs-lookup"><span data-stu-id="e93f1-123">Element</span></span>|<span data-ttu-id="e93f1-124">描述</span><span class="sxs-lookup"><span data-stu-id="e93f1-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="e93f1-125">\<binding></span><span class="sxs-lookup"><span data-stu-id="e93f1-125">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="e93f1-126">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="e93f1-126">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="e93f1-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e93f1-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
