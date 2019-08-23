---
title: <mexTcpBinding>
ms.date: 03/30/2017
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
ms.openlocfilehash: 491597da508487c3988b284c84411123d434fe72
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69932524"
---
# <a name="mextcpbinding"></a><span data-ttu-id="f1147-101">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f1147-101">\<mexTcpBinding></span></span>
<span data-ttu-id="f1147-102">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="f1147-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="f1147-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="f1147-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="f1147-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f1147-104">\<bindings></span></span>  
<span data-ttu-id="f1147-105">\<mexTcpBinding></span><span class="sxs-lookup"><span data-stu-id="f1147-105">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f1147-106">語法</span><span class="sxs-lookup"><span data-stu-id="f1147-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f1147-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f1147-107">Attributes and Elements</span></span>  
 <span data-ttu-id="f1147-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="f1147-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f1147-109">屬性</span><span class="sxs-lookup"><span data-stu-id="f1147-109">Attributes</span></span>  
  
|<span data-ttu-id="f1147-110">屬性</span><span class="sxs-lookup"><span data-stu-id="f1147-110">Attribute</span></span>|<span data-ttu-id="f1147-111">說明</span><span class="sxs-lookup"><span data-stu-id="f1147-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="f1147-112"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f1147-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="f1147-113">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f1147-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f1147-114">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f1147-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="f1147-115">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="f1147-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="f1147-116">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="f1147-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="f1147-117">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="f1147-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="f1147-118">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="f1147-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="f1147-119">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="f1147-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="f1147-120">如需預設設定和無相關系結和行為的詳細資訊, 請參閱[簡化](../../../wcf/simplified-configuration.md)的設定和[WCF 服務的簡化](../../../wcf/samples/simplified-configuration-for-wcf-services.md)設定。</span><span class="sxs-lookup"><span data-stu-id="f1147-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="f1147-121"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f1147-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="f1147-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f1147-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f1147-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f1147-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="f1147-124"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f1147-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="f1147-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f1147-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f1147-126">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="f1147-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="f1147-127"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="f1147-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="f1147-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="f1147-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="f1147-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="f1147-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f1147-130">子元素</span><span class="sxs-lookup"><span data-stu-id="f1147-130">Child Elements</span></span>  
 <span data-ttu-id="f1147-131">無。</span><span class="sxs-lookup"><span data-stu-id="f1147-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f1147-132">父項目</span><span class="sxs-lookup"><span data-stu-id="f1147-132">Parent Elements</span></span>  
  
|<span data-ttu-id="f1147-133">項目</span><span class="sxs-lookup"><span data-stu-id="f1147-133">Element</span></span>|<span data-ttu-id="f1147-134">說明</span><span class="sxs-lookup"><span data-stu-id="f1147-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f1147-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="f1147-135">\<bindings></span></span>](bindings.md)|<span data-ttu-id="f1147-136">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="f1147-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="f1147-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f1147-137">See also</span></span>

- <xref:System.ServiceModel.Configuration.MexTcpBindingElement>
- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>
- [<span data-ttu-id="f1147-138">如何：使用設定檔發佈服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f1147-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="f1147-139">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="f1147-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="f1147-140">中繼資料</span><span class="sxs-lookup"><span data-stu-id="f1147-140">Metadata</span></span>](../../../wcf/feature-details/metadata.md)
- [<span data-ttu-id="f1147-141">繫結</span><span class="sxs-lookup"><span data-stu-id="f1147-141">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f1147-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="f1147-142">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f1147-143">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="f1147-143">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f1147-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="f1147-144">\<binding></span></span>](../../../misc/binding.md)
