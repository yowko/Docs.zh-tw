---
title: '&lt;discoveryClientSettings&gt;'
ms.date: 03/30/2017
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
ms.openlocfilehash: bb443334e0713464e64ec9297bbab4ad11eda723
ms.sourcegitcommit: 4ac80713f6faa220e5a119d5165308a58f7ccdc8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/09/2019
ms.locfileid: "54145051"
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="f7d54-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="f7d54-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="f7d54-103">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="f7d54-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="f7d54-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f7d54-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="f7d54-105">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f7d54-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f7d54-106">語法</span><span class="sxs-lookup"><span data-stu-id="f7d54-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f7d54-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f7d54-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f7d54-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f7d54-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f7d54-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f7d54-109">Attributes</span></span>  
  
|<span data-ttu-id="f7d54-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f7d54-110">Attribute</span></span>|<span data-ttu-id="f7d54-111">描述</span><span class="sxs-lookup"><span data-stu-id="f7d54-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f7d54-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="f7d54-112">discoveryEndpoint</span></span>|<span data-ttu-id="f7d54-113">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="f7d54-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f7d54-114">子元素</span><span class="sxs-lookup"><span data-stu-id="f7d54-114">Child Elements</span></span>  
  
|<span data-ttu-id="f7d54-115">項目</span><span class="sxs-lookup"><span data-stu-id="f7d54-115">Element</span></span>|<span data-ttu-id="f7d54-116">描述</span><span class="sxs-lookup"><span data-stu-id="f7d54-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7d54-117">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f7d54-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f7d54-118">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="f7d54-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="f7d54-119">準則可以分組為搜尋準則 （指定您要尋找的服務），以及尋找終止準則 （搜尋應持續多久）。</span><span class="sxs-lookup"><span data-stu-id="f7d54-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="f7d54-120">父項目</span><span class="sxs-lookup"><span data-stu-id="f7d54-120">Parent Elements</span></span>  
  
|<span data-ttu-id="f7d54-121">項目</span><span class="sxs-lookup"><span data-stu-id="f7d54-121">Element</span></span>|<span data-ttu-id="f7d54-122">描述</span><span class="sxs-lookup"><span data-stu-id="f7d54-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f7d54-123">\<standardEndpoints ></span><span class="sxs-lookup"><span data-stu-id="f7d54-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="f7d54-124">定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="f7d54-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f7d54-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f7d54-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
