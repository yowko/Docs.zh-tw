---
title: <mexNamedPipeBinding>
ms.date: 03/30/2017
ms.assetid: 193412fa-3260-414c-92c6-b32ed3b94a34
ms.openlocfilehash: 9ac2b967e33571cbe0b4ad5ee81e13b009ffddd3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111354"
---
# <a name="mexnamedpipebinding"></a><span data-ttu-id="d8a9a-101">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d8a9a-101">\<mexNamedPipeBinding></span></span>
<span data-ttu-id="d8a9a-102">指定於具名管道上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-102">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over named pipe.</span></span>  
  
 <span data-ttu-id="d8a9a-103">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d8a9a-103">\<system.ServiceModel></span></span>  
<span data-ttu-id="d8a9a-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d8a9a-104">\<bindings></span></span>  
<span data-ttu-id="d8a9a-105">\<mexNamedPipeBinding></span><span class="sxs-lookup"><span data-stu-id="d8a9a-105">\<mexNamedPipeBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d8a9a-106">語法</span><span class="sxs-lookup"><span data-stu-id="d8a9a-106">Syntax</span></span>  
  
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
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d8a9a-107">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d8a9a-107">Attributes and Elements</span></span>  
 <span data-ttu-id="d8a9a-108">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-108">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d8a9a-109">屬性</span><span class="sxs-lookup"><span data-stu-id="d8a9a-109">Attributes</span></span>  
  
|<span data-ttu-id="d8a9a-110">屬性</span><span class="sxs-lookup"><span data-stu-id="d8a9a-110">Attribute</span></span>|<span data-ttu-id="d8a9a-111">描述</span><span class="sxs-lookup"><span data-stu-id="d8a9a-111">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="d8a9a-112"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-112">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="d8a9a-113">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-113">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8a9a-114">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-114">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="d8a9a-115">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-115">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="d8a9a-116">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-116">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="d8a9a-117">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-117">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="d8a9a-118">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-118">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="d8a9a-119">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-119">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="d8a9a-120">如需有關預設組態和無名稱繫結和行為的詳細資訊，請參閱 < [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md)並[Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-120">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="d8a9a-121"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-121">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="d8a9a-122">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-122">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8a9a-123">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-123">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="d8a9a-124"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-124">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="d8a9a-125">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-125">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8a9a-126">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-126">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="d8a9a-127"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-127">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="d8a9a-128">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-128">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="d8a9a-129">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-129">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d8a9a-130">子元素</span><span class="sxs-lookup"><span data-stu-id="d8a9a-130">Child Elements</span></span>  
 <span data-ttu-id="d8a9a-131">無。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-131">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d8a9a-132">父項目</span><span class="sxs-lookup"><span data-stu-id="d8a9a-132">Parent Elements</span></span>  
  
|<span data-ttu-id="d8a9a-133">項目</span><span class="sxs-lookup"><span data-stu-id="d8a9a-133">Element</span></span>|<span data-ttu-id="d8a9a-134">描述</span><span class="sxs-lookup"><span data-stu-id="d8a9a-134">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d8a9a-135">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d8a9a-135">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="d8a9a-136">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="d8a9a-136">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="d8a9a-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d8a9a-137">See also</span></span>

- <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexNamedPipeBinding%2A>
- <xref:System.ServiceModel.Configuration.MexNamedPipeBindingElement>
- [<span data-ttu-id="d8a9a-138">如何：發行服務，使用組態檔的中繼資料</span><span class="sxs-lookup"><span data-stu-id="d8a9a-138">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)
- [<span data-ttu-id="d8a9a-139">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="d8a9a-139">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)
- [<span data-ttu-id="d8a9a-140">中繼資料</span><span class="sxs-lookup"><span data-stu-id="d8a9a-140">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)
- [<span data-ttu-id="d8a9a-141">繫結</span><span class="sxs-lookup"><span data-stu-id="d8a9a-141">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d8a9a-142">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d8a9a-142">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d8a9a-143">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d8a9a-143">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d8a9a-144">\<binding></span><span class="sxs-lookup"><span data-stu-id="d8a9a-144">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
