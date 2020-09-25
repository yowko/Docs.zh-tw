---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 6e3f273af807eb362f005fef63246013ecc88581
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91192239"
---
# \<discoveryClientSettings>

<span data-ttu-id="4c533-101">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="4c533-101">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="4c533-102">Syntax</span><span class="sxs-lookup"><span data-stu-id="4c533-102">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
    <dynamicEndpoint>
      <standardEndpoint>
        <discoveryClientSettings discoveryEndpoint="String">
          <findCriteria duration="TimeSpan"
                        maxResults="Integer"
                        scopeMatchBy="Uri">
            <contractTypeNames>
              <add name="String"
                   namespace="String" />
            <contractTypeNames>
            <extensions />
            <scopes>
              <add scope="URI"/>
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="4c533-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="4c533-103">Attributes and Elements</span></span>  

 <span data-ttu-id="4c533-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="4c533-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="4c533-105">屬性</span><span class="sxs-lookup"><span data-stu-id="4c533-105">Attributes</span></span>  
  
|<span data-ttu-id="4c533-106">屬性</span><span class="sxs-lookup"><span data-stu-id="4c533-106">Attribute</span></span>|<span data-ttu-id="4c533-107">描述</span><span class="sxs-lookup"><span data-stu-id="4c533-107">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="4c533-108">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="4c533-108">discoveryEndpoint</span></span>|<span data-ttu-id="4c533-109">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="4c533-109">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="4c533-110">子元素</span><span class="sxs-lookup"><span data-stu-id="4c533-110">Child Elements</span></span>  
  
|<span data-ttu-id="4c533-111">項目</span><span class="sxs-lookup"><span data-stu-id="4c533-111">Element</span></span>|<span data-ttu-id="4c533-112">描述</span><span class="sxs-lookup"><span data-stu-id="4c533-112">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="4c533-113">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="4c533-113">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="4c533-114">您可以將標準群組為搜尋準則 (指定您要尋找的服務)，並且尋找終止準則 (搜尋應持續的時間長短)。</span><span class="sxs-lookup"><span data-stu-id="4c533-114">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="4c533-115">父項目</span><span class="sxs-lookup"><span data-stu-id="4c533-115">Parent Elements</span></span>  
  
|<span data-ttu-id="4c533-116">項目</span><span class="sxs-lookup"><span data-stu-id="4c533-116">Element</span></span>|<span data-ttu-id="4c533-117">描述</span><span class="sxs-lookup"><span data-stu-id="4c533-117">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="4c533-118">定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="4c533-118">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="4c533-119">另請參閱</span><span class="sxs-lookup"><span data-stu-id="4c533-119">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
