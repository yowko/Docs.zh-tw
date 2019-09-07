---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 57e9e19025db5e1fa588f073fdf30de09837a25d
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70399946"
---
# <a name="scopes"></a><span data-ttu-id="cf3cc-101">\<scopes></span><span class="sxs-lookup"><span data-stu-id="cf3cc-101">\<scopes></span></span>
<span data-ttu-id="cf3cc-102">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="cf3cc-102">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
<span data-ttu-id="cf3cc-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cf3cc-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cf3cc-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cf3cc-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cf3cc-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cf3cc-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="cf3cc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cf3cc-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="cf3cc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behavior-of-endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="cf3cc-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)</span></span>\
<span data-ttu-id="cf3cc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointDiscovery >** ](endpointdiscovery.md)</span><span class="sxs-lookup"><span data-stu-id="cf3cc-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)</span></span>\
<span data-ttu-id="cf3cc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<範圍 >**</span><span class="sxs-lookup"><span data-stu-id="cf3cc-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf3cc-110">語法</span><span class="sxs-lookup"><span data-stu-id="cf3cc-110">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cf3cc-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cf3cc-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cf3cc-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cf3cc-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cf3cc-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cf3cc-113">Attributes</span></span>  
 <span data-ttu-id="cf3cc-114">無。</span><span class="sxs-lookup"><span data-stu-id="cf3cc-114">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="cf3cc-115">子元素</span><span class="sxs-lookup"><span data-stu-id="cf3cc-115">Child Elements</span></span>  
  
|<span data-ttu-id="cf3cc-116">屬性</span><span class="sxs-lookup"><span data-stu-id="cf3cc-116">Attribute</span></span>|<span data-ttu-id="cf3cc-117">說明</span><span class="sxs-lookup"><span data-stu-id="cf3cc-117">Description</span></span>|  
|---------------|-----------------|  
|[<span data-ttu-id="cf3cc-118">\<add></span><span class="sxs-lookup"><span data-stu-id="cf3cc-118">\<add></span></span>](add-of-scopes.md)|<span data-ttu-id="cf3cc-119">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="cf3cc-119">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="cf3cc-120">父項目</span><span class="sxs-lookup"><span data-stu-id="cf3cc-120">Parent Elements</span></span>  
  
|<span data-ttu-id="cf3cc-121">項目</span><span class="sxs-lookup"><span data-stu-id="cf3cc-121">Element</span></span>|<span data-ttu-id="cf3cc-122">描述</span><span class="sxs-lookup"><span data-stu-id="cf3cc-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cf3cc-123">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="cf3cc-123">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="cf3cc-124">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="cf3cc-124">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cf3cc-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cf3cc-125">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
