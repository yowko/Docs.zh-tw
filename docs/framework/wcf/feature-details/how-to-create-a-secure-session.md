---
title: HOW TO：建立安全工作階段
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- security [WCF], creating a session
ms.assetid: b6f42b5a-bbf7-45cf-b917-7ec9fa7ae110
ms.openlocfilehash: 4464100012fe9b3e1f0e8743707b1dc9a477c3d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59205884"
---
# <a name="how-to-create-a-secure-session"></a><span data-ttu-id="16ae3-102">HOW TO：建立安全工作階段</span><span class="sxs-lookup"><span data-stu-id="16ae3-102">How to: Create a Secure Session</span></span>
<span data-ttu-id="16ae3-103">除了[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)繫結時，系統提供繫結 Windows Communication Foundation (WCF) 中自動使用訊息安全性啟用時的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="16ae3-103">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, the system-provided bindings in Windows Communication Foundation (WCF) automatically use secure sessions when message security is enabled.</span></span>  
  
 <span data-ttu-id="16ae3-104">根據預設，安全工作階段不會存留回收的 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="16ae3-104">By default, secure sessions do not survive a Web server that is recycled.</span></span> <span data-ttu-id="16ae3-105">當建立安全工作階段時，用戶端和服務會快取與安全工作階段有關聯的索引鍵。</span><span class="sxs-lookup"><span data-stu-id="16ae3-105">When a secure session is established, the client and the service cache the key that is associated with the secure session.</span></span> <span data-ttu-id="16ae3-106">當交換訊息時，只會交換快取索引鍵的識別碼。</span><span class="sxs-lookup"><span data-stu-id="16ae3-106">As the messages are exchanged, only an identifier to the cached key is exchanged.</span></span> <span data-ttu-id="16ae3-107">如果回收 Web 伺服器，也會回收快取，讓 Web 伺服器無法為識別碼擷取快取索引鍵。</span><span class="sxs-lookup"><span data-stu-id="16ae3-107">If the Web server is recycled, the cache is also recycled, such that the Web server cannot retrieve the cached key for the identifier.</span></span> <span data-ttu-id="16ae3-108">如果發生這種情況，便會將例外狀況擲回用戶端。</span><span class="sxs-lookup"><span data-stu-id="16ae3-108">If this happens, an exception is thrown back to the client.</span></span> <span data-ttu-id="16ae3-109">使用可設定狀態之安全性內容權杖 (SCT) 的安全工作階段可以存留已回收的 Web 伺服器。</span><span class="sxs-lookup"><span data-stu-id="16ae3-109">Secure sessions that use a stateful security context token (SCT) can survive a Web server being recycled.</span></span> <span data-ttu-id="16ae3-110">如需使用安全工作階段中的具狀態的 SCT 的詳細資訊，請參閱[How to:建立安全性內容權杖的安全工作階段](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md)。</span><span class="sxs-lookup"><span data-stu-id="16ae3-110">For more information about using a stateful SCT in a secure session, see [How to: Create a Security Context Token for a Secure Session](../../../../docs/framework/wcf/feature-details/how-to-create-a-security-context-token-for-a-secure-session.md).</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-one-of-the-system-provided-bindings"></a><span data-ttu-id="16ae3-111">使用其中一個系統提供的繫結來指定服務使用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="16ae3-111">To specify that a service uses secure sessions by using one of the system-provided bindings</span></span>  
  
-   <span data-ttu-id="16ae3-112">請將服務設定為使用支援訊息安全性之系統提供的繫結。</span><span class="sxs-lookup"><span data-stu-id="16ae3-112">Configure a service to use a system-provided binding that supports message security.</span></span>  
  
     <span data-ttu-id="16ae3-113">除了[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)繫結，當系統提供繫結會設定為自動使用訊息安全性時，WCF 會使用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="16ae3-113">With the exception of the [\<basicHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md) binding, when the system-provided bindings are configured to use message security, WCF automatically uses secure sessions.</span></span> <span data-ttu-id="16ae3-114">下表列出了支援訊息安全性之系統提供的繫結，以及訊息安全性是否為預設的安全性機制。</span><span class="sxs-lookup"><span data-stu-id="16ae3-114">The following table lists the system-provided bindings that support message security and whether message security is the default security mechanism.</span></span>  
  
    |<span data-ttu-id="16ae3-115">系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="16ae3-115">System-provided binding</span></span>|<span data-ttu-id="16ae3-116">組態項目</span><span class="sxs-lookup"><span data-stu-id="16ae3-116">Configuration element</span></span>|<span data-ttu-id="16ae3-117">訊息安全性預設為開啟</span><span class="sxs-lookup"><span data-stu-id="16ae3-117">Message security on by default</span></span>|  
    |------------------------------|---------------------------|------------------------------------|  
    |<xref:System.ServiceModel.BasicHttpBinding>|[<span data-ttu-id="16ae3-118">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="16ae3-118">\<basicHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|<span data-ttu-id="16ae3-119">否</span><span class="sxs-lookup"><span data-stu-id="16ae3-119">No</span></span>|  
    |<xref:System.ServiceModel.WSHttpBinding>|[<span data-ttu-id="16ae3-120">\<wsHttpBinding></span><span class="sxs-lookup"><span data-stu-id="16ae3-120">\<wsHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|<span data-ttu-id="16ae3-121">是</span><span class="sxs-lookup"><span data-stu-id="16ae3-121">Yes</span></span>|  
    |<xref:System.ServiceModel.WSDualHttpBinding>|[<span data-ttu-id="16ae3-122">\<wsDualHttpBinding></span><span class="sxs-lookup"><span data-stu-id="16ae3-122">\<wsDualHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|<span data-ttu-id="16ae3-123">是</span><span class="sxs-lookup"><span data-stu-id="16ae3-123">Yes</span></span>|  
    |<xref:System.ServiceModel.WSFederationHttpBinding>|[<span data-ttu-id="16ae3-124">\<wsFederationHttpBinding></span><span class="sxs-lookup"><span data-stu-id="16ae3-124">\<wsFederationHttpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|<span data-ttu-id="16ae3-125">是</span><span class="sxs-lookup"><span data-stu-id="16ae3-125">Yes</span></span>|  
    |<xref:System.ServiceModel.NetTcpBinding>|[<span data-ttu-id="16ae3-126">\<netTcpBinding></span><span class="sxs-lookup"><span data-stu-id="16ae3-126">\<netTcpBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|<span data-ttu-id="16ae3-127">否</span><span class="sxs-lookup"><span data-stu-id="16ae3-127">No</span></span>|  
    |<xref:System.ServiceModel.NetMsmqBinding>|[<span data-ttu-id="16ae3-128">\<netMsmqBinding></span><span class="sxs-lookup"><span data-stu-id="16ae3-128">\<netMsmqBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|<span data-ttu-id="16ae3-129">否</span><span class="sxs-lookup"><span data-stu-id="16ae3-129">No</span></span>|  
  
     <span data-ttu-id="16ae3-130">下列程式碼範例會使用組態來指定名為繫結`wsHttpBinding_Calculator`使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、 訊息安全性和安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="16ae3-130">The following code example uses configuration to specify a binding named `wsHttpBinding_Calculator` that uses the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions.</span></span>  
  
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
  
     <span data-ttu-id="16ae3-131">下列程式碼範例會指定[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)、 訊息安全性和安全工作階段用來保護`secureCalculator`服務。</span><span class="sxs-lookup"><span data-stu-id="16ae3-131">The following code example specifies that the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md), message security, and secure sessions are used to secure the `secureCalculator` service.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#1](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#1)]
     [!code-vb[c_CreateSecureSession#1](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#1)]  
  
    > [!NOTE]
    >  <span data-ttu-id="16ae3-132">您可以關閉安全工作階段的[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) splittunneling`establishSecurityContext`屬性設定為`false`。</span><span class="sxs-lookup"><span data-stu-id="16ae3-132">Secure sessions can be turned off for the [\<wsHttpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md) by setting the `establishSecurityContext` attribute to `false`.</span></span> <span data-ttu-id="16ae3-133">對於其他系統提供的繫結程序，安全工作階段只能藉由建立自訂繫結程序來關閉。</span><span class="sxs-lookup"><span data-stu-id="16ae3-133">For the other system-provided bindings, secure sessions can only be turned off by creating a custom binding.</span></span>  
  
### <a name="to-specify-that-a-service-uses-secure-sessions-by-using-a-custom-binding"></a><span data-ttu-id="16ae3-134">使用自訂繫結來指定服務使用安全工作階段</span><span class="sxs-lookup"><span data-stu-id="16ae3-134">To specify that a service uses secure sessions by using a custom binding</span></span>  
  
-   <span data-ttu-id="16ae3-135">請建立自訂繫結，指定 SOAP 訊息受到安全工作階段的保護。</span><span class="sxs-lookup"><span data-stu-id="16ae3-135">Create a custom binding that specifies that SOAP messages are protected by a secure session.</span></span>  
  
     <span data-ttu-id="16ae3-136">如需建立自訂繫結的詳細資訊，請參閱[How to:自訂系統提供的繫結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)。</span><span class="sxs-lookup"><span data-stu-id="16ae3-136">For more information about creating a custom binding, see [How to: Customize a System-Provided Binding](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md).</span></span>  
  
     <span data-ttu-id="16ae3-137">下列程式碼範例會使用組態來指定使用安全工作階段傳送訊息的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="16ae3-137">The following code example uses configuration to specify a custom binding that messages using a secure session.</span></span>  
  
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
  
     <span data-ttu-id="16ae3-138">下列程式碼範例建立了一個會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 驗證模式來啟動載入安全工作階段的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="16ae3-138">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
     [!code-csharp[c_CreateSecureSession#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createsecuresession/cs/secureservice.cs#2)]
     [!code-vb[c_CreateSecureSession#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createsecuresession/vb/secureservice.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="16ae3-139">另請參閱</span><span class="sxs-lookup"><span data-stu-id="16ae3-139">See also</span></span>

- [<span data-ttu-id="16ae3-140">WCF 繫結概觀</span><span class="sxs-lookup"><span data-stu-id="16ae3-140">WCF Bindings Overview</span></span>](../../../../docs/framework/wcf/bindings-overview.md)
