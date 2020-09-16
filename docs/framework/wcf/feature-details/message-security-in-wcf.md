---
title: WCF 中的訊息安全性
description: 瞭解 TransportWithMessageCredential，這是一種使用傳輸和訊息安全性模式組合的 WCF 訊息安全性。
ms.date: 03/30/2017
ms.assetid: a80efb59-591a-4a37-bb3c-8fffa6ca0b7d
ms.openlocfilehash: ea10a87a7c8f9e545c320af30c5cf9958317c2f7
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90551128"
---
# <a name="message-security-in-wcf"></a><span data-ttu-id="b51ff-103">WCF 中的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="b51ff-103">Message Security in WCF</span></span>

<span data-ttu-id="b51ff-104">Windows Communication Foundation (WCF) 有兩種主要模式可提供安全性 (`Transport` 和 `Message`) ，以及結合這兩者的第三種模式 (`TransportWithMessageCredential`) 。</span><span class="sxs-lookup"><span data-stu-id="b51ff-104">Windows Communication Foundation (WCF) has two major modes for providing security (`Transport` and `Message`) and a third mode (`TransportWithMessageCredential`) that combines the two.</span></span> <span data-ttu-id="b51ff-105">本主題將說明訊息安全性以及使用的原因。</span><span class="sxs-lookup"><span data-stu-id="b51ff-105">This topic discusses message security and the reasons to use it.</span></span>

## <a name="what-is-message-security"></a><span data-ttu-id="b51ff-106">什麼是訊息安全性？</span><span class="sxs-lookup"><span data-stu-id="b51ff-106">What Is Message Security?</span></span>

<span data-ttu-id="b51ff-107">訊息安全性會使用 WS-Security 規格來保護訊息的安全。</span><span class="sxs-lookup"><span data-stu-id="b51ff-107">Message security uses the WS-Security specification to secure messages.</span></span> <span data-ttu-id="b51ff-108">WS-MANAGEMENT 規格描述 SOAP 訊息的增強功能，以確保 SOAP 訊息層級 (的機密性、完整性和驗證，而不是) 傳輸層級。</span><span class="sxs-lookup"><span data-stu-id="b51ff-108">The WS-Security specification describes enhancements to SOAP messaging to ensure confidentiality, integrity, and authentication at the SOAP message level (instead of the transport level).</span></span>

<span data-ttu-id="b51ff-109">簡單的說，訊息安全性與傳輸安全性不同，它會連同訊息保護 (簽章或加密)，和每個訊息一起封裝安全性憑證和宣告。</span><span class="sxs-lookup"><span data-stu-id="b51ff-109">In brief, message security differs from transport security by encapsulating the security credentials and claims with every message along with any message protection (signing or encryption).</span></span> <span data-ttu-id="b51ff-110">藉由修改內容將安全性直接套用至訊息，可讓該安全訊息在有關安全性的方面上獨立。</span><span class="sxs-lookup"><span data-stu-id="b51ff-110">Applying the security directly to the message by modifying its content allows the secured message to be self-containing with respect to the security aspects.</span></span> <span data-ttu-id="b51ff-111">這會啟用一些在使用傳輸安全性時不可能發生的案例。</span><span class="sxs-lookup"><span data-stu-id="b51ff-111">This enables some scenarios that are not possible when transport security is used.</span></span>

## <a name="reasons-to-use-message-security"></a><span data-ttu-id="b51ff-112">使用訊息安全性的理由</span><span class="sxs-lookup"><span data-stu-id="b51ff-112">Reasons to Use Message Security</span></span>

<span data-ttu-id="b51ff-113">在訊息層級的安全性中，所有的安全性資訊都會封裝在訊息中。</span><span class="sxs-lookup"><span data-stu-id="b51ff-113">In message-level security, all of the security information is encapsulated in the message.</span></span> <span data-ttu-id="b51ff-114">使用訊息層級安全性取代傳輸層級安全性來保護訊息的安全有下列優點：</span><span class="sxs-lookup"><span data-stu-id="b51ff-114">Securing the message with message-level security instead of transport-level security has the following advantages:</span></span>

- <span data-ttu-id="b51ff-115">端對端安全性。</span><span class="sxs-lookup"><span data-stu-id="b51ff-115">End-to-end security.</span></span> <span data-ttu-id="b51ff-116">如 Secure Sockets Layer (SSL) 等傳輸安全性，只有在通訊是點對點時才會保護訊息安全。</span><span class="sxs-lookup"><span data-stu-id="b51ff-116">Transport security, such as Secure Sockets Layer (SSL) only secures messages when the communication is point-to-point.</span></span> <span data-ttu-id="b51ff-117">如果訊息在到達最終接收者之前，傳送至一個或多個 SOAP 媒介 (例如路由器)，則只要一個媒介從網路讀取該訊息，該訊息本身便不受保護。</span><span class="sxs-lookup"><span data-stu-id="b51ff-117">If the message is routed to one or more SOAP intermediaries (for example a router) before reaching the ultimate receiver, the message itself is not protected once an intermediary reads it from the wire.</span></span> <span data-ttu-id="b51ff-118">此外，用戶端驗證資訊只供第一個媒介使用，且如有需要，必須再次傳輸到以超出範圍方式接收的最終接收者。</span><span class="sxs-lookup"><span data-stu-id="b51ff-118">Additionally, the client authentication information is available only to the first intermediary and must be re-transmitted to the ultimate receiver in out-of-band fashion, if necessary.</span></span> <span data-ttu-id="b51ff-119">即使整個路由在個別躍點之間使用 SSL 安全性也適用。</span><span class="sxs-lookup"><span data-stu-id="b51ff-119">This applies even if the entire route uses SSL security between individual hops.</span></span> <span data-ttu-id="b51ff-120">由於訊息安全性是直接和訊息一起運作，並在其中保護 XML 的安全，因此不論在到達最終接收者之前包含多少個媒介，安全性都會伴隨訊息。</span><span class="sxs-lookup"><span data-stu-id="b51ff-120">Because message security works directly with the message and secures the XML in it, the security stays with the message regardless of how many intermediaries are involved before it reaches the ultimate receiver.</span></span> <span data-ttu-id="b51ff-121">這會啟用真正的端對端安全性案例。</span><span class="sxs-lookup"><span data-stu-id="b51ff-121">This enables a true end-to-end security scenario.</span></span>

- <span data-ttu-id="b51ff-122">增加的彈性。</span><span class="sxs-lookup"><span data-stu-id="b51ff-122">Increased flexibility.</span></span> <span data-ttu-id="b51ff-123">可簽署或加密部分訊息 (而非整個訊息)。</span><span class="sxs-lookup"><span data-stu-id="b51ff-123">Parts of the message, instead of the entire message, can be signed or encrypted.</span></span> <span data-ttu-id="b51ff-124">這表示媒介可以檢視為它們提供的部分訊息。</span><span class="sxs-lookup"><span data-stu-id="b51ff-124">This means that intermediaries can view the parts of the message that are intended for them.</span></span> <span data-ttu-id="b51ff-125">如果傳送者需要讓媒介看到訊息中的部分資訊，但希望確保不會遭到竄改，可以只簽署而不加密。</span><span class="sxs-lookup"><span data-stu-id="b51ff-125">If the sender needs to make part of the information in the message visible to the intermediaries but wants to ensure that it is not tampered with, it can just sign it but leave it unencrypted.</span></span> <span data-ttu-id="b51ff-126">由於簽章是訊息的一部分，因此最終接收者可以確認已完整接收訊息中的資訊。</span><span class="sxs-lookup"><span data-stu-id="b51ff-126">Since the signature is part of the message, the ultimate receiver can verify that the information in the message was received intact.</span></span> <span data-ttu-id="b51ff-127">有一種案例可能會有根據 Action 標頭值傳送訊息的 SOAP 媒介服務。</span><span class="sxs-lookup"><span data-stu-id="b51ff-127">One scenario might have a SOAP intermediary service that routes message according the Action header value.</span></span> <span data-ttu-id="b51ff-128">根據預設，WCF 不會加密動作值，但會在使用訊息安全性時加以簽署。</span><span class="sxs-lookup"><span data-stu-id="b51ff-128">By default, WCF does not encrypt the Action value but signs it if message security is used.</span></span> <span data-ttu-id="b51ff-129">因此，此資訊可供所有媒介使用，但是無法變更。</span><span class="sxs-lookup"><span data-stu-id="b51ff-129">Therefore, this information is available to all intermediaries, but no one can change it.</span></span>

- <span data-ttu-id="b51ff-130">支援多重傳輸。</span><span class="sxs-lookup"><span data-stu-id="b51ff-130">Support for multiple transports.</span></span> <span data-ttu-id="b51ff-131">您可以使用許多不同的傳輸來傳送安全訊息，例如具名管道和 TCP，而不必依賴通訊協定來達到安全性。</span><span class="sxs-lookup"><span data-stu-id="b51ff-131">You can send secured messages over many different transports, such as named pipes and TCP, without having to rely on the protocol for security.</span></span> <span data-ttu-id="b51ff-132">使用傳輸層級安全性，所有的安全性資訊都會限定在單一特定傳輸連線的範圍內，並且無法從訊息內容本身取得。</span><span class="sxs-lookup"><span data-stu-id="b51ff-132">With transport-level security, all the security information is scoped to a single particular transport connection and is not available from the message content itself.</span></span> <span data-ttu-id="b51ff-133">不論您使用何種傳輸來傳輸訊息，訊息安全性都可以保護訊息的安全，且安全性內容會直接內嵌在訊息中。</span><span class="sxs-lookup"><span data-stu-id="b51ff-133">Message security makes the message secure regardless of what transport you use to transmit the message, and the security context is directly embedded inside the message.</span></span>

- <span data-ttu-id="b51ff-134">支援一整組認證和宣告。</span><span class="sxs-lookup"><span data-stu-id="b51ff-134">Support for a wide set of credentials and claims.</span></span> <span data-ttu-id="b51ff-135">訊息安全性是以 WS-Security 規格為基礎，提供可傳輸 SOAP 訊息內任何類型宣告的可延伸架構。</span><span class="sxs-lookup"><span data-stu-id="b51ff-135">The message security is based on the WS-Security specification, which provides an extensible framework capable of transmitting any type of claim inside the SOAP message.</span></span> <span data-ttu-id="b51ff-136">和傳輸安全性不同的是，您可以使用的驗證機制 (或宣告) 集合不受傳輸功能的限制。</span><span class="sxs-lookup"><span data-stu-id="b51ff-136">Unlike transport security, the set of authentication mechanisms, or claims, that you can use is not limited by the transport capabilities.</span></span> <span data-ttu-id="b51ff-137">WCF 訊息安全性包括多種類型的驗證和宣告傳輸，而且可以視需要擴充以支援其他類型。</span><span class="sxs-lookup"><span data-stu-id="b51ff-137">WCF message security includes multiple types of authentication and claim transmission and can be extended to support additional types as necessary.</span></span> <span data-ttu-id="b51ff-138">例如，基於這些原因，聯合認證案例一定要有訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="b51ff-138">For those reasons, for example, a federated credentials scenario is not possible without message security.</span></span> <span data-ttu-id="b51ff-139">如需 WCF 支援之同盟案例的詳細資訊，請參閱 [同盟和已發行的權杖](federation-and-issued-tokens.md)。</span><span class="sxs-lookup"><span data-stu-id="b51ff-139">For more information about federation scenarios WCF supports, see [Federation and Issued Tokens](federation-and-issued-tokens.md).</span></span>

## <a name="how-message-and-transport-security-compare"></a><span data-ttu-id="b51ff-140">如何比較訊息和傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="b51ff-140">How Message and Transport Security Compare</span></span>

### <a name="pros-and-cons-of-transport-level-security"></a><span data-ttu-id="b51ff-141">傳輸層級安全性的優缺點</span><span class="sxs-lookup"><span data-stu-id="b51ff-141">Pros and Cons of Transport-Level Security</span></span>

<span data-ttu-id="b51ff-142">傳輸安全性有下列優點：</span><span class="sxs-lookup"><span data-stu-id="b51ff-142">Transport security has the following advantages:</span></span>

- <span data-ttu-id="b51ff-143">不需要通訊方瞭解 XML 層級的安全性概念。</span><span class="sxs-lookup"><span data-stu-id="b51ff-143">Does not require that the communicating parties understand XML-level security concepts.</span></span> <span data-ttu-id="b51ff-144">這可以增進互通性，例如當使用 HTTPS 來保護通訊安全時。</span><span class="sxs-lookup"><span data-stu-id="b51ff-144">This can improve the interoperability, for example, when HTTPS is used to secure the communication.</span></span>

- <span data-ttu-id="b51ff-145">普遍提升效能。</span><span class="sxs-lookup"><span data-stu-id="b51ff-145">Generally improved performance.</span></span>

- <span data-ttu-id="b51ff-146">提供硬體加速器。</span><span class="sxs-lookup"><span data-stu-id="b51ff-146">Hardware accelerators are available.</span></span>

- <span data-ttu-id="b51ff-147">可使用資料流。</span><span class="sxs-lookup"><span data-stu-id="b51ff-147">Streaming is possible.</span></span>

 <span data-ttu-id="b51ff-148">傳輸安全性有下列缺點：</span><span class="sxs-lookup"><span data-stu-id="b51ff-148">Transport security has the following disadvantages:</span></span>

- <span data-ttu-id="b51ff-149">僅限躍點對躍點。</span><span class="sxs-lookup"><span data-stu-id="b51ff-149">Hop-to-hop only.</span></span>

- <span data-ttu-id="b51ff-150">有限且無法延伸的認證集合。</span><span class="sxs-lookup"><span data-stu-id="b51ff-150">Limited and inextensible set of credentials.</span></span>

- <span data-ttu-id="b51ff-151">與傳輸相關。</span><span class="sxs-lookup"><span data-stu-id="b51ff-151">Transport-dependent.</span></span>

### <a name="disadvantages-of-message-level-security"></a><span data-ttu-id="b51ff-152">訊息層級安全性的缺點</span><span class="sxs-lookup"><span data-stu-id="b51ff-152">Disadvantages of Message-Level Security</span></span>

<span data-ttu-id="b51ff-153">訊息安全性有下列缺點：</span><span class="sxs-lookup"><span data-stu-id="b51ff-153">Message security has the following disadvantages:</span></span>

- <span data-ttu-id="b51ff-154">效能</span><span class="sxs-lookup"><span data-stu-id="b51ff-154">Performance</span></span>

- <span data-ttu-id="b51ff-155">無法使用訊息資料流。</span><span class="sxs-lookup"><span data-stu-id="b51ff-155">Cannot use message streaming.</span></span>

- <span data-ttu-id="b51ff-156">需要實作 XML 層級的安全性機制及支援 WS-Security 規格。</span><span class="sxs-lookup"><span data-stu-id="b51ff-156">Requires implementation of XML-level security mechanisms and support for WS-Security specification.</span></span> <span data-ttu-id="b51ff-157">這可能會影響互通性。</span><span class="sxs-lookup"><span data-stu-id="b51ff-157">This might affect the interoperability.</span></span>

## <a name="see-also"></a><span data-ttu-id="b51ff-158">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b51ff-158">See also</span></span>

- [<span data-ttu-id="b51ff-159">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="b51ff-159">Securing Services and Clients</span></span>](securing-services-and-clients.md)
- [<span data-ttu-id="b51ff-160">傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="b51ff-160">Transport Security</span></span>](transport-security.md)
- [<span data-ttu-id="b51ff-161">作法：使用傳輸安全性和訊息認證</span><span class="sxs-lookup"><span data-stu-id="b51ff-161">How to: Use Transport Security and Message Credentials</span></span>](how-to-use-transport-security-and-message-credentials.md)
- <span data-ttu-id="b51ff-162">[Microsoft 典範與實例，第 3 章：實作傳輸和訊息層安全性](/previous-versions/msp-n-p/ff647370(v=pandp.10))</span><span class="sxs-lookup"><span data-stu-id="b51ff-162">[Microsoft Patterns and Practices, Chapter 3: Implementing Transport and Message Layer Security](/previous-versions/msp-n-p/ff647370(v=pandp.10))</span></span>
