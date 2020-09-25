---
title: <message> 的 <basicHttpBinding>
ms.date: 03/30/2017
ms.assetid: 51cdd329-6461-471a-8747-56c2299b61e5
ms.openlocfilehash: 8b1e889efc53d0132368111037399ea8872008b1
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91204862"
---
# <a name="message-of-basichttpbinding"></a><span data-ttu-id="38ab4-102">\<message> 的 \<basicHttpBinding></span><span class="sxs-lookup"><span data-stu-id="38ab4-102">\<message> of \<basicHttpBinding></span></span>

<span data-ttu-id="38ab4-103">定義訊息層級安全性的設定 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="38ab4-103">Defines the settings for message-level security of the [\<basicHttpBinding>](basichttpbinding.md).</span></span>  
  
[**\<configuration>**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.serviceModel>**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<bindings>**](bindings.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<basicHttpBinding>**](basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<binding>**\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<security>**](security-of-basichttpbinding.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<message>**  
  
## <a name="syntax"></a><span data-ttu-id="38ab4-104">Syntax</span><span class="sxs-lookup"><span data-stu-id="38ab4-104">Syntax</span></span>  
  
```xml  
<message algorithmSuite="Basic128/Basic192/Basic256/Basic128Rsa15/Basic256Rsa15/TripleDes/TripleDesRsa15/Basic128Sha256/Basic192Sha256/TripleDesSha256/Basic128Sha256Rsa15/Basic192Sha256Rsa15/Basic256Sha256Rsa15/TripleDesSha256Rsa15"
         clientCredentialType="UserName/Certificate" />
```  
  
## <a name="attributes-and-elements"></a><span data-ttu-id="38ab4-105">屬性和項目</span><span class="sxs-lookup"><span data-stu-id="38ab4-105">Attributes and Elements</span></span>  

 <span data-ttu-id="38ab4-106">下列各節說明屬性、子元素和父元素</span><span class="sxs-lookup"><span data-stu-id="38ab4-106">The following sections describe attributes, child elements, and parent elements</span></span>  
  
### <a name="attributes"></a><span data-ttu-id="38ab4-107">屬性</span><span class="sxs-lookup"><span data-stu-id="38ab4-107">Attributes</span></span>  
  
|<span data-ttu-id="38ab4-108">屬性</span><span class="sxs-lookup"><span data-stu-id="38ab4-108">Attribute</span></span>|<span data-ttu-id="38ab4-109">描述</span><span class="sxs-lookup"><span data-stu-id="38ab4-109">Description</span></span>|  
|---------------|-----------------|  
|<span data-ttu-id="38ab4-110">algorithmSuite</span><span class="sxs-lookup"><span data-stu-id="38ab4-110">algorithmSuite</span></span>|<span data-ttu-id="38ab4-111">設定訊息加密和金鑰包裝演算法。</span><span class="sxs-lookup"><span data-stu-id="38ab4-111">Sets the message encryption and key-wrap algorithms.</span></span> <span data-ttu-id="38ab4-112">此屬性的型別為 <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>，它會指定演算法和金鑰大小。</span><span class="sxs-lookup"><span data-stu-id="38ab4-112">This attribute is of type <xref:System.ServiceModel.Security.SecurityAlgorithmSuite>, which specifies the algorithms and the key sizes.</span></span> <span data-ttu-id="38ab4-113">這些演算法會對應到安全性原則語言 (WS-SecurityPolicy) 規格中所指定的演算法。</span><span class="sxs-lookup"><span data-stu-id="38ab4-113">These algorithms map to those specified in the Security Policy Language (WS-SecurityPolicy) specification.</span></span><br /><br /> <span data-ttu-id="38ab4-114">預設值是 `Basic256`。</span><span class="sxs-lookup"><span data-stu-id="38ab4-114">The default value is `Basic256`.</span></span>|  
|<span data-ttu-id="38ab4-115">clientCredentialType</span><span class="sxs-lookup"><span data-stu-id="38ab4-115">clientCredentialType</span></span>|<span data-ttu-id="38ab4-116">指定當使用訊息安全性執行用戶端驗證時，要使用的認證類型。</span><span class="sxs-lookup"><span data-stu-id="38ab4-116">Specifies the type of credential to be used when performing client authentication using message-based security.</span></span> <span data-ttu-id="38ab4-117">預設值為 `UserName`。</span><span class="sxs-lookup"><span data-stu-id="38ab4-117">The default is `UserName`.</span></span>|  
  
## <a name="clientcredentialtype-attribute"></a><span data-ttu-id="38ab4-118">clientCredentialType 屬性</span><span class="sxs-lookup"><span data-stu-id="38ab4-118">clientCredentialType Attribute</span></span>  
  
|<span data-ttu-id="38ab4-119">值</span><span class="sxs-lookup"><span data-stu-id="38ab4-119">Value</span></span>|<span data-ttu-id="38ab4-120">描述</span><span class="sxs-lookup"><span data-stu-id="38ab4-120">Description</span></span>|  
|-----------|-----------------|  
|<span data-ttu-id="38ab4-121">UserName</span><span class="sxs-lookup"><span data-stu-id="38ab4-121">UserName</span></span>|<span data-ttu-id="38ab4-122">-要求用戶端使用使用者名稱認證向伺服器進行驗證。</span><span class="sxs-lookup"><span data-stu-id="38ab4-122">-   Requires the client be authenticated to the server with a UserName credential.</span></span> <span data-ttu-id="38ab4-123">您必須使用來指定此認證 [\<clientCredentials>](clientcredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="38ab4-123">This credential needs to be specified using the [\<clientCredentials>](clientcredentials.md).</span></span><br /><span data-ttu-id="38ab4-124">-WCF 不支援傳送密碼摘要或使用密碼衍生金鑰，並使用這類金鑰來進行訊息安全性。</span><span class="sxs-lookup"><span data-stu-id="38ab4-124">-   WCF does not support sending a password digest or deriving keys using passwords and using such keys for message security.</span></span> <span data-ttu-id="38ab4-125">因此，WCF 會在使用 UserName 認證時強制保護傳輸。</span><span class="sxs-lookup"><span data-stu-id="38ab4-125">Therefore, WCF enforces that the transport be secured when using UserName credentials.</span></span> <span data-ttu-id="38ab4-126">對於 `basicHttpBinding`，這需要設定 SSL 通道。</span><span class="sxs-lookup"><span data-stu-id="38ab4-126">For the `basicHttpBinding`, this requires setting up an SSL channel.</span></span>|  
|<span data-ttu-id="38ab4-127">憑證</span><span class="sxs-lookup"><span data-stu-id="38ab4-127">Certificate</span></span>|<span data-ttu-id="38ab4-128">需要使用憑證對伺服器驗證用戶端。</span><span class="sxs-lookup"><span data-stu-id="38ab4-128">Requires that the client be authenticated to the server using a certificate.</span></span> <span data-ttu-id="38ab4-129">在此情況下，必須使用和來指定用戶端認證 [\<clientCredentials>](clientcredentials.md) [\<clientCertificate>](clientcertificate-of-servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="38ab4-129">The client credential in this case needs to be specified using [\<clientCredentials>](clientcredentials.md) and the [\<clientCertificate>](clientcertificate-of-servicecredentials.md).</span></span> <span data-ttu-id="38ab4-130">此外，當使用訊息安全性模式時，必須提供服務憑證給用戶端。</span><span class="sxs-lookup"><span data-stu-id="38ab4-130">In addition, when using message security mode, the client needs to be provisioned with the service certificate.</span></span> <span data-ttu-id="38ab4-131">此案例中的服務認證必須使用 <xref:System.ServiceModel.Description.ClientCredentials> 類別或行為專案加以指定 `ClientCredentials` ，並使用來指定服務憑證 [\<serviceCertificate>](servicecertificate-of-servicecredentials.md) 。</span><span class="sxs-lookup"><span data-stu-id="38ab4-131">The service credential in this case needs to be specified using <xref:System.ServiceModel.Description.ClientCredentials> class or `ClientCredentials` behavior element and specifying the service certificate using the [\<serviceCertificate>](servicecertificate-of-servicecredentials.md).</span></span>|  
  
### <a name="child-elements"></a><span data-ttu-id="38ab4-132">子元素</span><span class="sxs-lookup"><span data-stu-id="38ab4-132">Child Elements</span></span>  

 <span data-ttu-id="38ab4-133">無</span><span class="sxs-lookup"><span data-stu-id="38ab4-133">None</span></span>  
  
### <a name="parent-elements"></a><span data-ttu-id="38ab4-134">父項目</span><span class="sxs-lookup"><span data-stu-id="38ab4-134">Parent Elements</span></span>  
  
|<span data-ttu-id="38ab4-135">項目</span><span class="sxs-lookup"><span data-stu-id="38ab4-135">Element</span></span>|<span data-ttu-id="38ab4-136">描述</span><span class="sxs-lookup"><span data-stu-id="38ab4-136">Description</span></span>|  
|-------------|-----------------|  
|[\<security>](security-of-basichttpbinding.md)|<span data-ttu-id="38ab4-137">定義的安全性功能 [\<basicHttpBinding>](basichttpbinding.md) 。</span><span class="sxs-lookup"><span data-stu-id="38ab4-137">Defines the security capabilities for the [\<basicHttpBinding>](basichttpbinding.md).</span></span>|  
  
## <a name="example"></a><span data-ttu-id="38ab4-138">範例</span><span class="sxs-lookup"><span data-stu-id="38ab4-138">Example</span></span>  

 <span data-ttu-id="38ab4-139">這個範例會示範如何實作一個使用 basicHttpBinding 和訊息安全性的應用程式。</span><span class="sxs-lookup"><span data-stu-id="38ab4-139">This sample demonstrates how to implement an application that uses the basicHttpBinding and message security.</span></span> <span data-ttu-id="38ab4-140">在下列服務組態範例中，端點定義會指定 basicHttpBinding，並參考名為 `Binding1` 的繫結組態。</span><span class="sxs-lookup"><span data-stu-id="38ab4-140">In the following configuration example for a service, the endpoint definition specifies the basicHttpBinding and references a binding configuration named `Binding1`.</span></span> <span data-ttu-id="38ab4-141">服務對用戶端驗證它自己時所使用的憑證是在組態檔案 `behaviors` 區段中的 `serviceCredentials` 項目下設定。</span><span class="sxs-lookup"><span data-stu-id="38ab4-141">The certificate that the service uses to authenticate itself to the client is set in the `behaviors` section of the configuration file under the `serviceCredentials` element.</span></span> <span data-ttu-id="38ab4-142">用戶端用來對服務驗證本身之憑證所套用的驗證模式，也是在 `behaviors` 項目下的 `clientCertificate` 區段中設定。</span><span class="sxs-lookup"><span data-stu-id="38ab4-142">The validation mode that applies to the certificate that the client uses to authenticate itself to the service is also set in the `behaviors` section under the `clientCertificate` element.</span></span>  
  
 <span data-ttu-id="38ab4-143">相同的繫結和安全性詳細資訊是在用戶端組態檔中設定。</span><span class="sxs-lookup"><span data-stu-id="38ab4-143">The same binding and security details are specified in the client configuration file.</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="38ab4-144">另請參閱</span><span class="sxs-lookup"><span data-stu-id="38ab4-144">See also</span></span>

- <xref:System.ServiceModel.BasicHttpMessageSecurity>
- <xref:System.ServiceModel.Configuration.BasicHttpSecurityElement.Message%2A>
- <xref:System.ServiceModel.BasicHttpSecurity.Message%2A>
- <xref:System.ServiceModel.Configuration.BasicHttpMessageSecurityElement>
- [<span data-ttu-id="38ab4-145">確保服務與用戶端的安全</span><span class="sxs-lookup"><span data-stu-id="38ab4-145">Securing Services and Clients</span></span>](../../../wcf/feature-details/securing-services-and-clients.md)
- [<span data-ttu-id="38ab4-146">繫結</span><span class="sxs-lookup"><span data-stu-id="38ab4-146">Bindings</span></span>](../../../wcf/bindings.md)
- [<span data-ttu-id="38ab4-147">設定系統提供的繫結</span><span class="sxs-lookup"><span data-stu-id="38ab4-147">Configuring System-Provided Bindings</span></span>](../../../wcf/feature-details/configuring-system-provided-bindings.md)
- [<span data-ttu-id="38ab4-148">使用繫結來設定服務和用戶端</span><span class="sxs-lookup"><span data-stu-id="38ab4-148">Using Bindings to Configure Services and Clients</span></span>](../../../wcf/using-bindings-to-configure-services-and-clients.md)
- [\<binding>](bindings.md)
