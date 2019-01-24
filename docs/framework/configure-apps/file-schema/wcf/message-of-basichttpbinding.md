---
title: '&lt;basicHttpBinding&gt; 的 &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: f4f50f0cf3010259677af2c8675cb2551c29ae42
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54497051"
---
# <a name="ltmessagegt-of-ltbasichttpbindinggt"></a><span data-ttu-id="d4b9a-102">&lt;basicHttpBinding&gt; 的 &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="d4b9a-102">&lt;message&gt; of &lt;basicHttpBinding&gt;</span></span>
<span data-ttu-id="d4b9a-103">定義訊息層級安全性的設定[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="d4b9a-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="d4b9a-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="d4b9a-105">\<bindings></span><span class="sxs-lookup"><span data-stu-id="d4b9a-105">\<bindings></span></span>  
<span data-ttu-id="d4b9a-106">\<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="d4b9a-106">\<basicHttpBinding></span></span>  
<span data-ttu-id="d4b9a-107">\<binding></span><span class="sxs-lookup"><span data-stu-id="d4b9a-107">\<binding></span></span>  
<span data-ttu-id="d4b9a-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="d4b9a-108">\<security></span></span>  
<span data-ttu-id="d4b9a-109">\<message></span><span class="sxs-lookup"><span data-stu-id="d4b9a-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d4b9a-110">語法</span><span class="sxs-lookup"><span data-stu-id="d4b9a-110">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="d4b9a-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="d4b9a-111">Attributes and Elements</span></span>  
 <span data-ttu-id="d4b9a-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="d4b9a-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="d4b9a-113">屬性</span><span class="sxs-lookup"><span data-stu-id="d4b9a-113">Attributes</span></span>  
  
|<span data-ttu-id="d4b9a-114">屬性</span><span class="sxs-lookup"><span data-stu-id="d4b9a-114">Attribute</span></span>|<span data-ttu-id="d4b9a-115">描述</span><span class="sxs-lookup"><span data-stu-id="d4b9a-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="d4b9a-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="d4b9a-116">algorithmSuite</span></span>|<span data-ttu-id="d4b9a-117">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="d4b9a-118">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>，它會指定演算法和金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="d4b9a-119">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="d4b9a-120">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="d4b9a-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="d4b9a-121">clientCredentialType</span></span>|<span data-ttu-id="d4b9a-122">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="d4b9a-123">預設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="d4b9a-124">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="d4b9a-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="d4b9a-125">值</span><span class="sxs-lookup"><span data-stu-id="d4b9a-125">Value</span></span>|<span data-ttu-id="d4b9a-126">描述</span><span class="sxs-lookup"><span data-stu-id="d4b9a-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="d4b9a-127">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="d4b9a-127">UserName</span></span>|<span data-ttu-id="d4b9a-128">-需要使用 UserName 認證的伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="d4b9a-129">這個認證必須使用來指定[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-129">This credential needs to be specified using the [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md).</span></span><br /><span data-ttu-id="d4b9a-130">WCF 不支援傳送密碼摘要或衍生金鑰使用密碼，並使用訊息安全性這類金鑰。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-130">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="d4b9a-131">因此，傳輸保護使用 UserName 認證時，會強制執行 WCF。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-131">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="d4b9a-132">對於 `basicHttpBinding`，這需要設定 SSL 通道。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="d4b9a-133">憑證</span><span class="sxs-lookup"><span data-stu-id="d4b9a-133">Certificate</span></span>|<span data-ttu-id="d4b9a-134">需要使用憑證對伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="d4b9a-135">在此情況下必須使用指定的用戶端認證[ \<clientCredentials >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)並[ \<clientCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-135">The client credential in this case needs to be specified using [\<clientCredentials>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) and the [\<clientCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="d4b9a-136">此外，當使用訊息安全性模式時，必須提供服務憑證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="d4b9a-137">在此情況下必須使用指定的服務認證<xref:System.ServiceModel.Description.ClientCredentials>類別或`ClientCredentials`行為項目，並指定服務憑證使用[ \<serviceCertificate >](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](../../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="d4b9a-138">子元素</span><span class="sxs-lookup"><span data-stu-id="d4b9a-138">Child Elements</span></span>  
 <span data-ttu-id="d4b9a-139">無</span><span class="sxs-lookup"><span data-stu-id="d4b9a-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="d4b9a-140">父項目</span><span class="sxs-lookup"><span data-stu-id="d4b9a-140">Parent Elements</span></span>  
  
|<span data-ttu-id="d4b9a-141">項目</span><span class="sxs-lookup"><span data-stu-id="d4b9a-141">Element</span></span>|<span data-ttu-id="d4b9a-142">描述</span><span class="sxs-lookup"><span data-stu-id="d4b9a-142">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="d4b9a-143">\<security></span><span class="sxs-lookup"><span data-stu-id="d4b9a-143">\<security></span></span>](../../../../../docs/framework/configure-apps/file-schema/wcf/security-of-basichttpbinding.md)|<span data-ttu-id="d4b9a-144">定義的安全性功能[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-144">Defines the security capabilities for the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="d4b9a-145">範例</span><span class="sxs-lookup"><span data-stu-id="d4b9a-145">Example</span></span>  
 <span data-ttu-id="d4b9a-146">這個範例會示範如何實作一個使用 basicHttpBinding 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="d4b9a-147">在下列服務組態範例中，端點定義會指定 basicHttpBinding，並參考名為 `Binding1` 的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="d4b9a-148">服務對用戶端驗證它自己時所使用的憑證是在組態檔案 `behaviors` 區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="d4b9a-149">用戶端用來對服務驗證本身之憑證所套用的驗證模式，也是在 `behaviors` 項目下的 `clientCertificate` 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="d4b9a-150">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="d4b9a-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>
  <services>
    <service name="Microsoft.ServiceModel.Samples.CalculatorService"
             behaviorConfiguration="CalculatorServiceBehavior">
      <host>
        <baseAddresses>
          <add baseAddress="http://localhost:8000/ServiceModelSamples/service" />
        </baseAddresses>
      </host>
      <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service -->
      <endpoint address=""
                binding="basicHttpBinding"
                bindingConfiguration="Binding1"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
      <!-- the mex endpoint is exposed at http://localhost:8000/ServiceModelSamples/service/mex -->
      <endpoint address="mex"
                binding="mexHttpBinding"
                contract="IMetadataExchange" />
    </service>
  </services>
  <bindings>
    <basicHttpBinding>
    <!-- This configuration defines the SecurityMode as Message and
         the clientCredentialType as Certificate. -->
      <binding name="Binding1">
        <security mode = "Message">
          <message clientCredentialType="Certificate" />
        </security>
      </binding>
    </basicHttpBinding>
  </bindings>
  <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->
  <behaviors>
    <serviceBehaviors>
      <behavior name="CalculatorServiceBehavior">
        <serviceMetadata httpGetEnabled="True" />
        <serviceDebug includeExceptionDetailInFaults="False" />
        <!-- The serviceCredentials behavior allows one to define a service certificate.
             A service certificate is used by a client to authenticate the service and provide message protection.
             This configuration references the "localhost" certificate installed during the setup instructions. -->
        <serviceCredentials>
          <serviceCertificate findValue="localhost"
                              storeLocation="LocalMachine"
                              storeName="My"
                              x509FindType="FindBySubjectName" />
          <clientCertificate>
            <!-- Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate
               is in the user's Trusted People store, then it will be trusted without performing a
               validation of the certificate's issuer chain. This setting is used here for convenience so that the
               sample can be run without having to have certificates issued by a certification authority (CA).
               This setting is less secure than the default, ChainTrust. The security implications of this
               setting should be carefully considered before using PeerOrChainTrust in production code. -->
            <authentication certificateValidationMode="PeerOrChainTrust" />
          </clientCertificate>
        </serviceCredentials>
      </behavior>
    </serviceBehaviors>
  </behaviors>
</system.serviceModel>
```  
  
## <a name="see-also"></a><span data-ttu-id="d4b9a-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d4b9a-151">See also</span></span>
- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="d4b9a-152">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="d4b9a-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="d4b9a-153">繫結</span><span class="sxs-lookup"><span data-stu-id="d4b9a-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)
- [<span data-ttu-id="d4b9a-154">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="d4b9a-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="d4b9a-155">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="d4b9a-155">Using Bindings to Configure Services and Clients</span></span>](../../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="d4b9a-156">\<binding></span><span class="sxs-lookup"><span data-stu-id="d4b9a-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
