---
title: Windows Communication Foundation 中的傳輸
ms.date: 03/30/2017
helpviewer_keywords:
- transports [WCF]
- WCF, transports
- Windows Communication Foundation, transports
ms.assetid: 005c894b-af70-48aa-a1c1-c99338083c27
ms.openlocfilehash: 8623b788b848867f25836a657b07349dd50c2780
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96251681"
---
# <a name="transports-in-windows-communication-foundation"></a>Windows Communication Foundation 中的傳輸

傳輸層 (Transport Layer) 屬於通道堆疊中的最底層。 Windows Communication Foundation (WCF) 中使用的主要傳輸為 HTTP、HTTPS、TCP 和具名管道。 本節中的主題將討論如何在這些傳輸之間進行選擇、設定傳輸，以及設定調整屬性。  
  
 WCF 包含額外的傳輸。 如需訊息佇列 (也稱為 MSMQ) 傳輸的相關資訊，請參閱 [佇列和可靠會話](queues-and-reliable-sessions.md)。 如需對等傳輸的詳細資訊，請參閱 [對等網路](peer-to-peer-networking.md)。  
  
## <a name="in-this-section"></a>本節內容  

 [選擇傳輸](choosing-a-transport.md)  
 說明這三種主要傳輸，以及進行選擇時的考量因素。  
  
 [選擇訊息編碼器](choosing-a-message-encoder.md)  
 說明選擇訊息編碼繫結項目時的考量因素。  
  
 [資料流訊息傳輸](streaming-message-transfer.md)  
 說明如何設定傳輸層來傳送資料流。  
  
 [設定 HTTP 和 HTTPS](configuring-http-and-https.md)  
 說明如何設定 HTTP 和 HTTPS 傳輸繫結項目。  
  
 [作法：以受限的保留項目取代 WCF URL 保留項目](how-to-replace-the-wcf-url-reservation-with-a-restricted-reservation.md)  
 說明如何使用 WCFURL 限制的保留。  
  
 [傳輸配額](transport-quotas.md)  
 說明在設定傳輸層之可用配額時的考量因素。  
  
 [使用 NAT 與防火牆](working-with-nats-and-firewalls.md)  
 說明當訊息是在防火牆後方進行傳送或接收、或是當網路位址轉譯 (NAT) 存在時的傳輸層設定方式。  
  
 [Net.TCP Port Sharing](net-tcp-port-sharing.md)  
 描述如何使用 WCF 的 Net.tcp 埠共用元件。  
  
## <a name="reference"></a>參考  

 <xref:System.ServiceModel.Channels.HttpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.HttpsTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.TcpTransportBindingElement>  
  
 <xref:System.ServiceModel.Channels.NamedPipeTransportBindingElement>  
  
## <a name="related-sections"></a>相關章節  

 [繫結](bindings.md)  
  
 [擴充繫結](../extending/extending-bindings.md)
