---
title: "HOW TO：指定用戶端認證值 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: 82293d7f-471a-4549-8f19-0be890e7b074
caps.latest.revision: 28
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 28
---
# HOW TO：指定用戶端認證值
使用 [!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 可以讓服務指定用戶端向服務驗證自身的方式。  例如，服務可以規定用戶端必須出示憑證交付驗證。  
  
### 判斷用戶端認證類型  
  
1.  從服務的中繼資料端點擷取中繼資料。  中繼資料通常包含兩個檔案：以您所選程式語言 \(預設為 Visual C\#\) 撰寫的用戶端程式碼，還有 XML 組態檔。  擷取中繼資料的方法之一，是使用 Svcutil.exe 工具傳回用戶端程式碼和用戶端組態。  如需詳細資訊，請參閱[擷取中繼資料](../../../docs/framework/wcf/feature-details/retrieving-metadata.md)與 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)。  
  
2.  開啟 XML 組態檔。  如果您是使用 Svcutil.exe 工具，檔案的預設名稱即為 Output.config。  
  
3.  尋找具有 **mode** 屬性的 **\<security\>** 元素 \(**\<security mode \=** `MessageOrTransport`**\>**，其中的 `MessageOrTransport` 會設定為某一種安全性模式。  
  
4.  找出符合模式值的子項目。  例如，假定模式設為 \[**訊息**\]，則尋找包含於 **\<security\>** 項目中的 **\<message\>** 項目。  
  
5.  記下已指派給 **clientCredentialType** 屬性的值。  實際值取決於使用的模式是傳輸還是訊息。  
  
 下列 XML 程式碼所示為使用訊息安全性，且用戶端驗證時需要憑證的用戶端組態。  
  
```  
<security mode="Message">  
    <transport clientCredentialType="Windows" proxyCredentialType="None"  
        realm="" />  
     <message clientCredentialType="Certificate" negotiateServiceCredential="true"  
    algorithmSuite="Default" establishSecurityContext="true" />  
</security>  
```  
  
## 範例：TCP 傳輸模式結合用戶端認證的憑證  
 這個範例會將安全性模式設為傳輸模式，並將用戶端認證值設為 X.509 憑證。  下列程序示範如何透過程式碼與組態，設定用戶端的用戶端認證值。  此程序假設您已經使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 從服務傳回中繼資料 \(程式碼與組態\)。  [!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [HOW TO：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)。  
  
#### 若要透過程式碼指定用戶端的用戶端認證值  
  
1.  使用 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md) 從服務產生程式碼與組態。  
  
2.  使用產生的程式碼來建立 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 用戶端的執行個體。  
  
3.  在用戶端類別上，將 <xref:System.ServiceModel.ClientBase%601.ClientCredentials%2A> 類別的 <xref:System.ServiceModel.ClientBase%601> 屬性設定為適當值。  這個範例會使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法，將屬性設定為 X.509 憑證。  
  
     [!code-csharp[c_TcpService#4](../../../samples/snippets/csharp/VS_Snippets_CFX/c_tcpservice/cs/source.cs#4)]
     [!code-vb[c_TcpService#4](../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_tcpservice/vb/source.vb#4)]  
  
     您可以使用 <xref:System.Security.Cryptography.X509Certificates.X509FindType> 類別的任何一種列舉。  此處將使用主旨名稱，以避免憑證因為到期日關係而變更。  使用主旨名稱可讓基礎結構重新找到憑證。  
  
#### 若要透過組態指定用戶端的用戶端認證值  
  
1.  將 [\<行為\>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md) 元素新增至 [\<行為\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 元素。  
  
2.  將 [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 元素新增至 [\<行為\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md) 元素。  請務必將必要的 `name` 屬性設定為適當值。  
  
3.  將 [\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md) 元素新增至 [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md) 元素。  
  
4.  將下列屬性設為適當的值：`storeLocation`、`storeName`、`x509FindType` 和 `findValue`，如下列程式碼所示。  [!INCLUDE[crabout](../../../includes/crabout-md.md)]憑證的詳細資訊，請參閱[使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
    ```  
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
  
5.  設定用戶端時，設定 `behaviorConfiguration` 項目的 `<endpoint>` 屬性來指定行為，如下列程式碼所示。  端點元素是 [\<client\>](../../../docs/framework/configure-apps/file-schema/wcf/client.md) 元素的子系。  同時，將 `bindingConfiguration` 屬性設定為用戶端的繫結，以指定繫結組態的名稱。  如果您使用的是產生的組態檔，繫結名稱就會自動產生。  在這個範例中，名稱為 `"tcpBindingWithCredential"`。  
  
    ```  
    <client>  
      <endpoint name =""  
                address="net.tcp://contoso.com:8036/aloha"  
                binding="netTcpBinding"  
                bindingConfiguration="tcpBindingWithCredential"  
                behaviorConfiguration="endpointCredentialBehavior" />  
    </client>  
    ```  
  
## 請參閱  
 <xref:System.ServiceModel.NetTcpBinding>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A>   
 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential>   
 <xref:System.ServiceModel.ClientBase%601>   
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential>   
 [WCF 安全性程式設計](../../../docs/framework/wcf/feature-details/programming-wcf-security.md)   
 [選取認證類型](../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)   
 [ServiceModel 中繼資料公用程式工具 \(Svcutil.exe\)](../../../docs/framework/wcf/servicemodel-metadata-utility-tool-svcutil-exe.md)   
 [使用憑證](../../../docs/framework/wcf/feature-details/working-with-certificates.md)   
 [HOW TO：建立用戶端](../../../docs/framework/wcf/how-to-create-a-wcf-client.md)   
 [\<netTcpBinding\>](../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)   
 [\<安全性\>](../../../docs/framework/configure-apps/file-schema/wcf/security-of-nettcpbinding.md)   
 [\<訊息\>](../../../docs/framework/configure-apps/file-schema/wcf/message-element-of-nettcpbinding.md)   
 [\<行為\>](../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)   
 [\<行為\>](../../../docs/framework/configure-apps/file-schema/wcf/behaviors.md)   
 [\<clientCertificate\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcertificate-of-servicecredentials.md)   
 [\<clientCredentials\>](../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)