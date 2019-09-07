---
title: <add> 的 <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70398299"
---
# <a name="add-of-scopes"></a><span data-ttu-id="efe09-102">\<新增範圍的\<> ></span><span class="sxs-lookup"><span data-stu-id="efe09-102">\<add> of \<scopes></span></span>
<span data-ttu-id="efe09-103">加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。</span><span class="sxs-lookup"><span data-stu-id="efe09-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="efe09-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="efe09-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="efe09-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="efe09-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="efe09-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="efe09-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="efe09-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<範圍 >** ](scopes.md)</span><span class="sxs-lookup"><span data-stu-id="efe09-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)</span></span>\
<span data-ttu-id="efe09-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<新增 >**</span><span class="sxs-lookup"><span data-stu-id="efe09-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="efe09-112">語法</span><span class="sxs-lookup"><span data-stu-id="efe09-112">Syntax</span></span>  
  
```xml  
<behaviors>
  <endpointBehaviors>
    <behavior name="String">
      <endpointDiscovery enable="Boolean">
        <scopes>
          <add scope="URI" />
        </scopes>
      </endpointDiscovery>
    </behavior>
  </endpointBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="efe09-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="efe09-113">Attributes and Elements</span></span>  
 <span data-ttu-id="efe09-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="efe09-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="efe09-115">屬性</span><span class="sxs-lookup"><span data-stu-id="efe09-115">Attributes</span></span>  
  
|<span data-ttu-id="efe09-116">屬性</span><span class="sxs-lookup"><span data-stu-id="efe09-116">Attribute</span></span>|<span data-ttu-id="efe09-117">描述</span><span class="sxs-lookup"><span data-stu-id="efe09-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="efe09-118">範圍</span><span class="sxs-lookup"><span data-stu-id="efe09-118">scope</span></span>|<span data-ttu-id="efe09-119">URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="efe09-119">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="efe09-120">子元素</span><span class="sxs-lookup"><span data-stu-id="efe09-120">Child Elements</span></span>  
 <span data-ttu-id="efe09-121">無。</span><span class="sxs-lookup"><span data-stu-id="efe09-121">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="efe09-122">父項目</span><span class="sxs-lookup"><span data-stu-id="efe09-122">Parent Elements</span></span>  
  
|<span data-ttu-id="efe09-123">項目</span><span class="sxs-lookup"><span data-stu-id="efe09-123">Element</span></span>|<span data-ttu-id="efe09-124">描述</span><span class="sxs-lookup"><span data-stu-id="efe09-124">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="efe09-125">\<scopes></span><span class="sxs-lookup"><span data-stu-id="efe09-125">\<scopes></span></span>](scopes.md)|<span data-ttu-id="efe09-126">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="efe09-126">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="efe09-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="efe09-127">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
