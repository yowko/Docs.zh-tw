---
title: "服務通道層級的程式設計"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
ms.assetid: 8d8dcd85-0a05-4c44-8861-4a0b3b90cca9
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0a1a6ef03b3ee0cc68809ec6ba80a7eadbc44cb1
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="service-channel-level-programming"></a><span data-ttu-id="20d9f-102">服務通道層級的程式設計</span><span class="sxs-lookup"><span data-stu-id="20d9f-102">Service Channel-Level Programming</span></span>
<span data-ttu-id="20d9f-103">本主題說明如何撰寫 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 服務應用程式，而不使用 <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> 類別及其相關的物件模型。</span><span class="sxs-lookup"><span data-stu-id="20d9f-103">This topic describes how to write a [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] service application without using the <xref:System.ServiceModel.ServiceHost?displayProperty=nameWithType> and its associated object model.</span></span>  
  
## <a name="receiving-messages"></a><span data-ttu-id="20d9f-104">接收訊息</span><span class="sxs-lookup"><span data-stu-id="20d9f-104">Receiving Messages</span></span>  
 <span data-ttu-id="20d9f-105">以下為準備接收和處理訊息時所需的步驟：</span><span class="sxs-lookup"><span data-stu-id="20d9f-105">To be ready to receive and process messages, the following steps are required:</span></span>  
  
1.  <span data-ttu-id="20d9f-106">建立繫結。</span><span class="sxs-lookup"><span data-stu-id="20d9f-106">Create a binding.</span></span>  
  
2.  <span data-ttu-id="20d9f-107">建置通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="20d9f-107">Build a channel listener.</span></span>  
  
3.  <span data-ttu-id="20d9f-108">開啟通道接聽程式。</span><span class="sxs-lookup"><span data-stu-id="20d9f-108">Open the channel listener.</span></span>  
  
4.  <span data-ttu-id="20d9f-109">讀取要求並傳送回覆。</span><span class="sxs-lookup"><span data-stu-id="20d9f-109">Read the request and send a reply.</span></span>  
  
5.  <span data-ttu-id="20d9f-110">關閉所有通道物件。</span><span class="sxs-lookup"><span data-stu-id="20d9f-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="20d9f-111">建立繫結。</span><span class="sxs-lookup"><span data-stu-id="20d9f-111">Creating a Binding</span></span>  
 <span data-ttu-id="20d9f-112">接聽與接收訊息的第一步，就是建立繫結。</span><span class="sxs-lookup"><span data-stu-id="20d9f-112">The first step in listening for and receiving messages is creating a binding.</span></span> [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="20d9f-113"> 隨附幾個內建或系統提供的繫結，您可以具現化其中一個來直接使用。</span><span class="sxs-lookup"><span data-stu-id="20d9f-113"> ships with several built-in or system-provided bindings that can be used directly by instantiating one of them.</span></span> <span data-ttu-id="20d9f-114">此外，您也可以產生 CustomBinding 類別來建立自己的自訂繫結 (清單 1 中的程式碼也會執行相同作業)。</span><span class="sxs-lookup"><span data-stu-id="20d9f-114">In addition, you can also create your own custom binding by instantiating a CustomBinding class which is what the code in listing 1 does.</span></span>  
  
 <span data-ttu-id="20d9f-115">下列的程式碼範例會建立 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> 的執行個體，並將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> 新增至其項目集合 (用來建置通道堆疊的繫結項目集合)。</span><span class="sxs-lookup"><span data-stu-id="20d9f-115">The code example below creates an instance of <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection which is a collection of binding elements that are used to build the channel stack.</span></span> <span data-ttu-id="20d9f-116">在此範例中，由於項目集合只具有 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>，因此結果通道堆疊也只有 HTTP 傳輸通道。</span><span class="sxs-lookup"><span data-stu-id="20d9f-116">In this example, because the elements collection has only the <xref:System.ServiceModel.Channels.HttpTransportBindingElement>, the resulting channel stack has only the HTTP transport channel.</span></span>  
  
#### <a name="building-a-channellistener"></a><span data-ttu-id="20d9f-117">建置 ChannelListener</span><span class="sxs-lookup"><span data-stu-id="20d9f-117">Building a ChannelListener</span></span>  
 <span data-ttu-id="20d9f-118">建立繫結之後, 我們呼叫<!--zz<xref:System.ServiceModel.Channels.Binding.BuildChannelListener%601%2A?displayProperty=nameWithType>-->`System.ServiceModel.Channels.Binding.BuildChannelListener`來建置通道接聽程式，其中型別參數是要建立的通道。</span><span class="sxs-lookup"><span data-stu-id="20d9f-118">After creating a binding, we call <!--zz<xref:System.ServiceModel.Channels.Binding.BuildChannelListener%601%2A?displayProperty=nameWithType>--> `System.ServiceModel.Channels.Binding.BuildChannelListener` to build the channel listener where the type parameter is the channel shape to create.</span></span> <span data-ttu-id="20d9f-119">在此範例中，我們會使用 <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType>，因為我們想要以要求/回覆訊息交換模式來接聽傳入訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-119">In this example we are using <xref:System.ServiceModel.Channels.IReplyChannel?displayProperty=nameWithType> because we want to listen for incoming messages in a request/reply message exchange pattern.</span></span>  
  
 <span data-ttu-id="20d9f-120"><xref:System.ServiceModel.Channels.IReplyChannel> 會被用來接收要求訊息與傳回回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-120"><xref:System.ServiceModel.Channels.IReplyChannel> is used for receiving request messages and sending back reply messages.</span></span> <span data-ttu-id="20d9f-121">呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> 會傳回 <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>，以便用來接收要求訊息並傳回回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-121">Calling <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A?displayProperty=nameWithType> returns an <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>, which can be used to receive the request message and to send back a reply message.</span></span>  
  
 <span data-ttu-id="20d9f-122">在建立接聽程式時，我們會傳送接聽程式所接聽的網路位址，在此範例為 `http://localhost:8080/channelapp`。</span><span class="sxs-lookup"><span data-stu-id="20d9f-122">When creating the listener, we pass the network address on which it listens, in this case `http://localhost:8080/channelapp`.</span></span> <span data-ttu-id="20d9f-123">一般來說，每個傳輸通道都支援一到數個位址配置，例如，HTTP 傳輸同時支援 http 和 https 配置。</span><span class="sxs-lookup"><span data-stu-id="20d9f-123">In general, each transport channel supports one or possibly several address schemes, for example, the HTTP transport supports both http and https schemes.</span></span>  
  
 <span data-ttu-id="20d9f-124">在建立接聽程式時，我們同時會傳送空的 <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="20d9f-124">We also pass an empty <xref:System.ServiceModel.Channels.BindingParameterCollection?displayProperty=nameWithType> when creating the listener.</span></span> <span data-ttu-id="20d9f-125">繫結參數機制會負責將控制接聽程式建置方式的參數傳送出去。</span><span class="sxs-lookup"><span data-stu-id="20d9f-125">A binding parameter is a mechanism to pass parameters that control how the listener should be built.</span></span> <span data-ttu-id="20d9f-126">我們的範例並未使用此類參數，因此我們會傳送空的集合。</span><span class="sxs-lookup"><span data-stu-id="20d9f-126">In our example, we are not using any such parameters so we pass an empty collection.</span></span>  
  
#### <a name="listening-for-incoming-messages"></a><span data-ttu-id="20d9f-127">接聽傳入訊息</span><span class="sxs-lookup"><span data-stu-id="20d9f-127">Listening for Incoming Messages</span></span>  
 <span data-ttu-id="20d9f-128">接著，我們會在接聽程式上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> 並開始接受通道。</span><span class="sxs-lookup"><span data-stu-id="20d9f-128">We then call <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on the listener and start accepting channels.</span></span> <span data-ttu-id="20d9f-129"><xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> 的行為將視傳輸為連線導向還是沒有連線模式而定。</span><span class="sxs-lookup"><span data-stu-id="20d9f-129">The behavior of <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A?displayProperty=nameWithType> depends on whether the transport is connection-oriented or connection-less.</span></span> <span data-ttu-id="20d9f-130">如果是連線導向傳輸，<xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> 會在新的連線要求進入時才停止封鎖，這時它會傳回一個代表該項新連線的新通道。</span><span class="sxs-lookup"><span data-stu-id="20d9f-130">For connection-oriented transports, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> blocks until a new connection request comes in at which point it returns a new channel that represents that new connection.</span></span> <span data-ttu-id="20d9f-131">如果是沒有連線的傳輸，例如 HTTP，則 <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> 會立即傳回由傳輸接聽程式所建立，且是唯一的通道。</span><span class="sxs-lookup"><span data-stu-id="20d9f-131">For connection-less transports, such as HTTP, <xref:System.ServiceModel.Channels.IChannelListener%601.AcceptChannel%2A> returns immediately with the one and only channel that the transport listener creates.</span></span>  
  
 <span data-ttu-id="20d9f-132">在此範例中，接聽程式會傳回可實作 <xref:System.ServiceModel.Channels.IReplyChannel> 的通道。</span><span class="sxs-lookup"><span data-stu-id="20d9f-132">In this example, the listener returns a channel that implements <xref:System.ServiceModel.Channels.IReplyChannel>.</span></span> <span data-ttu-id="20d9f-133">為了在此通道上接收訊息，首先我們必須在其上呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType>，以將之轉換成準備通訊的狀態。</span><span class="sxs-lookup"><span data-stu-id="20d9f-133">To receive messages on this channel we first call <xref:System.ServiceModel.ICommunicationObject.Open%2A?displayProperty=nameWithType> on it to place it in a state ready for communication.</span></span> <span data-ttu-id="20d9f-134">接著我們會呼叫 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 並在訊息抵達之前進行封鎖。</span><span class="sxs-lookup"><span data-stu-id="20d9f-134">We then call <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> which blocks until a message arrives.</span></span>  
  
#### <a name="reading-the-request-and-sending-a-reply"></a><span data-ttu-id="20d9f-135">讀取要求並傳送回覆</span><span class="sxs-lookup"><span data-stu-id="20d9f-135">Reading the Request and Sending a Reply</span></span>  
 <span data-ttu-id="20d9f-136">當 <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> 傳回 <xref:System.ServiceModel.Channels.RequestContext>，我們會透過其 <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> 屬性來取回接收的訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-136">When <xref:System.ServiceModel.Channels.IReplyChannel.ReceiveRequest%2A> returns a <xref:System.ServiceModel.Channels.RequestContext>, we get the received message using its <xref:System.ServiceModel.Channels.RequestContext.RequestMessage%2A> property.</span></span> <span data-ttu-id="20d9f-137">我們會寫出訊息的行動與本文內容 (我們假定是字串)。</span><span class="sxs-lookup"><span data-stu-id="20d9f-137">We write out the message’s action and body content, (which we assume is a string).</span></span>  
  
 <span data-ttu-id="20d9f-138">在此情況下，為了傳送回覆，我們會建立新的回覆訊息並傳回要求中所收到的字串資料。</span><span class="sxs-lookup"><span data-stu-id="20d9f-138">To send a reply, we create a new reply message in this case passing back the string data we received in the request.</span></span> <span data-ttu-id="20d9f-139">接著，我們會呼叫 <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> 來傳送回覆訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-139">We then call <xref:System.ServiceModel.Channels.RequestContext.Reply%2A> to send the reply message.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="20d9f-140">關閉物件</span><span class="sxs-lookup"><span data-stu-id="20d9f-140">Closing Objects</span></span>  
 <span data-ttu-id="20d9f-141">為避免洩漏資源，請在不再需要時，關閉通訊期間所使用的物件，這點請您務必注意。</span><span class="sxs-lookup"><span data-stu-id="20d9f-141">To avoid leaking resources, it is very important to close objects used in communications when they are no longer required.</span></span> <span data-ttu-id="20d9f-142">在此範例中，我們會關閉要求訊息、要求內容、通道和接聽程式。</span><span class="sxs-lookup"><span data-stu-id="20d9f-142">In this example we close the request message, the request context, the channel and the listener.</span></span>  
  
 <span data-ttu-id="20d9f-143">下列程式碼範例示範基本服務，其中的通道接聽程式只會收到一個訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-143">The following code example shows a basic service in which a channel listener receives only one message.</span></span> <span data-ttu-id="20d9f-144">真實的服務會在服務結束之前持續接受通道並接收訊息。</span><span class="sxs-lookup"><span data-stu-id="20d9f-144">A real service keeps accepting channels and receiving messages until the service exits.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/serviceprogram.cs#1)]
 [!code-vb[ChannelProgrammingBasic#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/serviceprogram.vb#1)]
