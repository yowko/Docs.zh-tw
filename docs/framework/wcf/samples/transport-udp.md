---
title: 傳輸：UDP
ms.date: 03/30/2017
ms.assetid: 738705de-ad3e-40e0-b363-90305bddb140
ms.openlocfilehash: 4ae4bf22f452035d10ecba6bcf93bf580ab7f5f8
ms.sourcegitcommit: 9b1ac36b6c80176fd4e20eb5bfcbd9d56c3264cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/28/2019
ms.locfileid: "67422164"
---
# <a name="transport-udp"></a><span data-ttu-id="55062-102">傳輸：UDP</span><span class="sxs-lookup"><span data-stu-id="55062-102">Transport: UDP</span></span>
<span data-ttu-id="55062-103">UDP 傳輸範例示範如何實作 UDP 單點傳播與多點傳送做為自訂的 Windows Communication Foundation (WCF) 傳輸。</span><span class="sxs-lookup"><span data-stu-id="55062-103">The UDP Transport sample demonstrates how to implement UDP unicast and multicast as a custom Windows Communication Foundation (WCF) transport.</span></span> <span data-ttu-id="55062-104">此範例描述，以建立自訂傳輸在 WCF 中，使用通道架構並遵循 WCF 的最佳做法建議的程序。</span><span class="sxs-lookup"><span data-stu-id="55062-104">The sample describes the recommended procedure for creating a custom transport in WCF, by using the channel framework and following WCF best practices.</span></span> <span data-ttu-id="55062-105">建立自訂傳輸的步驟如下：</span><span class="sxs-lookup"><span data-stu-id="55062-105">The steps to create a custom transport are as follows:</span></span>  
  
1. <span data-ttu-id="55062-106">決定哪一個通道[訊息交換模式](#MessageExchangePatterns)（IOutputChannel、 IInputChannel、 IDuplexChannel、 IRequestChannel 或 IReplyChannel） ChannelFactory 和 channellistener 所支援。</span><span class="sxs-lookup"><span data-stu-id="55062-106">Decide which of the channel [Message Exchange Patterns](#MessageExchangePatterns) (IOutputChannel, IInputChannel, IDuplexChannel, IRequestChannel, or IReplyChannel) your ChannelFactory and ChannelListener will support.</span></span> <span data-ttu-id="55062-107">然後決定是否要支援這些介面的工作階段變化。</span><span class="sxs-lookup"><span data-stu-id="55062-107">Then decide whether you will support the sessionful variations of these interfaces.</span></span>  
  
2. <span data-ttu-id="55062-108">建立支援「訊息交換模式」的通道處理站和接聽項。</span><span class="sxs-lookup"><span data-stu-id="55062-108">Create a channel factory and listener that support your Message Exchange Pattern.</span></span>  
  
3. <span data-ttu-id="55062-109">確認已將所有網路特定例外狀況正規化為適當的 <xref:System.ServiceModel.CommunicationException> 衍生類別。</span><span class="sxs-lookup"><span data-stu-id="55062-109">Ensure that any network-specific exceptions are normalized to the appropriate derived class of <xref:System.ServiceModel.CommunicationException>.</span></span>  
  
4. <span data-ttu-id="55062-110">新增[\<繫結 >](../../../../docs/framework/misc/binding.md)將自訂傳輸新增至通道堆疊的項目。</span><span class="sxs-lookup"><span data-stu-id="55062-110">Add a [\<binding>](../../../../docs/framework/misc/binding.md) element that adds the custom transport to a channel stack.</span></span> <span data-ttu-id="55062-111">如需詳細資訊，請參閱 <<c0> [ 新增繫結項目](#AddingABindingElement)。</span><span class="sxs-lookup"><span data-stu-id="55062-111">For more information, see [Adding a Binding Element](#AddingABindingElement).</span></span>  
  
5. <span data-ttu-id="55062-112">新增繫結元素延伸區段，即可將新的繫結元素公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="55062-112">Add a binding element extension section to expose the new binding element to the configuration system.</span></span>  
  
6. <span data-ttu-id="55062-113">新增中繼資料延伸，即可將功能傳達給其他端點。</span><span class="sxs-lookup"><span data-stu-id="55062-113">Add metadata extensions to communicate capabilities to other endpoints.</span></span>  
  
7. <span data-ttu-id="55062-114">新增繫結，此繫結會根據妥善定義的設定檔來預先設定繫結項目的堆疊。</span><span class="sxs-lookup"><span data-stu-id="55062-114">Add a binding that pre-configures a stack of binding elements according to a well-defined profile.</span></span> <span data-ttu-id="55062-115">如需詳細資訊，請參閱 <<c0> [ 加入標準繫結](#AddingAStandardBinding)。</span><span class="sxs-lookup"><span data-stu-id="55062-115">For more information, see [Adding a Standard Binding](#AddingAStandardBinding).</span></span>  
  
8. <span data-ttu-id="55062-116">新增繫結區段和繫結組態項目，即可將繫結公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="55062-116">Add a binding section and binding configuration element to expose the binding to the configuration system.</span></span> <span data-ttu-id="55062-117">如需詳細資訊，請參閱 <<c0> [ 新增組態支援](#AddingConfigurationSupport)。</span><span class="sxs-lookup"><span data-stu-id="55062-117">For more information, see [Adding Configuration Support](#AddingConfigurationSupport).</span></span>  
  
<a name="MessageExchangePatterns"></a>   
## <a name="message-exchange-patterns"></a><span data-ttu-id="55062-118">訊息交換模式</span><span class="sxs-lookup"><span data-stu-id="55062-118">Message Exchange Patterns</span></span>  
 <span data-ttu-id="55062-119">撰寫自訂傳輸時的第一個步驟是決定傳輸所需要的「訊息交換模式」(Message Exchange Patterns，MEP)。</span><span class="sxs-lookup"><span data-stu-id="55062-119">The first step in writing a custom transport is to decide which Message Exchange Patterns (MEPs) are required for the transport.</span></span> <span data-ttu-id="55062-120">您可以從三個 MEP 中選擇：</span><span class="sxs-lookup"><span data-stu-id="55062-120">There are three MEPs to choose from:</span></span>  
  
- <span data-ttu-id="55062-121">資料包 (IInputChannel/IOutputChannel)</span><span class="sxs-lookup"><span data-stu-id="55062-121">Datagram (IInputChannel/IOutputChannel)</span></span>  
  
     <span data-ttu-id="55062-122">當使用資料包 (Datagram) MEP 時，用戶端會使用「射後不理」(Fire and Forget) 交換來傳送訊息。</span><span class="sxs-lookup"><span data-stu-id="55062-122">When using a datagram MEP, a client sends a message using a "fire and forget" exchange.</span></span> <span data-ttu-id="55062-123">射後不理交換是一種需要以超出範圍之外的方式確認傳遞成功的交換。</span><span class="sxs-lookup"><span data-stu-id="55062-123">A fire and forget exchange is one that requires out-of-band confirmation of successful delivery.</span></span> <span data-ttu-id="55062-124">訊息可能會在傳輸時遺失而永遠無法抵達服務。</span><span class="sxs-lookup"><span data-stu-id="55062-124">The message might be lost in transit and never reach the service.</span></span> <span data-ttu-id="55062-125">即使傳送作業在用戶端已成功完成，也無法保證遠端端點已接收到該訊息。</span><span class="sxs-lookup"><span data-stu-id="55062-125">If the send operation completes successfully at the client end, it does not guarantee that the remote endpoint has received the message.</span></span> <span data-ttu-id="55062-126">資料包是訊息的基本建置組塊，您可以在資料包的最上層建立自己的通訊協定，其中包括可靠的通訊協定和安全的通訊協定。</span><span class="sxs-lookup"><span data-stu-id="55062-126">The datagram is a fundamental building block for messaging, as you can build your own protocols on top of it—including reliable protocols and secure protocols.</span></span> <span data-ttu-id="55062-127">用戶端資料包通道會實作 <xref:System.ServiceModel.Channels.IOutputChannel> 介面，服務資料包通道則會實作 <xref:System.ServiceModel.Channels.IInputChannel> 介面。</span><span class="sxs-lookup"><span data-stu-id="55062-127">Client datagram channels implement the <xref:System.ServiceModel.Channels.IOutputChannel> interface and service datagram channels implement the <xref:System.ServiceModel.Channels.IInputChannel> interface.</span></span>  
  
- <span data-ttu-id="55062-128">要求-回應 (IRequestChannel/IReplyChannel)</span><span class="sxs-lookup"><span data-stu-id="55062-128">Request-Response (IRequestChannel/IReplyChannel)</span></span>  
  
     <span data-ttu-id="55062-129">在此 MEP 中，會傳送訊息，而且會接收回覆。</span><span class="sxs-lookup"><span data-stu-id="55062-129">In this MEP, a message is sent, and a reply is received.</span></span> <span data-ttu-id="55062-130">此模式是由要求-回應組合所構成。</span><span class="sxs-lookup"><span data-stu-id="55062-130">The pattern consists of request-response pairs.</span></span> <span data-ttu-id="55062-131">遠端程序呼叫 (Remote Procedure Call，RPC) 與瀏覽器的 GET 就是要求-回應呼叫的例子。</span><span class="sxs-lookup"><span data-stu-id="55062-131">Examples of request-response calls are remote procedure calls (RPC) and browser GETs.</span></span> <span data-ttu-id="55062-132">這個模式又稱為「半雙工」。</span><span class="sxs-lookup"><span data-stu-id="55062-132">This pattern is also known as Half-Duplex.</span></span> <span data-ttu-id="55062-133">在此 MEP 中，用戶端通道會實作 <xref:System.ServiceModel.Channels.IRequestChannel>，服務通道則會實作 <xref:System.ServiceModel.Channels.IReplyChannel>。</span><span class="sxs-lookup"><span data-stu-id="55062-133">In this MEP, client channels implement <xref:System.ServiceModel.Channels.IRequestChannel> and service channels implement <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span>  
  
- <span data-ttu-id="55062-134">雙工 (IDuplexChannel)</span><span class="sxs-lookup"><span data-stu-id="55062-134">Duplex (IDuplexChannel)</span></span>  
  
     <span data-ttu-id="55062-135">雙工 MEP 會允許用戶端傳送任意數目的訊息，並以任何順序接收這些訊息。</span><span class="sxs-lookup"><span data-stu-id="55062-135">The duplex MEP allows an arbitrary number of messages to be sent by a client and received in any order.</span></span> <span data-ttu-id="55062-136">雙工 MEP 就像是電話交談，談話中說出的每個字都是一則訊息。</span><span class="sxs-lookup"><span data-stu-id="55062-136">The duplex MEP is like a phone conversation, where each word being spoken is a message.</span></span> <span data-ttu-id="55062-137">由於兩端都可以透過此種 MEP 來傳送和接收訊息，所以由用戶端和服務通道所實作的介面會是 <xref:System.ServiceModel.Channels.IDuplexChannel>。</span><span class="sxs-lookup"><span data-stu-id="55062-137">Because both sides can send and receive in this MEP, the interface implemented by the client and service channels is <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
 <span data-ttu-id="55062-138">上述的每個 MEP 都能支援「工作階段」(Session)。</span><span class="sxs-lookup"><span data-stu-id="55062-138">Each of these MEPs can also support sessions.</span></span> <span data-ttu-id="55062-139">工作階段感知通道提供的新增功能可以將通道中傳送及接收的所有訊息相互關聯。</span><span class="sxs-lookup"><span data-stu-id="55062-139">The added functionality provided by a session-aware channel is that it correlates all messages sent and received on a channel.</span></span> <span data-ttu-id="55062-140">因為要求與回覆相互關聯，「要求-回應」模式是一個獨立的兩訊息工作階段。</span><span class="sxs-lookup"><span data-stu-id="55062-140">The Request-Response pattern is a stand-alone two-message session, as the request and reply are correlated.</span></span> <span data-ttu-id="55062-141">相較之下，支援工作階段的「要求-回應」模式，就意味著該通道上的所有要求/回應組合都是彼此相互關聯的。</span><span class="sxs-lookup"><span data-stu-id="55062-141">In contrast, the Request-Response pattern that supports sessions implies that all request/response pairs on that channel are correlated with each other.</span></span> <span data-ttu-id="55062-142">如此一來，您總共有六種 MEP (資料包、要求-回應、雙工、搭配工作階段的資料包、搭配工作階段的要求-回應以及搭配工作階段的雙工) 可以選擇。</span><span class="sxs-lookup"><span data-stu-id="55062-142">This gives you a total of six MEPs—Datagram, Request-Response, Duplex, Datagram with sessions, Request-Response with sessions, and Duplex with sessions—to choose from.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="55062-143">就 UDP 傳輸而言，唯一支援的 MEP 是「資料包」，因為 UDP 原本就是「射後不理」(Fire and Forget) 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="55062-143">For the UDP transport, the only MEP that is supported is Datagram, because UDP is inherently a "fire and forget" protocol.</span></span>  
  
### <a name="the-icommunicationobject-and-the-wcf-object-lifecycle"></a><span data-ttu-id="55062-144">ICommunicationObject 和 WCF 物件生命週期</span><span class="sxs-lookup"><span data-stu-id="55062-144">The ICommunicationObject and the WCF object lifecycle</span></span>  
 <span data-ttu-id="55062-145">WCF 有通用的狀態機器用來管理這類物件的生命週期<xref:System.ServiceModel.Channels.IChannel>， <xref:System.ServiceModel.Channels.IChannelFactory>，和<xref:System.ServiceModel.Channels.IChannelListener>，用來通訊。</span><span class="sxs-lookup"><span data-stu-id="55062-145">WCF has a common state machine that is used for managing the lifecycle of objects like <xref:System.ServiceModel.Channels.IChannel>, <xref:System.ServiceModel.Channels.IChannelFactory>, and <xref:System.ServiceModel.Channels.IChannelListener> that are used for communication.</span></span> <span data-ttu-id="55062-146">這些通訊物件可能呈現的狀態有五種。</span><span class="sxs-lookup"><span data-stu-id="55062-146">There are five states in which these communication objects can exist.</span></span> <span data-ttu-id="55062-147">這些狀態是由 <xref:System.ServiceModel.CommunicationState> 列舉表示，如下所述：</span><span class="sxs-lookup"><span data-stu-id="55062-147">These states are represented by the <xref:System.ServiceModel.CommunicationState> enumeration, and are as follows:</span></span>  
  
- <span data-ttu-id="55062-148">建立：這是狀態<xref:System.ServiceModel.ICommunicationObject>當它第一次具現化。</span><span class="sxs-lookup"><span data-stu-id="55062-148">Created: This is the state of a <xref:System.ServiceModel.ICommunicationObject> when it is first instantiated.</span></span> <span data-ttu-id="55062-149">在這個狀態下不會發生任何輸入/輸出 (I/O)。</span><span class="sxs-lookup"><span data-stu-id="55062-149">No input/output (I/O) occurs in this state.</span></span>  
  
- <span data-ttu-id="55062-150">正在開啟：物件會轉換至此狀態時<xref:System.ServiceModel.ICommunicationObject.Open%2A>呼叫。</span><span class="sxs-lookup"><span data-stu-id="55062-150">Opening: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Open%2A> is called.</span></span> <span data-ttu-id="55062-151">此時會將屬性設為不變，並且可以開始輸入/輸出。</span><span class="sxs-lookup"><span data-stu-id="55062-151">At this point properties are made immutable, and input/output can begin.</span></span> <span data-ttu-id="55062-152">只有從 Created 狀態轉變過來，這種轉換才算有效。</span><span class="sxs-lookup"><span data-stu-id="55062-152">This transition is valid only from the Created state.</span></span>  
  
- <span data-ttu-id="55062-153">開啟：物件會轉換至開啟的處理序完成時，此狀態。</span><span class="sxs-lookup"><span data-stu-id="55062-153">Opened: Objects transition to this state when the open process completes.</span></span> <span data-ttu-id="55062-154">只有從 Opening 狀態轉變過來，這種轉換才算有效。</span><span class="sxs-lookup"><span data-stu-id="55062-154">This transition is valid only from the Opening state.</span></span> <span data-ttu-id="55062-155">此時，物件完全無法進行傳輸。</span><span class="sxs-lookup"><span data-stu-id="55062-155">At this point, the object is fully usable for transfer.</span></span>  
  
- <span data-ttu-id="55062-156">關閉：物件會轉換至此狀態時<xref:System.ServiceModel.ICommunicationObject.Close%2A>正常關機程序呼叫。</span><span class="sxs-lookup"><span data-stu-id="55062-156">Closing: Objects transition to this state when <xref:System.ServiceModel.ICommunicationObject.Close%2A> is called for a graceful shutdown.</span></span> <span data-ttu-id="55062-157">只有從 Opened 狀態轉變過來，這種轉換才算有效。</span><span class="sxs-lookup"><span data-stu-id="55062-157">This transition is valid only from the Opened state.</span></span>  
  
- <span data-ttu-id="55062-158">關閉：在 Closed 狀態物件就不再可用。</span><span class="sxs-lookup"><span data-stu-id="55062-158">Closed: In the Closed state objects are no longer usable.</span></span> <span data-ttu-id="55062-159">一般來說，大部分組態仍然可供存取以便檢查，但是無法進行任何通訊。</span><span class="sxs-lookup"><span data-stu-id="55062-159">In general, most configuration is still accessible for inspection, but no communication can occur.</span></span> <span data-ttu-id="55062-160">這種狀態相當於正在處置。</span><span class="sxs-lookup"><span data-stu-id="55062-160">This state is equivalent to being disposed.</span></span>  
  
- <span data-ttu-id="55062-161">發生錯誤：在 Faulted 狀態中，物件會是存取以便檢查，但無法供使用。</span><span class="sxs-lookup"><span data-stu-id="55062-161">Faulted: In the Faulted state, objects are accessible to inspection but no longer usable.</span></span> <span data-ttu-id="55062-162">當發生無法修復的錯誤時，物件會轉換至此狀態。</span><span class="sxs-lookup"><span data-stu-id="55062-162">When a non-recoverable error occurs, the object transitions into this state.</span></span> <span data-ttu-id="55062-163">在這個狀態中的唯一有效的轉換是`Closed`狀態。</span><span class="sxs-lookup"><span data-stu-id="55062-163">The only valid transition from this state is into the `Closed` state.</span></span>  
  
 <span data-ttu-id="55062-164">每個狀態轉換都會引發一些事件。</span><span class="sxs-lookup"><span data-stu-id="55062-164">There are events that fire for each state transition.</span></span> <span data-ttu-id="55062-165"><xref:System.ServiceModel.ICommunicationObject.Abort%2A> 方法可在任何時間加以呼叫，讓物件立即從目前的狀態轉換為 Closed 狀態。</span><span class="sxs-lookup"><span data-stu-id="55062-165">The <xref:System.ServiceModel.ICommunicationObject.Abort%2A> method can be called at any time, and causes the object to transition immediately from its current state into the Closed state.</span></span> <span data-ttu-id="55062-166">呼叫 <xref:System.ServiceModel.ICommunicationObject.Abort%2A> 會終止任何未完成的工作。</span><span class="sxs-lookup"><span data-stu-id="55062-166">Calling <xref:System.ServiceModel.ICommunicationObject.Abort%2A> terminates any unfinished work.</span></span>  
  
<a name="ChannelAndChannelListener"></a>   
## <a name="channel-factory-and-channel-listener"></a><span data-ttu-id="55062-167">通道處理站和通道接聽項</span><span class="sxs-lookup"><span data-stu-id="55062-167">Channel Factory and Channel Listener</span></span>  
 <span data-ttu-id="55062-168">撰寫自訂傳輸的下一個步驟是，建立用戶端通道的 <xref:System.ServiceModel.Channels.IChannelFactory> 實作以及服務通道的 <xref:System.ServiceModel.Channels.IChannelListener> 實作。</span><span class="sxs-lookup"><span data-stu-id="55062-168">The next step in writing a custom transport is to create an implementation of <xref:System.ServiceModel.Channels.IChannelFactory> for client channels and of <xref:System.ServiceModel.Channels.IChannelListener> for service channels.</span></span> <span data-ttu-id="55062-169">通道層會使用建構通道所需的處理站模式。</span><span class="sxs-lookup"><span data-stu-id="55062-169">The channel layer uses a factory pattern for constructing channels.</span></span> <span data-ttu-id="55062-170">WCF 會提供此程序中的基底類別協助程式。</span><span class="sxs-lookup"><span data-stu-id="55062-170">WCF provides base class helpers for this process.</span></span>  
  
- <span data-ttu-id="55062-171"><xref:System.ServiceModel.Channels.CommunicationObject> 類別會實作 <xref:System.ServiceModel.ICommunicationObject>，並強制執行先前在步驟 2 中所述的狀態機器。</span><span class="sxs-lookup"><span data-stu-id="55062-171">The <xref:System.ServiceModel.Channels.CommunicationObject> class implements <xref:System.ServiceModel.ICommunicationObject> and enforces the state machine previously described in Step 2.</span></span> 

- <span data-ttu-id="55062-172"><xref:System.ServiceModel.Channels.ChannelManagerBase> 類別會實作 <xref:System.ServiceModel.Channels.CommunicationObject>，並為 <xref:System.ServiceModel.Channels.ChannelFactoryBase> 和 <xref:System.ServiceModel.Channels.ChannelListenerBase> 提供統一的基底類別。</span><span class="sxs-lookup"><span data-stu-id="55062-172">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class implements <xref:System.ServiceModel.Channels.CommunicationObject> and provides a unified base class for <xref:System.ServiceModel.Channels.ChannelFactoryBase> and <xref:System.ServiceModel.Channels.ChannelListenerBase>.</span></span> <span data-ttu-id="55062-173"><xref:System.ServiceModel.Channels.ChannelManagerBase> 類別可以和 <xref:System.ServiceModel.Channels.ChannelBase> 一起運作，而後者是實作 <xref:System.ServiceModel.Channels.IChannel> 的基底類別。</span><span class="sxs-lookup"><span data-stu-id="55062-173">The <xref:System.ServiceModel.Channels.ChannelManagerBase> class works in conjunction with <xref:System.ServiceModel.Channels.ChannelBase>, which is a base class that implements <xref:System.ServiceModel.Channels.IChannel>.</span></span>  
  
- <span data-ttu-id="55062-174"><xref:System.ServiceModel.Channels.ChannelFactoryBase>類別會實作<xref:System.ServiceModel.Channels.ChannelManagerBase>並<xref:System.ServiceModel.Channels.IChannelFactory>並合併`CreateChannel`其中一個多載`OnCreateChannel`抽象方法。</span><span class="sxs-lookup"><span data-stu-id="55062-174">The <xref:System.ServiceModel.Channels.ChannelFactoryBase> class implements <xref:System.ServiceModel.Channels.ChannelManagerBase> and <xref:System.ServiceModel.Channels.IChannelFactory> and consolidates the `CreateChannel` overloads into one `OnCreateChannel` abstract method.</span></span>  
  
- <span data-ttu-id="55062-175"><xref:System.ServiceModel.Channels.ChannelListenerBase> 類別會實作 <xref:System.ServiceModel.Channels.IChannelListener>。</span><span class="sxs-lookup"><span data-stu-id="55062-175">The <xref:System.ServiceModel.Channels.ChannelListenerBase> class implements <xref:System.ServiceModel.Channels.IChannelListener>.</span></span> <span data-ttu-id="55062-176">它會負責基礎的狀態管理。</span><span class="sxs-lookup"><span data-stu-id="55062-176">It takes care of basic state management.</span></span>  
  
 <span data-ttu-id="55062-177">在這個範例中，處理站的實作包含在 UdpChannelFactory.cs 中，而接聽項的實作則包含在 UdpChannelListener.cs 中。</span><span class="sxs-lookup"><span data-stu-id="55062-177">In this sample, the factory implementation is contained in UdpChannelFactory.cs and the listener implementation is contained in UdpChannelListener.cs.</span></span> <span data-ttu-id="55062-178"><xref:System.ServiceModel.Channels.IChannel> 的實作是在 UdpOutputChannel.cs 和 UdpInputChannel.cs 中。</span><span class="sxs-lookup"><span data-stu-id="55062-178">The <xref:System.ServiceModel.Channels.IChannel> implementations are in UdpOutputChannel.cs and UdpInputChannel.cs.</span></span>  
  
### <a name="the-udp-channel-factory"></a><span data-ttu-id="55062-179">UDP 通道處理站</span><span class="sxs-lookup"><span data-stu-id="55062-179">The UDP Channel Factory</span></span>  
 <span data-ttu-id="55062-180">`UdpChannelFactory` 是衍生自 <xref:System.ServiceModel.Channels.ChannelFactoryBase>。</span><span class="sxs-lookup"><span data-stu-id="55062-180">The `UdpChannelFactory` derives from <xref:System.ServiceModel.Channels.ChannelFactoryBase>.</span></span> <span data-ttu-id="55062-181">範例會覆寫 <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A>，以提供訊息編碼器之訊息版本的存取權。</span><span class="sxs-lookup"><span data-stu-id="55062-181">The sample overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.GetProperty%2A> to provide access to the message version of the message encoder.</span></span> <span data-ttu-id="55062-182">範例也會覆寫 <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A>，以便在狀態機器進行轉換時卸除 <xref:System.ServiceModel.Channels.BufferManager> 的執行個體。</span><span class="sxs-lookup"><span data-stu-id="55062-182">The sample also overrides <xref:System.ServiceModel.Channels.ChannelFactoryBase.OnClose%2A> so that we can tear down our instance of <xref:System.ServiceModel.Channels.BufferManager> when the state machine transitions.</span></span>  
  
#### <a name="the-udp-output-channel"></a><span data-ttu-id="55062-183">UDP 輸出通道</span><span class="sxs-lookup"><span data-stu-id="55062-183">The UDP Output Channel</span></span>  
 <span data-ttu-id="55062-184">`UdpOutputChannel` 會實作 <xref:System.ServiceModel.Channels.IOutputChannel>。</span><span class="sxs-lookup"><span data-stu-id="55062-184">The `UdpOutputChannel` implements <xref:System.ServiceModel.Channels.IOutputChannel>.</span></span> <span data-ttu-id="55062-185">建構函式會驗證引數，並根據傳進的 <xref:System.Net.EndPoint> 建構目的地 <xref:System.ServiceModel.EndpointAddress> 物件。</span><span class="sxs-lookup"><span data-stu-id="55062-185">The constructor validates the arguments and constructs a destination <xref:System.Net.EndPoint> object based on the <xref:System.ServiceModel.EndpointAddress> that is passed in.</span></span>  
  
```csharp
this.socket = new Socket(this.remoteEndPoint.AddressFamily, SocketType.Dgram, ProtocolType.Udp);  
```  
  
 <span data-ttu-id="55062-186">可以依正常程序或非正常程序關閉通道。</span><span class="sxs-lookup"><span data-stu-id="55062-186">The channel can be closed gracefully or ungracefully.</span></span> <span data-ttu-id="55062-187">如果依正常程序關閉通道，將會關閉通訊端，並且會呼叫基底類別 `OnClose` 方法。</span><span class="sxs-lookup"><span data-stu-id="55062-187">If the channel is closed gracefully the socket is closed and a call is made to the base class `OnClose` method.</span></span> <span data-ttu-id="55062-188">如果因此發生例外狀況，則基礎結構會呼叫 `Abort`，確保已清除通道。</span><span class="sxs-lookup"><span data-stu-id="55062-188">If this throws an exception, the infrastructure calls `Abort` to ensure the channel is cleaned up.</span></span>  
  
```csharp
this.socket.Close(0);  
```  
  
 <span data-ttu-id="55062-189">接著實作`Send()`並`BeginSend()` / `EndSend()`。</span><span class="sxs-lookup"><span data-stu-id="55062-189">We then implement `Send()` and `BeginSend()`/`EndSend()`.</span></span> <span data-ttu-id="55062-190">這分成兩個主要區段。</span><span class="sxs-lookup"><span data-stu-id="55062-190">This breaks down into two main sections.</span></span> <span data-ttu-id="55062-191">首先，將訊息序列化為位元組陣列。</span><span class="sxs-lookup"><span data-stu-id="55062-191">First we serialize the message into a byte array.</span></span>  
  
```csharp
ArraySegment<byte> messageBuffer = EncodeMessage(message);  
```  
  
 <span data-ttu-id="55062-192">然後在網路上傳送產生的資料。</span><span class="sxs-lookup"><span data-stu-id="55062-192">Then we send the resulting data on the wire.</span></span>  
  
```csharp
this.socket.SendTo(messageBuffer.Array, messageBuffer.Offset, messageBuffer.Count, SocketFlags.None, this.remoteEndPoint);  
```  
  
### <a name="the-udpchannellistener"></a><span data-ttu-id="55062-193">UdpChannelListener</span><span class="sxs-lookup"><span data-stu-id="55062-193">The UdpChannelListener</span></span>  
 <span data-ttu-id="55062-194">`UdpChannelListener`此範例會實作衍生自<xref:System.ServiceModel.Channels.ChannelListenerBase>類別。</span><span class="sxs-lookup"><span data-stu-id="55062-194">The `UdpChannelListener` that the sample implements derives from the <xref:System.ServiceModel.Channels.ChannelListenerBase> class.</span></span> <span data-ttu-id="55062-195">它會使用單一 UDP 通訊端來接收資料包。</span><span class="sxs-lookup"><span data-stu-id="55062-195">It uses a single UDP socket to receive datagrams.</span></span> <span data-ttu-id="55062-196">`OnOpen` 方法會透過非同步迴圈的 UDP 通訊端來接收資料，</span><span class="sxs-lookup"><span data-stu-id="55062-196">The `OnOpen` method receives data using the UDP socket in an asynchronous loop.</span></span> <span data-ttu-id="55062-197">然後透過下列「訊息編碼架構」將資料轉換為訊息。</span><span class="sxs-lookup"><span data-stu-id="55062-197">The data are then converted into messages using the Message Encoding Framework.</span></span>  
  
```csharp
message = MessageEncoderFactory.Encoder.ReadMessage(new ArraySegment<byte>(buffer, 0, count), bufferManager);  
```  
  
 <span data-ttu-id="55062-198">由於相同的資料包通道代表來自幾個來源的訊息，因此 `UdpChannelListener` 是單一接聽程式。</span><span class="sxs-lookup"><span data-stu-id="55062-198">Because the same datagram channel represents messages that arrive from a number of sources, the `UdpChannelListener` is a singleton listener.</span></span> <span data-ttu-id="55062-199">沒有，最多一個作用<xref:System.ServiceModel.Channels.IChannel>與此接聽程式相關聯，一次。</span><span class="sxs-lookup"><span data-stu-id="55062-199">There is, at most, one active <xref:System.ServiceModel.Channels.IChannel> associated with this listener at a time.</span></span> <span data-ttu-id="55062-200">只有當 `AcceptChannel` 方法所傳回的通道被接著處理後，範例才會產生另一個通道。</span><span class="sxs-lookup"><span data-stu-id="55062-200">The sample generates another one only if a channel that is returned by the `AcceptChannel` method is subsequently disposed.</span></span> <span data-ttu-id="55062-201">收到訊息時，就會將它加入此單一通道佇列中。</span><span class="sxs-lookup"><span data-stu-id="55062-201">When a message is received, it is enqueued into this singleton channel.</span></span>  
  
#### <a name="udpinputchannel"></a><span data-ttu-id="55062-202">UdpInputChannel</span><span class="sxs-lookup"><span data-stu-id="55062-202">UdpInputChannel</span></span>  
 <span data-ttu-id="55062-203">`UdpInputChannel` 類別會實作 `IInputChannel`。</span><span class="sxs-lookup"><span data-stu-id="55062-203">The `UdpInputChannel` class implements `IInputChannel`.</span></span> <span data-ttu-id="55062-204">它包含由 `UdpChannelListener` 通訊端所填入的傳入訊息佇列。</span><span class="sxs-lookup"><span data-stu-id="55062-204">It consists of a queue of incoming messages that is populated by the `UdpChannelListener`'s socket.</span></span> <span data-ttu-id="55062-205">這些訊息佇列會由 `IInputChannel.Receive` 方法加以清除。</span><span class="sxs-lookup"><span data-stu-id="55062-205">These messages are dequeued by the `IInputChannel.Receive` method.</span></span>  
  
<a name="AddingABindingElement"></a>   
## <a name="adding-a-binding-element"></a><span data-ttu-id="55062-206">新增繫結項目</span><span class="sxs-lookup"><span data-stu-id="55062-206">Adding a Binding Element</span></span>  
 <span data-ttu-id="55062-207">既然建置了處理站和通道，就必須透過繫結公開至 ServiceModel 執行階段。</span><span class="sxs-lookup"><span data-stu-id="55062-207">Now that the factories and channels are built, we must expose them to the ServiceModel runtime through a binding.</span></span> <span data-ttu-id="55062-208">繫結是繫結項目的集合，表示與服務位址相關聯的通訊堆疊。</span><span class="sxs-lookup"><span data-stu-id="55062-208">A binding is a collection of binding elements that represents the communication stack associated with a service address.</span></span> <span data-ttu-id="55062-209">在堆疊中的每個項目由[\<繫結 >](../../../../docs/framework/misc/binding.md)項目。</span><span class="sxs-lookup"><span data-stu-id="55062-209">Each element in the stack is represented by a [\<binding>](../../../../docs/framework/misc/binding.md) element.</span></span>  
  
 <span data-ttu-id="55062-210">在此範例中，繫結項目為 `UdpTransportBindingElement`，其衍生自 <xref:System.ServiceModel.Channels.TransportBindingElement>。</span><span class="sxs-lookup"><span data-stu-id="55062-210">In the sample, the binding element is `UdpTransportBindingElement`, which derives from <xref:System.ServiceModel.Channels.TransportBindingElement>.</span></span> <span data-ttu-id="55062-211">它會覆寫下列方法來建置與繫結關聯的處理站。</span><span class="sxs-lookup"><span data-stu-id="55062-211">It overrides the following methods to build the factories associated with our binding.</span></span>  
  
```csharp
public IChannelFactory<TChannel> BuildChannelFactory<TChannel>(BindingContext context)  
{  
    return (IChannelFactory<TChannel>)(object)new UdpChannelFactory(this, context);  
}  
  
public IChannelListener<TChannel> BuildChannelListener<TChannel>(BindingContext context)  
{  
    return (IChannelListener<TChannel>)(object)new UdpChannelListener(this, context);  
}  
```  
  
 <span data-ttu-id="55062-212">它還包含可以用來複製 `BindingElement` 以及傳回我們的結構描述 (soap.udp) 的成員。</span><span class="sxs-lookup"><span data-stu-id="55062-212">It also contains members for cloning the `BindingElement` and returning our scheme (soap.udp).</span></span>  
  
## <a name="adding-metadata-support-for-a-transport-binding-element"></a><span data-ttu-id="55062-213">新增傳輸繫結項目的中繼資料支援</span><span class="sxs-lookup"><span data-stu-id="55062-213">Adding Metadata Support for a Transport Binding Element</span></span>  
 <span data-ttu-id="55062-214">若要將傳輸整合到中繼資料系統中，必須同時支援匯入與匯出原則。</span><span class="sxs-lookup"><span data-stu-id="55062-214">To integrate our transport into the metadata system, we must support both the import and export of policy.</span></span> <span data-ttu-id="55062-215">這可讓我們來產生用戶端透過繫結的[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。</span><span class="sxs-lookup"><span data-stu-id="55062-215">This allows us to generate clients of our binding through the [ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md).</span></span>  
  
### <a name="adding-wsdl-support"></a><span data-ttu-id="55062-216">新增 WSDL 支援</span><span class="sxs-lookup"><span data-stu-id="55062-216">Adding WSDL Support</span></span>  
 <span data-ttu-id="55062-217">繫結中的傳輸繫結項目是負責匯出與匯入中繼資料中的定址資訊。</span><span class="sxs-lookup"><span data-stu-id="55062-217">The transport binding element in a binding is responsible for exporting and importing addressing information in metadata.</span></span> <span data-ttu-id="55062-218">當使用 SOAP 繫結時，傳輸繫結項目也應該匯出中繼資料中的正確傳輸 URI。</span><span class="sxs-lookup"><span data-stu-id="55062-218">When using a SOAP binding, the transport binding element should also export a correct transport URI in metadata.</span></span>  
  
#### <a name="wsdl-export"></a><span data-ttu-id="55062-219">WSDL 匯出</span><span class="sxs-lookup"><span data-stu-id="55062-219">WSDL Export</span></span>  
 <span data-ttu-id="55062-220">若要匯出定址資訊，`UdpTransportBindingElement` 會實作 `IWsdlExportExtension` 介面。</span><span class="sxs-lookup"><span data-stu-id="55062-220">To export addressing information the `UdpTransportBindingElement` implements the `IWsdlExportExtension` interface.</span></span> <span data-ttu-id="55062-221">`ExportEndpoint` 方法會新增正確的定址資訊至 WSDL 連接埠。</span><span class="sxs-lookup"><span data-stu-id="55062-221">The `ExportEndpoint` method adds the correct addressing information to the WSDL port.</span></span>  
  
```csharp
if (context.WsdlPort != null)  
{  
    AddAddressToWsdlPort(context.WsdlPort, context.Endpoint.Address, encodingBindingElement.MessageVersion.Addressing);  
}  
```  
  
 <span data-ttu-id="55062-222">當端點使用 SOAP 繫結時，`UdpTransportBindingElement` 方法的 `ExportEndpoint` 實作也會匯出傳輸 URI。</span><span class="sxs-lookup"><span data-stu-id="55062-222">The `UdpTransportBindingElement` implementation of the `ExportEndpoint` method also exports a transport URI when the endpoint uses a SOAP binding.</span></span>  
  
```csharp
WsdlNS.SoapBinding soapBinding = GetSoapBinding(context, exporter);  
if (soapBinding != null)  
{  
    soapBinding.Transport = UdpPolicyStrings.UdpNamespace;  
}  
```  
  
#### <a name="wsdl-import"></a><span data-ttu-id="55062-223">WSDL 匯入</span><span class="sxs-lookup"><span data-stu-id="55062-223">WSDL Import</span></span>  
 <span data-ttu-id="55062-224">若要延伸 WSDL 匯入系統以處理位址匯入，就必須將下列組態新增至 Svcutil.exe 的組態檔中，如 Svcutil.exe.config 檔案所示。</span><span class="sxs-lookup"><span data-stu-id="55062-224">To extend the WSDL import system to handle importing the addresses, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <wsdlImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="55062-225">當執行 Svcutil.exe 時，有兩個選項可以讓 Svcutil.exe 載入 WSDL 匯入延伸：</span><span class="sxs-lookup"><span data-stu-id="55062-225">When running Svcutil.exe, there are two options for getting Svcutil.exe to load the WSDL import extensions:</span></span>  
  
1. <span data-ttu-id="55062-226">Svcutil.exe 指向組態檔使用 /SvcutilConfig:\<檔案 >。</span><span class="sxs-lookup"><span data-stu-id="55062-226">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="55062-227">將組態區段新增至與 Svcutil.exe 位於相同目錄的 Svcutil.exe.config 中。</span><span class="sxs-lookup"><span data-stu-id="55062-227">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
 <span data-ttu-id="55062-228">`UdpBindingElementImporter` 型別會實作 `IWsdlImportExtension` 介面。</span><span class="sxs-lookup"><span data-stu-id="55062-228">The `UdpBindingElementImporter` type implements the `IWsdlImportExtension` interface.</span></span> <span data-ttu-id="55062-229">`ImportEndpoint` 方法會從 WSDL 連接埠匯入位址。</span><span class="sxs-lookup"><span data-stu-id="55062-229">The `ImportEndpoint` method imports the address from the WSDL port.</span></span>  
  
```csharp
BindingElementCollection bindingElements = context.Endpoint.Binding.CreateBindingElements();  
TransportBindingElement transportBindingElement = bindingElements.Find<TransportBindingElement>();  
if (transportBindingElement is UdpTransportBindingElement)  
{  
    ImportAddress(context);  
}  
```  
  
### <a name="adding-policy-support"></a><span data-ttu-id="55062-230">新增原則支援</span><span class="sxs-lookup"><span data-stu-id="55062-230">Adding Policy Support</span></span>  
 <span data-ttu-id="55062-231">自訂繫結項目可以匯出服務端點之 WSDL 繫結的原則判斷提示，以表示該繫結項目的功能。</span><span class="sxs-lookup"><span data-stu-id="55062-231">The custom binding element can export policy assertions in the WSDL binding for a service endpoint to express the capabilities of that binding element.</span></span>  
  
#### <a name="policy-export"></a><span data-ttu-id="55062-232">原則匯出</span><span class="sxs-lookup"><span data-stu-id="55062-232">Policy Export</span></span>  
 <span data-ttu-id="55062-233">`UdpTransportBindingElement`型別會實作`IPolicyExportExtension`來增加對匯出原則支援。</span><span class="sxs-lookup"><span data-stu-id="55062-233">The `UdpTransportBindingElement` type implements `IPolicyExportExtension` to add support for exporting policy.</span></span> <span data-ttu-id="55062-234">因此，`System.ServiceModel.MetadataExporter` 會針對包含它的任何繫結，在產生原則時包含 `UdpTransportBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="55062-234">As a result, `System.ServiceModel.MetadataExporter` includes `UdpTransportBindingElement` in the generation of policy for any binding that includes it.</span></span>  
  
 <span data-ttu-id="55062-235">在 `IPolicyExportExtension.ExportPolicy` 中，我們會新增 UDP 的判斷提示以及其他判斷提示 (如果使用多點傳送模式)。</span><span class="sxs-lookup"><span data-stu-id="55062-235">In `IPolicyExportExtension.ExportPolicy`, we add an assertion for UDP and another assertion if we are in multicast mode.</span></span> <span data-ttu-id="55062-236">這是因為多點傳送模式會影響通訊堆疊的建構方式，所以必須同時對兩端進行協調。</span><span class="sxs-lookup"><span data-stu-id="55062-236">This is because multicast mode affects how the communication stack is constructed, and thus must be coordinated between both sides.</span></span>  
  
```csharp
ICollection<XmlElement> bindingAssertions = context.GetBindingAssertions();  
XmlDocument xmlDocument = new XmlDocument();  
bindingAssertions.Add(xmlDocument.CreateElement(  
UdpPolicyStrings.Prefix, UdpPolicyStrings.TransportAssertion, UdpPolicyStrings.UdpNamespace));  
if (Multicast)  
{  
    bindingAssertions.Add(xmlDocument.CreateElement(
        UdpPolicyStrings.Prefix, 
        UdpPolicyStrings.MulticastAssertion, 
        UdpPolicyStrings.UdpNamespace));  
}  
```  
  
 <span data-ttu-id="55062-237">因為自訂傳輸繫結項目會負責處理定址，所以 `IPolicyExportExtension` 上的 `UdpTransportBindingElement` 實作也必須處理適當之 WS-Addressing 原則判斷提示的匯出，以表示所使用的 WS-Addressing 版本。</span><span class="sxs-lookup"><span data-stu-id="55062-237">Because custom transport binding elements are responsible for handling addressing, the `IPolicyExportExtension` implementation on the `UdpTransportBindingElement` must also handle exporting the appropriate WS-Addressing policy assertions to indicate the version of WS-Addressing being used.</span></span>  
  
```csharp
AddWSAddressingAssertion(context, encodingBindingElement.MessageVersion.Addressing);  
```  
  
#### <a name="policy-import"></a><span data-ttu-id="55062-238">原則匯入</span><span class="sxs-lookup"><span data-stu-id="55062-238">Policy Import</span></span>  
 <span data-ttu-id="55062-239">若要延伸原則匯入系統，就必須將下列組態新增至 Svcutil.exe 的組態檔中，如 Svcutil.exe.config 檔案所示。</span><span class="sxs-lookup"><span data-stu-id="55062-239">To extend the Policy Import system, we must add the following configuration to the configuration file for Svcutil.exe as shown in the Svcutil.exe.config file.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <metadata>  
        <policyImporters>  
          <extension type=" Microsoft.ServiceModel.Samples.UdpBindingElementImporter, UdpTransport" />  
        </policyImporters>  
      </metadata>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="55062-240">然後從已註冊類別 (`IPolicyImporterExtension`) 實作 `UdpBindingElementImporter`。</span><span class="sxs-lookup"><span data-stu-id="55062-240">Then we implement `IPolicyImporterExtension` from our registered class (`UdpBindingElementImporter`).</span></span> <span data-ttu-id="55062-241">在 `ImportPolicy()` 中，查看命名空間中的判斷提示，然後處理用來產生傳輸的判斷提示，並且檢查其是否使用多點傳送。</span><span class="sxs-lookup"><span data-stu-id="55062-241">In `ImportPolicy()`, we look through the assertions in our namespace, and process the ones for generating the transport and check whether it is multicast.</span></span> <span data-ttu-id="55062-242">此外，從繫結判斷提示清單中移除匯入所處理的判斷提示。</span><span class="sxs-lookup"><span data-stu-id="55062-242">We also must remove the assertions we handle from the list of binding assertions.</span></span> <span data-ttu-id="55062-243">同樣地，當執行 Svcutil.exe 時有兩個整合的選項：</span><span class="sxs-lookup"><span data-stu-id="55062-243">Again, when running Svcutil.exe, there are two options for integration:</span></span>  
  
1. <span data-ttu-id="55062-244">Svcutil.exe 指向組態檔使用 /SvcutilConfig:\<檔案 >。</span><span class="sxs-lookup"><span data-stu-id="55062-244">Point Svcutil.exe to our configuration file using the /SvcutilConfig:\<file>.</span></span>  
  
2. <span data-ttu-id="55062-245">將組態區段新增至與 Svcutil.exe 位於相同目錄的 Svcutil.exe.config 中。</span><span class="sxs-lookup"><span data-stu-id="55062-245">Add the configuration section to Svcutil.exe.config in the same directory as Svcutil.exe.</span></span>  
  
<a name="AddingAStandardBinding"></a>   
## <a name="adding-a-standard-binding"></a><span data-ttu-id="55062-246">新增標準繫結</span><span class="sxs-lookup"><span data-stu-id="55062-246">Adding a Standard Binding</span></span>  
 <span data-ttu-id="55062-247">可以透過下列兩種方式使用繫結項目：</span><span class="sxs-lookup"><span data-stu-id="55062-247">Our binding element can be used in the following two ways:</span></span>  
  
- <span data-ttu-id="55062-248">透過自訂繫結：自訂繫結可讓使用者建立自己的繫結根據任意一組繫結項目。</span><span class="sxs-lookup"><span data-stu-id="55062-248">Through a custom binding: A custom binding allows the user to create their own binding based on an arbitrary set of binding elements.</span></span>  
  
- <span data-ttu-id="55062-249">使用系統提供的繫結，其中包含我們的繫結元素。</span><span class="sxs-lookup"><span data-stu-id="55062-249">By using a system-provided binding that includes our binding element.</span></span> <span data-ttu-id="55062-250">WCF 會提供一些這些系統定義的繫結，例如`BasicHttpBinding`， `NetTcpBinding`，和`WsHttpBinding`。</span><span class="sxs-lookup"><span data-stu-id="55062-250">WCF provides a number of these system-defined bindings, such as `BasicHttpBinding`, `NetTcpBinding`, and `WsHttpBinding`.</span></span> <span data-ttu-id="55062-251">每個這個繫結都會與妥善定義的設定檔相關聯。</span><span class="sxs-lookup"><span data-stu-id="55062-251">Each of these bindings is associated with a well-defined profile.</span></span>  
  
 <span data-ttu-id="55062-252">範例會在衍生自 `SampleProfileUdpBinding` 的 <xref:System.ServiceModel.Channels.Binding> 中實作設定檔繫結。</span><span class="sxs-lookup"><span data-stu-id="55062-252">The sample implements profile binding in `SampleProfileUdpBinding`, which derives from <xref:System.ServiceModel.Channels.Binding>.</span></span> <span data-ttu-id="55062-253">`SampleProfileUdpBinding` 中最多包含四個繫結項目：`UdpTransportBindingElement`、`TextMessageEncodingBindingElement CompositeDuplexBindingElement` 和 `ReliableSessionBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="55062-253">The `SampleProfileUdpBinding` contains up to four binding elements within it: `UdpTransportBindingElement`, `TextMessageEncodingBindingElement CompositeDuplexBindingElement`, and `ReliableSessionBindingElement`.</span></span>  
  
```csharp
public override BindingElementCollection CreateBindingElements()  
{     
    BindingElementCollection bindingElements = new BindingElementCollection();  
    if (ReliableSessionEnabled)  
    {  
        bindingElements.Add(session);  
        bindingElements.Add(compositeDuplex);  
    }  
    bindingElements.Add(encoding);  
    bindingElements.Add(transport);  
    return bindingElements.Clone();  
}  
```  
  
### <a name="adding-a-custom-standard-binding-importer"></a><span data-ttu-id="55062-254">新增自訂標準繫結匯入工具</span><span class="sxs-lookup"><span data-stu-id="55062-254">Adding a Custom Standard Binding Importer</span></span>  
 <span data-ttu-id="55062-255">根據預設，Svcutil.exe 和 `WsdlImporter` 型別會辨識並匯入系統定義的繫結。</span><span class="sxs-lookup"><span data-stu-id="55062-255">Svcutil.exe and the `WsdlImporter` type, by default, recognizes and imports system-defined bindings.</span></span> <span data-ttu-id="55062-256">否則，會將繫結程序當做 `CustomBinding` 執行個體匯入。</span><span class="sxs-lookup"><span data-stu-id="55062-256">Otherwise, the binding gets imported as a `CustomBinding` instance.</span></span> <span data-ttu-id="55062-257">為了讓 Svcutil.exe 和 `WsdlImporter` 能夠匯入 `SampleProfileUdpBinding`，`UdpBindingElementImporter` 也會當做自訂標準繫結匯入工具。</span><span class="sxs-lookup"><span data-stu-id="55062-257">To enable Svcutil.exe and the `WsdlImporter` to import the `SampleProfileUdpBinding` the `UdpBindingElementImporter` also acts as a custom standard binding importer.</span></span>  
  
 <span data-ttu-id="55062-258">自訂標準繫結匯入工具會實作 `ImportEndpoint` 介面上的 `IWsdlImportExtension` 方法，檢視從中繼資料匯入的 `CustomBinding` 執行個體，以檢查特定標準繫結是否已產生該執行個體。</span><span class="sxs-lookup"><span data-stu-id="55062-258">A custom standard binding importer implements the `ImportEndpoint` method on the `IWsdlImportExtension` interface to examine the `CustomBinding` instance imported from metadata to see whether it could have been generated by a specific standard binding.</span></span>  
  
```csharp
if (context.Endpoint.Binding is CustomBinding)  
{  
    Binding binding;  
    if (transportBindingElement is UdpTransportBindingElement)  
    {  
        //if TryCreate is true, the CustomBinding will be replace by a SampleProfileUdpBinding in the  
        //generated config file for better typed generation.  
        if (SampleProfileUdpBinding.TryCreate(bindingElements, out binding))  
        {  
            binding.Name = context.Endpoint.Binding.Name;  
            binding.Namespace = context.Endpoint.Binding.Namespace;  
            context.Endpoint.Binding = binding;  
        }  
    }  
}  
```  
  
 <span data-ttu-id="55062-259">一般來說，實作自訂標準繫結程序匯入工具包含檢查已匯入之繫結程序項目的屬性，以驗證只有變更由標準繫結程序設定的屬性，而所有其他屬性都還是預設值。</span><span class="sxs-lookup"><span data-stu-id="55062-259">Generally, implementing a custom standard binding importer involves checking the properties of the imported binding elements to verify that only properties that could have been set by the standard binding have changed and all other properties are their defaults.</span></span> <span data-ttu-id="55062-260">實作標準繫結匯入工具的基本策略，是建立標準繫結的執行個體、從繫結項目將屬性傳播至標準繫結支援的標準繫結執行個體，然後比較標準繫結與已匯入繫結項目上的繫結項目。</span><span class="sxs-lookup"><span data-stu-id="55062-260">A basic strategy for implementing a standard binding importer is to create an instance of the standard binding, propagate the properties from the binding elements to the standard binding instance that the standard binding supports, and the compare the binding elements from the standard binding with the imported binding elements.</span></span>  
  
<a name="AddingConfigurationSupport"></a>   
## <a name="adding-configuration-support"></a><span data-ttu-id="55062-261">新增組態支援</span><span class="sxs-lookup"><span data-stu-id="55062-261">Adding Configuration Support</span></span>  
 <span data-ttu-id="55062-262">若要透過組態公開傳輸，就必須實作兩個組態區段。</span><span class="sxs-lookup"><span data-stu-id="55062-262">To expose our transport through configuration, we must implement two configuration sections.</span></span> <span data-ttu-id="55062-263">第一個是 `BindingElementExtensionElement` 的 `UdpTransportBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="55062-263">The first is a `BindingElementExtensionElement` for `UdpTransportBindingElement`.</span></span> <span data-ttu-id="55062-264">使用這個區段，`CustomBinding` 的實作就可以參考繫結項目。</span><span class="sxs-lookup"><span data-stu-id="55062-264">This is so that `CustomBinding` implementations can reference our binding element.</span></span> <span data-ttu-id="55062-265">第二個是 `Configuration` 的 `SampleProfileUdpBinding`。</span><span class="sxs-lookup"><span data-stu-id="55062-265">The second is a `Configuration` for our `SampleProfileUdpBinding`.</span></span>  
  
### <a name="binding-element-extension-element"></a><span data-ttu-id="55062-266">繫結項目延伸項目</span><span class="sxs-lookup"><span data-stu-id="55062-266">Binding Element Extension Element</span></span>  
 <span data-ttu-id="55062-267">區段 `UdpTransportElement` 是 `BindingElementExtensionElement`，它會將 `UdpTransportBindingElement` 公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="55062-267">The section `UdpTransportElement` is a `BindingElementExtensionElement` that exposes `UdpTransportBindingElement` to the configuration system.</span></span> <span data-ttu-id="55062-268">藉由一些基本的覆寫，範例定義了組態區段名稱、繫結項目型別和建立繫結項目的方式。</span><span class="sxs-lookup"><span data-stu-id="55062-268">With a few basic overrides, we define our configuration section name, the type of our binding element and how to create our binding element.</span></span> <span data-ttu-id="55062-269">因此，可以接著在組態檔中登錄延伸區段，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="55062-269">We can then register our extension section in a configuration file as shown in the following code.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <extensions>  
      <bindingElementExtensions>  
        <add name="udpTransport" type="Microsoft.ServiceModel.Samples.UdpTransportElement, UdpTransport />  
      </bindingElementExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
 <span data-ttu-id="55062-270">您可以從自訂繫結參考該延伸，以使用 UDP 做為傳輸方式。</span><span class="sxs-lookup"><span data-stu-id="55062-270">The extension can be referenced from custom bindings to use UDP as the transport.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <bindings>  
      <customBinding>  
       <binding configurationName="UdpCustomBinding">  
         <udpTransport/>  
       </binding>  
      </customBinding>  
    </bindings>  
  </system.serviceModel>  
</configuration>  
```  
  
### <a name="binding-section"></a><span data-ttu-id="55062-271">繫結區段</span><span class="sxs-lookup"><span data-stu-id="55062-271">Binding Section</span></span>  
 <span data-ttu-id="55062-272">區段 `SampleProfileUdpBindingCollectionElement` 是 `StandardBindingCollectionElement`，它會將 `SampleProfileUdpBinding` 公開至組態系統。</span><span class="sxs-lookup"><span data-stu-id="55062-272">The section `SampleProfileUdpBindingCollectionElement` is a `StandardBindingCollectionElement` that exposes `SampleProfileUdpBinding` to the configuration system.</span></span> <span data-ttu-id="55062-273">大量實作會委派至衍生自 `SampleProfileUdpBindingConfigurationElement` 的 `StandardBindingElement`。</span><span class="sxs-lookup"><span data-stu-id="55062-273">The bulk of the implementation is delegated to the `SampleProfileUdpBindingConfigurationElement`, which derives from `StandardBindingElement`.</span></span> <span data-ttu-id="55062-274">`SampleProfileUdpBindingConfigurationElement`的屬性會對應至屬性上`SampleProfileUdpBinding`，並從對應的函式`ConfigurationElement`繫結。</span><span class="sxs-lookup"><span data-stu-id="55062-274">The `SampleProfileUdpBindingConfigurationElement` has properties that correspond to the properties on `SampleProfileUdpBinding`, and functions to map from the `ConfigurationElement` binding.</span></span> <span data-ttu-id="55062-275">最後，在 `OnApplyConfiguration` 中覆寫 `SampleProfileUdpBinding` 方法，如下列範例程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="55062-275">Finally, override the `OnApplyConfiguration` method in our `SampleProfileUdpBinding`, as shown in the following sample code.</span></span>  
  
```csharp
protected override void OnApplyConfiguration(string configurationName)  
{  
    if (binding == null)
        throw new ArgumentNullException("binding");

    if (binding.GetType() != typeof(SampleProfileUdpBinding))
    {
        throw new ArgumentException(string.Format(CultureInfo.CurrentCulture,
            "Invalid type for binding. Expected type: {0}. Type passed in: {1}.",
            typeof(SampleProfileUdpBinding).AssemblyQualifiedName,
            binding.GetType().AssemblyQualifiedName));
    }
    SampleProfileUdpBinding udpBinding = (SampleProfileUdpBinding)binding;

    udpBinding.OrderedSession = this.OrderedSession;
    udpBinding.ReliableSessionEnabled = this.ReliableSessionEnabled;
    udpBinding.SessionInactivityTimeout = this.SessionInactivityTimeout;
    if (this.ClientBaseAddress != null)
        udpBinding.ClientBaseAddress = ClientBaseAddress;
}
```  
  
 <span data-ttu-id="55062-276">為了使用組態系統註冊這個處理常式，範例將下列區段新增至相關的組態檔。</span><span class="sxs-lookup"><span data-stu-id="55062-276">To register this handler with the configuration system, we add the following section to the relevant configuration file.</span></span>  
  
```xml
<configuration>  
  <configSections>  
     <sectionGroup name="system.serviceModel">  
        <sectionGroup name="bindings">  
          <section name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport />  
        </sectionGroup>  
     </sectionGroup>  
  </configSections>  
</configuration>  
```  
  
 <span data-ttu-id="55062-277">因此，可以從 serviceModel 組態區段參考它。</span><span class="sxs-lookup"><span data-stu-id="55062-277">It can then be referenced from the serviceModel configuration section.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>  
    <client>  
      <endpoint configurationName="calculator"  
                address="soap.udp://localhost:8001/"   
                bindingConfiguration="CalculatorServer"  
                binding="sampleProfileUdpBinding"   
                contract= "Microsoft.ServiceModel.Samples.ICalculatorContract">  
      </endpoint>  
    </client>  
  </system.serviceModel>  
</configuration>  
```  
  
## <a name="the-udp-test-service-and-client"></a><span data-ttu-id="55062-278">UDP 測試服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="55062-278">The UDP Test Service and Client</span></span>  
 <span data-ttu-id="55062-279">您可以在 UdpTestService 和 UdpTestClient 目錄中，找到使用此範例傳輸的測試程式碼。</span><span class="sxs-lookup"><span data-stu-id="55062-279">Test code for using this sample transport is available in the UdpTestService and UdpTestClient directories.</span></span> <span data-ttu-id="55062-280">服務程式碼由兩項測試組成：其中一項測試會從程式碼設定繫結和端點，而另一項則是透過組態進行設定。</span><span class="sxs-lookup"><span data-stu-id="55062-280">The service code consists of two tests—one test sets up bindings and endpoints from code and the other does it through configuration.</span></span> <span data-ttu-id="55062-281">這兩項測試都會使用兩個端點。</span><span class="sxs-lookup"><span data-stu-id="55062-281">Both tests use two endpoints.</span></span> <span data-ttu-id="55062-282">一個端點會使用`SampleUdpProfileBinding`具有[ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))設定為`true`。</span><span class="sxs-lookup"><span data-stu-id="55062-282">One endpoint uses the `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `true`.</span></span> <span data-ttu-id="55062-283">另一個端點會使用包含 `UdpTransportBindingElement` 的自訂繫結程序。</span><span class="sxs-lookup"><span data-stu-id="55062-283">The other endpoint uses a custom binding with `UdpTransportBindingElement`.</span></span> <span data-ttu-id="55062-284">這相當於使用`SampleUdpProfileBinding`具有[ \<reliableSession >](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90))設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="55062-284">This is equivalent to using `SampleUdpProfileBinding` with [\<reliableSession>](https://docs.microsoft.com/previous-versions/ms731375(v=vs.90)) set to `false`.</span></span> <span data-ttu-id="55062-285">這兩項測試都會建立服務、為每個繫結新增端點、開啟服務，然後等候使用者按下 ENTER，再關閉服務。</span><span class="sxs-lookup"><span data-stu-id="55062-285">Both tests create a service, add an endpoint for each binding, open the service and then wait for the user to hit ENTER before closing the service.</span></span>  
  
 <span data-ttu-id="55062-286">當啟動服務的測試應用程式時，您應該會看見下列輸出。</span><span class="sxs-lookup"><span data-stu-id="55062-286">When you start the service test application you should see the following output.</span></span>  
  
```console
Testing Udp From Code.  
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
```  
  
 <span data-ttu-id="55062-287">此時，您就可以對已發行的端點執行測試用戶端應用程式。</span><span class="sxs-lookup"><span data-stu-id="55062-287">You can then run the test client application against the published endpoints.</span></span> <span data-ttu-id="55062-288">用戶端測試應用程式會為每個端點建立用戶端，並傳送五則訊息給每個端點。</span><span class="sxs-lookup"><span data-stu-id="55062-288">The client test application creates a client for each endpoint and sends five messages to each endpoint.</span></span> <span data-ttu-id="55062-289">下列是用戶端的輸出。</span><span class="sxs-lookup"><span data-stu-id="55062-289">The following output is on the client.</span></span>  
  
```console
Testing Udp From Imported Files Generated By SvcUtil.  
0  
3  
6  
9  
12  
Press <ENTER> to complete test.  
```  
  
 <span data-ttu-id="55062-290">下列是服務上的完整輸出。</span><span class="sxs-lookup"><span data-stu-id="55062-290">The following is the full output on the service.</span></span>  
  
```console
Service is started from code...  
Press <ENTER> to terminate the service and start service from config...  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
Hello, world!  
   adding 0 + 0  
   adding 1 + 2  
   adding 2 + 4  
   adding 3 + 6  
   adding 4 + 8  
```  
  
 <span data-ttu-id="55062-291">若要使用組態對已發行的端點執行用戶端應用程式，請在服務上按下 ENTER，然後再執行測試用戶端一次。</span><span class="sxs-lookup"><span data-stu-id="55062-291">To run the client application against endpoints published using configuration, hit ENTER on the service and then run the test client again.</span></span> <span data-ttu-id="55062-292">您應該會在服務上看見下列輸出。</span><span class="sxs-lookup"><span data-stu-id="55062-292">You should see the following output on the service.</span></span>  
  
```console
Testing Udp From Config.  
Service is started from config...  
Press <ENTER> to terminate the service and exit...  
```  
  
 <span data-ttu-id="55062-293">再次執行用戶端，會產生與前面相同的結果。</span><span class="sxs-lookup"><span data-stu-id="55062-293">Running the client again yields the same as the preceding results.</span></span>  
  
 <span data-ttu-id="55062-294">若要使用 Svcutil.exe 重新產生用戶端程式碼和組態，請啟動服務應用程式，然後從範例的根目錄執行下列 Svcutil.exe。</span><span class="sxs-lookup"><span data-stu-id="55062-294">To regenerate the client code and configuration using Svcutil.exe, start the service application and then run the following Svcutil.exe from the root directory of the sample.</span></span>  
  
```console
svcutil http://localhost:8000/udpsample/ /reference:UdpTransport\bin\UdpTransport.dll /svcutilConfig:svcutil.exe.config  
```  
  
 <span data-ttu-id="55062-295">請注意，Svcutil.exe 不會為 `SampleProfileUdpBinding` 產生繫結延伸組態，所以您必須以手動方式新增。</span><span class="sxs-lookup"><span data-stu-id="55062-295">Note that Svcutil.exe does not generate the binding extension configuration for the `SampleProfileUdpBinding`, so you must add it manually.</span></span>  
  
```xml
<configuration>  
  <system.serviceModel>      
    <extensions>  
      <!-- This was added manually because svcutil.exe does not add this extension to the file -->  
      <bindingExtensions>  
        <add name="sampleProfileUdpBinding" type="Microsoft.ServiceModel.Samples.SampleProfileUdpBindingCollectionElement, UdpTransport" />  
      </bindingExtensions>  
    </extensions>  
  </system.serviceModel>  
</configuration>  
```  
  
#### <a name="to-set-up-build-and-run-the-sample"></a><span data-ttu-id="55062-296">若要安裝、建置及執行範例</span><span class="sxs-lookup"><span data-stu-id="55062-296">To set up, build, and run the sample</span></span>  
  
1. <span data-ttu-id="55062-297">若要建置方案時，請依照中的指示[建置 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/building-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="55062-297">To build the solution, follow the instructions in [Building the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/building-the-samples.md).</span></span>  
  
2. <span data-ttu-id="55062-298">若要在單一或跨電腦組態中執行範例，請依照下列中的指示[執行 Windows Communication Foundation 範例](../../../../docs/framework/wcf/samples/running-the-samples.md)。</span><span class="sxs-lookup"><span data-stu-id="55062-298">To run the sample in a single- or cross-machine configuration, follow the instructions in [Running the Windows Communication Foundation Samples](../../../../docs/framework/wcf/samples/running-the-samples.md).</span></span>  
  
3. <span data-ttu-id="55062-299">請參閱前面的「UDP 測試服務和用戶端」一節。</span><span class="sxs-lookup"><span data-stu-id="55062-299">Refer to the preceding "The UDP Test Service and Client" section.</span></span>  
  
> [!IMPORTANT]
>  <span data-ttu-id="55062-300">這些範例可能已安裝在您的電腦上。</span><span class="sxs-lookup"><span data-stu-id="55062-300">The samples may already be installed on your machine.</span></span> <span data-ttu-id="55062-301">請先檢查下列 (預設) 目錄，然後再繼續。</span><span class="sxs-lookup"><span data-stu-id="55062-301">Check for the following (default) directory before continuing.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples`  
>   
>  <span data-ttu-id="55062-302">如果此目錄不存在，請移至[Windows Communication Foundation (WCF) 和.NET Framework 4 的 Windows Workflow Foundation (WF) 範例](https://go.microsoft.com/fwlink/?LinkId=150780)以下載所有 Windows Communication Foundation (WCF) 和[!INCLUDE[wf1](../../../../includes/wf1-md.md)]範例。</span><span class="sxs-lookup"><span data-stu-id="55062-302">If this directory does not exist, go to [Windows Communication Foundation (WCF) and Windows Workflow Foundation (WF) Samples for .NET Framework 4](https://go.microsoft.com/fwlink/?LinkId=150780) to download all Windows Communication Foundation (WCF) and [!INCLUDE[wf1](../../../../includes/wf1-md.md)] samples.</span></span> <span data-ttu-id="55062-303">此範例位於下列目錄。</span><span class="sxs-lookup"><span data-stu-id="55062-303">This sample is located in the following directory.</span></span>  
>   
>  `<InstallDrive>:\WF_WCF_Samples\WCF\Extensibility\Transport\Udp`
