---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 8d0ae2a1848eaf28c2e408542b8209cf968de4c1
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430299"
---
# <a name="mextcpbinding"></a><span data-ttu-id="f65e1-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f65e1-101">\<mexTcpBinding></span></span>
<span data-ttu-id="f65e1-102">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="f65e1-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
<span data-ttu-id="f65e1-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f65e1-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f65e1-104">&nbsp;&nbsp;[ **\<system.serviceModel>** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f65e1-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f65e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<bindings>** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f65e1-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f65e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexTcpBinding>**</span><span class="sxs-lookup"><span data-stu-id="f65e1-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexTcpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f65e1-107">語法</span><span class="sxs-lookup"><span data-stu-id="f65e1-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexTcpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f65e1-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f65e1-108">Attributes and Elements</span></span>  
 <span data-ttu-id="f65e1-109">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f65e1-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f65e1-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f65e1-110">Attributes</span></span>  
  
|<span data-ttu-id="f65e1-111">屬性</span><span class="sxs-lookup"><span data-stu-id="f65e1-111">Attribute</span></span>|<span data-ttu-id="f65e1-112">描述</span><span class="sxs-lookup"><span data-stu-id="f65e1-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f65e1-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f65e1-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f65e1-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f65e1-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f65e1-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f65e1-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f65e1-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="f65e1-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f65e1-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="f65e1-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f65e1-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span><span class="sxs-lookup"><span data-stu-id="f65e1-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f65e1-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span><span class="sxs-lookup"><span data-stu-id="f65e1-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f65e1-120"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f65e1-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f65e1-121">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f65e1-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f65e1-122">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f65e1-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f65e1-123"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f65e1-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f65e1-124">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f65e1-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f65e1-125">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="f65e1-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f65e1-126"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f65e1-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f65e1-127">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f65e1-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f65e1-128">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f65e1-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f65e1-129">子項目</span><span class="sxs-lookup"><span data-stu-id="f65e1-129">Child Elements</span></span>  
 <span data-ttu-id="f65e1-130">無。</span><span class="sxs-lookup"><span data-stu-id="f65e1-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f65e1-131">父項目</span><span class="sxs-lookup"><span data-stu-id="f65e1-131">Parent Elements</span></span>  
  
|<span data-ttu-id="f65e1-132">項目</span><span class="sxs-lookup"><span data-stu-id="f65e1-132">Element</span></span>|<span data-ttu-id="f65e1-133">描述</span><span class="sxs-lookup"><span data-stu-id="f65e1-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f65e1-134">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f65e1-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f65e1-135">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="f65e1-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f65e1-136">請參閱</span><span class="sxs-lookup"><span data-stu-id="f65e1-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="f65e1-137">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f65e1-137">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f65e1-138">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f65e1-138">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="f65e1-139">中繼資料</span><span class="sxs-lookup"><span data-stu-id="f65e1-139">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="f65e1-140">繫結</span><span class="sxs-lookup"><span data-stu-id="f65e1-140">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f65e1-141">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="f65e1-141">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f65e1-142">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="f65e1-142">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f65e1-143">\<binding></span><span class="sxs-lookup"><span data-stu-id="f65e1-143">\<binding></span></span>](bindings.md)
