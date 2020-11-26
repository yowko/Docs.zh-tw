---
title: 佇列和可靠的工作階段
ms.date: 03/30/2017
ms.assetid: 7e794d03-141c-45ed-b6b1-6c0e104c1464
ms.openlocfilehash: db47838db1608dac4e0fe22252795b6dd33a0b6e
ms.sourcegitcommit: bc293b14af795e0e999e3304dd40c0222cf2ffe4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/26/2020
ms.locfileid: "96244687"
---
# <a name="queues-and-reliable-sessions"></a>佇列和可靠的工作階段

佇列和可靠會話是執行可靠訊息的 WCF) 功能 Windows Communication Foundation (。 本章節包含的主題會討論 WCF 可靠訊息功能。  
  
 「可信賴傳訊」為可信賴傳訊來源 (稱為來源) 將訊息可靠地傳輸到可信賴傳訊目的地 (稱為目的地) 的方式。  
  
 可信賴傳訊具有下列重要功能：  
  
- 傳輸保證，保證無論是訊息傳輸 (Transfer) 失敗或傳輸 (Transport) 失敗，訊息都會從來源傳送到目的地。  
  
- 將來源和目的地彼此分開，如此可對來源與目的地提供獨立的失敗與復原作業，以及可靠訊息傳輸與傳遞，就算來源或目的地無法使用也是一樣。  
  
 可信賴傳訊通常會伴隨長延遲時間的發生。 「延遲時間」為訊息從來源到達目的地所需要的時間。 因此，WCF 提供下列類型的可靠訊息：  
  
- [可靠的會話](reliable-sessions.md)，提供可靠的傳輸而不需要高延遲的成本  
  
- [WCF 中的佇列](queues-in-wcf.md)，可在來源與目的地之間提供可靠的傳輸和分隔。  
  
## <a name="reliable-sessions"></a>可靠工作階段  

 可靠工作階段使用 WS-ReliableMessaging 通訊協定提供來源和目的地之間的端對端可靠訊息傳輸，而不論傳訊端點 (來源和目的地) 之間媒介的類型或數目為何。 這包括不是使用 SOAP 的任何傳輸媒介 (例如，HTTP Proxy) 或使用 SOAP 的媒介 (例如，SOAP 架構的路由器或橋接器)，而訊息在端點之間流動時需要這些媒介。 可靠工作階段會使用記憶體中傳輸視窗來遮罩 SOAP 訊息層級的失敗，並在發生傳輸失敗時重新建立連線。  
  
 可靠工作階段會提供短延遲時間的可信賴訊息傳輸。 它們可透過任何的 Proxy 或媒介提供 SOAP 訊息，而這相當於 TCP 透過 IP 橋接器為封包提供的內容。 如需可靠會話的詳細資訊，請參閱 [可靠會話](reliable-sessions.md)。  
  
## <a name="queues"></a>佇列  

 WCF 中的佇列提供可靠的訊息傳輸，並以高延遲的成本在來源與目的地之間分開。 WCF 佇列的通訊是以訊息佇列 (（也稱為 MSMQ) ）為基礎。  
  
 MSMQ 是 Windows 隨附的選用元件，而且會以 NT 服務的身分執行。 它會代表來源擷取傳輸佇列中要進行傳輸的訊息，並將該訊息傳遞至目標佇列。 目標佇列會代表目的地接受訊息，以便隨時因應目的地要求訊息而進行傳遞。 MSMQ 佇列管理員會實作可靠訊息傳輸通訊協定，使訊息不會在傳輸期間遺失。 此通訊協定可以是原生或以 SOAP 為基礎的 SOAP Reliable Messaging Protocol (SRMP)。  
  
 佇列之間的區隔性以及可信賴傳訊，可讓鬆散耦合的應用程式進行可靠的通訊。 與可靠工作階段不同的是，來源和目的地不需要同時執行。 這個特點促使當來源的訊息生產率與目的地的訊息消耗率不相同時，作用中的佇列會被用來當做負載平衡機制。 如需佇列的詳細資訊，請參閱 [WCF 中的佇列](queues-in-wcf.md)。  
  
## <a name="see-also"></a>另請參閱

- [WCF 中的佇列](queues-in-wcf.md)
- [WCF 中的佇列](queuing-in-wcf.md)
- [可靠工作階段](reliable-sessions.md)
- [可靠的工作階段概觀](reliable-sessions-overview.md)
