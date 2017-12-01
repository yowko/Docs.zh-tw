---
title: "設計微服務導向應用程式"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計微服務導向應用程式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 1e1dc919c7e35580576c86b4cf9872b4f8cea2c2
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/22/2017
---
# <a name="designing-a-microservice-oriented-application"></a>設計微服務導向應用程式

本節著重於開發假設伺服器端企業應用程式。

## <a name="application-specifications"></a>應用程式規格

假設應用程式會藉由執行商務邏輯、 存取資料庫，然後傳回 HTML、 JSON 或 XML 回應處理要求。 我們會假設應用程式必須支援各種不同的用戶端，包括執行單一頁面應用程式 (SPAs)、 傳統 web 應用程式、 行動裝置 web 應用程式，以及原生行動應用程式的桌面瀏覽器。 應用程式也可能會公開給第三方使用的 API。 它也應該能夠以非同步的方式，其 microservices 或外部應用程式整合，讓方法有助於 microservices 部分故障的恢復功能。

應用程式將會包含這些類型的元件：

-   簡報元件。 這些是負責處理 UI 和使用遠端服務。

-   網域或商務邏輯。 這是應用程式的網域邏輯。

-   資料庫存取邏輯。 這包含資料存取元件負責存取資料庫 （SQL 或 NoSQL）。

-   應用程式整合邏輯。 這包括傳訊通道，主要是根據訊息代理程式。

應用程式需要高延展性，同時允許垂直子系統、 向外延展的自主，因為某些子系統需要將可調適性比其他項目。

應用程式必須能夠在多個基礎結構環境 （多個公用雲端和內部部署） 部署，並在理想情況下應該是跨平台，能夠輕鬆地移動從 Linux windows （反之亦然）。

## <a name="development-team-context"></a>開發小組內容

我們也假設下列有關應用程式的開發程序：

-   您必須將焦點放在不同的商務應用程式區域的多個開發團隊。

-   新的小組成員必須上手，而且應用程式必須是容易了解和修改。

-   應用程式將會有長期的演進，不斷改變的商務規則。

-   您需要長期優，這表示擁有靈活度，同時能夠對其他子系統的最小影響更新多個子系統實作未來新的變更時。

-   您要練習持續整合與連續部署的應用程式。

-   您想要利用新興技術 （架構、 程式設計語言中，等） 時進化的應用程式。 您不想讓應用程式的完整移轉時移到新的技術，因為會導致高成本而且會影響可預測性及應用程式的穩定性。

## <a name="choosing-an-architecture"></a>選擇架構

應該將應用程式部署的架構是什麼？ 應用程式，以及開發內容的規格，強烈建議您應該將它分解成自發子系統 microservices 共同作業和容器，表單中，其中的微服務所建構應用程式是一個容器。

這種方法，每個服務 （容器） 會實作一組凝聚和範圍狹窄相關函式。 例如，應用程式可能包含例如目錄服務，排序服務、 購物籃服務、 使用者設定檔服務等服務。

Microservices 通訊使用通訊協定等 HTTP (REST)，但也會以非同步方式 （亦即 AMQP） 可能的話，特別是當傳播更新與整合事件。

Microservices 的開發和部署為彼此的容器。 這表示開發團隊可以開發和部署而不會影響其他子系統的某些微服務。

每個微服務有它自己的資料庫，讓它可以完全與其他 microservices 分離。 必要時，從不同 microservices 資料庫之間的一致性是利用來達成應用程式層級整合事件 （透過邏輯事件匯流排），為已處理命令和查詢責任隔離 (CQRS) 中。 因此，商務條件約束也必須不怕之間多個 microservices 最終一致性和相關資料庫。

### <a name="eshoponcontainers-a-reference-application-for-net-core-and-microservices-deployed-using-containers"></a>eShopOnContainers:.NET Core 和 microservices 部署使用容器的參考應用程式

您可以專注於架構和技術，而不是您可能不知道 hypothetic 商務網域思考，我們選取已知的商務網域 — 也就是簡化的電子商務 （e 廳） 的應用程式所呈現的類別目錄產品，會接受來自客戶，會驗證清查，以及執行其他商務功能。 此容器為基礎的應用程式的原始程式碼位於[eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub 儲存機制。

此應用程式包含多個子系統，包括數個存放區 UI 前端 （Web 應用程式和原生行動應用程式），以及後端 microservices 和所有必要的伺服器端作業的容器。 圖 8-1 會示範參考應用程式的架構。

![](./media/image1.png)

**圖 8-1**。 EShopOnContainers 參考應用程式，其中顯示直接的用戶端的微服務通訊，以及事件匯流排

**裝載環境**。 在圖 8-1，您會看到部署在單一的 Docker 主機內的數個容器。 部署到單一的 Docker 主機使用 docker 時，也就是案例-撰寫 up 命令。 不過，如果您是使用 orchestrator 或容器的叢集，每個容器可在執行的不同的主機 （節點），而且任何節點可能會執行任何數目的容器，因為我們稍早架構一節所述。

**通訊架構**。 EShopOnContainers 應用程式會使用兩種通訊類型功能的動作 （查詢和更新及交易） 的類型而定：

-   直接到微服務的用戶端通訊。 這用於查詢和接受更新或交易式命令，從用戶端應用程式時。

-   以事件為基礎的非同步通訊。 這是透過事件匯流排 microservices 中散佈的更新，或與外部應用程式整合。 事件匯流排可以任何傳訊 broker 基礎結構技術，例如 RabbitMQ，或使用 Azure 服務匯流排、 NServiceBus、 MassTransit 或 Brighter 等較高層級的服務匯流排用來實作。

應用程式部署為 microservices 表單的容器中的一組。 用戶端應用程式可以與這些容器通訊，以及 microservices 之間的通訊。 如前所述，此初始架構正在使用直接通訊，用戶端的微服務架構，這表示，用戶端應用程式可以對每個 microservices 直接提出要求。 每個微服務有 https://servicename.applicationname.companyname 類似的公用端點。 必要時，每個微服務可以使用不同的 TCP 連接埠。 生產環境中，URL 會對應至 microservices' 負載平衡器，這會將要求分散跨可用的微服務執行個體。

**API 閘道 vs 的重要注意事項。EShopOnContainers 中的直接通訊。** 本指南中的架構 > 一節所述，直接通訊，用戶端的微服務架構可以有缺點，當您在建立的大型且複雜微服務應用程式。 但它可能是適用於小型應用程式，例如 eShopOnContainers 中應用程式，其目標是將焦點放在更簡單的快速入門啟動 Docker 容器基礎的應用程式，我們不想要建立單一整合型 API 閘道會影響microservices' 開發自主。

但是，如果您要設計大型微服務應用程式，使用數十個 microservices，我們強烈建議您考慮 API 閘道模式中，我們在架構 > 一節中所述。
無法重構此架構的決策，一旦實際執行的應用程式和特別進行外貌思考遠端用戶端。 需根據用戶端應用程式的表單係數的多個自訂 API 閘道可提供不同的資料彙總每個用戶端應用程式方面的優點，以及您可以隱藏內部 microservices 或應用程式開發介面，用戶端應用程式，並授權該單一階層中。 

不過，而且如所述，請注意針對可能會終止 microservices' 開發自主性的大型和整合型 API 閘道器。

### <a name="data-sovereignty-per-microservice"></a>資料 sovereignty 每微服務

範例應用程式中每個微服務擁有它自己的資料庫或資料來源，而每個資料庫或資料來源會部署為另一個容器。 此設計決策的只是為了方便開發人員從 GitHub 取得程式碼、 複製它，並在 Visual Studio 或 Visual Studio 程式碼中開啟它。 或者，或者，它方便您將編譯使用.NET 核心 CLI 和 Docker CLI，自訂的 Docker 映像，然後部署並執行它們在 Docker 開發環境中。 無論如何，容器使用的資料來源可讓開發人員建置，並在幾分鐘內部署而不需要佈建外部資料庫或硬式相依性 （雲端或內部部署） 的基礎結構上與任何其他資料來源。

針對高可用性和延展性，實際執行環境中的資料庫應該基礎的雲端或內部部署，但不是在容器的資料庫伺服器。

因此，部署為 microservices （以及甚至此應用程式中的資料庫） 的單位為 Docker 容器和參考應用程式是採用 microservices 原則的多個容器應用程式。

### <a name="additional-resources"></a>其他資源

-   **eShopOnContainers GitHub 儲存機制。參考應用程式的原始程式碼**
    *https://aka.ms/eShopOnContainers/*

## <a name="benefits-of-a-microservice-based-solution"></a>微服務為基礎的解決方案的優點

像這樣基礎的微服務方案中有許多優點：

**每個微服務是相對較小，輕鬆地管理及改進**。 尤其是：

-   很容易開發人員了解並快速開始使用良好的產能。

-   容器快速入門讓開發人員更具生產力。

-   類似 Visual Studio IDE 可載入較小的專案快速，讓開發人員生產力。

-   每個微服務可以設計、 開發，並部署獨立於其他 microservices 提供靈活度，因為它是經常部署新版 microservices 更為容易。

**可延展的應用程式的個別區域**。 例如，類別目錄服務或購物籃服務可能需要向外延展，但未排序的處理程序。 Microservices 基礎結構將會整合的架構比向外延展時使用的資源方面更有效率。

**您可以將分割之間的多個小組的開發工作**。 每個服務可以由單一開發小組所擁有。 每個小組可以管理、 開發、 部署及調整其服務與其他小組分開。

**問題會更加隔離**。 如果一項服務有問題，只有該服務一開始受影響 （除非錯誤設計使用時，直接間的相依性 microservices），且其他服務可以繼續處理要求。 相較之下，一個整合的部署架構中的故障元件，可以關閉整個系統中，特別是當它牽涉到資源，例如記憶體流失。 此外，當在微服務中的問題解決後，您可以部署只受影響的微服務而不會影響應用程式的其餘部分。

**您可以使用最新技術**。 因為您可以開始獨立開發服務，並執行它們並排顯示 （這點受惠容器和.NET 核心），您可以開始使用最新技術與架構方便而不在較舊的堆疊或為整個架構所造成應用程式。

## <a name="downsides-of-a-microservice-based-solution"></a>缺點在於的微服務為基礎的解決方案

基礎的微服務方案也有一些缺點：

**分散式應用程式**。 散發應用程式將複雜性加入適用於開發人員設計及建立服務時。 例如，開發人員必須實作 interservice 通訊使用通訊協定，例如 HTTP 或 AMPQ，這會增加複雜度測試和例外狀況處理。 它也會加入至系統的延遲。

**部署的複雜性**。 有數十個 microservices 類型，並在需要高延展性 （它必須是能夠建立許多執行個體，每個服務和跨許多主機平衡這些服務） 的應用程式表示較高程度的部署複雜性 IT 作業及管理。 如果您未使用的微服務導向基礎結構 （例如 orchestrator 和排程器），額外的複雜性，可以要求比商務應用程式本身的更多的開發工作。

**不可部分完成交易**。 不可部分完成的交易，通常是多個 microservices 之間不可能。 必須採用多個 microservices 之間最終一致性的商務需求。

**增加全域資源需求**（總計記憶體、 磁碟機和網路資源的所有伺服器或主機）。 在許多情況下，當您使用 microservices 方法時，取代整合的應用程式時所需的新微服務為基礎的應用程式的全域資源數量會大於原始整合的應用程式的基礎結構需求。 這是因為資料粒度和分散式的服務的更高程度需要更通用的資源。 不過，由於低成本的一般和優點就是可以向外擴充相較於長期的成本時發展整合的應用程式的應用程式特定區域中的資源增加的使用的資源是，通常良好權衡取捨大，長期的應用程式。

**直接 client‑to‑microservice 通訊問題**。 大型的 microservices 許多應用程式時，有挑戰和限制在應用程式需要直接用戶端的微服務通訊。 一個問題是潛在的用戶端需求與每個 microservices 所公開的 Api 之間不相符。 在某些情況下，用戶端應用程式可能需要進行許多不同的要求，來撰寫可透過網際網路效率不佳，而且不適合在行動裝置的網路上的 UI。 因此，從用戶端應用程式後端系統的要求應該降到最低。

與直接以微服務的用戶端通訊的另一個問題是某些 microservices 可能使用不是 Web 上易用的通訊協定。 一個服務可能會使用二進位通訊協定，而另一個服務可能會使用 AMQP 通訊。 這些通訊協定不 firewall‑friendly，最好在內部使用。 通常，應用程式應該使用通訊協定，例如 HTTP 和 WebSockets 防火牆的外部通訊。

尚未使用此方法時直接 client‑to‑service 的另一個缺點是，它讓使用者難以重構這些 microservices 的合約。 經過一段時間開發人員可能會想要變更系統分割成服務的方式。 比方說，它們可能會合併兩個服務或服務分成兩個或多個服務。 不過，如果用戶端會直接與服務通訊，執行這種重構可以中斷與用戶端應用程式的相容性。

中所述的架構區段中，設計和建置 microservices 為基礎的複雜應用程式時，您可以考慮使用多個更細緻 API 閘道，而不是更簡單的直接 client‑to‑microservice 通訊方法。

**資料分割 microservices**。 最後，不論您的微服務架構採取哪種方法，另一項挑戰決定如何分割成多個 microservices 的端對端應用程式。 本指南的架構 > 一節中所述，有數個技術和您可以採取的方法。 基本上，您需要識別的應用程式的區域，分開的其他區域，並具有硬式相依性數目最少。 在許多情況下，這會對齊資料分割服務使用大小寫。 比方說，我們 e 商店應用程式中，我們有排序服務負責所有與訂單程序相關的商務邏輯。 我們也有目錄服務 」 和 「 購物籃服務實作的其他功能。 在理想情況下，每個服務都應該只有一小群責任。 這是類似於單一責任原則 (SRP) 套用至類別，其中說明類別應該只有其中一個原因，若要變更。 但在此情況下，它是關於 microservices，因此範圍將會大於單一類別。 最棒的微服務必須是完全自主，端對端，包括它自己的資料來源的責任。

## <a name="external-versus-internal-architecture-and-design-patterns"></a>外部與內部的架構和設計模式

外部的架構是由多個服務，遵循本指南中的架構 > 一節中所述的原則微服務架構。 不過，根據每個微服務，以及與您選擇的高層級的微服務架構無關的本質，它很常見而且有時也建議您在具有不同的內部架構，每個以不同的模式不同microservices。 Microservices 甚至可以使用不同的技術和程式語言。 圖 8-2 說明此變異。

![](./media/image2.png)

**圖 8-2**。 外部與內部架構和設計

例如，在我們*eShopOnContainers*是簡單的範例、 目錄、 購物籃和使用者設定檔 microservices （基本上，CRUD 子系統）。 因此，其內部的架構和設計是很直接。 不過，您可能需要其他 microservices，例如排序的微服務，這是更複雜，而且代表不斷改變的商務規則的網域複雜性程度高。 在這些情況下，您可能想要實作中特定的微服務，如同我們在中，網域導向設計 (DDD) 方法，以定義像更進階的模式*eShopOnContainers*排序微服務。 (我們將復一節稍後說明的實作，這些 DDD 模式*eShopOnContainers*排序微服務。)

不同的技術，每個微服務的另一個原因可能是每個微服務的本質。 例如，可能最好使用功能的程式設計語言，例如 F\#，或甚至 R 等語言，如果您的目標 AI 和機器學習服務網域，而不是其他物件導向程式設計語言如 C\#。

營收是每個微服務可以有不同的內部架構根據不同的設計模式。 並非所有 microservices 應該都實作中使用進階的 DDD 模式，就會過度工程它們。 同樣地，不應該為 CRUD 元件實作複雜 microservices 不斷改變的商務邏輯，或您可以得到低品質的程式碼。



## <a name="the-new-world-multiple-architectural-patterns-and-polyglot-microservices"></a>新的世界： 多個架構模式和 polyglot microservices

有許多軟體架構設計人員和開發人員使用的架構模式。 以下是一些 （混合架構樣式和架構模式）：

-   簡單 CRUD，單一層單一階層。

-   [傳統 N 分層](https://msdn.microsoft.com/en-us/library/ee658109.aspx#Layers)。

-   [網域導向設計 N 分層](https://blogs.msdn.microsoft.com/cesardelatorre/2011/07/03/published-first-alpha-version-of-domain-oriented-n-layered-architecture-v2-0/)。

-   [清理架構](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)(如搭配[eShopOnWeb](http://aka.ms/WebAppArchitecture))

-   [命令和查詢責任隔離](https://martinfowler.com/bliki/CQRS.html)(CQRS)。

-   [事件驅動的架構](https://en.wikipedia.org/wiki/Event-driven_architecture)(EDA)。

您也可以建立許多技術和語言，例如 ASP.NET Core Web 應用程式開發介面，NancyFx、 ASP.NET Core SignalR （適用於.NET Core 2），F microservices\#、 Node.js、 Python、 Java、 c + +、 GoLang，等等。

很重要的一點是，沒有特定架構模式或樣式或任何特定的技術，最適合所有情況。 圖 8-3 顯示 （雖然不在任何特定順序） 的一些方法和技術，可用於不同 microservices。

![](./media/image3.png)

**圖 8-3**。 多重架構模式及 polyglot microservices 全球

中所示圖 8-3，在應用程式中組成許多 microservices （繫結內容中網域導向設計術語中或只是 「 子系統 」 為自發 microservices 中），您可能會以不同方式實作每個微服務。 每個可能具有不同的架構模式，並使用不同的語言，取決於應用程式的本質，商務需求和優先順序的資料庫。 在某些情況下 microservices 可能類似。 但這不是通常情況下，因為每個子系統內容界限和需求通常不同。

比方說，是簡單的 CRUD 維護應用程式，它可能沒有意義設計及實作 DDD 模式。 但您的核心網域或核心企業，可能需要適用於更進階的模式來處理不斷改變的商務規則與商務複雜性。

特別是當您處理多個子系統所組成的大型應用程式，您不應該套用單一架構模式為基礎的單一最上層架構。 比方說，CQRS 不會套用為最上層的架構，為整個應用程式，但可能適用於一組特定的服務。

沒有任何靈丹或每個指定的情況下的正確的架構模式。 您不能有"其中一個架構模式來排除它們全部。 」 根據每個微服務的優先順序，您必須針對每個，選擇不同的方法，如下列各節所述。


>[!div class="step-by-step"]
[上一個](index.md) [下一步] (資料-驅動-crud-microservice.md)
