---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "70400473"
---
# \<connectionPoolSettings>
<span data-ttu-id="a9c28-101">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="a9c28-101">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**  
  
## <a name="syntax"></a><span data-ttu-id="a9c28-102">語法</span><span class="sxs-lookup"><span data-stu-id="a9c28-102">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="a9c28-103">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="a9c28-103">Attributes and Elements</span></span>  
 <span data-ttu-id="a9c28-104">下列章節說明屬性、子元素和父元素。</span><span class="sxs-lookup"><span data-stu-id="a9c28-104">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="a9c28-105">屬性</span><span class="sxs-lookup"><span data-stu-id="a9c28-105">Attributes</span></span>  
  
|<span data-ttu-id="a9c28-106">屬性</span><span class="sxs-lookup"><span data-stu-id="a9c28-106">Attribute</span></span>|<span data-ttu-id="a9c28-107">描述</span><span class="sxs-lookup"><span data-stu-id="a9c28-107">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="a9c28-108">定義用於傳出通道之連線集區名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="a9c28-108">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="a9c28-109">在資料流處理模式中，不會共用連線，意指會停用連線集區。</span><span class="sxs-lookup"><span data-stu-id="a9c28-109">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="a9c28-110">預設為 "default" 字串。</span><span class="sxs-lookup"><span data-stu-id="a9c28-110">The default is a "default" string.</span></span> <span data-ttu-id="a9c28-111">您可以修改這個值，將特定用戶端的連線隔離在不同群組中。</span><span class="sxs-lookup"><span data-stu-id="a9c28-111">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="a9c28-112">正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="a9c28-112">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="a9c28-113">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="a9c28-113">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="a9c28-114">正整數，指定與服務初始化之遠端端點連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="a9c28-114">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="a9c28-115">超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="a9c28-115">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="a9c28-116">`idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。</span><span class="sxs-lookup"><span data-stu-id="a9c28-116">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="a9c28-117">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="a9c28-117">The default is 10.</span></span><br /><br /> <span data-ttu-id="a9c28-118">這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。</span><span class="sxs-lookup"><span data-stu-id="a9c28-118">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="a9c28-119">如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。</span><span class="sxs-lookup"><span data-stu-id="a9c28-119">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="a9c28-120">在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="a9c28-120">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="a9c28-121">子元素</span><span class="sxs-lookup"><span data-stu-id="a9c28-121">Child Elements</span></span>  
 <span data-ttu-id="a9c28-122">無。</span><span class="sxs-lookup"><span data-stu-id="a9c28-122">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="a9c28-123">父項目</span><span class="sxs-lookup"><span data-stu-id="a9c28-123">Parent Elements</span></span>  
  
|<span data-ttu-id="a9c28-124">元素</span><span class="sxs-lookup"><span data-stu-id="a9c28-124">Element</span></span>|<span data-ttu-id="a9c28-125">描述</span><span class="sxs-lookup"><span data-stu-id="a9c28-125">Description</span></span>|  
|-------------|-----------------|  
|[\<namedPipeTransport>](namedpipetransport.md)|<span data-ttu-id="a9c28-126">定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="a9c28-126">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="a9c28-127">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a9c28-127">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="a9c28-128">傳輸</span><span class="sxs-lookup"><span data-stu-id="a9c28-128">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="a9c28-129">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="a9c28-129">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="a9c28-130">繫結</span><span class="sxs-lookup"><span data-stu-id="a9c28-130">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="a9c28-131">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="a9c28-131">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="a9c28-132">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="a9c28-132">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [\<customBinding>](custombinding.md)
