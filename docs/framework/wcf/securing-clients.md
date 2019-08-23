---
title: 確保用戶端的安全
ms.date: 03/30/2017
helpviewer_keywords:
- clients [WCF], security considerations
ms.assetid: 44c8578c-9a5b-4acd-8168-1c30a027c4c5
ms.openlocfilehash: 7f9a02bc650f54338dfcb1d3f41397e745483430
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/22/2019
ms.locfileid: "69959527"
---
# <a name="securing-clients"></a>確保用戶端的安全
在 Windows Communication Foundation (WCF) 中, 服務會規定用戶端的安全性需求。 也就是說，服務會指定使用哪一個安全性模式，以及用戶端是否必須提供認證。 因此，保護用戶端安全的程序便十分簡單，只要使用從服務 (如果已發行) 取得的中繼資料並建立用戶端即可。 中繼資料指定如何設定用戶端。 如果服務要求用戶端提供認證，則您必須取得符合要求的認證。 本主題將進一步探討此程序。 如需建立安全服務的詳細資訊, 請參閱[保護服務](../../../docs/framework/wcf/securing-services.md)。  
  
## <a name="the-service-specifies-security"></a>指定安全性的服務  
 根據預設, WCF 系結已啟用安全性功能。 (例外狀況是 <xref:System.ServiceModel.BasicHttpBinding>)。因此, 如果服務是使用 WCF 建立的, 則它會有更多的機會來執行安全性, 以確保驗證、機密性和完整性。 在該情況下，服務提供的中繼資料將指示它需要什麼來建立安全的通訊通道。 如果服務中繼資料沒有任何安全性需要，那麼就沒有方法強制服務採用安全性配置 (例如透過 HTTP 的 Secure Sockets Layer (SSL))。 如果服務要求用戶端提供認證，則用戶端開發人員、部署人員或管理員必須提供用戶端用來向服務驗證的實際認證。  
  
## <a name="obtaining-metadata"></a>取得中繼資料  
 建立用戶端時，第一個步驟是取得與用戶端通訊的服務中繼資料。 有兩種方法可以達到這個目的： 首先, 如果服務發行中繼資料交換 (MEX) 端點, 或透過 HTTP 或 HTTPS 提供它的中繼資料, 您可以使用[System.servicemodel 中繼資料公用程式工具 (Svcutil)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)來下載中繼資料, 這會產生用戶端的兩個程式碼檔案。以及設定檔案。 (如需使用此工具的詳細資訊, 請參閱[使用 WCF 用戶端存取服務](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md))。如果服務未發行 MEX 端點，而且也沒有透過 HTTP 或 HTTPS 提供它的中繼資料，您必須向服務建立者要求描述安全性需求與中繼資料的文件。  
  
> [!IMPORTANT]
> 建議使用來自受信任來源且不可竄改的中繼資料。 使用 HTTP 通訊協定擷取的中繼資料會以純文字傳送出去且可以竄改。 如果服務使用 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A> 和 <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A> 屬性，請以服務建立者提供的 URL 來使用 HTTPS 通訊協定下載資料。  
  
## <a name="validating-security"></a>驗證安全性  
 中繼來源可以區分成兩大類別：信任來源與不受信任的來源。 如果您信任來源，而且已從該來源的安全 MEX 端點下載用戶端程式碼和其他中繼資料，那麼您可以建立用戶端，提供用戶端正確的認證，並且毫無後顧之憂地執行它。  
  
 如果您選擇從您對它幾乎一無所知的來源下載用戶端和中繼資料，請務必驗證程式碼使用的安全性措施。 例如，您不可以只建立傳送您的個人資料或財務資料到服務的用戶端，除非該服務僅要求機密性和完整性。 您服務擁有者的信任應該可達到您願意公開這類資訊的程度，因為他或她將會看到這些資訊。  
  
 因此，通常在使用來自不受信任來源的程式碼和中繼資料時，請檢查程式碼和中繼資料，以確保其符合您要求的安全性等級。  
  
## <a name="setting-a-client-credential"></a>設定用戶端認證  
 在用戶端上設定用戶端認證是由兩個步驟所組成：  
  
1. 判斷服務所需的*用戶端認證類型*。 這可以由兩個方法的其中之一完成。 首先，如果您有來自服務建立者的文件，文件中應指出服務需要的用戶端認證類型 (如果有的話)。 再者，如果您只有 Svcutil.exe 工具產生的組態檔，您可以檢查個別的繫結來判斷需要哪一種認證類型。  
  
2. 指定實際的用戶端認證。 實際的用戶端認證稱為*用戶端認證值*, 以區別它與類型。 例如，如果用戶端認證類型指定憑證，您必須提供由服務信任的憑證授權單位核發的 X.509 憑證。  
  
### <a name="determining-the-client-credential-type"></a>判斷用戶端認證類型  
 如果您已產生 Svcutil .exe 工具的設定檔, 請檢查[ \<>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)區段的系結, 以判斷需要哪一種用戶端認證類型。 在該部分內有指定安全性需要的繫結項目。 具體而言, 請\<檢查每個系結的安全性 > 元素。 該項目包括 `mode` 屬性，您可以將該屬性設定為三個可能值 (`Message`、`Transport` 或 `TransportWithMessageCredential`) 的其中之一。 屬性的值決定模式，而模式決定哪一個子項目是重要的。  
  
 元素可以包含`<transport>` 或`<message>`元素, 或兩者。 `<security>` 重要的項目就是符合安全性模式的項目。 例如，下列程式碼指定安全性模式為 `"Message"`，而且 `<message>` 項目的用戶端認證類型是 `"Certificate"`。 在這個情況中，可以忽略 `<transport>` 項目。 但 `<message>` 項目指定必須提供 X.509 憑證。  

```xml  
<wsHttpBinding>  
    <binding name="WSHttpBinding_ICalculator">  
       <security mode="Message">  
           <transport clientCredentialType="Windows"   
                      realm="" />  
           <message clientCredentialType="Certificate"   
                    negotiateServiceCredential="true"  
                    algorithmSuite="Default"   
                    establishSecurityContext="true" />  
       </security>  
    </binding>  
</wsHttpBinding>  
```  

 請注意，如果 `clientCredentialType` 屬性已設定為 `"Windows"`，如下列範例所示，您不需要提供實際的認證值。 這是因為 Windows 整合式安全性已提供執行用戶端之人員的實際認證 (Kerberos 權杖)。  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows "   
        realm="" />  
</security>  
```  
  
### <a name="setting-the-client-credential-value"></a>設定用戶端認證值  
 如果用戶端必須提供認證，請使用適當方法設定用戶端。 例如，使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 方法設定用戶端憑證。  
  
 常見的認證形式是 X.509 憑證。 您可以用兩種方式提供認證：  
  
- 以程式設計方式將它編寫在您的用戶端程式碼中 (使用 `SetCertificate` 方法)。  
  
 藉由在[ \< ](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) `clientCredentials`用戶端的設定檔 > 區段中新增行為, 並使用元素 (如下所示)。  
  
#### <a name="setting-a-clientcredentials-value-in-code"></a>在程式碼中設定clientCredentials>值\<  
 若要在程式碼中設定[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)值, <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>您必須存取<xref:System.ServiceModel.ClientBase%601>類別的屬性。 該屬性傳回允許存取各種認證類型的 <xref:System.ServiceModel.Description.ClientCredentials> 物件，如下表所示。  
  
|ClientCredential 屬性|描述|注意|  
|-------------------------------|-----------------|-----------|  
|<xref:System.ServiceModel.Description.ClientCredentials.ClientCertificate%2A>|傳回 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>|代表用戶端向服務進行驗證時提供的 X.509 憑證。|  
|<xref:System.ServiceModel.Description.ClientCredentials.HttpDigest%2A>|傳回 <xref:System.ServiceModel.Security.HttpDigestClientCredential>|代表 HTTP 摘要式認證。 此認證是使用者名稱與密碼的雜湊。|  
|<xref:System.ServiceModel.Description.ClientCredentials.IssuedToken%2A>|傳回 <xref:System.ServiceModel.Security.IssuedTokenClientCredential>|代表安全性權杖服務核發的自訂安全性權杖，常使用於聯合案例中。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Peer%2A>|傳回 <xref:System.ServiceModel.Security.PeerCredential>|代表用在 Windows 網域上參與對等網狀結構的對等認證。|  
|<xref:System.ServiceModel.Description.ClientCredentials.ServiceCertificate%2A>|傳回 <xref:System.ServiceModel.Security.X509CertificateRecipientClientCredential>|代表超出範圍交涉中的服務所提供的 X.509 憑證。|  
|<xref:System.ServiceModel.Description.ClientCredentials.UserName%2A>|傳回 <xref:System.ServiceModel.Security.UserNamePasswordClientCredential>|代表使用者名稱和密碼組。|  
|<xref:System.ServiceModel.Description.ClientCredentials.Windows%2A>|傳回 <xref:System.ServiceModel.Security.WindowsClientCredential>|代表 Windows 用戶端認證 (Kerberos 認證)。 類別的屬性是唯讀屬性。|  
  
#### <a name="setting-a-clientcredentials-value-in-configuration"></a>在 Configuration 中設定clientCredentials>值\<  
 認證值的指定方式是使用端點行為做為[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)元素的子項目。 使用的項目視用戶端認證類型而定。 例如, 下列範例顯示使用 <[ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-clientcredentials-element.md)設定 x.509 憑證的設定。  
  
```xml  
<configuration>  
  <system.serviceModel>  
    <behaviors>  
      <endpointBehaviors>  
        <behavior name="myEndpointBehavior">  
          <clientCredentials>  
            <clientCertificate findvalue="myMachineName"   
            storeLocation="Current" X509FindType="FindBySubjectName" />  
          </clientCredentials>  
        </behavior>              
    </behaviors>  
  </system.serviceModel>  
</configuration>  
```  
  
 若要在 configuration 中設定用戶端認證, 請將[ \<endpointBehaviors >](../../../docs/framework/configure-apps/file-schema/wcf/endpointbehaviors.md)元素新增至設定檔。 此外, 新增的行為專案必須使用`behaviorConfiguration` [ \< \<用戶端 > 專案之端點 >](../configure-apps/file-schema/wcf/endpoint-of-client.md)的屬性 (attribute) 連結至服務的端點, 如下列範例所示。 `behaviorConfiguration` 屬性的值必須與 `name` 屬性的值相符。  

```xml
<configuration>
  <system.serviceModel>
    <client>
      <endpoint address="http://localhost/servicemodelsamples/service.svc"
                binding="wsHttpBinding"
                bindingConfiguration="Binding1"
                behaviorConfiguration="myEndpointBehavior"
                contract="Microsoft.ServiceModel.Samples.ICalculator" />
    </client>
  </system.serviceModel>
</configuration>
```
  
> [!NOTE]
> 使用應用程式組態檔無法設定某些用戶端認證值，例如使用者名稱和密碼，或者 Windows 使用者和密碼值。 這類認證值只能在程式碼中指定。  
  
 如需設定用戶端認證的詳細資訊, [請參閱如何:指定用戶端認證](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)值。  
  
> [!NOTE]
> `ClientCredentialType` 設定為 `SecurityMode` 時，會忽略 `"TransportWithMessageCredential",`，如下列範例組態所示。  
  
```xml  
<wsHttpBinding>  
    <binding name="PingBinding">  
        <security mode="TransportWithMessageCredential"  >  
           <message  clientCredentialType="UserName"   
               establishSecurityContext="false"    
               negotiateServiceCredential="false" />  
           <transport clientCredentialType="Certificate"  />  
         </security>  
    </binding>  
</wsHttpBinding>  
```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Description.ClientCredentials>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetEnabled%2A>
- <xref:System.ServiceModel.Description.ServiceMetadataBehavior.HttpsGetUrl%2A>
- [\<bindings>](../../../docs/framework/configure-apps/file-schema/wcf/bindings.md)
- [設定編輯器工具 (SvcConfigEditor.exe)](../../../docs/framework/wcf/configuration-editor-tool-svcconfigeditor-exe.md)
- [保護服務安全](../../../docs/framework/wcf/securing-services.md)
- [使用 WCF 用戶端存取服務](../../../docs/framework/wcf/accessing-services-using-a-wcf-client.md)
- [如何：指定用戶端認證值](../../../docs/framework/wcf/how-to-specify-client-credential-values.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [如何：指定用戶端認證類型](../../../docs/framework/wcf/how-to-specify-the-client-credential-type.md)
