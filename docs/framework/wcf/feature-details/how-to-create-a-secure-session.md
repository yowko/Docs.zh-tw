---
title: HOW TO：建立安全工作階段
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 80973a31050cf1ede03d4a3919066c62625ae590
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84593408"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="d4684-102">HOW TO：建立安全工作階段</span><span class="sxs-lookup"><span data-stu-id="d4684-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="d4684-103">除了系結以外 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ，Windows Communication Foundation （WCF）中的系統提供系結會在啟用訊息安全性時，自動使用安全會話。</span><span class="sxs-lookup"><span data-stu-id="d4684-103">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="d4684-104">根據預設，安全工作階段不會存留回收的 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d4684-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="d4684-105">當建立安全工作階段時，用戶端和服務會快取與安全工作階段有關聯的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d4684-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="d4684-106">當交換訊息時，只會交換快取索引鍵的識別碼。</span><span class="sxs-lookup"><span data-stu-id="d4684-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="d4684-107">如果回收 Web 伺服器，也會回收快取，讓 Web 伺服器無法為識別碼擷取快取索引鍵。</span><span class="sxs-lookup"><span data-stu-id="d4684-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="d4684-108">如果發生這種情況，便會將例外狀況擲回用戶端。</span><span class="sxs-lookup"><span data-stu-id="d4684-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="d4684-109">使用可設定狀態之安全性內容權杖 (SCT) 的安全工作階段可以存留已回收的 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="d4684-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="d4684-110">如需在安全會話中使用可設定狀態之 SCT 的詳細資訊，請參閱[如何：為安全會話建立安全性內容 Token](how-to-create-a-security-context-token-for-a-secure-session.md)。</span><span class="sxs-lookup"><span data-stu-id="d4684-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="d4684-111">使用其中一個系統提供的繫結來指定服務使用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="d4684-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
- <span data-ttu-id="d4684-112">請將服務設定為使用支援訊息安全性之系統提供的繫結。</span><span class="sxs-lookup"><span data-stu-id="d4684-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="d4684-113">除了系結之外 [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) ，當系統提供的系結設定為使用訊息安全性時，WCF 會自動使用安全會話。</span><span class="sxs-lookup"><span data-stu-id="d4684-113">With the exception of the [\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="d4684-114">下表列出了支援訊息安全性之系統提供的繫結，以及訊息安全性是否為預設的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="d4684-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="d4684-115">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d4684-115">System-provided binding</span></span>|<span data-ttu-id="d4684-116">設定元素</span><span class="sxs-lookup"><span data-stu-id="d4684-116">Configuration element</span></span>|<span data-ttu-id="d4684-117">訊息安全性預設為開啟</span><span class="sxs-lookup"><span data-stu-id="d4684-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../../configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="d4684-118">否</span><span class="sxs-lookup"><span data-stu-id="d4684-118">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="d4684-119">是</span><span class="sxs-lookup"><span data-stu-id="d4684-119">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="d4684-120">是</span><span class="sxs-lookup"><span data-stu-id="d4684-120">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="d4684-121">是</span><span class="sxs-lookup"><span data-stu-id="d4684-121">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="d4684-122">否</span><span class="sxs-lookup"><span data-stu-id="d4684-122">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../../configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="d4684-123">否</span><span class="sxs-lookup"><span data-stu-id="d4684-123">No</span></span>|  
  
     <span data-ttu-id="d4684-124">下列程式碼範例會使用設定來指定名為的系結，該系結 `wsHttpBinding_Calculator` 會使用 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 、訊息安全性和安全會話。</span><span class="sxs-lookup"><span data-stu-id="d4684-124">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
    ```xml  
    <bindings>  
      <WSHttpBinding>  
       <binding name = "wsHttpBinding_Calculator">  
         <security mode="Message">  
           <message clientCredentialType="Windows"/>  
         </security>  
        </binding>  
      </WSHttpBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="d4684-125">下列程式碼範例 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 會指定使用、訊息安全性和安全會話來保護 `secureCalculator` 服務。</span><span class="sxs-lookup"><span data-stu-id="d4684-125">The following code example specifies that the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    > <span data-ttu-id="d4684-126">您可以藉 [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) 由將屬性設定為，關閉的安全會話 `establishSecurityContext` `false` 。</span><span class="sxs-lookup"><span data-stu-id="d4684-126">Secure sessions can be turned off for the [\<wsHttpBinding>](../../configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="d4684-127">對於其他系統提供的繫結程序，安全工作階段只能藉由建立自訂繫結程序來關閉。</span><span class="sxs-lookup"><span data-stu-id="d4684-127">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="d4684-128">使用自訂繫結來指定服務使用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="d4684-128">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
- <span data-ttu-id="d4684-129">請建立自訂繫結，指定 SOAP 訊息受到安全工作階段的保護。</span><span class="sxs-lookup"><span data-stu-id="d4684-129">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="d4684-130">如需建立自訂系結的詳細資訊，請參閱[如何：自訂系統提供](../extending/how-to-customize-a-system-provided-binding.md)的系結。</span><span class="sxs-lookup"><span data-stu-id="d4684-130">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="d4684-131">下列程式碼範例會使用組態來指定使用安全工作階段傳送訊息的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d4684-131">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
    ```xml  
    <bindings>  
      <!-- configure a custom binding -->  
      <customBinding>  
        <binding name="customBinding_Calculator">  
          <security authenticationMode="SecureConversation" />  
          <secureConversationBootstrap authenticationMode="SspiNegotiated" />  
          <textMessageEncoding messageVersion="Soap12WSAddressing10" writeEncoding="utf-8"/>  
          <httpTransport/>  
        </binding>  
      </customBinding>  
    </bindings>  
    ```  
  
     <span data-ttu-id="d4684-132">下列程式碼範例建立了一個會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 驗證模式來啟動載入安全工作階段的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="d4684-132">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d4684-133">請參閱</span><span class="sxs-lookup"><span data-stu-id="d4684-133">See also</span></span>

- [<span data-ttu-id="d4684-134">WCF 繫結概觀</span><span class="sxs-lookup"><span data-stu-id="d4684-134">WCF Bindings Overview</span></span>](../bindings-overview.md)
