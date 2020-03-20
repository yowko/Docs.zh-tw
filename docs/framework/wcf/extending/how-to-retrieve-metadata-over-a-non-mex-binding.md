---
title: HOW TO：透過非 MEX 繫結擷取中繼資料
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: a006795c87a2ae845d03db90dce296692c4339fa
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/12/2020
ms.locfileid: "79186439"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="a3e3b-102">HOW TO：透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="a3e3b-102">How to: Retrieve Metadata Over a non-MEX Binding</span></span>
<span data-ttu-id="a3e3b-103">本主題說明如何透過非 MEX 繫結，擷取 MEX 端點的中繼資料。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-103">This topic describes how to retrieve metadata from a MEX endpoint over a non-MEX binding.</span></span> <span data-ttu-id="a3e3b-104">此示例中的代碼基於[自訂安全中繼資料終結點](../samples/custom-secure-metadata-endpoint.md)示例。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-104">The code in this sample is based on the [Custom Secure Metadata Endpoint](../samples/custom-secure-metadata-endpoint.md) sample.</span></span>  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a><span data-ttu-id="a3e3b-105">透過非 MEX 繫結擷取中繼資料</span><span class="sxs-lookup"><span data-stu-id="a3e3b-105">To retrieve metadata over a non-MEX binding</span></span>  
  
1. <span data-ttu-id="a3e3b-106">判定 MEX 端點使用的繫結。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-106">Determine the binding used by the MEX endpoint.</span></span> <span data-ttu-id="a3e3b-107">對於 Windows 通信基礎 （WCF） 服務，您可以通過訪問服務的設定檔來確定 MEX 綁定。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-107">For Windows Communication Foundation (WCF) services, you can determine the MEX binding by accessing the service's configuration file.</span></span> <span data-ttu-id="a3e3b-108">在此例中，MEX 繫結是定義於下列服務組態。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-108">In this case, the MEX binding is defined in the following service configuration.</span></span>  
  
    ```xml  
    <services>  
        <service name="Microsoft.ServiceModel.Samples.CalculatorService"  
                behaviorConfiguration="CalculatorServiceBehavior">  
         <!-- Use the base address provided by the host. -->  
         <endpoint address=""  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding2"  
           contract="Microsoft.ServiceModel.Samples.ICalculator" />  
         <endpoint address="mex"  
           binding="wsHttpBinding"  
           bindingConfiguration="Binding1"  
           contract="IMetadataExchange" />  
         </service>  
     </services>  
     <bindings>  
       <wsHttpBinding>  
         <binding name="Binding1">  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
         <binding name="Binding2">  
           <reliableSession inactivityTimeout="00:01:00" enabled="true" />  
           <security mode="Message">  
             <message clientCredentialType="Certificate" />  
           </security>  
         </binding>  
       </wsHttpBinding>  
     </bindings>  
    ```  
  
2. <span data-ttu-id="a3e3b-109">在用戶端組態檔中，設定相同的自訂繫結。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-109">In the client configuration file, configure the same custom binding.</span></span> <span data-ttu-id="a3e3b-110">在此用戶端也會定義 `clientCredentials` 行為以提供憑證，當要求 MEX 端點的中繼資料時可以用來驗證服務。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-110">Here the client also defines a `clientCredentials` behavior to provide a certificate to use to authenticate to the service when requesting metadata from the MEX endpoint.</span></span> <span data-ttu-id="a3e3b-111">當使用 Svcutil.exe 透過自訂繫結要求中繼資料時，您應該將 MEX 端點組態新增至 Svcutil.exe 的組態檔 (Svcutil.exe.config)，並且端點組態的名稱應符合 MEX 端點位址的 URI 結構描述，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-111">When using Svcutil.exe to request metadata over a custom binding, you should add the MEX endpoint configuration to the configuration file for Svcutil.exe (Svcutil.exe.config), and the name of the endpoint configuration should match the URI scheme of the address of the MEX endpoint, as shown in the following code.</span></span>  
  
    ```xml  
    <system.serviceModel>  
      <client>  
        <endpoint name="http"  
                  binding="wsHttpBinding"  
                  bindingConfiguration="Binding1"  
                  behaviorConfiguration="ClientCertificateBehavior"  
                  contract="IMetadataExchange" />  
      </client>  
      <bindings>  
        <wsHttpBinding>  
          <binding name="Binding1">  
            <security mode="Message">  
              <message clientCredentialType="Certificate"/>  
            </security>  
          </binding>  
        </wsHttpBinding>  
      </bindings>  
      <behaviors>  
        <endpointBehaviors>  
          <behavior name="ClientCertificateBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="client.com" storeLocation="CurrentUser" storeName="My" x509FindType="FindBySubjectName" />  
              <serviceCertificate>  
                <authentication certificateValidationMode="PeerOrChainTrust" />  
              </serviceCertificate>  
            </clientCredentials>  
          </behavior>  
        </endpointBehaviors>  
      </behaviors>
    </system.serviceModel>  
    ```  
  
3. <span data-ttu-id="a3e3b-112">建立 `MetadataExchangeClient` 並呼叫 `GetMetadata`。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-112">Create a `MetadataExchangeClient` and call `GetMetadata`.</span></span> <span data-ttu-id="a3e3b-113">這有兩種做法：您可以在組態中指定自訂繫結，或是在程式碼中指定自訂繫結，如下列範例所示。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-113">There are two ways to do this: you can specify the custom binding in configuration, or you can specify the custom binding in code, as shown in the following example.</span></span>  
  
    ```csharp
    // The custom binding is specified in configuration.  
    EndpointAddress mexAddress = new EndpointAddress("http://localhost:8000/ServiceModelSamples/Service/mex");  
  
    MetadataExchangeClient mexClient = new MetadataExchangeClient("http");  
    mexClient.ResolveMetadataReferences = true;  
    MetadataSet mexSet = mexClient.GetMetadata(mexAddress);  
  
    // The custom binding is specified in code.  
    // Specify the Metadata Exchange binding and its security mode.  
    WSHttpBinding mexBinding = new WSHttpBinding(SecurityMode.Message);  
    mexBinding.Security.Message.ClientCredentialType = MessageCredentialType.Certificate;  
  
    // Create a MetadataExchangeClient and set the certificate details.  
    MetadataExchangeClient mexClient = new MetadataExchangeClient(mexBinding);  
    mexClient.SoapCredentials.ClientCertificate.SetCertificate(  
        StoreLocation.CurrentUser, StoreName.My,  
        X509FindType.FindBySubjectName, "client.com");  
    mexClient.SoapCredentials.ServiceCertificate.Authentication.  
        CertificateValidationMode =  
        X509CertificateValidationMode.PeerOrChainTrust;  
    mexClient.SoapCredentials.ServiceCertificate.SetDefaultCertificate(  
        StoreLocation.CurrentUser, StoreName.TrustedPeople,  
        X509FindType.FindBySubjectName, "localhost");  
    MetadataExchangeClient mexClient2 = new MetadataExchangeClient(customBinding);  
    mexClient2.ResolveMetadataReferences = true;  
    MetadataSet mexSet2 = mexClient2.GetMetadata(mexAddress);  
    ```  
  
4. <span data-ttu-id="a3e3b-114">建立 `WsdlImporter` 並呼叫 `ImportAllEndpoints`，如下列程式碼所示。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-114">Create a `WsdlImporter` and call `ImportAllEndpoints`, as shown in the following code.</span></span>  
  
    ```csharp
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. <span data-ttu-id="a3e3b-115">此時，您會擁有服務端點的集合。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-115">At this point, you have a collection of service endpoints.</span></span> <span data-ttu-id="a3e3b-116">有關導入中繼資料的詳細資訊，請參閱[如何：將中繼資料導入服務終結點](../feature-details/how-to-import-metadata-into-service-endpoints.md)。</span><span class="sxs-lookup"><span data-stu-id="a3e3b-116">For more information about importing metadata, see [How to: Import Metadata into Service Endpoints](../feature-details/how-to-import-metadata-into-service-endpoints.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a3e3b-117">另請參閱</span><span class="sxs-lookup"><span data-stu-id="a3e3b-117">See also</span></span>

- [<span data-ttu-id="a3e3b-118">元</span><span class="sxs-lookup"><span data-stu-id="a3e3b-118">Metadata</span></span>](../feature-details/metadata.md)
