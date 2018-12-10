---
title: 一般 Web 應用程式架構
description: 使用 ASP.NET Core 和 Azure 架構現代化 Web 應用程式 | 探索一般 Web 應用程式架構
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: 3b0b109b0910eb5763ecab228115b7bc932d4a10
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53129931"
---
# <a name="common-web-application-architectures"></a>一般 Web 應用程式架構

> 「如果您認為好的架構很昂貴，那就試試壞的架構吧。」  
> _- Brian Foote 和 Joseph Yoder_

大部分傳統的 .NET 應用程式會部署為單一單位，對應至在單一 IIS appdomain 內執行的可執行檔或單一 Web 應用程式。 這是最簡單的部署模型，而且很妥善地服務許多與小型的內部公用應用程式。 不過，即使指定這種單一部署單位，大部分重要的商務應用程式都能受益於將邏輯稍微分割到數個層級。

## <a name="what-is-a-monolithic-application"></a>什麼是整合型應用程式？

整合型應用程式是在行為方面完全獨立的應用程式。 它可能會在執行作業的過程中，與其他服務或資料存放區互動，但它的行為核心會在自己的處理序內執行，且整個應用程式通常會部署為單一單位。 如果這樣的應用程式需要水平縮放，通常會在多個伺服器或虛擬機器之間複製整個應用程式。

## <a name="all-in-one-applications"></a>全方位應用程式

應用程式架構專案的最小可能數目是一個。 在這種架構中，應用程式的整個邏輯都包含在單一專案內、編譯成單一組件，並部署為單一單位。

新的 ASP.NET Core 專案，不論是在 Visual Studio 或從命令列建立，一開始都是簡單的「全方位」整合型。 它包含應用程式的所有行為，包括簡報、商務和資料存取邏輯。 圖 5-1 顯示單一專案應用程式的檔案結構。

![](./media/image5-1.png)

**圖 5-1。** 單一專案 ASP.NET Core 應用程式。

在單一專案案例中，關注點分離是透過資料夾的使用而達成。 預設範本包含 Models、Views 和 Controllers 等 MVC 模式責任的個別資料夾，以及適用於資料和服務的其他資料夾。 在這種安排中，應該盡量將簡報詳細資料限制在 Views 資料夾，且資料存取實作詳細資料應該限制為保留在 Data 資料夾中的類別。 商務邏輯應該位於 Models 資料夾內的服務和類別。

雖然簡單，但單一專案整合型解決方案有一些缺點。 隨著專案的大小和複雜度增加，檔案和資料夾的數目也會持續成長。 使用者介面 (UI) 考量 (模型、檢視、控制器) 位於不依字母順序分組在一起的多個資料夾中。 當有其他 UI 層級建構，例如 Filter 或 ModelBinder ，新增到它們自己的資料夾中時，此問題只會惡化。 商務邏輯散佈在 Models 和 Services 資料夾之間，且不會清楚指出哪些資料夾中的哪些類別應該相依於哪些其他類別。 這種在專案層級缺乏組織的情形經常會導致 [Spaghetti Code](https://deviq.com/spaghetti-code/) (非結構程式碼)。

為了解決這些問題，應用程式經常演化成多專案解決方案，其中每個專案被視為位於應用程式的特定「層級」。

## <a name="what-are-layers"></a>什麼是「層級」？

當應用程式變得越來越複雜時，管理這種複雜性的一種方法，是根據應用程式的責任或關注點來分解應用程式。 這會遵循關注點分離原則，並有助於成長中的程式碼庫維持井井有條，以便開發人員可以輕鬆地找到特定的功能實作在哪裡。 不過，除了程式碼組織之外，分層的架構還提供許多優勢。

藉由將程式碼組織成層級，就可以在整個應用程式重複使用通用的低階功能。 這種重複使用是有益的，因為這表示需要撰寫較少的程式碼，且因為它可讓應用程式在單一實作標準化，遵循[一次且僅一次 (DRY)](https://en.wikipedia.org/wiki/Don%27t_repeat_yourself) 準則。

使用分層式架構，應用程式可以強制限制哪些層級可以與其他層級通訊。 這有助於達成封裝。 變更或取代層級時，只有處理該層級的層級會受到影響。 藉由限制哪些層級相依於哪些其他層級，變更的影響可以得到緩解，讓單一變更不會影響整個應用程式。

層級 (和封裝) 使得可以更容易取代應用程式中的功能。 例如，針對持續性，應用程式一開始可能使用自己的 SQL Server 資料庫，但後來可以選擇使用以雲端為基礎的持續性策略，或 Web API 之後的策略。 如果應用程式已將其持續性實作正確封裝在邏輯層內，該 SQL Server 特定的層級可以取代為實作相同公用介面的新層級。

除了為了回應未來的需求變更而換掉實作的可能性，應用程式層級也能更輕鬆地基於測試目的而換掉實作。 您不必撰寫測試來操作應用程式的實際資料層級或 UI 層級，這些層級可以在測試階段取代為假的實作，以提供已知的回應給要求。 這通常可讓測試更容易撰寫且更快速地執行 (相較於針對應用程式的實際基礎結構來執行測試)。

邏輯分層是改善企業軟體應用程式中的程式碼組織的常見技術，並且有數種方式可以將程式碼組織成層級。

> [!NOTE]
 > 「層級」代表應用程式中的邏輯分隔。 應用程式邏輯實際上分佈至不同伺服器或處理程序時，這些個別的實體部署目標稱為「層」。 可能 (而且很常見) 會有 N 層應用程式部署到單一層。

## <a name="traditional-n-layer-architecture-applications"></a>傳統的「N 層」架構應用程式

將應用程式邏輯組織成為層級的最常見方式顯示在圖 5-2 中。

![](./media/image5-2.png)

**圖 5-2.** 一般應用程式層級。

這些層級經常縮寫為 UI、BLL (商務邏輯層)，以及 DAL (資料存取層)。 使用此架構，使用者會透過 UI 層提出要求，這個層級只與 BLL 互動。 接著，BLL 可以呼叫 DAL 以處理資料存取要求。 UI 層應該不會對 DAL 直接提出任何要求，也不應直接透過其他方式與持續性互動。 同樣地，BLL 應該只能透過 DAL 與持續性互動。 如此一來，每個層級都會有自己的已知責任。

這種傳統分層方法的一項缺點是編譯時間相依性會從頂端一直到底部。 也就是說，UI 層相依於 BLL，BLL 相依於 DAL。 這表示，通常保存應用程式中最重要邏輯的 BLL，會相依於資料存取實作細節 (且通常相依於資料庫的存在)。 在這類架構中測試商務邏輯經常會很困難，需要一個測試資料庫。 相依性反轉原則可用來解決這個問題，您將會在下一節看到。

圖 5-3 顯示範例解決方案，會依責任 (或層級) 將應用程式分成三個專案。

![](./media/image5-3.png)

**圖 5-3.** 簡單的整合型應用程式，含三個專案。

雖然此應用程式為了組織的目的而使用數個專案，但它仍會部署為單一單位，且其用戶端會以單一 Web 應用程式與它互動。 這樣能有非常簡單的部署程序。 圖 5-4 將示範這類應用程式可如何使用 Azure 來裝載。

![](./media/image5-4.png)

**圖 5-4.** Azure Web 應用程式的簡單部署

當應用程式需求成長，可能需要更複雜且功能強大的部署解決方案。 圖 5-5 示範更複雜的部署計劃範例，它支援額外的功能。

![](./media/image5-5.png)

**圖 5-5.** 將 Web 應用程式部署至 Azure App Service

就內部而言，根據責任將此專案組織成多個專案，可以改善應用程式的可維護性。

此單位可以相應增加或相應放大以充分利用雲端隨選延展性。 相應增加意思是新增額外的 CPU、記憶體、磁碟空間或其他資源到裝載應用程式的伺服器。 相應放大意思是新增這類伺服器的額外執行個體，不論這些是實體伺服器還是虛擬機器。 當您的應用程式裝載於多個執行個體時，負載平衡器會用於將要求指派給個別的應用程式執行個體。

在 Azure 中調整 Web 應用程式最簡單的方式，是在應用程式的 App Service 方案中手動設定調整。 圖 5-6 顯示適當的 Azure 儀表板畫面，以設定多少個執行個體正在服務應用程式。

![](./media/image5-6.png)

**圖 5-6。** 在 Azure 中調整應用程式服務方案。

## <a name="clean-architecture"></a>Clean Architecture

遵循相依性反轉準則以及領域驅動設計 (DDD) 準則的應用程式通常會達到類似的架構。 這個架構多年來有了許多名稱。 最早的其中一個名稱是 Hexagonal Architecture，後來則是 Ports-and-Adapters。 最近，它被引用為 [Onion Architecture](https://jeffreypalermo.com/blog/the-onion-architecture-part-1/) 或 [Clean Architecture](https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html)。 本電子書使用第二個名稱 Clean Architecture 作為此架構的名稱。

> [!NOTE]
> Clean Architecture 一詞可以套用至使用 DDD 原則建置的應用程式，以及不是使用 DDD 原則建置的應用程式。 在前者的案例，這種組合可能會稱為 Clean DDD Architecture。

Clean Architecture 會將商務邏輯和應用程式模型放在應用程式的中央位置。 不讓商務邏輯相依於資料存取或其他基礎結構的關注點，而是反轉此相依性：基礎結構和實作詳細資料相依於應用程式核心。 藉由在應用程式核心定義抽象或介面，然後它們會由基礎結構層中定義的類型所實作，即可達到此目的。 視覺化這個架構的常見方式是使用一系列的同心圓，類似於洋蔥。 圖 5-7 示範這種架構的表示法。

![](./media/image5-7.png)

**圖 5-7.** Clean Architecture；洋蔥檢視

在此圖中，相依性會流向最內層的圓形。 應用程式核心從其在此圖核心的位置擷取其名稱。 如圖所示，應用程式核心對於其他應用程式層級沒有任何相依性。 應用程式的實體和介面位於正中心。 在外面一點，但仍在應用程式核心中，則是網域服務，它們通常會實作內部圓形中定義的介面。 在應用程式核心外面，UI 與基礎結構層都相依於應用程式核心，但彼此不一定相依。

圖 5-8 顯示更傳統的水平分層圖，更能反映出 UI 和其他層級之間的相依性。

![](./media/image5-8.png)

**圖 5-8.** Clean Architecture；水平層檢視

請注意，實心箭號代表編譯時期相依性，而虛線箭頭代表僅限執行階段的相依性。 使用 Clean Architecture，UI 層適用於在編譯時期，在應用程式核心中定義的介面，並且在理想情況下，應該不知道基礎結構層定義的實作類型。 不過，在執行階段，必須有這些實作類型，應用程式才能執行，因此它們必須存在並透過相依性插入而連接到應用程式核心介面。

圖 5-9 顯示遵循這些建議建置時，更詳細的 ASP.NET Core 應用程式架構。

![ASPNET Core 架構](./media/image5-9.png)

**圖 5-9.** 遵循 Clean Architecture 的 ASP.NET Core 架構圖表。

因為應用程式核心不會相依於基礎結構，所以很容易就能為此層級撰寫自動化的單元測試。 圖 5-10 和 5-11 顯示測試如何配合這個架構。

![UnitTestCore](./media/image5-10.png)

**圖 5-10.** 隔離進行應用程式核心的單元測試。

![IntegrationTests](./media/image5-11.png)

**圖 5-11.** 整合測試具有外部相依性的基礎結構實作。

因為 UI 層對於基礎結構專案中定義的類型沒有直接的相依性，所以同樣很容易就能換掉實作，以方便測試或回應不斷變更的應用程式需求。 ASP.NET Core 的內建相依性插入使用和支援，可讓此架構成為建構重要整合型應用程式的最適當方式。

對於整合型應用程式，應用程式核心、基礎結構和 UI 專案全都執行為單一應用程式。 執行階段應用程式架構看起來可能圖 5-12。

![ASP.NET Core 架構 2](./media/image5-12.png)

**圖 5-12.** 範例 ASP.NET Core 應用程式的執行階段架構。

### <a name="organizing-code-in-clean-architecture"></a>以 Clean Architecture 組織程式碼

在 Clean Architecture 解決方案中，每個專案都有清楚的責任。 因此，某些類型屬於每個專案，而您將經常找到對應至適當專案中這些類型的資料夾。

應用程式核心會保存商務模型，其中包含實體、服務和介面。 這些介面包含將使用基礎結構執行的作業抽象，例如資料存取、檔案系統存取、網路呼叫等。有時在這個層級定義的服務或介面會需要使用不相依於 UI 或基礎結構的非實體類型。 這些可以定義為簡單的資料傳輸物件 (DTO)。

### <a name="application-core-types"></a>應用程式核心類型

- 實體 (持續保存的商務模型類別)
- 介面
- 服務
- DTO

基礎結構專案通常會包含資料存取實作。 在一般 ASP.NET Core Web 應用程式中，這些實作包括 Entity Framework (EF) DbContext、已定義的任何 EF Core `Migration` 物件和資料存取實作類別。 擷取資料存取實作程式碼的最常見方式，是透過使用 [Repository design pattern](https://deviq.com/repository-pattern/) (存放庫設計模式)。

除了資料存取實作，基礎結構專案也應包含必須與基礎結構關注點互動的服務實作。 這些服務應該實作在應用程式核心定義的介面，且基礎結構應該有應用程式核心專案的參考。

### <a name="infrastructure-types"></a>基礎結構類型

- EF Core 類型 (`DbContext`、`Migration`)
- 資料存取實作類型 (存放庫)
- 基礎結構特定服務 (例如 `FileLogger` 或 `SmtpNotifier`)

ASP.NET Core MVC 應用程式中的使用者介面層是應用程式的進入點。 這個專案應該參考應用程式核心專案，而其類型應該嚴格地透過應用程式核心中定義的介面與基礎結構互動。 在 UI 層不應該允許基礎結構層類型的任何直接具現化或靜態呼叫。

### <a name="ui-layer-types"></a>UI 層類型

- Controllers
- 篩選條件
- 檢視
- ViewModels
- 啟動

啟動類別負責設定應用程式，以及將實作類型連接至介面，讓相依性插入能在執行階段正常運作。

> [!NOTE]
> 若要在 UI 專案之 Startup.cs 檔的 ConfigureServices 中連接相依性插入，專案可能需要參考基礎結構專案。 此相依性可以使用自訂 DI 容器來輕易地去除。 基於此範例的目的，最簡單的方法是允許 UI 專案參考基礎結構專案。

## <a name="monolithic-applications-and-containers"></a>整合型應用程式和容器

您可以建置單一且以整合型部署為基礎的 Web 應用程式或服務，並將它部署為容器。 在應用程式內，它可能不是整合型，而是組織成幾個程式庫、元件或層級。 從外部來看，它是單一容器，像是單一處理序、單一 Web 應用程式或單一服務。

為了管理此模型，您會部署單一容器來代表應用程式。 若要調整，只要透過前端負載平衡器新增額外的複本即可。 由於是在單一容器或 VM 中管理單一部署，因此很簡單。

![](./media/image5-13.png)

您可以在每個容器中包含多個元件/程式庫或內部層級，如圖 5-13 所示。 不過，遵循「容器執行一項動作並在一個處理序中執行該動作」的容器準則時，整合型模式可能會是一項衝突。

如果應用程式成長而需要擴充，此方法的缺點便會浮現。 若整個應用程式都擴充，則不成問題。 不過，在大多數情況下，應用程式只需要調整幾個造成阻礙的部分，其他元件則較少使用。

使用一般的電子商務範例，您可能需要調整的是產品資訊元件。 瀏覽產品的客戶比購買的人多。 比起使用付款管道，會有更多客戶使用其購物籃。 新增留言或檢視其購買歷程記錄的客戶較少。 而且在單一區域中，您可能只有少數幾個員工，需要管理內容和行銷活動。 藉由調整整合型設計，所有的程式碼會多次部署。

除了「全部調整」的問題之外，單一元件的變更都需要完整地重新測試整個應用程式，並完整重新部署所有執行個體。

整合型方法很常見，許多組織也正在使用這個架構方法進行開發。 許多有足夠好的結果，但其他則只是達到限制。 許多組織使用此模型來設計其應用程式，因為工具和基礎結構很難建置服務導向架構 (SOA)，而且在應用程式成長之前也看不到此需求。 如果您發現您達到整合型方法的限制，下個邏輯步驟可能是分解應用程式，以便讓它能更充分利用容器和微服務。

![](./media/image5-14.png)

您可以針對每個執行個體使用專用 VM，在 Microsoft Azure 中部署整合型應用程式。 您可以使用 [Azure 虛擬機器擴展集](https://docs.microsoft.com/azure/virtual-machine-scale-sets/)輕鬆地調整 VM。 [Azure App Service](https://azure.microsoft.com/services/app-service/) 可以執行整合型應用程式並輕鬆地調整執行個體，而不必管理 VM。 Azure App Service 也可以執行 Docker 容器的單一執行個體，以簡化部署。 使用 Docker 時，您可以部署單一 VM 作為 Docker 主機，並執行多個執行個體。 使用 Azure 平衡器，如圖 5-14 中所示，您可以管理調整。

您可以透過傳統部署技術來管理不同主機的部署， 並可以手動執行 **docker run** 等命令，或是透過持續傳遞 (CD) 管線等自動化方法來管理 Docker 主機。

### <a name="monolithic-application-deployed-as-a-container"></a>整合型應用程式部署為容器

使用容器來管理整合型應用程式部署有許多優點。 調整容器執行個體遠比部署額外的 VM 更輕鬆快速。 即使是使用虛擬機器擴展集來調整 VM，它們也需要時間具現化。 當部署為應用程式執行個體時，應用程式的設定是作為 VM 的一部分管理。

以 Docker 映像來部署更新會更快且網路效率更高。 Docker 映像通常只要幾秒鐘就能啟動，因此可加速推出。 卸除 Docker 執行個體很容易，只要發出 `docker stop` 命令即可，而且通常不到一秒就會完成。

容器的設計原本就是不可變的，您永遠不需要擔心 VM 損毀，而更新指令碼可能會忘記處理部分特定設定或是檔案殘留在磁碟上。

您可以使用 Docker 容器進行更簡單 Web 應用程式的整合型部署。_如此可改善持續整合與持續部署管線，並協助完成部署到生產的過程。不再產生「它可在我的電腦中運作，但為何無法在生產環境中運作？」的疑問_

微服務架構有許多好處，但這些好處的代價是複雜度會增加。 在某些情況下，這些代價會遠大於所獲得的好處，因此在單一容器或幾個容器中執行整合型部署應用程式會是較佳的選擇。

整合型應用程式可能不容易分解成多個適當分離的微服務。 微服務應該彼此獨立運作，才能提供復原能力更高的應用程式。 如果您無法獨立切割應用程式的功能，將它分離只會增加複雜度。

應用程式可能還不需要獨立擴充功能。 許多應用程式若其規模需要超過單一執行個體，則可透過複製整個執行個體之相當簡單的程序來完成。 執行額外工作以將應用程式分成不同服務的好處有限，而擴充應用程式的整個執行個體不僅簡單且符合成本效益。

在開發應用程式初期，您可能不清楚自然功能邊界止於何處。 當您開發最低可行性產品 (Minimum Viable Product) 時，自然分離的情況可能尚不明顯。 有些情況可能是暫時性的。 您可以先建立一個整合型應用程式，稍後再將某些功能分成微服務來開發和部署。 其他情況可能對應用程式的問題空間很重要，這表示應用程式可能永遠不會分成多個微服務。

將應用程式分成許多不同的處理序也會引進額外負荷。 將功能分成不同處理序的複雜度更高。 通訊協定變得更複雜。 您必須在服務之間使用非同步通訊，而不是方法呼叫。 當您移至微服務架構時，您需要新增在 eShopOnContainers 應用程式的微服務版本中實作的許多建置組塊：事件匯流排處理、訊息復原與重試、最終一致性等等。

更簡單的 [eShopOnWeb 參考應用程式](https://github.com/dotnet-architecture/eShopOnWeb)支援單一容器的整合型容器使用。 此應用程式包含兩個 Web 應用程式：一個使用傳統 MVC，另一個使用 Razor Pages。 這兩個應用程式可使用 `docker-compose build` 和 `docker-compose up` 命令從方案根目錄啟動。 此命令會使用在每個 Web 專案根目錄中找到的 `Dockerfile`，為每個 Web 執行個體設定不同的容器，並在個別連接埠上執行每個容器。 您可以從 GitHub 下載此應用程式的來源並在本機執行。 即使是此整合型應用程式也可以透過部署至容器環境獲利。

其中一個優點是，容器化部署表示每個應用程式執行個體都會在相同的環境中執行。 這包括進行早期測試和開發的開發人員環境。 開發小組可以在與生產環境相符的容器化環境中執行應用程式。

此外，擴充容器化應用程式的成本較低。 使用容器環境可共用的資源比傳統 VM 環境更多。

最後，容器化應用程式會強制分離商務邏輯與存放區伺服器。 當應用程式擴充時，多個容器全部都會依賴單一實體儲存媒體。 此儲存媒體通常會是執行 SQL Server 資料庫的高可用性伺服器。

## <a name="docker-support"></a>Docker 支援

`eShopOnWeb` 專案是在 .NET Core 上執行。 因此，它可以在 Linux 或 Windows 容器中執行。 請注意，若是 Docker 部署，您想要針對 SQL Server 使用相同的主機類型。 Linux 容器允許較小的使用量，而且是偏好選項。

您可以使用 Visual Studio 2017 將 Docker 支援新增至現有的應用程式，方法是以滑鼠右鍵按一下 [方案總管] 中的專案，然後選擇 [新增] > [Docker 支援]。 這會新增所需的檔案，並修改專案以使用這些檔案。 目前的 `eShopOnWeb` 範例已有這些檔案。

方案層級 `docker-compose.yml` 檔案包含要建置哪些映像及要啟動哪些容器的相關資訊。 該檔案可讓您使用 `docker-compose` 命令同時啟動兩個 Web 應用程式版本。 您也可以使用它來設定相依性，例如個別的資料庫容器。

```yml
version: '3'

services:
  eshopwebrazor:
    image: eshopwebrazor
    build:
      context: .
      dockerfile: src/WebRazorPages/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5107:5107"

  eshopwebmvc:
    image: eshopwebmvc
    build:
      context: .
      dockerfile: src/Web/Dockerfile
    environment:
      - ASPNETCORE_ENVIRONMENT=Development
    ports:
      - "5106:5106"

networks:
  default:
    external:
      name: nat
```

`docker-compose.yml` 檔案會參考 `Web` 和 `WebRazorPages` 專案中的 `Dockerfile`。 `Dockerfile` 是用來指定將使用的基底容器，以及如何在其上設定應用程式。 `WebRazorPages` 的 `Dockerfile`：

```
FROM microsoft/dotnet:2.1-aspnetcore-runtime AS base
WORKDIR /app
EXPOSE 80

FROM microsoft/aspnetcore-build:2.1.300-preview1 AS build
RUN npm install -g bower@1.8.4
WORKDIR /src
COPY . .
WORKDIR /src/src/WebRazorPages
RUN dotnet restore -nowarn:msb3202,nu1503
RUN dotnet build --no-restore -c Release -o /app

FROM build AS publish
RUN dotnet publish --no-restore -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "Microsoft.eShopWeb.RazorPages.dll"]
```

### <a name="troubleshooting-docker-problems"></a>Docker 問題疑難排解

一旦您執行容器化應用程式，它會一直執行到您停止為止。 您可以使用 `docker ps` 命令，來檢視哪些容器正在執行。 您可以透過使用 `docker stop` 命令並指定容器識別碼，來停止執行容器。

請注意，執行 Docker 容器可能會繫結至您嘗試在開發環境中使用的連接埠。 如果您嘗試使用與執行 Docker 容器相同的連接埠來執行或偵錯應用程式，您會收到錯誤，指出伺服器無法繫結至該連接埠。 同樣地，停止容器應能解決此問題。

如果您想要使用 Visual Studio 將 Docker 支援新增至應用程式，請確定這樣做時，Docker 正在執行。 當您啟動精靈時，如果 Docker 未執行，精靈將無法正確執行。 此外，精靈會檢查您目前的容器選擇，以新增正確的 Docker 支援。 如果您想要新增 Windows 容器的支援，您需要在有執行中 Docker 並已設定 Windows 容器的同時執行精靈。 如果您想要新增 Linux 容器的支援，請在有執行中 Docker 並已設定 Linux 容器的同時執行精靈。

> ### <a name="references--common-web-architectures"></a>參考資料 - 一般 Web 架構
>
> - **Clean Architecture**  
>   <https://8thlight.com/blog/uncle-bob/2012/08/13/the-clean-architecture.html>
> - **Onion Architecture**  
>   <https://jeffreypalermo.com/blog/the-onion-architecture-part-1/>
> - **存放庫模式**  
>   <https://deviq.com/repository-pattern/>
> - **Clean Architecture 解決方案範例**  
>   <https://github.com/ardalis/cleanarchitecture>
> - **架構微服務電子書**  
>   <https://aka.ms/MicroservicesEbook>

>[!div class="step-by-step"]
>[上一頁](architectural-principles.md)
>[下一頁](common-client-side-web-technologies.md)