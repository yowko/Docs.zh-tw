---
title: "何謂 Windows Communication Foundation | Microsoft Docs"
ms.custom: ""
ms.date: "03/30/2017"
ms.prod: ".net-framework"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "dotnet-clr"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "VB"
  - "CSharp"
helpviewer_keywords: 
  - "Windows Communication Foundation [WCF], 技術概觀"
  - "技術概觀 [WCF]"
  - "WCF [WCF], 技術概觀"
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
caps.latest.revision: 51
author: "Erikre"
ms.author: "erikre"
manager: "erikre"
caps.handback.revision: 49
---
# 何謂 Windows Communication Foundation
[!INCLUDE[indigo1](../../../includes/indigo1-md.md)] 是用於建置服務導向應用程式的架構。 使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]，您可以在各個服務端點之間傳送非同步訊息形式的資料。 服務端點可能是由 IIS 裝載之持續上線服務的一部分，或為應用程式中裝載的服務。 端點則大致是某項服務的用戶端，會向該服務端點要求資料。 訊息可為簡單的單一字元或以 XML 傳送的字組，乃至如二進位資料的資料流這般複雜的形式都沒問題。 其中幾個範例案例包括：  
  
-   處理商務交易的安全服務。  
  
-   提供當前資料給其他使用者的服務，例如流量報表或其他監控服務。  
  
-   讓兩人可相互即時通訊或交換資料的聊天交談服務。  
  
-   輪詢一項或多項服務以取得資料，再按邏輯呈現簡報資料的儀表板應用程式。  
  
-   使用 Windows Workflow Foundation 實作且公開為 WCF 服務的工作流程。  
  
-   輪詢服務以取得最新資料摘要的 Silverlight 應用程式。  
  
 儘管在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 面市之前，原本就能建立這幾類應用程式，但 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 使得端點開發比以往更為容易。 簡言之，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 的設計提供了便於管理的方式以讓您建立 Web 服務與 Web 服務用戶端。  
  
## WCF 的功能  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 包括下列功能集。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md).  
  
-   **服務導向**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 採用 WS 標準的結果，代表您可以建立「*服務導向*」\(Service Oriented\) 應用程式。 服務導向架構 \(SOA\) 是 Web 服務賴以傳送和接收資料的基礎。 服務具備鬆散耦合的普遍優點，而非隨應用程式而異的硬式編碼。 鬆散耦合的關係意味著在任何平台建立的任何用戶端，只要遵守基本合約便能連線至任何服務。  
  
-   **互通性**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 實作了 Web 服務互通性的最新業界標準。[!INCLUDE[crabout](../../../includes/crabout-md.md)]受支援標準的詳細資訊，請參閱[互通性與整合](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)。  
  
-   **多種訊息模式**  
  
     訊息將以數種模式的其中一種進行交換。 最常見的模式為要求\/回覆模式，即某端點向另一端點要求資料， 然後由該另一端點予以回覆。 其他模式還包括單向訊息，則是僅由單一端點傳送訊息，但從不期待會收到回覆。 更複雜的模式為雙工交換模式，其中會由兩個端點建立連線，並相互往返傳送資料，類似立即訊息程式。[!INCLUDE[crabout](../../../includes/crabout-md.md)]如何使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 來實作各種訊息交換模式的詳細資訊，請參閱 [合約](../../../docs/framework/wcf/feature-details/contracts.md)。  
  
-   **服務中繼資料**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 支援採用業界標準 \(如 WSDL、XML 結構描述及 WS\-Policy\) 指定的格式來發行服務中繼資料。 這份中繼資料可用於自動產生和設定將要存取 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務的用戶端。 您可以透過 HTTP 及 HTTPS，或者使用 Web 服務中繼資料交換標準來發行中繼資料。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [中繼資料](../../../docs/framework/wcf/feature-details/metadata.md).  
  
-   **資料合約**  
  
     由於 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 是使用 [!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)] 所建置，其亦包含了便利的程式碼方法，以讓您提供希望強制履行的合約。 其中一種通用的合約類型就是資料合約。 基本上，當您使用 Visual C\# 或 Visual Basic 撰寫服務程式碼時，處理資料最簡單的做法，就是建立類別，以屬於資料實體的屬性來表示資料實體。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 包含完善的系統，能以如此簡便的方式來處理資料。 一旦表示資料的類別已建立，您的服務便會自動產生中繼資料，而讓用戶端能夠遵照您所設計的資料型別。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [使用資料合約](../../../docs/framework/wcf/feature-details/using-data-contracts.md)  
  
-   **安全性**  
  
     訊息經過加密後可以保護隱私權，而您也可以要求使用者必須先驗證才能接收訊息。 使用諸如 SSL 或 WS\-SecureConversation 等公認的標準即可實作安全性。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [安全性](../../../docs/framework/wcf/feature-details/security.md).  
  
-   **多重傳輸與編碼**  
  
     訊息可以透過數種內建傳輸通訊協定與編碼的任何方式進行傳送。 最常用的通訊協定與編碼方式為傳送文字編碼的 SOAP 訊息，其所使用的是全球資訊網泛用的超文字傳輸通訊協定 \(HTTP\)。 或者，[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 也能讓您透過 TCP、具名管道或 MSMQ 傳送訊息。 這些訊息可編碼為文字，或採用最佳化的二進位格式。  使用 MTOM 標準將能有效傳送二進位資料。 如果所提供的傳輸或編碼都無法滿足您的需求，您還可以建立自己的自訂傳輸或編碼。[!INCLUDE[crabout](../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 支援的傳輸與編碼的詳細資訊，請參閱 [傳輸](../../../docs/framework/wcf/feature-details/transports.md)。  
  
-   **可靠的佇列訊息**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 使用透過 WS\-Reliable 傳訊來實作的可靠工作階段以及 MSMQ，來支援可靠的訊息交換。[!INCLUDE[crabout](../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中可靠及佇列訊息支援的詳細資訊，請參閱 [佇列和可靠的工作階段](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)。  
  
-   **永久性的訊息**  
  
     永久性的訊息是指不會因為通訊中斷而遺失的訊息。 處於永久性訊息模式的訊息一律儲存至資料庫。 萬一發生中斷，資料庫可以讓您在恢復連線後繼續進行訊息交換。 您也能夠使用 [!INCLUDE[wf](../../../includes/wf-md.md)] 建立永久性的訊息。[!INCLUDE[crdefault](../../../includes/crdefault-md.md)] [工作流程服務](../../../docs/framework/wcf/feature-details/workflow-services.md).  
  
-   **異動**  
  
     WCF 還支援使用三種交易模型中的任一種進行交易：WS\-AtomicTtransaction、<xref:System.Transactions> 命名空間中的應用程式開發介面，以及 Microsoft 分散式交易協調器。[!INCLUDE[crabout](../../../includes/crabout-md.md)][!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 中支援交易的詳細資訊，請參閱 [異動](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)。  
  
-   **AJAX 與 REST 支援**  
  
     REST 是 Web 2.0 技術演進的一個範例。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 可設定成用來處理未包裝在 SOAP Envelope 中的「純」XML 資料。[!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 也可以擴充，以支援特定的 XML 格式，例如 ATOM \(常用的 RSS 標準\)，甚至是非 XML 格式，例如 JavaScript Object Notation \(JSON\)。  
  
-   **擴充性**  
  
     [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 架構具有若干擴充點。 如果需要額外的功能，有數個進入點可讓您自訂服務的行為。[!INCLUDE[crabout](../../../includes/crabout-md.md)]可用擴充點的詳細資訊，請參閱 [延伸 WCF](../../../docs/framework/wcf/extending/extending-wcf.md)。  
  
## WCF 與其他 Microsoft 技術的整合  
 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 是具有靈活彈性的平台。 由於提供了極大彈性，許多其他 Microsoft 產品也使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)]。 了解 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 的基本概念後，您在使用任何這些產品時就能立即掌握優勢。  
  
 第一項與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 搭檔的技術為 Windows Workflow Foundation \(WF\)。 工作流程會將其步驟封裝在工作流程中成為活動，藉以簡化應用程式開發。 若是使用第一版的 [!INCLUDE[wf2](../../../includes/wf2-md.md)]，開發人員則必須為工作流程建立主應用程式。 下一版的 [!INCLUDE[wf2](../../../includes/wf2-md.md)] 已與 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 相整合。 如此可讓任何工作流程輕鬆地裝載在 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 服務中，您只要自動選擇 WF\/WCF \([!INCLUDE[vs_current_long](../../../includes/vs-current-long-md.md)] 中的專案類型\) 即可。  
  
 Microsoft BizTalk Server R2 同樣使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 做為通訊技術。 BizTalk 是設計用來接收標準化格式的資料以及轉換成其他格式。 訊息必須傳遞至中央訊息槽，以在該處使用嚴格對應或利用 BizTalk 功能 \(例如工作流程引擎\) 才可轉換訊息。 BizTalk 如今已可使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 企業營運 \(LOB\) 配接器將訊息傳遞至訊息槽。  
  
 Microsoft Silverlight 為可供建立高互通性多樣化 Web 應用程式的平台，能讓開發人員建立媒體播放 \(例如串流視訊\) 頻繁的網站。 Silverlight 從 2 版起已納入 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 做為通訊技術，將 Silverlight 應用程式連接至 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 端點。  
  
 [!INCLUDE[dublin](../../../includes/dublin-md.md)] 應用程式伺服器是用於部署與管理使用 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 進行通訊的應用程式而特別建立的。[!INCLUDE[dublin2](../../../includes/dublin2-md.md)] 包含了專為 [!INCLUDE[indigo2](../../../includes/indigo2-md.md)] 已啟用的應用程式而設計之豐富的工具及組態選項。  
  
## 請參閱  
 <xref:System.ServiceModel>   
 [Windows Communication Foundation 的主要概念](../../../docs/framework/wcf/fundamental-concepts.md)   
 [Windows Communication Foundation 架構](../../../docs/framework/wcf/architecture.md)   
 [方針及最佳做法](../../../docs/framework/wcf/guidelines-and-best-practices.md)   
 [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)   
 [文件指南](../../../docs/framework/wcf/guide-to-the-documentation.md)   
 [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)   
 [Windows Communication Foundation Samples](http://msdn.microsoft.com/zh-tw/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)