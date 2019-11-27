---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 41f5b19f5067d9ac7faa2c7329dd07dd9d48e9b3
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430868"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="6f728-101">\<mexNamedPipeBinding ></span><span class="sxs-lookup"><span data-stu-id="6f728-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="6f728-102">指定於具名管道上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="6f728-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
<span data-ttu-id="6f728-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="6f728-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="6f728-104">&nbsp;&nbsp;[ **\<system.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="6f728-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="6f728-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="6f728-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="6f728-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexNamedPipeBinding >**</span><span class="sxs-lookup"><span data-stu-id="6f728-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexNamedPipeBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="6f728-107">語法</span><span class="sxs-lookup"><span data-stu-id="6f728-107">Syntax</span></span>  
  
```xml  
<mexNamedPipeBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexNamedPipeBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="6f728-108">屬性和元素</span><span class="sxs-lookup"><span data-stu-id="6f728-108">Attributes and Elements</span></span>  
 <span data-ttu-id="6f728-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="6f728-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="6f728-110">屬性</span><span class="sxs-lookup"><span data-stu-id="6f728-110">Attributes</span></span>  
  
|<span data-ttu-id="6f728-111">屬性</span><span class="sxs-lookup"><span data-stu-id="6f728-111">Attribute</span></span>|<span data-ttu-id="6f728-112">描述</span><span class="sxs-lookup"><span data-stu-id="6f728-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="6f728-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6f728-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="6f728-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6f728-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6f728-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6f728-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="6f728-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="6f728-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="6f728-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="6f728-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="6f728-118">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="6f728-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="6f728-119">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="6f728-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="6f728-120"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6f728-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="6f728-121">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6f728-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6f728-122">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6f728-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="6f728-123"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6f728-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="6f728-124">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6f728-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6f728-125">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="6f728-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="6f728-126"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="6f728-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="6f728-127">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="6f728-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="6f728-128">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="6f728-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="6f728-129">子元素</span><span class="sxs-lookup"><span data-stu-id="6f728-129">Child Elements</span></span>  
 <span data-ttu-id="6f728-130">None。</span><span class="sxs-lookup"><span data-stu-id="6f728-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="6f728-131">父項目</span><span class="sxs-lookup"><span data-stu-id="6f728-131">Parent Elements</span></span>  
  
|<span data-ttu-id="6f728-132">項目</span><span class="sxs-lookup"><span data-stu-id="6f728-132">Element</span></span>|<span data-ttu-id="6f728-133">描述</span><span class="sxs-lookup"><span data-stu-id="6f728-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="6f728-134">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="6f728-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="6f728-135">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="6f728-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="6f728-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="6f728-136">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="6f728-137">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="6f728-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="6f728-138">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="6f728-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="6f728-139">中繼資料</span><span class="sxs-lookup"><span data-stu-id="6f728-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="6f728-140">繫結</span><span class="sxs-lookup"><span data-stu-id="6f728-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="6f728-141">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="6f728-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="6f728-142">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="6f728-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="6f728-143">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="6f728-143">\<binding></span></span>](bindings.md)
