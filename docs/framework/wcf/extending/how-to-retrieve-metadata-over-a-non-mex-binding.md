---
title: HOW TO：透過非 MEX 繫結擷取中繼資料
ms.date: 03/30/2017
ms.assetid: 2292e124-81b2-4317-b881-ce9c1ec66ecb
ms.openlocfilehash: 4a127e3e2283050018705c85606bd7c03c36de8b
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2019
ms.locfileid: "59345946"
---
# <a name="how-to-retrieve-metadata-over-a-non-mex-binding"></a>HOW TO：透過非 MEX 繫結擷取中繼資料
本主題說明如何透過非 MEX 繫結，擷取 MEX 端點的中繼資料。 在此範例中的程式碼根據[自訂安全中繼資料端點](../../../../docs/framework/wcf/samples/custom-secure-metadata-endpoint.md)範例。  
  
### <a name="to-retrieve-metadata-over-a-non-mex-binding"></a>透過非 MEX 繫結擷取中繼資料  
  
1. 判定 MEX 端點使用的繫結。 對於 Windows Communication Foundation (WCF) 服務，您可以藉由存取服務的組態檔來判斷 MEX 繫結。 在此例中，MEX 繫結是定義於下列服務組態。  
  
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
  
2. 在用戶端組態檔中，設定相同的自訂繫結。 在此用戶端也會定義 `clientCredentials` 行為以提供憑證，當要求 MEX 端點的中繼資料時可以用來驗證服務。 當使用 Svcutil.exe 透過自訂繫結要求中繼資料時，您應該將 MEX 端點組態新增至 Svcutil.exe 的組態檔 (Svcutil.exe.config)，並且端點組態的名稱應符合 MEX 端點位址的 URI 結構描述，如下列程式碼所示。  
  
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
  
3. 建立 `MetadataExchangeClient` 並呼叫 `GetMetadata`。 這有兩種做法：您可以在組態中指定自訂繫結，或是在程式碼中指定自訂繫結，如下列範例所示。  
  
    ```  
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
  
4. 建立 `WsdlImporter` 並呼叫 `ImportAllEndpoints`，如下列程式碼所示。  
  
    ```  
    WsdlImporter importer = new WsdlImporter(mexSet);  
    ServiceEndpointCollection endpoints = importer.ImportAllEndpoints();  
    ```  
  
5. 此時，您會擁有服務端點的集合。 如需有關如何匯入中繼資料的詳細資訊，請參閱[How to:中繼資料匯入服務端點](../../../../docs/framework/wcf/feature-details/how-to-import-metadata-into-service-endpoints.md)。  
  
## <a name="see-also"></a>另請參閱

- [中繼資料](../../../../docs/framework/wcf/feature-details/metadata.md)
