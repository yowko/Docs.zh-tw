---
title: <message> 的 <netHttpBinding>
ms.date: 03/30/2017
ms.assetid: 9def5a35-475d-40d6-b716-ccdbd93863c7
ms.openlocfilehash: 62b1793d18ddc8edc1f55b02137c4e0a9f7327d2
ms.sourcegitcommit: b16c00371ea06398859ecd157defc81301c9070f
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/06/2020
ms.locfileid: "73738955"
---
# <a name="message-of-nethttpbinding"></a><span data-ttu-id="17c03-102">\<message> 的 \<netHttpBinding></span><span class="sxs-lookup"><span data-stu-id="17c03-102">\<message> of \<netHttpBinding></span></span>
<span data-ttu-id="17c03-103">定義的訊息層級安全性設定 [\<netHttpBinding>](nethttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="17c03-103">Defines the settings for message-level security of the [\<netHttpBinding>](nethttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<netHttpBinding>**](nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-nethttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="17c03-104">語法</span><span class="sxs-lookup"><span data-stu-id="17c03-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="17c03-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="17c03-105">Attributes and Elements</span></span>  
 <span data-ttu-id="17c03-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="17c03-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="17c03-107">屬性</span><span class="sxs-lookup"><span data-stu-id="17c03-107">Attributes</span></span>  
  
|<span data-ttu-id="17c03-108">屬性</span><span class="sxs-lookup"><span data-stu-id="17c03-108">Attribute</span></span>|<span data-ttu-id="17c03-109">描述</span><span class="sxs-lookup"><span data-stu-id="17c03-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="17c03-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="17c03-110">algorithmSuite</span></span>|<span data-ttu-id="17c03-111">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="17c03-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="17c03-112">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>，它會指定演算法和金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="17c03-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="17c03-113">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="17c03-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="17c03-114">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="17c03-114">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="17c03-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="17c03-115">clientCredentialType</span></span>|<span data-ttu-id="17c03-116">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="17c03-116">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="17c03-117">預設值為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="17c03-117">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="17c03-118">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="17c03-118">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="17c03-119">值</span><span class="sxs-lookup"><span data-stu-id="17c03-119">Value</span></span>|<span data-ttu-id="17c03-120">描述</span><span class="sxs-lookup"><span data-stu-id="17c03-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="17c03-121">UserName</span><span class="sxs-lookup"><span data-stu-id="17c03-121">UserName</span></span>|<span data-ttu-id="17c03-122">-要求用戶端必須使用 UserName 認證向伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="17c03-122">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="17c03-123">此認證必須使用 <> 元素來指定 `clientCredentials` 。</span><span class="sxs-lookup"><span data-stu-id="17c03-123">This credential needs to be specified using the <`clientCredentials`> element.</span></span><br /><span data-ttu-id="17c03-124">-WCF 不支援傳送密碼摘要或使用密碼衍生金鑰，以及使用這類金鑰來取得訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="17c03-124">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="17c03-125">因此，在使用使用者名稱認證時，WCF 會強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="17c03-125">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="17c03-126">對於 `basicHttpBinding`，這需要設定 SSL 通道。</span><span class="sxs-lookup"><span data-stu-id="17c03-126">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="17c03-127">憑證</span><span class="sxs-lookup"><span data-stu-id="17c03-127">Certificate</span></span>|<span data-ttu-id="17c03-128">需要使用憑證對伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="17c03-128">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="17c03-129">此案例中的用戶端認證必須使用 <`clientCredentials`> 和 <> 來指定 `clientCertificate` 。</span><span class="sxs-lookup"><span data-stu-id="17c03-129">The client credential in this case needs to be specified using <`clientCredentials`> and the <`clientCertificate`>.</span></span> <span data-ttu-id="17c03-130">此外，當使用訊息安全性模式時，必須提供服務憑證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="17c03-130">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="17c03-131">此案例中的服務認證必須使用 <xref:System.ServiceModel.Description.ClientCredentials> 類別或 `ClientCredentials` 行為元素來指定，並使用 serviceCredentials 的元素來指定服務憑證 \<serviceCertificate> 。</span><span class="sxs-lookup"><span data-stu-id="17c03-131">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the \<serviceCertificate> element of serviceCredentials.</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="17c03-132">子元素</span><span class="sxs-lookup"><span data-stu-id="17c03-132">Child Elements</span></span>  
 <span data-ttu-id="17c03-133">無</span><span class="sxs-lookup"><span data-stu-id="17c03-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="17c03-134">父項目</span><span class="sxs-lookup"><span data-stu-id="17c03-134">Parent Elements</span></span>  
  
|<span data-ttu-id="17c03-135">元素</span><span class="sxs-lookup"><span data-stu-id="17c03-135">Element</span></span>|<span data-ttu-id="17c03-136">描述</span><span class="sxs-lookup"><span data-stu-id="17c03-136">Description</span></span>|  
|-------------|-----------------|  
|<span data-ttu-id="17c03-137"><`security`<的> 元素`netHttpBinding`></span><span class="sxs-lookup"><span data-stu-id="17c03-137"><`security`> element of <`netHttpBinding`></span></span>|<span data-ttu-id="17c03-138">定義 <> 元素的安全性功能 `netHttpBinding` 。</span><span class="sxs-lookup"><span data-stu-id="17c03-138">Defines the security capabilities for the <`netHttpBinding`> Element.</span></span>|  
  
## <a name="example"></a><span data-ttu-id="17c03-139">範例</span><span class="sxs-lookup"><span data-stu-id="17c03-139">Example</span></span>  
 <span data-ttu-id="17c03-140">這個範例會示範如何實作一個使用 basicHttpBinding 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="17c03-140">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="17c03-141">在下列服務組態範例中，端點定義會指定 basicHttpBinding，並參考名為 `Binding1` 的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="17c03-141">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="17c03-142">服務對用戶端驗證它自己時所使用的憑證是在組態檔案 `behaviors` 區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="17c03-142">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="17c03-143">用戶端用來對服務驗證本身之憑證所套用的驗證模式，也是在 `behaviors` 項目下的 `clientCertificate` 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="17c03-143">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="17c03-144">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="17c03-144">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="17c03-145">另請參閱</span><span class="sxs-lookup"><span data-stu-id="17c03-145">See also</span></span>

- [<span data-ttu-id="17c03-146">Securing Services and Clients</span><span class="sxs-lookup"><span data-stu-id="17c03-146">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="17c03-147">繫結</span><span class="sxs-lookup"><span data-stu-id="17c03-147">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="17c03-148">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="17c03-148">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="17c03-149">使用繫結設定服務與用戶端</span><span class="sxs-lookup"><span data-stu-id="17c03-149">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
