---
title: HOW TO：指定用戶端認證值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: ecb8f7ef74f1f0625454eb2d6cebf9d282a5ece3
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/18/2019
ms.locfileid: "59327096"
---
# <a name="how-to-specify-client-credential-values"></a>HOW TO：指定用戶端認證值
使用 Windows Communication Foundation (WCF)，服務可以指定用戶端驗證服務的方式。 例如，服務可以規定用戶端必須出示憑證交付驗證。  
  
### <a name="to-determine-the-client-credential-type"></a>判斷用戶端認證類型  
  
1. 從服務的中繼資料端點擷取中繼資料。 中繼資料通常包含兩個檔案：以您所選程式語言 (預設為 Visual C#) 撰寫的用戶端程式碼，還有 XML 組態檔。 擷取中繼資料的方法之一，是使用 Svcutil.exe 工具傳回用戶端程式碼和用戶端組態。 如需詳細資訊，請參閱 <<c0> [ 擷取的中繼資料](../../../docs/framework/wcf/feature-details/retrieving-metadata.md)並[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
2. 開啟 XML 組態檔。 如果您是使用 Svcutil.exe 工具，檔案的預設名稱即為 Output.config。  
  
3. 尋找**\<安全性 >** 項目**模式**屬性 (**< 安全性模式 =** `MessageOrTransport` **>** 其中`MessageOrTransport`設為其中一種安全性模式。  
  
4. 找出符合模式值的子項目。 例如，如果模式設定為**訊息**，尋找**\<訊息 >** 中所包含的項目**\<安全性 >** 項目。  
  
5. 記下值指派給**clientCredentialType**屬性。 實際值取決於使用的模式是傳輸還是訊息。  
  
 下列 XML 程式碼所示為使用訊息安全性，且用戶端驗證時需要憑證的用戶端組態。  
  
```xml  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## <a name="example-tcp-transport-mode-with-certificate-as-client-credential"></a>範例：TCP 傳輸模式結合用戶端認證的憑證  
 這個範例會將安全性模式設為傳輸模式，並將用戶端認證值設為 X.509 憑證。 下列程序示範如何透過程式碼與組態，設定用戶端的用戶端認證值。 這是假設您已使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務傳回中繼資料 （程式碼和組態）。 如需詳細資訊，請參閱[如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>若要透過程式碼指定用戶端的用戶端認證值  
  
1. 使用[ServiceModel Metadata Utility Tool (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)從服務產生程式碼和組態。  
  
2. 建立 WCF 用戶端會使用產生的程式碼的執行個體。  
  
3. 在用戶端類別上，將 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性設定為適當值。 這個範例會使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法，將屬性設定為 X.509 憑證。  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     您可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 類別的任何一種列舉。 此處將使用主旨名稱，以避免憑證因為到期日關係而變更。 使用主旨名稱可讓基礎結構重新找到憑證。  
  
#### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>若要透過組態指定用戶端的用戶端認證值  
  
1. 新增[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)項目[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。  
  
2. 新增[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目[\<行為 >](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)項目。 請務必將必要的 `name` 屬性設定為適當值。  
  
3. 新增[ \<clientCertificate >](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)項目[ \<clientCredentials >](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)項目。  
  
4. 將下列屬性設為適當的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下列程式碼所示。 如需憑證的詳細資訊，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
    ```xml  
    <behaviors>  
       <endpointBehaviors>  
          <behavior name="endpointCredentialBehavior">  
            <clientCredentials>  
              <clientCertificate findValue="Contoso.com"   
                                 storeLocation="LocalMachine"  
                                 storeName="TrustedPeople"  
                                 x509FindType="FindBySubjectName" />  
            </clientCredentials>  
          </behavior>  
       </endpointBehaviors>  
    </behaviors>  
    ```  
  
5. 設定用戶端時，設定 `behaviorConfiguration` 項目的 `<endpoint>` 屬性來指定行為，如下列程式碼所示。 端點元素是子系[\<用戶端 >](../../../docs/framework/configure-apps/file-schema/wcf/client.md)項目。 同時，將 `bindingConfiguration` 屬性設定為用戶端的繫結，以指定繫結組態的名稱。 如果您使用的是產生的組態檔，繫結名稱就會自動產生。 在這個範例中，名稱為 `"tcpBindingWithCredential"`。  
  
    ```xml  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [WCF 安全性程式設計](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
- [選取認證類型](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)
- [使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)
- [如何：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)
