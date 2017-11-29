---
title: "自訂繫結"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- Windows Communication Foundation, endpoints
- Windows Communication Foundation, configuration
ms.assetid: 58532b6d-4eea-4a4f-854f-a1c8c842564d
caps.latest.revision: "33"
author: Erikre
ms.author: erikre
manager: erikre
ms.openlocfilehash: 07247573678d81bb45f8b4b7f07a453573326cbc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="custom-bindings"></a>自訂繫結
當系統提供的其中一個繫結不符合服務的需求時，您可以使用 <xref:System.ServiceModel.Channels.CustomBinding> 類別。 所有繫結都是根據已排序的繫結項目組所建構。 自訂的繫結可以從系統提供的繫結項目建置，或是可以包含使用者定義的自訂繫結項目。 例如，您可以使用自訂繫結項目，以便在服務端點使用新的傳輸或編碼器。 如需實用範例，請參閱[自訂繫結範例](http://msdn.microsoft.com/en-us/657e8143-beb0-472d-9cfe-ed1a19c2ab08)。 [!INCLUDE[crdefault](../../../../includes/crdefault-md.md)][ \<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)。  
  
## <a name="construction-of-a-custom-binding"></a>建構自訂繫結  
 在建構自訂繫結時，會使用依特定順序堆疊的繫結項目集合中的 <xref:System.ServiceModel.Channels.CustomBinding.%23ctor%2A> 建構函式：  
  
-   在最上方為允許流動交易的選擇性 <xref:System.ServiceModel.Channels.TransactionFlowBindingElement> 類別。  
  
-   接下來是選擇性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement> 類別，它會提供 WS-ReliableMessaging 規格中所定義的工作階段和排序機制。 工作階段可以跨 SOAP 和傳輸媒介。  
  
-   下一個是選擇性的 <xref:System.ServiceModel.Channels.SecurityBindingElement> 類別，它會提供如授權、驗證、保護和機密性等安全性功能。  
  
-   下一個是選擇性的 <xref:System.ServiceModel.Channels.CompositeDuplexBindingElement> 類別，它可以與傳輸通訊協定進行雙向的雙工通訊，HTTP 之類的通訊協定原本並不支援雙工通訊。  
  
-   下一個是選擇性的 <xref:System.ServiceModel.Channels.OneWayBindingElement> 類別，它提供單向通訊。  
  
-   下一個是選擇性的資料流安全性繫結項目，這個項目可以是下列其中一種。  
  
    -   <xref:System.ServiceModel.Channels.SslStreamSecurityBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.WindowsStreamSecurityBindingElement>  
  
-   再來是必要的訊息編碼繫結項目。 您可以使用自己的訊息編碼器，或是三個訊息編碼繫結的其中一個：  
  
    -   <xref:System.ServiceModel.Channels.TextMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.BinaryMessageEncodingBindingElement>  
  
    -   <xref:System.ServiceModel.Channels.MtomMessageEncodingBindingElement>  
  
 最下方是必要的傳輸項目。 您可以使用自己的傳輸，或是下列其中一個 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 提供的傳輸繫結項目：  
  
-   <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.PeerTransportBindingElement>  
  
-   <xref:System.ServiceModel.Channels.MsmqTransportBindingElement>  
  
-   <xref:System.ServiceModel.MsmqIntegration.MsmqIntegrationBindingElement>  
  
-   <xref:System.ServiceModel.Channels.ConnectionOrientedTransportBindingElement>  
  
 下表摘要列出每一層的選項。  
  
|圖層|選項|必要項|  
|-----------|-------------|--------------|  
|異動|<xref:System.ServiceModel.Channels.TransactionFlowBindingElement>|否|  
|可靠性|<xref:System.ServiceModel.Channels.ReliableSessionBindingElement>|否|  
|安全性|<xref:System.ServiceModel.Channels.SecurityBindingElement>|否|  
|編碼|文字、二進位、訊息傳輸最佳化機制 (MTOM)、自訂|是|  
|Transport|TCP、HTTP、HTTPS、具名管道 (也稱為 IPC)、對等式 (P2P)、訊息佇列 (也稱為 MSMQ)、自訂|是|  
  
 此外，您也可以定義自己的繫結項目，並將其插入上述任何定義層之間。  
  
## <a name="see-also"></a>另請參閱  
 [建立端點概觀](../../../../docs/framework/wcf/endpoint-creation-overview.md)  
 [使用繫結設定服務與用戶端](../../../../docs/framework/wcf/using-bindings-to-configure-services-and-clients.md)  
 [系統提供的繫結](../../../../docs/framework/wcf/system-provided-bindings.md)  
 [如何： 自訂系統提供的繫結](../../../../docs/framework/wcf/extending/how-to-customize-a-system-provided-binding.md)  
 [\<customBinding >](../../../../docs/framework/configure-apps/file-schema/wcf/custombinding.md)  
 [自訂繫結](../../../../docs/framework/wcf/samples/custom-binding.md)
