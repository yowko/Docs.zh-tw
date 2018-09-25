---
title: HOW TO：為安全工作階段建立安全性內容權杖
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 640676b6-c75a-4ff7-aea4-b1a1524d71b2
author: BrucePerlerMS
ms.openlocfilehash: 85954dd89bdb576b68d234a364a406a6e0d2145b
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/25/2018
ms.locfileid: "47079879"
---
# <a name="how-to-create-a-security-context-token-for-a-secure-session"></a><span data-ttu-id="2bfda-102">HOW TO：為安全工作階段建立安全性內容權杖</span><span class="sxs-lookup"><span data-stu-id="2bfda-102">How to: Create a Security Context Token for a Secure Session</span></span>
<span data-ttu-id="2bfda-103">在安全工作階段中使用具狀態的安全性內容權杖時，工作階段可以承受正在回收的服務。</span><span class="sxs-lookup"><span data-stu-id="2bfda-103">By using a stateful security context token (SCT) in a secure session, the session can withstand the service being recycled.</span></span> <span data-ttu-id="2bfda-104">例如，當安全工作階段使用無狀態的 SCT 而且重設了網際網路資訊服務 (IIS)，則與該服務相關聯的工作階段資料就會遺失。</span><span class="sxs-lookup"><span data-stu-id="2bfda-104">For instance, when a stateless SCT is used in a secure session and Internet Information Services (IIS) is reset, then the session data that is associated with the service is lost.</span></span> <span data-ttu-id="2bfda-105">這個工作階段資料包含 SCT 權杖快取。</span><span class="sxs-lookup"><span data-stu-id="2bfda-105">This session data includes an SCT token cache.</span></span> <span data-ttu-id="2bfda-106">因此，下一次當用戶端傳送的服務是無狀態的 SCT 時，便會傳回錯誤，因為無法擷取與 SCT 相關聯的金鑰。</span><span class="sxs-lookup"><span data-stu-id="2bfda-106">So, the next time a client sends the service a stateless SCT, an error is returned, because the key that is associated with the SCT cannot be retrieved.</span></span> <span data-ttu-id="2bfda-107">但是，如果使用具狀態的 SCT，則與 SCT 相關聯的金鑰就會包含在 SCT 中。</span><span class="sxs-lookup"><span data-stu-id="2bfda-107">If, however, a stateful SCT is used, then the key that is associated with the SCT is contained within the SCT.</span></span> <span data-ttu-id="2bfda-108">由於金鑰是包含在 SCT (因此也包含在訊息中)，安全工作階段就不會受到正在回收的服務所影響。</span><span class="sxs-lookup"><span data-stu-id="2bfda-108">Because the key is contained within the SCT and thus contained within the message, the secure session is not affected by the service being recycled.</span></span> <span data-ttu-id="2bfda-109">根據預設，Windows Communication Foundation (WCF) 會使用無狀態的 Sct 的安全工作階段中。</span><span class="sxs-lookup"><span data-stu-id="2bfda-109">By default, Windows Communication Foundation (WCF) uses stateless SCTs in a secure session.</span></span> <span data-ttu-id="2bfda-110">此主題將詳細說明如何在安全工作階段中使用具狀態的 SCT。</span><span class="sxs-lookup"><span data-stu-id="2bfda-110">This topic details how to use stateful SCTs in a secure session.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bfda-111">您無法在安全工作階段 (與衍生自 <xref:System.ServiceModel.Channels.IDuplexChannel> 的合約相關) 中使用可設定狀態的 SCT。</span><span class="sxs-lookup"><span data-stu-id="2bfda-111">Stateful SCTs cannot be used in a secure session that involves a contract that derives from <xref:System.ServiceModel.Channels.IDuplexChannel>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bfda-112">對於在安全工作階段中使用具狀態之 SCT 的應用程式來說，服務的執行緒識別必須是具有相關使用者設定檔的使用者帳戶。</span><span class="sxs-lookup"><span data-stu-id="2bfda-112">For applications that use stateful SCTs in a secure session, the thread identity for the service must be a user account that has an associated user profile.</span></span> <span data-ttu-id="2bfda-113">如果服務透過不具備使用者設定檔的帳戶來執行，例如 `Local Service`，可能會擲回例外狀況。</span><span class="sxs-lookup"><span data-stu-id="2bfda-113">When the service is run under an account that does not have a user profile, such as `Local Service`, an exception may be thrown.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="2bfda-114">當 Windows XP 需要模擬時，請使用不包含可設定狀態之 SCT 的安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="2bfda-114">When impersonation is required on Windows XP, use a secure session without a stateful SCT.</span></span> <span data-ttu-id="2bfda-115">當可設定狀態的 SCT 與模擬一起使用時，就會擲回 <xref:System.InvalidOperationException>。</span><span class="sxs-lookup"><span data-stu-id="2bfda-115">When stateful SCTs are used with impersonation, an <xref:System.InvalidOperationException> is thrown.</span></span> <span data-ttu-id="2bfda-116">如需詳細資訊，請參閱 <<c0> [ 不支援的案例](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfda-116">For more information, see [Unsupported Scenarios](../../../../docs/framework/wcf/feature-details/unsupported-scenarios.md).</span></span>  
  
### <a name="to-use-stateful-scts-in-a-secure-session"></a><span data-ttu-id="2bfda-117">若要在安全工作階段中使用具狀態的 SCT</span><span class="sxs-lookup"><span data-stu-id="2bfda-117">To use stateful SCTs in a secure session</span></span>  
  
-   <span data-ttu-id="2bfda-118">建立自訂繫結，以指定 SOAP 訊息由使用具狀態之 SCT 的安全工作階段來保護。</span><span class="sxs-lookup"><span data-stu-id="2bfda-118">Create a custom binding that specifies that SOAP messages are protected by a secure session that uses a stateful SCT.</span></span>  
  
    1.  <span data-ttu-id="2bfda-119">定義自訂繫結，加上[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)至服務組態檔。</span><span class="sxs-lookup"><span data-stu-id="2bfda-119">Define a custom binding, by adding a [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md) to the configuration file for the service.</span></span>  
  
        ```xml  
        <customBinding>  
        ```  
  
    2.  <span data-ttu-id="2bfda-120">新增[\<繫結 >](../../../../docs/framework/misc/binding.md)子項目[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfda-120">Add a [\<binding>](../../../../docs/framework/misc/binding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="2bfda-121">您可以在組態檔中將 `name` 屬性設為唯一的名稱來指定繫結名稱。</span><span class="sxs-lookup"><span data-stu-id="2bfda-121">Specify a binding name by setting the `name` attribute to a unique name within the configuration file.</span></span>  
  
        ```xml  
        <binding name="StatefulSCTSecureSession">  
        ```  
  
    3.  <span data-ttu-id="2bfda-122">指定的驗證模式，藉由新增這項服務的來回傳送的訊息[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)子項目[ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfda-122">Specify the authentication mode for messages sent to and from this service by adding a [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md) child element to the [\<customBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md).</span></span>  
  
         <span data-ttu-id="2bfda-123">您可以將 `authenticationMode` 屬性設為 `SecureConversation`，指定使用安全工作階段。</span><span class="sxs-lookup"><span data-stu-id="2bfda-123">Specify that a secure session is used by setting the `authenticationMode` attribute to `SecureConversation`.</span></span> <span data-ttu-id="2bfda-124">您可以將 `requireSecurityContextCancellation` 屬性設為 `false`，指定使用可設定狀態的 SCT。</span><span class="sxs-lookup"><span data-stu-id="2bfda-124">Specify that stateful SCTs are used by setting the `requireSecurityContextCancellation` attribute to `false`.</span></span>  
  
        ```xml  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
        ```  
  
    4.  <span data-ttu-id="2bfda-125">指定藉由新增建立安全工作階段時要如何驗證用戶端[ \<secureConversationBootstrap >](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md)子項目[\<安全性 >](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfda-125">Specify how the client is authenticated while the secure session is established by adding a [\<secureConversationBootstrap>](../../../../docs/framework/configure-apps/file-schema/wcf/secureconversationbootstrap.md) child element to the [\<security>](../../../../docs/framework/configure-apps/file-schema/wcf/security-of-custombinding.md).</span></span>  
  
         <span data-ttu-id="2bfda-126">您可以設定 `authenticationMode` 屬性，指定用戶端的驗證方式。</span><span class="sxs-lookup"><span data-stu-id="2bfda-126">Specify how the client is authenticated by setting the `authenticationMode` attribute.</span></span>  
  
        ```xml  
        <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        ```  
  
    5.  <span data-ttu-id="2bfda-127">指定的訊息編碼，藉由新增編碼項目，例如[ \<textMessageEncoding >](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfda-127">Specify the message encoding by adding an encoding element, such as [\<textMessageEncoding>](../../../../docs/framework/configure-apps/file-schema/wcf/textmessageencoding.md).</span></span>  
  
        ```xml  
        <textMessageEncoding />  
        ```  
  
    6.  <span data-ttu-id="2bfda-128">指定傳輸方式新增傳輸項目，例如[ \<httpTransport >](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md)。</span><span class="sxs-lookup"><span data-stu-id="2bfda-128">Specify the transport by adding a transport element, such as the [\<httpTransport>](../../../../docs/framework/configure-apps/file-schema/wcf/httptransport.md).</span></span>  
  
        ```xml  
        <httpTransport />  
        ```  
  
     <span data-ttu-id="2bfda-129">下列程式碼範例使用組態來指定安全工作階段中，訊息可以搭配具狀態的 SCT 使用的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="2bfda-129">The following code example uses configuration to specify a custom binding that messages can use with stateful SCTs in a secure session.</span></span>  
  
    ```xml  
    <customBinding>  
      <binding name="StatefulSCTSecureSession">  
        <security authenticationMode="SecureConversation"  
                  requireSecurityContextCancellation="false">  
          <secureConversationBootstrap authenticationMode="UserNameForCertificate" />  
        </security>  
        <textMessageEncoding />  
        <httpTransport />  
      </binding>  
    </customBinding>  
    ```  
  
## <a name="example"></a><span data-ttu-id="2bfda-130">範例</span><span class="sxs-lookup"><span data-stu-id="2bfda-130">Example</span></span>  
 <span data-ttu-id="2bfda-131">下列程式碼範例建立了一個會使用 <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> 驗證模式來啟動載入安全工作階段的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="2bfda-131">The following code example creates a custom binding that uses the <xref:System.ServiceModel.Configuration.AuthenticationMode.MutualCertificate> authentication mode to bootstrap a secure session.</span></span>  
  
 [!code-csharp[c_CreateStatefulSCT#2](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_createstatefulsct/cs/secureservice.cs#2)]
 [!code-vb[c_CreateStatefulSCT#2](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_createstatefulsct/vb/secureservice.vb#2)]  
  
 <span data-ttu-id="2bfda-132">使用 Windows 驗證時，搭配具狀態的 SCT，WCF 不會填入<xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A>屬性使用實際呼叫者的身分識別，但改為將屬性設定為匿名。</span><span class="sxs-lookup"><span data-stu-id="2bfda-132">When Windows authentication is used in combination with a stateful SCT, WCF does not populate the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property with the actual caller's identity but instead sets the property to anonymous.</span></span> <span data-ttu-id="2bfda-133">WCF 安全性必須重新建立來自傳入 SCT 的每個要求的服務安全性內容的內容，因為伺服器不會不追蹤的安全性工作階段，在記憶體中。</span><span class="sxs-lookup"><span data-stu-id="2bfda-133">Because WCF security must re-create the content of the service security context for every request from the incoming SCT, the server does not keep track of the security session in the memory.</span></span> <span data-ttu-id="2bfda-134">由於您不可能將 <xref:System.Security.Principal.WindowsIdentity> 執行個體序列化為 SCT，<xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> 屬性將傳回匿名身分識別。</span><span class="sxs-lookup"><span data-stu-id="2bfda-134">Because it is impossible to serialize the <xref:System.Security.Principal.WindowsIdentity> instance into the SCT, the <xref:System.ServiceModel.ServiceSecurityContext.WindowsIdentity%2A> property returns an anonymous identity.</span></span>  
  
 <span data-ttu-id="2bfda-135">下列組態將示範此行為。</span><span class="sxs-lookup"><span data-stu-id="2bfda-135">The following configuration exhibits this behavior.</span></span>  
  
```xml  
<customBinding>  
  <binding name="Cancellation">  
       <textMessageEncoding />  
        <security   
            requireSecurityContextCancellation="false">  
              <secureConversationBootstrap />  
      </security>  
    <httpTransport />  
  </binding>  
</customBinding>  
```  
  
## <a name="see-also"></a><span data-ttu-id="2bfda-136">另請參閱</span><span class="sxs-lookup"><span data-stu-id="2bfda-136">See Also</span></span>  
 [<span data-ttu-id="2bfda-137">\<customBinding></span><span class="sxs-lookup"><span data-stu-id="2bfda-137">\<customBinding></span></span>](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)
