---
title: <connectionPoolSettings>
ms.date: 03/30/2017
ms.assetid: 6fa7fa65-2c6e-4eab-b8cf-7690112c0be5
ms.openlocfilehash: 842173c7bd9673a1e08c93d5ed650a42b9d979e5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400473"
---
# <a name="connectionpoolsettings"></a><span data-ttu-id="cb3d4-101">\<connectionPoolSettings></span><span class="sxs-lookup"><span data-stu-id="cb3d4-101">\<connectionPoolSettings></span></span>
<span data-ttu-id="cb3d4-102">為具名管道繫結指定其他連線集區設定。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-102">Specifies additional connection pool settings for a Named Pipe binding.</span></span>  
  
<span data-ttu-id="cb3d4-103">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-103">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="cb3d4-104">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-104">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="cb3d4-105">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-105">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="cb3d4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<customBinding >** ](custombinding.md)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-106">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<customBinding>**](custombinding.md)</span></span>\
<span data-ttu-id="cb3d4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="cb3d4-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="cb3d4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<namedPipeTransport >** ](namedpipetransport.md)</span><span class="sxs-lookup"><span data-stu-id="cb3d4-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<namedPipeTransport>**](namedpipetransport.md)</span></span>\
<span data-ttu-id="cb3d4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<connectionPoolSettings >**</span><span class="sxs-lookup"><span data-stu-id="cb3d4-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<connectionPoolSettings>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cb3d4-110">語法</span><span class="sxs-lookup"><span data-stu-id="cb3d4-110">Syntax</span></span>  
  
```xml  
<connectionPoolSettings groupName="String"
                        idleTimeout="TimeSpan"
                        maxOutboundConnectionsPerEndpoint="Integer" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="cb3d4-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="cb3d4-111">Attributes and Elements</span></span>  
 <span data-ttu-id="cb3d4-112">下列各節描述屬性、子項目和父項目。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-112">The following sections describe attributes, child elements, and parent elements.</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="cb3d4-113">屬性</span><span class="sxs-lookup"><span data-stu-id="cb3d4-113">Attributes</span></span>  
  
|<span data-ttu-id="cb3d4-114">屬性</span><span class="sxs-lookup"><span data-stu-id="cb3d4-114">Attribute</span></span>|<span data-ttu-id="cb3d4-115">說明</span><span class="sxs-lookup"><span data-stu-id="cb3d4-115">Description</span></span>|  
|---------------|-----------------|  
|`groupName`|<span data-ttu-id="cb3d4-116">定義用於傳出通道之連線集區名稱的字串。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-116">A string that defines the name of the connection pool used for outgoing channels.</span></span> <span data-ttu-id="cb3d4-117">在資料流處理模式中，不會共用連線，意指會停用連線集區。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-117">In streamed mode, connections are not shared, meaning that connection pooling is disabled.</span></span> <span data-ttu-id="cb3d4-118">預設為 "default" 字串。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-118">The default is a "default" string.</span></span> <span data-ttu-id="cb3d4-119">您可以修改這個值，將特定用戶端的連線隔離在不同群組中。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-119">You can modify this value to isolate the connections for a particular client into separate groups.</span></span>|  
|`idleTimeout`|<span data-ttu-id="cb3d4-120">正的 <xref:System.TimeSpan>，指定連線在中斷連接之前，可以閒置的最長時間。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-120">A positive <xref:System.TimeSpan> that specifies the maximum time the connection can be idle before being disconnected.</span></span> <span data-ttu-id="cb3d4-121">預設為 00:02:00。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-121">The default is 00:02:00.</span></span>|  
|`maxOutboundConnectionsPerEndpoint`|<span data-ttu-id="cb3d4-122">正整數，指定與服務初始化之遠端端點連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-122">A positive integer that specifies the maximum number of connections to a remote endpoint initiated by the service.</span></span> <span data-ttu-id="cb3d4-123">超過這個限制的連線都會進入佇列，直到低於此限制的空間可用為止。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-123">Connections in excess of the limit are queued until a space below the limit becomes available.</span></span> <span data-ttu-id="cb3d4-124">`idleTimeout` 會限制在擲回例外狀況之前，連線保留在佇列中的持續期間。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-124">The `idleTimeout` limits the duration in which connections remain queued before an exception is thrown.</span></span> <span data-ttu-id="cb3d4-125">預設值為 10。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-125">The default is 10.</span></span><br /><br /> <span data-ttu-id="cb3d4-126">這個屬性會限制從用戶端到特定服務端點的同時作用中連線數目。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-126">This attribute limits the number of simultaneous active connections from the client to a particular service endpoint.</span></span> <span data-ttu-id="cb3d4-127">如果因為擁有更多個作用中的用戶端連線而超出這個值，對用戶端而言，服務可能會像是沒有回應。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-127">If this value is exceeded by having more active client connections, the service may appear unresponsive to the client.</span></span> <span data-ttu-id="cb3d4-128">在這種情況下，這個值應調整為超過預期的、用戶端對特定端點之同時連線的數目上限。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-128">In this case, this value should be adjusted to exceed the maximum number of expected simultaneous client connections to a specific endpoint.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="cb3d4-129">子元素</span><span class="sxs-lookup"><span data-stu-id="cb3d4-129">Child Elements</span></span>  
 <span data-ttu-id="cb3d4-130">無。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-130">None.</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="cb3d4-131">父項目</span><span class="sxs-lookup"><span data-stu-id="cb3d4-131">Parent Elements</span></span>  
  
|<span data-ttu-id="cb3d4-132">項目</span><span class="sxs-lookup"><span data-stu-id="cb3d4-132">Element</span></span>|<span data-ttu-id="cb3d4-133">描述</span><span class="sxs-lookup"><span data-stu-id="cb3d4-133">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="cb3d4-134">\<namedPipeTransport></span><span class="sxs-lookup"><span data-stu-id="cb3d4-134">\<namedPipeTransport></span></span>](namedpipetransport.md)|<span data-ttu-id="cb3d4-135">定義傳輸，此傳輸會使用具名管道產生可傳輸訊息的通道。</span><span class="sxs-lookup"><span data-stu-id="cb3d4-135">Defines a transport that causes a channel to transfer messages using named pipes.</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="cb3d4-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="cb3d4-136">See also</span></span>

- <xref:System.ServiceModel.Configuration.NamedPipeConnectionPoolSettingsElement>
- <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement.ConnectionPoolSettings%2A>
- <xref:System.ServiceModel.Channels.NamedPipeConnectionPoolSettings>
- <xref:System.ServiceModel.Channels.TransportBindingElement>
- <xref:System.ServiceModel.Channels.CustomBinding>
- [<span data-ttu-id="cb3d4-137">傳輸</span><span class="sxs-lookup"><span data-stu-id="cb3d4-137">Transports</span></span>](../../../wcf/feature-details/transports.md)
- [<span data-ttu-id="cb3d4-138">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="cb3d4-138">Choosing a Transport</span></span>](../../../wcf/feature-details/choosing-a-transport.md)
- [<span data-ttu-id="cb3d4-139">繫結</span><span class="sxs-lookup"><span data-stu-id="cb3d4-139">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="cb3d4-140">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="cb3d4-140">Extending Bindings</span></span>](../../../wcf/extending/extending-bindings.md)
- [<span data-ttu-id="cb3d4-141">自訂繫結</span><span class="sxs-lookup"><span data-stu-id="cb3d4-141">Custom Bindings</span></span>](../../../wcf/extending/custom-bindings.md)
- [<span data-ttu-id="cb3d4-142">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="cb3d4-142">\<customBinding></span></span>](custombinding.md)
