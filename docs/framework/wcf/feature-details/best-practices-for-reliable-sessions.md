---
title: 可靠的工作階段最佳做法
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61857983"
---
# <a name="best-practices-for-reliable-sessions"></a><span data-ttu-id="6901d-102">可靠的工作階段最佳做法</span><span class="sxs-lookup"><span data-stu-id="6901d-102">Best Practices for Reliable Sessions</span></span>

<span data-ttu-id="6901d-103">本主題會討論最佳做法的可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="6901d-103">This topic discusses best practices for reliable sessions.</span></span>

## <a name="setting-maxtransferwindowsize"></a><span data-ttu-id="6901d-104">設定 MaxTransferWindowSize</span><span class="sxs-lookup"><span data-stu-id="6901d-104">Setting MaxTransferWindowSize</span></span>

<span data-ttu-id="6901d-105">Windows Communication Foundation (WCF) 中的可靠工作階段會使用傳輸窗口將訊息保留在用戶端和服務。</span><span class="sxs-lookup"><span data-stu-id="6901d-105">Reliable sessions in Windows Communication Foundation (WCF) use a transfer window to hold messages on the client and service.</span></span> <span data-ttu-id="6901d-106">可設定的屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表傳輸窗口可保留的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="6901d-106">The configurable property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indicates how many messages the transfer window can hold.</span></span>

<span data-ttu-id="6901d-107">在傳送端，這表示傳輸窗口可以等候認可; 期間保留的訊息數目在接收者，表示要緩衝處理服務的訊息數目。</span><span class="sxs-lookup"><span data-stu-id="6901d-107">On the sender, this indicates how many messages the transfer window can hold while waiting for acknowledgements; on the receiver, it indicates how many messages to buffer for the service.</span></span>

<span data-ttu-id="6901d-108">選擇正確的大小，會影響網路效率和服務的最佳的容量。</span><span class="sxs-lookup"><span data-stu-id="6901d-108">Choosing the right size impacts the efficiency of the network and the optimal capacity of the service.</span></span> <span data-ttu-id="6901d-109">下列各節將詳細說明選擇此屬性的值影響的值時的考量事項。</span><span class="sxs-lookup"><span data-stu-id="6901d-109">The following sections detail what to consider when choosing a value for this property and the impact of the value.</span></span>

<span data-ttu-id="6901d-110">預設的傳輸窗口大小為 8 則訊息。</span><span class="sxs-lookup"><span data-stu-id="6901d-110">The default transfer window size is eight messages.</span></span>

### <a name="efficient-use-of-the-network"></a><span data-ttu-id="6901d-111">有效率地使用網路</span><span class="sxs-lookup"><span data-stu-id="6901d-111">Efficient use of the network</span></span>

<span data-ttu-id="6901d-112">在此情況下，詞彙*網路*對應至為基礎的用戶端 （傳送者） 和服務 （接收者） 之間的通訊使用的所有項目。</span><span class="sxs-lookup"><span data-stu-id="6901d-112">In this context, the term *network* corresponds to everything used as the basis of communication between a client (sender) and a service (receiver).</span></span> <span data-ttu-id="6901d-113">這包括傳輸連線及任何媒介或橋接器之間，包括 SOAP 路由器或 HTTP proxy/防火牆。</span><span class="sxs-lookup"><span data-stu-id="6901d-113">This includes the transport connections and any intermediary or bridges in between, including SOAP routers or HTTP proxies/firewalls.</span></span>

<span data-ttu-id="6901d-114">有效率地使用網路可確保充分運用網路功能。</span><span class="sxs-lookup"><span data-stu-id="6901d-114">Efficient use of the network ensures that network capacity is fully used.</span></span> <span data-ttu-id="6901d-115">可以透過網路每秒傳送的資料量 (*資料速率*) 和寄件者的資料傳送至接收者所花費的時間 (*延遲*) 如何有效地影響網路這項承諾。</span><span class="sxs-lookup"><span data-stu-id="6901d-115">Both the amount of data that can be transferred per second over the network (*data rate*) and the time it takes to transfer data from the sender to the receiver (*latency*) impact how effectively the network is utilized.</span></span>

<span data-ttu-id="6901d-116">在傳送端，屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表其傳輸窗口在等候認可期間能夠保留的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="6901d-116">On the sender, the property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> indicates how many messages its transfer window can hold while waiting for acknowledgements.</span></span> <span data-ttu-id="6901d-117">如果網路延遲很高，而且為了確保回應的傳送者和有效的網路使用率，您應該增加傳輸窗口大小。</span><span class="sxs-lookup"><span data-stu-id="6901d-117">If the network latency is high and in order to ensure a responsive sender and effective network utilization, you should increase the transfer window size.</span></span>

<span data-ttu-id="6901d-118">例如寄件者配合資料速率，其值為即使，延遲可能是高如果寄件者與接收者之間存在好幾個媒介或資料都必須通過失真的媒介或網路。</span><span class="sxs-lookup"><span data-stu-id="6901d-118">For example even if the sender keeps up with data rate, latency could be high if several intermediaries exist between the sender and receiver or the data must pass through a lossy intermediary or network.</span></span> <span data-ttu-id="6901d-119">因此，寄件者必須等候其傳輸窗之訊息的通知，然後再接受新的訊息，以在網路上傳送。</span><span class="sxs-lookup"><span data-stu-id="6901d-119">Thus, the sender has to wait for acknowledgements for the messages in its transfer window before accepting new messages to send on the wire.</span></span> <span data-ttu-id="6901d-120">緩衝區小而具有高延遲，較少的有效網路使用率。</span><span class="sxs-lookup"><span data-stu-id="6901d-120">The smaller the buffer with high latency, the less effective the network utilization.</span></span> <span data-ttu-id="6901d-121">相反地，太高的傳輸窗口會影響服務，因為服務可能需要擷取並更新與高比率的用戶端傳送的資料。</span><span class="sxs-lookup"><span data-stu-id="6901d-121">On the other hand, too high a transfer window size may impact the service because the service may need to catch up to the high rate of data sent by the client.</span></span>

### <a name="running-the-service-to-capacity"></a><span data-ttu-id="6901d-122">容量來執行服務</span><span class="sxs-lookup"><span data-stu-id="6901d-122">Running the service to capacity</span></span>

<span data-ttu-id="6901d-123">盡可能有效率地使用網路，在理想情況下您也想要達到最佳的產能執行的服務。</span><span class="sxs-lookup"><span data-stu-id="6901d-123">As much as the network is used efficiently, ideally you also want the service to run at optimal capacity.</span></span> <span data-ttu-id="6901d-124">接收端上的傳輸窗口大小屬性代表接收端可以緩衝處理的訊息數量。</span><span class="sxs-lookup"><span data-stu-id="6901d-124">The transfer window size property on the receiver indicates how many messages the receiver can buffer.</span></span> <span data-ttu-id="6901d-125">這項訊息緩衝處理作業不只能協助控制網路流量，同時能讓服務效能發揮到極致。</span><span class="sxs-lookup"><span data-stu-id="6901d-125">This message buffering helps not only the network flow control but also enables the service to run to full capacity.</span></span> <span data-ttu-id="6901d-126">如果緩衝區是一則訊息，而且訊息抵達服務處理速度的範例，然後網路可能會捨棄訊息，並可能會浪費或是未能充分運用容量。</span><span class="sxs-lookup"><span data-stu-id="6901d-126">For example if the buffer is one message and messages arrive faster than the service can process them, then the network might drop messages and capacity might be wasted or underutilized.</span></span>

<span data-ttu-id="6901d-127">使用緩衝區會增加服務的可用性，因為能夠一面接收與緩衝處理先前接收的訊息時的訊息。</span><span class="sxs-lookup"><span data-stu-id="6901d-127">Using a buffer increases the availability of the service as it concurrently receives and buffers a message while processing the previously received messages.</span></span>

<span data-ttu-id="6901d-128">我們建議使用相同`MaxTransferWindowSize`寄件者和接收者。</span><span class="sxs-lookup"><span data-stu-id="6901d-128">We recommended that you use the same `MaxTransferWindowSize` on both the sender and receiver.</span></span>

### <a name="enabling-flow-control"></a><span data-ttu-id="6901d-129">啟用流量控制</span><span class="sxs-lookup"><span data-stu-id="6901d-129">Enabling flow control</span></span>

<span data-ttu-id="6901d-130">*流量控制*是一種機制可確保傳送者和接收者跟上彼此，也就是訊息會取用及處理，因為它們產生速度。</span><span class="sxs-lookup"><span data-stu-id="6901d-130">*Flow control* is a mechanism that ensures that the sender and receiver keep pace with each other, that is, the messages are consumed and acted upon as fast as they're produced.</span></span> <span data-ttu-id="6901d-131">用戶端與服務上的傳輸窗口大小可確保傳送端與接收端都有同樣合理的同步處理時間。</span><span class="sxs-lookup"><span data-stu-id="6901d-131">The transfer window size on the client and service ensures that the sender and receiver are within a reasonable window of synchronization.</span></span>

<span data-ttu-id="6901d-132">我們強烈建議您設定屬性<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A>至`true`當您使用 WCF 用戶端和 WCF 服務之間可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="6901d-132">We highly recommended that you set the property <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> to `true` when you're using a reliable session between a WCF client and a WCF service.</span></span>

## <a name="setting-maxpendingchannels"></a><span data-ttu-id="6901d-133">設定 MaxPendingChannels</span><span class="sxs-lookup"><span data-stu-id="6901d-133">Setting MaxPendingChannels</span></span>

<span data-ttu-id="6901d-134">撰寫服務時，可讓來自不同的用戶端的可靠工作階段通訊，就可以有許多用戶端建立的可靠工作階段服務在相同的時間。</span><span class="sxs-lookup"><span data-stu-id="6901d-134">When writing a service that enables reliable session communication from different clients, it's possible to have many clients establish a reliable session to the service at the same time.</span></span> <span data-ttu-id="6901d-135">在這些情況中，服務將視 `MaxPendingChannels` 屬性做出回應。</span><span class="sxs-lookup"><span data-stu-id="6901d-135">The response of the service in these situations depends on the `MaxPendingChannels` property.</span></span>

<span data-ttu-id="6901d-136">當傳送端對接收端建立可靠工作階段通道時，彼此之間的信號交換會建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="6901d-136">When the sender creates a reliable session channel to a receiver, a handshake between them establishes a reliable session.</span></span> <span data-ttu-id="6901d-137">一旦建立了可靠工作階段，就會將通道放到擱置的通道佇列中，等候服務來接受它。</span><span class="sxs-lookup"><span data-stu-id="6901d-137">After the reliable session is established, the channel is put in a pending channel queue for acceptance by the service.</span></span> <span data-ttu-id="6901d-138">`MaxPendingChannels` 屬性代表可處於此狀態的通道數量。</span><span class="sxs-lookup"><span data-stu-id="6901d-138">The `MaxPendingChannels` property indicates how many channels can be in this state.</span></span>

<span data-ttu-id="6901d-139">很可能是它無法在此接受多個通道的狀態中的服務。</span><span class="sxs-lookup"><span data-stu-id="6901d-139">It's possible for the service to be in a state where it can't accept more channels.</span></span> <span data-ttu-id="6901d-140">如果佇列已滿，嘗試建立可靠工作階段遭到拒絕，並在用戶端必須重試一次。</span><span class="sxs-lookup"><span data-stu-id="6901d-140">If the queue is full, an attempt to establish a reliable session is rejected, and the client must retry.</span></span>

<span data-ttu-id="6901d-141">此外，也可以在佇列中擱置的通道保持在佇列中持續時間較長。</span><span class="sxs-lookup"><span data-stu-id="6901d-141">It's also possible that the pending channels in the queue remain in the queue for a longer duration.</span></span> <span data-ttu-id="6901d-142">在此同時，可靠工作階段閒置逾時可能會發生，導致通道轉換至 faulted 狀態。</span><span class="sxs-lookup"><span data-stu-id="6901d-142">In the meantime, an inactivity timeout on the reliable session may occur, causing the channel to transition to a faulted state.</span></span>

<span data-ttu-id="6901d-143">在撰寫時同時服務多個用戶端的服務，您應該設定為適合您需求的值。</span><span class="sxs-lookup"><span data-stu-id="6901d-143">When writing a service that services multiple clients simultaneously, you should set a value that's suitable for your needs.</span></span> <span data-ttu-id="6901d-144">設定太高的值`MaxPendingChannels`屬性會影響您的工作集。</span><span class="sxs-lookup"><span data-stu-id="6901d-144">Setting too high a value for the `MaxPendingChannels` property impacts your working set.</span></span>

<span data-ttu-id="6901d-145">預設值為<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A>是四個通道。</span><span class="sxs-lookup"><span data-stu-id="6901d-145">The default value for <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> is four channels.</span></span>

## <a name="reliable-sessions-and-hosting"></a><span data-ttu-id="6901d-146">可靠工作階段與裝載</span><span class="sxs-lookup"><span data-stu-id="6901d-146">Reliable sessions and hosting</span></span>

<span data-ttu-id="6901d-147">Web 裝載的服務，會使用可靠工作階段時，您應該記住下列重要事項：</span><span class="sxs-lookup"><span data-stu-id="6901d-147">When web hosting a service that uses reliable sessions, you should keep the following important considerations in mind:</span></span>

- <span data-ttu-id="6901d-148">可靠工作階段是可設定狀態的，而且可透過 AppDomain 來維護狀態。</span><span class="sxs-lookup"><span data-stu-id="6901d-148">Reliable sessions are stateful, and state is maintained in the AppDomain.</span></span> <span data-ttu-id="6901d-149">意思就是，所有屬於可靠工作階段一部分的訊息，都必須透過同一個 AppDomain 來處理。</span><span class="sxs-lookup"><span data-stu-id="6901d-149">This means that all messages that are part of a reliable session must be processed in the same AppDomain.</span></span> <span data-ttu-id="6901d-150">Web 伺服陣列與 web 處理序區伺服陣列或處理序區的大小大於一個節點無法保證此條件約束。</span><span class="sxs-lookup"><span data-stu-id="6901d-150">Web farms and web gardens where the size of the farm or garden is greater than one node can't guarantee this constraint.</span></span>

- <span data-ttu-id="6901d-151">使用雙重 HTTP 通道的可靠工作階段 (例如，使用`WsDualHttpBinding`) 可能需要超過兩個 HTTP 連線每個用戶端的預設值。</span><span class="sxs-lookup"><span data-stu-id="6901d-151">Reliable sessions using dual HTTP channels (for example, using `WsDualHttpBinding`) can require more than the default of two HTTP connections per-client.</span></span> <span data-ttu-id="6901d-152">這表示雙工可靠工作階段可能需要最多兩個連線每種方法，因為並行的應用程式與通訊協定訊息可以在任何時候傳輸每種方法。</span><span class="sxs-lookup"><span data-stu-id="6901d-152">This means a duplex reliable session can require up to two connections each way because concurrent application and protocol messages may be transferring each way at any given time.</span></span> <span data-ttu-id="6901d-153">某些狀況下根據服務的訊息交換模式，這表示它是可能發生死結 web 裝載的服務，使用雙重 HTTP 與可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="6901d-153">Under certain conditions depending on the message exchange pattern of the service, this means that it's possible to deadlock a web-hosted service using dual HTTP and reliable sessions.</span></span> <span data-ttu-id="6901d-154">若要增加允許的 HTTP 連線，每個用戶端數目，將下列新增至相關的組態檔 (例如*web.config*有問題的服務):</span><span class="sxs-lookup"><span data-stu-id="6901d-154">To increase the number of allowable HTTP connections per client, add the following to the relevant configuration file (for example, *web.config* of the service in question):</span></span>

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  <span data-ttu-id="6901d-155">值`maxconnection`屬性是所需的連線數。</span><span class="sxs-lookup"><span data-stu-id="6901d-155">The value of the `maxconnection` attribute is the number of connections needed.</span></span> <span data-ttu-id="6901d-156">在此情況下，至少應該是四個連線。</span><span class="sxs-lookup"><span data-stu-id="6901d-156">The minimum in this case should be four connections.</span></span>
