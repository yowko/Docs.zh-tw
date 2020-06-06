---
title: <discoveryClient>
ms.date: 03/30/2017
ms.assetid: a78f74c3-1152-4149-ab29-3f12d316caeb
ms.openlocfilehash: 71305720cad0206ec3dabb1863e2f1cd72eb85f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73739042"
---
# \<discoveryClient>
<span data-ttu-id="6287a-101">組態項目，用於建立自訂繫結，該繫結可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="6287a-101">A configuration element for creating a custom binding that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClient>**  
  
## <a name="syntax"></a><span data-ttu-id="6287a-102">語法</span><span class="sxs-lookup"><span data-stu-id="6287a-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6287a-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="6287a-103">Attributes and Elements</span></span>  
 <span data-ttu-id="6287a-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6287a-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6287a-105">屬性</span><span class="sxs-lookup"><span data-stu-id="6287a-105">Attributes</span></span>  
  
|<span data-ttu-id="6287a-106">屬性</span><span class="sxs-lookup"><span data-stu-id="6287a-106">Attribute</span></span>|<span data-ttu-id="6287a-107">描述</span><span class="sxs-lookup"><span data-stu-id="6287a-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="6287a-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="6287a-108">discoveryEndpoint</span></span>|<span data-ttu-id="6287a-109">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="6287a-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6287a-110">子元素</span><span class="sxs-lookup"><span data-stu-id="6287a-110">Child Elements</span></span>  
  
|<span data-ttu-id="6287a-111">元素</span><span class="sxs-lookup"><span data-stu-id="6287a-111">Element</span></span>|<span data-ttu-id="6287a-112">描述</span><span class="sxs-lookup"><span data-stu-id="6287a-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="6287a-113">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="6287a-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="6287a-114">您可以將標準群組為搜尋準則 (指定您要尋找的服務)，並且尋找終止準則 (搜尋應持續的時間長短)。</span><span class="sxs-lookup"><span data-stu-id="6287a-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="6287a-115">父項目</span><span class="sxs-lookup"><span data-stu-id="6287a-115">Parent Elements</span></span>  
  
|<span data-ttu-id="6287a-116">元素</span><span class="sxs-lookup"><span data-stu-id="6287a-116">Element</span></span>|<span data-ttu-id="6287a-117">描述</span><span class="sxs-lookup"><span data-stu-id="6287a-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="6287a-118">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="6287a-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6287a-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6287a-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientElement>
