---
title: '&lt;discoveryClient&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 55c8b9a01eaf53105968e044aecb7e38ad691aac
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientgt"></a><span data-ttu-id="0d8de-102">&lt;discoveryClient&gt;</span><span class="sxs-lookup"><span data-stu-id="0d8de-102">&lt;discoveryClient&gt;</span></span>
<span data-ttu-id="0d8de-103">組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="0d8de-103">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="0d8de-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="0d8de-104">\<system.serviceModel></span></span>  
<span data-ttu-id="0d8de-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="0d8de-105">\<bindings></span></span>  
<span data-ttu-id="0d8de-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="0d8de-106">\<customBinding></span></span>  
<span data-ttu-id="0d8de-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="0d8de-107">\<binding></span></span>  
<span data-ttu-id="0d8de-108">\<discoveryClient ></span><span class="sxs-lookup"><span data-stu-id="0d8de-108">\<discoveryClient></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0d8de-109">語法</span><span class="sxs-lookup"><span data-stu-id="0d8de-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0d8de-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0d8de-110">Attributes and Elements</span></span>  
 <span data-ttu-id="0d8de-111">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="0d8de-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0d8de-112">屬性</span><span class="sxs-lookup"><span data-stu-id="0d8de-112">Attributes</span></span>  
  
|<span data-ttu-id="0d8de-113">屬性</span><span class="sxs-lookup"><span data-stu-id="0d8de-113">Attribute</span></span>|<span data-ttu-id="0d8de-114">描述</span><span class="sxs-lookup"><span data-stu-id="0d8de-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="0d8de-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="0d8de-115">discoveryEndpoint</span></span>|<span data-ttu-id="0d8de-116">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="0d8de-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="0d8de-117">子元素</span><span class="sxs-lookup"><span data-stu-id="0d8de-117">Child Elements</span></span>  
  
|<span data-ttu-id="0d8de-118">項目</span><span class="sxs-lookup"><span data-stu-id="0d8de-118">Element</span></span>|<span data-ttu-id="0d8de-119">說明</span><span class="sxs-lookup"><span data-stu-id="0d8de-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d8de-120">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="0d8de-120">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="0d8de-121">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="0d8de-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="0d8de-122">條件可以分組為搜尋準則 （指定您要尋找的服務），並且尋找終止準則 （搜尋應時間長短）。</span><span class="sxs-lookup"><span data-stu-id="0d8de-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0d8de-123">父項目</span><span class="sxs-lookup"><span data-stu-id="0d8de-123">Parent Elements</span></span>  
  
|<span data-ttu-id="0d8de-124">項目</span><span class="sxs-lookup"><span data-stu-id="0d8de-124">Element</span></span>|<span data-ttu-id="0d8de-125">說明</span><span class="sxs-lookup"><span data-stu-id="0d8de-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="0d8de-126">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="0d8de-126">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)|<span data-ttu-id="0d8de-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="0d8de-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0d8de-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0d8de-128">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
