---
title: 可靠的服務
ms.date: 03/30/2017
helpviewer_keywords:
- WCF [WCF], reliable messaging
- Windows Communication Foundation [WCF], reliable messaging
- WCF [WCF], reliable sessions
- Windows Communication Foundation [WCF], reliable sessions
- service contracts [WCF], reliable services
ms.assetid: 07814ed0-0775-47f2-987b-d8134fdd5099
ms.openlocfilehash: 67da784646cd918d7ce4a269311eedb6abee5013
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651026"
---
# <a name="reliable-services"></a>可靠的服務
佇列和可靠工作階段會實作可信賴傳訊的 Windows Communication Foundation (WCF) 功能。 本主題說明 WCF 的可靠傳訊功能。  
  
 *可靠的傳訊*是可信賴傳訊來源 (稱為*來源*) 將訊息可靠地傳輸到可信賴傳訊目的地 (稱為*目的地*)。  
  
 可信賴傳訊可執行下列功能：  
  
- 傳輸保證，保證無論是訊息傳輸或傳輸失敗，訊息都會從來源傳輸到目的地。  
  
- 區隔來源和目的地。 這樣可以讓來源和目的地所發生的失敗與復原不具相關性，並且提供可靠的訊息傳輸和傳遞，即使在來源或目的地無法使用的情況下也是如此。  
  
 可信賴傳訊通常會伴隨長延遲時間的發生。 *延遲*是要從來源到達目的地的訊息所花費的時間。 WCF，因此，提供下列類型的可信賴傳訊：  
  
- [可靠工作階段](../../../docs/framework/wcf/feature-details/reliable-sessions.md)，提供可靠的傳輸，而不需要高延遲的成本。  
  
- [WCF 中的佇列](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)，提供可信賴傳訊以及來源和目的地之間的分隔。  
  
## <a name="reliable-sessions"></a>可靠工作階段  
 可靠工作階段使用 WS-Reliable Messaging 通訊協定提供來源和目的地之間的端對端可靠訊息傳輸，而不論個別傳訊端點 (來源和目的地) 之間媒介的類型或數目為何。 這包括不是使用 SOAP 的任何傳輸媒介 (例如，HTTP Proxy) 或使用 SOAP 的媒介 (例如，SOAP 架構的路由器或橋接器)，而訊息在端點之間流動時需要這些媒介。 可靠工作階段會使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。  
  
 可靠工作階段會提供短延遲時間的可信賴訊息傳輸。 它們可透過任何的 Proxy 或媒介提供 SOAP 訊息，而這相當於 TCP 透過 IP 橋接器為封包提供的內容。 如需可靠工作階段的詳細資訊，請參閱[可靠工作階段](../../../docs/framework/wcf/feature-details/reliable-sessions.md)。  
  
### <a name="queues"></a>佇列  
 WCF 中的佇列會提供可信賴訊息和區隔來源和目的地，但代價是高延遲之間。 WCF 佇列通訊建置在之上 Message Queuing (MSMQ)。  
  
 MSMQ 是 Windows 所附的選用元件。 MSMQ 服務會執行為 Windows 服務。 它會代表來源擷取傳輸佇列中要進行傳輸的訊息，並將該訊息傳遞至目標佇列。 目標佇列會代表目的地接受訊息，以便隨時因應目的地要求訊息而進行傳遞。 MSMQ 管理員會實作可信賴傳訊通訊協定，這樣訊息就不會在傳輸期間遺失。 此通訊協定可以是原生 (Native)，或是稱為 SOAP Reliable Messaging Protocol (SRMP) 的 SOAP 架構通訊協定。  
  
 佇列之間的區隔性以及可信賴傳訊，可讓鬆散耦合的應用程式進行可靠的通訊。 與可靠工作階段不同的是，來源和目的地不需要同時執行。 這個特點促使當來源的訊息生產率與目的地的訊息消耗率不相同時，作用中的佇列會被用來當做負載撫平機制。 如需有關佇列的詳細資訊，請參閱 < [WCF 中的佇列](../../../docs/framework/wcf/feature-details/queues-in-wcf.md)。  
  
## <a name="see-also"></a>另請參閱

- [可靠工作階段概觀](../../../docs/framework/wcf/feature-details/reliable-sessions-overview.md)
- [WCF 中的佇列](../../../docs/framework/wcf/feature-details/queuing-in-wcf.md)
