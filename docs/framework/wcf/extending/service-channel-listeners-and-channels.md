---
title: 服務：通道接聽程式和通道
ms.date: 03/30/2017
ms.assetid: 8ccbe0e8-7e55-441d-80de-5765f67542fa
ms.openlocfilehash: 0a740f5dcf682c3c140adb9c4c7c9678c4eae132
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/07/2019
ms.locfileid: "70797177"
---
# <a name="service-channel-listeners-and-channels"></a><span data-ttu-id="dad6e-102">服務：通道接聽程式和通道</span><span class="sxs-lookup"><span data-stu-id="dad6e-102">Service: Channel listeners and channels</span></span>

<span data-ttu-id="dad6e-103">通道物件有三種類別：通道、通道接聽程式和通道處理站。</span><span class="sxs-lookup"><span data-stu-id="dad6e-103">There are three categories of channel objects: channels, channel listeners, and channel factories.</span></span> <span data-ttu-id="dad6e-104">通道是介於應用程式與通道堆疊之間的介面。</span><span class="sxs-lookup"><span data-stu-id="dad6e-104">Channels are the interface between the application and the channel stack.</span></span> <span data-ttu-id="dad6e-105">通道接聽程式負責建立接收 (或接聽) 端的通道，一般用來回應新傳入的訊息或連線。</span><span class="sxs-lookup"><span data-stu-id="dad6e-105">Channel listeners are responsible for creating channels on the receive (or listen) side, typically in response to a new incoming message or connection.</span></span> <span data-ttu-id="dad6e-106">通道處理站負責建立傳送端的通道，以初始化與端點的通訊。</span><span class="sxs-lookup"><span data-stu-id="dad6e-106">Channel factories are responsible for creating channels on the send side to initiate communication with an endpoint.</span></span>

## <a name="channel-listeners-and-channels"></a><span data-ttu-id="dad6e-107">通道接聽程式和通道</span><span class="sxs-lookup"><span data-stu-id="dad6e-107">Channel listeners and channels</span></span>

<span data-ttu-id="dad6e-108">通道接聽程式負責建立通道並接收來自網路或下一層的訊息。</span><span class="sxs-lookup"><span data-stu-id="dad6e-108">Channel listeners are responsible for creating channels and receiving messages from the layer below or from the network.</span></span> <span data-ttu-id="dad6e-109">接收到的訊息會透過通道接聽程式所建立的通道傳遞至上一層。</span><span class="sxs-lookup"><span data-stu-id="dad6e-109">Received messages are delivered to the layer above using a channel that is created by the channel listener.</span></span>

<span data-ttu-id="dad6e-110">下列圖表會說明接收訊息與將之傳遞至上一層的處理序。</span><span class="sxs-lookup"><span data-stu-id="dad6e-110">The following diagram illustrates the process of receiving messages and delivering them to the layer above.</span></span>

<span data-ttu-id="dad6e-111">![通道接聽程式和通道](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")</span><span class="sxs-lookup"><span data-stu-id="dad6e-111">![Channel listeners and channels](./media/wcfc-wcfchannelsigure1highlevelc.gif "wcfc_WCFChannelsigure1HighLevelc")</span></span>

<span data-ttu-id="dad6e-112">負責接收訊息並透過通道傳遞至上一層的通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="dad6e-112">A channel listener receiving messages and delivering to the layer above through channels.</span></span>

<span data-ttu-id="dad6e-113">儘管實作時也許不會真的用到佇列，在概念上處理序還是可以做成位於每個通道內部的佇列模型。</span><span class="sxs-lookup"><span data-stu-id="dad6e-113">The process can be conceptually modeled as a queue inside each channel although the implementation may not actually use a queue.</span></span> <span data-ttu-id="dad6e-114">通道接聽程式負責接收來自下一層或網路的訊息，並將其放到佇列中。</span><span class="sxs-lookup"><span data-stu-id="dad6e-114">The channel listener is responsible for receiving messages from the layer below or the network and putting them in the queue.</span></span> <span data-ttu-id="dad6e-115">通道負責從佇列取得訊息，並在上一層要求訊息時，將它交給上一層，例如呼叫通道上的 `Receive`。</span><span class="sxs-lookup"><span data-stu-id="dad6e-115">The channel is responsible for getting messages from the queue and handing them to the layer above when that layer asks for a message, for example by calling `Receive` on the channel.</span></span>

<span data-ttu-id="dad6e-116">WCF 會為此程式提供基類 helper。</span><span class="sxs-lookup"><span data-stu-id="dad6e-116">WCF provides base class helpers for this process.</span></span> <span data-ttu-id="dad6e-117">（如需本文所討論之通道協助程式類別的圖表，請參閱[通道模型總覽](channel-model-overview.md)）。</span><span class="sxs-lookup"><span data-stu-id="dad6e-117">(For a diagram of the channel helper classes discussed in this article, see [Channel Model Overview](channel-model-overview.md).)</span></span>

- <span data-ttu-id="dad6e-118">類別會執行[開發通道](developing-channels.md)的步驟2中所述的狀態機器，並加以強制執行。<xref:System.ServiceModel.ICommunicationObject> <xref:System.ServiceModel.Channels.CommunicationObject></span><span class="sxs-lookup"><span data-stu-id="dad6e-118">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine described in step 2 of [Developing Channels](developing-channels.md).</span></span>

- <span data-ttu-id="dad6e-119"><xref:System.ServiceModel.Channels.ChannelManagerBase> 類別會實作 <xref:System.ServiceModel.Channels.CommunicationObject>，並為 <xref:System.ServiceModel.Channels.ChannelFactoryBase> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase> 提供統一的基底類別。</span><span class="sxs-lookup"><span data-stu-id="dad6e-119">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="dad6e-120"><xref:System.ServiceModel.Channels.ChannelManagerBase> 類別可以和 <xref:System.ServiceModel.Channels.ChannelBase> 一起運作，而後者是實作 <xref:System.ServiceModel.Channels.IChannel> 的基底類別。</span><span class="sxs-lookup"><span data-stu-id="dad6e-120">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>

- <span data-ttu-id="dad6e-121"><xref:System.ServiceModel.Channels.ChannelFactoryBase> `OnCreateChannel`類別會執行`CreateChannel`和，<xref:System.ServiceModel.Channels.IChannelFactory>並將多載合併為單一抽象方法。 <xref:System.ServiceModel.Channels.ChannelManagerBase></span><span class="sxs-lookup"><span data-stu-id="dad6e-121">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>

- <span data-ttu-id="dad6e-122"><xref:System.ServiceModel.Channels.ChannelListenerBase> 類別會實作 <xref:System.ServiceModel.Channels.IChannelListener>。</span><span class="sxs-lookup"><span data-stu-id="dad6e-122">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="dad6e-123">它會負責基礎的狀態管理。</span><span class="sxs-lookup"><span data-stu-id="dad6e-123">It takes care of basic state management.</span></span>

<span data-ttu-id="dad6e-124">下列討論是以[傳輸為基礎：UDP](../samples/transport-udp.md)範例。</span><span class="sxs-lookup"><span data-stu-id="dad6e-124">The following discussion is based upon the [Transport: UDP](../samples/transport-udp.md) sample.</span></span>

## <a name="creating-a-channel-listener"></a><span data-ttu-id="dad6e-125">建立通道接聽程式</span><span class="sxs-lookup"><span data-stu-id="dad6e-125">Creating a channel listener</span></span>

<span data-ttu-id="dad6e-126">範例`UdpChannelListener`所執行的衍生<xref:System.ServiceModel.Channels.ChannelListenerBase>自類別。</span><span class="sxs-lookup"><span data-stu-id="dad6e-126">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="dad6e-127">它會使用單一 UDP 通訊端來接收資料包。</span><span class="sxs-lookup"><span data-stu-id="dad6e-127">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="dad6e-128">`OnOpen` 方法會透過非同步迴圈的 UDP 通訊端來接收資料，</span><span class="sxs-lookup"><span data-stu-id="dad6e-128">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="dad6e-129">然後透過下列訊息編碼系統將資料轉換為訊息：</span><span class="sxs-lookup"><span data-stu-id="dad6e-129">The data are then converted into messages using the message encoding system:</span></span>

```csharp
message = UdpConstants.MessageEncoder.ReadMessage(
  new ArraySegment<byte>(buffer, 0, count),
  bufferManager
);
```

<span data-ttu-id="dad6e-130">由於相同的資料包通道代表來自幾個來源的訊息，因此 `UdpChannelListener` 是單一接聽程式。</span><span class="sxs-lookup"><span data-stu-id="dad6e-130">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="dad6e-131">一次最多隻會<xref:System.ServiceModel.Channels.IChannel>有一個與此接聽程式相關聯的作用中。</span><span class="sxs-lookup"><span data-stu-id="dad6e-131">There is at most one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="dad6e-132">只有當 <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> 方法所傳回的通道被接著處理後，範例才會產生另一個通道。</span><span class="sxs-lookup"><span data-stu-id="dad6e-132">The sample generates another one only if a channel that is returned by the <xref:System.ServiceModel.Channels.ChannelListenerBase%601.AcceptChannel%2A> method is subsequently disposed.</span></span> <span data-ttu-id="dad6e-133">當收到訊息時，就會將它加入這個單一通道的佇列中。</span><span class="sxs-lookup"><span data-stu-id="dad6e-133">When a message is received, it's enqueued into this singleton channel.</span></span>

### <a name="udpinputchannel"></a><span data-ttu-id="dad6e-134">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="dad6e-134">UdpInputChannel</span></span>

<span data-ttu-id="dad6e-135">`UdpInputChannel` 類別會實作 <xref:System.ServiceModel.Channels.IInputChannel>。</span><span class="sxs-lookup"><span data-stu-id="dad6e-135">The `UdpInputChannel` class implements <xref:System.ServiceModel.Channels.IInputChannel>.</span></span> <span data-ttu-id="dad6e-136">它包含由 `UdpChannelListener` 通訊端所填入的傳入訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="dad6e-136">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="dad6e-137">這些訊息佇列會由 <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> 方法加以清除。</span><span class="sxs-lookup"><span data-stu-id="dad6e-137">These messages are dequeued by the <xref:System.ServiceModel.Channels.IInputChannel.Receive%2A> method.</span></span>
