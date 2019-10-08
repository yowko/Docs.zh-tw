---
title: 何謂 Windows Communication Foundation
ms.date: 03/30/2017
helpviewer_keywords:
- Windows Communication Foundation [WCF], technology overview
- technology overview [WCF]
- WCF [WCF], technology overview
ms.assetid: 40e1009d-ef15-450b-9848-62eabe5e5738
ms.openlocfilehash: 21a01c5d59d30ac89f6baa19dbcdcf718a1b7d88
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834856"
---
# <a name="what-is-windows-communication-foundation"></a>何謂 Windows Communication Foundation
Windows Communication Foundation （WCF）是用來建立服務導向應用程式的架構。 使用 WCF 時，您可以將資料當做非同步訊息，從一個服務端點傳送到另一個。 服務端點可能是由 IIS 裝載之持續上線服務的一部分，或為應用程式中裝載的服務。 端點則大致是某項服務的用戶端，會向該服務端點要求資料。 訊息可為簡單的單一字元或以 XML 傳送的字組，乃至如二進位資料的資料流這般複雜的形式都沒問題。 其中幾個範例案例包括：

- 處理商務交易的安全服務。

- 提供當前資料給其他使用者的服務，例如流量報表或其他監控服務。

- 讓兩人可相互即時通訊或交換資料的聊天交談服務。

- 輪詢一項或多項服務以取得資料，再按邏輯呈現簡報資料的儀表板應用程式。

- 使用 Windows Workflow Foundation 實作且公開為 WCF 服務的工作流程。

- 輪詢服務以取得最新資料摘要的 Silverlight 應用程式。

建立這類應用程式之前，在 WCF 存在之前，WCF 可以讓端點的開發作業比以往更容易。 總而言之，WCF 的設計目的是要提供可管理的方法來建立 Web 服務和 Web 服務用戶端。

## <a name="features-of-wcf"></a>WCF 的功能

WCF 包含下列功能集。 如需詳細資訊，請參閱[WCF 功能詳細資料](../../../docs/framework/wcf/feature-details/index.md)。

- **服務導向**

     使用 WS 標準的其中一個結果是，WCF 可讓您建立*服務導向*的應用程式。 服務導向架構 (SOA) 是 Web 服務賴以傳送和接收資料的基礎。 服務具備鬆散耦合的普遍優點，而非隨應用程式而異的硬式編碼。 鬆散耦合的關係意味著在任何平台建立的任何用戶端，只要遵守基本合約便能連線至任何服務。

- **互通性**

     WCF 會針對 Web 服務互通性實行現代化的業界標準。 如需所支援標準的詳細資訊，請參閱[互通性與整合](../../../docs/framework/wcf/feature-details/interoperability-and-integration.md)。

- **多種訊息模式**

     訊息將以數種模式的其中一種進行交換。 最常見的模式為要求/回覆模式，即某端點向另一端點要求資料， 然後由該另一端點予以回覆。 其他模式還包括單向訊息，則是僅由單一端點傳送訊息，但從不期待會收到回覆。 更複雜的模式為雙工交換模式，其中會由兩個端點建立連線，並相互往返傳送資料，類似立即訊息程式。 如需如何使用 WCF 來執行不同訊息交換模式的詳細資訊，請參閱[合約](../../../docs/framework/wcf/feature-details/contracts.md)。

- **服務中繼資料**

     WCF 支援使用業界標準（如 WSDL、XML 架構和 WS 原則）中指定的格式來發行服務中繼資料。 此中繼資料可用於自動產生及設定用戶端，以存取 WCF 服務。 您可以透過 HTTP 及 HTTPS，或者使用 Web 服務中繼資料交換標準來發行中繼資料。 如需詳細資訊，請參閱[中繼資料](../../../docs/framework/wcf/feature-details/metadata.md)。

- **資料合約**

     因為 WCF 是使用 .NET Framework 所建立，所以它也包含提供您想要強制執行之合約的程式碼易懂方法。 其中一種通用的合約類型就是資料合約。 基本上，當您使用 Visual C# 或 Visual Basic 撰寫服務程式碼時，處理資料最簡單的做法，就是建立類別，以屬於資料實體的屬性來表示資料實體。 WCF 包含完整的系統，可讓您以這種簡單的方式處理資料。 一旦表示資料的類別已建立，您的服務便會自動產生中繼資料，而讓用戶端能夠遵照您所設計的資料型別。 如需詳細資訊，請參閱[使用資料合約](../../../docs/framework/wcf/feature-details/using-data-contracts.md)。

- **安全性**

     訊息經過加密後可以保護隱私權，而您也可以要求使用者必須先驗證才能接收訊息。 使用諸如 SSL 或 WS-SecureConversation 等公認的標準即可實作安全性。 如需詳細資訊，請參閱[安全性](../../../docs/framework/wcf/feature-details/security.md)。

- **多重傳輸與編碼**

     訊息可以透過數種內建傳輸通訊協定與編碼的任何方式進行傳送。 最常見的通訊協定和編碼方式，就是使用超文字傳輸通訊協定（HTTP）傳送文字編碼的 SOAP 訊息，以便在萬維網上使用。 或者，WCF 可讓您透過 TCP、具名管道或 MSMQ 來傳送訊息。 這些訊息可編碼為文字，或採用最佳化的二進位格式。  使用 MTOM 標準將能有效傳送二進位資料。 如果所提供的傳輸或編碼都無法滿足您的需求，您還可以建立自己的自訂傳輸或編碼。 如需 WCF 支援的傳輸和編碼的詳細資訊，請參閱[傳輸](../../../docs/framework/wcf/feature-details/transports.md)。

- **可靠的佇列訊息**

     WCF 支援可靠的訊息交換，其使用可靠的會話，並透過 WS-TRUST 訊息和 MSMQ 來執行。 如需 WCF 中可靠和佇列訊息支援的詳細資訊，請參閱[佇列和可靠會話](../../../docs/framework/wcf/feature-details/queues-and-reliable-sessions.md)。

- **永久性的訊息**

     永久性的訊息是指不會因為通訊中斷而遺失的訊息。 處於永久性訊息模式的訊息一律儲存至資料庫。 萬一發生中斷，資料庫可以讓您在恢復連線後繼續進行訊息交換。 您也可以使用 Windows Workflow Foundation （WF）來建立持久的訊息。 如需詳細資訊，請參閱[工作流程服務](../../../docs/framework/wcf/feature-details/workflow-services.md)。

- **異動**

     WCF 也支援使用下列三種交易模型之一的交易：AtomicTransactions、@no__t 0 命名空間中的 Api，以及 Microsoft 分散式交易協調器。 如需 WCF 中交易支援的詳細資訊，請參閱[交易](../../../docs/framework/wcf/feature-details/transactions-in-wcf.md)。

- **AJAX 與 REST 支援**

     REST 是 Web 2.0 技術演進的一個範例。 WCF 可以設定為處理未包裝在 SOAP 封套中的「純文字」 XML 資料。 WCF 也可以延伸以支援特定的 XML 格式，例如 ATOM （熱門的 RSS 標準），甚至是非 XML 格式，例如 JavaScript 物件標記法（JSON）。

- **擴充性**

     WCF 架構具有許多擴充點。 如果需要額外的功能，有數個進入點可讓您自訂服務的行為。 如需可用擴充點的詳細資訊，請參閱[延伸 WCF](../../../docs/framework/wcf/extending/index.md)。

## <a name="wcf-integration-with-other-microsoft-technologies"></a>WCF 與其他 Microsoft 技術的整合

WCF 是彈性的平臺。 由於這項極大的彈性，WCF 也會用於其他幾種 Microsoft 產品。 藉由瞭解 WCF 的基本概念，如果您也使用其中任何一種產品，就能立即享有優勢。

與 WCF 配對的第一項技術是 Windows Workflow Foundation （WF）。 工作流程會將工作流程中的步驟封裝為「活動」，以簡化應用程式開發。 在第一版的 Windows Workflow Foundation 中，開發人員必須為工作流程建立主機。 下一個版本的 Windows Workflow Foundation 已與 WCF 整合。 這可以讓任何工作流程輕鬆地裝載在 WCF 服務中。 若要這麼做，您可以在 Visual Studio 2012 或更新版本中自動選擇 WF/WCF 專案類型。

Microsoft BizTalk Server R2 也會利用 WCF 做為通訊技術。 BizTalk 是設計用來接收標準化格式的資料以及轉換成其他格式。 訊息必須傳遞至中央訊息槽，以在該處使用嚴格對應或利用 BizTalk 功能 (例如工作流程引擎) 才可轉換訊息。 BizTalk 現在可以使用 WCF 企業營運（LOB）介面卡，將訊息傳遞至訊息方塊。

Microsoft Silverlight 為可供建立高互通性多樣化 Web 應用程式的平台，能讓開發人員建立媒體播放 (例如串流視訊) 頻繁的網站。 從第2版開始，Silverlight 已將 WCF 納入為通訊技術，以將 Silverlight 應用程式連線到 WCF 端點。

Windows Server AppFabric 應用程式伺服器的裝載功能是特別設計來部署和管理使用 WCF 進行通訊的應用程式。 裝載功能包括專為啟用 WCF 之應用程式設計的豐富工具和設定選項。

## <a name="see-also"></a>另請參閱

- <xref:System.ServiceModel>
- [Windows Communication Foundation 的基本概念](../../../docs/framework/wcf/fundamental-concepts.md)
- [Windows Communication Foundation 架構](../../../docs/framework/wcf/architecture.md)
- [方針及最佳做法](../../../docs/framework/wcf/guidelines-and-best-practices.md)
- [快速入門教學課程](../../../docs/framework/wcf/getting-started-tutorial.md)
- [文件指南](../../../docs/framework/wcf/guide-to-the-documentation.md)
- [基本 WCF 程式設計](../../../docs/framework/wcf/basic-wcf-programming.md)
- [Windows Communication Foundation 範例](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms751514%28v=vs.90%29)
