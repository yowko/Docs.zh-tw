---
title: HOW TO：使用傳輸安全性和訊息認證
description: 瞭解如何使用訊息認證來執行傳輸安全性，以在 WCF 中提供最佳的傳輸和訊息安全性模式。
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TransportWithMessageCredentials
ms.assetid: 6cc35346-c37a-4859-b82b-946c0ba6e68f
ms.openlocfilehash: f632a4389eafc155cedcae94707c9418b6696f2c
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/23/2020
ms.locfileid: "85246645"
---
# <a name="how-to-use-transport-security-and-message-credentials"></a>HOW TO：使用傳輸安全性和訊息認證
使用傳輸和訊息認證來保護服務的安全，會在 Windows Communication Foundation （WCF）中使用傳輸和訊息安全性模式的最佳選擇。 簡單地說，傳輸層安全性可提供完整性與機密性，而訊息層安全性則提供各種在嚴格的傳輸安全性機制中不可能提供的認證。 本主題將說明使用 <xref:System.ServiceModel.WSHttpBinding> 和 <xref:System.ServiceModel.NetTcpBinding> 繫結，以訊息認證來實作傳輸時的基本步驟。 如需設定安全性模式的詳細資訊，請參閱[如何：設定安全性模式](../how-to-set-the-security-mode.md)。  
  
 當您將安全性模式設為 `TransportWithMessageCredential` 時，傳輸會決定用來提供傳輸層安全性的實際機制。 對 HTTP 來說，此機制為 Secure Sockets Layer (SSL) over HTTP (HTTPS)；對 TCP 來說，此機制是 SSL over TCP 或 Windows 安全性。  
  
 如果傳輸機制為 HTTP (使用 <xref:System.ServiceModel.WSHttpBinding>)，則 SSL over HTTP 會提供傳輸層級的安全性。 在此情況下，您必須設定電腦使用繫結至連接埠的 SSL 憑證來裝載服務 (如本主題稍後所示)。  
  
 如果傳輸機制為 TCP (使用 <xref:System.ServiceModel.NetTcpBinding>)，則預設會提供的傳輸層安全性便是 Windows 安全性或 SSL over TCP。 一旦使用 SSL over TCP，您必須使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 方法來指定憑證 (如本主題稍後所示)。  
  
### <a name="to-use-the-wshttpbinding-with-a-certificate-for-transport-security-in-code"></a>若要使用 WSHttpBinding 搭配憑證來獲得傳輸安全性 (透過程式碼)  
  
1. 請使用 HttpCfg.exe 工具，將 SSL 憑證繫結至電腦的連接埠。 如需詳細資訊，請參閱[如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)。  
  
2. 建立 <xref:System.ServiceModel.WSHttpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.WSHttpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。  
  
3. 將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 屬性設定為適當值。 （如需詳細資訊，請參閱[選取認證類型](selecting-a-credential-type.md)。）下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。  
  
4. 使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體 請注意，位址必須使用 "HTTPS" 配置，而且必須包含電腦的實際名稱，以及 SSL 憑證所繫結的連接埠號碼。 (另外，您也可以在組態中設定基底位址)。  
  
5. 使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。  
  
6. 如下列程式碼所示，建立 <xref:System.ServiceModel.ServiceHost> 的執行個體並呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法。  
  
     [!code-csharp[c_SettingSecurityMode#7](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#7)]
     [!code-vb[c_SettingSecurityMode#7](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#7)]  
  
### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security-in-code"></a>若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性 (透過程式碼)  
  
1. 建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。  
  
2. 將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。 下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。  
  
3. 使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體 請注意，位址必須使用 "net.tcp" 配置。 (另外，您也可以在組態中設定基底位址)。  
  
4. 建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。  
  
5. 使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，明確設定服務的 X.509 憑證。  
  
6. 使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。  
  
7. 呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。  
  
     [!code-csharp[c_SettingSecurityMode#8](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#8)]
     [!code-vb[c_SettingSecurityMode#8](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#8)]  
  
### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security-in-code"></a>若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性 (透過程式碼)  
  
1. 建立 <xref:System.ServiceModel.NetTcpBinding> 類別的執行個體，並將 <xref:System.ServiceModel.NetTcpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.SecurityMode.TransportWithMessageCredential>。  
  
2. 將 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 設定為 <xref:System.ServiceModel.TcpClientCredentialType.Windows>，藉此將傳輸安全性設定為使用 Windows  (請注意，此設定為預設值)。  
  
3. 將 <xref:System.ServiceModel.MessageSecurityOverTcp.ClientCredentialType%2A> 設定為適當值。 下列程式碼會使用 <xref:System.ServiceModel.MessageCredentialType.Certificate> 值。  
  
4. 使用適當的基底位址，建立 <xref:System.Uri> 類別的執行個體 請注意，位址必須使用 "net.tcp" 配置。 (另外，您也可以在組態中設定基底位址)。  
  
5. 建立 <xref:System.ServiceModel.ServiceHost> 類別的執行個體。  
  
6. 使用 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential.SetCertificate%2A> 類別的 <xref:System.ServiceModel.Security.X509CertificateRecipientServiceCredential> 方法，明確設定服務的 X.509 憑證。  
  
7. 使用 <xref:System.ServiceModel.ServiceHost.AddServiceEndpoint%2A> 方法新增服務端點。  
  
8. 呼叫 <xref:System.ServiceModel.ICommunicationObject.Open%2A> 方法，如下列程式碼所示。  
  
     [!code-csharp[c_SettingSecurityMode#9](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_settingsecuritymode/cs/source.cs#9)]
     [!code-vb[c_SettingSecurityMode#9](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_settingsecuritymode/vb/source.vb#9)]  
  
## <a name="using-configuration"></a>使用組態  
  
#### <a name="to-use-the-wshttpbinding"></a>若要使用 WSHttpBinding  
  
1. 使用繫結至連接埠的 SSL 憑證來設定電腦  （如需詳細資訊，請參閱[如何：使用 SSL 憑證設定埠](how-to-configure-a-port-with-an-ssl-certificate.md)）。 您不需要使用此設定來設定 <`transport`> 元素值。  
  
2. 指定訊息層級安全性的用戶端認證類型。 下列範例會將 `clientCredentialType` <> 元素的屬性設定 `message` 為 `UserName` 。  
  
    ```xml  
    <wsHttpBinding>  
    <binding name="WsHttpBinding_ICalculator">  
            <security mode="TransportWithMessageCredential" >  
               <message clientCredentialType="UserName" />  
            </security>  
    </binding>  
    </wsHttpBinding>  
    ```  
  
#### <a name="to-use-the-nettcpbinding-with-a-certificate-for-transport-security"></a>若要使用 NetTcpBinding 搭配憑證來獲得傳輸安全性  
  
1. 如果要使用 SSL over TCP，您必須在 `<behaviors>` 項目中明確指定憑證。 下列範例會在預設的存放區位置中 (本機電腦與個人存放區)，按照憑證簽發者指定憑證。  
  
    ```xml  
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
  
2. 將加入 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 至系結區段  
  
3. 新增繫結項目，然後將 `name` 屬性設定為適當值。  
  
4. 新增 <`security`> 元素，並將屬性設定 `mode` 為 `TransportWithMessageCredential` 。  
  
5. 新增 <`message>` 元素，並將屬性設定 `clientCredentialType` 為適當的值。  
  
    ```xml  
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
  
#### <a name="to-use-the-nettcpbinding-with-windows-for-transport-security"></a>若要使用 NetTcpBinding 搭配 Windows 來獲得傳輸安全性  
  
1. 將加入 [\<netTcpBinding>](../../configure-apps/file-schema/wcf/nettcpbinding.md) 至系結區段，  
  
2. 新增 <`binding`> 元素，並將 `name` 屬性設定為適當的值。  
  
3. 新增 <`security`> 元素，並將屬性設定 `mode` 為 `TransportWithMessageCredential` 。  
  
4. 新增 <`transport`> 元素，並將 `clientCredentialType` 屬性設定為 `Windows` 。  
  
5. 新增 <`message`> 元素，並將 `clientCredentialType` 屬性設定為適當的值。 下列程式碼會設定憑證的值。  
  
    ```xml  
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
  
## <a name="see-also"></a>另請參閱

- [如何：設定安全性模式](../how-to-set-the-security-mode.md)
- [保護服務安全](../securing-services.md)
- [Securing Services and Clients](securing-services-and-clients.md)
