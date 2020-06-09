---
title: HOW TO：使用傳輸安全性和訊息認證
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f49c0eb46141081b91100a5ae1869cbcf556e353
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/09/2020
ms.locfileid: "84579380"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a><span data-ttu-id="469ba-102">HOW TO：使用傳輸安全性和訊息認證</span><span class="sxs-lookup"><span data-stu-id="469ba-102">How to: Use Transport Security and Message Credentials</span></span>
<span data-ttu-id="469ba-103">使用傳輸和訊息認證來保護服務的安全，會在 Windows Communication Foundation （WCF）中使用傳輸和訊息安全性模式的最佳選擇。</span><span class="sxs-lookup"><span data-stu-id="469ba-103">Securing a service with both transport and message credentials uses the best of both Transport and Message security modes in Windows Communication Foundation (WCF).</span></span> <span data-ttu-id="469ba-104">簡單地說，傳輸層安全性可提供完整性與機密性，而訊息層安全性則提供各種在嚴格的傳輸安全性機制中不可能提供的認證。</span><span class="sxs-lookup"><span data-stu-id="469ba-104">In sum, transport-layer security provides integrity and confidentiality, while message-layer security provides a variety of credentials that are not possible with strict transport security mechanisms.</span></span> <span data-ttu-id="469ba-105">本主題將說明使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 繫結，以訊息認證來實作傳輸時的基本步驟。</span><span class="sxs-lookup"><span data-stu-id="469ba-105">This topic shows the basic steps for implementing transport with message credentials using the <xref:System.ServiceModel.WSHttpBinding> and <xref:System.ServiceModel.NetTcpBinding> bindings.</span></span> <span data-ttu-id="469ba-106">如需設定安全性模式的詳細資訊，請參閱[如何：設定安全性模式](../how-to-set-the-security-mode.md)。</span><span class="sxs-lookup"><span data-stu-id="469ba-106">For more information about setting the security mode, see [How to: Set the Security Mode](../how-to-set-the-security-mode.md).</span></span>  
  
 <span data-ttu-id="469ba-107">當您將安全性模式設為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。</span><span class="sxs-lookup"><span data-stu-id="469ba-107">When setting the security mode to `TransportWithMessageCredential`, the transport determines the actual mechanism that provides the transport-level security.</span></span> <span data-ttu-id="469ba-108">對 HTTP 來說，此機制為 Secure Sockets Layer (SSL) over HTTP (HTTPS)；對 TCP 來說，此機制是 SSL over TCP 或 Windows 安全性。</span><span class="sxs-lookup"><span data-stu-id="469ba-108">For HTTP, the mechanism is Secure Sockets Layer (SSL) over HTTP (HTTPS); for TCP, it is SSL over TCP or Windows.</span></span>  
  
 <span data-ttu-id="469ba-109">如果傳輸機制為 HTTP (使用 <xref:System.ServiceModel.WSHttpBinding>)，則 SSL over HTTP 會提供傳輸層級的安全性。</span><span class="sxs-lookup"><span data-stu-id="469ba-109">If the transport is HTTP (using the <xref:System.ServiceModel.WSHttpBinding>), SSL over HTTP provides the transport-level security.</span></span> <span data-ttu-id="469ba-110">在此情況下，您必須設定電腦使用繫結至連接埠的 SSL 憑證來裝載服務 (如本主題稍後所示)。</span><span class="sxs-lookup"><span data-stu-id="469ba-110">In that case, you must configure the computer hosting the service with an SSL certificate bound to a port, as shown later in this topic.</span></span>  
  
 <span data-ttu-id="469ba-111">如果傳輸機制為 TCP (使用 <xref:System.ServiceModel.NetTcpBinding>)，則預設會提供的傳輸層安全性便是 Windows 安全性或 SSL over TCP。</span><span class="sxs-lookup"><span data-stu-id="469ba-111">If the transport is TCP (using the <xref:System.ServiceModel.NetTcpBinding>), by default the transport-level security provided is Windows security, or SSL over TCP.</span></span> <span data-ttu-id="469ba-112">一旦使用 SSL over TCP，您必須使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法來指定憑證 (如本主題稍後所示)。</span><span class="sxs-lookup"><span data-stu-id="469ba-112">When using SSL over TCP, you must specify the certificate using the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method, as shown later in this topic.</span></span>  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="469ba-113">若要使用 WSHttpBinding 搭配憑證來獲得傳輸安全性 (透過程式碼)</span><span class="sxs-lookup"><span data-stu-id="469ba-113">To use the WSHttpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="469ba-114">請使用 HttpCfg.exe 工具，將 SSL 憑證繫結至電腦的連接埠。</span><span class="sxs-lookup"><span data-stu-id="469ba-114">Use the HttpCfg.exe tool to bind an SSL certificate to a port on the machine.</span></span> <span data-ttu-id="469ba-115">如需詳細資訊，請參閱[如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)。</span><span class="sxs-lookup"><span data-stu-id="469ba-115">For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md).</span></span>  
  
2. <span data-ttu-id="469ba-116">建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="469ba-116">Create an instance of the <xref:System.ServiceModel.WSHttpBinding> class and set the <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
3. <span data-ttu-id="469ba-117">將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="469ba-117">Set the <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> property to an appropriate value.</span></span> <span data-ttu-id="469ba-118">（如需詳細資訊，請參閱[選取認證類型](selecting-a-credential-type.md)。）下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="469ba-118">(For more information, see [Selecting a Credential Type](selecting-a-credential-type.md).) The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="469ba-119">使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="469ba-119">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="469ba-120">請注意，位址必須使用 "HTTPS" 配置，而且必須包含電腦的實際名稱，以及 SSL 憑證所繫結的連接埠號碼。</span><span class="sxs-lookup"><span data-stu-id="469ba-120">Note that the address must use the "HTTPS" scheme and must contain the actual name of the machine and the port number that the SSL certificate is bound to.</span></span> <span data-ttu-id="469ba-121">(另外，您也可以在組態中設定基底位址)。</span><span class="sxs-lookup"><span data-stu-id="469ba-121">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="469ba-122">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="469ba-122">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
6. <span data-ttu-id="469ba-123">如下列程式碼所示，建立 <xref:System.ServiceModel.ServiceHost> 的執行個體並呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。</span><span class="sxs-lookup"><span data-stu-id="469ba-123">Create the instance of the <xref:System.ServiceModel.ServiceHost> and call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a><span data-ttu-id="469ba-124">若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性 (透過程式碼)</span><span class="sxs-lookup"><span data-stu-id="469ba-124">To use the NetTcpBinding with a certificate for transport security (in code)</span></span>  
  
1. <span data-ttu-id="469ba-125">建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="469ba-125">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="469ba-126">將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="469ba-126">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="469ba-127">下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="469ba-127">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
3. <span data-ttu-id="469ba-128">使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="469ba-128">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="469ba-129">請注意，位址必須使用 "net.tcp" 配置。</span><span class="sxs-lookup"><span data-stu-id="469ba-129">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="469ba-130">(另外，您也可以在組態中設定基底位址)。</span><span class="sxs-lookup"><span data-stu-id="469ba-130">(Alternatively, you can set the base address in configuration.)</span></span>  
  
4. <span data-ttu-id="469ba-131">建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="469ba-131">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
5. <span data-ttu-id="469ba-132">使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，明確設定服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="469ba-132">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
6. <span data-ttu-id="469ba-133">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="469ba-133">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
7. <span data-ttu-id="469ba-134">呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="469ba-134">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a><span data-ttu-id="469ba-135">若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性 (透過程式碼)</span><span class="sxs-lookup"><span data-stu-id="469ba-135">To use the NetTcpBinding with Windows for transport security (in code)</span></span>  
  
1. <span data-ttu-id="469ba-136">建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。</span><span class="sxs-lookup"><span data-stu-id="469ba-136">Create an instance of the <xref:System.ServiceModel.NetTcpBinding> class and set the <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> property to <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>.</span></span>  
  
2. <span data-ttu-id="469ba-137">將 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 設定為 <xref:System.ServiceModel.TcpClientCredentialType.Windows>，藉此將傳輸安全性設定為使用 Windows </span><span class="sxs-lookup"><span data-stu-id="469ba-137">Set the transport security to use Windows by setting the <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> to <xref:System.ServiceModel.TcpClientCredentialType.Windows>.</span></span> <span data-ttu-id="469ba-138">(請注意，此設定為預設值)。</span><span class="sxs-lookup"><span data-stu-id="469ba-138">(Note that this is the default.)</span></span>  
  
3. <span data-ttu-id="469ba-139">將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="469ba-139">Set the <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> to an appropriate value.</span></span> <span data-ttu-id="469ba-140">下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。</span><span class="sxs-lookup"><span data-stu-id="469ba-140">The following code uses the <xref:System.ServiceModel.MessageCredentialType.Certificate> value.</span></span>  
  
4. <span data-ttu-id="469ba-141">使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體</span><span class="sxs-lookup"><span data-stu-id="469ba-141">Create an instance of the <xref:System.Uri> class with an appropriate base address.</span></span> <span data-ttu-id="469ba-142">請注意，位址必須使用 "net.tcp" 配置。</span><span class="sxs-lookup"><span data-stu-id="469ba-142">Note that the address must use the "net.tcp" scheme.</span></span> <span data-ttu-id="469ba-143">(另外，您也可以在組態中設定基底位址)。</span><span class="sxs-lookup"><span data-stu-id="469ba-143">(Alternatively, you can set the base address in configuration.)</span></span>  
  
5. <span data-ttu-id="469ba-144">建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。</span><span class="sxs-lookup"><span data-stu-id="469ba-144">Create the instance of the <xref:System.ServiceModel.ServiceHost> class.</span></span>  
  
6. <span data-ttu-id="469ba-145">使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，明確設定服務的 X.509 憑證。</span><span class="sxs-lookup"><span data-stu-id="469ba-145">Use the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> method of the <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> class to explicitly set the X.509 certificate for the service.</span></span>  
  
7. <span data-ttu-id="469ba-146">使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。</span><span class="sxs-lookup"><span data-stu-id="469ba-146">Add a service endpoint using the <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> method.</span></span>  
  
8. <span data-ttu-id="469ba-147">呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="469ba-147">Call the <xref:System.ServiceModel.ICommunicationObject.Open%2A> method, as shown in the following code.</span></span>  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a><span data-ttu-id="469ba-148">使用組態</span><span class="sxs-lookup"><span data-stu-id="469ba-148">Using Configuration</span></span>  
  
#### <a name="to-use-the-wshttpbinding"></a><span data-ttu-id="469ba-149">若要使用 WSHttpBinding</span><span class="sxs-lookup"><span data-stu-id="469ba-149">To use the WSHttpBinding</span></span>  
  
1. <span data-ttu-id="469ba-150">使用繫結至連接埠的 SSL 憑證來設定電腦 </span><span class="sxs-lookup"><span data-stu-id="469ba-150">Configure the computer with an SSL certificate bound to a port.</span></span> <span data-ttu-id="469ba-151">（如需詳細資訊，請參閱[如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)）。</span><span class="sxs-lookup"><span data-stu-id="469ba-151">(For more information, see [How to: Configure a Port with an SSL Certificate](how-to-configure-a-port-with-an-ssl-certificate.md)).</span></span> <span data-ttu-id="469ba-152">您不需要使用此設定來設定 <`transport`> 元素值。</span><span class="sxs-lookup"><span data-stu-id="469ba-152">You do not need to set a <`transport`> element value with this configuration.</span></span>  
  
2. <span data-ttu-id="469ba-153">指定訊息層級安全性的用戶端認證類型。</span><span class="sxs-lookup"><span data-stu-id="469ba-153">Specify the client credential type for the message-level security.</span></span> <span data-ttu-id="469ba-154">下列範例會將 `clientCredentialType` <> 元素的屬性設定 `message` 為 `UserName` 。</span><span class="sxs-lookup"><span data-stu-id="469ba-154">The following example sets the `clientCredentialType` attribute of the <`message`> element to `UserName`.</span></span>  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a><span data-ttu-id="469ba-155">若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="469ba-155">To use the NetTcpBinding with a certificate for transport security</span></span>  
  
1. <span data-ttu-id="469ba-156">如果要使用 SSL over TCP，您必須在 `<behaviors>` 項目中明確指定憑證。</span><span class="sxs-lookup"><span data-stu-id="469ba-156">For SSL over TCP, you must explicitly specify the certificate in the `<behaviors>` element.</span></span> <span data-ttu-id="469ba-157">下列範例會在預設的存放區位置中 (本機電腦與個人存放區)，按照憑證簽發者指定憑證。</span><span class="sxs-lookup"><span data-stu-id="469ba-157">The following example specifies a certificate by its issuer in the default store location (local machine and personal stores).</span></span>  
  
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
  
2. <span data-ttu-id="469ba-158">將加入 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 至系結區段</span><span class="sxs-lookup"><span data-stu-id="469ba-158">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section</span></span>  
  
3. <span data-ttu-id="469ba-159">新增繫結項目，然後將 `name` 屬性設定為適當值。</span><span class="sxs-lookup"><span data-stu-id="469ba-159">Add a binding element, and set the `name` attribute to an appropriate value.</span></span>  
  
4. <span data-ttu-id="469ba-160">新增 <`security`> 元素，並將屬性設定 `mode` 為 `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="469ba-160">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
5. <span data-ttu-id="469ba-161">新增 <`message>` 元素，並將屬性設定 `clientCredentialType` 為適當的值。</span><span class="sxs-lookup"><span data-stu-id="469ba-161">Add a <`message>` element, and set the `clientCredentialType` attribute to an appropriate value.</span></span>  
  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a><span data-ttu-id="469ba-162">若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性</span><span class="sxs-lookup"><span data-stu-id="469ba-162">To use the NetTcpBinding with Windows for transport security</span></span>  
  
1. <span data-ttu-id="469ba-163">將加入 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 至系結區段，</span><span class="sxs-lookup"><span data-stu-id="469ba-163">Add a [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) to the bindings section,</span></span>  
  
2. <span data-ttu-id="469ba-164">新增 <`binding`> 元素，並將 `name` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="469ba-164">Add a <`binding`> element and set the `name` attribute to an appropriate value.</span></span>  
  
3. <span data-ttu-id="469ba-165">新增 <`security`> 元素，並將屬性設定 `mode` 為 `TransportWithMessageCredential` 。</span><span class="sxs-lookup"><span data-stu-id="469ba-165">Add a <`security`> element, and set the `mode` attribute to `TransportWithMessageCredential`.</span></span>  
  
4. <span data-ttu-id="469ba-166">新增 <`transport`> 元素，並將 `clientCredentialType` 屬性設定為 `Windows` 。</span><span class="sxs-lookup"><span data-stu-id="469ba-166">Add a <`transport`> element and set the `clientCredentialType` attribute to `Windows`.</span></span>  
  
5. <span data-ttu-id="469ba-167">新增 <`message`> 元素，並將 `clientCredentialType` 屬性設定為適當的值。</span><span class="sxs-lookup"><span data-stu-id="469ba-167">Add a <`message`> element and set the `clientCredentialType` attribute to an appropriate value.</span></span> <span data-ttu-id="469ba-168">下列程式碼會設定憑證的值。</span><span class="sxs-lookup"><span data-stu-id="469ba-168">The following code sets the value to a certificate.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="469ba-169">請參閱</span><span class="sxs-lookup"><span data-stu-id="469ba-169">See also</span></span>

- [<span data-ttu-id="469ba-170">如何：設定安全性模式</span><span class="sxs-lookup"><span data-stu-id="469ba-170">How to: Set the Security Mode</span></span>](../how-to-set-the-security-mode.md)
- [<span data-ttu-id="469ba-171">保護服務安全</span><span class="sxs-lookup"><span data-stu-id="469ba-171">Securing Services</span></span>](../securing-services.md)
- [<span data-ttu-id="469ba-172">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="469ba-172">Securing Services and Clients</span></span>](securing-services-and-clients.md)
