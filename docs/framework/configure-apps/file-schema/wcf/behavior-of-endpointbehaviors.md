---
title: <behavior> 的 <endpointBehaviors>
ms.date: 03/30/2017
ms.assetid: b90ca3bc-3c22-4174-b903-e3a39898bd27
ms.openlocfilehash: 489678a5adeae3965acae90a847c4b087478354d
ms.sourcegitcommit: fbb8a593a511ce667992502a3ce6d8f65c594edf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/16/2019
ms.locfileid: "74140807"
---
# <a name="behavior-of-endpointbehaviors"></a><span data-ttu-id="ef764-102">\<endpointBehaviors 的 \<行為 > ></span><span class="sxs-lookup"><span data-stu-id="ef764-102">\<behavior> of \<endpointBehaviors></span></span>
<span data-ttu-id="ef764-103">`behavior` 項目包含端點行為之設定的集合。</span><span class="sxs-lookup"><span data-stu-id="ef764-103">The `behavior` element contains a collection of settings for the behavior of an endpoint.</span></span> <span data-ttu-id="ef764-104">各個行為是依其 `name` 進行索引。</span><span class="sxs-lookup"><span data-stu-id="ef764-104">Each behavior is indexed by its `name`.</span></span> <span data-ttu-id="ef764-105">端點可透過這個名稱連結至每一個行為。</span><span class="sxs-lookup"><span data-stu-id="ef764-105">Endpoints can link to each behavior through this name.</span></span> <span data-ttu-id="ef764-106">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="ef764-106">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ef764-107">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="ef764-107">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>  
  
<span data-ttu-id="ef764-108">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="ef764-108">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="ef764-109">&nbsp; &nbsp;[ **\<system system.servicemodel >** ](system-servicemodel.md) </span><span class="sxs-lookup"><span data-stu-id="ef764-109">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="ef764-110">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<行為 >** ](behaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ef764-110">&nbsp;&nbsp;&nbsp;&nbsp;[**\<behaviors>**](behaviors.md)</span></span>\
<span data-ttu-id="ef764-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<endpointBehaviors >** ](endpointbehaviors.md)</span><span class="sxs-lookup"><span data-stu-id="ef764-111">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<endpointBehaviors>**](endpointbehaviors.md)</span></span>\
<span data-ttu-id="ef764-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<行為 >**</span><span class="sxs-lookup"><span data-stu-id="ef764-112">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<behavior>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ef764-113">語法</span><span class="sxs-lookup"><span data-stu-id="ef764-113">Syntax</span></span>  
  
```xml  
<system.ServiceModel>
  <behaviors>
    <endpointBehaviors>
      <behavior name="String" />
    </endpointBehaviors>
  </behaviors>
</system.ServiceModel>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="ef764-114">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="ef764-114">Attributes and Elements</span></span>  
 <span data-ttu-id="ef764-115">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="ef764-115">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="ef764-116">屬性</span><span class="sxs-lookup"><span data-stu-id="ef764-116">Attributes</span></span>  
  
|<span data-ttu-id="ef764-117">屬性</span><span class="sxs-lookup"><span data-stu-id="ef764-117">Attribute</span></span>|<span data-ttu-id="ef764-118">描述</span><span class="sxs-lookup"><span data-stu-id="ef764-118">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="ef764-119">NAME</span><span class="sxs-lookup"><span data-stu-id="ef764-119">name</span></span>|<span data-ttu-id="ef764-120">唯一的字串，其中包含行為的組態名稱。</span><span class="sxs-lookup"><span data-stu-id="ef764-120">A unique string that contains the configuration name of the behavior.</span></span> <span data-ttu-id="ef764-121">這個值是使用者定義的字串，它必須是唯一的，因為它會充當項目的識別字串。</span><span class="sxs-lookup"><span data-stu-id="ef764-121">This value is a user-defined string that must be unique, since it acts as the identification string for the element.</span></span> <span data-ttu-id="ef764-122">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="ef764-122">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="ef764-123">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="ef764-123">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="ef764-124">子項目</span><span class="sxs-lookup"><span data-stu-id="ef764-124">Child Elements</span></span>  
  
|<span data-ttu-id="ef764-125">項目</span><span class="sxs-lookup"><span data-stu-id="ef764-125">Element</span></span>|<span data-ttu-id="ef764-126">描述</span><span class="sxs-lookup"><span data-stu-id="ef764-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef764-127">\<clientCredentials ></span><span class="sxs-lookup"><span data-stu-id="ef764-127">\<clientCredentials></span></span>](clientcredentials.md)|<span data-ttu-id="ef764-128">指定用來對服務驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="ef764-128">Specifies the credentials used to authenticate the client to a service.</span></span>|  
|[<span data-ttu-id="ef764-129">\<callbackDebug ></span><span class="sxs-lookup"><span data-stu-id="ef764-129">\<callbackDebug></span></span>](callbackdebug.md)|<span data-ttu-id="ef764-130">指定 Windows Communication Foundation （WCF）回呼物件的服務偵錯工具。</span><span class="sxs-lookup"><span data-stu-id="ef764-130">Specifies service debugging for a Windows Communication Foundation (WCF) callback object.</span></span>|  
|[<span data-ttu-id="ef764-131">\<callbackTimeouts ></span><span class="sxs-lookup"><span data-stu-id="ef764-131">\<callbackTimeouts></span></span>](callbacktimeouts.md)|<span data-ttu-id="ef764-132">指定用戶端回呼的逾時。</span><span class="sxs-lookup"><span data-stu-id="ef764-132">Specifies the timeout for the client callback.</span></span>|  
|[<span data-ttu-id="ef764-133">\<clientVia ></span><span class="sxs-lookup"><span data-stu-id="ef764-133">\<clientVia></span></span>](clientvia.md)|<span data-ttu-id="ef764-134">指定訊息應採用的路徑。</span><span class="sxs-lookup"><span data-stu-id="ef764-134">Specifies the route a message should take.</span></span>|  
|[<span data-ttu-id="ef764-135">\<dataContractSerializer ></span><span class="sxs-lookup"><span data-stu-id="ef764-135">\<dataContractSerializer></span></span>](datacontractserializer.md)|<span data-ttu-id="ef764-136">包含 DataContractSerializer 的組態資料。</span><span class="sxs-lookup"><span data-stu-id="ef764-136">Contains configuration data for the DataContractSerializer.</span></span>|  
|[<span data-ttu-id="ef764-137">\<dispatcherSynchronization ></span><span class="sxs-lookup"><span data-stu-id="ef764-137">\<dispatcherSynchronization></span></span>](dispatchersynchronization.md)|<span data-ttu-id="ef764-138">指定可讓服務以非同步方式傳送回覆的端點行為。</span><span class="sxs-lookup"><span data-stu-id="ef764-138">Specifies an endpoint behavior that enables a service to send replies asynchronously.</span></span>|  
|[<span data-ttu-id="ef764-139">\<enableWebScript ></span><span class="sxs-lookup"><span data-stu-id="ef764-139">\<enableWebScript></span></span>](enablewebscript.md)|<span data-ttu-id="ef764-140">可啟用端點行為，以取用 ASP.NET AJAX 網頁上的服務。</span><span class="sxs-lookup"><span data-stu-id="ef764-140">Enables the endpoint behavior that makes it possible to consume the service from ASP.NET AJAX web pages.</span></span> <span data-ttu-id="ef764-141">行為只能與 \<webHttpBinding > 標準系結或 \<webMessageEncoding > 繫結項目搭配使用。</span><span class="sxs-lookup"><span data-stu-id="ef764-141">The behavior should only be used in conjunction with either the \<webHttpBinding> standard binding, or the \<webMessageEncoding> binding element.</span></span>|  
|[<span data-ttu-id="ef764-142">\<endpointDiscovery ></span><span class="sxs-lookup"><span data-stu-id="ef764-142">\<endpointDiscovery></span></span>](endpointdiscovery.md)|<span data-ttu-id="ef764-143">指定端點的各種探索設定，例如其探索能力、範圍以及中繼資料的任何自訂延伸模組。</span><span class="sxs-lookup"><span data-stu-id="ef764-143">Specifies the various discovery settings for an endpoint, such as its discoverability, scopes, and any custom extensions to its metadata.</span></span>|  
|[<span data-ttu-id="ef764-144">\<soapProcessing ></span><span class="sxs-lookup"><span data-stu-id="ef764-144">\<soapProcessing></span></span>](soapprocessing.md)|<span data-ttu-id="ef764-145">定義用戶端端點行為，這個行為會用來封送處理不同繫結型別和訊息版本之間的訊息。</span><span class="sxs-lookup"><span data-stu-id="ef764-145">Defines the client endpoint behavior used to marshal messages between different binding types and message versions.</span></span>|  
|[<span data-ttu-id="ef764-146">\<synchronousReceive ></span><span class="sxs-lookup"><span data-stu-id="ef764-146">\<synchronousReceive></span></span>](synchronousreceive-element.md)|<span data-ttu-id="ef764-147">指定在服務或用戶端應用程式中接收訊息的執行階段行為。</span><span class="sxs-lookup"><span data-stu-id="ef764-147">Specifies run-time behavior for receiving messages in either a service or client application.</span></span> <span data-ttu-id="ef764-148">它沒有任何屬性或子項目。</span><span class="sxs-lookup"><span data-stu-id="ef764-148">It does not have any attributes or child elements.</span></span>|  
|[<span data-ttu-id="ef764-149">\<transactedBatching ></span><span class="sxs-lookup"><span data-stu-id="ef764-149">\<transactedBatching></span></span>](transactedbatching.md)|<span data-ttu-id="ef764-150">指定是否支援接收作業的交易批次處理。</span><span class="sxs-lookup"><span data-stu-id="ef764-150">Specifies whether transaction batching is supported for receive operations.</span></span>|  
|[<span data-ttu-id="ef764-151">\<webHttp ></span><span class="sxs-lookup"><span data-stu-id="ef764-151">\<webHttp></span></span>](webhttp.md)|<span data-ttu-id="ef764-152">透過組態指定端點上的 WebHttpBehavior。</span><span class="sxs-lookup"><span data-stu-id="ef764-152">Specifies the WebHttpBehavior on an endpoint through configuration.</span></span> <span data-ttu-id="ef764-153">這個行為與 \<webHttpBinding > 標準系結搭配使用時，會啟用 WCF 服務的 Web 程式設計模型。</span><span class="sxs-lookup"><span data-stu-id="ef764-153">This behavior, when used in conjunction with the \<webHttpBinding> standard binding, enables the Web programming model for a WCF service.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="ef764-154">父項目</span><span class="sxs-lookup"><span data-stu-id="ef764-154">Parent Elements</span></span>  
  
|<span data-ttu-id="ef764-155">項目</span><span class="sxs-lookup"><span data-stu-id="ef764-155">Element</span></span>|<span data-ttu-id="ef764-156">描述</span><span class="sxs-lookup"><span data-stu-id="ef764-156">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="ef764-157">\<endpointBehaviors ></span><span class="sxs-lookup"><span data-stu-id="ef764-157">\<endpointBehaviors></span></span>](endpointbehaviors.md)|<span data-ttu-id="ef764-158">端點行為項目的集合。</span><span class="sxs-lookup"><span data-stu-id="ef764-158">A collection of endpoint behavior elements.</span></span>|
