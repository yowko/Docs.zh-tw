---
title: <oneWay>
ms.date: 03/30/2017
ms.assetid: 00e67e0e-77c0-4695-9138-c0997b0e5f3c
ms.openlocfilehash: a5c773ea91de882920775ac8dc0ecc1da68a6c9f
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738784"
---
# \<oneWay>
<span data-ttu-id="b7947-101">針對自訂繫結啟用封包路由和使用單向方法。</span><span class="sxs-lookup"><span data-stu-id="b7947-101">Enables packet routing and the use of one-way methods for a custom binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<oneWay>**  
  
## <a name="syntax"></a><span data-ttu-id="b7947-102">語法</span><span class="sxs-lookup"><span data-stu-id="b7947-102">Syntax</span></span>  
  
```xml  
<oneWay packetRoutable="Boolean">
  <channelPoolSettings idleTimeout="TimeSpan"
                       leaseTimeout="TimeSpan"
                       maxOutboundConnectionsPerEndpoint="Integer" />
</oneWay>
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="b7947-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="b7947-103">Attributes and Elements</span></span>  
 <span data-ttu-id="b7947-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="b7947-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="b7947-105">屬性</span><span class="sxs-lookup"><span data-stu-id="b7947-105">Attributes</span></span>  
  
|<span data-ttu-id="b7947-106">屬性</span><span class="sxs-lookup"><span data-stu-id="b7947-106">Attribute</span></span>|<span data-ttu-id="b7947-107">描述</span><span class="sxs-lookup"><span data-stu-id="b7947-107">Description</span></span>|  
|---------------|-----------------|  
|`packetRoutable`|<span data-ttu-id="b7947-108">布林值，指定是否啟用封包路由。</span><span class="sxs-lookup"><span data-stu-id="b7947-108">A Boolean value that specifies whether packet routing is enabled.</span></span> <span data-ttu-id="b7947-109">預設值為 `false`。</span><span class="sxs-lookup"><span data-stu-id="b7947-109">The default is `false`.</span></span>|  
|`MaxAcceptedChannels`|<span data-ttu-id="b7947-110">整數，指定可接受的通道數目上限。</span><span class="sxs-lookup"><span data-stu-id="b7947-110">An integer that specifies the maximum number of channels that can be accepted.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="b7947-111">子元素</span><span class="sxs-lookup"><span data-stu-id="b7947-111">Child Elements</span></span>  
  
|<span data-ttu-id="b7947-112">元素</span><span class="sxs-lookup"><span data-stu-id="b7947-112">Element</span></span>|<span data-ttu-id="b7947-113">描述</span><span class="sxs-lookup"><span data-stu-id="b7947-113">Description</span></span>|  
|-------------|-----------------|  
|[\<channelPoolSettings>](channelpoolsettings.md)|<span data-ttu-id="b7947-114"><xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> 物件，包含目前通道的通道集區的屬性。</span><span class="sxs-lookup"><span data-stu-id="b7947-114">A <xref:System.ServiceModel.Configuration.ChannelPoolSettingsElement> object that contains properties of the channel pool for the current channel.</span></span>|  
  
### <a name="parent-elements"></a><span data-ttu-id="b7947-115">父項目</span><span class="sxs-lookup"><span data-stu-id="b7947-115">Parent Elements</span></span>  
  
|<span data-ttu-id="b7947-116">元素</span><span class="sxs-lookup"><span data-stu-id="b7947-116">Element</span></span>|<span data-ttu-id="b7947-117">描述</span><span class="sxs-lookup"><span data-stu-id="b7947-117">Description</span></span>|  
|-------------|-----------------|  
|[\<binding>](bindings.md)|<span data-ttu-id="b7947-118">定義自訂繫結的所有繫結功能。</span><span class="sxs-lookup"><span data-stu-id="b7947-118">Defines all binding capabilities of the custom binding.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b7947-119">備註</span><span class="sxs-lookup"><span data-stu-id="b7947-119">Remarks</span></span>  
 <span data-ttu-id="b7947-120">如果要啟用封包路由，便需要這個項目提供的單向轉換層。</span><span class="sxs-lookup"><span data-stu-id="b7947-120">To enable packet routing, a one-way conversion layer is required, which this element provides.</span></span> <span data-ttu-id="b7947-121">使用者可以建立自訂繫結，將這個繫結置於工作階段感知或要求-回覆傳輸層上，讓它啟用路由傳送封包功能。</span><span class="sxs-lookup"><span data-stu-id="b7947-121">A user can create a custom binding that layers this binding over a session-aware or request-reply transport to make it packet routable.</span></span> <span data-ttu-id="b7947-122">當您要以較原始的方式來公開單向方法時，也可以使用這個項目。</span><span class="sxs-lookup"><span data-stu-id="b7947-122">This element is also useful when you want to expose one-way methods in a more native fashion.</span></span> <span data-ttu-id="b7947-123">還有其他轉換可套用至這一層，例如複合雙工和可信賴傳訊。</span><span class="sxs-lookup"><span data-stu-id="b7947-123">More transformations can be applied over this layer, such as Composite Duplex and Reliable Messaging.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b7947-124">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b7947-124">See also</span></span>

- <xref:System.ServiceModel.Channels.OneWayBindingElement>
- <xref:System.ServiceModel.Configuration.OneWayElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="b7947-125">繫結</span><span class="sxs-lookup"><span data-stu-id="b7947-125">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="b7947-126">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b7947-126">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="b7947-127">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="b7947-127">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
