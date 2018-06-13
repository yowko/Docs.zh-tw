---
title: Windows Communication Foundation 中的傳輸
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 6bb8e8b90c26533661684bd403b9ec439f1bb37e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33498120"
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation 中的傳輸
傳輸層 (Transport Layer) 屬於通道堆疊中的最底層。 使用 Windows Communication Foundation (WCF) 的主要傳輸是 HTTP、 HTTPS、 TCP 及具名的管道。 本節中的主題將討論如何在這些傳輸之間進行選擇、設定傳輸，以及設定調整屬性。  
  
 WCF 包含額外的傳輸。 如需訊息佇列 (也稱為 MSMQ) 傳輸的資訊，請參閱[佇列和可靠工作階段](../../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)。 如需端對端傳輸的資訊，請參閱[對等網路](../../../../docs/framework/wcf/feature-details/peer-to-peer-networking.md)。  
  
## <a name="in-this-section"></a>本節內容  
 [選擇傳輸](../../../../docs/framework/wcf/feature-details/choosing-a-transport.md)  
 說明這三種主要傳輸，以及進行選擇時的考量因素。  
  
 [選擇訊息編碼器](../../../../docs/framework/wcf/feature-details/choosing-a-message-encoder.md)  
 說明選擇訊息編碼繫結項目時的考量因素。  
  
 [資料流訊息傳輸](../../../../docs/framework/wcf/feature-details/streaming-message-transfer.md)  
 說明如何設定傳輸層來傳送資料流。  
  
 [設定 HTTP 和 HTTPS](../../../../docs/framework/wcf/feature-details/configuring-http-and-https.md)  
 說明如何設定 HTTP 和 HTTPS 傳輸繫結項目。  
  
 [如何：將 WCF URL 保留項目取代為受限保留項目](../../../../docs/framework/wcf/feature-details/how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 描述如何使用受限制的 WCFURL 保留項目。  
  
 [傳輸配額](../../../../docs/framework/wcf/feature-details/transport-quotas.md)  
 說明在設定傳輸層之可用配額時的考量因素。  
  
 [使用 NAT 與防火牆](../../../../docs/framework/wcf/feature-details/working-with-nats-and-firewalls.md)  
 說明當訊息是在防火牆後方進行傳送或接收、或是當網路位址轉譯 (NAT) 存在時的傳輸層設定方式。  
  
 [Net.TCP 連接埠共用](../../../../docs/framework/wcf/feature-details/net-tcp-port-sharing.md)  
 描述如何使用 WCF 的 Net.TCP 連接埠共用元件。  
  
## <a name="reference"></a>參考資料  
 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>相關章節  
 [繫結](../../../../docs/framework/wcf/feature-details/bindings.md)  
  
 [擴充繫結](../../../../docs/framework/wcf/extending/extending-bindings.md)
