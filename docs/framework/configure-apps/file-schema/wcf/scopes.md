---
title: <scopes>
ms.date: 03/30/2017
ms.assetid: 9a0dd3ce-e383-4ac3-b7be-7d604388304a
ms.openlocfilehash: 63f46753da13469147b378f373de9888a007bf52
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91162214"
---
# \<scopes>

<span data-ttu-id="8457c-101">包含組態項目的集合，這些項目會指定可用於在查詢期間篩選服務端點的自訂範圍 URI。</span><span class="sxs-lookup"><span data-stu-id="8457c-101">Contains a collection of configuration elements that specify custom scope Uris that can be used to filter service endpoints during query.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<behavior>**](behavior-of-endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointDiscovery>**](endpointdiscovery.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<scopes>**  
  
## <a name="syntax"></a><span data-ttu-id="8457c-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="8457c-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8457c-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8457c-103">Attributes and Elements</span></span>  

 <span data-ttu-id="8457c-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="8457c-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8457c-105">屬性</span><span class="sxs-lookup"><span data-stu-id="8457c-105">Attributes</span></span>  

 <span data-ttu-id="8457c-106">無。</span><span class="sxs-lookup"><span data-stu-id="8457c-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="8457c-107">子元素</span><span class="sxs-lookup"><span data-stu-id="8457c-107">Child Elements</span></span>  
  
|<span data-ttu-id="8457c-108">屬性</span><span class="sxs-lookup"><span data-stu-id="8457c-108">Attribute</span></span>|<span data-ttu-id="8457c-109">描述</span><span class="sxs-lookup"><span data-stu-id="8457c-109">Description</span></span>|  
|---------------|-----------------|  
|[\<add>](add-of-scopes.md)|<span data-ttu-id="8457c-110">加入端點的範圍資訊，可用於比對尋找服務的準則。</span><span class="sxs-lookup"><span data-stu-id="8457c-110">Adds the scope information for the endpoint that can be used in matching criteria for finding services.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="8457c-111">父項目</span><span class="sxs-lookup"><span data-stu-id="8457c-111">Parent Elements</span></span>  
  
|<span data-ttu-id="8457c-112">項目</span><span class="sxs-lookup"><span data-stu-id="8457c-112">Element</span></span>|<span data-ttu-id="8457c-113">描述</span><span class="sxs-lookup"><span data-stu-id="8457c-113">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="8457c-114">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="8457c-114">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="8457c-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8457c-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.EndpointDiscoveryBehavior>
