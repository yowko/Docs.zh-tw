---
title: 系統提供的繫結
description: 深入了解系統提供的所有 Windows Communication Foundation (WCF) 繫結。
ms.date: 06/05/2018
helpviewer_keywords:
- bindings [WCF], system-provided
ms.assetid: 2c243746-45ce-4588-995e-c17126a579a6
ms.openlocfilehash: 3c6c6b628d208aede8c547dcfa66fc189a26ae01
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/23/2019
ms.locfileid: "54569596"
---
# <a name="system-provided-bindings"></a>系統提供的繫結

在與端點對話時，繫結會指定要使用的通訊機制，並指出如何連接至端點。 繫結包含下列項目：

- 對於傳送至端點的訊息來說，通訊協定堆疊決定了要使用的安全性、可靠性，與內容流量設定。

- 傳輸則決定了在傳送訊息給端點時要使用的基礎傳輸通訊協定，例如 TCP 或 HTTP。

- 編碼會決定用來傳送到端點之訊息的 Wire 編碼。 例如，文字/XML、二進位或訊息傳輸最佳化機制 (MTOM)。

 本文提供所有系統提供的 Windows Communication Foundation (WCF) 繫結。 如果這些繫結都無法完全符合您的應用程式準則，您可以建立自訂繫結。 如需建立自訂繫結的詳細資訊，請參閱[自訂繫結](./extending/custom-bindings.md)。

 一個安全、互通，且可支援 WS-Federation 通訊協定的繫結，此繫結可讓聯合組織有效率地驗證並授權使用者。

> [!IMPORTANT]
> 請務必選取包含安全性的繫結。 根據預設，除了 [\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md) 項目之外，所有繫結都會啟用安全性。 如果您沒有選取安全繫結程序或是停用了安全性，請記得透過某種方式來保護您的資料，例如儲存在安全的資料中心或是另外放在隔離的網路上。

> [!IMPORTANT]
> 請勿使用不支援或已停用安全性的繫結來搭配雙工合約一起使用，除非您能夠以其他方式來保護資料的安全。

下列繫結會隨附於 WCF：

|繫結|組態項目|描述|
|-------------|---------------------------|-----------------|
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding>](../configure-apps/file-schema/wcf/basichttpbinding.md)|適合用來與 WS-Basic Profile 相容之 Web 服務通訊的繫結；例如，以 ASP.NET Web 服務 (ASMX) 為基礎的服務。 此繫結使用 HTTP 做為傳輸，並使用文字/XML 做為預設的訊息編碼。|
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding>](../configure-apps/file-schema/wcf/wshttpbinding.md)|適用在非雙工服務合約上的安全且互通的繫結。|
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding>](../configure-apps/file-schema/wcf/wsdualhttpbinding.md)|安全且互通的繫結，適用於雙工服務合約或透過 SOAP 媒介的通訊。|
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding>](../configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|安全、互通且支援 WS-Federation 通訊協定的繫結，此繫結可讓聯合組織有效率地驗證並授權使用者。|
|<xref:System.ServiceModel.NetHttpBinding>|[\<netHttpBinding>](../configure-apps/file-schema/wcf/nethttpbinding.md)|為了使用 HTTP 或 WebSocket 服務而設計的繫結，其預設會使用二進位編碼。|
|<xref:System.ServiceModel.NetHttpsBinding>|[\<netHttpsBinding>](../configure-apps/file-schema/wcf/nethttpsbinding.md)|為了使用 HTTP 或 WebSocket 服務而設計的安全繫結，其預設會採用二進位編碼。|
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding>](../configure-apps/file-schema/wcf/nettcpbinding.md)|安全且最佳化的繫結，適用於 WCF 應用程式之間的跨電腦通訊。|
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding>](../configure-apps/file-schema/wcf/netnamedpipebinding.md)|安全、可靠且最佳化的繫結，適用於 WCF 應用程式之間的電腦通訊。|
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding>](../configure-apps/file-schema/wcf/netmsmqbinding.md)|佇列繫結，適用於 WCF 應用程式之間的跨電腦通訊。|
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding>](../configure-apps/file-schema/wcf/netpeertcpbinding.md)|可啟用安全、多電腦通訊的繫結。|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding>](../configure-apps/file-schema/wcf/msmqintegrationbinding.md)|一種適用於 WCF 應用程式與現有訊息佇列應用程式之間的跨電腦通訊之繫結。|
|<xref:System.ServiceModel.BasicHttpContextBinding>|[\<basicHttpContextBinding>](../configure-apps/file-schema/wcf/basichttpcontextbinding.md)|一種適合用來與 WS-Basic Profile 相容的 Web 服務進行通訊之繫結，能夠啟用用於交換內容的 HTTP Cookie。|
|<xref:System.ServiceModel.NetTcpContextBinding>|[\<netTcpContextBinding>](../configure-apps/file-schema/wcf/nettcpcontextbinding.md)|安全且最佳化的繫結，適用於在 WCF 應用程式之間進行跨電腦的通訊，可以啟用用於交換內容的 SOAP 標頭。|
|<xref:System.ServiceModel.WebHttpBinding>|[\<webHttpBinding>](../configure-apps/file-schema/wcf/webhttpbinding.md)|用於設定 WCF Web 服務端點的繫結，這些服務的公開會透過 HTTP 要求，而非 SOAP 訊息。|
|<xref:System.ServiceModel.WSHttpContextBinding>|[\<wsHttpContextBinding>](../configure-apps/file-schema/wcf/wshttpcontextbinding.md)|適用在非雙工服務合約上的安全且互通的繫結，可以啟用用於交換內容的 SOAP 標頭。|
|<xref:System.ServiceModel.UdpBinding>|[\<udpBinding>](../configure-apps/file-schema/wcf/udpbinding.md)|要在同時傳送一批突發之簡單訊息給大量用戶端時使用的繫結。|

 下表說明每一個系統提供繫結的個別功能。 您將於表格欄位中找到繫結；各項功能則列於各資料列，並於另一個表格中加以描述。 下表將說明使用的繫結縮寫。 若要選取繫結，請決定哪一欄可滿足所有您需要的資料列功能。

|繫結|互通性|安全性 (預設值)|工作階段<br />(預設值)|異動|雙工|編碼 (預設值)|資料流<br />(預設值)|
|-------------|----------------------|--------------------------|-----------------------------|------------------|------------|--------------------------|-------------------------------|
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(無)、傳輸、訊息、混合|(無)|(無)|N/A|文字、(MTOM)|是<br />(緩衝)|
|<xref:System.ServiceModel.WSHttpBinding>|WS|傳輸、(訊息)、混合|(無)、可靠工作階段、安全性工作階段|(無)、是|N/A|(文字)、MTOM|否|
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|(訊息)、無|(可靠工作階段)、安全性工作階段|(無)、是|是|(文字)、MTOM|否|
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|(訊息)、混合、無|(無)、可靠工作階段、安全性工作階段|(無)、是|否|(文字)、MTOM|否|
|<xref:System.ServiceModel.NetHttpBinding>|.NET|(無)、傳輸、訊息、TransportWithMessageCredential、TransportCredentialOnly|請參閱下列注意事項|無|請參閱下列注意事項|(二進位)、文字、MTOM|是 (緩衝)|
|<xref:System.ServiceModel.NetHttpsBinding>|.NET|(傳輸)、TransportWithMessageCredential|請參閱下列注意事項|無|請參閱下列注意事項|(二進位)、文字、MTOM|是<br />(緩衝)|
|<xref:System.ServiceModel.NetTcpBinding>|.NET|(傳輸)、訊息、無、混合|(傳輸)、可靠工作階段、安全性工作階段|(無)、是|是|二元|是<br />(緩衝)|
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|(傳輸)、無|無、(傳輸)|(無)、是|是|二元|是<br />(緩衝)|
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|訊息、(傳輸)、無|(無)、傳輸|無、(是)|否|二元|否|
|<xref:System.ServiceModel.NetPeerTcpBinding>|對等|(傳輸)|(無)|(無)|是||否|
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|(傳輸)|(無)|無、(是)|N/A|N/A|否|
|<xref:System.ServiceModel.BasicHttpContextBinding>|Basic Profile 1.1|(無)、傳輸、訊息、混合|(無)|(無)|N/A|文字、(MTOM)|是<br />(緩衝)|
|<xref:System.ServiceModel.NetTcpContextBinding>|.NET|(傳輸)、訊息、無、混合|(傳輸)、可靠工作階段、安全性工作階段|(無)、是|是|二元|是<br />(緩衝)|
|<xref:System.ServiceModel.WSHttpContextBinding>|WS|傳輸、(訊息)、混合|(無)、可靠工作階段、安全性工作階段|(無)、是|N/A|文字、(MTOM)|否|
|<xref:System.ServiceModel.UdpBinding> <br /><br /> **注意：** 互通性可以透過實作這個繫結所實作的標準 SOAP-over-UDP 規格來達成。|.NET|(無)|(無)|(無)|N/A|(文字)|否|

> [!IMPORTANT]
> <xref:System.ServiceModel.NetHttpBinding> 是為了使用 HTTP 或 WebSocket 服務而設計的繫結，其預設會使用二進位編碼。 <xref:System.ServiceModel.NetHttpBinding> 會偵測其所搭配使用的是要求-回覆合約還是雙工合約，並改變行為來配合，也就是會針對要求-回覆合約使用 HTTP，並針對雙工合約使用 WebSockets。 此行為可以使用來覆寫<xref:System.ServiceModel.Channels.WebSocketTransportUsage>繫結設定：WhenDuplex-這是預設值，行為方式如上所述。 Never-這會避免使用 WebSockets。 嘗試將這個設定用於雙工合約會導致例外狀況。 Always-這會強制使用 WebSockets，甚至用於要求-回覆合約。 NetHttpBinding 在 HTTP 模式和 WebSocket 模式下都會支援可靠工作階段。 在 WebSocket 模式中，工作階段是由傳輸提供。

 下表說明上一個表格中列出的各項功能。

|功能|描述|
|-------------|-----------------|
|互通性類型|表示繫結一定可與其互通的通訊協定或技術。|
|安全性|指定保護通道的方式：<br />-None:SOAP 訊息未受保護，並在用戶端未通過驗證。<br />-傳輸：已滿足傳輸層安全性需求。<br />訊息：訊息層已滿足安全性需求。<br />混合：宣告包含在 message;完整性和機密性需求已滿足傳輸層。|
|工作階段|指定此繫結是否支援工作階段合約。|
|異動|指定是否已啟用異動。|
|雙工|指定是否支援雙工合約。 請注意，此功能需要繫結對工作階段的支援。|
|編碼|請指定訊息的 Wire 格式。 允許的值包括：<br />- 文字：例如 UTF-8。<br />- 二進位<br />-Message Transmission Optimization Mechanism (MTOM):一種方法的有效編碼的 SOAP 封套內容中的二進位 XML 項目。|
|資料流|指定傳入與傳出的訊息是否支援資料流。 請使用繫結上的 `TransferMode` 屬性來設定該值。 允許的值包括：<br />- <xref:System.ServiceModel.TransferMode.Buffered>：要求訊息和回應訊息皆以緩衝處理。<br />- <xref:System.ServiceModel.TransferMode.Streamed>：要求訊息和回應訊息皆以資料流處理。<br />- <xref:System.ServiceModel.TransferMode.StreamedRequest>：資料流處理要求訊息，緩衝處理回應訊息。<br />- <xref:System.ServiceModel.TransferMode.StreamedResponse>：緩衝處理要求訊息，資料流處理回應訊息。|

## <a name="see-also"></a>另請參閱

- [建立端點概觀](endpoint-creation-overview.md)
- [使用繫結設定服務與用戶端](using-bindings-to-configure-services-and-clients.md)
- [基本 WCF 程式設計](basic-wcf-programming.md)
