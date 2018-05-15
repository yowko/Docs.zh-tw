---
title: '&lt;discoveryClient&gt;'
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 8c69104b9eb1097ef5dc94c9aae7352d4949668f
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="fdfbf-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="fdfbf-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="fdfbf-103">組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="fdfbf-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="fdfbf-104">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="fdfbf-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fdfbf-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fdfbf-105">\<bindings></span></span>  
<span data-ttu-id="fdfbf-106">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="fdfbf-106">\<customBinding></span></span>  
<span data-ttu-id="fdfbf-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fdfbf-107">\<binding></span></span>  
<span data-ttu-id="fdfbf-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="fdfbf-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fdfbf-109">語法</span><span class="sxs-lookup"><span data-stu-id="fdfbf-109">Syntax</span></span>  
  
```xml  
<discoveryClient discoveryEndpoint="String" >
  <findCriteria duration="TimeSpan" maxResults="Integer" scopeMatchBy="Uri">
    <contractTypeNames>
      <add name="String" namespace="String" />
    <contractTypeNames>
    <extensions />
    <scopes>
      <add scope="URI"/>
    </scopes>
  </findCriteria>
</discoveryClient>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fdfbf-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fdfbf-110">Attributes and Elements</span></span>  
 <span data-ttu-id="fdfbf-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fdfbf-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fdfbf-112">屬性</span><span class="sxs-lookup"><span data-stu-id="fdfbf-112">Attributes</span></span>  
  
|<span data-ttu-id="fdfbf-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fdfbf-113">Attribute</span></span>|<span data-ttu-id="fdfbf-114">描述</span><span class="sxs-lookup"><span data-stu-id="fdfbf-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="fdfbf-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="fdfbf-115">discoveryEndpoint</span></span>|<span data-ttu-id="fdfbf-116">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="fdfbf-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fdfbf-117">子項目</span><span class="sxs-lookup"><span data-stu-id="fdfbf-117">Child Elements</span></span>  
  
|<span data-ttu-id="fdfbf-118">項目</span><span class="sxs-lookup"><span data-stu-id="fdfbf-118">Element</span></span>|<span data-ttu-id="fdfbf-119">描述</span><span class="sxs-lookup"><span data-stu-id="fdfbf-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdfbf-120">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="fdfbf-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="fdfbf-121">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="fdfbf-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="fdfbf-122">條件可以分組為搜尋準則 （指定您要尋找的服務），並且尋找終止準則 （搜尋應時間長短）。</span><span class="sxs-lookup"><span data-stu-id="fdfbf-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="fdfbf-123">父項目</span><span class="sxs-lookup"><span data-stu-id="fdfbf-123">Parent Elements</span></span>  
  
|<span data-ttu-id="fdfbf-124">項目</span><span class="sxs-lookup"><span data-stu-id="fdfbf-124">Element</span></span>|<span data-ttu-id="fdfbf-125">描述</span><span class="sxs-lookup"><span data-stu-id="fdfbf-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fdfbf-126">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fdfbf-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="fdfbf-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="fdfbf-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="fdfbf-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fdfbf-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
