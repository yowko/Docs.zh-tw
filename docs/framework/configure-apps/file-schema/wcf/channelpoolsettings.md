---
title: <channelPoolSettings>
ms.date: 03/30/2017
ms.assetid: 4755f3d3-4213-4c68-ae7f-45b67d744459
ms.openlocfilehash: 26537980a6be5c0fe12661d93a6ba5fe862ceb4e
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70398163"
---
# \<channelPoolSettings>
<span data-ttu-id="b41a6-101">指定自訂繫結的通道集區設定。</span><span class="sxs-lookup"><span data-stu-id="b41a6-101">Specifies the channel pool settings for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<oneWay>**](oneway.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<channelPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="b41a6-102">語法</span><span class="sxs-lookup"><span data-stu-id="b41a6-102">Syntax</span></span>  
  
```xml  
<channelPoolSettings idleTimeout="TimeSpan"
                     leaseTimeout="TimeSpan"
                     maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b41a6-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b41a6-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b41a6-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b41a6-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b41a6-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b41a6-105">Attributes</span></span>  
  
|<span data-ttu-id="b41a6-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b41a6-106">Attribute</span></span>|<span data-ttu-id="b41a6-107">描述</span><span class="sxs-lookup"><span data-stu-id="b41a6-107">Description</span></span>|  
|---------------|-----------------|  
|`idleTimeout`|<span data-ttu-id="b41a6-108">正的 <xref:System.TimeSpan>，指定集區中的通道在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="b41a6-108">A positive <xref:System.TimeSpan> that specifies the maximum time the channels in the pool can be idle before being disconnected.</span></span> <span data-ttu-id="b41a6-109">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="b41a6-109">The default is 00:02:00.</span></span>|  
|`leaseTimeout`|<span data-ttu-id="b41a6-110"><xref:System.TimeSpan>，指定已傳回到集區之通道多久之後將關閉的間隔時間。</span><span class="sxs-lookup"><span data-stu-id="b41a6-110">A <xref:System.TimeSpan> that specifies the interval of time after which a channel, when returned to the pool, is closed.</span></span> <span data-ttu-id="b41a6-111">預設為 00:10:00。</span><span class="sxs-lookup"><span data-stu-id="b41a6-111">The default is 00:10:00.</span></span>|  
|`maxOutboundChannelsPerEndpoint`|<span data-ttu-id="b41a6-112">正整數，指定每個遠端端點可儲存在集區中的最大通道數目。</span><span class="sxs-lookup"><span data-stu-id="b41a6-112">A positive integer that specifies the maximum number of channels that can be stored in the pool for each remote endpoint.</span></span> <span data-ttu-id="b41a6-113">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="b41a6-113">The default is 10.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b41a6-114">子元素</span><span class="sxs-lookup"><span data-stu-id="b41a6-114">Child Elements</span></span>  
 <span data-ttu-id="b41a6-115">無。</span><span class="sxs-lookup"><span data-stu-id="b41a6-115">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="b41a6-116">父項目</span><span class="sxs-lookup"><span data-stu-id="b41a6-116">Parent Elements</span></span>  
  
|<span data-ttu-id="b41a6-117">元素</span><span class="sxs-lookup"><span data-stu-id="b41a6-117">Element</span></span>|<span data-ttu-id="b41a6-118">描述</span><span class="sxs-lookup"><span data-stu-id="b41a6-118">Description</span></span>|  
|-------------|-----------------|  
|[\<oneWay>](oneway.md)|<span data-ttu-id="b41a6-119">啟用自訂繫結的封包路由。</span><span class="sxs-lookup"><span data-stu-id="b41a6-119">Enables packet routing for a custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b41a6-120">備註</span><span class="sxs-lookup"><span data-stu-id="b41a6-120">Remarks</span></span>  
 <span data-ttu-id="b41a6-121">配額是一種用來避免資源過度耗費的原則機制。</span><span class="sxs-lookup"><span data-stu-id="b41a6-121">Quotas are used as a policy mechanism to prevent the consumption of excessive resources.</span></span> <span data-ttu-id="b41a6-122">這類配額會防止惡意或是無意間發生的阻斷服務 (DOS) 攻擊。</span><span class="sxs-lookup"><span data-stu-id="b41a6-122">They prevent Denial of Service (DOS) attacks that are either malicious or unintentional.</span></span> <span data-ttu-id="b41a6-123">當設定自訂通道配額的時候，請使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="b41a6-123">Use this element when setting channel quotas on a custom channel.</span></span>  
  
 <span data-ttu-id="b41a6-124">`ChannelPoolSettings` 指定三種配額：</span><span class="sxs-lookup"><span data-stu-id="b41a6-124">`ChannelPoolSettings` specifies three quotas:</span></span>  
  
- <span data-ttu-id="b41a6-125">`idleTimeout` 配額，可用來降低在伺服器上藉由佔用資源一段延長期間所產生的阻斷服務 (DOS) 攻擊情形。</span><span class="sxs-lookup"><span data-stu-id="b41a6-125">The `idleTimeout` quota is used to mitigate Denial of Service (DOS) attacks on the server that rely on tying up resources for an extended period of time.</span></span> <span data-ttu-id="b41a6-126">在用戶端，設定正確的值可以增加與服務的連接可靠性。</span><span class="sxs-lookup"><span data-stu-id="b41a6-126">On the client, setting the correct value can increase the reliability of connecting with the service.</span></span> <span data-ttu-id="b41a6-127">預設值是依據最為保守穩當的資源配置所設定。</span><span class="sxs-lookup"><span data-stu-id="b41a6-127">The default value is based on a conservatively modest allocation of resources.</span></span> <span data-ttu-id="b41a6-128">這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="b41a6-128">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="b41a6-129">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="b41a6-129">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="b41a6-130">`leaseTimeout` 配額，其用途在於整合負載平衡器和改善可靠性。</span><span class="sxs-lookup"><span data-stu-id="b41a6-130">The `leaseTimeout` quota is used to for integration with load balancers and for improving reliability.</span></span> <span data-ttu-id="b41a6-131">預設值是依據保守的資源配置所設定。</span><span class="sxs-lookup"><span data-stu-id="b41a6-131">The default value is based on a conservative allocation of resources.</span></span> <span data-ttu-id="b41a6-132">這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="b41a6-132">It is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="b41a6-133">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="b41a6-133">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
- <span data-ttu-id="b41a6-134">`maxOutboundChannelsPerEndpoint` 配額會設定伺服器和用戶端雙方的快取限制，並可用來改善可靠性。</span><span class="sxs-lookup"><span data-stu-id="b41a6-134">The `maxOutboundChannelsPerEndpoint` quota sets cache limits on both the server and the client and is used to improve reliability.</span></span> <span data-ttu-id="b41a6-135">預設值是依據最為保守穩當的資源配置所設定，這個設定值適合開發環境和小規模的安裝情況。</span><span class="sxs-lookup"><span data-stu-id="b41a6-135">The default value is based on a conservatively modest allocation of resources that is suitable for a development environment and small installation scenarios.</span></span> <span data-ttu-id="b41a6-136">如果安裝時資源不足，或是連線不論是否有額外的資源都會受到限制，服務系統管理員就應該檢查此值。</span><span class="sxs-lookup"><span data-stu-id="b41a6-136">Service administrators should review the value if an installation is running out of resources or if connections are being limited despite the availability of additional resources.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b41a6-137">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b41a6-137">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Channels.ChannelPoolSettings>
- <xref:System.ServiceModel.Configuration.OneWayElement.ChannelPoolSettings%2A>
- <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [\<oneWay>](oneway.md)
- [<span data-ttu-id="b41a6-138">繫結</span><span class="sxs-lookup"><span data-stu-id="b41a6-138">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b41a6-139">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b41a6-139">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b41a6-140">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b41a6-140">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
