---
title: "HOW TO：使用傳輸安全性和訊息認證 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework-4.6"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
helpviewer_keywords: 
  - "TransportWithMessageCredentials"
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
caps.latest.revision: 11
author: "BrucePerlerMS"
ms.author: "bruceper"
manager: "mbaldwin"
caps.handback.revision: 11
---
# HOW TO：使用傳輸安全性和訊息認證
同時使用傳輸與訊息認證來保護服務的安全時，需要在 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中同時運用最佳的傳輸與訊息安全性模式。簡單地說，傳輸層安全性可提供完整性與機密性，而訊息層安全性則提供各種在嚴格的傳輸安全性機制中不可能提供的認證。本主題將說明使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 繫結並使用訊息認證來實作傳輸時的基本步驟。[!INCLUDE[crabout](../../../../includes/crabout-md.md)]設定安全性模式的詳細資訊，請參閱 [HOW TO：設定安全性模式](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)。  
  
 當您將安全性模式設定為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。對 HTTP 來說，此機制為 Secure Sockets Layer \(SSL\) over HTTP \(HTTPS\)；對 TCP 來說，此機制是 SSL over TCP 或 Windows 安全性。  
  
 如果傳輸機制為 HTTP \(使用 <xref:System.ServiceModel.WSHttpBinding>\)，則 SSL over HTTP 會提供傳輸層級的安全性。在此情況下，您必須設定電腦使用繫結至連接埠的 SSL 憑證來裝載服務 \(如本主題稍後所示\)。  
  
 如果傳輸機制為 TCP \(使用 <xref:System.ServiceModel.NetTcpBinding>\)，則預設會提供的傳輸層安全性便是 Windows 安全性或 SSL over TCP。一旦使用 SSL over TCP，您必須使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法來指定憑證 \(如本主題稍後所示\)。  
  
### 若要使用 WSHttpBinding 搭配憑證來獲得傳輸安全性 \(透過程式碼\)  
  
1.  請使用 HttpCfg.exe 工具，將 SSL 憑證繫結至電腦的連接埠。[!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HOW TO：使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md).  
  
2.  建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode>。  
  
3.  將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 屬性設定為適當值。\([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][選取認證類型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md).\)下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType> 值。  
  
4.  使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體請注意，位址必須使用 "HTTPS" 配置，而且必須包含電腦的實際名稱，以及 SSL 憑證所繫結的連接埠號碼。\(另外，您也可以在組態中設定基底位址\)。  
  
5.  使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。  
  
6.  如下列程式碼所示，建立 <xref:System.ServiceModel.ServiceHost> 的執行個體並呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### 若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性 \(透過程式碼\)  
  
1.  建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode>。  
  
2.  將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType> 值。  
  
3.  使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體請注意，位址必須使用 "net.tcp" 配置。\(另外，您也可以在組態中設定基底位址\)。  
  
4.  建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。  
  
5.  使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法，明確設定服務的 X.509 憑證。  
  
6.  使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。  
  
7.  如下列程式碼所示，呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### 若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性 \(透過程式碼\)  
  
1.  建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode>。  
  
2.  將 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 設定為 <xref:System.ServiceModel.TcpClientCredentialType>，藉此將傳輸安全性設定為使用 Windows \(請注意，此設定為預設值\)。  
  
3.  將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType> 值。  
  
4.  使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體請注意，位址必須使用 "net.tcp" 配置。\(另外，您也可以在組態中設定基底位址\)。  
  
5.  建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。  
  
6.  使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法，明確設定服務的 X.509 憑證。  
  
7.  使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。  
  
8.  呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## 使用組態  
  
#### 若要使用 WSHttpBinding  
  
1.  使用繫結至連接埠的 SSL 憑證來設定電腦 \([!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][HOW TO：使用 SSL 憑證設定連接埠](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)\).您不需要使用此組態來設定 \<`transport`\> 項目值。  
  
2.  指定訊息層級安全性的用戶端認證類型。下列範例會將 \<`message`\> 項目的 `clientCredentialType` 屬性設定為 `UserName`。  
  
    ```  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### 若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性  
  
1.  如果要使用 SSL over TCP，您必須在 `<behaviors>` 項目中明確指定憑證。下列範例會在預設的存放區位置中 \(本機電腦與個人存放區\)，按照憑證簽發者指定憑證。  
  
    ```  
    <behaviors>  
     <serviceBehaviors>  
       <behavior name="mySvcBehavior">  
           <serviceCredentials>  
             <serviceCertificate findValue="contoso.com"  
                                 x509FindType="FindByIssuerName" />  
           </serviceCredentials>  
       </behavior>  
     </serviceBehaviors>  
    </behaviors>  
    ```  
  
2.  將 [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) 新增至繫結區段。  
  
3.  新增繫結項目，然後將 `name` 屬性設定為適當值。  
  
4.  新增 \<`security`\> 項目，然後將 `mode` 屬性設定為 `TransportWithMessageCredential`。  
  
5.  新增 \<`message>` 項目，並將 `clientCredentialType` 屬性設定為適當值。  
  
    ```  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <message clientCredentialType="Windows" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
    ```  
  
#### 若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性  
  
1.  將 [\<netTcpBinding\>](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md) 新增至繫結區段。  
  
2.  新增 \<`binding`\> 項目，並將 `name` 屬性設定為適當值。  
  
3.  新增 \<`security`\> 項目，然後將 `mode` 屬性設定為 `TransportWithMessageCredential`。  
  
4.  新增 \<`transport`\> 項目，然後將 `clientCredentialType` 屬性設定為 `Windows`。  
  
5.  新增 \<`message`\> 項目，並將 `clientCredentialType` 屬性設定為適當值。下列程式碼會設定憑證的值。  
  
    ```  
    <bindings>  
    <netTcpBinding>  
      <binding name="myTcpBinding">  
        <security mode="TransportWithMessageCredential" >  
           <transport clientCredentialType="Windows" />  
           <message clientCredentialType="Certificate" />  
        </security>  
      </binding>  
    </netTcpBinding>  
    </bindings>  
  
    ```  
  
## 請參閱  
 [HOW TO：設定安全性模式](../../../../docs/framework/wcf/how-to-set-the-security-mode.md)   
 [保護服務的安全](../../../../docs/framework/wcf/securing-services.md)   
 [確保服務與用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)