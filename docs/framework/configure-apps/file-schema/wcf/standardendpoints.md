---
title: <standardEndpoints>
ms.date: 03/30/2017
ms.assetid: d62153d7-a6e6-462a-a784-cca61e9c2ba1
ms.openlocfilehash: 76a5303650c4e2b2887d29f511d3088c78b58fe2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70399518"
---
# \<standardEndpoints>
<span data-ttu-id="1dd52-101">這個組態區段可讓您定義標準端點的集合，這些端點是可重複使用的預先設定端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-101">This configuration section allows you to define a collection of standard endpoints, which are reusable preconfigured endpoints.</span></span> <span data-ttu-id="1dd52-102">標準端點會有一個或多個位址、繫結，以及設為固定值的合約屬性。</span><span class="sxs-lookup"><span data-stu-id="1dd52-102">A standard endpoint will have one or more of the address, binding and contract attributes set to a fixed value.</span></span> <span data-ttu-id="1dd52-103">例如，探索端點中的合約是固定的。</span><span class="sxs-lookup"><span data-stu-id="1dd52-103">For example, in the discovery endpoint the contract is fixed.</span></span> <span data-ttu-id="1dd52-104">您也可以使用標準端點，以類似定義自訂繫結的新屬性擴充服務端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-104">You can also use standard endpoints to extend service endpoint with new properties similar to defining custom bindings.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;**\<standardEndpoints>**  
  
## <a name="syntax"></a><span data-ttu-id="1dd52-105">語法</span><span class="sxs-lookup"><span data-stu-id="1dd52-105">Syntax</span></span>  
  
```xml  
<system.serviceModel>
  <standardEndpoints>
  </standardEndpoints>
</system.serviceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="1dd52-106">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="1dd52-106">Attributes and Elements</span></span>  
 <span data-ttu-id="1dd52-107">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="1dd52-107">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="1dd52-108">屬性</span><span class="sxs-lookup"><span data-stu-id="1dd52-108">Attributes</span></span>  
 <span data-ttu-id="1dd52-109">無。</span><span class="sxs-lookup"><span data-stu-id="1dd52-109">None.</span></span>  
  
### <a name="child-elements"></a><span data-ttu-id="1dd52-110">子元素</span><span class="sxs-lookup"><span data-stu-id="1dd52-110">Child Elements</span></span>  
  
|<span data-ttu-id="1dd52-111">元素</span><span class="sxs-lookup"><span data-stu-id="1dd52-111">Element</span></span>|<span data-ttu-id="1dd52-112">描述</span><span class="sxs-lookup"><span data-stu-id="1dd52-112">Description</span></span>|  
|-------------|-----------------|  
|[\<announcementEndpoint>](announcementendpoint.md)|<span data-ttu-id="1dd52-113">定義具有固定公告合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-113">Defines a standard endpoint with a fixed announcement contract.</span></span> <span data-ttu-id="1dd52-114">服務可以選擇性地公告其可用性，方法是分別在開啟與關閉該服務時傳送線上及離線公告訊息。</span><span class="sxs-lookup"><span data-stu-id="1dd52-114">A service can optionally announce its availability by sending an online and offline announcement message when it is opened or closed respectively.</span></span> <span data-ttu-id="1dd52-115">Windows Communication Foundation （WCF）服務會在元素中指定公告端點 [\<serviceDiscovery>](servicediscovery.md) ，並使用 AnnouncementClient 來執行公告。</span><span class="sxs-lookup"><span data-stu-id="1dd52-115">A Windows Communication Foundation (WCF) service specifies the announcement endpoints in the [\<serviceDiscovery>](servicediscovery.md) element and uses the AnnouncementClient to perform the announcements.</span></span> <span data-ttu-id="1dd52-116">想要接聽來自其他服務之公告的用戶端實際上是作為 WCF 服務;因此，您必須在區段中設定該用戶端的宣告端點 [\<services>](services.md) 。</span><span class="sxs-lookup"><span data-stu-id="1dd52-116">A client wishing to listen for the announcement from other service is actually acting as a WCF service; thus you have to configure the announcement endpoints for that client in the [\<services>](services.md) section.</span></span>|  
|[\<discoveryEndpoint>](discoveryendpoint.md)|<span data-ttu-id="1dd52-117">定義具有固定探索合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-117">Defines a standard endpoint with a fixed discovery contract.</span></span> <span data-ttu-id="1dd52-118">加入至服務組態時，此組態項目會指定接聽探索訊息的位置。</span><span class="sxs-lookup"><span data-stu-id="1dd52-118">When added to the service configuration, it specifies where to listen for the discovery messages.</span></span> <span data-ttu-id="1dd52-119">加入至用戶端組態時，此組態項目會指定傳送探索查詢的位置。</span><span class="sxs-lookup"><span data-stu-id="1dd52-119">When added to the client configuration it specifies where to send the discovery queries.</span></span>|  
|[\<dynamicEndpoint>](dynamicendpoint.md)|<span data-ttu-id="1dd52-120">這個組態項目定義標準端點，其中包含的資訊可讓您啟用應用程式做為用戶端程式，在執行階段時動態尋找端點位址。</span><span class="sxs-lookup"><span data-stu-id="1dd52-120">This configuration element defines a standard endpoint that contains information to enable an application to function as a client program that can find the endpoint address dynamically at runtime.</span></span>|  
|[\<mexEndpoint>](mexendpoint.md)|<span data-ttu-id="1dd52-121">定義具有固定 IMetadataExchange 合約的標準端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-121">Defines a standard endpoint with a fixed IMetadataExchange contract.</span></span> <span data-ttu-id="1dd52-122">由於所有中繼資料交換端點都指定 IMetadataExchange 做為它們的合約，因此您可以使用這個標準端點，而不需自行定義端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-122">Since all metadata exchange endpoints specify IMetadataExchange as their contract, you can use this standard point instead of defining one for yourself.</span></span>|  
|[\<udpAnnouncementEndpoint>](udpannouncementendpoint.md)|<span data-ttu-id="1dd52-123">定義標準端點，此端點可為在 UDP 繫結上傳送公告訊息的服務使用。</span><span class="sxs-lookup"><span data-stu-id="1dd52-123">Defines a standard endpoint that is used by services to send announcement messages over a UDP binding.</span></span> <span data-ttu-id="1dd52-124">此端點具備固定合約，而且支援兩種探索版本。</span><span class="sxs-lookup"><span data-stu-id="1dd52-124">It has a fixed contract and supports two discovery versions.</span></span> <span data-ttu-id="1dd52-125">此外，它擁有固定的 UDP 繫結和預設位址值，如 WS-Discovery 規格 (WS-Discovery 2005 年 4 月或 WS-Discovery 1.1 版) 中所指定。</span><span class="sxs-lookup"><span data-stu-id="1dd52-125">In addition it has a fixed UDP binding and a default address value as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery version 1.1).</span></span> <span data-ttu-id="1dd52-126">您可以指定傳送及接收公告訊息時所使用的多點傳送位址。</span><span class="sxs-lookup"><span data-stu-id="1dd52-126">You can specify the multicast address to use for sending and receiving the announcement messages.</span></span>|  
|[\<udpDiscoveryEndpoint>](udpdiscoveryendpoint.md)|<span data-ttu-id="1dd52-127">定義標準端點，該端點已預先設定透過 UDP 多點傳送繫結進行探索作業。</span><span class="sxs-lookup"><span data-stu-id="1dd52-127">Defines a standard endpoint that is pre-configured for discovery operations over a UDP multicast binding.</span></span> <span data-ttu-id="1dd52-128">此端點具備固定合約，而且支援兩種 WS-Discovery 通訊協定版本。</span><span class="sxs-lookup"><span data-stu-id="1dd52-128">This endpoint has a fixed contract and supports two WS-Discovery protocol versions.</span></span> <span data-ttu-id="1dd52-129">此外，它擁有固定的 UDP 繫結和預設位址，如 WS-Discovery 規格 (WS-Discovery 2005 年 4 月或 WS-Discovery V1.1) 中所指定。</span><span class="sxs-lookup"><span data-stu-id="1dd52-129">In addition, it has a fixed UDP binding and a default address as specified in the WS-Discovery specifications (WS-Discovery April 2005 or WS-Discovery V1.1).</span></span>|  
|[\<webHttpEndpoint>](webhttpendpoint.md)|<span data-ttu-id="1dd52-130">定義具有固定系結的標準端點 [\<webHttpBinding>](webhttpbinding.md) ，此系結會自動加入 [\<webHttp>](webhttp.md) 行為。</span><span class="sxs-lookup"><span data-stu-id="1dd52-130">Defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<webHttp>](webhttp.md) behavior.</span></span> <span data-ttu-id="1dd52-131">撰寫 REST 服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-131">Use this endpoint when writing a REST service.</span></span>|  
|[\<webScriptEndpoint>](webscriptendpoint.md)|<span data-ttu-id="1dd52-132">定義具有固定系結的標準端點 [\<webHttpBinding>](webhttpbinding.md) ，此系結會自動加入 [\<enableWebScript>](enablewebscript.md) 行為。</span><span class="sxs-lookup"><span data-stu-id="1dd52-132">Defines a standard endpoint with a fixed [\<webHttpBinding>](webhttpbinding.md) binding that automatically adds the [\<enableWebScript>](enablewebscript.md) behavior.</span></span> <span data-ttu-id="1dd52-133">撰寫從 ASP.NET AJAX 應用程式呼叫的服務時，請使用這個端點。</span><span class="sxs-lookup"><span data-stu-id="1dd52-133">Use this endpoint when you are writing a service that is called from an ASP.NET AJAX application.</span></span>|  
|[\<workflowControlEndpoint>](workflowcontrolendpoint.md)|<span data-ttu-id="1dd52-134">定義一個標準端點，用於控制工作流程執行個體 (建立、執行、暫停、終止等) 的執行。</span><span class="sxs-lookup"><span data-stu-id="1dd52-134">Defines a standard endpoint for controlling the execution of workflow instances (create, run, suspend, terminate, etc).</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="1dd52-135">父項目</span><span class="sxs-lookup"><span data-stu-id="1dd52-135">Parent Elements</span></span>  
  
|<span data-ttu-id="1dd52-136">元素</span><span class="sxs-lookup"><span data-stu-id="1dd52-136">Element</span></span>|<span data-ttu-id="1dd52-137">描述</span><span class="sxs-lookup"><span data-stu-id="1dd52-137">Description</span></span>|  
|-------------|-----------------|  
|\<system.ServiceModel>|<span data-ttu-id="1dd52-138">所有 WCF 組態項目的根項目。</span><span class="sxs-lookup"><span data-stu-id="1dd52-138">The root element of all WCF configuration elements.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="1dd52-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="1dd52-139">See also</span></span>

- [<span data-ttu-id="1dd52-140">標準端點</span><span class="sxs-lookup"><span data-stu-id="1dd52-140">Standard Endpoints</span></span>](../../../wcf/feature-details/standard-endpoints.md)
