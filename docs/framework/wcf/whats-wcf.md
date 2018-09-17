---
title: 何謂 Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: f202d922b441d86838dd41992104ceecfc9bbabf
ms.sourcegitcommit: 5bbfe34a9a14e4ccb22367e57b57585c208cf757
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45747331"
---
# <a name="what-is-windows-communication-foundation"></a>何謂 Windows Communication Foundation

Windows Communication Foundation (WCF) 是用於建置服務導向應用程式的架構。 使用 WCF，您可以將資料傳送非同步訊息形式從一個服務端點之間。 服務端點可能是由 IIS 裝載之持續上線服務的一部分，或為應用程式中裝載的服務。 端點則大致是某項服務的用戶端，會向該服務端點要求資料。 訊息可為簡單的單一字元或以 XML 傳送的字組，乃至如二進位資料的資料流這般複雜的形式都沒問題。 其中幾個範例案例包括：

-   處理商務交易的安全服務。

-   提供當前資料給其他使用者的服務，例如流量報表或其他監控服務。

-   讓兩人可相互即時通訊或交換資料的聊天交談服務。

-   輪詢一項或多項服務以取得資料，再按邏輯呈現簡報資料的儀表板應用程式。

-   使用 Windows Workflow Foundation 實作且公開為 WCF 服務的工作流程。

-   輪詢服務以取得最新資料摘要的 Silverlight 應用程式。

建立這類應用程式的 WCF 存在之前如有必要時，WCF 可讓端點開發比以往更容易。 總而言之，WCF 被設計來提供可管理的方法，用來建立 Web 服務和 Web 服務用戶端。

## <a name="features-of-wcf"></a>WCF 的功能

WCF 包含下列幾組功能。 如需詳細資訊，請參閱 < [WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)。

-   **服務導向**

     採用 WS 標準的一種結果是，WCF 可讓您建立*服務導向*應用程式。 服務導向架構 (SOA) 是 Web 服務賴以傳送和接收資料的基礎。 服務具備鬆散耦合的普遍優點，而非隨應用程式而異的硬式編碼。 鬆散耦合的關係意味著在任何平台建立的任何用戶端，只要遵守基本合約便能連線至任何服務。

-   **互通性**

     WCF 實作 Web 服務互通性的最新業界標準。 如需有關支援的標準的詳細資訊，請參閱[互通性與整合](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)。

-   **多種訊息模式**

     訊息將以數種模式的其中一種進行交換。 最常見的模式為要求/回覆模式，即某端點向另一端點要求資料， 然後由該另一端點予以回覆。 其他模式還包括單向訊息，則是僅由單一端點傳送訊息，但從不期待會收到回覆。 更複雜的模式為雙工交換模式，其中會由兩個端點建立連線，並相互往返傳送資料，類似立即訊息程式。 如需有關如何實作各種訊息交換模式使用 WCF 請參閱[合約](../../../docs/framework/wcf/feature-details/contracts.md)。

-   **服務中繼資料**

     WCF 支援發行服務中繼資料，使用業界標準，例如 WSDL、 XML 結構描述及 Ws-policy 中所指定的格式。 此中繼資料可以用於自動產生，並設定用戶端存取 WCF 服務。 您可以透過 HTTP 及 HTTPS，或者使用 Web 服務中繼資料交換標準來發行中繼資料。 如需詳細資訊，請參閱 <<c0> [ 中繼資料](../../../docs/framework/wcf/feature-details/metadata.md)。

-   **資料合約**

     因為 WCF 建置使用[!INCLUDE[dnprdnshort](../../../includes/dnprdnshort-md.md)]，它也包含便利的程式碼方法，提供您想要強制執行的合約。 其中一種通用的合約類型就是資料合約。 基本上，當您使用 Visual C# 或 Visual Basic 撰寫服務程式碼時，處理資料最簡單的做法，就是建立類別，以屬於資料實體的屬性來表示資料實體。 WCF 包含完整的系統以這個簡單的方式處理資料。 一旦表示資料的類別已建立，您的服務便會自動產生中繼資料，而讓用戶端能夠遵照您所設計的資料型別。 如需詳細資訊，請參閱[Using Data Contracts](../../../docs/framework/wcf/feature-details/using-data-contracts.md)

-   **安全性**

     訊息經過加密後可以保護隱私權，而您也可以要求使用者必須先驗證才能接收訊息。 使用諸如 SSL 或 WS-SecureConversation 等公認的標準即可實作安全性。 如需詳細資訊，請參閱[安全性](../../../docs/framework/wcf/feature-details/security.md)。

-   **多重傳輸與編碼**

     訊息可以透過數種內建傳輸通訊協定與編碼的任何方式進行傳送。 最常見的通訊協定和編碼方式是將傳送編碼使用超文字傳輸通訊協定 (HTTP) 在 World Wide Web 上使用的 SOAP 訊息的文字。 或者，WCF 可讓您傳送訊息的 TCP 具名管道或 MSMQ。 這些訊息可編碼為文字，或採用最佳化的二進位格式。  使用 MTOM 標準將能有效傳送二進位資料。 如果所提供的傳輸或編碼都無法滿足您的需求，您還可以建立自己的自訂傳輸或編碼。 如需支援的 WCF 傳輸與編碼詳細資訊，請參閱[傳輸](../../../docs/framework/wcf/feature-details/transports.md)。

-   **可靠的佇列訊息**

     WCF 支援使用可靠工作階段，透過 Ws-reliable 訊息實作及使用 MSMQ 的可靠訊息交換。 如需可靠及佇列訊息的支援，WCF 的詳細資訊，請參閱[佇列和可靠工作階段](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)。

-   **永久性的訊息**

     永久性的訊息是指不會因為通訊中斷而遺失的訊息。 處於永久性訊息模式的訊息一律儲存至資料庫。 萬一發生中斷，資料庫可以讓您在恢復連線後繼續進行訊息交換。 您也可以建立永久性的訊息，使用 Windows Workflow Foundation (WF)。 如需詳細資訊，請參閱 <<c0> [ 工作流程服務](../../../docs/framework/wcf/feature-details/workflow-services.md)。

-   **異動**

     WCF 還支援使用三種交易模型中的任一種進行交易：WS-AtomicTtransaction、 <xref:System.Transactions> 命名空間中的應用程式開發介面，以及 Microsoft 分散式交易協調器。 如需有關交易看到在 WCF 中的支援[交易](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)。

-   **AJAX 與 REST 支援**

     REST 是 Web 2.0 技術演進的一個範例。 WCF 可以設定成處理不會包裝在 SOAP 封套的 「 純 」 XML 資料。 WCF 也可以擴充以支援特定的 XML 格式，例如 ATOM (常用的 RSS 標準)，即使非 XML 格式，例如 JavaScript Object Notation (JSON)。

-   **擴充性**

     WCF 架構具有若干擴充點。 如果需要額外的功能，有數個進入點可讓您自訂服務的行為。 如需有關可用擴充點看到[延伸 WCF](../../../docs/framework/wcf/extending/index.md)。

## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF 與其他 Microsoft 技術的整合

WCF 是彈性的平台。 極大彈性，因為 WCF 也會在數個其他 Microsoft 產品。 了解 WCF 的基本概念，您會有立即掌握優勢，如果您同時使用這些產品。

WCF 與配對的第一個技術是 Windows Workflow Foundation (WF)。 工作流程由工作流程中的封裝步驟簡化應用程式開發，為 「 活動 」。 在 Windows Workflow Foundation 的第一個版本中，開發人員則必須建立工作流程主機。 與 WCF 整合 Windows Workflow Foundation 的下一個版本。 允許任何要輕鬆地裝載 WCF 服務中的工作流程。 您可以自動選擇 WF/WCF 專案類型在 Visual Studio 2012 或更新版本來執行這項操作。

Microsoft BizTalk Server R2 同樣使用 WCF，做為通訊技術。 BizTalk 是設計用來接收標準化格式的資料以及轉換成其他格式。 訊息必須傳遞至中央訊息槽，以在該處使用嚴格對應或利用 BizTalk 功能 (例如工作流程引擎) 才可轉換訊息。 BizTalk 現在可以使用 WCF 企業營運 (LOB) 配接器將訊息傳遞到 messagebox。

Microsoft Silverlight 為可供建立高互通性多樣化 Web 應用程式的平台，能讓開發人員建立媒體播放 (例如串流視訊) 頻繁的網站。 從第 2 版開始，Silverlight 已經納入 WCF 做為通訊技術，來連接至 WCF 端點的 Silverlight 應用程式。

[!INCLUDE[dublin](../../../includes/dublin-md.md)]應用程式伺服器特別建置用於部署和管理使用 WCF 進行通訊的應用程式。 [!INCLUDE[dublin2](../../../includes/dublin2-md.md)]包含專為 WCF 啟用應用程式的豐富工具及組態選項。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel>
- [Windows Communication Foundation 的基本概念](../../../docs/framework/wcf/fundamental-concepts.md)
- [Windows Communication Foundation 架構](../../../docs/framework/wcf/architecture.md)
- [方針及最佳做法](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)
- [文件指南](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Communication Foundation 範例](http://msdn.microsoft.com/library/8ec9d192-5d81-4f64-bfd3-90c5e5858c91)
