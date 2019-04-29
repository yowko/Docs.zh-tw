---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: e1a53869faa1997d2e79c3d2869a15001ee29626
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673156"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="2a635-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="2a635-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="2a635-102">這個組態項目定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="2a635-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="2a635-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="2a635-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="2a635-104">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2a635-104">\<standardEndpoints></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="2a635-105">語法</span><span class="sxs-lookup"><span data-stu-id="2a635-105">Syntax</span></span>  
  
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
              <add scope="URI" />
            </scopes>
          </findCriteria>
        </discoveryClientSettings>
      <standardEndpoint>
    </dynamicEndpoint>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="2a635-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="2a635-106">Attributes and Elements</span></span>  
 <span data-ttu-id="2a635-107">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="2a635-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="2a635-108">屬性</span><span class="sxs-lookup"><span data-stu-id="2a635-108">Attributes</span></span>  
 <span data-ttu-id="2a635-109">無。</span><span class="sxs-lookup"><span data-stu-id="2a635-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="2a635-110">子元素</span><span class="sxs-lookup"><span data-stu-id="2a635-110">Child Elements</span></span>  
  
|<span data-ttu-id="2a635-111">項目</span><span class="sxs-lookup"><span data-stu-id="2a635-111">Element</span></span>|<span data-ttu-id="2a635-112">描述</span><span class="sxs-lookup"><span data-stu-id="2a635-112">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a635-113">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="2a635-113">\<discoveryClientSettings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/discoveryclientsettings.md)|<span data-ttu-id="2a635-114">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="2a635-114">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="2a635-115">父項目</span><span class="sxs-lookup"><span data-stu-id="2a635-115">Parent Elements</span></span>  
  
|<span data-ttu-id="2a635-116">項目</span><span class="sxs-lookup"><span data-stu-id="2a635-116">Element</span></span>|<span data-ttu-id="2a635-117">描述</span><span class="sxs-lookup"><span data-stu-id="2a635-117">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="2a635-118">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="2a635-118">\<standardEndpoints></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/standardendpoints.md)|<span data-ttu-id="2a635-119">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="2a635-119">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="2a635-120">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2a635-120">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
