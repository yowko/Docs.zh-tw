---
title: Windows Communication Foundation 中的傳輸
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 077d63d8038b245a68083611897c1e6c68971071
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84598667"
---
# <a name="transports-in-windows-communication-foundation"></a><span data-ttu-id="5ceb6-102">Windows Communication Foundation 中的傳輸</span><span class="sxs-lookup"><span data-stu-id="5ceb6-102">Transports in Windows Communication Foundation</span></span>
<span data-ttu-id="5ceb6-103">傳輸層 (Transport Layer) 屬於通道堆疊中的最底層。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-103">The transport layer is at the lowest level of the channel stack.</span></span> <span data-ttu-id="5ceb6-104">Windows Communication Foundation （WCF）中使用的主要傳輸為 HTTP、HTTPS、TCP 和具名管道。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-104">The main transports used in Windows Communication Foundation (WCF) are HTTP, HTTPS, TCP, and named pipes.</span></span> <span data-ttu-id="5ceb6-105">本節中的主題將討論如何在這些傳輸之間進行選擇、設定傳輸，以及設定調整屬性。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-105">The topics in this section discuss choosing among these transports, configuring the transport, and setting tuning properties.</span></span>  
  
 <span data-ttu-id="5ceb6-106">WCF 包含額外的傳輸。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-106">WCF includes additional transports.</span></span> <span data-ttu-id="5ceb6-107">如需訊息佇列（也稱為 MSMQ）傳輸的相關資訊，請參閱[佇列和可靠會話](queues-and-reliable-sessions.md)。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-107">For information about Message Queuing (also known as MSMQ) transport, see [Queues and Reliable Sessions](queues-and-reliable-sessions.md).</span></span> <span data-ttu-id="5ceb6-108">如需對等傳輸的詳細資訊，請參閱[對等網路](peer-to-peer-networking.md)。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-108">For information about peer-to-peer transport, see [Peer-to-Peer Networking](peer-to-peer-networking.md).</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="5ceb6-109">本節內容</span><span class="sxs-lookup"><span data-stu-id="5ceb6-109">In This Section</span></span>  
 [<span data-ttu-id="5ceb6-110">選擇傳輸</span><span class="sxs-lookup"><span data-stu-id="5ceb6-110">Choosing a Transport</span></span>](choosing-a-transport.md)  
 <span data-ttu-id="5ceb6-111">說明這三種主要傳輸，以及進行選擇時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-111">Describes the three main transports and considerations in selecting one.</span></span>  
  
 [<span data-ttu-id="5ceb6-112">選擇訊息編碼器</span><span class="sxs-lookup"><span data-stu-id="5ceb6-112">Choosing a Message Encoder</span></span>](choosing-a-message-encoder.md)  
 <span data-ttu-id="5ceb6-113">說明選擇訊息編碼繫結項目時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-113">Describes factors to consider when choosing a message-encoding binding element.</span></span>  
  
 [<span data-ttu-id="5ceb6-114">資料流訊息傳輸</span><span class="sxs-lookup"><span data-stu-id="5ceb6-114">Streaming Message Transfer</span></span>](streaming-message-transfer.md)  
 <span data-ttu-id="5ceb6-115">說明如何設定傳輸層來傳送資料流。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-115">Describes how to configure the transport layer to do streaming.</span></span>  
  
 [<span data-ttu-id="5ceb6-116">設定 HTTP 和 HTTPS</span><span class="sxs-lookup"><span data-stu-id="5ceb6-116">Configuring HTTP and HTTPS</span></span>](configuring-http-and-https.md)  
 <span data-ttu-id="5ceb6-117">說明如何設定 HTTP 和 HTTPS 傳輸繫結項目。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-117">Describes how to configure the HTTP and HTTPS transport binding elements.</span></span>  
  
 [<span data-ttu-id="5ceb6-118">HOW TO：若要以受限的保留項目取代 WCF URL URL 保留項目</span><span class="sxs-lookup"><span data-stu-id="5ceb6-118">How to: Replace the WCF URL Reservation with a Restricted Reservation</span></span>](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 <span data-ttu-id="5ceb6-119">說明如何使用 WCFURL 限制的保留。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-119">Describes how to use WCFURL restricted reservations.</span></span>  
  
 [<span data-ttu-id="5ceb6-120">傳輸配額</span><span class="sxs-lookup"><span data-stu-id="5ceb6-120">Transport Quotas</span></span>](transport-quotas.md)  
 <span data-ttu-id="5ceb6-121">說明在設定傳輸層之可用配額時的考量因素。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-121">Describes considerations in setting the quotas available in the transport layer.</span></span>  
  
 [<span data-ttu-id="5ceb6-122">使用 NAT 與防火牆</span><span class="sxs-lookup"><span data-stu-id="5ceb6-122">Working with NATs and Firewalls</span></span>](working-with-nats-and-firewalls.md)  
 <span data-ttu-id="5ceb6-123">說明當訊息是在防火牆後方進行傳送或接收、或是當網路位址轉譯 (NAT) 存在時的傳輸層設定方式。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-123">Describes how to configure the transport layer when messages are sent or received behind a firewall or when network address translation (NAT) is present.</span></span>  
  
 [<span data-ttu-id="5ceb6-124">Net.TCP 連接埠共用</span><span class="sxs-lookup"><span data-stu-id="5ceb6-124">Net.TCP Port Sharing</span></span>](net-tcp-port-sharing.md)  
 <span data-ttu-id="5ceb6-125">描述如何使用 WCF 的 Net.tcp 埠共用元件。</span><span class="sxs-lookup"><span data-stu-id="5ceb6-125">Describes how to use the Net.TCP Port Sharing component of WCF.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="5ceb6-126">參考</span><span class="sxs-lookup"><span data-stu-id="5ceb6-126">Reference</span></span>  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a><span data-ttu-id="5ceb6-127">相關章節</span><span class="sxs-lookup"><span data-stu-id="5ceb6-127">Related Sections</span></span>  
 [<span data-ttu-id="5ceb6-128">繫結</span><span class="sxs-lookup"><span data-stu-id="5ceb6-128">Bindings</span></span>](bindings.md)  
  
 [<span data-ttu-id="5ceb6-129">擴充繫結</span><span class="sxs-lookup"><span data-stu-id="5ceb6-129">Extending Bindings</span></span>](../extending/extending-bindings.md)
