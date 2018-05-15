---
title: '&lt;netHttpBinding&gt; 的 &lt;message&gt;'
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 6e4cd2c000d577e26b54e09f24279e0fd74afcf1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/03/2018
---
# <a name="ltmessagegt-of-ltnethttpbindinggt"></a><span data-ttu-id="8e1ff-102">&lt;netHttpBinding&gt; 的 &lt;message&gt;</span><span class="sxs-lookup"><span data-stu-id="8e1ff-102">&lt;message&gt; of &lt;netHttpBinding&gt;</span></span>
<span data-ttu-id="8e1ff-103">定義訊息層級安全性的設定[ \<basicHttpBinding >](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-103">Defines the settings for message-level security of the [\<basicHttpBinding>](../../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md).</span></span>  
  
 <span data-ttu-id="8e1ff-104">\<system.ServiceModel></span><span class="sxs-lookup"><span data-stu-id="8e1ff-104">\<system.ServiceModel></span></span>  
<span data-ttu-id="8e1ff-105">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="8e1ff-105">\<bindings></span></span>  
<span data-ttu-id="8e1ff-106">\<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="8e1ff-106">\<netHttpBinding></span></span>  
<span data-ttu-id="8e1ff-107">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="8e1ff-107">\<binding></span></span>  
<span data-ttu-id="8e1ff-108">\<安全性 ></span><span class="sxs-lookup"><span data-stu-id="8e1ff-108">\<security></span></span>  
<span data-ttu-id="8e1ff-109">\<message></span><span class="sxs-lookup"><span data-stu-id="8e1ff-109">\<message></span></span>  
  
## <a name="syntax"></a><span data-ttu-id="8e1ff-110">語法</span><span class="sxs-lookup"><span data-stu-id="8e1ff-110">Syntax</span></span>  
  
```xml  
<message   
   algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"  
      clientCredentialType="UserName/Certificate"/>  
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="8e1ff-111">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="8e1ff-111">Attributes and Elements</span></span>  
 <span data-ttu-id="8e1ff-112">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="8e1ff-112">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="8e1ff-113">屬性</span><span class="sxs-lookup"><span data-stu-id="8e1ff-113">Attributes</span></span>  
  
|<span data-ttu-id="8e1ff-114">屬性</span><span class="sxs-lookup"><span data-stu-id="8e1ff-114">Attribute</span></span>|<span data-ttu-id="8e1ff-115">描述</span><span class="sxs-lookup"><span data-stu-id="8e1ff-115">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="8e1ff-116">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="8e1ff-116">algorithmSuite</span></span>|<span data-ttu-id="8e1ff-117">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-117">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="8e1ff-118">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>，它會指定演算法和金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-118">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="8e1ff-119">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-119">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="8e1ff-120">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-120">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="8e1ff-121">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="8e1ff-121">clientCredentialType</span></span>|<span data-ttu-id="8e1ff-122">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-122">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="8e1ff-123">預設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-123">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="8e1ff-124">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="8e1ff-124">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="8e1ff-125">值</span><span class="sxs-lookup"><span data-stu-id="8e1ff-125">Value</span></span>|<span data-ttu-id="8e1ff-126">描述</span><span class="sxs-lookup"><span data-stu-id="8e1ff-126">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="8e1ff-127">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="8e1ff-127">UserName</span></span>|<span data-ttu-id="8e1ff-128">-需要使用 UserName 認證伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-128">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="8e1ff-129">這個認證必須使用 <`clientCredentials`> 項目來指定。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-129">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="8e1ff-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 不支援傳送密碼摘要或衍生金鑰，使用密碼，甚至對訊息安全性使用該金鑰。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-130">-   [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="8e1ff-131">因此，[!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] 會在使用 UserName 認證時強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-131">Therefore, [!INCLUDE[indigo2](../../../../../includes/indigo2-md.md)] enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="8e1ff-132">對於 `basicHttpBinding`，這需要設定 SSL 通道。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-132">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="8e1ff-133">憑證</span><span class="sxs-lookup"><span data-stu-id="8e1ff-133">Certificate</span></span>|<span data-ttu-id="8e1ff-134">需要使用憑證對伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-134">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="8e1ff-135">此案例中的用戶端認證必須使用 <`clientCredentials`> 和 <`clientCertificate`> 來指定。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-135">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="8e1ff-136">此外，當使用訊息安全性模式時，必須提供服務憑證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-136">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="8e1ff-137">在此情況下必須指定使用服務認證<xref:System.ServiceModel.Description.ClientCredentials>類別或`ClientCredentials`行為項目，並指定服務憑證使用\<serviceCertificate > serviceCredentials 的項目。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-137">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="8e1ff-138">子項目</span><span class="sxs-lookup"><span data-stu-id="8e1ff-138">Child Elements</span></span>  
 <span data-ttu-id="8e1ff-139">無</span><span class="sxs-lookup"><span data-stu-id="8e1ff-139">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="8e1ff-140">父項目</span><span class="sxs-lookup"><span data-stu-id="8e1ff-140">Parent Elements</span></span>  
  
|<span data-ttu-id="8e1ff-141">項目</span><span class="sxs-lookup"><span data-stu-id="8e1ff-141">Element</span></span>|<span data-ttu-id="8e1ff-142">描述</span><span class="sxs-lookup"><span data-stu-id="8e1ff-142">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="8e1ff-143"><`security`> 項目 <`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="8e1ff-143"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="8e1ff-144">定義 <`netHttpBinding`> 項目的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-144">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="8e1ff-145">範例</span><span class="sxs-lookup"><span data-stu-id="8e1ff-145">Example</span></span>  
 <span data-ttu-id="8e1ff-146">這個範例會示範如何實作一個使用 basicHttpBinding 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-146">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="8e1ff-147">在下列服務組態範例中，端點定義會指定 basicHttpBinding，並參考名為 `Binding1` 的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-147">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="8e1ff-148">服務對用戶端驗證它自己時所使用的憑證是在組態檔案 `behaviors` 區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-148">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="8e1ff-149">用戶端用來對服務驗證本身之憑證所套用的驗證模式，也是在 `behaviors` 項目下的 `clientCertificate` 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-149">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="8e1ff-150">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="8e1ff-150">The same binding and security details are specified in the client configuration file.</span></span>  
  
```xml  
<system.serviceModel>  
    <services>  
      <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
               behaviorConfiguration="CalculatorServiceBehavior">  
        <host>  
          <baseAddresses>  
            <add baseAddress="http://localhost:8000/ServiceModelSamples/service"/>  
          </baseAddresses>  
        </host>  
        <!-- this endpoint is exposed at the base address provided by host: http://localhost:8000/ServiceModelSamples/service  -->  
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
        <!--   
        This configuration defines the SecurityMode as Message and   
        the clientCredentialType as Certificate.  
        -->  
        <binding name="Binding1" >  
          <security mode = "Message">  
            <message clientCredentialType="Certificate"/>  
          </security>  
        </binding>  
      </basicHttpBinding>  
    </bindings>  
  
    <!--For debugging purposes set the includeExceptionDetailInFaults attribute to true-->  
    <behaviors>  
      <serviceBehaviors>  
        <behavior name="CalculatorServiceBehavior">  
          <serviceMetadata httpGetEnabled="True"/>  
          <serviceDebug includeExceptionDetailInFaults="False" />  
          <!--  
        The serviceCredentials behavior allows one to define a service certificate.  
        A service certificate is used by a client to authenticate the service and provide message protection.  
        This configuration references the "localhost" certificate installed during the setup instructions.  
        -->  
          <serviceCredentials>  
            <serviceCertificate findValue="localhost" storeLocation="LocalMachine" storeName="My" x509FindType="FindBySubjectName" />  
            <clientCertificate>  
              <!--   
            Setting the certificateValidationMode to PeerOrChainTrust means that if the certificate   
            is in the user's Trusted People store, then it will be trusted without performing a  
            validation of the certificate's issuer chain. This setting is used here for convenience so that the   
            sample can be run without having to have certificates issued by a certification authority (CA).  
            This setting is less secure than the default, ChainTrust. The security implications of this   
            setting should be carefully considered before using PeerOrChainTrust in production code.   
            -->  
              <authentication certificateValidationMode="PeerOrChainTrust" />  
            </clientCertificate>  
          </serviceCredentials>  
        </behavior>  
      </serviceBehaviors>  
    </behaviors>  
</system.serviceModel>  
```  
  
## <a name="see-also"></a><span data-ttu-id="8e1ff-151">另請參閱</span><span class="sxs-lookup"><span data-stu-id="8e1ff-151">See Also</span></span>  
 [<span data-ttu-id="8e1ff-152">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="8e1ff-152">Securing Services and Clients</span></span>](../../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [<span data-ttu-id="8e1ff-153">繫結</span><span class="sxs-lookup"><span data-stu-id="8e1ff-153">Bindings</span></span>](../../../../../docs/framework/wcf/bindings.md)  
 [<span data-ttu-id="8e1ff-154">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="8e1ff-154">Configuring System-Provided Bindings</span></span>](../../../../../docs/framework/wcf/feature-details/configuring-system-provided-bindings.md)  
 [<span data-ttu-id="8e1ff-155">使用繫結來設定 Windows Communication Foundation 服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="8e1ff-155">Using Bindings to Configure Windows Communication Foundation Services and Clients</span></span>](http://msdn.microsoft.com/library/bd8b277b-932f-472f-a42a-b02bb5257dfb)  
 [<span data-ttu-id="8e1ff-156">\<繫結 ></span><span class="sxs-lookup"><span data-stu-id="8e1ff-156">\<binding></span></span>](../../../../../docs/framework/misc/binding.md)
