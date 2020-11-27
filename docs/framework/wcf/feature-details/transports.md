---
title: Windows Communication Foundation 中的傳輸
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 8623b788b848867f25836a657b07349dd50c2780
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251681"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="b5b71-102">Windows Communication Foundation 中的傳輸</span><span class="sxs-lookup"><span data-stu-id="b5b71-102">Transports in Windows Communication Foundation</span></span>

<span data-ttu-id="b5b71-103">傳輸層 (Transport Layer) 屬於通道堆疊中的最底層。</span><span class="sxs-lookup"><span data-stu-id="b5b71-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="b5b71-104">Windows Communication Foundation (WCF) 中使用的主要傳輸為 HTTP、HTTPS、TCP 和具名管道。</span><span class="sxs-lookup"><span data-stu-id="b5b71-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="b5b71-105">本節中的主題將討論如何在這些傳輸之間進行選擇、設定傳輸，以及設定調整屬性。</span><span class="sxs-lookup"><span data-stu-id="b5b71-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="b5b71-106">WCF 包含額外的傳輸。</span><span class="sxs-lookup"><span data-stu-id="b5b71-106">WCF includes additional transports.</span></span> <span data-ttu-id="b5b71-107">如需訊息佇列 (也稱為 MSMQ) 傳輸的相關資訊，請參閱 [佇列和可靠會話](queues-and-reliable-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="b5b71-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="b5b71-108">如需對等傳輸的詳細資訊，請參閱 [對等網路](peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="b5b71-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="b5b71-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="b5b71-109">In This Section</span></span>  

 [<span data-ttu-id="b5b71-110">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="b5b71-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="b5b71-111">說明這三種主要傳輸，以及進行選擇時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="b5b71-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="b5b71-112">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="b5b71-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="b5b71-113">說明選擇訊息編碼繫結項目時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="b5b71-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="b5b71-114">資料流訊息傳輸</span><span class="sxs-lookup"><span data-stu-id="b5b71-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="b5b71-115">說明如何設定傳輸層來傳送資料流。</span><span class="sxs-lookup"><span data-stu-id="b5b71-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="b5b71-116">設定 HTTP 和 HTTPS</span><span class="sxs-lookup"><span data-stu-id="b5b71-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="b5b71-117">說明如何設定 HTTP 和 HTTPS 傳輸繫結項目。</span><span class="sxs-lookup"><span data-stu-id="b5b71-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="b5b71-118">作法：以受限的保留項目取代 WCF URL 保留項目</span><span class="sxs-lookup"><span data-stu-id="b5b71-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="b5b71-119">說明如何使用 WCFURL 限制的保留。</span><span class="sxs-lookup"><span data-stu-id="b5b71-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="b5b71-120">傳輸配額</span><span class="sxs-lookup"><span data-stu-id="b5b71-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="b5b71-121">說明在設定傳輸層之可用配額時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="b5b71-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="b5b71-122">使用 NAT 與防火牆</span><span class="sxs-lookup"><span data-stu-id="b5b71-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="b5b71-123">說明當訊息是在防火牆後方進行傳送或接收、或是當網路位址轉譯 (NAT) 存在時的傳輸層設定方式。</span><span class="sxs-lookup"><span data-stu-id="b5b71-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="b5b71-124">Net.TCP Port Sharing</span><span class="sxs-lookup"><span data-stu-id="b5b71-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="b5b71-125">描述如何使用 WCF 的 Net.tcp 埠共用元件。</span><span class="sxs-lookup"><span data-stu-id="b5b71-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="b5b71-126">參考</span><span class="sxs-lookup"><span data-stu-id="b5b71-126">Reference</span></span>  

 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="b5b71-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="b5b71-127">Related Sections</span></span>  

 [<span data-ttu-id="b5b71-128">繫結</span><span class="sxs-lookup"><span data-stu-id="b5b71-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="b5b71-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="b5b71-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
