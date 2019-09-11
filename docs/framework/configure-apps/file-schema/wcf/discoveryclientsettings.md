---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 929c5d170bfc27160e3e15b8bd2f9f26e0ed8975
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855407"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="15602-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="15602-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="15602-102">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="15602-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="15602-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="15602-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="15602-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="15602-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="15602-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="15602-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="15602-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<dynamicEndpoint >** ](dynamicendpoint.md)</span><span class="sxs-lookup"><span data-stu-id="15602-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<dynamicEndpoint>**](dynamicendpoint.md)</span></span>\
<span data-ttu-id="15602-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<standardEndpoint >** </span><span class="sxs-lookup"><span data-stu-id="15602-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoint>**</span></span>\
<span data-ttu-id="15602-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<discoveryClientSettings >**</span><span class="sxs-lookup"><span data-stu-id="15602-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<discoveryClientSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="15602-109">語法</span><span class="sxs-lookup"><span data-stu-id="15602-109">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="15602-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="15602-110">Attributes and Elements</span></span>  
 <span data-ttu-id="15602-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="15602-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="15602-112">屬性</span><span class="sxs-lookup"><span data-stu-id="15602-112">Attributes</span></span>  
  
|<span data-ttu-id="15602-113">屬性</span><span class="sxs-lookup"><span data-stu-id="15602-113">Attribute</span></span>|<span data-ttu-id="15602-114">描述</span><span class="sxs-lookup"><span data-stu-id="15602-114">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="15602-115">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="15602-115">discoveryEndpoint</span></span>|<span data-ttu-id="15602-116">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="15602-116">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="15602-117">子元素</span><span class="sxs-lookup"><span data-stu-id="15602-117">Child Elements</span></span>  
  
|<span data-ttu-id="15602-118">項目</span><span class="sxs-lookup"><span data-stu-id="15602-118">Element</span></span>|<span data-ttu-id="15602-119">描述</span><span class="sxs-lookup"><span data-stu-id="15602-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15602-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="15602-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="15602-121">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="15602-121">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="15602-122">準則可以分組為搜尋準則（指定您要尋找的服務），並尋找終止準則（搜尋應持續的時間長度）。</span><span class="sxs-lookup"><span data-stu-id="15602-122">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="15602-123">父項目</span><span class="sxs-lookup"><span data-stu-id="15602-123">Parent Elements</span></span>  
  
|<span data-ttu-id="15602-124">項目</span><span class="sxs-lookup"><span data-stu-id="15602-124">Element</span></span>|<span data-ttu-id="15602-125">說明</span><span class="sxs-lookup"><span data-stu-id="15602-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="15602-126">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="15602-126">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="15602-127">定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="15602-127">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="15602-128">另請參閱</span><span class="sxs-lookup"><span data-stu-id="15602-128">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
