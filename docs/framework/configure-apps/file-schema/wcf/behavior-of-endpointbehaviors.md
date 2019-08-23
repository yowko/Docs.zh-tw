---
title: <behavior> 的 <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: f14e80798a9b088508f23d718c8b386286ad65a3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69919848"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="62f53-102">\<endpointBehaviors > 的\<行為 ></span><span class="sxs-lookup"><span data-stu-id="62f53-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="62f53-103">`behavior` 項目包含端點行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="62f53-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="62f53-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="62f53-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="62f53-105">端點可透過這個名稱連結至每一個行為。</span><span class="sxs-lookup"><span data-stu-id="62f53-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="62f53-106">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="62f53-106">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="62f53-107">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="62f53-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
 <span data-ttu-id="62f53-108">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="62f53-108">\<system.ServiceModel></span></span>  
<span data-ttu-id="62f53-109">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="62f53-109">\<behaviors></span></span>  
<span data-ttu-id="62f53-110">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="62f53-110">\<endpointBehaviors></span></span>  
<span data-ttu-id="62f53-111">\<行為 ></span><span class="sxs-lookup"><span data-stu-id="62f53-111">\<behavior></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62f53-112">語法</span><span class="sxs-lookup"><span data-stu-id="62f53-112">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="62f53-113">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="62f53-113">Attributes and Elements</span></span>  
 <span data-ttu-id="62f53-114">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="62f53-114">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="62f53-115">屬性</span><span class="sxs-lookup"><span data-stu-id="62f53-115">Attributes</span></span>  
  
|<span data-ttu-id="62f53-116">屬性</span><span class="sxs-lookup"><span data-stu-id="62f53-116">Attribute</span></span>|<span data-ttu-id="62f53-117">說明</span><span class="sxs-lookup"><span data-stu-id="62f53-117">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="62f53-118">NAME</span><span class="sxs-lookup"><span data-stu-id="62f53-118">name</span></span>|<span data-ttu-id="62f53-119">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="62f53-119">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="62f53-120">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="62f53-120">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="62f53-121">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="62f53-121">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="62f53-122">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="62f53-122">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="62f53-123">子元素</span><span class="sxs-lookup"><span data-stu-id="62f53-123">Child Elements</span></span>  
  
|<span data-ttu-id="62f53-124">項目</span><span class="sxs-lookup"><span data-stu-id="62f53-124">Element</span></span>|<span data-ttu-id="62f53-125">描述</span><span class="sxs-lookup"><span data-stu-id="62f53-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62f53-126">\<clientCredentials></span><span class="sxs-lookup"><span data-stu-id="62f53-126">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="62f53-127">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="62f53-127">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[<span data-ttu-id="62f53-128">\<callbackDebug></span><span class="sxs-lookup"><span data-stu-id="62f53-128">\<callbackDebug></span></span>](callbackdebug.md)|<span data-ttu-id="62f53-129">指定 Windows Communication Foundation (WCF) 回呼物件的服務偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="62f53-129">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[<span data-ttu-id="62f53-130">\<callbackTimeouts></span><span class="sxs-lookup"><span data-stu-id="62f53-130">\<callbackTimeouts></span></span>](callbacktimeouts.md)|<span data-ttu-id="62f53-131">指定用戶端回呼的逾時。</span><span class="sxs-lookup"><span data-stu-id="62f53-131">Specifies the timeout for the client callback.</span></span>|  
|[<span data-ttu-id="62f53-132">\<clientVia></span><span class="sxs-lookup"><span data-stu-id="62f53-132">\<clientVia></span></span>](clientvia.md)|<span data-ttu-id="62f53-133">指定訊息應採用的路徑。</span><span class="sxs-lookup"><span data-stu-id="62f53-133">Specifies the route a message should take.</span></span>|  
|[<span data-ttu-id="62f53-134">\<dataContractSerializer></span><span class="sxs-lookup"><span data-stu-id="62f53-134">\<dataContractSerializer></span></span>](datacontractserializer.md)|<span data-ttu-id="62f53-135">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="62f53-135">Contains configuration data for the DataContractSerializer.</span></span>|  
|[<span data-ttu-id="62f53-136">\<dispatcherSynchronization></span><span class="sxs-lookup"><span data-stu-id="62f53-136">\<dispatcherSynchronization></span></span>](dispatchersynchronization.md)|<span data-ttu-id="62f53-137">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="62f53-137">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[<span data-ttu-id="62f53-138">\<enableWebScript></span><span class="sxs-lookup"><span data-stu-id="62f53-138">\<enableWebScript></span></span>](enablewebscript.md)|<span data-ttu-id="62f53-139">可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="62f53-139">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="62f53-140">行為應該只與\<webHttpBinding > 標準系結\<或 webMessageEncoding > 繫結項目搭配使用。</span><span class="sxs-lookup"><span data-stu-id="62f53-140">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[<span data-ttu-id="62f53-141">\<endpointDiscovery></span><span class="sxs-lookup"><span data-stu-id="62f53-141">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="62f53-142">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="62f53-142">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[<span data-ttu-id="62f53-143">\<soapProcessing></span><span class="sxs-lookup"><span data-stu-id="62f53-143">\<soapProcessing></span></span>](soapprocessing.md)|<span data-ttu-id="62f53-144">定義用戶端端點行為，這個行為會用來封送處理不同繫結型別和訊息版本之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="62f53-144">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[<span data-ttu-id="62f53-145">\<synchronousReceive></span><span class="sxs-lookup"><span data-stu-id="62f53-145">\<synchronousReceive></span></span>](synchronousreceive-element.md)|<span data-ttu-id="62f53-146">指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="62f53-146">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="62f53-147">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="62f53-147">It does not have any attributes or child elements.</span></span>|  
|[<span data-ttu-id="62f53-148">\<transactedBatching></span><span class="sxs-lookup"><span data-stu-id="62f53-148">\<transactedBatching></span></span>](transactedbatching.md)|<span data-ttu-id="62f53-149">指定是否支援接收作業的交易批次處理。</span><span class="sxs-lookup"><span data-stu-id="62f53-149">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[<span data-ttu-id="62f53-150">\<webHttp></span><span class="sxs-lookup"><span data-stu-id="62f53-150">\<webHttp></span></span>](webhttp.md)|<span data-ttu-id="62f53-151">透過組態指定端點上的 WebHttpBehavior。</span><span class="sxs-lookup"><span data-stu-id="62f53-151">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="62f53-152">這個行為與\<webHttpBinding > 標準系結搭配使用時, 會啟用 WCF 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="62f53-152">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="62f53-153">父項目</span><span class="sxs-lookup"><span data-stu-id="62f53-153">Parent Elements</span></span>  
  
|<span data-ttu-id="62f53-154">項目</span><span class="sxs-lookup"><span data-stu-id="62f53-154">Element</span></span>|<span data-ttu-id="62f53-155">說明</span><span class="sxs-lookup"><span data-stu-id="62f53-155">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="62f53-156">\<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="62f53-156">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="62f53-157">端點行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="62f53-157">A collection of endpoint behavior elements.</span></span>|
