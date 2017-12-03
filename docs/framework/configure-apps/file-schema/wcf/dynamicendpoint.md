---
title: '&lt;dynamicEndpoint&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
caps.latest.revision: "2"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e780e1975aecc80ea458ec6a86fca61e4ad22448
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/02/2017
---
# <a name="ltdynamicendpointgt"></a><span data-ttu-id="853aa-102">&lt;dynamicEndpoint&gt;</span><span class="sxs-lookup"><span data-stu-id="853aa-102">&lt;dynamicEndpoint&gt;</span></span>
<span data-ttu-id="853aa-103">這個組態項目定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="853aa-103">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="853aa-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="853aa-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="853aa-105">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="853aa-105">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="853aa-106">語法</span><span class="sxs-lookup"><span data-stu-id="853aa-106">Syntax</span></span>  
  
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
            <add scope="URI" />
          </scopes>
        </findCriteria>
      </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>  
</system.serviceModel>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="853aa-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="853aa-107">Attributes and Elements</span></span>  
 <span data-ttu-id="853aa-108">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="853aa-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="853aa-109">屬性</span><span class="sxs-lookup"><span data-stu-id="853aa-109">Attributes</span></span>  
 <span data-ttu-id="853aa-110">無。</span><span class="sxs-lookup"><span data-stu-id="853aa-110">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="853aa-111">子項目</span><span class="sxs-lookup"><span data-stu-id="853aa-111">Child Elements</span></span>  
  
|<span data-ttu-id="853aa-112">項目</span><span class="sxs-lookup"><span data-stu-id="853aa-112">Element</span></span>|<span data-ttu-id="853aa-113">說明</span><span class="sxs-lookup"><span data-stu-id="853aa-113">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="853aa-114">\<discoveryClientSettings ></span><span class="sxs-lookup"><span data-stu-id="853aa-114">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="853aa-115">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="853aa-115">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="853aa-116">父項目</span><span class="sxs-lookup"><span data-stu-id="853aa-116">Parent Elements</span></span>  
  
|<span data-ttu-id="853aa-117">項目</span><span class="sxs-lookup"><span data-stu-id="853aa-117">Element</span></span>|<span data-ttu-id="853aa-118">說明</span><span class="sxs-lookup"><span data-stu-id="853aa-118">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="853aa-119">\<Kind ></span><span class="sxs-lookup"><span data-stu-id="853aa-119">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="853aa-120">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="853aa-120">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="853aa-121">另請參閱</span><span class="sxs-lookup"><span data-stu-id="853aa-121">See Also</span></span>  
 <xref:System.ServiceModel.Discovery.DynamicEndpoint>  
 <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
