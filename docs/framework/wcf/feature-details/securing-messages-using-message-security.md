---
title: 使用訊息安全性來保護訊息的安全
ms.date: 03/30/2017
ms.assetid: a17ebe67-836b-4c52-9a81-2c3d58e225ee
ms.openlocfilehash: 9ba8923d23140bb951a4993739ec267ad6f6a4c4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69911779"
---
# <a name="securing-messages-using-message-security"></a><span data-ttu-id="a78e2-102">使用訊息安全性來保護訊息的安全</span><span class="sxs-lookup"><span data-stu-id="a78e2-102">Securing Messages Using Message Security</span></span>
<span data-ttu-id="a78e2-103">本節將討論使用<xref:System.ServiceModel.NetMsmqBinding>時的 WCF 訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="a78e2-103">This section discusses WCF message security when using <xref:System.ServiceModel.NetMsmqBinding>.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="a78e2-104">閱讀本主題之前, 建議您先閱讀[安全性概念](../../../../docs/framework/wcf/feature-details/security-concepts.md)。</span><span class="sxs-lookup"><span data-stu-id="a78e2-104">Before reading through this topic, it is recommended that you read [Security Concepts](../../../../docs/framework/wcf/feature-details/security-concepts.md).</span></span>  
  
 <span data-ttu-id="a78e2-105">下圖提供使用 WCF 之佇列通訊的概念模型。</span><span class="sxs-lookup"><span data-stu-id="a78e2-105">The following illustration provides a conceptual model of queued communication using WCF.</span></span> <span data-ttu-id="a78e2-106">此圖例和術語是要用來說明</span><span class="sxs-lookup"><span data-stu-id="a78e2-106">This illustration and terminology are used to explain</span></span>  
  
 <span data-ttu-id="a78e2-107">傳輸安全性概念。</span><span class="sxs-lookup"><span data-stu-id="a78e2-107">transport security concepts.</span></span>  
  
 <span data-ttu-id="a78e2-108">![排入佇列的應用程式圖表](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "分散式-佇列-圖表")</span><span class="sxs-lookup"><span data-stu-id="a78e2-108">![Queued Application Diagram](../../../../docs/framework/wcf/feature-details/media/distributed-queue-figure.jpg "Distributed-Queue-Figure")</span></span>  
  
 <span data-ttu-id="a78e2-109">使用 WCF 傳送佇列訊息時, WCF 訊息會附加為訊息佇列 (MSMQ) 訊息的主體。</span><span class="sxs-lookup"><span data-stu-id="a78e2-109">When sending queued messages using WCF, the WCF message is attached as a body of the Message Queuing (MSMQ) message.</span></span> <span data-ttu-id="a78e2-110">傳輸安全性會保護整個 MSMQ 訊息的安全，而訊息 (或 SOAP) 安全性只能保護 MSMQ 訊息本文的安全。</span><span class="sxs-lookup"><span data-stu-id="a78e2-110">While transport security secures the entire MSMQ message, message (or SOAP) security only secures the body of the MSMQ message.</span></span>  
  
 <span data-ttu-id="a78e2-111">訊息安全性的重要概念是用戶端必須保護接收應用程式 (服務) 之訊息安全，這點不同於用戶端要保護目標佇列之訊息安全的傳輸安全性。</span><span class="sxs-lookup"><span data-stu-id="a78e2-111">The key concept of message security is that the client secures the message for the receiving application (service), unlike transport security where the client secures the message for the Target Queue.</span></span> <span data-ttu-id="a78e2-112">因此, 當使用訊息安全性保護 WCF 訊息時, MSMQ 不會扮演任何部分。</span><span class="sxs-lookup"><span data-stu-id="a78e2-112">As such, MSMQ plays no part when securing the WCF message using message security.</span></span>  
  
 <span data-ttu-id="a78e2-113">WCF 訊息安全性會將安全性標頭加入至與現有安全性基礎結構 (例如憑證或 Kerberos 通訊協定) 整合的 WCF 訊息。</span><span class="sxs-lookup"><span data-stu-id="a78e2-113">WCF message security adds security headers to the WCF message that integrate with existing security infrastructures, such as a certificate or the Kerberos protocol.</span></span>  
  
## <a name="message-credential-type"></a><span data-ttu-id="a78e2-114">訊息認證類型</span><span class="sxs-lookup"><span data-stu-id="a78e2-114">Message Credential Type</span></span>  
 <span data-ttu-id="a78e2-115">使用訊息安全性時，服務和用戶端可提供認證來彼此驗證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-115">Using message security, the service and client can present credentials to authenticate each another.</span></span> <span data-ttu-id="a78e2-116">您可以將 <xref:System.ServiceModel.NetMsmqBinding.Security%2A> 模式設定為 `Message` 或 `Both` (也就是同時使用傳輸安全性與訊息安全性) 來選取訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="a78e2-116">You can select message security by setting the <xref:System.ServiceModel.NetMsmqBinding.Security%2A> mode to `Message` or `Both` (that is, use both transport security and message security).</span></span>  
  
 <span data-ttu-id="a78e2-117">該服務可以使用 <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> 屬性來檢查用來驗證用戶端的認證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-117">The service can use the <xref:System.ServiceModel.ServiceSecurityContext.Current%2A> property to inspect the credential used to authenticate the client.</span></span> <span data-ttu-id="a78e2-118">這個屬性也可以用來進行服務所選擇實作的進一步授權檢查。</span><span class="sxs-lookup"><span data-stu-id="a78e2-118">This can also be used for further authorization checks that the service chooses to implement.</span></span>  
  
 <span data-ttu-id="a78e2-119">本章節會說明不同的認證類型，以及如何搭配佇列使用這些認證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-119">This section explains the different credential types and how to use them with queues.</span></span>  
  
### <a name="certificate"></a><span data-ttu-id="a78e2-120">憑證</span><span class="sxs-lookup"><span data-stu-id="a78e2-120">Certificate</span></span>  
 <span data-ttu-id="a78e2-121">憑證認證類型會使用 X.509 憑證來識別服務和用戶端。</span><span class="sxs-lookup"><span data-stu-id="a78e2-121">The certificate credential type uses an X.509 certificate to identify the service and the client.</span></span>  
  
 <span data-ttu-id="a78e2-122">在一般案例中，用戶端和服務都會由受信任的憑證授權單位發行有效的憑證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-122">In a typical scenario, the client and the service are issued a valid certificate by a trusted certification authority.</span></span> <span data-ttu-id="a78e2-123">接著在連線建立之後，用戶端會使用服務的憑證來驗證該服務的有效性，以決定是否能夠信任該服務。</span><span class="sxs-lookup"><span data-stu-id="a78e2-123">Then the connection is established, the client authenticates the validity of the service using the service's certificate to decide whether it can trust the service.</span></span> <span data-ttu-id="a78e2-124">同樣地，服務會使用該用戶端的憑證來驗證用戶端託管。</span><span class="sxs-lookup"><span data-stu-id="a78e2-124">Similarly, the service uses the client's certificate to validate the client trust.</span></span>  
  
 <span data-ttu-id="a78e2-125">由於佇列中斷的關係，用戶端和服務可能不會在同時位於線上。</span><span class="sxs-lookup"><span data-stu-id="a78e2-125">Given the disconnected nature of queues, the client and the service may not be online at the same time.</span></span> <span data-ttu-id="a78e2-126">因此，用戶端和服務必須超出範圍地交換憑證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-126">As such, the client and service have to exchange certificates out-of-band.</span></span> <span data-ttu-id="a78e2-127">尤其是用戶端因為有在其信任的存放區中保存服務的憑證 (該憑證可以鏈結至憑證授權單位)，所以它必定會信任自己是與正確的服務進行通訊。</span><span class="sxs-lookup"><span data-stu-id="a78e2-127">In particular, the client, by virtue of holding the service's certificate (which can be chained to a certification authority) in its trusted store, must trust that it is communicating with the correct service.</span></span> <span data-ttu-id="a78e2-128">為了驗證用戶端，服務會使用訊息附加的 X.509 憑證來比對在其存放區中的憑證，以便確認該用戶端的真實性。</span><span class="sxs-lookup"><span data-stu-id="a78e2-128">For authenticating the client, the service uses the X.509 certificate attached with the message to matches it with the certificate in its store to verify the authenticity of the client.</span></span> <span data-ttu-id="a78e2-129">同樣的，該憑證一定會鏈結至憑證授權單位。</span><span class="sxs-lookup"><span data-stu-id="a78e2-129">Again, the certificate must be chained to a certification authority.</span></span>  
  
 <span data-ttu-id="a78e2-130">在執行 Windows 的電腦上，憑證會保存在幾種存放區中。</span><span class="sxs-lookup"><span data-stu-id="a78e2-130">On a computer running Windows, certificates are held in several kinds of stores.</span></span> <span data-ttu-id="a78e2-131">如需不同存放區的詳細資訊, 請參閱[憑證存放區](https://go.microsoft.com/fwlink/?LinkId=87787)。</span><span class="sxs-lookup"><span data-stu-id="a78e2-131">For more information about the different stores, see [Certificate stores](https://go.microsoft.com/fwlink/?LinkId=87787).</span></span>  
  
### <a name="windows"></a><span data-ttu-id="a78e2-132">Windows</span><span class="sxs-lookup"><span data-stu-id="a78e2-132">Windows</span></span>  
 <span data-ttu-id="a78e2-133">Windows 訊息認證類型會使用 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a78e2-133">Windows message credential type uses the Kerberos protocol.</span></span>  
  
 <span data-ttu-id="a78e2-134">Kerberos 通訊協定是驗證網域上使用者的安全性機制，其可讓通過驗證的使用者透過網域上的其他實體來建立安全內容。</span><span class="sxs-lookup"><span data-stu-id="a78e2-134">The Kerberos protocol is a security mechanism that authenticates users on a domain and allows the authenticated users to establish secure contexts with other entities on a domain.</span></span>  
  
 <span data-ttu-id="a78e2-135">針對佇列通訊使用 Kerberos 通訊協定時所存在的一個問題，就是包含金鑰發佈中心 (KDC) 所發佈之用戶端身分識別的票證相對存留較短。</span><span class="sxs-lookup"><span data-stu-id="a78e2-135">The problem with using the Kerberos protocol for queued communication is that the tickets that contain client identity that the Key Distribution Center (KDC) distributes are relatively short-lived.</span></span> <span data-ttu-id="a78e2-136">*存留期*會與指出票證有效性的 Kerberos 票證相關聯。</span><span class="sxs-lookup"><span data-stu-id="a78e2-136">A *lifetime* is associated with the Kerberos ticket that indicates the validity of the ticket.</span></span> <span data-ttu-id="a78e2-137">因此，若為高度幕後性，您就無法確定該權杖對負責驗證用戶端的服務是否仍然有效。</span><span class="sxs-lookup"><span data-stu-id="a78e2-137">As such, given high latency, you cannot be sure that the token is still valid for the service that authenticates the client.</span></span>  
  
 <span data-ttu-id="a78e2-138">請注意，當使用這個認證類型時，服務必須在 SERVICE 帳戶下執行。</span><span class="sxs-lookup"><span data-stu-id="a78e2-138">Note that when using this credential type, the service must be running under the SERVICE account.</span></span>  
  
 <span data-ttu-id="a78e2-139">選擇訊息認證時會預設使用 Kerberos 通訊協定。</span><span class="sxs-lookup"><span data-stu-id="a78e2-139">The Kerberos protocol is used by default when choosing message credential.</span></span> <span data-ttu-id="a78e2-140">如需詳細資訊, 請參閱[探索 Kerberos, 這是 Windows 2000 中分散式安全性的通訊協定](https://go.microsoft.com/fwlink/?LinkId=87790)。</span><span class="sxs-lookup"><span data-stu-id="a78e2-140">For more information, see [Exploring Kerberos, the Protocol for Distributed Security in Windows 2000](https://go.microsoft.com/fwlink/?LinkId=87790).</span></span>  
  
### <a name="username-password"></a><span data-ttu-id="a78e2-141">Username Password</span><span class="sxs-lookup"><span data-stu-id="a78e2-141">Username Password</span></span>  
 <span data-ttu-id="a78e2-142">使用這個屬性，用戶端便可使用訊息之安全性標頭中的使用者名稱密碼，來向伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-142">Using this property, the client can authenticate to the server using a username password in the security header of the message.</span></span>  
  
### <a name="issuedtoken"></a><span data-ttu-id="a78e2-143">IssuedToken</span><span class="sxs-lookup"><span data-stu-id="a78e2-143">IssuedToken</span></span>  
 <span data-ttu-id="a78e2-144">用戶端可以使用安全性權杖服務來發行權杖，而此權杖會接著附加到訊息，以便服務用來驗證該用戶端。</span><span class="sxs-lookup"><span data-stu-id="a78e2-144">The client can use the security token service to issue a token that can then be attached to the message for the service to authenticate the client.</span></span>  
  
## <a name="using-transport-and-message-security"></a><span data-ttu-id="a78e2-145">使用傳輸和訊息安全性</span><span class="sxs-lookup"><span data-stu-id="a78e2-145">Using Transport and Message Security</span></span>  
 <span data-ttu-id="a78e2-146">當同時使用傳輸安全性和訊息安全性時，在傳輸層級和 SOAP 訊息層級中用來保護訊息安全的必須是相同的憑證。</span><span class="sxs-lookup"><span data-stu-id="a78e2-146">When using both transport security and message security, the certificate used to secure the message both at the transport and the SOAP message level must be the same.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a78e2-147">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a78e2-147">See also</span></span>

- [<span data-ttu-id="a78e2-148">使用傳輸安全性來保護訊息的安全</span><span class="sxs-lookup"><span data-stu-id="a78e2-148">Securing Messages Using Transport Security</span></span>](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)
- [<span data-ttu-id="a78e2-149">訊息佇列上的訊息安全性</span><span class="sxs-lookup"><span data-stu-id="a78e2-149">Message Security over Message Queuing</span></span>](../../../../docs/framework/wcf/samples/message-security-over-message-queuing.md)
- [<span data-ttu-id="a78e2-150">安全性概念</span><span class="sxs-lookup"><span data-stu-id="a78e2-150">Security Concepts</span></span>](../../../../docs/framework/wcf/feature-details/security-concepts.md)
- [<span data-ttu-id="a78e2-151">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="a78e2-151">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
