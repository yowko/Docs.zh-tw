---
title: <add> 的 <scopes>
ms.date: 03/30/2017
ms.assetid: 0563a7d8-fc84-4c85-9066-af32665857c2
ms.openlocfilehash: bcde6b18c34dccf1716c809dddeb45b1b4da90f0
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398299"
---
# <a name="add-of-scopes"></a><span data-ttu-id="bde25-102">\<add> 的 \<scopes></span><span class="sxs-lookup"><span data-stu-id="bde25-102">\<add> of \<scopes></span></span>
<span data-ttu-id="bde25-103">加入自訂的範圍 URI，這個 URI 可用於在查詢期間篩選服務端點。</span><span class="sxs-lookup"><span data-stu-id="bde25-103">Adds a custom scope Uri that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<scopes>**](scopes.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<add>**  
  
## <a name="syntax"></a><span data-ttu-id="bde25-104">語法</span><span class="sxs-lookup"><span data-stu-id="bde25-104">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="bde25-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="bde25-105">Attributes and Elements</span></span>  
 <span data-ttu-id="bde25-106">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="bde25-106">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="bde25-107">屬性</span><span class="sxs-lookup"><span data-stu-id="bde25-107">Attributes</span></span>  
  
|<span data-ttu-id="bde25-108">屬性</span><span class="sxs-lookup"><span data-stu-id="bde25-108">Attribute</span></span>|<span data-ttu-id="bde25-109">描述</span><span class="sxs-lookup"><span data-stu-id="bde25-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="bde25-110">scope</span><span class="sxs-lookup"><span data-stu-id="bde25-110">scope</span></span>|<span data-ttu-id="bde25-111">URI，其中包含端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="bde25-111">A URI that contains scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="bde25-112">子元素</span><span class="sxs-lookup"><span data-stu-id="bde25-112">Child Elements</span></span>  
 <span data-ttu-id="bde25-113">無。</span><span class="sxs-lookup"><span data-stu-id="bde25-113">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="bde25-114">父項目</span><span class="sxs-lookup"><span data-stu-id="bde25-114">Parent Elements</span></span>  
  
|<span data-ttu-id="bde25-115">元素</span><span class="sxs-lookup"><span data-stu-id="bde25-115">Element</span></span>|<span data-ttu-id="bde25-116">描述</span><span class="sxs-lookup"><span data-stu-id="bde25-116">Description</span></span>|  
|-------------|-----------------|  
|[\<scopes>](scopes.md)|<span data-ttu-id="bde25-117">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="bde25-117">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="bde25-118">另請參閱</span><span class="sxs-lookup"><span data-stu-id="bde25-118">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
