---
title: '&lt;discoveryClientSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 02e1b823-a8bb-4074-90d5-8599f71e8f9d
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3d5e7106de716e4f25e649dbbca716ef66dfa496
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltdiscoveryclientsettingsgt"></a><span data-ttu-id="30cc9-102">&lt;discoveryClientSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="30cc9-102">&lt;discoveryClientSettings&gt;</span></span>
<span data-ttu-id="30cc9-103">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="30cc9-103">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>  
  
<span data-ttu-id="30cc9-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="30cc9-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="30cc9-105">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="30cc9-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="30cc9-106">語法</span><span class="sxs-lookup"><span data-stu-id="30cc9-106">Syntax</span></span>  
  
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
              <add name="String" namespace="String" />
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="30cc9-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="30cc9-107">Attributes and Elements</span></span>  
 <span data-ttu-id="30cc9-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="30cc9-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="30cc9-109">屬性</span><span class="sxs-lookup"><span data-stu-id="30cc9-109">Attributes</span></span>  
  
|<span data-ttu-id="30cc9-110">屬性</span><span class="sxs-lookup"><span data-stu-id="30cc9-110">Attribute</span></span>|<span data-ttu-id="30cc9-111">描述</span><span class="sxs-lookup"><span data-stu-id="30cc9-111">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="30cc9-112">discoveryEndpoint</span><span class="sxs-lookup"><span data-stu-id="30cc9-112">discoveryEndpoint</span></span>|<span data-ttu-id="30cc9-113">字串，其中包含探索端點的名稱，該探索端點可讓用戶端應用程式自動搜尋可探索的服務，並且在執行階段時尋找其位址。</span><span class="sxs-lookup"><span data-stu-id="30cc9-113">A string that contains the name of the Discovery Endpoint that enables a client application to automatically search for a discoverable service and find its address at runtime.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="30cc9-114">子元素</span><span class="sxs-lookup"><span data-stu-id="30cc9-114">Child Elements</span></span>  
  
|<span data-ttu-id="30cc9-115">項目</span><span class="sxs-lookup"><span data-stu-id="30cc9-115">Element</span></span>|<span data-ttu-id="30cc9-116">說明</span><span class="sxs-lookup"><span data-stu-id="30cc9-116">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30cc9-117">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="30cc9-117">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="30cc9-118">組態項目，該項目提供一組用戶端應用程式搜尋探索服務時所用的準則。</span><span class="sxs-lookup"><span data-stu-id="30cc9-118">A configuration element that supplies a set of criteria used by a client application to search for a discovery service.</span></span> <span data-ttu-id="30cc9-119">條件可以分組為搜尋準則 （指定您要尋找的服務），並且尋找終止準則 （搜尋應時間長短）。</span><span class="sxs-lookup"><span data-stu-id="30cc9-119">Criteria can be grouped into search criteria (specifying what services you’re looking for) and find termination criteria (how long the search should last).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="30cc9-120">父項目</span><span class="sxs-lookup"><span data-stu-id="30cc9-120">Parent Elements</span></span>  
  
|<span data-ttu-id="30cc9-121">項目</span><span class="sxs-lookup"><span data-stu-id="30cc9-121">Element</span></span>|<span data-ttu-id="30cc9-122">說明</span><span class="sxs-lookup"><span data-stu-id="30cc9-122">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="30cc9-123">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="30cc9-123">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="30cc9-124">定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="30cc9-124">Defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="30cc9-125">另請參閱</span><span class="sxs-lookup"><span data-stu-id="30cc9-125">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DiscoveryClientBindingElement>  
 <xref:System.ServiceModel.Discovery.Configuration.DiscoveryClientSettingsElement>
