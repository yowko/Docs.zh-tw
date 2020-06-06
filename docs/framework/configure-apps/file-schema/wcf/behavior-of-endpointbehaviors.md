---
title: <behavior> 的 <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "74140807"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="e4297-102">\<behavior> 的 \<endpointBehaviors></span><span class="sxs-lookup"><span data-stu-id="e4297-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="e4297-103">`behavior` 項目包含端點行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="e4297-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="e4297-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="e4297-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="e4297-105">端點可透過這個名稱連結至每一個行為。</span><span class="sxs-lookup"><span data-stu-id="e4297-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="e4297-106">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="e4297-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e4297-107">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="e4297-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**  
  
## <a name="syntax"></a><span data-ttu-id="e4297-108">語法</span><span class="sxs-lookup"><span data-stu-id="e4297-108">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="e4297-109">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="e4297-109">Attributes and Elements</span></span>  
 <span data-ttu-id="e4297-110">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="e4297-110">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="e4297-111">屬性</span><span class="sxs-lookup"><span data-stu-id="e4297-111">Attributes</span></span>  
  
|<span data-ttu-id="e4297-112">屬性</span><span class="sxs-lookup"><span data-stu-id="e4297-112">Attribute</span></span>|<span data-ttu-id="e4297-113">描述</span><span class="sxs-lookup"><span data-stu-id="e4297-113">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="e4297-114">NAME</span><span class="sxs-lookup"><span data-stu-id="e4297-114">name</span></span>|<span data-ttu-id="e4297-115">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="e4297-115">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="e4297-116">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="e4297-116">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="e4297-117">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="e4297-117">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="e4297-118">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="e4297-118">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="e4297-119">子元素</span><span class="sxs-lookup"><span data-stu-id="e4297-119">Child Elements</span></span>  
  
|<span data-ttu-id="e4297-120">元素</span><span class="sxs-lookup"><span data-stu-id="e4297-120">Element</span></span>|<span data-ttu-id="e4297-121">描述</span><span class="sxs-lookup"><span data-stu-id="e4297-121">Description</span></span>|  
|-------------|-----------------|  
|[\<clientCredentials>](clientcredentials.md)|<span data-ttu-id="e4297-122">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="e4297-122">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[\<callbackDebug>](callbackdebug.md)|<span data-ttu-id="e4297-123">指定 Windows Communication Foundation （WCF）回呼物件的服務偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="e4297-123">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[\<callbackTimeouts>](callbacktimeouts.md)|<span data-ttu-id="e4297-124">指定用戶端回呼的逾時。</span><span class="sxs-lookup"><span data-stu-id="e4297-124">Specifies the timeout for the client callback.</span></span>|  
|[\<clientVia>](clientvia.md)|<span data-ttu-id="e4297-125">指定訊息應採用的路徑。</span><span class="sxs-lookup"><span data-stu-id="e4297-125">Specifies the route a message should take.</span></span>|  
|[\<dataContractSerializer>](datacontractserializer.md)|<span data-ttu-id="e4297-126">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="e4297-126">Contains configuration data for the DataContractSerializer.</span></span>|  
|[\<dispatcherSynchronization>](dispatchersynchronization.md)|<span data-ttu-id="e4297-127">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="e4297-127">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[\<enableWebScript>](enablewebscript.md)|<span data-ttu-id="e4297-128">可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="e4297-128">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="e4297-129">行為只能與標準系結或繫結項目搭配使用 \<webHttpBinding> \<webMessageEncoding> 。</span><span class="sxs-lookup"><span data-stu-id="e4297-129">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[\<endpointDiscovery>](endpointdiscovery.md)|<span data-ttu-id="e4297-130">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="e4297-130">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[\<soapProcessing>](soapprocessing.md)|<span data-ttu-id="e4297-131">定義用戶端端點行為，這個行為會用來封送處理不同繫結型別和訊息版本之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="e4297-131">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[\<synchronousReceive>](synchronousreceive-element.md)|<span data-ttu-id="e4297-132">指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="e4297-132">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="e4297-133">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="e4297-133">It does not have any attributes or child elements.</span></span>|  
|[\<transactedBatching>](transactedbatching.md)|<span data-ttu-id="e4297-134">指定是否支援接收作業的交易批次處理。</span><span class="sxs-lookup"><span data-stu-id="e4297-134">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[\<webHttp>](webhttp.md)|<span data-ttu-id="e4297-135">透過組態指定端點上的 WebHttpBehavior。</span><span class="sxs-lookup"><span data-stu-id="e4297-135">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="e4297-136">這個行為與標準系結搭配使用時 \<webHttpBinding> ，會啟用 WCF 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="e4297-136">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="e4297-137">父項目</span><span class="sxs-lookup"><span data-stu-id="e4297-137">Parent Elements</span></span>  
  
|<span data-ttu-id="e4297-138">元素</span><span class="sxs-lookup"><span data-stu-id="e4297-138">Element</span></span>|<span data-ttu-id="e4297-139">描述</span><span class="sxs-lookup"><span data-stu-id="e4297-139">Description</span></span>|  
|-------------|-----------------|  
|[\<endpointBehaviors>](endpointbehaviors.md)|<span data-ttu-id="e4297-140">端點行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="e4297-140">A collection of endpoint behavior elements.</span></span>|
