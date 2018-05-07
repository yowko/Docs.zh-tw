---
title: 可靠的工作階段最佳做法
ms.date: 03/30/2017
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
ms.openlocfilehash: 1d9671e7e3124d535b66de8cd8468f76dcb32b10
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="best-practices-for-reliable-sessions"></a>可靠的工作階段最佳做法

本主題討論的可靠工作階段的最佳作法。

## <a name="setting-maxtransferwindowsize"></a>設定 MaxTransferWindowSize

可靠工作階段中 Windows Communication Foundation (WCF) 會使用傳輸窗口，來保留用戶端和服務上的訊息。 可設定的屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表傳輸窗口可保留的訊息數量。

在傳送端，這表示傳輸窗口可以保存等候認可; 期間的訊息數目在收件者，它會指出服務緩衝處理的訊息數目。

選擇正確的大小會影響網路效率和服務的最大的效用。 下列各節將詳細說明，請考慮選擇的值，這個屬性與值的影響。

預設的傳輸窗口大小是 8 個訊息。

### <a name="efficient-use-of-the-network"></a>有效率地使用網路

在此內容中，詞彙*網路*對應至為基礎的用戶端 （傳送者） 和服務 （接收者） 之間的通訊使用的所有項目。 這包括傳輸連線及任何媒介或橋接器之間，包括 SOAP 路由器或 HTTP proxy/防火牆等。

有效率地使用網路可確保充分運用網路功能。 可以透過網路每秒傳送的資料量 (*資料速率*) 以及寄件者的資料傳送至收件者的時間 (*延遲*) 如何有效地影響網路利用。

在傳送端，屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表其傳輸窗口在等候認可期間能夠保留的訊息數量。 如果網路延遲性很高，以確保能繼續回應的傳送者和有效的網路使用率，您應該增加傳輸窗口大小。

例如即使傳送端保持資料的速率，延遲可能是高如果傳送者與接收者之間存在好幾個媒介或是資料必須通過失真媒介或網路。 因此，寄件者並等候其傳輸窗口中之訊息的通知，才能接受新的網路上傳送的訊息。 緩衝區小而高延遲，較少的有效網路使用率。 另一方面，太大的傳輸窗口可能會影響服務，因為服務可能需要高的用戶端傳送的資料速率趕上進度。

### <a name="running-the-service-to-capacity"></a>執行服務容量

盡可能有效率地使用網路時，在理想情況下您也想在最大的效用執行服務。 接收端上的傳輸窗口大小屬性代表接收端可以緩衝處理的訊息數量。 這項訊息緩衝處理作業不只能協助控制網路流量，同時能讓服務效能發揮到極致。 例如，如果緩衝區為一則訊息，而訊息抵達的速度快過服務處理，網路可能會捨棄訊息，然後可能會浪費或是未能充分運用容量。

使用緩衝區會增加服務的可用性，因為能夠一面接收與緩衝處理先前接收的訊息時處理訊息。

我們建議使用的相同`MaxTransferWindowSize`寄件者和接收者上。

### <a name="enabling-flow-control"></a>啟用流量控制

*流量控制*是一種機制可確保寄件者與接收者跟彼此，也就是取用與處理訊息，它們所產生的一樣快。 用戶端與服務上的傳輸窗口大小可確保傳送端與接收端都有同樣合理的同步處理時間。

我們強烈建議您將屬性<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A>至`true`當您使用 WCF 用戶端和 WCF 服務之間可靠工作階段。

## <a name="setting-maxpendingchannels"></a>設定 MaxPendingChannels

在撰寫啟用來自不同用戶端的可靠工作階段通訊的服務時，很可能有許多用戶端建立的可靠工作階段服務在相同的時間。 在這些情況中，服務將視 `MaxPendingChannels` 屬性做出回應。

當傳送端對接收端建立可靠工作階段通道時，彼此之間的信號交換會建立可靠工作階段。 一旦建立了可靠工作階段，就會將通道放到擱置的通道佇列中，等候服務來接受它。 `MaxPendingChannels` 屬性代表可處於此狀態的通道數量。

它有可能的狀態，它無法在此接受多個通道的服務。 如果佇列已滿，嘗試建立可靠工作階段遭到拒絕，並在用戶端必須重試。

此外，也可以在佇列中的暫止通道保留在佇列較長時間。 在此同時，可靠工作階段的閒置逾時可能會發生，導致通道轉換為錯誤狀態。

當撰寫同時服務多個用戶端的服務，您應該設定為適合您需求的值。 設定太高的值`MaxPendingChannels`屬性會影響您的工作集。

預設值為<xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A>是四個通道。

## <a name="reliable-sessions-and-hosting"></a>可靠工作階段與裝載

當 web 裝載使用可靠工作階段的服務，您應該記住下列重要事項：

- 可靠工作階段具狀態，而且可透過 AppDomain 來維護狀態。 意思就是，所有屬於可靠工作階段一部分的訊息，都必須透過同一個 AppDomain 來處理。 Web 伺服陣列與 web 處理序區的伺服陣列或處理序區大小大於一個節點無法保證此條件約束。

- 使用雙重 HTTP 通道的可靠工作階段 (例如，使用`WsDualHttpBinding`) 可能需要超過兩個 HTTP 連線個別用戶端的預設值。 這表示雙工可靠工作階段可以要求最多兩個連線每一種方式，因為並行的應用程式和通訊協定訊息可能會在任何指定時間傳送每一種方式。 在特定條件之服務的訊息交換模式，這表示它是可以將使用雙重 HTTP 與可靠工作階段的 web 裝載服務鎖死。 若要增加允許的 HTTP 連線，每個用戶端數目，加入下列相關的組態檔 (例如， *web.config*有問題的服務):

  ```xml
  <configuration>
    <system.net>
      <connectionManagement>
        <add name="*" maxconnection="4" />
      </connectionManagement>
    </system.net>
  </configuration>
  ```

  值`maxconnection`屬性是必要的連線數。 在此情況下，至少應該是四個連接。
