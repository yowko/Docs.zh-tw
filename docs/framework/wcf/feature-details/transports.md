---
title: "Windows Communication Foundation 中的傳輸"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
caps.latest.revision: "18"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 115e2a69c7d990c7d4c59634644fb557e83ad405
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="ca508-102">Windows Communication Foundation 中的傳輸</span><span class="sxs-lookup"><span data-stu-id="ca508-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="ca508-103">傳輸層 (Transport Layer) 屬於通道堆疊中的最底層。</span><span class="sxs-lookup"><span data-stu-id="ca508-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="ca508-104">[!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中所使用的主要傳輸有 HTTP、HTTPS、TCP 和具名管道。</span><span class="sxs-lookup"><span data-stu-id="ca508-104">The main transports used in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="ca508-105">本節中的主題將討論如何在這些傳輸之間進行選擇、設定傳輸，以及設定調整屬性。</span><span class="sxs-lookup"><span data-stu-id="ca508-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]<span data-ttu-id="ca508-106"> 包含額外的傳輸。</span><span class="sxs-lookup"><span data-stu-id="ca508-106"> includes additional transports.</span></span> <span data-ttu-id="ca508-107">如需訊息佇列 (也稱為 MSMQ) 傳輸的資訊，請參閱[佇列和可靠工作階段](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="ca508-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="ca508-108">如需端對端傳輸的資訊，請參閱[對等網路](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="ca508-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ca508-109">本章節內容</span><span class="sxs-lookup"><span data-stu-id="ca508-109">In This Section</span></span>  
 [<span data-ttu-id="ca508-110">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="ca508-110">Choosing a Transport</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 <span data-ttu-id="ca508-111">說明這三種主要傳輸，以及進行選擇時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="ca508-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="ca508-112">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="ca508-112">Choosing a Message Encoder</span></span>](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 <span data-ttu-id="ca508-113">說明選擇訊息編碼繫結項目時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="ca508-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="ca508-114">資料流訊息傳輸</span><span class="sxs-lookup"><span data-stu-id="ca508-114">Streaming Message Transfer</span></span>](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 <span data-ttu-id="ca508-115">說明如何設定傳輸層來傳送資料流。</span><span class="sxs-lookup"><span data-stu-id="ca508-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="ca508-116">設定 HTTP 和 HTTPS</span><span class="sxs-lookup"><span data-stu-id="ca508-116">Configuring HTTP and HTTPS</span></span>](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 <span data-ttu-id="ca508-117">說明如何設定 HTTP 和 HTTPS 傳輸繫結項目。</span><span class="sxs-lookup"><span data-stu-id="ca508-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="ca508-118">如何： 以受限制的保留項目取代 WCF URL 保留項目</span><span class="sxs-lookup"><span data-stu-id="ca508-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="ca508-119">說明如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL 限制的保留區。</span><span class="sxs-lookup"><span data-stu-id="ca508-119">Describes how to use [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)]URL restricted reservations.</span></span>  
  
 [<span data-ttu-id="ca508-120">傳輸配額</span><span class="sxs-lookup"><span data-stu-id="ca508-120">Transport Quotas</span></span>](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 <span data-ttu-id="ca508-121">說明在設定傳輸層之可用配額時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="ca508-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="ca508-122">使用 Nat 與防火牆</span><span class="sxs-lookup"><span data-stu-id="ca508-122">Working with NATs and Firewalls</span></span>](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 <span data-ttu-id="ca508-123">說明當訊息是在防火牆後方進行傳送或接收、或是當網路位址轉譯 (NAT) 存在時的傳輸層設定方式。</span><span class="sxs-lookup"><span data-stu-id="ca508-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="ca508-124">Net.TCP 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="ca508-124">Net.TCP Port Sharing</span></span>](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 <span data-ttu-id="ca508-125">說明如何使用 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的 Net.TCP 連接埠共用服務元件。</span><span class="sxs-lookup"><span data-stu-id="ca508-125">Describes how to use the Net.TCP Port Sharing component of [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)].</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ca508-126">參考資料</span><span class="sxs-lookup"><span data-stu-id="ca508-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="ca508-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="ca508-127">Related Sections</span></span>  
 [<span data-ttu-id="ca508-128">繫結</span><span class="sxs-lookup"><span data-stu-id="ca508-128">Bindings</span></span>](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [<span data-ttu-id="ca508-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="ca508-129">Extending Bindings</span></span>](../../../../docs/framework/wcf/extending/extending-bindings.md)
