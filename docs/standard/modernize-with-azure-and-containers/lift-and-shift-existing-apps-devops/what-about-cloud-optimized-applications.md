---
title: "雲端最佳化應用程式呢？"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |雲端最佳化應用程式呢？"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: adcb9d2352022cc94238296562b3eb7677bdf20b
ms.sourcegitcommit: c3957fdb990060559d73cca44ab3e2c7b4d049c0
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/05/2018
---
# <a name="what-about-cloud-optimized-applications"></a>雲端最佳化應用程式呢？

雖然雲端最佳化和[雲端原生](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms)應用程式不是主要焦點本指南中，最好先了解此現代化成熟度層級，以及區別從雲端 DevOps 就緒。

圖 4-3 的應用程式現代化成熟度層級中放置雲端最佳化應用程式：

![定位雲端最佳化應用程式](./media/image3.png)

> **圖 4-3。** 定位雲端最佳化應用程式

雲端最佳化現代化成熟度等級通常會需要新的開發投資。 移動至雲端最佳化層級通常由來現代化盡量較低的成本並增加靈活性應用程式的商務需求所驅使，且會競爭優勢。 這些目標被透過最大化的 PaaS 雲端使用。 這表示不只使用 PaaS 服務，像是 DBaaS、 CaaS 和儲存體做為服務 (STaaS)，還包括將自己的應用程式和服務移轉到 PaaS 計算平台，例如 Azure 應用程式服務，或使用 orchestrators。

這種類型的現代化通常需要重構或撰寫新程式碼是適合雲端 PaaS 平台 （如 Azure 應用程式服務類似）。 它甚至可能需要架構專為雲端環境中，特別是如果您要移動到 microservices 為基礎的雲端原生應用程式模型。 這是索引鍵區別相較於雲端 DevOps 就緒，這需要任何重新架構和新的程式碼的因素。

在某些更進階的情況下，您可能會建立[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)microservices 架構，它可以形成具有高的靈活性並調整會很難達到整合架構中的限制為基礎的應用程式部署至內部部署環境。

圖 4-4 顯示當您使用雲端最佳化的模型，您可以部署應用程式的型別。 您有兩個基本選項現代化 web 應用程式和雲端原生應用程式。

> ![在雲端最佳化層級的應用程式類型](./media/image4.png)
>
> **圖 4-4。** 在雲端最佳化層級的應用程式類型

您可以藉由新增其他服務，例如人工地智慧 (AI)、 機器學習 (ML) 和 IoT 擴充基本的現代化 web 應用程式和雲端原生應用程式。 您可能會使用任一這些服務來擴充任何可行的雲端最佳化方法。

在雲端最佳化層級的應用程式中的基本差異是在應用程式架構。 [雲端原生](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms)應用程式是，根據定義，microservices 為基礎的應用程式。 雲端原生應用程式需要特殊的架構、 技術與平台，相較於龐大的 web 應用程式或傳統的多層式架構應用程式。

建立新的應用程式，請勿使用 microservices 也有意義。 有許多新的和仍然現代案例所在 microservices 為基礎的方法可能會超過您的需求。 在某些情況下，您可能只想要建立簡單的龐大的 web 應用程式，或將粗略的服務加入多層式架構應用程式。 在這些情況下，您仍可完全使用雲端的 PaaS 功能，例如 Azure 應用程式服務所提供的項目。 您仍然可以減少維護工作的限制。

此外，因為您在開發新的程式碼在雲端最佳化情況下 （完整的應用程式或部分的子系統），當您建立新的程式碼，您應該使用較新版本的.NET ([.NET Core](../../../core/index.md)和[ASP.NET Core](/aspnet/core/)，尤其)。 這是因為.NET Core 是簡式又快速的 framework，建立 microservices 和容器的特別有用。 您會取得小的記憶體使用量和快速開始在容器中，而且您的應用程式高效能。 這種方法完全符合的需求 microservices 和容器，因此您跨平台架構-能夠 Linux、 Windows Server 和 Mac (Mac 開發環境) 中執行相同的應用程式的優點。

## <a name="cloud-native-applications-with-cloud-optimized-applications"></a>與雲端最佳化應用程式的雲端原生應用程式

[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)是大型和業務關鍵應用程式的更進階或成熟狀態。 雲端原生應用程式通常需要架構和設計，而不是從頭由種現有的應用程式。 雲端原生應用程式部署到 PaaS 更簡單的雲端最佳化的 web 應用程式之間的主要差異是使用以雲端原生方法 microservices 架構建議。 雲端最佳化應用程式也可以整合 web 應用程式或多層式架構應用程式部署至雲端的 Azure App Service 等的 PaaS 服務。

[12 個因素應用程式](https://12factor.net/)（microservices 方法密切相關的模式的集合） 也視為需求[雲端原生](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms)應用程式架構。

[雲端原生運算基礎 (CNCF)](https://www.cncf.io/)是主要的升級程式的原生雲端原則。 Microsoft 是[隸屬 CNCF](https://azure.microsoft.com/blog/announcing-cncf/)。

範例定義和雲端原生應用程式的特性的詳細資訊，請參閱 Gartner 文章[如何架構設計人員和設計雲端原生應用程式](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)。 如需 microsoft 如何實作雲端原生應用程式的特定指引，請參閱[.NET microservices： 容器化的.NET 應用程式的架構](https://aka.ms/microservicesebook)。

考慮移轉至完整的應用程式最重要的因素[雲端原生](https://www.gartner.com/doc/3738117/comparing-leading-cloudnative-application-platforms)模型是您必須重新設計 microservices 為基礎的架構。 清楚地，這需要大量投資，在開發大型重構流程，因為。 選擇此選項，通常是針對需要新的層級的延展性和長期的靈活度關鍵任務應用程式。 但是，可以開始加入幾個新的情況下，microservices 邁向雲端原生，最終重構為 microservices 完整應用程式。 這是最佳的選項，在某些情況下的漸進方法。

## <a name="what-about-microservices"></a>Microservices 呢？ 

當您考慮雲端原生應用程式為您的組織，則了 microservices 以及它們如何運作相當重要。

Microservices 架構是針對全新或改良的現有應用程式建立的應用程式，您可以使用進階的方法 （在內部部署或雲端 DevOps 已備妥應用程式） 朝雲端原生應用程式。 您可以開始將少數 microservices 加入至現有的應用程式，以了解新 microservices 典範。 但是很明顯地，您需要架構設計人員和程式碼，特別是針對這種類型的架構方法。

不過，microservices 並非強制的任何新的或現代應用程式。 Microservices 不"magic bullet"，而且這些參數不會建立每個應用程式的單一的最佳方式。 您如何及何時使用 microservices 取決於您要建置的應用程式的類型。

Microservices 架構成為分散式和大型或複雜關鍵任務應用程式為基礎的自發的服務形式的多個獨立子系統的慣用的方法。 在 microservices 基礎架構中，應用程式會建立可以是獨立開發、 測試、 版本設定，部署，以及調整的服務集合。 這可包括任何相關的自發每個資料庫微服務。

您可以使用.NET 核心實作 microservices 架構的詳細檢視，請參閱可下載 PDF 電子書[.NET microservices： 容器化的.NET 應用程式的架構](https://aka.ms/microservicesebook)。 本指南也可以使用[線上](../../microservices-architecture/index.md)。

但即使是個 microservices 提供功能強大的功能與獨立部署、 強式子系統界限和技術多樣化的案例-它們也會引發許多新的挑戰。 分散式應用程式開發，例如分散且獨立的資料模型中; 與挑戰相關達到復原 microservices; 之間的通訊最終一致性; 需要和操作的複雜性。 Microservices 導入相較於傳統的整合應用程式的複雜性較高的層的級。

由於 microservices 架構的複雜度，只有特定案例與特定應用程式類型是適用於微服務為基礎的應用程式。 這些包括具有多個大型且複雜的應用程式發展子系統。 在這些情況下，值得投資更複雜的軟體架構，更長期高的靈活性和更有效率地維護應用程式。 但較不複雜的情況下，可能是較好的方式繼續進行整合的應用程式方法，或接近簡單多層式架構。

您不應該查看在做為應用程式中使用 microservices 為最後請注意，即使有重複有關這個概念，將風險"all-in 或根本沒有*。*" 您可以擴充，並藉由新增新的、 根據 microservices 小規模案例發展整合的現有應用程式。 您不需要從頭開始使用 microservices 架構方法。 事實上，我們建議您發展藉由新增新的案例中使用現有的龐大的單一或多層式架構應用程式。 最後，您可以細分成自主元件或 microservices 應用程式。 您可以啟動發展 microservices 方向，逐步解說應用程式整合。

## <a name="when-to-use-azure-app-service-for-modernizing-existing-net-apps"></a>使用 Azure App Service 種現有的.NET 應用程式的時機

當您現代化雲端最佳化成熟度層級的現有 ASP.NET web 應用程式，因為由使用.NET Framework 所開發的 web 應用程式時，您主要的相依性會在 Windows 和最有可能，Internet Information Server (IIS)。 您可以使用和部署 Windows 為基礎和以 IIS 為基礎的應用程式藉由直接部署到[Azure App Service](https://docs.microsoft.com/azure/app-service/app-service-value-prop-what-is)或先 containerizing 您的應用程式藉由使用 Windows 容器。 如果 containerizing，部署應用程式可以是 Windows 容器主機 （以 VM 為基礎） 或 Azure Service Fabric 叢集支援的 Windows 容器。

當您使用 Windows 容器時，您會取得集裝箱化的所有優點。 增加靈活性傳送和部署您的應用程式，並減少摩擦環境問題 （預備環境，開發/測試、 生產環境）。 在接下來的章節，我們移到更多詳細資料可從使用容器所獲得的好處。

本指南的撰寫，Azure 應用程式服務不支援 Windows 容器。 它支援適用於 Linux 容器。 因此，您的下一個問題可能是 「 如何選擇 Azure App Service 與 Windows 容器之間？ 」

基本上，如果 Azure 應用程式服務適用於您的應用程式，而且沒有任何伺服器或自訂的相依性封鎖要使用應用程式服務的路徑，您應該移轉現有.NET web 應用程式的應用程式服務。 這是最簡單且最有效方式維護您的應用程式。 在 Azure 中，您的應用程式也會有更簡單維護路徑因為 PaaS 基礎結構，例如 DBaaS、 CaaS 和 STaaS 優勢。

不過，如果您的應用程式具有伺服器或自訂 Azure App Service 中不支援的相依性，您可能需要考慮為基礎的 Windows 容器的選項。 伺服器或自訂的相依性的範例包括協力廠商軟體或.msi 檔案，必須安裝在伺服器上，但不是支援在 Azure App Service 中。 另一個例子是不支援在 Azure 應用程式服務中，例如使用中的全域組件快取 (GAC) 或 COM 的組件的任何其他伺服器設定 / COM + 元件。 由於 Windows 容器映像，您可以包含自訂相依性，在相同"的部署單位。 」

或者，您無法重構不支援的 Azure App Service 應用程式的區域。 根據工作的磁碟區重構都需要，您必須仔細評估是否值得。

### <a name="benefits-of-moving-to-azure-app-service"></a>移至 Azure 應用程式服務的優點

Azure App Service 是完全受管理的 PaaS 供應項目，方便您將建置 web 應用程式都由商務程序。 當您使用應用程式服務時，您會避免升級並維護 web 應用程式在內部部署與相關聯的基礎結構管理成本。 具體來說，您剪下的硬體和授權成本的內部部署執行 web 應用程式上。

如果適用於移轉至 Azure App Service web 應用程式，主要的優點是時間的簡短的移動應用程式所花費量。 應用程式服務提供非常簡單的環境中要開始。

Azure App Service 是大部分 web 應用程式的最佳選擇，因為它是最簡單的 PaaS Azure 可讓您執行 web 應用程式中。 部署及管理整合平台、 站台和調整其規模快速處理高流量負載，內建的負載平衡與流量管理員提供高可用性。

即使監視 web 應用程式是簡單，透過 Azure Application Insights。 Application Insights 是免費的應用程式服務，而不需要撰寫應用程式中的任何特殊的程式碼。 只在應用程式服務中，執行您 web 應用程式，而您將會吸引人的監視系統，進行任何其他工作。

與應用程式服務，您可以也會直接使用許多開放原始碼應用程式從 Azure Web 應用程式庫 （例如 WordPress 或 Umbraco），或您可以使用的架構和工具，您的選擇，像 ASP.NET，以便建立新的站台。 應用程式服務 WebJobs 功能可讓您更輕鬆地加入至您的 App Service web 應用程式處理的背景工作。

使用 Azure App Service Web 應用程式功能來移轉您的 web 應用程式的主要優點包括：

-   自動縮放以符合需求的忙碌時間期間，並在無訊息的時間降低成本。

-   自動站台備份來保護變更與資料。

-   高可用性和恢復功能的 Azure PaaS 平台上。

-   用於開發和預備環境，以及測試多個網站設計的部署位置。

-   負載平衡和分散式阻斷服務 (DDoS) 保護。

-   若要將使用者導向至最接近的地理部署的流量管理。

即使應用程式服務可能是新的 web 應用程式的最佳選擇，不過，對於現有的應用程式，應用程式服務可能是最好的選擇只有當應用程式服務中支援您的應用程式相依性。

### <a name="additional-resources"></a>其他資源

-   **Azure App Service 的相容性分析**  
[https://www.migratetoazure.net/Resources](https://www.migratetoazure.net/Resources)


### <a name="benefits-of-moving-to-windows-containers"></a>移至 Windows 容器的優點

使用 Windows 容器的主要優點是，您就可以更可靠且改善部署體驗，相較於非容器化應用程式。 此外，有效地使用容器的現代化應用程式可讓您的應用程式準備好進行許多其他平台和支援 Windows 容器的雲端。 移到 Windows 容器的優點會在下一節中詳細說明。

在 Azure 中 （在一般可用性、 mid 2017 年） 支援 Windows 容器的主要計算環境是 Azure Service Fabric 和基本的 Windows 容器主機 (Windows Server 2016 Vm)。 這些環境包括涵蓋在本指南中的主要的基礎結構案例。

您也可以部署到其他 orchestrators，像是 Kubernetes、 Docker Swarm，或 DC/OS Windows 容器。 目前 （早期落在 2017年），這些平台使用 Windows 容器是 Azure 容器服務中的預覽。

>[!div class="step-by-step"]
[上一頁](microsoft-technologies-in-cloud-devops-ready-applications.md)
[下一頁](how-to-deploy-existing-net-apps-to-azure-app-service.md)
