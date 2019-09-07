---
title: <message> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: bce80d96b1bcec0d580f2de3fe88d5fd6ad0a3b5
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70400269"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="f3ded-102">\<basicHttpBinding > 的\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="f3ded-102">\<message> of \<basicHttpBinding></span></span>
<span data-ttu-id="f3ded-103">定義[ \<basicHttpBinding >](basichttpbinding.md)的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="f3ded-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
<span data-ttu-id="f3ded-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="f3ded-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="f3ded-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="f3ded-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="f3ded-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="f3ded-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="f3ded-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<basicHttpBinding >** ](basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f3ded-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)</span></span>\
<span data-ttu-id="f3ded-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="f3ded-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="f3ded-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-basichttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="f3ded-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)</span></span>\
<span data-ttu-id="f3ded-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<訊息 >**</span><span class="sxs-lookup"><span data-stu-id="f3ded-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f3ded-111">語法</span><span class="sxs-lookup"><span data-stu-id="f3ded-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="f3ded-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="f3ded-112">Attributes and Elements</span></span>  
 <span data-ttu-id="f3ded-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="f3ded-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="f3ded-114">屬性</span><span class="sxs-lookup"><span data-stu-id="f3ded-114">Attributes</span></span>  
  
|<span data-ttu-id="f3ded-115">屬性</span><span class="sxs-lookup"><span data-stu-id="f3ded-115">Attribute</span></span>|<span data-ttu-id="f3ded-116">描述</span><span class="sxs-lookup"><span data-stu-id="f3ded-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="f3ded-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="f3ded-117">algorithmSuite</span></span>|<span data-ttu-id="f3ded-118">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="f3ded-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="f3ded-119">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>，它會指定演算法和金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="f3ded-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="f3ded-120">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="f3ded-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="f3ded-121">預設值為 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="f3ded-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="f3ded-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="f3ded-122">clientCredentialType</span></span>|<span data-ttu-id="f3ded-123">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="f3ded-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="f3ded-124">預設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="f3ded-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="f3ded-125">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="f3ded-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="f3ded-126">值</span><span class="sxs-lookup"><span data-stu-id="f3ded-126">Value</span></span>|<span data-ttu-id="f3ded-127">說明</span><span class="sxs-lookup"><span data-stu-id="f3ded-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="f3ded-128">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="f3ded-128">UserName</span></span>|<span data-ttu-id="f3ded-129">-要求用戶端必須使用 UserName 認證向伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="f3ded-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="f3ded-130">此認證必須使用[ \<clientCredentials >](clientcredentials.md)來指定。</span><span class="sxs-lookup"><span data-stu-id="f3ded-130">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="f3ded-131">-WCF 不支援傳送密碼摘要或使用密碼衍生金鑰，以及使用這類金鑰來取得訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="f3ded-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="f3ded-132">因此，在使用使用者名稱認證時，WCF 會強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="f3ded-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="f3ded-133">對於 `basicHttpBinding`，這需要設定 SSL 通道。</span><span class="sxs-lookup"><span data-stu-id="f3ded-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="f3ded-134">憑證</span><span class="sxs-lookup"><span data-stu-id="f3ded-134">Certificate</span></span>|<span data-ttu-id="f3ded-135">需要使用憑證對伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="f3ded-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="f3ded-136">此案例中的用戶端認證必須使用[ \<clientCredentials](clientcredentials.md) [ \<> 和 clientCertificate >](clientcertificate-of-servicecredentials.md)來指定。</span><span class="sxs-lookup"><span data-stu-id="f3ded-136">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="f3ded-137">此外，當使用訊息安全性模式時，必須提供服務憑證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="f3ded-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="f3ded-138">此案例中的服務認證必須使用<xref:System.ServiceModel.Description.ClientCredentials>類別或`ClientCredentials`行為元素來指定，並使用[ \<serviceCertificate >](servicecertificate-of-servicecredentials.md)指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="f3ded-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="f3ded-139">子元素</span><span class="sxs-lookup"><span data-stu-id="f3ded-139">Child Elements</span></span>  
 <span data-ttu-id="f3ded-140">無</span><span class="sxs-lookup"><span data-stu-id="f3ded-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="f3ded-141">父項目</span><span class="sxs-lookup"><span data-stu-id="f3ded-141">Parent Elements</span></span>  
  
|<span data-ttu-id="f3ded-142">項目</span><span class="sxs-lookup"><span data-stu-id="f3ded-142">Element</span></span>|<span data-ttu-id="f3ded-143">描述</span><span class="sxs-lookup"><span data-stu-id="f3ded-143">Description</span></span>|  
|-------------|-----------------|  
|[<span data-ttu-id="f3ded-144">\<security></span><span class="sxs-lookup"><span data-stu-id="f3ded-144">\<security></span></span>](security-of-basichttpbinding.md)|<span data-ttu-id="f3ded-145">定義[ \<basicHttpBinding >](basichttpbinding.md)的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="f3ded-145">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="f3ded-146">範例</span><span class="sxs-lookup"><span data-stu-id="f3ded-146">Example</span></span>  
 <span data-ttu-id="f3ded-147">這個範例會示範如何實作一個使用 basicHttpBinding 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f3ded-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="f3ded-148">在下列服務組態範例中，端點定義會指定 basicHttpBinding，並參考名為 `Binding1` 的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="f3ded-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="f3ded-149">服務對用戶端驗證它自己時所使用的憑證是在組態檔案 `behaviors` 區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="f3ded-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="f3ded-150">用戶端用來對服務驗證本身之憑證所套用的驗證模式，也是在 `behaviors` 項目下的 `clientCertificate` 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="f3ded-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="f3ded-151">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="f3ded-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="f3ded-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="f3ded-152">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="f3ded-153">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="f3ded-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="f3ded-154">繫結</span><span class="sxs-lookup"><span data-stu-id="f3ded-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="f3ded-155">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="f3ded-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="f3ded-156">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="f3ded-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="f3ded-157">\<binding></span><span class="sxs-lookup"><span data-stu-id="f3ded-157">\<binding></span></span>](../../../misc/binding.md)
