---
title: "設定系統提供的繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation [WCF], system-provided bindings
- WCF [WCF], system-provided bindings
- bindings [WCF], system-provided
ms.assetid: 443f8d65-f1f2-4311-83b3-4d8fdf7ccf16
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e77cf5cc271e86c02e8355dde6f721fe7751416
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/22/2017
---
# <a name="configuring-system-provided-bindings"></a>設定系統提供的繫結
在與端點對話時，繫結會指定要使用的通訊機制，並指出如何連接至端點。 繫結包含的項目定義了 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 通道的分層處理方式，以提供所需通訊功能。 繫結包含三種項目型別：  
  
-   通訊協定通道繫結項目，可決定要與傳送至端點的訊息搭配使用的安全性、可靠性、內容流量設定，或是使用者定義的通訊協定。  
  
-   傳輸通道繫結項目，則決定了在傳送訊息給端點時要使用的基礎傳輸通訊協定，例如 TCP 或 HTTP。  
  
-   訊息編碼繫結項目，對於傳送至端點的訊息來說，這些項目決定了要使用的 Wire 編碼，例如，文字/XML、二進位，或是訊息傳輸最佳化機制 (MTOM)。  
  
 本主題將提供所有系統提供的 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 繫結。 如果這些項目都不能完全符合應用程式的需求，您可以使用 <xref:System.ServiceModel.Channels.CustomBinding> 類別來建立繫結。 [!INCLUDE[crabout](../../../../includes/crabout-md.md)]建立自訂繫結，請參閱[自訂繫結](../../../../docs/framework/wcf/extending/custom-bindings.md)。  
  
> [!IMPORTANT]
>  請選取啟用了安全性的繫結。 根據預設，除了 <xref:System.ServiceModel.BasicHttpBinding> 繫結之外，所有繫結都會啟用安全性。 如果您沒有選取安全繫結或是停用了安全性，請務必透過其他方式來保護您的網路交換，例如儲存在安全的資料中心或是另外放在隔離的網路上。  
  
> [!IMPORTANT]
>  請勿使用不支援安全性或已停用安全性的繫結程序來搭配雙工合約一起使用，除非您能夠以其他方式來保護網路交換的安全。  
  
## <a name="system-provided-bindings"></a>系統提供的繫結  
 下列是隨附於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 的繫結。  
  
|繫結|組態項目|描述|  
|-------------|---------------------------|-----------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|[\<basicHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/basichttpbinding.md)|適合用來與 WS-Basic Profile 相容之 Web 服務通訊的繫結，例如，以 ASP.NET Web 服務 (ASMX) 為基礎的服務。 此繫結使用 HTTP 做為傳輸，並使用文字/XML 做為預設的訊息編碼。|  
|<xref:System.ServiceModel.WSHttpBinding>|[\<wsHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wshttpbinding.md)|適用在非雙工服務合約上的安全且互通的繫結。|  
|<xref:System.ServiceModel.WS2007HttpBinding>|[\<ws2007HttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007httpbinding.md)|安全且互通的繫結，可針對 <xref:System.ServiceModel.WSHttpBinding.Security%2A>、<xref:System.ServiceModel.ReliableSession> 與 <xref:System.ServiceModel.WSHttpBindingBase.TransactionFlow%2A> 繫結項目提供正確的版本支援。|  
|<xref:System.ServiceModel.WSDualHttpBinding>|[\<wsDualHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsdualhttpbinding.md)|安全且互通的繫結，適用於雙工服務合約或透過 SOAP 媒介的通訊。|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|[\<wsFederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/wsfederationhttpbinding.md)|安全、互通，且可支援 WS-Federation 通訊協定的繫結，此繫結可讓聯合組織有效率地驗證並授權使用者。|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|[\<ws2007FederationHttpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/ws2007federationhttpbinding.md)|衍生自 <xref:System.ServiceModel.WS2007HttpBinding> 且支援聯合安全性的安全、可互通的繫結。|  
|<xref:System.ServiceModel.NetTcpBinding>|[\<netTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/nettcpbinding.md)|安全且最佳化的繫結，適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式之間的跨電腦通訊。|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|[\<netNamedPipeBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netnamedpipebinding.md)|安全、可靠且最佳化的繫結，適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式之間的電腦通訊。|  
|<xref:System.ServiceModel.NetMsmqBinding>|[\<netMsmqBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netmsmqbinding.md)|佇列繫結，適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式之間的跨電腦通訊。|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|[\<netPeerTcpBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/netpeertcpbinding.md)|可啟用安全、多電腦通訊的繫結。|  
|<xref:System.ServiceModel.WebHttpBinding>|[\<w >](../../../../docs/framework/configure-apps/file-schema/wcf/webhttpbinding.md)|用於設定 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] Web 服務端點的繫結，這些服務的公開會透過 HTTP 要求，而非 SOAP 訊息。|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|[\<msmqIntegrationBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/msmqintegrationbinding.md)|繫結，適用於 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 應用程式與現有訊息佇列 (亦稱為 MSMQ) 應用程式之間的跨電腦通訊。|  
  
## <a name="binding-features"></a>繫結功能  
 下表說明每一個系統提供繫結所提供的一些重要功能。 繫結將列在第一欄，而有關功能的資訊則會在表格中說明。 下表將說明使用的繫結縮寫。 若要選取繫結，請決定哪一欄可滿足所有您需要的資料列功能。  
  
|繫結|互通性|安全性模式 (預設值)|工作階段<br /><br /> (預設值)|異動|雙工|  
|-------------|----------------------|----------------------------------|-----------------------------|------------------|------------|  
|<xref:System.ServiceModel.BasicHttpBinding>|Basic Profile 1.1|(無)、傳輸、訊息、混合|無、(無)|(無)|N/A|  
|<xref:System.ServiceModel.WSHttpBinding>|WS|無、傳輸、(訊息)、混合|(無)、傳輸、可靠工作階段|(無)、是|N/A|  
|<xref:System.ServiceModel.WS2007HttpBinding>|WS-Security、WS-Trust、WS-SecureConversation、WS-SecurityPolicy|無、傳輸、(訊息)、混合|(無)、傳輸、可靠工作階段|(無)、是|N/A|  
|<xref:System.ServiceModel.WSDualHttpBinding>|WS|無、(訊息)|(可靠工作階段)|(無)、是|[是]|  
|<xref:System.ServiceModel.WSFederationHttpBinding>|WS-Federation|無、(訊息)、混合|(無)、可靠工作階段|(無)、是|否|  
|<xref:System.ServiceModel.WS2007FederationHttpBinding>|WS-Federation|無、(訊息)、混合|(無)、可靠工作階段|(無)、是|否|  
|<xref:System.ServiceModel.NetTcpBinding>|.NET|無、(傳輸)、訊息、<br /><br /> 混合|可靠工作階段、(傳輸)|(無)、是|[是]|  
|<xref:System.ServiceModel.NetNamedPipeBinding>|.NET|無、<br /><br /> (傳輸)|無、(傳輸)|(無)、是|[是]|  
|<xref:System.ServiceModel.NetMsmqBinding>|.NET|無、訊息、(傳輸)、兩者|(無)|(無)、是|否|  
|<xref:System.ServiceModel.NetPeerTcpBinding>|對等|無、訊息、(傳輸)、混合|(無)|(無)|[是]|  
|<xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBinding>|MSMQ|無、(傳輸)|(無)|(無)、是|N/A|  
  
 下表說明上一個表格中的各項功能。  
  
|功能|描述|  
|-------------|-----------------|  
|互通性類型|表示繫結一定可與其互通的通訊協定或技術。|  
|安全性|指定保護通道的方式：<br /><br /> -無： SOAP 訊息並不安全，而且無法驗證用戶端。<br />傳輸： 已滿足傳輸層安全性需求。<br />-訊息： 已滿足訊息層安全性需求。<br />混合： 此安全性模式亦稱為`TransportWithMessageCredentials`。 它負責處理訊息層級的認證，而完整性和機密性需求則交由傳輸層負責。<br />-兩者： 兩個訊息層級與傳輸層級安全性會使用。 這項能力是 <xref:System.ServiceModel.NetMsmqBinding> 所獨有的。|  
|工作階段|指定此繫結是否支援工作階段合約。|  
|異動|指定是否已啟用異動。|  
|雙工|指定是否支援雙工合約。 請注意，此功能需要繫結對工作階段的支援。|  
|資料流|指定是否支援訊息資料流。|  
  
## <a name="see-also"></a>請參閱  
 [建立端點概觀](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [使用繫結設定服務與用戶端](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [基本 WCF 程式設計](../../../../docs/framework/wcf/basic-wcf-programming.md)
