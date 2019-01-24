---
title: 可靠的工作階段概觀
ms.date: 03/30/2017
ms.assetid: a7fc4146-ee2c-444c-82d4-ef6faffccc2d
ms.openlocfilehash: 6dd90ef800daf236d77c419d48c0857ac2d78aa2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54548020"
---
# <a name="reliable-sessions-overview"></a><span data-ttu-id="036d0-102">可靠的工作階段概觀</span><span class="sxs-lookup"><span data-stu-id="036d0-102">Reliable Sessions Overview</span></span>

<span data-ttu-id="036d0-103">Windows Communication Foundation (WCF) SOAP 可信賴傳訊提供 SOAP 端點之間的端對端訊息傳輸可靠性。</span><span class="sxs-lookup"><span data-stu-id="036d0-103">Windows Communication Foundation (WCF) SOAP reliable messaging provides end-to-end message transfer reliability between SOAP endpoints.</span></span> <span data-ttu-id="036d0-104">它會克服不可靠網路上的傳輸失敗與 SOAP 訊息層級失敗來達到這個目的。</span><span class="sxs-lookup"><span data-stu-id="036d0-104">It does this on networks that are unreliable by overcoming transport failures and SOAP message-level failures.</span></span> <span data-ttu-id="036d0-105">尤其，傳遞透過 SOAP 或傳輸媒介傳送的訊息時，它可讓您採用工作階段架構的方式單次並選擇是否依序進行。</span><span class="sxs-lookup"><span data-stu-id="036d0-105">In particular, it provides session-based, single, and (optionally) ordered delivery for messages sent across SOAP or transport intermediaries.</span></span> <span data-ttu-id="036d0-106">工作階段為基礎的傳遞提供群組和選擇性訊息順序方面的工作階段中的訊息。</span><span class="sxs-lookup"><span data-stu-id="036d0-106">Session-based delivery provides for grouping messages in a session with optional ordering of the messages.</span></span>

<span data-ttu-id="036d0-107">本主題描述如何可靠工作階段，和使用時機，以及如何保護其安全。</span><span class="sxs-lookup"><span data-stu-id="036d0-107">This topic describes reliable sessions, how and when to use them, and how to secure them.</span></span>

## <a name="wcf-reliable-sessions"></a><span data-ttu-id="036d0-108">WCF 可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="036d0-108">WCF reliable sessions</span></span>

<span data-ttu-id="036d0-109">WCF 可靠工作階段是實作 SOAP 可信賴傳訊 WS-ReliableMessaging 通訊協定所定義。</span><span class="sxs-lookup"><span data-stu-id="036d0-109">WCF reliable sessions is an implementation of SOAP reliable messaging as defined by the WS-ReliableMessaging protocol.</span></span>

<span data-ttu-id="036d0-110">WCF SOAP 可信賴傳訊提供兩個端點，不論分隔傳訊端點的媒介的類型或數目之間的端對端可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-110">WCF SOAP reliable messaging provides an end-to-end reliable session between two endpoints, regardless of the number or type of intermediaries that separate the messaging endpoints.</span></span> <span data-ttu-id="036d0-111">這包括任何傳輸媒介不使用 SOAP (例如，HTTP proxy) 或使用 SOAP （例如，SOAP 為基礎的路由器或橋接器） 所需的訊息，以在端點之間流動的媒介。</span><span class="sxs-lookup"><span data-stu-id="036d0-111">This includes any transport intermediaries that don't use SOAP (for example, HTTP proxies) or intermediaries that use SOAP (for example, SOAP-based routers or bridges) that are required for messages to flow between the endpoints.</span></span> <span data-ttu-id="036d0-112">支援可靠工作階段通道*互動式*通訊以便同時執行這類通道連接的服務，並在低延遲性的也就是的情況下交換與處理訊息在相對較短時間間隔。</span><span class="sxs-lookup"><span data-stu-id="036d0-112">A reliable session channel supports *interactive* communication so that the services connected by such a channel run concurrently and exchange and process messages under conditions of low latency, that is, within relatively short intervals of time.</span></span> <span data-ttu-id="036d0-113">此結合表示同時進行這些元件，或失敗，，因此提供兩者之間沒有隔離。</span><span class="sxs-lookup"><span data-stu-id="036d0-113">This coupling means that these components make progress together or fail together, so there's no isolation provided between them.</span></span>

<span data-ttu-id="036d0-114">可靠工作階段會針對兩種失敗情況進行遮罩處理：</span><span class="sxs-lookup"><span data-stu-id="036d0-114">A reliable session masks two kinds of failures:</span></span>

- <span data-ttu-id="036d0-115">SOAP 訊息層級的失敗，包括已遺失或重複的訊息，以及以不同於其傳送順序之順序抵達的訊息。</span><span class="sxs-lookup"><span data-stu-id="036d0-115">SOAP message-level failures, which includes lost or duplicated messages and messages that arrive in a different order from the order in which they were sent.</span></span>

- <span data-ttu-id="036d0-116">傳輸失敗。</span><span class="sxs-lookup"><span data-stu-id="036d0-116">Transport failures.</span></span>

<span data-ttu-id="036d0-117">可靠工作階段會實作 WS-ReliableMessaging 通訊協定並使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。</span><span class="sxs-lookup"><span data-stu-id="036d0-117">A reliable session implements the WS-ReliableMessaging protocol and an in-memory transfer window to mask SOAP message-level failures and re-establishes connections in the case of transport failures.</span></span>

<span data-ttu-id="036d0-118">TCP 提供給 IP 封包的功能，可靠工作階段也會提供給 SOAP 訊息。</span><span class="sxs-lookup"><span data-stu-id="036d0-118">A reliable session provides for SOAP messages what TCP provides for IP packets.</span></span> <span data-ttu-id="036d0-119">TCP 通訊端連線可在節點之間提供單數、依序的 IP 封包傳輸。</span><span class="sxs-lookup"><span data-stu-id="036d0-119">A TCP socket connection provides a singular, in-order transfer of IP packets between nodes.</span></span> <span data-ttu-id="036d0-120">可靠通道會提供同類型的可靠傳輸，但此傳輸在下列情況中會不同於 TCP 通訊端可靠性：</span><span class="sxs-lookup"><span data-stu-id="036d0-120">The reliable channel provides the same type of reliable transfer, but it differs from TCP socket reliability in the following ways:</span></span>

- <span data-ttu-id="036d0-121">可靠性位於 SOAP 訊息層級，且不適用任意大小的位元組封包。</span><span class="sxs-lookup"><span data-stu-id="036d0-121">The reliability is at the SOAP message level, not for an arbitrarily sized packet of bytes.</span></span>

- <span data-ttu-id="036d0-122">可靠性是傳輸中立，不只是針對透過 TCP 的傳輸。</span><span class="sxs-lookup"><span data-stu-id="036d0-122">The reliability is transport-neutral, not just for transfer over TCP.</span></span>

- <span data-ttu-id="036d0-123">可靠性未繫結至特定的傳輸工作階段 （例如，TCP 連線提供工作階段），可以使用多個傳輸工作階段並行或連續的可靠工作階段存留期。</span><span class="sxs-lookup"><span data-stu-id="036d0-123">The reliability isn't tied to a particular transport session (for example, the session a TCP connection provides) and can use multiple transport sessions concurrently or sequentially over the lifetime of the reliable session.</span></span>

- <span data-ttu-id="036d0-124">可靠工作階段適用於寄件者與接收者 SOAP 端點之間，而不管在兩者之間建立連線所需的傳輸連線數量為何。</span><span class="sxs-lookup"><span data-stu-id="036d0-124">The reliable session is between the sender and receiver SOAP endpoints, regardless of the number of transport connections required for connectivity between them.</span></span> <span data-ttu-id="036d0-125">簡單地說，TCP 可靠性會傳輸連線結束位置，而可靠的工作階段提供端對端可靠性。</span><span class="sxs-lookup"><span data-stu-id="036d0-125">In short, TCP reliability ends where the transport connection ends, while a reliable session provides end-to-end reliability.</span></span>

## <a name="reliable-sessions-and-bindings"></a><span data-ttu-id="036d0-126">可靠工作階段和繫結</span><span class="sxs-lookup"><span data-stu-id="036d0-126">Reliable sessions and bindings</span></span>

<span data-ttu-id="036d0-127">如先前所述，可靠工作階段是傳輸中性的特質。</span><span class="sxs-lookup"><span data-stu-id="036d0-127">As mentioned earlier, a reliable session is transport neutral.</span></span> <span data-ttu-id="036d0-128">此外，您也可以透過許多訊息交換模式，例如要求-回覆或雙工建立可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-128">Also, you can establish a reliable session over many message exchange patterns, such as request-reply or duplex.</span></span> <span data-ttu-id="036d0-129">WCF 可靠工作階段會公開為一組繫結的屬性。</span><span class="sxs-lookup"><span data-stu-id="036d0-129">A WCF reliable session is exposed as a property of a set of bindings.</span></span>

<span data-ttu-id="036d0-130">您可以使用可靠工作階段上使用的端點：</span><span class="sxs-lookup"><span data-stu-id="036d0-130">Use a reliable session on endpoints that use:</span></span>

- <span data-ttu-id="036d0-131">HTTP 傳輸標準繫結：</span><span class="sxs-lookup"><span data-stu-id="036d0-131">HTTP-based transport standard bindings:</span></span>

  - <span data-ttu-id="036d0-132">`WsHttpBinding` 並公開要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="036d0-132">`WsHttpBinding` and expose request-reply or one-way contracts.</span></span>

  - <span data-ttu-id="036d0-133">在透過要求-回覆或簡易單向服務合約使用可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-133">When using reliable session over a request-reply or simple one-way service contract.</span></span>

  - <span data-ttu-id="036d0-134">`WsDualHttpBinding` 並公開雙工、要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="036d0-134">`WsDualHttpBinding` and expose duplex, request-reply, or one-way contracts.</span></span>

  - <span data-ttu-id="036d0-135">`WsFederationHttpBinding` 並公開要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="036d0-135">`WsFederationHttpBinding` and expose request-reply or one-way contracts.</span></span>

- <span data-ttu-id="036d0-136">TCP 傳輸標準繫結：</span><span class="sxs-lookup"><span data-stu-id="036d0-136">TCP-based transport standard bindings:</span></span>

  - <span data-ttu-id="036d0-137">`NetTcpBinding` 並公開雙工、要求-回覆或單向合約。</span><span class="sxs-lookup"><span data-stu-id="036d0-137">`NetTcpBinding` and expose duplex, request reply, or one-way contracts.</span></span>

<span data-ttu-id="036d0-138">在其他任何繫結上使用可靠工作階段，方法是建立自訂繫結，例如 HTTPS (如需問題的詳細資訊，請參閱<a href="#reliable-sessions-and-security">可靠工作階段與安全性</a>) 或具名的管道繫結。</span><span class="sxs-lookup"><span data-stu-id="036d0-138">Use a reliable session on any other bindings by creating a custom binding, such as HTTPS (for more information about issues, see <a href="#reliable-sessions-and-security">Reliable sessions and security</a>) or a named pipe binding.</span></span>

<span data-ttu-id="036d0-139">您可以堆疊上不同基礎通道型別，可靠工作階段，並產生的可靠工作階段通道類型而有所不同。</span><span class="sxs-lookup"><span data-stu-id="036d0-139">You can stack a reliable session on different underlying channel types, and the resulting reliable session channel shape varies.</span></span> <span data-ttu-id="036d0-140">用戶端和伺服器所支援的可靠工作階段通道型別取決於所使用的基礎通道型別。</span><span class="sxs-lookup"><span data-stu-id="036d0-140">On both the client and the server, the type of reliable session channel supported depends on the type of underlying channel used.</span></span> <span data-ttu-id="036d0-141">下表列出用戶端上支援做為基礎通道型別功能的工作階段通道型別。</span><span class="sxs-lookup"><span data-stu-id="036d0-141">The following table lists the types of session channels supported on the client as a function of the underlying channel type.</span></span>

| <span data-ttu-id="036d0-142">支援可靠工作階段通道型別&#8224;</span><span class="sxs-lookup"><span data-stu-id="036d0-142">Supported reliable session channel types&#8224;</span></span> | `IRequestChannel` | `IRequestSessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :---------------: | :----------------------: | :--------------: | :---------------------: |
| `IOutputSessionChannel`                         | <span data-ttu-id="036d0-143">是</span><span class="sxs-lookup"><span data-stu-id="036d0-143">Yes</span></span>               | <span data-ttu-id="036d0-144">是</span><span class="sxs-lookup"><span data-stu-id="036d0-144">Yes</span></span>                      | <span data-ttu-id="036d0-145">是</span><span class="sxs-lookup"><span data-stu-id="036d0-145">Yes</span></span>              | <span data-ttu-id="036d0-146">是</span><span class="sxs-lookup"><span data-stu-id="036d0-146">Yes</span></span>                     |
| `IRequestSessionChannel`                        | <span data-ttu-id="036d0-147">是</span><span class="sxs-lookup"><span data-stu-id="036d0-147">Yes</span></span>               | <span data-ttu-id="036d0-148">是</span><span class="sxs-lookup"><span data-stu-id="036d0-148">Yes</span></span>                      | <span data-ttu-id="036d0-149">否</span><span class="sxs-lookup"><span data-stu-id="036d0-149">No</span></span>               | <span data-ttu-id="036d0-150">否</span><span class="sxs-lookup"><span data-stu-id="036d0-150">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="036d0-151">否</span><span class="sxs-lookup"><span data-stu-id="036d0-151">No</span></span>                | <span data-ttu-id="036d0-152">否</span><span class="sxs-lookup"><span data-stu-id="036d0-152">No</span></span>                       | <span data-ttu-id="036d0-153">是</span><span class="sxs-lookup"><span data-stu-id="036d0-153">Yes</span></span>              | <span data-ttu-id="036d0-154">是</span><span class="sxs-lookup"><span data-stu-id="036d0-154">Yes</span></span>                     |

<span data-ttu-id="036d0-155">&#8224;支援的通道型別是泛型所提供的值`TChannel`傳入的參數值<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29>方法。</span><span class="sxs-lookup"><span data-stu-id="036d0-155">&#8224;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelFactory%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

<span data-ttu-id="036d0-156">下表列出伺服器上支援做為基礎通道型別功能的工作階段通道型別。</span><span class="sxs-lookup"><span data-stu-id="036d0-156">The following table lists the types of session channels supported on the server as a function of the underlying channel type.</span></span>

| <span data-ttu-id="036d0-157">支援可靠工作階段通道型別&#8225;</span><span class="sxs-lookup"><span data-stu-id="036d0-157">Supported reliable session channel types&#8225;</span></span> | `IReplyChannel` | `IReplySessionChannel` | `IDuplexChannel` | `IDuplexSessionChannel` |
| ----------------------------------------------- | :-------------: | :--------------------: | :--------------: | :---------------------: |
| `IInputSessionChannel`                          | <span data-ttu-id="036d0-158">是</span><span class="sxs-lookup"><span data-stu-id="036d0-158">Yes</span></span>             | <span data-ttu-id="036d0-159">是</span><span class="sxs-lookup"><span data-stu-id="036d0-159">Yes</span></span>                    | <span data-ttu-id="036d0-160">是</span><span class="sxs-lookup"><span data-stu-id="036d0-160">Yes</span></span>              | <span data-ttu-id="036d0-161">是</span><span class="sxs-lookup"><span data-stu-id="036d0-161">Yes</span></span>                     |
| `IReplySessionChannel`                          | <span data-ttu-id="036d0-162">是</span><span class="sxs-lookup"><span data-stu-id="036d0-162">Yes</span></span>             | <span data-ttu-id="036d0-163">是</span><span class="sxs-lookup"><span data-stu-id="036d0-163">Yes</span></span>                    | <span data-ttu-id="036d0-164">否</span><span class="sxs-lookup"><span data-stu-id="036d0-164">No</span></span>               | <span data-ttu-id="036d0-165">否</span><span class="sxs-lookup"><span data-stu-id="036d0-165">No</span></span>                      |
| `IDuplexSessionChannel`                         | <span data-ttu-id="036d0-166">否</span><span class="sxs-lookup"><span data-stu-id="036d0-166">No</span></span>              | <span data-ttu-id="036d0-167">否</span><span class="sxs-lookup"><span data-stu-id="036d0-167">No</span></span>                     | <span data-ttu-id="036d0-168">是</span><span class="sxs-lookup"><span data-stu-id="036d0-168">Yes</span></span>              | <span data-ttu-id="036d0-169">是</span><span class="sxs-lookup"><span data-stu-id="036d0-169">Yes</span></span>                     |

<span data-ttu-id="036d0-170">&#8225;支援的通道型別是泛型所提供的值`TChannel`傳入的參數值<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29>方法。</span><span class="sxs-lookup"><span data-stu-id="036d0-170">&#8225;The supported channel types are the values available for the generic `TChannel` parameter value that is passed into the <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.BuildChannelListener%60%601%28System.ServiceModel.Channels.BindingContext%29> method.</span></span>

## <a name="reliable-sessions-and-security"></a><span data-ttu-id="036d0-171">可靠工作階段與安全性</span><span class="sxs-lookup"><span data-stu-id="036d0-171">Reliable sessions and security</span></span>

<span data-ttu-id="036d0-172">保護可靠工作階段務必要確定通訊雙方 （服務與用戶端） 會驗證和交換工作階段中的訊息未遭竄改。</span><span class="sxs-lookup"><span data-stu-id="036d0-172">Securing a reliable session is important to ensure that the communicating parties (service and client) are authenticated and that the messages exchanged in the session aren't tampered with.</span></span> <span data-ttu-id="036d0-173">此外，務必確保每個個別可靠工作階段的完整性。</span><span class="sxs-lookup"><span data-stu-id="036d0-173">Furthermore, it's important to ensure the integrity of each individual reliable session.</span></span> <span data-ttu-id="036d0-174">保護可靠工作階段繫結至具有代表並由安全性工作階段通道的安全性內容。</span><span class="sxs-lookup"><span data-stu-id="036d0-174">A reliable session is secured by binding it to a security context that's represented and managed by a security session channel.</span></span> <span data-ttu-id="036d0-175">安全性通道會提供安全性工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-175">The security channel provides a security session.</span></span> <span data-ttu-id="036d0-176">在工作階段的建立期間所交換的安全性權杖會接著用來保護可靠工作階段中的訊息安全。</span><span class="sxs-lookup"><span data-stu-id="036d0-176">Security tokens exchanged during the session establishment are then used to secure the messages in the reliable session.</span></span>

<span data-ttu-id="036d0-177">透過 TCP-S 可靠工作階段時，TCP 工作階段會繫結可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-177">When a reliable session is over TCP-S, the TCP session is tied to the reliable session.</span></span> <span data-ttu-id="036d0-178">因此，傳輸安全性可確保安全性也會繫結至可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-178">Therefore, transport security ensures that security is also tied to the reliable session.</span></span> <span data-ttu-id="036d0-179">在此情況下，會關閉連線的重新建立作業。</span><span class="sxs-lookup"><span data-stu-id="036d0-179">In this case, connection re-establishment is turned off.</span></span>

<span data-ttu-id="036d0-180">唯一的例外是在使用 HTTPS 時。</span><span class="sxs-lookup"><span data-stu-id="036d0-180">The only exception is when using HTTPS.</span></span> <span data-ttu-id="036d0-181">安全通訊端層 (SSL) 工作階段沒有繫結可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-181">The Secure Sockets Layer (SSL) session isn't bound to the reliable session.</span></span> <span data-ttu-id="036d0-182">這會造成威脅，因為共用安全性內容 （SSL 工作階段） 的工作階段不會受到保護彼此;這可能會或可能不是真正的威脅，根據應用程式。</span><span class="sxs-lookup"><span data-stu-id="036d0-182">This imposes a threat because sessions that are sharing a security context (the SSL session) aren't protected from each other; this might or might not be a real threat depending on the application.</span></span>

## <a name="using-reliable-sessions"></a><span data-ttu-id="036d0-183">使用可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="036d0-183">Using reliable sessions</span></span>

<span data-ttu-id="036d0-184">若要使用 WCF 可靠工作階段，建立支援可靠工作階段的繫結的端點。</span><span class="sxs-lookup"><span data-stu-id="036d0-184">To use WCF reliable sessions, create an endpoint with a binding that supports a reliable session.</span></span> <span data-ttu-id="036d0-185">使用 WCF 提供可靠的工作階段的系統提供繫結的其中一個已啟用，或建立您自己自訂的繫結此。</span><span class="sxs-lookup"><span data-stu-id="036d0-185">Use one of the system-provided bindings that WCF provides with the reliable session enabled or create your own custom binding that does this.</span></span>

<span data-ttu-id="036d0-186">根據預設，支援且啟用可靠工作階段的系統定義繫結包括：</span><span class="sxs-lookup"><span data-stu-id="036d0-186">The system-defined bindings that support and enable a reliable session by default include:</span></span>

- <xref:System.ServiceModel.WSDualHttpBinding>

<span data-ttu-id="036d0-187">支援可靠工作階段，但未啟用其中一個預設的系統提供繫結包括：</span><span class="sxs-lookup"><span data-stu-id="036d0-187">The system-provided bindings that support a reliable session as an option but don't enable one by default include:</span></span>

- <xref:System.ServiceModel.WSHttpBinding>

- <xref:System.ServiceModel.WSFederationHttpBinding>

- <xref:System.ServiceModel.NetTcpBinding>

<span data-ttu-id="036d0-188">如需如何建立自訂繫結的範例，請參閱[How to:使用 HTTPS 建立自訂可靠工作階段繫結](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md)。</span><span class="sxs-lookup"><span data-stu-id="036d0-188">For an example of how to create a custom binding, see [How to: Create a Custom Reliable Session Binding with HTTPS](../../../../docs/framework/wcf/feature-details/how-to-create-a-custom-reliable-session-binding-with-https.md).</span></span>

<span data-ttu-id="036d0-189">如需支援可靠工作階段的 WCF 繫結的討論，請參閱 < [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)。</span><span class="sxs-lookup"><span data-stu-id="036d0-189">For a discussion of WCF bindings that support reliable sessions, see [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md).</span></span>

## <a name="when-to-use-reliable-sessions"></a><span data-ttu-id="036d0-190">使用可靠工作階段的時機</span><span class="sxs-lookup"><span data-stu-id="036d0-190">When to use reliable sessions</span></span>

<span data-ttu-id="036d0-191">請務必了解應用程式中使用可靠工作階段的時機。</span><span class="sxs-lookup"><span data-stu-id="036d0-191">It's important to understand when to use reliable sessions in your application.</span></span> <span data-ttu-id="036d0-192">WCF 支援同時為作用中和執行的端點之間的可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-192">WCF supports reliable sessions between endpoints that are active and alive at the same time.</span></span> <span data-ttu-id="036d0-193">如果您的應用程式需要有一個端點無法使用一段時間，然後使用佇列來達到可靠性。</span><span class="sxs-lookup"><span data-stu-id="036d0-193">If your application requires one of the endpoints be unavailable for a duration of time, then use queues to achieve reliability.</span></span>

<span data-ttu-id="036d0-194">如果情況需要透過 TCP 連接的兩個端點，TCP 可能就足以提供可靠的訊息交換。</span><span class="sxs-lookup"><span data-stu-id="036d0-194">If the scenario requires two endpoints connected over TCP, then TCP may be sufficient to provide reliable message exchanges.</span></span> <span data-ttu-id="036d0-195">雖然不需要使用可靠工作階段，因為 TCP 可確保封包抵達順序，以及一次。</span><span class="sxs-lookup"><span data-stu-id="036d0-195">Although, it isn't necessary to use a reliable session, since TCP ensures that the packets arrive in order and only once.</span></span>

<span data-ttu-id="036d0-196">如果您的案例會有任何下列特性，則您必須認真考慮使用可靠工作階段。</span><span class="sxs-lookup"><span data-stu-id="036d0-196">If your scenario has any of the following characteristics, then you must seriously consider using a reliable session.</span></span>

- <span data-ttu-id="036d0-197">SOAP 媒介，例如 SOAP 路由器</span><span class="sxs-lookup"><span data-stu-id="036d0-197">SOAP intermediaries, such as SOAP routers</span></span>

- <span data-ttu-id="036d0-198">Proxy 媒介或傳輸橋接器</span><span class="sxs-lookup"><span data-stu-id="036d0-198">Proxy intermediaries or transport bridges</span></span>

- <span data-ttu-id="036d0-199">間歇性連線</span><span class="sxs-lookup"><span data-stu-id="036d0-199">Intermittent connectivity</span></span>

- <span data-ttu-id="036d0-200">透過 HTTP 工作階段</span><span class="sxs-lookup"><span data-stu-id="036d0-200">Sessions over HTTP</span></span>

## <a name="see-also"></a><span data-ttu-id="036d0-201">另請參閱</span><span class="sxs-lookup"><span data-stu-id="036d0-201">See also</span></span>

- [<span data-ttu-id="036d0-202">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="036d0-202">Using Bindings to Configure Services and Clients</span></span>](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="036d0-203">WS 可靠工作階段</span><span class="sxs-lookup"><span data-stu-id="036d0-203">WS Reliable Session</span></span>](../../../../docs/framework/wcf/samples/ws-reliable-session.md)
