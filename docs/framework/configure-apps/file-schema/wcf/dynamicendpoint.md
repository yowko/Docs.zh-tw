---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855351"
---
# <a name="dynamicendpoint"></a><span data-ttu-id="c0f4c-101">\<dynamicEndpoint></span><span class="sxs-lookup"><span data-stu-id="c0f4c-101">\<dynamicEndpoint></span></span>
<span data-ttu-id="c0f4c-102">這個組態項目定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="c0f4c-102">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
<span data-ttu-id="c0f4c-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="c0f4c-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="c0f4c-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="c0f4c-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="c0f4c-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<standardEndpoints >** ](standardendpoints.md)</span><span class="sxs-lookup"><span data-stu-id="c0f4c-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)</span></span>\
<span data-ttu-id="c0f4c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<dynamicEndpoint >**</span><span class="sxs-lookup"><span data-stu-id="c0f4c-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c0f4c-107">語法</span><span class="sxs-lookup"><span data-stu-id="c0f4c-107">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="c0f4c-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="c0f4c-108">Attributes and Elements</span></span>  
 <span data-ttu-id="c0f4c-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="c0f4c-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="c0f4c-110">屬性</span><span class="sxs-lookup"><span data-stu-id="c0f4c-110">Attributes</span></span>  
 <span data-ttu-id="c0f4c-111">無。</span><span class="sxs-lookup"><span data-stu-id="c0f4c-111">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="c0f4c-112">子元素</span><span class="sxs-lookup"><span data-stu-id="c0f4c-112">Child Elements</span></span>  
  
|<span data-ttu-id="c0f4c-113">項目</span><span class="sxs-lookup"><span data-stu-id="c0f4c-113">Element</span></span>|<span data-ttu-id="c0f4c-114">描述</span><span class="sxs-lookup"><span data-stu-id="c0f4c-114">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0f4c-115">\<discoveryClientSettings></span><span class="sxs-lookup"><span data-stu-id="c0f4c-115">\<discoveryClientSettings></span></span>](discoveryclientsettings.md)|<span data-ttu-id="c0f4c-116">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="c0f4c-116">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="c0f4c-117">父項目</span><span class="sxs-lookup"><span data-stu-id="c0f4c-117">Parent Elements</span></span>  
  
|<span data-ttu-id="c0f4c-118">項目</span><span class="sxs-lookup"><span data-stu-id="c0f4c-118">Element</span></span>|<span data-ttu-id="c0f4c-119">說明</span><span class="sxs-lookup"><span data-stu-id="c0f4c-119">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="c0f4c-120">\<standardEndpoints></span><span class="sxs-lookup"><span data-stu-id="c0f4c-120">\<standardEndpoints></span></span>](standardendpoints.md)|<span data-ttu-id="c0f4c-121">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="c0f4c-121">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c0f4c-122">另請參閱</span><span class="sxs-lookup"><span data-stu-id="c0f4c-122">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
