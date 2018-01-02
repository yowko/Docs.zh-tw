---
title: '&lt;mexTcpBinding&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 01baba8d-d784-4255-9ea2-7afff1482bf0
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e768bf3014afa2c9205ea80fe1d101b93d36fbc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="ltmextcpbindinggt"></a><span data-ttu-id="923b2-102">&lt;mexTcpBinding&gt;</span><span class="sxs-lookup"><span data-stu-id="923b2-102">&lt;mexTcpBinding&gt;</span></span>
<span data-ttu-id="923b2-103">指定用於 TCP 上 WS-MetadataExchange (WS-MEX) 訊息交換之繫結的設定。</span><span class="sxs-lookup"><span data-stu-id="923b2-103">Specifies the settings for a binding used for the WS-MetadataExchange (WS-MEX) message exchange over TCP.</span></span>  
  
 <span data-ttu-id="923b2-104">\<系統。ServiceModel ></span><span class="sxs-lookup"><span data-stu-id="923b2-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="923b2-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="923b2-105">\<bindings></span></span>  
<span data-ttu-id="923b2-106">\<mexTcpBinding ></span><span class="sxs-lookup"><span data-stu-id="923b2-106">\<mexTcpBinding></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="923b2-107">語法</span><span class="sxs-lookup"><span data-stu-id="923b2-107">Syntax</span></span>  
  
```xml  
<mexTcpBinding>  
   <binding   
       closeTimeout="TimeSpan"   
       name="string"   
       openTimeout="TimeSpan"   
       receiveTimeout="TimeSpan"  
       sendTimeout="TimeSpan">  
   </binding>  
</mexTcpBinding>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="923b2-108">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="923b2-108">Attributes and Elements</span></span>  
 <span data-ttu-id="923b2-109">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="923b2-109">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="923b2-110">屬性</span><span class="sxs-lookup"><span data-stu-id="923b2-110">Attributes</span></span>  
  
|<span data-ttu-id="923b2-111">屬性</span><span class="sxs-lookup"><span data-stu-id="923b2-111">Attribute</span></span>|<span data-ttu-id="923b2-112">描述</span><span class="sxs-lookup"><span data-stu-id="923b2-112">Description</span></span>|  
|---------------|-----------------|  
|`closeTimeout`|<span data-ttu-id="923b2-113"><xref:System.TimeSpan> 值，指定提供用來讓關閉作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="923b2-113">A <xref:System.TimeSpan> value that specifies the interval of time provided for a close operation to complete.</span></span> <span data-ttu-id="923b2-114">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="923b2-114">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="923b2-115">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="923b2-115">The default is 00:01:00.</span></span>|  
|`name`|<span data-ttu-id="923b2-116">包含繫結之組態名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="923b2-116">A string that contains the configuration name of the binding.</span></span> <span data-ttu-id="923b2-117">這個值應該是唯一的，因為它會當做繫結的識別使用。</span><span class="sxs-lookup"><span data-stu-id="923b2-117">This value should be unique because it is used as an identification for the binding.</span></span> <span data-ttu-id="923b2-118">每一個繫結都有一個 `name` 和 `namespace` 屬性，兩者結合在一起便可在服務的中繼資料中唯一識別各個繫結。</span><span class="sxs-lookup"><span data-stu-id="923b2-118">Each binding has a `name` and `namespace` attribute that together uniquely identify it in the metadata of the service.</span></span> <span data-ttu-id="923b2-119">此外，這個名稱在相同型別的繫結中也是唯一的。</span><span class="sxs-lookup"><span data-stu-id="923b2-119">In addition, this name is unique among bindings of the same type.</span></span> <span data-ttu-id="923b2-120">從 [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)] 開始，繫結和行為都不需要有名稱。</span><span class="sxs-lookup"><span data-stu-id="923b2-120">Starting with [!INCLUDE[netfx40_short](../../../../../includes/netfx40-short-md.md)], bindings and behaviors are not required to have a name.</span></span> <span data-ttu-id="923b2-121">如需有關預設組態沒有名稱繫結和行為的詳細資訊，請參閱[簡化的組態](../../../../../docs/framework/wcf/simplified-configuration.md)和[簡化 WCF 服務的組態](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md)。</span><span class="sxs-lookup"><span data-stu-id="923b2-121">For more information about default configuration and nameless bindings and behaviors, see [Simplified Configuration](../../../../../docs/framework/wcf/simplified-configuration.md) and [Simplified Configuration for WCF Services](../../../../../docs/framework/wcf/samples/simplified-configuration-for-wcf-services.md).</span></span>|  
|`openTimeout`|<span data-ttu-id="923b2-122"><xref:System.TimeSpan> 值，指定提供用來讓開啟作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="923b2-122">A <xref:System.TimeSpan> value that specifies the interval of time provided for an open operation to complete.</span></span> <span data-ttu-id="923b2-123">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="923b2-123">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="923b2-124">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="923b2-124">The default is 00:01:00.</span></span>|  
|`receiveTimeout`|<span data-ttu-id="923b2-125"><xref:System.TimeSpan> 值，指定接收作業完成其作業之時間間隔。</span><span class="sxs-lookup"><span data-stu-id="923b2-125">A <xref:System.TimeSpan> value that specifies the interval of time provided for a receive operation to complete.</span></span> <span data-ttu-id="923b2-126">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="923b2-126">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="923b2-127">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="923b2-127">The default is 00:10:00.</span></span>|  
|`sendTimeout`|<span data-ttu-id="923b2-128"><xref:System.TimeSpan> 值，指定提供用來讓傳送作業完成的時間間隔。</span><span class="sxs-lookup"><span data-stu-id="923b2-128">A <xref:System.TimeSpan> value that specifies the interval of time provided for a send operation to complete.</span></span> <span data-ttu-id="923b2-129">這個值應該大於或等於 <xref:System.TimeSpan.Zero>。</span><span class="sxs-lookup"><span data-stu-id="923b2-129">This value should be greater than or equal to <xref:System.TimeSpan.Zero>.</span></span> <span data-ttu-id="923b2-130">預設為 00:01:00。</span><span class="sxs-lookup"><span data-stu-id="923b2-130">The default is 00:01:00.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="923b2-131">子元素</span><span class="sxs-lookup"><span data-stu-id="923b2-131">Child Elements</span></span>  
 <span data-ttu-id="923b2-132">無。</span><span class="sxs-lookup"><span data-stu-id="923b2-132">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="923b2-133">父項目</span><span class="sxs-lookup"><span data-stu-id="923b2-133">Parent Elements</span></span>  
  
|<span data-ttu-id="923b2-134">項目</span><span class="sxs-lookup"><span data-stu-id="923b2-134">Element</span></span>|<span data-ttu-id="923b2-135">描述</span><span class="sxs-lookup"><span data-stu-id="923b2-135">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="923b2-136">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="923b2-136">\<bindings></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)|<span data-ttu-id="923b2-137">這個項目會保存標準和自訂繫結的集合。</span><span class="sxs-lookup"><span data-stu-id="923b2-137">This element holds a collection of standard and custom bindings.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="923b2-138">請參閱</span><span class="sxs-lookup"><span data-stu-id="923b2-138">See Also</span></span>  
 <xref:System.ServiceModel.Configuration.MexTcpBindingElement>  
 <xref:System.ServiceModel.Description.MetadataExchangeBindings.CreateMexTcpBinding%2A>  
 [<span data-ttu-id="923b2-139">如何：使用組態檔發行服務的中繼資料</span><span class="sxs-lookup"><span data-stu-id="923b2-139">How to: Publish Metadata for a Service Using a Configuration File</span></span>](../../../../../docs/framework/wcf/feature-details/how-to-publish-metadata-for-a-service-using-a-configuration-file.md)  
 [<span data-ttu-id="923b2-140">發行與擷取自訂繫結上的中繼資料</span><span class="sxs-lookup"><span data-stu-id="923b2-140">Publishing and Retrieving Metadata Over a Custom Binding</span></span>](../../../../../docs/framework/wcf/extending/publishing-and-retrieving-metadata-over-a-custom-binding.md)  
 [<span data-ttu-id="923b2-141">中繼資料</span><span class="sxs-lookup"><span data-stu-id="923b2-141">Metadata</span></span>](../../../../../docs/framework/wcf/feature-details/metadata.md)  
 [<span data-ttu-id="923b2-142">繫結</span><span class="sxs-lookup"><span data-stu-id="923b2-142">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="923b2-143">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="923b2-143">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="923b2-144">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="923b2-144">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/en-us/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="923b2-145">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="923b2-145">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
