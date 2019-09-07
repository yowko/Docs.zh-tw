---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 5e586437e3b269d361c254744e820ee8e8c0ca0a
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400391"
---
# <a name="discoveryclient"></a><span data-ttu-id="82b32-101">\<discoveryClient></span><span class="sxs-lookup"><span data-stu-id="82b32-101">\<discoveryClient></span></span>
<span data-ttu-id="82b32-102">組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="82b32-102">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
<span data-ttu-id="82b32-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="82b32-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="82b32-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="82b32-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="82b32-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="82b32-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="82b32-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="82b32-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="82b32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="82b32-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="82b32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClient >**</span><span class="sxs-lookup"><span data-stu-id="82b32-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="82b32-109">語法</span><span class="sxs-lookup"><span data-stu-id="82b32-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="82b32-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="82b32-110">Attributes and Elements</span></span>  
 <span data-ttu-id="82b32-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="82b32-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="82b32-112">屬性</span><span class="sxs-lookup"><span data-stu-id="82b32-112">Attributes</span></span>  
  
|<span data-ttu-id="82b32-113">屬性</span><span class="sxs-lookup"><span data-stu-id="82b32-113">Attribute</span></span>|<span data-ttu-id="82b32-114">描述</span><span class="sxs-lookup"><span data-stu-id="82b32-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="82b32-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="82b32-115">discoveryEndpoint</span></span>|<span data-ttu-id="82b32-116">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="82b32-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="82b32-117">子元素</span><span class="sxs-lookup"><span data-stu-id="82b32-117">Child Elements</span></span>  
  
|<span data-ttu-id="82b32-118">項目</span><span class="sxs-lookup"><span data-stu-id="82b32-118">Element</span></span>|<span data-ttu-id="82b32-119">描述</span><span class="sxs-lookup"><span data-stu-id="82b32-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82b32-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="82b32-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="82b32-121">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="82b32-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="82b32-122">準則可以分組為搜尋準則（指定您要尋找的服務），並尋找終止準則（搜尋應持續的時間長度）。</span><span class="sxs-lookup"><span data-stu-id="82b32-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="82b32-123">父項目</span><span class="sxs-lookup"><span data-stu-id="82b32-123">Parent Elements</span></span>  
  
|<span data-ttu-id="82b32-124">項目</span><span class="sxs-lookup"><span data-stu-id="82b32-124">Element</span></span>|<span data-ttu-id="82b32-125">描述</span><span class="sxs-lookup"><span data-stu-id="82b32-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="82b32-126">\<binding></span><span class="sxs-lookup"><span data-stu-id="82b32-126">\<binding></span></span>](../../../misc/binding.md)|<span data-ttu-id="82b32-127">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="82b32-127">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="82b32-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="82b32-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
