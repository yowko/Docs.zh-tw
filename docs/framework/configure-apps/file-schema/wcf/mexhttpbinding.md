---
title: <mexHttpBinding>
ms.date: 03/30/2017
ms.assetid: e50b2e1f-9668-41a5-8077-dee7abff9f0f
ms.openlocfilehash: 8d5b9378bf7769754586d0b13f742659aee18f03
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430917"
---
# <a name="mexhttpbinding"></a><span data-ttu-id="9cf67-101">\<mexHttpBinding ></span><span class="sxs-lookup"><span data-stu-id="9cf67-101">\<mexHttpBinding></span></span>
<span data-ttu-id="9cf67-102">指定用於 HTTP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="9cf67-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over HTTP.</span></span>  
  
<span data-ttu-id="9cf67-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="9cf67-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="9cf67-104">&nbsp;&nbsp;[ **\<system.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="9cf67-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="9cf67-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<** ](bindings.md)系結 ></span><span class="sxs-lookup"><span data-stu-id="9cf67-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="9cf67-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<mexHttpBinding >**</span><span class="sxs-lookup"><span data-stu-id="9cf67-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<mexHttpBinding>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9cf67-107">語法</span><span class="sxs-lookup"><span data-stu-id="9cf67-107">Syntax</span></span>  
  
```xml  
<mexHttpBinding>
  <binding closeTimeout="TimeSpan"
           name="string"
           openTimeout="TimeSpan"
           receiveTimeout="TimeSpan"
           sendTimeout="TimeSpan">
  </binding>
</mexHttpBinding>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="9cf67-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="9cf67-108">Attributes and Elements</span></span>  
 <span data-ttu-id="9cf67-109">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="9cf67-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="9cf67-110">屬性</span><span class="sxs-lookup"><span data-stu-id="9cf67-110">Attributes</span></span>  
  
|<span data-ttu-id="9cf67-111">屬性</span><span class="sxs-lookup"><span data-stu-id="9cf67-111">Attribute</span></span>|<span data-ttu-id="9cf67-112">描述</span><span class="sxs-lookup"><span data-stu-id="9cf67-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="9cf67-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9cf67-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="9cf67-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9cf67-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9cf67-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9cf67-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="9cf67-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="9cf67-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="9cf67-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="9cf67-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="9cf67-118">從 .NET Framework 4 開始，系結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="9cf67-118">Starting with .NET Framework 4, bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="9cf67-119">如需預設設定和無相關系結和行為的詳細資訊，請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="9cf67-119">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="9cf67-120"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9cf67-120">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="9cf67-121">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9cf67-121">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9cf67-122">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9cf67-122">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="9cf67-123"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9cf67-123">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="9cf67-124">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9cf67-124">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9cf67-125">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="9cf67-125">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="9cf67-126"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="9cf67-126">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="9cf67-127">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="9cf67-127">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="9cf67-128">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="9cf67-128">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="9cf67-129">子元素</span><span class="sxs-lookup"><span data-stu-id="9cf67-129">Child Elements</span></span>  
 <span data-ttu-id="9cf67-130">無。</span><span class="sxs-lookup"><span data-stu-id="9cf67-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="9cf67-131">父項目</span><span class="sxs-lookup"><span data-stu-id="9cf67-131">Parent Elements</span></span>  
  
|<span data-ttu-id="9cf67-132">項目</span><span class="sxs-lookup"><span data-stu-id="9cf67-132">Element</span></span>|<span data-ttu-id="9cf67-133">描述</span><span class="sxs-lookup"><span data-stu-id="9cf67-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="9cf67-134">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="9cf67-134">\<bindings></span></span>](bindings.md)|<span data-ttu-id="9cf67-135">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="9cf67-135">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9cf67-136">備註</span><span class="sxs-lookup"><span data-stu-id="9cf67-136">Remarks</span></span>  
 <span data-ttu-id="9cf67-137">這個繫結實質上是停用安全性的 `WSHttpBinding` 繫結。</span><span class="sxs-lookup"><span data-stu-id="9cf67-137">This binding is essentially a `WSHttpBinding` binding with security disabled.</span></span> <span data-ttu-id="9cf67-138">它支援大部分的中繼資料要求。</span><span class="sxs-lookup"><span data-stu-id="9cf67-138">It supports most metadata requests.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9cf67-139">請參閱</span><span class="sxs-lookup"><span data-stu-id="9cf67-139">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexHttpBinding%2A>
- <xref:System.ServiceModel.Configuration.MexHttpBindingElement>
- [<span data-ttu-id="9cf67-140">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="9cf67-140">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="9cf67-141">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="9cf67-141">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="9cf67-142">中繼資料</span><span class="sxs-lookup"><span data-stu-id="9cf67-142">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="9cf67-143">繫結</span><span class="sxs-lookup"><span data-stu-id="9cf67-143">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="9cf67-144">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="9cf67-144">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="9cf67-145">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="9cf67-145">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="9cf67-146">\<系結 ></span><span class="sxs-lookup"><span data-stu-id="9cf67-146">\<binding></span></span>](bindings.md)
