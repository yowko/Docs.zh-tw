---
title: <discoveryClientSettings>
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: 0b014a9d797ded61949a374486824ee3ebc34661
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59136249"
---
# <a name="discoveryclientsettings"></a><span data-ttu-id="30917-101">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="30917-101">\<discoveryClientSettings></span></span>
<span data-ttu-id="30917-102">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="30917-102">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="30917-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="30917-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="30917-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="30917-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30917-105">語法</span><span class="sxs-lookup"><span data-stu-id="30917-105">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30917-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="30917-106">Attributes and Elements</span></span>  
 <span data-ttu-id="30917-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="30917-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30917-108">屬性</span><span class="sxs-lookup"><span data-stu-id="30917-108">Attributes</span></span>  
  
|<span data-ttu-id="30917-109">屬性</span><span class="sxs-lookup"><span data-stu-id="30917-109">Attribute</span></span>|<span data-ttu-id="30917-110">描述</span><span class="sxs-lookup"><span data-stu-id="30917-110">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30917-111">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="30917-111">discoveryEndpoint</span></span>|<span data-ttu-id="30917-112">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="30917-112">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30917-113">子元素</span><span class="sxs-lookup"><span data-stu-id="30917-113">Child Elements</span></span>  
  
|<span data-ttu-id="30917-114">項目</span><span class="sxs-lookup"><span data-stu-id="30917-114">Element</span></span>|<span data-ttu-id="30917-115">描述</span><span class="sxs-lookup"><span data-stu-id="30917-115">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30917-116">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="30917-116">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="30917-117">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="30917-117">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="30917-118">準則可以分組為搜尋準則 （指定您要尋找的服務），以及尋找終止準則 （搜尋應持續多久）。</span><span class="sxs-lookup"><span data-stu-id="30917-118">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30917-119">父項目</span><span class="sxs-lookup"><span data-stu-id="30917-119">Parent Elements</span></span>  
  
|<span data-ttu-id="30917-120">項目</span><span class="sxs-lookup"><span data-stu-id="30917-120">Element</span></span>|<span data-ttu-id="30917-121">描述</span><span class="sxs-lookup"><span data-stu-id="30917-121">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30917-122">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="30917-122">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="30917-123">定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="30917-123">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30917-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30917-124">See also</span></span>

- <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>
- <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
