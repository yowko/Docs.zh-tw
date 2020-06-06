---
title: <dynamicEndpoint>
ms.date: 03/30/2017
ms.assetid: 929f223d-176d-4205-9505-234ddb6dbff4
ms.openlocfilehash: da57ca3ba3bc0036727a749f1cab9ec3657a4fda
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70855351"
---
# \<dynamicEndpoint>
<span data-ttu-id="0ba24-101">這個組態項目定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="0ba24-101">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<standardEndpoints>**](standardendpoints.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<dynamicEndpoint>**  
  
## <a name="syntax"></a><span data-ttu-id="0ba24-102">語法</span><span class="sxs-lookup"><span data-stu-id="0ba24-102">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="0ba24-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="0ba24-103">Attributes and Elements</span></span>  
 <span data-ttu-id="0ba24-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="0ba24-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="0ba24-105">屬性</span><span class="sxs-lookup"><span data-stu-id="0ba24-105">Attributes</span></span>  
 <span data-ttu-id="0ba24-106">無。</span><span class="sxs-lookup"><span data-stu-id="0ba24-106">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="0ba24-107">子元素</span><span class="sxs-lookup"><span data-stu-id="0ba24-107">Child Elements</span></span>  
  
|<span data-ttu-id="0ba24-108">元素</span><span class="sxs-lookup"><span data-stu-id="0ba24-108">Element</span></span>|<span data-ttu-id="0ba24-109">描述</span><span class="sxs-lookup"><span data-stu-id="0ba24-109">Description</span></span>|  
|-------------|-----------------|  
|[\<discoveryClientSettings>](discoveryclientsettings.md)|<span data-ttu-id="0ba24-110">包含應用程式參與服務探索處理序做為用戶端所需的設定。</span><span class="sxs-lookup"><span data-stu-id="0ba24-110">Contains the settings needed by an application to participate in the service discovery process as a client.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="0ba24-111">父項目</span><span class="sxs-lookup"><span data-stu-id="0ba24-111">Parent Elements</span></span>  
  
|<span data-ttu-id="0ba24-112">元素</span><span class="sxs-lookup"><span data-stu-id="0ba24-112">Element</span></span>|<span data-ttu-id="0ba24-113">描述</span><span class="sxs-lookup"><span data-stu-id="0ba24-113">Description</span></span>|  
|-------------|-----------------|  
|[\<standardEndpoints>](standardendpoints.md)|<span data-ttu-id="0ba24-114">標準端點的集合，這些端點是預先定義的端點，其中包含一個或多個固定的屬性 (位址、繫結、合約)。</span><span class="sxs-lookup"><span data-stu-id="0ba24-114">A collection of standard endpoints that are pre-defined endpoints with one or more of their properties (address, binding, contract) fixed.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="0ba24-115">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0ba24-115">See also</span></span>

- <xref:System.ServiceModel.Discovery.DynamicEndpoint>
- <xref:System.ServiceModel.Discovery.Configuration.DynamicEndpointElement>
