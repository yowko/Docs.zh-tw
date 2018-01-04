---
title: "確保對等通道應用程式安全"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
ms.assetid: d4a0311d-3f78-4525-9c4b-5c93c4492f28
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 7358852ffc50576f892c70fa2b212a8102d8ab85
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="securing-peer-channel-applications"></a><span data-ttu-id="fddaf-102">確保對等通道應用程式安全</span><span class="sxs-lookup"><span data-stu-id="fddaf-102">Securing Peer Channel Applications</span></span>
<span data-ttu-id="fddaf-103">和 [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)] 下的其他繫結一樣，`NetPeerTcpBinding` 預設已啟用安全性，並且會提供傳輸和訊息型安全性 (或兩者皆提供)。</span><span class="sxs-lookup"><span data-stu-id="fddaf-103">Like other bindings under the [!INCLUDE[vstecwinfx](../../../../includes/vstecwinfx-md.md)], `NetPeerTcpBinding` has security enabled by default and offers both transport- and message-based security (or both).</span></span> <span data-ttu-id="fddaf-104">這個主題會討論這兩種類型的安全性。</span><span class="sxs-lookup"><span data-stu-id="fddaf-104">This topic discusses these two types of security.</span></span> <span data-ttu-id="fddaf-105">安全性類型則是由繫結規格中的安全性模式標記所指定 (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`)。</span><span class="sxs-lookup"><span data-stu-id="fddaf-105">The type of security is specified by the security mode tag in the binding specification (<xref:System.ServiceModel.NetPeerTcpBinding.Security%2A>`Mode`).</span></span>  
  
## <a name="transport-based-security"></a><span data-ttu-id="fddaf-106">傳輸型安全性</span><span class="sxs-lookup"><span data-stu-id="fddaf-106">Transport-Based Security</span></span>  
 <span data-ttu-id="fddaf-107">對等通道支援兩種可用來保護傳輸的驗證認證類型，這兩種類型都需要在相關聯的 `ClientCredentialSettings.Peer` 上設定 `ChannelFactory` 屬性：</span><span class="sxs-lookup"><span data-stu-id="fddaf-107">Peer Channel supports two types of authentication credentials for securing transport, both of which require setting out the `ClientCredentialSettings.Peer` property on the associated `ChannelFactory`:</span></span>  
  
-   <span data-ttu-id="fddaf-108">密碼。</span><span class="sxs-lookup"><span data-stu-id="fddaf-108">Password.</span></span> <span data-ttu-id="fddaf-109">用戶端會運用已知的機密密碼來驗證連線。</span><span class="sxs-lookup"><span data-stu-id="fddaf-109">Clients use knowledge of a secret password to authenticate connections.</span></span> <span data-ttu-id="fddaf-110">使用這個認證類型時，`ClientCredentialSettings.Peer.MeshPassword` 必須傳遞有效的密碼並選擇性傳遞 `X509Certificate2` 執行個體。</span><span class="sxs-lookup"><span data-stu-id="fddaf-110">When this credential type is used, `ClientCredentialSettings.Peer.MeshPassword` must carry a valid password and optionally an `X509Certificate2` instance.</span></span>  
  
-   <span data-ttu-id="fddaf-111">憑證。</span><span class="sxs-lookup"><span data-stu-id="fddaf-111">Certificate.</span></span> <span data-ttu-id="fddaf-112">將會使用特定的應用程式驗證。</span><span class="sxs-lookup"><span data-stu-id="fddaf-112">Specific application authentication is used.</span></span> <span data-ttu-id="fddaf-113">使用這個認證類型時，您必須在 <xref:System.IdentityModel.Selectors.X509CertificateValidator> 中使用實體 `ClientCredentialSettings.Peer.PeerAuthentication` 實作。</span><span class="sxs-lookup"><span data-stu-id="fddaf-113">When this credential type is used, you must use a concrete implementation of <xref:System.IdentityModel.Selectors.X509CertificateValidator> in `ClientCredentialSettings.Peer.PeerAuthentication`.</span></span>  
  
## <a name="message-based-security"></a><span data-ttu-id="fddaf-114">訊息型安全性</span><span class="sxs-lookup"><span data-stu-id="fddaf-114">Message-Based Security</span></span>  
 <span data-ttu-id="fddaf-115">使用訊息安全性時，應用程式可以簽署傳輸訊息，因此所有接收方都可驗證是否從信任的一方傳出訊息，而且該訊息並沒有遭到竄改。</span><span class="sxs-lookup"><span data-stu-id="fddaf-115">Using message security, an application can sign outgoing messages so that all receiving parties can verify the message is sent by a trusted party and that the message was not tampered with.</span></span> <span data-ttu-id="fddaf-116">目前對等通道僅支援 X.509 認證的訊息簽署。</span><span class="sxs-lookup"><span data-stu-id="fddaf-116">Currently, Peer Channel supports only X.509 credential message signing.</span></span>  
  
## <a name="best-practices"></a><span data-ttu-id="fddaf-117">最佳作法</span><span class="sxs-lookup"><span data-stu-id="fddaf-117">Best Practices</span></span>  
  
-   <span data-ttu-id="fddaf-118">本節會討論保護對等通道應用程式安全的最佳做法。</span><span class="sxs-lookup"><span data-stu-id="fddaf-118">This section discusses the best practices for securing Peer Channel applications.</span></span>  
  
### <a name="enable-security-with-peer-channel-applications"></a><span data-ttu-id="fddaf-119">啟用對等通道應用程式的安全性</span><span class="sxs-lookup"><span data-stu-id="fddaf-119">Enable Security with Peer Channel Applications</span></span>  
 <span data-ttu-id="fddaf-120">有鑑於對等通道通訊協定的分散式特性，在不安全的網狀結構中很難強制施行網狀結構成員資格、機密性和隱私權。</span><span class="sxs-lookup"><span data-stu-id="fddaf-120">Due to the distributed nature of the Peer Channel protocols, it is hard to enforce mesh membership, confidentiality, and privacy in an unsecured mesh.</span></span> <span data-ttu-id="fddaf-121">而記住用戶端和解析程式服務之間的安全通訊也相當重要。</span><span class="sxs-lookup"><span data-stu-id="fddaf-121">It is also important to remember to secure communication between clients and the resolver service.</span></span> <span data-ttu-id="fddaf-122">在套用對等名稱解析通訊協定 (PNRP) 時，請使用安全名稱來避免詐騙和其他常見攻擊。</span><span class="sxs-lookup"><span data-stu-id="fddaf-122">Under Peer Name Resolution Protocol (PNRP), use secure names to avoid spoofing and other common attacks.</span></span> <span data-ttu-id="fddaf-123">啟用連線用戶端使用上的安全性以連絡解析程式服務，即可保護自訂解析程式服務，而這包括了訊息和傳輸型安全性。</span><span class="sxs-lookup"><span data-stu-id="fddaf-123">Secure a custom resolver service by enabling security on the connection clients use to contact the resolver service, including both message- and transport-based security.</span></span>  
  
### <a name="use-the-strongest-possible-security-model"></a><span data-ttu-id="fddaf-124">使用最強的可能安全性模型</span><span class="sxs-lookup"><span data-stu-id="fddaf-124">Use the Strongest Possible Security Model</span></span>  
 <span data-ttu-id="fddaf-125">例如，如果網狀結構的每個成員都需要個別識別，請使用憑證型驗證模型。</span><span class="sxs-lookup"><span data-stu-id="fddaf-125">For example, if each member of the mesh needs to be individually identified, use certificate-based authentication model.</span></span> <span data-ttu-id="fddaf-126">如果不可能這樣做，請使用密碼型驗證，再使用目前的建議以保持其安全。</span><span class="sxs-lookup"><span data-stu-id="fddaf-126">If that is not possible, use password-based authentication following current recommendations to keep them secure.</span></span> <span data-ttu-id="fddaf-127">這包括僅與受信任的對象共用密碼、使用安全媒介傳輸密碼、經常變更密碼以及確保密碼為強式 (長度至少為八個字元，其中至少包括大小寫字母、數字和特殊字元)。</span><span class="sxs-lookup"><span data-stu-id="fddaf-127">This includes sharing passwords only with trusted parties, transmitting passwords using a secure medium, changing passwords frequently, and ensuring that passwords are strong (at least eight characters long, include at least one letter from both cases, a digit, and a special character).</span></span>  
  
### <a name="never-accept-self-signed-certificates"></a><span data-ttu-id="fddaf-128">永不接受自我簽署的憑證</span><span class="sxs-lookup"><span data-stu-id="fddaf-128">Never Accept Self-Signed Certificates</span></span>  
 <span data-ttu-id="fddaf-129">永不接受以主體名稱為基礎的憑證認證。</span><span class="sxs-lookup"><span data-stu-id="fddaf-129">Never accept a certificate credential based on subject names.</span></span> <span data-ttu-id="fddaf-130">請注意，任何人都可建立憑證，而任何人也都可以選擇您要驗證的名稱。</span><span class="sxs-lookup"><span data-stu-id="fddaf-130">Note that anyone can create a certificate, and anyone can choose a name that you are validating.</span></span> <span data-ttu-id="fddaf-131">若要避免可能發生詐騙，請根據發行授權單位的認證來驗證憑證 (信任的簽發者或根憑證授權單位)。</span><span class="sxs-lookup"><span data-stu-id="fddaf-131">To avoid the possibility of spoofing, validate certificates based on issuing authority credentials (either a trusted issuer or a root certification authority).</span></span>  
  
### <a name="use-message-authentication"></a><span data-ttu-id="fddaf-132">使用訊息驗證</span><span class="sxs-lookup"><span data-stu-id="fddaf-132">Use Message Authentication</span></span>  
 <span data-ttu-id="fddaf-133">使用訊息驗證以驗證源自於信任來源的訊息，並驗證傳輸期間沒有任何人竄改訊息。</span><span class="sxs-lookup"><span data-stu-id="fddaf-133">Use message authentication to verify that a message originated from a trusted source and that no one has tampered with the message during transmission.</span></span> <span data-ttu-id="fddaf-134">如果不使用訊息驗證，就很容易讓惡意用戶端詐騙或竄改網狀結構中的訊息。</span><span class="sxs-lookup"><span data-stu-id="fddaf-134">Without message authentication, it is easy for a malicious client to spoof or tamper with messages in the mesh.</span></span>  
  
## <a name="peer-channel-code-examples"></a><span data-ttu-id="fddaf-135">對等通道程式碼範例</span><span class="sxs-lookup"><span data-stu-id="fddaf-135">Peer Channel Code Examples</span></span>  
 [<span data-ttu-id="fddaf-136">對等通道案例</span><span class="sxs-lookup"><span data-stu-id="fddaf-136">Peer Channel Scenarios</span></span>](../../../../docs/framework/wcf/feature-details/peer-channel-scenarios.md)  
  
## <a name="see-also"></a><span data-ttu-id="fddaf-137">請參閱</span><span class="sxs-lookup"><span data-stu-id="fddaf-137">See Also</span></span>  
 [<span data-ttu-id="fddaf-138">對等通道安全性</span><span class="sxs-lookup"><span data-stu-id="fddaf-138">Peer Channel Security</span></span>](../../../../docs/framework/wcf/feature-details/peer-channel-security.md)  
 [<span data-ttu-id="fddaf-139">建置對等通道應用程式</span><span class="sxs-lookup"><span data-stu-id="fddaf-139">Building a Peer Channel Application</span></span>](../../../../docs/framework/wcf/feature-details/building-a-peer-channel-application.md)
