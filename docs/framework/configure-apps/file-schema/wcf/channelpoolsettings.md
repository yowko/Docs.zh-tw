---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: ca1f680e2de67984dfcec49b3d262799000a2625
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61673325"
---
# <a name="channelpoolsettings"></a><span data-ttu-id="3e519-101">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="3e519-101">\<channelPoolSettings></span></span>
<span data-ttu-id="3e519-102">指定自訂繫結的通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="3e519-102">Specifies the channel pool settings for a custom binding.</span></span>  
  
 <span data-ttu-id="3e519-103">\<system.serviceModel></span><span class="sxs-lookup"><span data-stu-id="3e519-103">\<system.serviceModel></span></span>  
<span data-ttu-id="3e519-104">\<bindings></span><span class="sxs-lookup"><span data-stu-id="3e519-104">\<bindings></span></span>  
<span data-ttu-id="3e519-105">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3e519-105">\<customBinding></span></span>  
<span data-ttu-id="3e519-106">\<binding></span><span class="sxs-lookup"><span data-stu-id="3e519-106">\<binding></span></span>  
<span data-ttu-id="3e519-107">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="3e519-107">\<oneWay></span></span>  
<span data-ttu-id="3e519-108">\<channelPoolSettings></span><span class="sxs-lookup"><span data-stu-id="3e519-108">\<channelPoolSettings></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3e519-109">語法</span><span class="sxs-lookup"><span data-stu-id="3e519-109">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpopint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="3e519-110">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="3e519-110">Attributes and Elements</span></span>  
 <span data-ttu-id="3e519-111">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="3e519-111">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="3e519-112">屬性</span><span class="sxs-lookup"><span data-stu-id="3e519-112">Attributes</span></span>  
  
|<span data-ttu-id="3e519-113">屬性</span><span class="sxs-lookup"><span data-stu-id="3e519-113">Attribute</span></span>|<span data-ttu-id="3e519-114">描述</span><span class="sxs-lookup"><span data-stu-id="3e519-114">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="3e519-115">正的 <xref:System.TimeSpan>，指定集區中的通道在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="3e519-115">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="3e519-116">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="3e519-116">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="3e519-117"><xref:System.TimeSpan>，指定已傳回到集區之通道多久之後將關閉的間隔時間。</span><span class="sxs-lookup"><span data-stu-id="3e519-117">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="3e519-118">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="3e519-118">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="3e519-119">正整數，指定每個遠端端點可儲存在集區中的最大通道數目。</span><span class="sxs-lookup"><span data-stu-id="3e519-119">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="3e519-120">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="3e519-120">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="3e519-121">子元素</span><span class="sxs-lookup"><span data-stu-id="3e519-121">Child Elements</span></span>  
 <span data-ttu-id="3e519-122">無。</span><span class="sxs-lookup"><span data-stu-id="3e519-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="3e519-123">父項目</span><span class="sxs-lookup"><span data-stu-id="3e519-123">Parent Elements</span></span>  
  
|<span data-ttu-id="3e519-124">項目</span><span class="sxs-lookup"><span data-stu-id="3e519-124">Element</span></span>|<span data-ttu-id="3e519-125">描述</span><span class="sxs-lookup"><span data-stu-id="3e519-125">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="3e519-126">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="3e519-126">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)|<span data-ttu-id="3e519-127">啟用自訂繫結的封包路由。</span><span class="sxs-lookup"><span data-stu-id="3e519-127">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3e519-128">備註</span><span class="sxs-lookup"><span data-stu-id="3e519-128">Remarks</span></span>  
 <span data-ttu-id="3e519-129">配額是一種用來避免資源過度耗費的原則機制。</span><span class="sxs-lookup"><span data-stu-id="3e519-129">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="3e519-130">這類配額會防止惡意或是無意間發生的阻斷服務 (DOS) 攻擊。</span><span class="sxs-lookup"><span data-stu-id="3e519-130">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="3e519-131">當設定自訂通道配額的時候，請使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="3e519-131">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="3e519-132">`ChannelPoolSettings` 指定三種配額：</span><span class="sxs-lookup"><span data-stu-id="3e519-132">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
-   <span data-ttu-id="3e519-133">`idleTimeout` 配額，可用來降低在伺服器上藉由佔用資源一段延長期間所產生的阻斷服務 (DOS) 攻擊情形。</span><span class="sxs-lookup"><span data-stu-id="3e519-133">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="3e519-134">在用戶端，設定正確的值可以增加與服務的連接可靠性。</span><span class="sxs-lookup"><span data-stu-id="3e519-134">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="3e519-135">預設值是依據最為保守穩當的資源配置所設定。</span><span class="sxs-lookup"><span data-stu-id="3e519-135">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="3e519-136">這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="3e519-136">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3e519-137">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="3e519-137">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="3e519-138">`leaseTimeout` 配額，其用途在於整合負載平衡器和改善可靠性。</span><span class="sxs-lookup"><span data-stu-id="3e519-138">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="3e519-139">預設值是依據保守的資源配置所設定。</span><span class="sxs-lookup"><span data-stu-id="3e519-139">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="3e519-140">這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="3e519-140">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3e519-141">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="3e519-141">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
-   <span data-ttu-id="3e519-142">`maxOutboundChannelsPerEndpoint` 配額會設定伺服器和用戶端雙方的快取限制，並可用來改善可靠性。</span><span class="sxs-lookup"><span data-stu-id="3e519-142">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="3e519-143">預設值是依據最為保守穩當的資源配置所設定，這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="3e519-143">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="3e519-144">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="3e519-144">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3e519-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="3e519-145">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="3e519-146">\<oneWay></span><span class="sxs-lookup"><span data-stu-id="3e519-146">\<oneWay></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/oneway.md)
- [<span data-ttu-id="3e519-147">繫結</span><span class="sxs-lookup"><span data-stu-id="3e519-147">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="3e519-148">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="3e519-148">Extending Bindings</span></span>](../../../../../docs/framework/wcf/extending/extending-bindings.md)
- [<span data-ttu-id="3e519-149">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="3e519-149">Custom Bindings</span></span>](../../../../../docs/framework/wcf/extending/custom-bindings.md)
- [<span data-ttu-id="3e519-150">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="3e519-150">\<customBinding></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
