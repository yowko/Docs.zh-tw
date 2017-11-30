---
title: '&lt;channelPoolSettings&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
caps.latest.revision: "8"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 44e79c7af470cefead8bcfb0ef96606ecde30383
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="ltchannelpoolsettingsgt"></a><span data-ttu-id="fa51e-102">&lt;channelPoolSettings&gt;</span><span class="sxs-lookup"><span data-stu-id="fa51e-102">&lt;channelPoolSettings&gt;</span></span>
<span data-ttu-id="fa51e-103">指定自訂繫結的通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="fa51e-103">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="fa51e-104">\<system.serviceModel ></span><span class="sxs-lookup"><span data-stu-id="fa51e-104">\<system.serviceModel></span></span>  
<span data-ttu-id="fa51e-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fa51e-105">\<bindings></span></span>  
<span data-ttu-id="fa51e-106">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fa51e-106">\<customBinding></span></span>  
<span data-ttu-id="fa51e-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="fa51e-107">\<binding></span></span>  
<span data-ttu-id="fa51e-108">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fa51e-108">\<oneWay></span></span>  
<span data-ttu-id="fa51e-109">\<channelPoolSettings ></span><span class="sxs-lookup"><span data-stu-id="fa51e-109">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="fa51e-110">語法</span><span class="sxs-lookup"><span data-stu-id="fa51e-110">Syntax</span></span>  
  
```xml  
<channelPoolSettings  
    idleTimeout"TimeSpan"  
        leaseTimeout"TimeSpan"  
    maxOutboundConnectionsPerEndpopint="Integer" />  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="fa51e-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="fa51e-111">Attributes and Elements</span></span>  
 <span data-ttu-id="fa51e-112">下列章節說明屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="fa51e-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="fa51e-113">屬性</span><span class="sxs-lookup"><span data-stu-id="fa51e-113">Attributes</span></span>  
  
|<span data-ttu-id="fa51e-114">屬性</span><span class="sxs-lookup"><span data-stu-id="fa51e-114">Attribute</span></span>|<span data-ttu-id="fa51e-115">描述</span><span class="sxs-lookup"><span data-stu-id="fa51e-115">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="fa51e-116">正的 <xref:System.TimeSpan>，指定集區中的通道在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="fa51e-116">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="fa51e-117">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="fa51e-117">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="fa51e-118"><xref:System.TimeSpan>，指定已傳回到集區之通道多久之後將關閉的間隔時間。</span><span class="sxs-lookup"><span data-stu-id="fa51e-118">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="fa51e-119">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="fa51e-119">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="fa51e-120">正整數，指定每個遠端端點可儲存在集區中的最大通道數目。</span><span class="sxs-lookup"><span data-stu-id="fa51e-120">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="fa51e-121">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="fa51e-121">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="fa51e-122">子元素</span><span class="sxs-lookup"><span data-stu-id="fa51e-122">Child Elements</span></span>  
 <span data-ttu-id="fa51e-123">無。</span><span class="sxs-lookup"><span data-stu-id="fa51e-123">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="fa51e-124">父項目</span><span class="sxs-lookup"><span data-stu-id="fa51e-124">Parent Elements</span></span>  
  
|<span data-ttu-id="fa51e-125">項目</span><span class="sxs-lookup"><span data-stu-id="fa51e-125">Element</span></span>|<span data-ttu-id="fa51e-126">說明</span><span class="sxs-lookup"><span data-stu-id="fa51e-126">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="fa51e-127">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fa51e-127">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="fa51e-128">啟用自訂繫結的封包路由。</span><span class="sxs-lookup"><span data-stu-id="fa51e-128">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="fa51e-129">備註</span><span class="sxs-lookup"><span data-stu-id="fa51e-129">Remarks</span></span>  
 <span data-ttu-id="fa51e-130">配額是一種用來避免資源過度耗費的原則機制。</span><span class="sxs-lookup"><span data-stu-id="fa51e-130">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="fa51e-131">這類配額會防止惡意或是無意間發生的阻斷服務 (DOS) 攻擊。</span><span class="sxs-lookup"><span data-stu-id="fa51e-131">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="fa51e-132">當設定自訂通道配額的時候，請使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="fa51e-132">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="fa51e-133">`ChannelPoolSettings` 指定三種配額：</span><span class="sxs-lookup"><span data-stu-id="fa51e-133">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="fa51e-134">`idleTimeout` 配額，可用來降低在伺服器上藉由佔用資源一段延長期間所產生的阻斷服務 (DOS) 攻擊情形。</span><span class="sxs-lookup"><span data-stu-id="fa51e-134">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="fa51e-135">在用戶端，設定正確的值可以增加與服務的連接可靠性。</span><span class="sxs-lookup"><span data-stu-id="fa51e-135">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="fa51e-136">預設值是依據最為保守穩當的資源配置所設定。</span><span class="sxs-lookup"><span data-stu-id="fa51e-136">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="fa51e-137">這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="fa51e-137">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fa51e-138">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="fa51e-138">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fa51e-139">`leaseTimeout` 配額，其用途在於整合負載平衡器和改善可靠性。</span><span class="sxs-lookup"><span data-stu-id="fa51e-139">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="fa51e-140">預設值是依據保守的資源配置所設定。</span><span class="sxs-lookup"><span data-stu-id="fa51e-140">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="fa51e-141">這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="fa51e-141">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fa51e-142">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="fa51e-142">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="fa51e-143">`maxOutboundChannelsPerEndpoint` 配額會設定伺服器和用戶端雙方的快取限制，並可用來改善可靠性。</span><span class="sxs-lookup"><span data-stu-id="fa51e-143">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="fa51e-144">預設值是依據最為保守穩當的資源配置所設定，這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="fa51e-144">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="fa51e-145">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="fa51e-145">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa51e-146">另請參閱</span><span class="sxs-lookup"><span data-stu-id="fa51e-146">See Also</span></span>  
 <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Channels.ChannelPoolSettings>  
 <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>  
 <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>  
 <xref:System.ServiceModel.Channels.CustomBinding>  
 [<span data-ttu-id="fa51e-147">\<oneWay ></span><span class="sxs-lookup"><span data-stu-id="fa51e-147">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)  
 [<span data-ttu-id="fa51e-148">繫結</span><span class="sxs-lookup"><span data-stu-id="fa51e-148">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="fa51e-149">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="fa51e-149">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)  
 [<span data-ttu-id="fa51e-150">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="fa51e-150">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)  
 [<span data-ttu-id="fa51e-151">\<customBinding ></span><span class="sxs-lookup"><span data-stu-id="fa51e-151">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
