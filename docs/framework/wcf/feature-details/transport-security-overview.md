---
title: 傳輸安全性概觀
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
ms.assetid: 00959326-aa9d-44d0-af61-54933d4adc7f
ms.openlocfilehash: 04526e8aea09b412de4d3a94f17938b02ad6527b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61990793"
---
# <a name="transport-security-overview"></a>傳輸安全性概觀
Windows Communication Foundation (WCF) 中的傳輸安全性機制取決於繫結和傳輸而有所不同。 例如，使用 <xref:System.ServiceModel.WSHttpBinding> 類別時，傳輸為 HTTP，而保護此傳輸的主要機制則為 Secure Sockets Layer (SSL) over HTTP，通常稱為 HTTPS。 本主題討論 WCF 系統提供繫結中使用的主要傳輸安全性機制。  
  
> [!NOTE]
>  使用 SSL 安全性時使用.NET Framework 3.5 和更新版本的 WCF 用戶端會使用其憑證存放區中的中繼憑證和服務上執行憑證鏈結驗證的 SSL 交涉期間收到的中繼憑證憑證。 .NET Framework 3.0 只會使用安裝在本機憑證存放區中的中繼憑證。  
  
> [!WARNING]
>  使用傳輸安全性時，可能會覆寫 <xref:System.Threading.Thread.CurrentPrincipal%2A?displayProperty=nameWithType> 屬性。 若要防止發生組這<xref:System.ServiceModel.Description.ServiceAuthorizationBehavior.PrincipalPermissionMode%2A?displayProperty=nameWithType>至<xref:System.ServiceModel.Description.PrincipalPermissionMode.None?displayProperty=nameWithType>。 <xref:System.ServiceModel.Description.ServiceAuthorizationBehavior> 是可在服務描述上設定的服務行為。  
  
## <a name="basichttpbinding"></a>BasicHttpBinding  
 根據預設，<xref:System.ServiceModel.BasicHttpBinding> 類別不會提供安全性。 這個繫結是設計用來與未實作安全性的 Web 服務提供者互通。 不過，您可以透過將 <xref:System.ServiceModel.BasicHttpSecurity.Mode%2A> 屬性設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.None> 以外的任何值來啟動安全性。 若要啟用傳輸安全性，請將此屬性設為 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>。  
  
### <a name="interoperation-with-iis"></a>與 IIS 互通  
 <xref:System.ServiceModel.BasicHttpBinding> 類別主要用於與現有的 Web 服務互通，而這些服務當中有多數是由網際網路資訊服務 (IIS) 所裝載。 因此，這個繫結的傳輸安全性是設計成可用來與 IIS 站台進行流暢的互通。 將安全性模式設定為 <xref:System.ServiceModel.BasicHttpSecurityMode.Transport>，並接著設定用戶端認證類型，便可進行流暢的互通。 認證類型值會對應至 IIS 目錄安全性機制。 下列程式碼會示範所設定的模式以及設定為 Windows 的認證類型。 您可以在用戶端和伺服器都位於相同的 Windows 網域時使用這個組態。  
  
 [!code-csharp[c_ProgrammingSecurity#10](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#10)] 
 [!code-vb[c_ProgrammingSecurity#10](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#10)]  
  
 或者，使用下列組態：  
  
```xml  
<bindings>  
  <basicHttpBinding>  
    <binding name="SecurityByTransport">  
      <security mode="Transport">  
        <transport clientCredentialType="Windows" />  
       </security>  
     </binding>  
  </basicHttpBinding>  
</bindings>  
```  
  
 下列小節將討論其他的用戶端認證類型。  
  
#### <a name="basic"></a>基本  
 這種類型會對應至 IIS 中的基本驗證方法。 在使用此模式時，IIS 伺服器必須透過 Windows 使用者帳戶和適當的 NTFS 檔案系統權限進行設定。 如需詳細資訊[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，請參閱 <<c2> [ 啟用基本驗證及設定領域名稱](https://go.microsoft.com/fwlink/?LinkId=88592)。 如需詳細資訊[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，請參閱[IIS 7.0 Beta:設定基本驗證](https://go.microsoft.com/fwlink/?LinkId=88593)。  
  
#### <a name="certificate"></a>憑證  
 IIS 有一個會要求用戶端使用憑證登入的選項。 該功能也能讓 IIS 將用戶端憑證對應至 Windows 帳戶。 如需詳細資訊[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，請參閱 <<c2> [ 啟用 IIS 6.0 中的用戶端憑證](https://go.microsoft.com/fwlink/?LinkId=88594)。 如需詳細資訊[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，請參閱[IIS 7.0 Beta:在 IIS 7.0 中設定伺服器憑證](https://go.microsoft.com/fwlink/?LinkId=88595)。  
  
#### <a name="digest"></a>摘要  
 摘要式驗證類似於基本驗證，但是它具備以雜湊而非純文字形式來傳送認證的優點。 如需詳細資訊[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，請參閱 < [IIS 6.0 中的摘要式驗證](https://go.microsoft.com/fwlink/?LinkID=88443)。 如需詳細資訊[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，請參閱[IIS 7.0 Beta:設定摘要式驗證](https://go.microsoft.com/fwlink/?LinkId=88596)。  
  
#### <a name="windows"></a>Windows  
 這個類型會對應至 IIS 中的整合式 Windows 驗證。 當設定為這個值時，該伺服器必須出現在以 Kerberos 通訊協定做為網域控制站的 Windows 網域上。 如果伺服器未存在以 Kerberos 為基礎的網域中，或是如果 Kerberos 系統失敗，您可以使用下一節所介紹的 NT LAN Manager (NTLM) 值。 如需詳細資訊[!INCLUDE[iis601](../../../../includes/iis601-md.md)]，請參閱 < [IIS 6.0 中的整合式 Windows 驗證](https://go.microsoft.com/fwlink/?LinkId=88597)。 如需詳細資訊[!INCLUDE[iisver](../../../../includes/iisver-md.md)]，請參閱[IIS 7.0 Beta:在 IIS 7.0 中設定伺服器憑證](https://go.microsoft.com/fwlink/?LinkId=88595)。  
  
#### <a name="ntlm"></a>NTLM  
 這個類型可讓伺服器在 Kerberos 通訊協定失敗時，使用 NTLM 進行驗證。 如需有關中設定 IIS [!INCLUDE[iis601](../../../../includes/iis601-md.md)]，請參閱 <<c2> [ 強制 NTLM 驗證](https://go.microsoft.com/fwlink/?LinkId=88598)。 若是 [!INCLUDE[iisver](../../../../includes/iisver-md.md)]，Windows 驗證會包含 NTLM 驗證。 如需詳細資訊，請參閱[IIS 7.0 Beta:在 IIS 7.0 中設定伺服器憑證](https://go.microsoft.com/fwlink/?LinkID=88595)。  
  
## <a name="wshttpbinding"></a>WsHttpBinding  
 <xref:System.ServiceModel.WSHttpBinding> 類別主要是用來與實作 WS-* 規格的服務進行交互操作。 此繫結的傳輸安全性為使用 HTTP 或 HTTPS 的安全通訊端層 (SSL)。 若要建立使用 SSL 的 WCF 應用程式，使用 IIS 來裝載應用程式。 或者，如果您要建立自我裝載的應用程式，請使用 HttpCfg.exe 工具將 X.509 憑證繫結至電腦上的特定連接埠。 連接埠號碼指定為 WCF 應用程式的端點位址的一部分。 當使用傳輸模式時，端點位址必須包含 HTTPS 通訊協定，否則會在執行階段擲回例外狀況。 如需詳細資訊，請參閱 < [HTTP 傳輸安全性](../../../../docs/framework/wcf/feature-details/http-transport-security.md)。  
  
 若是用戶端驗證，請將 <xref:System.ServiceModel.HttpTransportSecurity.ClientCredentialType%2A> 類別的 <xref:System.ServiceModel.HttpTransportSecurity> 屬性設定為其中一個 <xref:System.ServiceModel.HttpClientCredentialType> 列舉值。 這些列舉值會與 <xref:System.ServiceModel.BasicHttpBinding> 的用戶端認證類型完全相同，而且是設計成與 IIS 服務進行裝載。  
  
 下列範例會示範要搭配 Windows 用戶端認證類型使用的繫結。  
  
 [!code-csharp[c_ProgrammingSecurity#11](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#11)]
 [!code-vb[c_ProgrammingSecurity#11](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#11)]  
  
## <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 這個繫結只會提供訊息層級安全性，而不提供傳輸層級安全性。  
  
## <a name="nettcpbinding"></a>NetTcpBinding  
 <xref:System.ServiceModel.NetTcpBinding> 類別會使用 TCP 來進行訊息傳輸。 傳輸模式的安全性是由實作透過 TCP 的傳輸層安全性 (TLS) 所提供。 而 TLS 實作則是由作業系統提供。  
  
 如下列程式碼所示，您也可以藉由將 <xref:System.ServiceModel.TcpTransportSecurity.ClientCredentialType%2A> 類別的 <xref:System.ServiceModel.TcpTransportSecurity> 屬性設定為其中一個 <xref:System.ServiceModel.TcpClientCredentialType> 值，來指定用戶端的認證類型。  
  
 [!code-csharp[c_ProgrammingSecurity#12](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#12)]
 [!code-vb[c_ProgrammingSecurity#12](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#12)]  
  
#### <a name="client"></a>用戶端  
 若是使用用戶端類型，您必須指定使用 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> 類別之 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential> 方法的憑證。  
  
> [!NOTE]
>  如果是使用 Windows 安全性，就不需要提供憑證。  
  
 下列程式碼範例使用可以提供唯一識別該憑證的憑證指紋。 如需憑證的詳細資訊，請參閱[使用憑證](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)。  
  
 [!code-csharp[c_ProgrammingSecurity#13](../../../../samples/snippets/csharp/VS_Snippets_CFX/c_programmingsecurity/cs/source.cs#13)]
 [!code-vb[c_ProgrammingSecurity#13](../../../../samples/snippets/visualbasic/VS_Snippets_CFX/c_programmingsecurity/vb/source.vb#13)]  
  
 或者，在用戶端的組態中指定的憑證使用[ \<clientCredentials >](../../../../docs/framework/configure-apps/file-schema/wcf/clientcredentials.md)行為區段中的項目。  
  
```xml  
<behaviors>  
  <behavior>  
   <clientCredentials>  
     <clientCertificate findValue= "101010101010101010101010101010000000000"   
      storeLocation="LocalMachine" storeName="My"   
      X509FindType="FindByThumbPrint"/>  
     </clientCertificate>  
   </clientCredentials>  
 </behavior>  
</behaviors>    
```  
  
## <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 <xref:System.ServiceModel.NetNamedPipeBinding> 類別已設計成可進行有效率的電腦內部通訊，也就是說，它可以用在執行於同一電腦的處理序，雖然您也可以在同一網路中的兩台電腦之間建立具名管道通道。 這個繫結只能提供傳輸層級安全性。 當建立使用這個繫結的應用程式時，其端點位址必須包含 "net.pipe" 做為端點位址的通訊協定。  
  
## <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 使用傳輸安全性時，這個繫結會使用透過 HTTP 的 SSL (即所謂的 HTTPS) 和已發行的權杖 (<xref:System.ServiceModel.WSFederationHttpSecurityMode.TransportWithMessageCredential>)。 如需有關同盟的應用程式的詳細資訊，請參閱[聯合與發行權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。  
  
## <a name="netpeertcpbinding"></a>NetPeerTcpBinding  
 <xref:System.ServiceModel.NetPeerTcpBinding> 類別是設計成可使用對等網路功能來進行有效通訊的安全傳輸。 從類別和繫結名稱可看出，TCP 是一種通訊協定。 當安全性模式設定為傳輸時，繫結會透過 TCP 實作 TLS。 如需端對端功能的詳細資訊，請參閱[對等網路](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## <a name="msmqintegrationbinding-and-netmsmqbinding"></a>MsmqIntegrationBinding 和 NetMsmqBinding  
 如需傳輸的完整討論安全性與訊息佇列 （先前稱為 MSMQ），請參閱[保護訊息使用傳輸安全性](../../../../docs/framework/wcf/feature-details/securing-messages-using-transport-security.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF 安全性程式設計](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)
