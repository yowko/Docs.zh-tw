---
title: HOW TO：指定用戶端認證值
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
ms.openlocfilehash: 2417c2dd16224d6cbf00d3f1f4a8958420830b6c
ms.sourcegitcommit: 628e8147ca10187488e6407dab4c4e6ebe0cac47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/15/2019
ms.locfileid: "72319855"
---
# <a name="how-to-specify-client-credential-values"></a>HOW TO：指定用戶端認證值

使用 Windows Communication Foundation （WCF），服務可以指定如何向服務驗證用戶端。 例如，服務可以規定用戶端必須出示憑證交付驗證。

## <a name="to-determine-the-client-credential-type"></a>判斷用戶端認證類型

1. 從服務的中繼資料端點擷取中繼資料。 中繼資料通常包含兩個檔案：以您所選程式語言 (預設為 Visual C#) 撰寫的用戶端程式碼，還有 XML 組態檔。 擷取中繼資料的方法之一，是使用 Svcutil.exe 工具傳回用戶端程式碼和用戶端組態。 如需詳細資訊，請參閱抓取[中繼資料](./feature-details/retrieving-metadata.md)和[System.servicemodel 中繼資料公用程式工具（Svcutil .exe）](servicemodel-metadata-utility-tool-svcutil-exe.md)。

2. 開啟 XML 組態檔。 如果您是使用 Svcutil.exe 工具，檔案的預設名稱即為 Output.config。

3. 尋找具有**mode**屬性的 **\<security >** 元素（ **\<security mode =** `MessageOrTransport` **>** ，其中 `MessageOrTransport` 會設定為其中一個安全性模式。

4. 找出符合模式值的子項目。 例如，如果 [模式] 設定為 [**訊息**]，請尋找 **\<security >** 專案中所包含的 **\<message >** 元素。

5. 請注意指派給**clientCredentialType**屬性的值。 實際值取決於使用的模式是傳輸還是訊息。

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

這個範例會將安全性模式設為傳輸模式，並將用戶端認證值設為 X.509 憑證。 下列程序示範如何透過程式碼與組態，設定用戶端的用戶端認證值。 這會假設您已使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](servicemodel-metadata-utility-tool-svcutil-exe.md)來傳回服務的中繼資料（程式碼和設定）。 如需詳細資訊，請參閱[如何：建立用戶端](how-to-create-a-wcf-client.md)。

### <a name="to-specify-the-client-credential-value-on-the-client-in-code"></a>若要透過程式碼指定用戶端的用戶端認證值

1. 使用[System.servicemodel 中繼資料公用程式工具（Svcutil）](servicemodel-metadata-utility-tool-svcutil-exe.md) ，從服務產生程式碼和設定。

2. 使用產生的程式碼，建立 WCF 用戶端的實例。

3. 在用戶端類別上，將 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性設定為適當值。 這個範例會使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法，將屬性設定為 X.509 憑證。

     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]

     您可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 類別的任何一種列舉。 此處將使用主旨名稱，以避免憑證因為到期日關係而變更。 使用主旨名稱可讓基礎結構重新找到憑證。

### <a name="to-specify-the-client-credential-value-on-the-client-in-configuration"></a>若要透過組態指定用戶端的用戶端認證值

1. 將[\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)元素新增至[\<behaviors 的 >](../configure-apps/file-schema/wcf/behaviors.md)專案。

2. 將[\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)元素新增至[\<behaviors 的 >](../configure-apps/file-schema/wcf/behaviors.md)專案。 請務必將必要的 `name` 屬性設定為適當值。

3. 將[\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)元素新增至[\<clientCredentials 的 >](../configure-apps/file-schema/wcf/clientcredentials.md)專案。

4. 將下列屬性設為適當的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下列程式碼所示。 如需憑證的詳細資訊，請參閱[使用憑證](./feature-details/working-with-certificates.md)。

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

5. 設定用戶端時，設定 `behaviorConfiguration` 項目的 `<endpoint>` 屬性來指定行為，如下列程式碼所示。 端點元素是[\<client >](../configure-apps/file-schema/wcf/client.md)元素的子系。 同時，將 `bindingConfiguration` 屬性設定為用戶端的繫結，以指定繫結組態的名稱。 如果您使用的是產生的組態檔，繫結名稱就會自動產生。 在這個範例中，名稱為 `"tcpBindingWithCredential"`。

    ```xml
    <client>
      <endpoint name =""
                address="net.tcp://contoso.com:8036/aloha"
                binding="netTcpBinding"
                bindingConfiguration="tcpBindingWithCredential"
                behaviorConfiguration="endpointCredentialBehavior" />
    </client>
    ```

## <a name="see-also"></a>請參閱

- <xref:System.ServiceModel.NetTcpBinding>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>
- <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>
- <xref:System.ServiceModel.ClientBase%601>
- <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>
- [WCF 安全性程式設計](./feature-details/programming-wcf-security.md)
- [選取認證類型](./feature-details/selecting-a-credential-type.md)
- [ServiceModel 中繼資料公用程式工具 (Svcutil.exe)](servicemodel-metadata-utility-tool-svcutil-exe.md)
- [使用憑證](./feature-details/working-with-certificates.md)
- [如何：建立用戶端](how-to-create-a-wcf-client.md)
- [\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)
- [\<security >](../configure-apps/file-schema/wcf/security-of-nettcpbinding.md)
- [\<message >](../configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)
- [\<behavior >](../configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)
- [\<behaviors >](../configure-apps/file-schema/wcf/behaviors.md)
- [\<clientCertificate >](../configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)
- [\<clientCredentials >](../configure-apps/file-schema/wcf/clientcredentials.md)
