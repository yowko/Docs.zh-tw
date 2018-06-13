---
title: 可靠的工作階段最佳做法
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491621"
---
# <a name="best-practices-for-reliable-sessions"></a><span data-ttu-id="b5f7f-102">可靠的工作階段最佳做法</span><span class="sxs-lookup"><span data-stu-id="b5f7f-102">Best Practices for Reliable Sessions</span></span>

<span data-ttu-id="b5f7f-103">本主題討論的可靠工作階段的最佳作法。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-103">This topic discusses best practices for reliable sessions.</span></span>

## <a name="setting-maxtransferwindowsize"></a><span data-ttu-id="b5f7f-104">設定 MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="b5f7f-104">Setting MaxTransferWindowSize</span></span>

<span data-ttu-id="b5f7f-105">可靠工作階段中 Windows Communication Foundation (WCF) 會使用傳輸窗口，來保留用戶端和服務上的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-105">Reliable sessions in Windows Communication Foundation (WCF) use a transfer window to hold messages on the client and service.</span></span> <span data-ttu-id="b5f7f-106">可設定的屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表傳輸窗口可保留的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-106">The configurable property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indicates how many messages the transfer window can hold.</span></span>

<span data-ttu-id="b5f7f-107">在傳送端，這表示傳輸窗口可以保存等候認可; 期間的訊息數目在收件者，它會指出服務緩衝處理的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-107">On the sender, this indicates how many messages the transfer window can hold while waiting for acknowledgements; on the receiver, it indicates how many messages to buffer for the service.</span></span>

<span data-ttu-id="b5f7f-108">選擇正確的大小會影響網路效率和服務的最大的效用。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-108">Choosing the right size impacts the efficiency of the network and the optimal capacity of the service.</span></span> <span data-ttu-id="b5f7f-109">下列各節將詳細說明，請考慮選擇的值，這個屬性與值的影響。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-109">The following sections detail what to consider when choosing a value for this property and the impact of the value.</span></span>

<span data-ttu-id="b5f7f-110">預設的傳輸窗口大小是 8 個訊息。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-110">The default transfer window size is eight messages.</span></span>

### <a name="efficient-use-of-the-network"></a><span data-ttu-id="b5f7f-111">有效率地使用網路</span><span class="sxs-lookup"><span data-stu-id="b5f7f-111">Efficient use of the network</span></span>

<span data-ttu-id="b5f7f-112">在此內容中，詞彙*網路*對應至為基礎的用戶端 （傳送者） 和服務 （接收者） 之間的通訊使用的所有項目。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-112">In this context, the term *network* corresponds to everything used as the basis of communication between a client (sender) and a service (receiver).</span></span> <span data-ttu-id="b5f7f-113">這包括傳輸連線及任何媒介或橋接器之間，包括 SOAP 路由器或 HTTP proxy/防火牆等。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-113">This includes the transport connections and any intermediary or bridges in between, including SOAP routers or HTTP proxies/firewalls.</span></span>

<span data-ttu-id="b5f7f-114">有效率地使用網路可確保充分運用網路功能。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-114">Efficient use of the network ensures that network capacity is fully used.</span></span> <span data-ttu-id="b5f7f-115">可以透過網路每秒傳送的資料量 (*資料速率*) 以及寄件者的資料傳送至收件者的時間 (*延遲*) 如何有效地影響網路利用。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-115">Both the amount of data that can be transferred per second over the network (*data rate*) and the time it takes to transfer data from the sender to the receiver (*latency*) impact how effectively the network is utilized.</span></span>

<span data-ttu-id="b5f7f-116">在傳送端，屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表其傳輸窗口在等候認可期間能夠保留的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-116">On the sender, the property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indicates how many messages its transfer window can hold while waiting for acknowledgements.</span></span> <span data-ttu-id="b5f7f-117">如果網路延遲性很高，以確保能繼續回應的傳送者和有效的網路使用率，您應該增加傳輸窗口大小。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-117">If the network latency is high and in order to ensure a responsive sender and effective network utilization, you should increase the transfer window size.</span></span>

<span data-ttu-id="b5f7f-118">例如即使傳送端保持資料的速率，延遲可能是高如果傳送者與接收者之間存在好幾個媒介或是資料必須通過失真媒介或網路。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-118">For example even if the sender keeps up with data rate, latency could be high if several intermediaries exist between the sender and receiver or the data must pass through a lossy intermediary or network.</span></span> <span data-ttu-id="b5f7f-119">因此，寄件者並等候其傳輸窗口中之訊息的通知，才能接受新的網路上傳送的訊息。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-119">Thus, the sender has to wait for acknowledgements for the messages in its transfer window before accepting new messages to send on the wire.</span></span> <span data-ttu-id="b5f7f-120">緩衝區小而高延遲，較少的有效網路使用率。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-120">The smaller the buffer with high latency, the less effective the network utilization.</span></span> <span data-ttu-id="b5f7f-121">另一方面，太大的傳輸窗口可能會影響服務，因為服務可能需要高的用戶端傳送的資料速率趕上進度。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-121">On the other hand, too high a transfer window size may impact the service because the service may need to catch up to the high rate of data sent by the client.</span></span>

### <a name="running-the-service-to-capacity"></a><span data-ttu-id="b5f7f-122">執行服務容量</span><span class="sxs-lookup"><span data-stu-id="b5f7f-122">Running the service to capacity</span></span>

<span data-ttu-id="b5f7f-123">盡可能有效率地使用網路時，在理想情況下您也想在最大的效用執行服務。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-123">As much as the network is used efficiently, ideally you also want the service to run at optimal capacity.</span></span> <span data-ttu-id="b5f7f-124">接收端上的傳輸窗口大小屬性代表接收端可以緩衝處理的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-124">The transfer window size property on the receiver indicates how many messages the receiver can buffer.</span></span> <span data-ttu-id="b5f7f-125">這項訊息緩衝處理作業不只能協助控制網路流量，同時能讓服務效能發揮到極致。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-125">This message buffering helps not only the network flow control but also enables the service to run to full capacity.</span></span> <span data-ttu-id="b5f7f-126">例如，如果緩衝區為一則訊息，而訊息抵達的速度快過服務處理，網路可能會捨棄訊息，然後可能會浪費或是未能充分運用容量。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-126">For example if the buffer is one message and messages arrive faster than the service can process them, then the network might drop messages and capacity might be wasted or underutilized.</span></span>

<span data-ttu-id="b5f7f-127">使用緩衝區會增加服務的可用性，因為能夠一面接收與緩衝處理先前接收的訊息時處理訊息。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-127">Using a buffer increases the availability of the service as it concurrently receives and buffers a message while processing the previously received messages.</span></span>

<span data-ttu-id="b5f7f-128">我們建議使用的相同`MaxTransferWindowSize`寄件者和接收者上。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-128">We recommended that you use the same `MaxTransferWindowSize` on both the sender and receiver.</span></span>

### <a name="enabling-flow-control"></a><span data-ttu-id="b5f7f-129">啟用流量控制</span><span class="sxs-lookup"><span data-stu-id="b5f7f-129">Enabling flow control</span></span>

<span data-ttu-id="b5f7f-130">*流量控制*是一種機制可確保寄件者與接收者跟彼此，也就是取用與處理訊息，它們所產生的一樣快。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-130">*Flow control* is a mechanism that ensures that the sender and receiver keep pace with each other, that is, the messages are consumed and acted upon as fast as they're produced.</span></span> <span data-ttu-id="b5f7f-131">用戶端與服務上的傳輸窗口大小可確保傳送端與接收端都有同樣合理的同步處理時間。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-131">The transfer window size on the client and service ensures that the sender and receiver are within a reasonable window of synchronization.</span></span>

<span data-ttu-id="b5f7f-132">我們強烈建議您將屬性<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A>至`true`當您使用 WCF 用戶端和 WCF 服務之間可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-132">We highly recommended that you set the property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> to `true` when you're using a reliable session between a WCF client and a WCF service.</span></span>

## <a name="setting-maxpendingchannels"></a><span data-ttu-id="b5f7f-133">設定 MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="b5f7f-133">Setting MaxPendingChannels</span></span>

<span data-ttu-id="b5f7f-134">在撰寫啟用來自不同用戶端的可靠工作階段通訊的服務時，很可能有許多用戶端建立的可靠工作階段服務在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-134">When writing a service that enables reliable session communication from different clients, it's possible to have many clients establish a reliable session to the service at the same time.</span></span> <span data-ttu-id="b5f7f-135">在這些情況中，服務將視 `MaxPendingChannels` 屬性做出回應。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-135">The response of the service in these situations depends on the `MaxPendingChannels` property.</span></span>

<span data-ttu-id="b5f7f-136">當傳送端對接收端建立可靠工作階段通道時，彼此之間的信號交換會建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-136">When the sender creates a reliable session channel to a receiver, a handshake between them establishes a reliable session.</span></span> <span data-ttu-id="b5f7f-137">一旦建立了可靠工作階段，就會將通道放到擱置的通道佇列中，等候服務來接受它。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-137">After the reliable session is established, the channel is put in a pending channel queue for acceptance by the service.</span></span> <span data-ttu-id="b5f7f-138">`MaxPendingChannels` 屬性代表可處於此狀態的通道數量。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-138">The `MaxPendingChannels` property indicates how many channels can be in this state.</span></span>

<span data-ttu-id="b5f7f-139">它有可能的狀態，它無法在此接受多個通道的服務。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-139">It's possible for the service to be in a state where it can't accept more channels.</span></span> <span data-ttu-id="b5f7f-140">如果佇列已滿，嘗試建立可靠工作階段遭到拒絕，並在用戶端必須重試。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-140">If the queue is full, an attempt to establish a reliable session is rejected, and the client must retry.</span></span>

<span data-ttu-id="b5f7f-141">此外，也可以在佇列中的暫止通道保留在佇列較長時間。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-141">It's also possible that the pending channels in the queue remain in the queue for a longer duration.</span></span> <span data-ttu-id="b5f7f-142">在此同時，可靠工作階段的閒置逾時可能會發生，導致通道轉換為錯誤狀態。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-142">In the meantime, an inactivity timeout on the reliable session may occur, causing the channel to transition to a faulted state.</span></span>

<span data-ttu-id="b5f7f-143">當撰寫同時服務多個用戶端的服務，您應該設定為適合您需求的值。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-143">When writing a service that services multiple clients simultaneously, you should set a value that's suitable for your needs.</span></span> <span data-ttu-id="b5f7f-144">設定太高的值`MaxPendingChannels`屬性會影響您的工作集。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-144">Setting too high a value for the `MaxPendingChannels` property impacts your working set.</span></span>

<span data-ttu-id="b5f7f-145">預設值為<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A>是四個通道。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-145">The default value for <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> is four channels.</span></span>

## <a name="reliable-sessions-and-hosting"></a><span data-ttu-id="b5f7f-146">可靠工作階段與裝載</span><span class="sxs-lookup"><span data-stu-id="b5f7f-146">Reliable sessions and hosting</span></span>

<span data-ttu-id="b5f7f-147">當 web 裝載使用可靠工作階段的服務，您應該記住下列重要事項：</span><span class="sxs-lookup"><span data-stu-id="b5f7f-147">When web hosting a service that uses reliable sessions, you should keep the following important considerations in mind:</span></span>

- <span data-ttu-id="b5f7f-148">可靠工作階段具狀態，而且可透過 AppDomain 來維護狀態。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-148">Reliable sessions are stateful, and state is maintained in the AppDomain.</span></span> <span data-ttu-id="b5f7f-149">意思就是，所有屬於可靠工作階段一部分的訊息，都必須透過同一個 AppDomain 來處理。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-149">This means that all messages that are part of a reliable session must be processed in the same AppDomain.</span></span> <span data-ttu-id="b5f7f-150">Web 伺服陣列與 web 處理序區的伺服陣列或處理序區大小大於一個節點無法保證此條件約束。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-150">Web farms and web gardens where the size of the farm or garden is greater than one node can't guarantee this constraint.</span></span>

- <span data-ttu-id="b5f7f-151">使用雙重 HTTP 通道的可靠工作階段 (例如，使用`WsDualHttpBinding`) 可能需要超過兩個 HTTP 連線個別用戶端的預設值。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-151">Reliable sessions using dual HTTP channels (for example, using `WsDualHttpBinding`) can require more than the default of two HTTP connections per-client.</span></span> <span data-ttu-id="b5f7f-152">這表示雙工可靠工作階段可以要求最多兩個連線每一種方式，因為並行的應用程式和通訊協定訊息可能會在任何指定時間傳送每一種方式。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-152">This means a duplex reliable session can require up to two connections each way because concurrent application and protocol messages may be transferring each way at any given time.</span></span> <span data-ttu-id="b5f7f-153">在特定條件之服務的訊息交換模式，這表示它是可以將使用雙重 HTTP 與可靠工作階段的 web 裝載服務鎖死。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-153">Under certain conditions depending on the message exchange pattern of the service, this means that it's possible to deadlock a web-hosted service using dual HTTP and reliable sessions.</span></span> <span data-ttu-id="b5f7f-154">若要增加允許的 HTTP 連線，每個用戶端數目，加入下列相關的組態檔 (例如， *web.config*有問題的服務):</span><span class="sxs-lookup"><span data-stu-id="b5f7f-154">To increase the number of allowable HTTP connections per client, add the following to the relevant configuration file (for example, *web.config* of the service in question):</span></span>

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  <span data-ttu-id="b5f7f-155">值`maxconnection`屬性是必要的連線數。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-155">The value of the `maxconnection` attribute is the number of connections needed.</span></span> <span data-ttu-id="b5f7f-156">在此情況下，至少應該是四個連接。</span><span class="sxs-lookup"><span data-stu-id="b5f7f-156">The minimum in this case should be four connections.</span></span>
