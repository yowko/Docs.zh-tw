---
title: 繫結和安全性
ms.date: 03/30/2017
helpviewer_keywords:
- bindings [WCF], security
- WCF security
- Windows Communication Foundation, security
- bindings [WCF]
ms.assetid: 4de03dd3-968a-4e65-af43-516e903d7f95
author: BrucePerlerMS
ms.openlocfilehash: 904ea64bd6e76e7bf99aa4a31ef752bfb2760c23
ms.sourcegitcommit: fb78d8abbdb87144a3872cf154930157090dd933
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/26/2018
ms.locfileid: "47198458"
---
# <a name="bindings-and-security"></a>繫結和安全性
包含與 Windows Communication Foundation (WCF) 的系統提供繫結會提供程式 WCF 應用程式的快速方法。 除了一個例外狀況以外，所有繫結預設都會啟用安全性配置。 本主題將根據您的安全性需求，協助您選取正確的繫結。  
  
 如需 WCF 安全性的概觀，請參閱 <<c0> [ 安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)。 如需程式設計使用繫結的 WCF 的詳細資訊，請參閱[Programming WCF 安全性](../../../../docs/framework/wcf/feature-details/programming-wcf-security.md)。  
  
 如果您已經選取繫結，您可以深入了解與安全性相關聯的執行階段行為[安全性行為](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)。  
  
 某些安全性功能無法使用系統提供的繫結進行程式設計。 如需使用自訂繫結的控制項，請參閱 <<c0> [ 自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)。  
  
## <a name="security-functions-of-bindings"></a>繫結的安全性功能  
 WCF 包含一些滿足大多數需求的系統提供繫結。 如果特定繫結不敷使用，您也可以建立自訂繫結。 如需系統提供繫結的清單，請參閱 < [System-Provided Bindings](../../../../docs/framework/wcf/system-provided-bindings.md)。 如需有關自訂繫結的詳細資訊，請參閱 <<c0> [ 自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
 在 WCF 中的每個繫結有兩種形式： 為 API，以及使用組態檔中的 XML 項目。 例如， `WSHttpBinding` (API) 中有對應[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。  
  
 下列章節將列出每個繫結的兩種型式，並摘要說明其安全功能。  
  
### <a name="basichttp"></a>BasicHttp  
 在程式碼，使用<xref:System.ServiceModel.BasicHttpBinding>類別; 在組態中，使用[ \<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)。  
  
 這個繫結是設計用來與一系列現有技術搭配使用的，包括下列各項：  
  
-   ASP.NET Web 服務 (ASMX) 第 1 版。  
  
-   Web Service Enhancements (WSE) 應用程式。  
  
-   基本設定檔中的 Web 服務互通性所定義 (WS-我) 規格 ([https://go.microsoft.com/fwlink/?LinkId=38955](https://go.microsoft.com/fwlink/?LinkId=38955))。  
  
-   如 WS-I 中定義的 Basic Security Profile。  
  
 根據預設，這個繫結是不安全的。 它是針對與 ASMX 服務相互操作所設計的。 啟用安全性時，繫結是設計成可用來與 Internet Information Services (IIS) 安全性機制進行順暢互通的，例如：基本的驗證、摘要和整合式 Windows 安全性。 如需詳細資訊，請參閱 <<c0> [ 傳輸安全性概觀](../../../../docs/framework/wcf/feature-details/transport-security-overview.md)。 這個繫結支援下列各項：  
  
-   HTTPS 傳輸安全性。  
  
-   HTTP 基本驗證。  
  
-   WS-Security。  
  
 如需詳細資訊，請參閱<xref:System.ServiceModel.BasicHttpSecurity>, <xref:System.ServiceModel.BasicHttpMessageSecurity>, <xref:System.ServiceModel.BasicHttpMessageCredentialType>和<xref:System.ServiceModel.BasicHttpSecurityMode>.  
  
### <a name="wshttpbinding"></a>WSHttpBinding  
 在程式碼，使用<xref:System.ServiceModel.WSHttpBinding>類別; 在組態中，使用[ \<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)。  
  
 根據預設，這個繫結會實作 WS-Security 規格，並提供與實作 WS-* 規格之服務的互通性。 它支援下列各項：  
  
-   HTTPS 傳輸安全性。  
  
-   WS-Security。  
  
-   用於驗證呼叫者的 HTTPS 傳輸保護 (具 SOAP 訊息認證安全性)。  
  
 如需詳細資訊，請參閱 < <xref:System.ServiceModel.WSHttpSecurity>， <xref:System.ServiceModel.MessageSecurityOverHttp>， <xref:System.ServiceModel.MessageCredentialType>， <xref:System.ServiceModel.SecurityMode>， <xref:System.ServiceModel.HttpTransportSecurity>， <xref:System.ServiceModel.HttpClientCredentialType>，和<xref:System.ServiceModel.HttpProxyCredentialType>。  
  
### <a name="wsdualhttpbinding"></a>WSDualHttpBinding  
 在程式碼，使用<xref:System.ServiceModel.WSDualHttpBinding>類別; 在組態中，使用[ \<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)。  
  
 這個繫結設計的目的，是為了要提供雙工服務應用程式。 這個繫結實作了 WS-Security 規格，以提供訊息傳輸安全性。 傳輸安全性在此無法使用。 根據預設，這個繫結提供了下列功能：  
  
-   實作 WS-Reliable 訊息以提供可靠性。  
  
-   實作 WS-Security 以提供傳輸安全性和驗證。  
  
-   使用 HTTP 傳遞訊息。  
  
-   使用 text/XML 訊息編碼。  
  
 使用 WS-Security (訊息層安全性) 時，繫結可讓您設定下列參數：  
  
-   安全性演算法組合，用於判斷密碼編譯演算法。  
  
-   可供下列項目運用的繫結選項：  
  
    -   經由超出範圍的方式，提供可在用戶端使用的服務認證。  
  
    -   提供通道設定期間之服務交涉的服務認證。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceModel.WSDualHttpSecurity> 與 <xref:System.ServiceModel.WSDualHttpSecurityMode>。  
  
### <a name="nettcpbinding"></a>NetTcpBinding  
 在程式碼，使用<xref:System.ServiceModel.NetTcpBinding>類別; 在組態中，使用[ \<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)。  
  
 這個繫結已針對跨電腦通訊進行最佳化。 根據預設，這個繫結具有下列特性：  
  
-   實作傳輸層安全性。  
  
-   以 Windows 安全性提供傳輸安全性和驗證。  
  
-   使用 TCP 進行傳輸。  
  
-   實作二進位訊息編碼。  
  
-   實作 WS-Reliable 訊息。  
  
 包括下列選項：  
  
-   訊息層安全性 (使用 WS-Security)。  
  
-   使用訊息認證的傳輸安全性，其機密性和完整性是由透過 TCP 之上的傳輸層安全性 (TLS) 所提供，而授權的認證則是由 WS-Security 提供。  
  
 如需詳細資訊，請參閱 < <xref:System.ServiceModel.NetTcpSecurity>， <xref:System.ServiceModel.TcpTransportSecurity>， <xref:System.ServiceModel.TcpClientCredentialType>， <xref:System.ServiceModel.MessageSecurityOverTcp>，和<xref:System.ServiceModel.MessageCredentialType>。  
  
### <a name="netnamedpipebinding"></a>NetNamedPipeBinding  
 在程式碼，使用<xref:System.ServiceModel.NetNamedPipeBinding>類別; 在組態中，使用[ \<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)。  
  
 這個繫結已針對跨處理序通訊進行最佳化 (通常是在同一部電腦上)。 根據預設，這個繫結具有下列特性：  
  
-   使用傳輸安全性進行訊息傳輸和驗證。  
  
-   使用具名管道 (Named Pipe) 傳遞訊息。  
  
-   實作二進位訊息編碼。  
  
-   加密和訊息簽署。  
  
 包括下列選項：  
  
-   使用 Windows 安全性進行驗證。  
  
 如需詳細資訊，請參閱<xref:System.ServiceModel.NetNamedPipeSecurity>、<xref:System.ServiceModel.NetNamedPipeSecurityMode>和<xref:System.ServiceModel.NamedPipeTransportSecurity>。  
  
### <a name="msmqintegrationbinding"></a>MsmqIntegrationBinding  
 在程式碼，使用<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>類別; 在組態中，使用[ \<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)。  
  
 這個繫結最適合使用非 WCF Microsoft 訊息佇列 MSMQ 端點建立 WCF 用戶端和服務相互操作。  
  
 根據預設，這個繫結會使用傳輸安全性，並提供下列安全性特性：  
  
-   可以停用安全性 (無)。  
  
-   MSMQ 傳輸安全性 (傳輸)。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceModel.NetMsmqSecurity> 與 <xref:System.ServiceModel.NetMsmqSecurityMode>。  
  
### <a name="netmsmqbinding"></a>NetMsmqBinding  
 在程式碼，使用<xref:System.ServiceModel.NetMsmqBinding>類別; 在組態中，使用[ \<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)。  
  
 這個繫結是用於建立 WCF 服務需要 MSMQ 佇列訊息支援。  
  
 根據預設，這個繫結會使用傳輸安全性，並提供下列安全性特性：  
  
-   可以停用安全性 (無)。  
  
-   MSMQ 傳輸安全性 (傳輸)。  
  
-   SOAP 訊息安全性 (訊息)。  
  
-   同時具有傳輸和訊息安全性 (兩者並存)。  
  
-   支援的用戶端認證類型：無、Windows、UserName、憑證、IssuedToken。  
  
 只有在將安全性模式設定為 <xref:System.ServiceModel.MessageCredentialType.Certificate> 或 <xref:System.ServiceModel.NetMsmqSecurityMode.Both> 時，才會支援 <xref:System.ServiceModel.NetMsmqSecurityMode.Message> 認證。  
  
 如需詳細資訊，請參閱 <xref:System.ServiceModel.MessageSecurityOverMsmq> 與 <xref:System.ServiceModel.MsmqTransportSecurity>。  
  
### <a name="wsfederationhttpbinding"></a>WSFederationHttpBinding  
 在程式碼，使用<xref:System.ServiceModel.WSFederationHttpBinding>類別; 在組態中，使用[ \<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)。  
  
 根據預設，這個繫結會使用 WS-Security (訊息層安全性)。  
  
 如需詳細資訊，請參閱 <<c0> [ 同盟](../../../../docs/framework/wcf/feature-details/federation.md)， <xref:System.ServiceModel.WSFederationHttpSecurity>，和<xref:System.ServiceModel.WSFederationHttpSecurityMode>。  
  
## <a name="custom-bindings"></a>自訂繫結  
 如果系統提供的繫結程序都不符合您的需求，您可以以自訂的安全性繫結程序項目建立自訂繫結程序。 如需詳細資訊，請參閱 <<c0> [ 自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)。  
  
## <a name="binding-choices"></a>繫結選擇  
 下表摘要說明了安全性模式設定中提供的功能，也就是說，列出了當安全性模式設定為 `Transport`、`Message` 或 `TransportWithMessageCredential` 時可以使用的功能。 此表可協助您找出應用程式所需的安全性功能。  
  
|設定|功能|  
|-------------|--------------|  
|Transport|伺服器驗證<br /><br /> 用戶端驗證<br /><br /> 點對點安全性<br /><br /> 互通性<br /><br /> 硬體加速<br /><br /> 高輸送量<br /><br /> 安全的防火牆<br /><br /> 高延遲的應用程式<br /><br /> 多個躍點間重新加密|  
|訊息|伺服器驗證<br /><br /> 用戶端驗證<br /><br /> 端對端安全性<br /><br /> 互通性<br /><br /> 豐富的宣告<br /><br /> 同盟<br /><br /> 多重要素驗證<br /><br /> 自訂權杖<br /><br /> 公證/時間戳記服務<br /><br /> 高延遲的應用程式<br /><br /> 訊息簽章的持續性|  
|TransportWithMessageCredential|伺服器驗證<br /><br /> 用戶端驗證<br /><br /> 點對點安全性<br /><br /> 互通性<br /><br /> 硬體加速<br /><br /> 高輸送量<br /><br /> 豐富的用戶端宣告<br /><br /> 同盟<br /><br /> 多重要素驗證<br /><br /> 自訂權杖<br /><br /> 安全的防火牆<br /><br /> 高延遲的應用程式<br /><br /> 多個躍點間重新加密|  
  
 下表列出支援各種模式設定的繫結。 您可以從表格中選取一種繫結，以便用來建立您的服務端點。  
  
|繫結|傳輸模式支援|訊息模式支援|TransportWithMessageCredential 支援|  
|-------------|----------------------------|--------------------------|--------------------------------------------|  
|`BasicHttpBinding`|是|是|是|  
|`WSHttpBinding`|是|是|是|  
|`WSDualHttpBinding`|否|是|否|  
|`NetTcpBinding`|是|是|是|  
|`NetNamedPipeBinding`|是|否|否|  
|`NetMsmqBinding`|是|是|否|  
|`MsmqIntegrationBinding`|是|否|否|  
|`wsFederationHttpBinding`|否|是|是|  
  
## <a name="transport-credentials-in-bindings"></a>繫結中的傳輸認證  
 下表列出在傳輸安全性模式中使用 `BasicHttpBinding` 或 `WSHttpBinding` 時，可以使用的用戶端認證類型。  
  
|類型|描述|  
|----------|-----------------|  
|無|指定用戶端不需要提出任何認證。 這會轉譯成匿名用戶端。|  
|基本|基本驗證。 如需詳細資訊，請參閱 RFC 2617 – HTTP 驗證： 基本與摘要式驗證，網址[ https://go.microsoft.com/fwlink/?LinkId=84023 ](https://go.microsoft.com/fwlink/?LinkId=84023)。|  
|摘要|摘要式驗證。 如需詳細資訊，請參閱 RFC 2617 – HTTP 驗證： 基本與摘要式驗證，網址[ https://go.microsoft.com/fwlink/?LinkId=84023 ](https://go.microsoft.com/fwlink/?LinkId=84023)。|  
|NTLM|NT LAN Manager (NTLM) 驗證。|  
|Windows|Windows 驗證。|  
|憑證|使用憑證執行的驗證。|  
|IssuedToken|允許服務要求用戶端必須以安全性權杖服務或 [!INCLUDE[infocard](../../../../includes/infocard-md.md)] 所發出的權杖進行驗證。 如需詳細資訊，請參閱 <<c0> [ 聯合與發行權杖](../../../../docs/framework/wcf/feature-details/federation-and-issued-tokens.md)。|  
  
### <a name="message-client-credentials-in-bindings"></a>繫結中的訊息用戶端認證  
 下表列出在訊息安全性模式中使用繫結時，可以使用的用戶端認證類型。  
  
|類型|描述|  
|----------|-----------------|  
|無|允許服務與匿名用戶端互動。|  
|Windows|允許在 Windows 認證的已驗證內容中進行 SOAP 訊息交換。|  
|使用者名稱|允許服務要求用戶端必須以使用者名稱認證進行驗證。 請注意，當安全性模式設定為`TransportWithMessageCredential`，WCF 不支援傳送密碼摘要或衍生的金鑰使用的密碼，並使用訊息模式安全性這類金鑰。 因此，WCF 會強制使用使用者名稱認證時，保護傳輸。|  
|憑證|允許服務要求用戶端使用憑證進行驗證。|  
|IssuedToken|允許服務使用安全性權杖服務提供自訂權杖。|  
  
## <a name="see-also"></a>另請參閱  
 [安全性概觀](../../../../docs/framework/wcf/feature-details/security-overview.md)  
 [保護服務和用戶端的安全](../../../../docs/framework/wcf/feature-details/securing-services-and-clients.md)  
 [選取認證類型](../../../../docs/framework/wcf/feature-details/selecting-a-credential-type.md)  
 [自訂繫結的安全性功能](../../../../docs/framework/wcf/feature-details/security-capabilities-with-custom-bindings.md)  
 [安全性行為](../../../../docs/framework/wcf/feature-details/security-behaviors-in-wcf.md)  
 [Windows Server App Fabric 的安全性模型](https://go.microsoft.com/fwlink/?LinkID=201279&clcid=0x409)
