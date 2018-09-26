---
title: 服務： 通道接聽程式與通道
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 88bfdc879e4f3c7df6b2c4035c7ed7fdc2b4c41d
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47176409"
---
# <a name="service-channel-listeners-and-channels"></a><span data-ttu-id="6882f-102">服務： 通道接聽程式與通道</span><span class="sxs-lookup"><span data-stu-id="6882f-102">Service: Channel listeners and channels</span></span>

<span data-ttu-id="6882f-103">有三種通道物件的類別： 通道、 通道接聽程式，以及通道處理站。</span><span class="sxs-lookup"><span data-stu-id="6882f-103">There are three categories of channel objects: channels, channel listeners, and channel factories.</span></span> <span data-ttu-id="6882f-104">通道是介於應用程式與通道堆疊之間的介面。</span><span class="sxs-lookup"><span data-stu-id="6882f-104">Channels are the interface between the application and the channel stack.</span></span> <span data-ttu-id="6882f-105">通道接聽程式負責建立接收 (或接聽) 端的通道，一般用來回應新傳入的訊息或連線。</span><span class="sxs-lookup"><span data-stu-id="6882f-105">Channel listeners are responsible for creating channels on the receive (or listen) side, typically in response to a new incoming message or connection.</span></span> <span data-ttu-id="6882f-106">通道處理站負責建立傳送端的通道，以初始化與端點的通訊。</span><span class="sxs-lookup"><span data-stu-id="6882f-106">Channel factories are responsible for creating channels on the send side to initiate communication with an endpoint.</span></span>

## <a name="channel-listeners-and-channels"></a><span data-ttu-id="6882f-107">通道接聽程式和通道</span><span class="sxs-lookup"><span data-stu-id="6882f-107">Channel listeners and channels</span></span>

<span data-ttu-id="6882f-108">通道接聽程式負責建立通道並接收來自網路或下一層的訊息。</span><span class="sxs-lookup"><span data-stu-id="6882f-108">Channel listeners are responsible for creating channels and receiving messages from the layer below or from the network.</span></span> <span data-ttu-id="6882f-109">接收到的訊息會透過通道接聽程式所建立的通道傳遞至上一層。</span><span class="sxs-lookup"><span data-stu-id="6882f-109">Received messages are delivered to the layer above using a channel that is created by the channel listener.</span></span>

<span data-ttu-id="6882f-110">下列圖表會說明接收訊息與將之傳遞至上一層的處理序。</span><span class="sxs-lookup"><span data-stu-id="6882f-110">The following diagram illustrates the process of receiving messages and delivering them to the layer above.</span></span>

<span data-ttu-id="6882f-111">![通道接聽程式與通道](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")</span><span class="sxs-lookup"><span data-stu-id="6882f-111">![Channel listeners and channels](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")</span></span>

<span data-ttu-id="6882f-112">負責接收訊息並透過通道傳遞至上一層的通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6882f-112">A channel listener receiving messages and delivering to the layer above through channels.</span></span>

<span data-ttu-id="6882f-113">儘管實作時也許不會真的用到佇列，在概念上處理序還是可以做成位於每個通道內部的佇列模型。</span><span class="sxs-lookup"><span data-stu-id="6882f-113">The process can be conceptually modeled as a queue inside each channel although the implementation may not actually use a queue.</span></span> <span data-ttu-id="6882f-114">通道接聽程式負責接收來自下一層或網路的訊息，並將其放到佇列中。</span><span class="sxs-lookup"><span data-stu-id="6882f-114">The channel listener is responsible for receiving messages from the layer below or the network and putting them in the queue.</span></span> <span data-ttu-id="6882f-115">通道負責從佇列取得訊息，並在上一層要求訊息時，將它交給上一層，例如呼叫通道上的 `Receive`。</span><span class="sxs-lookup"><span data-stu-id="6882f-115">The channel is responsible for getting messages from the queue and handing them to the layer above when that layer asks for a message, for example by calling `Receive` on the channel.</span></span>

<span data-ttu-id="6882f-116">WCF 會提供此程序中的基底類別協助程式。</span><span class="sxs-lookup"><span data-stu-id="6882f-116">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="6882f-117">(如本文所討論的通道協助程式類別的圖表，請參閱 <<c0> [ 通道模型概觀](channel-model-overview.md)。)</span><span class="sxs-lookup"><span data-stu-id="6882f-117">(For a diagram of the channel helper classes discussed in this article, see [Channel Model Overview](channel-model-overview.md).)</span></span>

- <span data-ttu-id="6882f-118"><xref:System.ServiceModel.Channels.CommunicationObject>類別會實作<xref:System.ServiceModel.ICommunicationObject>並強制執行的步驟 2 中所述的狀態機器[開發通道](developing-channels.md)。</span><span class="sxs-lookup"><span data-stu-id="6882f-118">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>

- <span data-ttu-id="6882f-119"><xref:System.ServiceModel.Channels.ChannelManagerBase> 類別會實作 <xref:System.ServiceModel.Channels.CommunicationObject>，並為 <xref:System.ServiceModel.Channels.ChannelFactoryBase> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase> 提供統一的基底類別。</span><span class="sxs-lookup"><span data-stu-id="6882f-119">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="6882f-120"><xref:System.ServiceModel.Channels.ChannelManagerBase> 類別可以和 <xref:System.ServiceModel.Channels.ChannelBase> 一起運作，而後者是實作 <xref:System.ServiceModel.Channels.IChannel> 的基底類別。</span><span class="sxs-lookup"><span data-stu-id="6882f-120">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>

- <span data-ttu-id="6882f-121"><xref:System.ServiceModel.Channels.ChannelFactoryBase>類別會實作<xref:System.ServiceModel.Channels.ChannelManagerBase>並<xref:System.ServiceModel.Channels.IChannelFactory>並合併`CreateChannel`其中一個多載`OnCreateChannel`抽象方法。</span><span class="sxs-lookup"><span data-stu-id="6882f-121">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>

- <span data-ttu-id="6882f-122"><xref:System.ServiceModel.Channels.ChannelListenerBase> 類別會實作 <xref:System.ServiceModel.Channels.IChannelListener>。</span><span class="sxs-lookup"><span data-stu-id="6882f-122">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="6882f-123">它會負責基礎的狀態管理。</span><span class="sxs-lookup"><span data-stu-id="6882f-123">It takes care of basic state management.</span></span>

<span data-ttu-id="6882f-124">以下討論以基礎[傳輸： UDP](../../../../docs/framework/wcf/samples/transport-udp.md)範例。</span><span class="sxs-lookup"><span data-stu-id="6882f-124">The following discussion is based upon the [Transport: UDP](../../../../docs/framework/wcf/samples/transport-udp.md) sample.</span></span>

## <a name="creating-a-channel-listener"></a><span data-ttu-id="6882f-125">建立通道接聽程式</span><span class="sxs-lookup"><span data-stu-id="6882f-125">Creating a channel listener</span></span>

<span data-ttu-id="6882f-126">`UdpChannelListener`此範例會實作衍生自<xref:System.ServiceModel.Channels.ChannelListenerBase>類別。</span><span class="sxs-lookup"><span data-stu-id="6882f-126">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="6882f-127">它會使用單一 UDP 通訊端來接收資料包。</span><span class="sxs-lookup"><span data-stu-id="6882f-127">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="6882f-128">`OnOpen` 方法會透過非同步迴圈的 UDP 通訊端來接收資料，</span><span class="sxs-lookup"><span data-stu-id="6882f-128">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="6882f-129">然後透過下列訊息編碼系統將資料轉換為訊息：</span><span class="sxs-lookup"><span data-stu-id="6882f-129">The data are then converted into messages using the message encoding system:</span></span>

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

<span data-ttu-id="6882f-130">由於相同的資料包通道代表來自幾個來源的訊息，因此 `UdpChannelListener` 是單一接聽程式。</span><span class="sxs-lookup"><span data-stu-id="6882f-130">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="6882f-131">大部分的一個作用<xref:System.ServiceModel.Channels.IChannel>與此接聽程式相關聯，一次。</span><span class="sxs-lookup"><span data-stu-id="6882f-131">There is at most one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="6882f-132">只有當 <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> 方法所傳回的通道被接著處理後，範例才會產生另一個通道。</span><span class="sxs-lookup"><span data-stu-id="6882f-132">The sample generates another one only if a channel that is returned by the <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> method is subsequently disposed.</span></span> <span data-ttu-id="6882f-133">收到訊息時，它會加入此單一通道佇列。</span><span class="sxs-lookup"><span data-stu-id="6882f-133">When a message is received, it's enqueued into this singleton channel.</span></span>

### <a name="udpinputchannel"></a><span data-ttu-id="6882f-134">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="6882f-134">UdpInputChannel</span></span>

<span data-ttu-id="6882f-135">`UdpInputChannel` 類別會實作 <xref:System.ServiceModel.Channels.IInputChannel>。</span><span class="sxs-lookup"><span data-stu-id="6882f-135">The `UdpInputChannel` class implements <xref:System.ServiceModel.Channels.IInputChannel>.</span></span> <span data-ttu-id="6882f-136">它包含由 `UdpChannelListener` 通訊端所填入的傳入訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="6882f-136">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="6882f-137">這些訊息佇列會由 <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> 方法加以清除。</span><span class="sxs-lookup"><span data-stu-id="6882f-137">These messages are dequeued by the <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> method.</span></span>
