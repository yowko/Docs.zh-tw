---
title: 可靠的工作階段概觀
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: a85a34c5e2ec7928c01586e4b01cdf5e90e896a7
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84601084"
---
# <a name="reliable-sessions-overview"></a><span data-ttu-id="aa9c4-102">可靠的工作階段概觀</span><span class="sxs-lookup"><span data-stu-id="aa9c4-102">Reliable Sessions Overview</span></span>

<span data-ttu-id="aa9c4-103">Windows Communication Foundation （WCF） SOAP 可靠訊息提供 SOAP 端點之間的端對端訊息傳輸可靠性。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-103">Windows Communication Foundation (WCF) SOAP reliable messaging provides end-to-end message transfer reliability between SOAP endpoints.</span></span> <span data-ttu-id="aa9c4-104">它會克服不可靠網路上的傳輸失敗與 SOAP 訊息層級失敗來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-104">It does this on networks that are unreliable by overcoming transport failures and SOAP message-level failures.</span></span> <span data-ttu-id="aa9c4-105">尤其，傳遞透過 SOAP 或傳輸媒介傳送的訊息時，它可讓您採用工作階段架構的方式單次並選擇是否依序進行。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-105">In particular, it provides session-based, single, and (optionally) ordered delivery for messages sent across SOAP or transport intermediaries.</span></span> <span data-ttu-id="aa9c4-106">以會話為基礎的傳遞可讓您以選擇性的訊息順序來分組會話中的訊息。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-106">Session-based delivery provides for grouping messages in a session with optional ordering of the messages.</span></span>

<span data-ttu-id="aa9c4-107">本主題描述可靠的會話、如何及何時使用它們，以及如何保護它們。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-107">This topic describes reliable sessions, how and when to use them, and how to secure them.</span></span>

## <a name="wcf-reliable-sessions"></a><span data-ttu-id="aa9c4-108">WCF 可靠會話</span><span class="sxs-lookup"><span data-stu-id="aa9c4-108">WCF reliable sessions</span></span>

<span data-ttu-id="aa9c4-109">WCF 可靠會話是由 WS-RELIABLEMESSAGING 通訊協定所定義的 SOAP 可靠訊息執行。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-109">WCF reliable sessions is an implementation of SOAP reliable messaging as defined by the WS-ReliableMessaging protocol.</span></span>

<span data-ttu-id="aa9c4-110">WCF SOAP 可靠訊息會在兩個端點之間提供端對端可靠會話，而不論分隔訊息端點的媒介數目或類型為何。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-110">WCF SOAP reliable messaging provides an end-to-end reliable session between two endpoints, regardless of the number or type of intermediaries that separate the messaging endpoints.</span></span> <span data-ttu-id="aa9c4-111">這包括不使用 SOAP （例如 HTTP proxy）的任何傳輸媒介，或使用 SOAP 的媒介（例如，以 SOAP 為基礎的路由器或橋接器），這是訊息在端點之間流動所需的。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-111">This includes any transport intermediaries that don't use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="aa9c4-112">可靠的會話通道支援*互動式*通訊，讓這類通道所連接的服務同時執行，並在低延遲的情況下（也就是在相對較短的時間間隔內）交換和處理訊息。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-112">A reliable session channel supports *interactive* communication so that the services connected by such a channel run concurrently and exchange and process messages under conditions of low latency, that is, within relatively short intervals of time.</span></span> <span data-ttu-id="aa9c4-113">這種結合表示這些元件會將進度一起或一起故障，因此不會在兩者之間提供隔離。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-113">This coupling means that these components make progress together or fail together, so there's no isolation provided between them.</span></span>

<span data-ttu-id="aa9c4-114">可靠工作階段會針對兩種失敗情況進行遮罩處理：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-114">A reliable session masks two kinds of failures:</span></span>

- <span data-ttu-id="aa9c4-115">SOAP 訊息層級的失敗，包括已遺失或重複的訊息，以及以不同於其傳送順序之順序抵達的訊息。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-115">SOAP message-level failures, which includes lost or duplicated messages and messages that arrive in a different order from the order in which they were sent.</span></span>

- <span data-ttu-id="aa9c4-116">傳輸失敗。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-116">Transport failures.</span></span>

<span data-ttu-id="aa9c4-117">可靠工作階段會實作 WS-ReliableMessaging 通訊協定並使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-117">A reliable session implements the WS-ReliableMessaging protocol and an in-memory transfer window to mask SOAP message-level failures and re-establishes connections in the case of transport failures.</span></span>

<span data-ttu-id="aa9c4-118">TCP 提供給 IP 封包的功能，可靠工作階段也會提供給 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-118">A reliable session provides for SOAP messages what TCP provides for IP packets.</span></span> <span data-ttu-id="aa9c4-119">TCP 通訊端連線可在節點之間提供單數、依序的 IP 封包傳輸。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-119">A TCP socket connection provides a singular, in-order transfer of IP packets between nodes.</span></span> <span data-ttu-id="aa9c4-120">可靠通道會提供同類型的可靠傳輸，但此傳輸在下列情況中會不同於 TCP 通訊端可靠性：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-120">The reliable channel provides the same type of reliable transfer, but it differs from TCP socket reliability in the following ways:</span></span>

- <span data-ttu-id="aa9c4-121">可靠性位於 SOAP 訊息層級，且不適用任意大小的位元組封包。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-121">The reliability is at the SOAP message level, not for an arbitrarily sized packet of bytes.</span></span>

- <span data-ttu-id="aa9c4-122">可靠性是以傳輸為中性，而不只是透過 TCP 傳輸。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-122">The reliability is transport-neutral, not just for transfer over TCP.</span></span>

- <span data-ttu-id="aa9c4-123">可靠性並不會系結至特定的傳輸會話（例如，TCP 連線提供的會話），而且可以在可靠會話的存留期內同時或連續使用多個傳輸會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-123">The reliability isn't tied to a particular transport session (for example, the session a TCP connection provides) and can use multiple transport sessions concurrently or sequentially over the lifetime of the reliable session.</span></span>

- <span data-ttu-id="aa9c4-124">可靠工作階段適用於寄件者與接收者 SOAP 端點之間，而不管在兩者之間建立連線所需的傳輸連線數量為何。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-124">The reliable session is between the sender and receiver SOAP endpoints, regardless of the number of transport connections required for connectivity between them.</span></span> <span data-ttu-id="aa9c4-125">簡單地說，TCP 可靠性會在傳輸連線結束的位置結束，而可靠會話會提供端對端的可靠性。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-125">In short, TCP reliability ends where the transport connection ends, while a reliable session provides end-to-end reliability.</span></span>

## <a name="reliable-sessions-and-bindings"></a><span data-ttu-id="aa9c4-126">可靠的會話和系結</span><span class="sxs-lookup"><span data-stu-id="aa9c4-126">Reliable sessions and bindings</span></span>

<span data-ttu-id="aa9c4-127">如先前所述，可靠會話是傳輸中性的。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-127">As mentioned earlier, a reliable session is transport neutral.</span></span> <span data-ttu-id="aa9c4-128">此外，您也可以透過許多訊息交換模式（例如要求-回復或雙工）來建立可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-128">Also, you can establish a reliable session over many message exchange patterns, such as request-reply or duplex.</span></span> <span data-ttu-id="aa9c4-129">WCF 可靠會話會公開為一組系結的屬性。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-129">A WCF reliable session is exposed as a property of a set of bindings.</span></span>

<span data-ttu-id="aa9c4-130">在使用的端點上使用可靠會話：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-130">Use a reliable session on endpoints that use:</span></span>

- <span data-ttu-id="aa9c4-131">HTTP 傳輸標準繫結：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-131">HTTP-based transport standard bindings:</span></span>

  - <span data-ttu-id="aa9c4-132">`WsHttpBinding` 並公開要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-132">`WsHttpBinding` and expose request-reply or one-way contracts.</span></span>

  - <span data-ttu-id="aa9c4-133">在要求-回復或簡單單向服務合約上使用可靠會話時。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-133">When using reliable session over a request-reply or simple one-way service contract.</span></span>

  - <span data-ttu-id="aa9c4-134">`WsDualHttpBinding` 並公開雙工、要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-134">`WsDualHttpBinding` and expose duplex, request-reply, or one-way contracts.</span></span>

  - <span data-ttu-id="aa9c4-135">`WsFederationHttpBinding` 並公開要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-135">`WsFederationHttpBinding` and expose request-reply or one-way contracts.</span></span>

- <span data-ttu-id="aa9c4-136">TCP 傳輸標準繫結：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-136">TCP-based transport standard bindings:</span></span>

  - <span data-ttu-id="aa9c4-137">`NetTcpBinding` 並公開雙工、要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-137">`NetTcpBinding` and expose duplex, request reply, or one-way contracts.</span></span>

<span data-ttu-id="aa9c4-138">藉由建立自訂系結（例如 HTTPS）（如需問題的詳細資訊，請參閱<a href="#reliable-sessions-and-security">可靠會話和安全性</a>）或具名管道系結，在任何其他系結上使用可靠會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-138">Use a reliable session on any other bindings by creating a custom binding, such as HTTPS (for more information about issues, see <a href="#reliable-sessions-and-security">Reliable sessions and security</a>) or a named pipe binding.</span></span>

<span data-ttu-id="aa9c4-139">您可以在不同的基礎通道類型上堆疊可靠會話，而產生的可靠會話通道圖形會有所不同。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-139">You can stack a reliable session on different underlying channel types, and the resulting reliable session channel shape varies.</span></span> <span data-ttu-id="aa9c4-140">在用戶端和伺服器上，支援的可靠會話通道類型取決於所使用的基礎通道類型。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-140">On both the client and the server, the type of reliable session channel supported depends on the type of underlying channel used.</span></span> <span data-ttu-id="aa9c4-141">下表列出用戶端上支援做為基礎通道型別功能的工作階段通道型別。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-141">The following table lists the types of session channels supported on the client as a function of the underlying channel type.</span></span>

| <span data-ttu-id="aa9c4-142">支援的可靠會話通道類型&#8224;</span><span class="sxs-lookup"><span data-stu-id="aa9c4-142">Supported reliable session channel types&#8224;</span></span> | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | <span data-ttu-id="aa9c4-143">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-143">Yes</span></span>               | <span data-ttu-id="aa9c4-144">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-144">Yes</span></span>                      | <span data-ttu-id="aa9c4-145">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-145">Yes</span></span>              | <span data-ttu-id="aa9c4-146">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-146">Yes</span></span>                     |
| `IRequestSessionChannel`                        | <span data-ttu-id="aa9c4-147">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-147">Yes</span></span>               | <span data-ttu-id="aa9c4-148">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-148">Yes</span></span>                      | <span data-ttu-id="aa9c4-149">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-149">No</span></span>               | <span data-ttu-id="aa9c4-150">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-150">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="aa9c4-151">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-151">No</span></span>                | <span data-ttu-id="aa9c4-152">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-152">No</span></span>                       | <span data-ttu-id="aa9c4-153">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-153">Yes</span></span>              | <span data-ttu-id="aa9c4-154">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-154">Yes</span></span>                     |

<span data-ttu-id="aa9c4-155">&#8224;支援的通道類型是 `TChannel` 傳遞至方法之泛型參數值的可用值 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> 。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-155">&#8224;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

<span data-ttu-id="aa9c4-156">下表列出伺服器上支援做為基礎通道型別功能的工作階段通道型別。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-156">The following table lists the types of session channels supported on the server as a function of the underlying channel type.</span></span>

| <span data-ttu-id="aa9c4-157">支援的可靠會話通道類型&#8225;</span><span class="sxs-lookup"><span data-stu-id="aa9c4-157">Supported reliable session channel types&#8225;</span></span> | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | <span data-ttu-id="aa9c4-158">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-158">Yes</span></span>             | <span data-ttu-id="aa9c4-159">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-159">Yes</span></span>                    | <span data-ttu-id="aa9c4-160">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-160">Yes</span></span>              | <span data-ttu-id="aa9c4-161">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-161">Yes</span></span>                     |
| `IReplySessionChannel`                          | <span data-ttu-id="aa9c4-162">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-162">Yes</span></span>             | <span data-ttu-id="aa9c4-163">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-163">Yes</span></span>                    | <span data-ttu-id="aa9c4-164">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-164">No</span></span>               | <span data-ttu-id="aa9c4-165">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-165">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="aa9c4-166">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-166">No</span></span>              | <span data-ttu-id="aa9c4-167">否</span><span class="sxs-lookup"><span data-stu-id="aa9c4-167">No</span></span>                     | <span data-ttu-id="aa9c4-168">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-168">Yes</span></span>              | <span data-ttu-id="aa9c4-169">是</span><span class="sxs-lookup"><span data-stu-id="aa9c4-169">Yes</span></span>                     |

<span data-ttu-id="aa9c4-170">&#8225;支援的通道類型是 `TChannel` 傳遞至方法之泛型參數值的可用值 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> 。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-170">&#8225;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

## <a name="reliable-sessions-and-security"></a><span data-ttu-id="aa9c4-171">可靠的會話和安全性</span><span class="sxs-lookup"><span data-stu-id="aa9c4-171">Reliable sessions and security</span></span>

<span data-ttu-id="aa9c4-172">保護可靠會話的安全，是為了確保通訊方（服務和用戶端）經過驗證，而且會話中交換的訊息不會遭到篡改。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-172">Securing a reliable session is important to ensure that the communicating parties (service and client) are authenticated and that the messages exchanged in the session aren't tampered with.</span></span> <span data-ttu-id="aa9c4-173">此外，請務必確保每個個別可靠會話的完整性。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-173">Furthermore, it's important to ensure the integrity of each individual reliable session.</span></span> <span data-ttu-id="aa9c4-174">可靠會話的保護方式是將它系結至安全性會話通道所表示和管理的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-174">A reliable session is secured by binding it to a security context that's represented and managed by a security session channel.</span></span> <span data-ttu-id="aa9c4-175">安全性通道會提供安全性工作階段。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-175">The security channel provides a security session.</span></span> <span data-ttu-id="aa9c4-176">在工作階段的建立期間所交換的安全性權杖會接著用來保護可靠工作階段中的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-176">Security tokens exchanged during the session establishment are then used to secure the messages in the reliable session.</span></span>

<span data-ttu-id="aa9c4-177">當可靠會話透過 TCP 時，TCP 會話會系結至可靠會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-177">When a reliable session is over TCP-S, the TCP session is tied to the reliable session.</span></span> <span data-ttu-id="aa9c4-178">因此，傳輸安全性可確保安全性也會系結到可靠的會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-178">Therefore, transport security ensures that security is also tied to the reliable session.</span></span> <span data-ttu-id="aa9c4-179">在此情況下，會關閉連線的重新建立作業。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-179">In this case, connection re-establishment is turned off.</span></span>

<span data-ttu-id="aa9c4-180">唯一的例外是在使用 HTTPS 時。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-180">The only exception is when using HTTPS.</span></span> <span data-ttu-id="aa9c4-181">安全通訊端層（SSL）會話未系結至可靠會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-181">The Secure Sockets Layer (SSL) session isn't bound to the reliable session.</span></span> <span data-ttu-id="aa9c4-182">這會造成威脅，因為共用安全性內容（SSL 會話）的會話不會彼此保護;這可能是根據應用程式而定，可能不是真正的威脅。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-182">This imposes a threat because sessions that are sharing a security context (the SSL session) aren't protected from each other; this might or might not be a real threat depending on the application.</span></span>

## <a name="using-reliable-sessions"></a><span data-ttu-id="aa9c4-183">使用可靠會話</span><span class="sxs-lookup"><span data-stu-id="aa9c4-183">Using reliable sessions</span></span>

<span data-ttu-id="aa9c4-184">若要使用 WCF 可靠會話，請使用支援可靠會話的系結來建立端點。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-184">To use WCF reliable sessions, create an endpoint with a binding that supports a reliable session.</span></span> <span data-ttu-id="aa9c4-185">使用 WCF 提供的其中一個系統提供系結，並啟用可靠會話，或建立您自己的自訂系結來執行這項工作。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-185">Use one of the system-provided bindings that WCF provides with the reliable session enabled or create your own custom binding that does this.</span></span>

<span data-ttu-id="aa9c4-186">根據預設，支援且啟用可靠工作階段的系統定義繫結包括：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-186">The system-defined bindings that support and enable a reliable session by default include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

<span data-ttu-id="aa9c4-187">系統提供的系結，支援可靠會話作為選項，但預設為不啟用，其中包括：</span><span class="sxs-lookup"><span data-stu-id="aa9c4-187">The system-provided bindings that support a reliable session as an option but don't enable one by default include:</span></span>

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

<span data-ttu-id="aa9c4-188">如需如何建立自訂系結的範例，請參閱[如何：使用 HTTPS 建立自訂可靠會話](how-to-create-a-custom-reliable-session-binding-with-https.md)系結。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-188">For an example of how to create a custom binding, see [How to: Create a Custom Reliable Session Binding with HTTPS](how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

<span data-ttu-id="aa9c4-189">如需支援可靠會話之 WCF 系結的討論，請參閱[系統提供](../system-provided-bindings.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-189">For a discussion of WCF bindings that support reliable sessions, see [System-Provided Bindings](../system-provided-bindings.md).</span></span>

## <a name="when-to-use-reliable-sessions"></a><span data-ttu-id="aa9c4-190">使用可靠會話的時機</span><span class="sxs-lookup"><span data-stu-id="aa9c4-190">When to use reliable sessions</span></span>

<span data-ttu-id="aa9c4-191">請務必瞭解在應用程式中使用可靠會話的時機。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-191">It's important to understand when to use reliable sessions in your application.</span></span> <span data-ttu-id="aa9c4-192">WCF 支援同時處於作用中狀態和作用中的端點之間的可靠會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-192">WCF supports reliable sessions between endpoints that are active and alive at the same time.</span></span> <span data-ttu-id="aa9c4-193">如果您的應用程式要求其中一個端點在一段時間內無法使用，則請使用佇列來達到可靠性。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-193">If your application requires one of the endpoints be unavailable for a duration of time, then use queues to achieve reliability.</span></span>

<span data-ttu-id="aa9c4-194">如果案例需要透過 TCP 連線的兩個端點，則 TCP 可能就足以提供可靠的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-194">If the scenario requires two endpoints connected over TCP, then TCP may be sufficient to provide reliable message exchanges.</span></span> <span data-ttu-id="aa9c4-195">雖然不一定要使用可靠會話，因為 TCP 會確保封包只會依序送達一次。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-195">Although, it isn't necessary to use a reliable session, since TCP ensures that the packets arrive in order and only once.</span></span>

<span data-ttu-id="aa9c4-196">如果您的案例具有下列任何特性，則您必須認真考慮使用可靠會話。</span><span class="sxs-lookup"><span data-stu-id="aa9c4-196">If your scenario has any of the following characteristics, then you must seriously consider using a reliable session.</span></span>

- <span data-ttu-id="aa9c4-197">SOAP 媒介，例如 SOAP 路由器</span><span class="sxs-lookup"><span data-stu-id="aa9c4-197">SOAP intermediaries, such as SOAP routers</span></span>

- <span data-ttu-id="aa9c4-198">Proxy 媒介或傳輸橋接器</span><span class="sxs-lookup"><span data-stu-id="aa9c4-198">Proxy intermediaries or transport bridges</span></span>

- <span data-ttu-id="aa9c4-199">間歇連線能力</span><span class="sxs-lookup"><span data-stu-id="aa9c4-199">Intermittent connectivity</span></span>

- <span data-ttu-id="aa9c4-200">透過 HTTP 的會話</span><span class="sxs-lookup"><span data-stu-id="aa9c4-200">Sessions over HTTP</span></span>

## <a name="see-also"></a><span data-ttu-id="aa9c4-201">請參閱</span><span class="sxs-lookup"><span data-stu-id="aa9c4-201">See also</span></span>

- [<span data-ttu-id="aa9c4-202">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="aa9c4-202">Using Bindings to Configure Services and Clients</span></span>](../using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="aa9c4-203">WS 可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="aa9c4-203">WS Reliable Session</span></span>](../samples/ws-reliable-session.md)
