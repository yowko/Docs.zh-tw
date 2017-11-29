---
title: "HOW TO：使用傳輸安全性和訊息認證"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords: TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: "11"
author: BrucePerlerMS
ms.author: bruceper
manager: mbaldwin
ms.openlocfilehash: e29ae3a0374f6ee027180835629eacceaa928d2f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="68583-102">HOW TO：使用傳輸安全性和訊息認證</span><span class="sxs-lookup"><span data-stu-id="68583-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="68583-103">同時使用傳輸與訊息認證來保護服務的安全時，需要在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中同時運用最佳的傳輸與訊息安全性模式。</span><span class="sxs-lookup"><span data-stu-id="68583-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)].</span></span> <span data-ttu-id="68583-104">簡單地說，傳輸層安全性可提供完整性與機密性，而訊息層安全性則提供各種在嚴格的傳輸安全性機制中不可能提供的認證。</span><span class="sxs-lookup"><span data-stu-id="68583-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="68583-105">本主題將說明使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 繫結，以訊息認證來實作傳輸時的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="68583-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> [!INCLUDE[crabout](../../../../includes/crabout-md.md)]<span data-ttu-id="68583-106">設定安全性模式，請參閱[How to： 設定安全性模式](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="68583-106"> setting the security mode, see [How to: Set the Security Mode](../../../../docs/framework/wcf/how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="68583-107">當您將安全性模式設為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。</span><span class="sxs-lookup"><span data-stu-id="68583-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="68583-108">對 HTTP 來說，此機制為 Secure Sockets Layer (SSL) over HTTP (HTTPS)；對 TCP 來說，此機制是 SSL over TCP 或 Windows 安全性。</span><span class="sxs-lookup"><span data-stu-id="68583-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="68583-109">如果傳輸機制為 HTTP (使用 <xref:System.ServiceModel.WSHttpBinding>)，則 SSL over HTTP 會提供傳輸層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="68583-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="68583-110">在此情況下，您必須設定電腦使用繫結至連接埠的 SSL 憑證來裝載服務 (如本主題稍後所示)。</span><span class="sxs-lookup"><span data-stu-id="68583-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="68583-111">如果傳輸機制為 TCP (使用 <xref:System.ServiceModel.NetTcpBinding>)，則預設會提供的傳輸層安全性便是 Windows 安全性或 SSL over TCP。</span><span class="sxs-lookup"><span data-stu-id="68583-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="68583-112">一旦使用 SSL over TCP，您必須使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法來指定憑證 (如本主題稍後所示)。</span><span class="sxs-lookup"><span data-stu-id="68583-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="68583-113">若要使用 WSHttpBinding 搭配憑證來獲得傳輸安全性 (透過程式碼)</span><span class="sxs-lookup"><span data-stu-id="68583-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="68583-114">請使用 HttpCfg.exe 工具，將 SSL 憑證繫結至電腦的連接埠。</span><span class="sxs-lookup"><span data-stu-id="68583-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)]<span data-ttu-id="68583-115">[How to： 使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="68583-115"> [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2.  <span data-ttu-id="68583-116">建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="68583-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3.  <span data-ttu-id="68583-117">將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="68583-118">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [選取認證類型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)。)下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="68583-118">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [Selecting a Credential Type](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="68583-119">使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="68583-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="68583-120">請注意，位址必須使用 "HTTPS" 配置，而且必須包含電腦的實際名稱，以及 SSL 憑證所繫結的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="68583-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="68583-121">(另外，您也可以在組態中設定基底位址)。</span><span class="sxs-lookup"><span data-stu-id="68583-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="68583-122">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="68583-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6.  <span data-ttu-id="68583-123">如下列程式碼所示，建立 <xref:System.ServiceModel.ServiceHost> 的執行個體並呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="68583-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="68583-124">若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性 (透過程式碼)</span><span class="sxs-lookup"><span data-stu-id="68583-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="68583-125">建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="68583-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="68583-126">將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="68583-127">下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="68583-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3.  <span data-ttu-id="68583-128">使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="68583-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="68583-129">請注意，位址必須使用 "net.tcp" 配置。</span><span class="sxs-lookup"><span data-stu-id="68583-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="68583-130">(另外，您也可以在組態中設定基底位址)。</span><span class="sxs-lookup"><span data-stu-id="68583-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4.  <span data-ttu-id="68583-131">建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68583-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5.  <span data-ttu-id="68583-132">使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，明確設定服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="68583-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6.  <span data-ttu-id="68583-133">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="68583-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7.  <span data-ttu-id="68583-134">呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="68583-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="68583-135">若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性 (透過程式碼)</span><span class="sxs-lookup"><span data-stu-id="68583-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1.  <span data-ttu-id="68583-136">建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="68583-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2.  <span data-ttu-id="68583-137">將 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 設定為 <xref:System.ServiceModel.TcpClientCredentialType.Windows>，藉此將傳輸安全性設定為使用 Windows </span><span class="sxs-lookup"><span data-stu-id="68583-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="68583-138">(請注意，此設定為預設值)。</span><span class="sxs-lookup"><span data-stu-id="68583-138">(Note that this is the default.)</span></span>  
  
3.  <span data-ttu-id="68583-139">將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="68583-140">下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="68583-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4.  <span data-ttu-id="68583-141">使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="68583-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="68583-142">請注意，位址必須使用 "net.tcp" 配置。</span><span class="sxs-lookup"><span data-stu-id="68583-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="68583-143">(另外，您也可以在組態中設定基底位址)。</span><span class="sxs-lookup"><span data-stu-id="68583-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5.  <span data-ttu-id="68583-144">建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="68583-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6.  <span data-ttu-id="68583-145">使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，明確設定服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="68583-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7.  <span data-ttu-id="68583-146">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="68583-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8.  <span data-ttu-id="68583-147">呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="68583-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="68583-148">使用組態</span><span class="sxs-lookup"><span data-stu-id="68583-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="68583-149">若要使用 WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="68583-149">To use the WSHttpBinding</span></span>  
  
1.  <span data-ttu-id="68583-150">使用繫結至連接埠的 SSL 憑證來設定電腦 </span><span class="sxs-lookup"><span data-stu-id="68583-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="68583-151">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [How to： 使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md))。</span><span class="sxs-lookup"><span data-stu-id="68583-151">([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)] [How to: Configure a Port with an SSL Certificate](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="68583-152">您不需要設定 <`transport`> 與這個組態項目值。</span><span class="sxs-lookup"><span data-stu-id="68583-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2.  <span data-ttu-id="68583-153">指定訊息層級安全性的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="68583-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="68583-154">下列範例會設定`clientCredentialType`屬性 <`message`> 項目`UserName`。</span><span class="sxs-lookup"><span data-stu-id="68583-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="68583-155">若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="68583-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1.  <span data-ttu-id="68583-156">如果要使用 SSL over TCP，您必須在 `<behaviors>` 項目中明確指定憑證。</span><span class="sxs-lookup"><span data-stu-id="68583-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="68583-157">下列範例會在預設的存放區位置中 (本機電腦與個人存放區)，按照憑證簽發者指定憑證。</span><span class="sxs-lookup"><span data-stu-id="68583-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
    ```xml  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  <span data-ttu-id="68583-158">新增[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)至繫結區段</span><span class="sxs-lookup"><span data-stu-id="68583-158">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3.  <span data-ttu-id="68583-159">新增繫結項目，然後將 `name` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4.  <span data-ttu-id="68583-160">新增 <`security`> 項目，並設定`mode`屬性`TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="68583-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5.  <span data-ttu-id="68583-161">新增 <`message>`項目，並設定`clientCredentialType`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="68583-162">若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="68583-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1.  <span data-ttu-id="68583-163">新增[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)繫結區段</span><span class="sxs-lookup"><span data-stu-id="68583-163">Add a [\<netTcpBinding>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2.  <span data-ttu-id="68583-164">新增 <`binding`> 項目並設定`name`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3.  <span data-ttu-id="68583-165">新增 <`security`> 項目，並設定`mode`屬性`TransportWithMessageCredential`。</span><span class="sxs-lookup"><span data-stu-id="68583-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4.  <span data-ttu-id="68583-166">新增 <`transport`> 項目並設定`clientCredentialType`屬性`Windows`。</span><span class="sxs-lookup"><span data-stu-id="68583-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5.  <span data-ttu-id="68583-167">新增 <`message`> 項目並設定`clientCredentialType`屬性設為適當值。</span><span class="sxs-lookup"><span data-stu-id="68583-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="68583-168">下列程式碼會設定憑證的值。</span><span class="sxs-lookup"><span data-stu-id="68583-168">The following code sets the value to a certificate.</span></span>  
  
    ```xml  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
## <a name="see-also"></a><span data-ttu-id="68583-169">另請參閱</span><span class="sxs-lookup"><span data-stu-id="68583-169">See Also</span></span>  
 [<span data-ttu-id="68583-170">如何：設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="68583-170">How to: Set the Security Mode</span></span>](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)  
 [<span data-ttu-id="68583-171">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="68583-171">Securing Services</span></span>](../../../../docs/framework/wcf/securing-services.md)  
 [<span data-ttu-id="68583-172">保護服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="68583-172">Securing Services and Clients</span></span>](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
