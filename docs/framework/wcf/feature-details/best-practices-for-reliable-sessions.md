---
title: "可靠的工作階段最佳做法 | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
ms.assetid: b94f6e01-8070-40b6-aac7-a2cb7b4cb4f2
caps.latest.revision: 6
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 6
---
# 可靠的工作階段最佳做法
本節討論可靠工作階段的最佳做法。  
  
## 設定 MaxTransferWindowSize  
 [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] 中的可靠工作階段使用傳輸窗口將訊息保留在用戶端與服務上。  可設定的屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表傳輸窗口可保留的訊息數量。  
  
 在傳送端，這個屬性代表傳輸窗口在等候認可期間能夠保留的訊息數量；在接收端，這個屬性則代表服務要緩衝處理的訊息數量。  
  
 選擇正確的數量會影響網路的使用效率，以及服務能夠發揮的最大效用。  下列各節將詳細說明選擇此屬性值要考量的事項，以及選擇的值對各方面的影響。  
  
 預設的傳輸窗口大小為 8 則訊息。  
  
### 有效率地使用網路  
 「*網路*」\(Network\) 一詞在這裡表示用戶端 \(傳送端\) 與服務 \(接收端\) 之間做為通訊基礎的所有事項。  這些事項包含傳輸連線與任何介於連線之間的媒介或橋接器 \(Bridge\)，包括 SOAP 路由器或 HTTP Proxy\/防火牆等。  
  
 有效率地使用網路可確保充分運用網路功能。  每秒透過網路傳送的資料量 \(稱為「*資料速率*」\(Data Rate\)\) 以及從傳送端將資料傳送到接收端所需的時間 \(稱為「*延遲時間*」\(Latency\)\)，兩者都會影響網路的使用效率。  
  
 在傳送端，屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxTransferWindowSize%2A> 代表其傳輸窗口在等候認可期間能夠保留的訊息數量。  因此，假如網路延遲時間很長，為了確保傳送端能夠提供回應並且有效地運用網路，您應該增加傳輸窗口的大小。  
  
 例如，即使傳送端保持不變的資料速率，如果在傳送端與接收端之間存在好幾個媒介或是耗損率高的媒介或網路，則延遲時間就會拉長。  因此，傳送端在接受新的訊息並在網路上傳輸之前，必須等候其傳輸窗口中的訊息得到認可。  如果緩衝區小而延遲時間長，則網路使用效率就會降低。  另一方面，太大的傳輸窗口會影響服務效率，因為服務可能必須跟上來自用戶端的高傳送速率。  
  
### 讓服務效能發揮到極致  
 不只網路需要有效運用，最好也能讓服務發揮最大的效用。  接收端上的傳輸窗口大小屬性代表接收端可以緩衝處理的訊息數量。  這項訊息緩衝處理作業不只能協助控制網路流量，同時能讓服務效能發揮到極致。  例如，如果緩衝區為 1 而訊息抵達的速度快過服務處理訊息的速度時，網路可能會捨棄訊息，導致網路效能遭到浪費或是未能充分運用。  
  
 使用緩衝區可以增加服務的可用性，因為緩衝區能夠一面接收與緩衝處理訊息，一面處理先前接收的訊息。  
  
 建議您同時在接收端與傳送端使用相同的 `MaxTransferWindowSize`。  
  
### 啟用流量控制  
 流量控制這項機制能夠確保傳送端與接收端彼此跟上對方的速度，亦即，訊息一旦產生，就能立刻被對方取用與處理。  用戶端與服務上的傳輸窗口大小可確保傳送端與接收端都有同樣合理的同步處理時間。  
  
 當您在 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 用戶端與 [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] 服務之間使用可靠工作階段時，強烈建議您將屬性 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.FlowControlEnabled%2A> 設為 true。  
  
## 設定 MaxPendingChannels  
 在撰寫啟用來自不同用戶端的可靠工作階段通訊的服務時，可能會有許多用戶端同時建立對服務的可靠工作階段連線。  在這些情況中，服務將視 `MaxPendingChannels` 屬性做出回應。  
  
 當傳送端對接收端建立可靠工作階段通道時，彼此之間的信號交換會建立可靠工作階段。  一旦建立了可靠工作階段，就會將通道放到擱置的通道佇列中，等候服務來接受它。  `MaxPendingChannels` 屬性代表可處於此狀態的通道數量。  
  
 服務有可能無法接受更多的通道。  如果佇列已滿，就會拒絕建立可靠工作階段的嘗試，這時用戶端就必須重試。  
  
 佇列中擱置的通道也可能會繼續停留在佇列一段時間。  這時候，可靠工作階段中可能會產生無活動逾時，導致通道轉換為錯誤狀態。  
  
 因此，在寫入可同時服務多個用戶端的服務時，您應該針對個人需要設定適當的值。  如果 `MaxPendingChannels` 屬性值設得太高，將會影響您的工作集。  
  
 <xref:System.ServiceModel.Channels.ReliableSessionBindingElement.MaxPendingChannels%2A> 的預設值為 4。  
  
## 可靠工作階段與裝載  
 當 Web 正在裝載使用可靠工作階段的服務時，您應該隨時注意下列重要事項：  
  
-   可靠工作階段是可設定狀態的，而且可透過 AppDomain 來維護狀態。  意思就是，所有屬於可靠工作階段一部分的訊息，都必須透過同一個 AppDomain 來處理。  Web 伺服陣列與 Web 處理序區 \(其中伺服陣列或處理序區的大小 \> 1\) 無法保證符合此條件約束。  
  
-   使用雙重 HTTP 通道的可靠工作階段 \(例如，使用 `WsDualHttpBinding`\) 可以在每個用戶端上要求兩倍的預設 HTTP 連線。  意思就是，雙工可靠工作階段最多可在每個方向要求兩個連線，因為並行的應用程式與通訊協定訊息在任何特定時間都可以雙向進行傳輸。  這意味著，在特定條件中，只要服務的訊息交換模式許可，可以將使用雙重 HTTP 與可靠工作階段的 Web 裝載服務鎖死。  若要增加每個用戶端上可允許的 HTTP 連線數量，請將下列新增到相關的組態檔中 \(例如，有問題的服務的 web.config\)：  
  
```  
<configuration>  
   <system.net>  
      <connectionManagement>  
         <add name = "*" maxconnection = "XX" />  
      </connectionManagement>  
   </system.net>  
</configuration>  
```  
  
 其中 “XX” 代表需要的連線數量。  在此情況中，最小值應為 4。