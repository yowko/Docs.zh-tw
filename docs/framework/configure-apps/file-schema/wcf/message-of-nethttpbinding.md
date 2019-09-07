---
title: <message> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 793e0541b1714d2afaafc634a9e9435e5243fa19
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397830"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="85d8b-102">\<netHttpBinding > 的\<訊息 ></span><span class="sxs-lookup"><span data-stu-id="85d8b-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="85d8b-103">定義[ \<netHttpBinding >](nethttpbinding.md)的訊息層級安全性設定。</span><span class="sxs-lookup"><span data-stu-id="85d8b-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
<span data-ttu-id="85d8b-104">[ **\<configuration>** ](../configuration-element.md)</span><span class="sxs-lookup"><span data-stu-id="85d8b-104">[**\<configuration>**](../configuration-element.md)</span></span>\
<span data-ttu-id="85d8b-105">&nbsp;&nbsp;[ **\<System.servicemodel >** ](system-servicemodel.md)</span><span class="sxs-lookup"><span data-stu-id="85d8b-105">&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)</span></span>\
<span data-ttu-id="85d8b-106">&nbsp;&nbsp;&nbsp;&nbsp;[ **\<系結 >** ](bindings.md)</span><span class="sxs-lookup"><span data-stu-id="85d8b-106">&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)</span></span>\
<span data-ttu-id="85d8b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<netHttpBinding >** ](nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="85d8b-107">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)</span></span>\
<span data-ttu-id="85d8b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<系結 >** </span><span class="sxs-lookup"><span data-stu-id="85d8b-108">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**</span></span>\
<span data-ttu-id="85d8b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<安全性 >** ](security-of-nethttpbinding.md)</span><span class="sxs-lookup"><span data-stu-id="85d8b-109">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)</span></span>\
<span data-ttu-id="85d8b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<訊息 >**</span><span class="sxs-lookup"><span data-stu-id="85d8b-110">&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="85d8b-111">語法</span><span class="sxs-lookup"><span data-stu-id="85d8b-111">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="85d8b-112">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="85d8b-112">Attributes and Elements</span></span>  
 <span data-ttu-id="85d8b-113">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="85d8b-113">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="85d8b-114">屬性</span><span class="sxs-lookup"><span data-stu-id="85d8b-114">Attributes</span></span>  
  
|<span data-ttu-id="85d8b-115">屬性</span><span class="sxs-lookup"><span data-stu-id="85d8b-115">Attribute</span></span>|<span data-ttu-id="85d8b-116">描述</span><span class="sxs-lookup"><span data-stu-id="85d8b-116">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="85d8b-117">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="85d8b-117">algorithmSuite</span></span>|<span data-ttu-id="85d8b-118">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="85d8b-118">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="85d8b-119">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>，它會指定演算法和金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="85d8b-119">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="85d8b-120">這些演算法會對應至安全性原則語言 (WS-SecurityPolicy) 規格中指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="85d8b-120">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="85d8b-121">預設值為 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="85d8b-121">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="85d8b-122">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="85d8b-122">clientCredentialType</span></span>|<span data-ttu-id="85d8b-123">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="85d8b-123">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="85d8b-124">預設為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="85d8b-124">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="85d8b-125">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="85d8b-125">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="85d8b-126">值</span><span class="sxs-lookup"><span data-stu-id="85d8b-126">Value</span></span>|<span data-ttu-id="85d8b-127">說明</span><span class="sxs-lookup"><span data-stu-id="85d8b-127">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="85d8b-128">使用者名稱</span><span class="sxs-lookup"><span data-stu-id="85d8b-128">UserName</span></span>|<span data-ttu-id="85d8b-129">-要求用戶端必須使用 UserName 認證向伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="85d8b-129">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="85d8b-130">此認證必須使用 <`clientCredentials`> 元素來指定。</span><span class="sxs-lookup"><span data-stu-id="85d8b-130">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="85d8b-131">-WCF 不支援傳送密碼摘要或使用密碼衍生金鑰，以及使用這類金鑰來取得訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="85d8b-131">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="85d8b-132">因此，在使用使用者名稱認證時，WCF 會強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="85d8b-132">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="85d8b-133">對於 `basicHttpBinding`，這需要設定 SSL 通道。</span><span class="sxs-lookup"><span data-stu-id="85d8b-133">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="85d8b-134">憑證</span><span class="sxs-lookup"><span data-stu-id="85d8b-134">Certificate</span></span>|<span data-ttu-id="85d8b-135">需要使用憑證對伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="85d8b-135">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="85d8b-136">此案例中的用戶端認證必須使用 <`clientCredentials`> 和 <`clientCertificate`> 來指定。</span><span class="sxs-lookup"><span data-stu-id="85d8b-136">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="85d8b-137">此外，當使用訊息安全性模式時，必須提供服務憑證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="85d8b-137">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="85d8b-138">此案例中的服務認證必須使用<xref:System.ServiceModel.Description.ClientCredentials>類別或`ClientCredentials`行為元素來指定，並使用 serviceCredentials 的\<serviceCertificate > 元素來指定服務憑證。</span><span class="sxs-lookup"><span data-stu-id="85d8b-138">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="85d8b-139">子元素</span><span class="sxs-lookup"><span data-stu-id="85d8b-139">Child Elements</span></span>  
 <span data-ttu-id="85d8b-140">無</span><span class="sxs-lookup"><span data-stu-id="85d8b-140">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="85d8b-141">父項目</span><span class="sxs-lookup"><span data-stu-id="85d8b-141">Parent Elements</span></span>  
  
|<span data-ttu-id="85d8b-142">項目</span><span class="sxs-lookup"><span data-stu-id="85d8b-142">Element</span></span>|<span data-ttu-id="85d8b-143">說明</span><span class="sxs-lookup"><span data-stu-id="85d8b-143">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="85d8b-144"><`security`< 的 > 元素`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="85d8b-144"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="85d8b-145">定義 <`netHttpBinding`> 元素的安全性功能。</span><span class="sxs-lookup"><span data-stu-id="85d8b-145">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="85d8b-146">範例</span><span class="sxs-lookup"><span data-stu-id="85d8b-146">Example</span></span>  
 <span data-ttu-id="85d8b-147">這個範例會示範如何實作一個使用 basicHttpBinding 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="85d8b-147">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="85d8b-148">在下列服務組態範例中，端點定義會指定 basicHttpBinding，並參考名為 `Binding1` 的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="85d8b-148">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="85d8b-149">服務對用戶端驗證它自己時所使用的憑證是在組態檔案 `behaviors` 區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="85d8b-149">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="85d8b-150">用戶端用來對服務驗證本身之憑證所套用的驗證模式，也是在 `behaviors` 項目下的 `clientCertificate` 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="85d8b-150">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="85d8b-151">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="85d8b-151">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
      <!-- This configuration defines the SecurityMode as Message and
           the clientCredentialType as Certificate. -->
      <binding name="Binding1" >
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
  
## <a name="see-also"></a><span data-ttu-id="85d8b-152">另請參閱</span><span class="sxs-lookup"><span data-stu-id="85d8b-152">See also</span></span>

- [<span data-ttu-id="85d8b-153">保護服務和用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="85d8b-153">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="85d8b-154">繫結</span><span class="sxs-lookup"><span data-stu-id="85d8b-154">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="85d8b-155">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="85d8b-155">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="85d8b-156">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="85d8b-156">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [<span data-ttu-id="85d8b-157">\<binding></span><span class="sxs-lookup"><span data-stu-id="85d8b-157">\<binding></span></span>](../../../misc/binding.md)
