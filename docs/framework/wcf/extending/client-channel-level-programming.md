---
title: 用戶端通道層級的程式設計
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 3b787719-4e77-4e77-96a6-5b15a11b995a
ms.openlocfilehash: ff399a2f3a4b86404695502fb002ee6920bea758
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33486501"
---
# <a name="client-channel-level-programming"></a><span data-ttu-id="435ac-102">用戶端通道層級的程式設計</span><span class="sxs-lookup"><span data-stu-id="435ac-102">Client Channel-Level Programming</span></span>
<span data-ttu-id="435ac-103">本主題說明如何撰寫 Windows Communication Foundation (WCF) 用戶端應用程式，而不使用<xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType>類別和其相關聯的物件模型。</span><span class="sxs-lookup"><span data-stu-id="435ac-103">This topic describes how to write a Windows Communication Foundation (WCF) client application without using the <xref:System.ServiceModel.ClientBase%601?displayProperty=nameWithType> class and its associated object model.</span></span>  
  
## <a name="sending-messages"></a><span data-ttu-id="435ac-104">傳送訊息</span><span class="sxs-lookup"><span data-stu-id="435ac-104">Sending Messages</span></span>  
 <span data-ttu-id="435ac-105">以下為準備傳送訊息及接收和處理回覆所需的步驟：</span><span class="sxs-lookup"><span data-stu-id="435ac-105">To be ready to send messages and receive and process replies, the following steps are required:</span></span>  
  
1.  <span data-ttu-id="435ac-106">建立繫結。</span><span class="sxs-lookup"><span data-stu-id="435ac-106">Create a binding.</span></span>  
  
2.  <span data-ttu-id="435ac-107">建置通道處理站。</span><span class="sxs-lookup"><span data-stu-id="435ac-107">Build a channel factory.</span></span>  
  
3.  <span data-ttu-id="435ac-108">建立通道。</span><span class="sxs-lookup"><span data-stu-id="435ac-108">Create a channel.</span></span>  
  
4.  <span data-ttu-id="435ac-109">傳送要求和讀取回覆。</span><span class="sxs-lookup"><span data-stu-id="435ac-109">Send a request and read the reply.</span></span>  
  
5.  <span data-ttu-id="435ac-110">關閉所有通道物件。</span><span class="sxs-lookup"><span data-stu-id="435ac-110">Close all channel objects.</span></span>  
  
#### <a name="creating-a-binding"></a><span data-ttu-id="435ac-111">建立繫結。</span><span class="sxs-lookup"><span data-stu-id="435ac-111">Creating a Binding</span></span>  
 <span data-ttu-id="435ac-112">類似於接收的情況 (請參閱[服務通道層級程式設計](../../../../docs/framework/wcf/extending/service-channel-level-programming.md))，以建立繫結傳送的訊息啟動。</span><span class="sxs-lookup"><span data-stu-id="435ac-112">Similar to the receiving case (see [Service Channel-Level Programming](../../../../docs/framework/wcf/extending/service-channel-level-programming.md)), sending messages starts by creating a binding.</span></span> <span data-ttu-id="435ac-113">這個範例會建立新的 <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType>，並將 <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> 加入至其 Elements 集合。</span><span class="sxs-lookup"><span data-stu-id="435ac-113">This example creates a new <xref:System.ServiceModel.Channels.CustomBinding?displayProperty=nameWithType> and adds an <xref:System.ServiceModel.Channels.HttpTransportBindingElement?displayProperty=nameWithType> to its Elements collection.</span></span>  
  
#### <a name="building-a-channelfactory"></a><span data-ttu-id="435ac-114">建置 ChannelFactory</span><span class="sxs-lookup"><span data-stu-id="435ac-114">Building a ChannelFactory</span></span>  
 <span data-ttu-id="435ac-115">這次我們不會建立 <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>，而是藉由在型別參數為 <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> 的繫結上呼叫 <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> 的方式建立 <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>。</span><span class="sxs-lookup"><span data-stu-id="435ac-115">Instead of creating a <xref:System.ServiceModel.Channels.IChannelListener?displayProperty=nameWithType>, this time we create a <xref:System.ServiceModel.ChannelFactory%601?displayProperty=nameWithType> by calling <xref:System.ServiceModel.ChannelFactory.CreateFactory%2A?displayProperty=nameWithType> on the binding where the type parameter is <xref:System.ServiceModel.Channels.IRequestChannel?displayProperty=nameWithType>.</span></span> <span data-ttu-id="435ac-116">通道接聽項是由等候傳入訊息的一端使用，而通道處理站是由初始化通訊以建立通道的一端使用。</span><span class="sxs-lookup"><span data-stu-id="435ac-116">While channel listeners are used by the side that waits for incoming messages, channel factories are used by the side that initiates the communication to create a channel.</span></span> <span data-ttu-id="435ac-117">就如同通道接聽項，通道處理站也必須先開啟才能使用。</span><span class="sxs-lookup"><span data-stu-id="435ac-117">Just like channel listeners, channel factories must be opened first before they can be used.</span></span>  
  
#### <a name="creating-a-channel"></a><span data-ttu-id="435ac-118">建立通道</span><span class="sxs-lookup"><span data-stu-id="435ac-118">Creating a Channel</span></span>  
 <span data-ttu-id="435ac-119">然後我們會呼叫 <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> 建立 <xref:System.ServiceModel.Channels.IRequestChannel>。</span><span class="sxs-lookup"><span data-stu-id="435ac-119">We then call <xref:System.ServiceModel.ChannelFactory%601.CreateChannel%2A?displayProperty=nameWithType> to create an <xref:System.ServiceModel.Channels.IRequestChannel>.</span></span> <span data-ttu-id="435ac-120">這個呼叫會使用建立的新通道，採用我們想要進行通訊的端點位址。</span><span class="sxs-lookup"><span data-stu-id="435ac-120">This call takes the address of the endpoint with which we want to communicate using the new channel being created.</span></span> <span data-ttu-id="435ac-121">一旦有了通道，我們就會在通道上呼叫 Open，讓通道進入準備好進行通訊的狀態。</span><span class="sxs-lookup"><span data-stu-id="435ac-121">Once we have a channel, we call Open on it to put it in a state ready for communication.</span></span> <span data-ttu-id="435ac-122">根據傳輸的本質，呼叫 Open 可能會初始化與目標端點的連線，或是不在網路上執行任何動作。</span><span class="sxs-lookup"><span data-stu-id="435ac-122">Depending on the nature of the transport, this call to Open may initiate a connection with the target endpoint or may do nothing at all on the network.</span></span>  
  
#### <a name="sending-a-request-and-reading-the-reply"></a><span data-ttu-id="435ac-123">傳送要求和讀取回覆</span><span class="sxs-lookup"><span data-stu-id="435ac-123">Sending a Request and Reading the Reply</span></span>  
 <span data-ttu-id="435ac-124">一旦開啟了通道，我們就能建立訊息並使用通道的 Request 方法傳送要求，然後等待回覆。</span><span class="sxs-lookup"><span data-stu-id="435ac-124">Once we have an opened channel, we can create a message and use the channel’s Request method to send the request and wait for the reply to come back.</span></span> <span data-ttu-id="435ac-125">當這個方法傳回時，我們會收到可以讀取的回覆訊息，並找出端點的回覆為何。</span><span class="sxs-lookup"><span data-stu-id="435ac-125">When this method returns, we have a reply message that we can read to find out what the endpoint’s reply was.</span></span>  
  
#### <a name="closing-objects"></a><span data-ttu-id="435ac-126">關閉物件</span><span class="sxs-lookup"><span data-stu-id="435ac-126">Closing Objects</span></span>  
 <span data-ttu-id="435ac-127">為避免洩漏資源，我們會在不再需要時，關閉通訊中所使用的物件。</span><span class="sxs-lookup"><span data-stu-id="435ac-127">To avoid leaking resources, we close objects used in communications when they are no longer required.</span></span>  
  
 <span data-ttu-id="435ac-128">以下程式碼範例會示範使用通道處理站傳送訊息和讀取回覆的基本用戶端。</span><span class="sxs-lookup"><span data-stu-id="435ac-128">The following code example shows a basic client using the channel factory to send a message and read the reply.</span></span>  
  
 [!code-csharp[ChannelProgrammingBasic#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/channelprogrammingbasic/cs/clientprogram.cs#2)]
 [!code-vb[ChannelProgrammingBasic#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/channelprogrammingbasic/vb/clientprogram.vb#2)]
