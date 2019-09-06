---
title: 利用 Azure 雲端服務及 Windows 容器將現有的 .NET 應用程式現代化 (第 2 版)
description: 了解如何利用這本電子書，將現有的應用程式原形移轉到 Azure 雲端及容器並加以現代化。
ms.date: 04/28/2018
ms.openlocfilehash: 99265e6179554214ae1684b6ea266693be7f80c1
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70374169"
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-2nd-edition"></a>利用 Azure 雲端服務及 Windows 容器將現有的 .NET 應用程式現代化 (第 2 版)

![將 .NET 應用程式現代化指南的封面影像。](./media/index/web-application-guide-cover-image.png)

發行者  
Microsoft Corporation  
Microsoft Press 及 Microsoft DevDiv 部門  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2018 by Microsoft Corporation  

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製。

本書免費提供，為電子書的格式，可以從 Microsoft 的多種不同管道取得，例如 <https://dot.net/architecture>。

若您對本書有相關問題，請傳送電子郵件到 [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路的網站參考) 如有變更，恕不另行通知。

此處所描述的一些範例僅供說明，純屬虛構。 任何實際關聯或連結純屬巧合。

Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。 所有其他商標皆屬於其各自擁有者的財產。

作者:
> **Cesar de la Torre**，Microsoft Corp. .NET 產品小組資深專案經理

參與者和檢閱者：
> **Scott Hunter**，Microsoft .NET 小組合夥人暨 PM 主管  
> **Paul Yuknewicz**，Microsoft Visual Studio Tools 小組首席 PM 經理  
> **Lisa Guthrie**，Microsoft Visual Studio Tools 小組資深專案經理  
> **Ankit Asthana**，Microsoft .NET 小組 PM 總經理  
> **Unai Zorrilla**，Plain Concepts 開發人員主管  
> **Javier Valero**，Grupo Solutio 營運長  

## <a name="introduction"></a>簡介

當您決定要將 Web 應用程式或服務現代化，並將其移至雲端時，您未必需要全面重新建構您的應用程式。 基於成本和時間的限制，使用微服務這類先進方法來重新建構應用程式，不一定每次都適合。 重新建構應用程式也不是必然，必須取決於應用程式的類型。 為了讓組織的雲端移轉策略發揮最高成本效益，考量您的業務需求與應用程式需求便成了重要的一環。 您必須判斷：

- 哪些應用程式需要轉換或重新建構。

- 哪些應用程式只需要進行部分修改。

- 哪些應用程式沒辦法直接「隨即轉移」到雲端。

## <a name="about-this-guide"></a>關於本指南

本指南主要著重於現有 Microsoft .NET Framework Web 應用程式或服務導向應用程式的第一次現代化，意即將工作負載移至較新或更現代化環境的動作，所以不會大幅改變應用程式的程式碼與基本架構。 

本指南也摘要列出將應用程式移至雲端，以及使用特定一組新技術及方法 (例如 Windows 容器及 Azure 支援之 Windows 容器中的相關計算平台)，將應用程式局部現代化的好處。

## <a name="path-to-the-cloud-for-existing-net-applications"></a>現有 .NET 應用程式前往雲端的路徑

組織通常會選擇移至雲端以提升其應用程式的靈活度與速度。 您可以在數分內於雲端設置上千個伺服器 (VM)，相較之下，設置內部部署伺服器通常需要幾個禮拜的時間。

將應用程式移轉到雲端並沒有一體適用的策略。 適合您的移轉策略取決於組織的需求與優先順序，以及所要移轉的應用程式種類。 並非所有應用程式都適合移至平台即服務 ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) 模型，或是開發[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)應用程式模型。 在許多情況下，您可以根據業務需求，使用分階或累進式方法將資產移至雲端。

對於組織中，可以長期保持敏捷度與價值的現代應用程式，投資*雲端原生*應用程式架構可能會對您有所助益； 但對於現有或舊版資產的應用程式，其關鍵在於如何花最少的時間與金錢，將這些應用程式移至雲端 (不重新建構或變更程式碼)，以從中獲取最大的利益。

圖 1-1 呈現了您採取累進方式將現有的 .NET 應用程式移至雲端時，可以採用的路徑。

 ![現有 .NET 應用程式及服務的現代化路徑](./media/image1-1.png)

**圖 1-1**。 現有 .NET 應用程式及服務的現代化路徑

每個移轉方法都有其優點及使用理由。 在將應用程式移至雲端時，您可以選擇單一方法，也可以從多種方法中擷取某些元件。 個別應用程式並不侷限於單一方法或成熟度。 比方說，一般混合方法會有某些內部部署元件，再加上雲端中的其他元件。

以下是每個應用程式成熟度等級的定義及簡短說明：

**等級 1：已具備雲端基礎結構的**應用程式：使用此移轉方式，您只需要將目前的內部部署應用程式移轉或重新裝載至基礎結構即服務 ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) 平台即可。 您的應用程式結構和以前幾乎相同，但您現已將其部署到雲端中的 VM。
這種簡單的移轉類型在業界我們稱為「原形移轉」。

**等級 2：雲端最佳化**應用程式：此等級仍無須重新架構或改變重要的程式碼。您可以利用容器和其他雲端管理的服務等現代化技術，在雲端中執行您的應用程式，從而獲取更多好處。 您可藉由精簡企業開發營運 (DevOps) 程序來增加應用程式的靈活度，加快出貨速度。 您可以使用採用 Docker 引擎的 Windows 容器等技術來達到此目的。 容器免除了在多個階段部署時，因應用程式相依性而引起的衝突。 在此成熟度模型中，您一方面可以在 IaaS 或 PaaS 上部署容器，一方面可以利用更多雲端管的資料庫服務、快取即服務、監視及持續整合/持續部署 (CI/CD) 管線服務等等。

第三等級的成熟度是雲端的終極目標，但對大多數應用程式而言並非必要，且非本指南的主要重點：

**等級 3：雲端原生**應用程式：此移轉方式通常是為了因應業務需求，並將目標放在將任務關鍵性應用程式現代化上。 在此等級中，您可使用 PaaS 服務將您的應用程式移至 PaaS 運算平台上。 您可以實作[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)應用程式及微服務架構，來發展具長期靈活度的應用程式，以及擴展新界限。 這種類型的現代化通常需要專為雲端設計的架構。 尤其在移至雲端原生應用程式及微服務式模型的時候，通常會需要撰寫新的程式碼。 這項方法可協助您取得在整合型及內部部署應用程式環境中難以達到的優點。

表 1-1 描述了選擇各項移轉或現代化方法的主要優點及理由。

| **雲端基礎結構就緒** <br /> *隨即轉移* | **雲端最佳化** <br /> *現代化* | **雲端原生** <br /> *現代化、重新架構及重新編寫* |
|---|---|---|
| **應用程式的計算目標** |
| 在 Azure 中部署到 VM 的應用程式 | 部署到 Azure App Service、Azure 容器執行個體 (ACI)、搭載容器的 VM 或 AKS (Azure Kubernetes Service) 的整合型或多層式架構 (N-Tier) 應用程式 | 容器化 Azure Kubernetes Service (AKS) 上的微服務及 (或) Azure Functions 上的無伺服器微服務。 |
| **資料目標** |
| SQL 或 VM 上的任何關聯式資料庫 | Azure SQL Database 受控執行個體或雲端中其他的受控資料庫。 | 依據 Azure SQL Database、Azure Cosmos DB 或雲端中其他受控資料庫上的微服務微調資料庫 |
| **優點**|
| <li>無須重新架構，也無須增加新的程式碼 <li> 以最少心力快速移轉 <li> Azure 中支援的最普及選項 <li> 保證基本可用性 <li> 移至雲端後更容易現代化 | <li> 無須重新架構 <li> 最少的程式碼/設定變更 <li> 因容器而獲得改善的部署及 DevOps 發行靈活度 <li> 增加密度並降低部署成本 <li> 應用程式及相依性的可攜性 <li> 彈性的主機目標：PaaS 方法或 IaaS | <li> 雲端架構，可以發揮雲端最大效益，但需要編寫新的程式碼 <li> 微服務雲端原生方法 <li> 現代化的任務關鍵性應用程式，具備可高度靈活調整的雲端復原能力 <li> 完整受控的服務 <li> 經最佳化以調整規模 <li> 為子系統的自主靈活度最佳化 <li> 建基於部署及 DevOps |
| **挑戰** |
| <li> 除了轉入營業費用或關閉資料中心之外，雲端價值較低 <li> 幾乎不需要管理：沒有 OS 或中介軟體修補；可能會使用基礎結構解決方案，像是 Terraform、Spinnaker 或 Puppet | <li> 對於開發人員與 IT 營運來說，容器化是學習曲線之外的另一個步驟 <li> DevOps 與 CI/CD 管線通常是此方式的必備條件。 若目前的組織文化中沒有這兩項，就可能形成另一項挑戰| <li> 需要重新架構雲端原生應用程式及微服務架構，而且在現代化時，通常需要重新分解或重新編寫重要的程式碼 (增加時間及預算)|
> **表 1-1。** 現有 .NET 應用程式及服務現代化路徑的優點與挑戰

### <a name="key-technologies-and-architectures-by-maturity-level"></a>依成熟度等級分階的主要技術及架構

.NET Framework 應用程式最初從 2001 年年底推出的 .NET Framework 1.0 版開始。 之後，公司移往了更新的版本 (例如 2.0、3.5 及 .NET 4.x)。 這些應用程式大多在 Windows Server 及 Internet Information Server (IIS) 上執行，而且使用像是 SQL Server、Oracle、MySQL 或任何其他 RDBMS 一類的關聯式資料庫。

如今，大多數現有的 .NET 應用程式可能以 .NET Framework 4.x 甚至是 .NET Framework 3.5 為基礎，且使用 ASP.NET MVC、ASP.NET Web Forms、ASP.NET Web API、Windows Communication Foundation (WCF)、ASP.NET SignalR 及 ASP.NET Web Pages 等 Web 架構。 這些已建立的 .NET Framework 技術相依於 Windows。 若您只是想移轉舊版應用程式，而且希望將對應用程式基礎結構產生的變更降至最低，該相依性是重要的考慮因素。

圖 1-2 顯示了在三個雲端成熟度等級中，各自使用的主要技術及架構樣式：

![各個成熟度等級將現有 .NET Web 應用程式現代化時使用的主要技術](./media/image1-2.png)

**圖 1-2。** 將現有 .NET Web 應用程式現代化時，各個成熟度等級使用的主要技術

圖 1-2 強調了大多數常見案例，然而在架構方面有可能會出現許多混合變化。 比方說，成熟度模型不僅適用現有 Web 應用程式中的整合型架構，也適用於服務導向、多層式架構 (N-Tier) 及其他架構樣式變化。 依賴其中任何一種架構類型及相關技術的程度高低，決定應用程式的整體成熟度等級。

現代化程序中的每個成熟度等級都與下列主要技術和方法相關：

- **具備雲端基礎結構** (重新裝載或基本原形移轉)：許多組織一開始都只想要快速執行雲端移轉策略。 因此會選擇重新裝載應用程式。 大多數重新裝載作業都能透過使用 [Azure Migrate](https://aka.ms/azuremigrate) 自動執行，此服務會提供必要的指導、深入解析及機制，協助您透過 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) 及 [Azure 資料庫移轉服務](https://azure.microsoft.com/campaigns/database-migration/)等雲端工具移轉到雲端。 您也可以手動設定重新裝載，使您能在將舊版應用程式移至雲端時，了解有關您資產的基礎結構詳細資料。 比方說將應用程式移至 Azure 上的 VM，您可能幾乎完全不需要修改，或可能只需小幅度變更設定即可。 在此情況中的網路功能與內部部署環境相似，特別是當您在 Azure 中建立虛擬網路的時候。

- **雲端最佳化** (受控服務及 Windows 容器)：此模型的重點在於，完全不需要變更應用程式的核心架構，只需要最佳化一些重要的部署，就能發揮雲端的最大效益。 基本步驟是將 [Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)支援新增至您現有的 .NET Framework 應用程式。 這項重要的步驟 (容器化) 不會影響程式碼，因此投入原形移轉的整體資源不大。 您可以使用 [Image2Docker](https://github.com/docker/communitytools-image2docker-win)、Visual Studio 以及 Visual Studio Tools for [Docker](https://www.docker.com/)。 Visual Studio 會自動選擇 ASP.NET 應用程式及 Windows 容器映像的智慧型預設。 這些工具提供了迅速的內部迴圈，以及容器到 Azure 的快速路徑， 並改善您部署到多個環境時的靈活度。 接著進入生產環境，若您偏好 IaaS 方式，您可以將 Windows 容器部署到 [Azure Web App for Containers](https://azure.microsoft.com/services/app-service/containers/)、[Azure 容器執行個體 (ACI)](https://azure.microsoft.com/services/container-instances/)，以及搭載 Windows Server 2016 與容器的 Azure VM。 對於更複雜的多容器應用程式，請考慮使用 [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) 這類的協調器。 

在第一次現代化期間，您也可以從雲端新增資產，像是使用 [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) 之類的工具執行監視；CI/CD 管線應用在 [Azure DevOps Services](https://azure.microsoft.com/services/devops/) 的應用程式生命週期；以及 Azure 所提供其他更多的資料資源服務。 比方說，您可以修改原先使用傳統 [ASP.NET Web Forms](https://www.asp.net/web-forms) 或 [ASP.NET MVC](https://www.asp.net/mvc) 開發的整合型 Web 應用程式，而您現在可以使用 Windows 容器進行部署。 當您使用 Windows 容器時，也應該將資料移轉到 [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/)中的資料庫，這完全不需要變更您應用程式的核心架構。

- **雲端原生**：一如介紹所述，若您的目標是與多個獨立開發團隊 (專注在可以自主開發及部署的各種微服務) 合作大型而複雜的應用程式，您可以考慮架構[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)應用程式。 此外還有每項微服務的微調與獨立調整能力。 這些架構方式雖然面臨十分重大的挑戰和複雜度，但可以藉由使用雲端 PaaS 和協調器 (像是 [Azure Kubernetes Service (AKS/ACS)](https://azure.microsoft.com/services/container-service/) (受控 Kubernetes)) 大幅簡化，以及在無伺服器方法中使用 [Azure Functions](https://azure.microsoft.com/services/functions/)。 這所有的方法 (例如微服務及無伺服器) 通常會需要雲端架構及編寫適用於特定 PaaS 平台的程式碼，或是編寫符合特定架構 (例如微服務) 的程式碼。

圖 1-3 顯示了您可在每個成熟度等級使用的內部技術：

![每個現代化成熟度等級的內部技術](./media/image1-3.png)

**圖 1-3。** 每個現代化成熟度等級的內部技術

## <a name="lift-and-shift-scenario"></a>原形移轉案例

對於隨即轉移，請記得您可以在應用程式案例中使用多種不同的隨即轉移變化。 如果您只重新裝載應用程式，可能會產生圖 1-4 中的情形，也就是您只在應用程式及資料庫伺服器使用雲端中的 VM。

![雲端中的單純 IaaS 案例範例](./media/image1-4.png)

**圖 1-4**。 雲端中的單純 IaaS 案例範例

## <a name="modernization-scenarios"></a>現代化案例

在現代化案例中，您可能只會有一個會有一個單純的雲端最佳化應用程式，只使用該成熟度等級的元素。 或者，您可能會一個處於中間狀態的應用程式，其中一部分元素來自原有的雲端基礎結構，另一部分元素來自雲端最佳化 (亦即「挑選」或混合式模型)，如圖 1-5 所示。

![有 IaaS 上的資料庫、DevOps 及容器化資產的範例「挑選」案例](./media/image1-5.png)

**圖 1-5。** 有 IaaS 上的資料庫、DevOps 及容器化資產的範例「挑選」案例

接下來，對於要移轉的許多現有 .NET Framework 應用程式而言，最理想的狀況就是移轉成雲端最佳化應用程式；您只需要花一點工夫，就能換取莫大的好處。 此方法也能讓您準備好隨著未來的演變，融入雲端原生。 範例請見圖 1-6。

![雲端最佳化應用程式案例範例，搭載 Windows 容器與受控服務](./media/image1-6.png)

**圖 1-6。** 雲端最佳化應用程式案例範例，搭載 Windows 容器與受控服務

更進一步來說，您可以針對特定案例新增一些微服務來延伸現有的雲端最佳化應用程式。 這會讓您有部分前進到雲端原生模型，但這不是本指導的重點。

## <a name="what-this-guide-does-not-cover"></a>本指南未涵蓋的內容

本指南涵蓋一部份的特定範例案例，如圖 1-7 所示。 本指南僅著重在原形移轉案例，乃至於雲端最佳化模型。 雲端最佳化模型會使用 Windows 容器加上像是監視和 CI/CD 管線等元件，將 .NET Framework 應用程式現代化。 若要以快速且具彈性的方式將應用程式部署到雲端，每項元件都是不可或缺的要素。

![本指南不包括雲端原生](./media/image1-7.png)

**圖 1-7。** 本指南不包括雲端原生

本指南的重點很明確。 主要在說明如何不重新架構及變更程式碼，就能原形移轉您現有 .NET 應用程式。 最後還說明了如何將您的應用程式移轉成雲端最佳化。

本指南並未說明如何建立雲端原生應用程式，例如如何演變成微服務架構。 若要重新架構您的應用程式，或建立採用微服務的全新應用程式，請參閱電子書 [.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook) (.NET 微服務: 容器化之 .NET 應用程式的架構)。

### <a name="additional-resources"></a>其他資源

- **Containerized Docker application lifecycle with Microsoft platform and tools** (Microsoft 平台與工具上容器化之 Docker 應用程式的生命週期) (可供下載的電子書) \
  <https://aka.ms/dockerlifecycleebook>

- **.NET 微服務：Architecture for containerized .NET applications** (容器化之 .NET 應用程式的架構) (可供下載的電子書) \
  <https://aka.ms/microservicesebook>

- **Architecting modern web applications with ASP.NET Core and Azure** (使用 ASP.NET Core 與 Azure 架構現代化 Web 應用程式) (可供下載的電子書) \
  <https://aka.ms/webappebook>

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

本指南的對象為想要將採用 .NET Framework 之現有 ASP.NET 應用程式或 WCF 服務現代化，以提升交貨及行應用程式之敏捷度的開發人員及解決方案架構設計師。

如果您是技術決策者，例如企業架構設計師，或是只想大略了解使用 Windows 容器及使用 Microsoft Azure 部署到雲端有何優點的開發部門主管，這篇指南也會很實用。

## <a name="how-to-use-this-guide"></a>如何使用本指南

本指南說明了「原因」：吸引您將現有應用程式現代化的誘因，以及將應用程式移往雲端時，使用 Windows 容器所能獲得的具體效益。 本指南前幾個章節中的內容專為想了解概要，但不需要專注在實作及技術性、逐步詳細資料的架構設計師與技術決策者設計而成。

本指南的最後一章導入了多個逐步解說，重點放在特定部署案例上。 本指南提供較短版本的逐步解說，概述了幾種案例及各案例的優點。 完整的逐步解說會向下切入安裝及實作細節，並以一組 [Wiki 文章](https://github.com/dotnet-architecture/eShopModernizing/wiki)的形式發佈到與範本應用程式所在的相同 [GitHub 存放區](https://github.com/dotnet-architecture/eShopModernizing)中 (會在下一節中提到)。 想要專注在實作細節的開發人員與架構師，可能會對最後一章與 GitHub 上的逐步 Wiki 解說較有興趣。

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>將舊版應用程式現代化的範例應用程式：eShopModernizing

GitHub 上的 [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) 存放庫提供兩個模擬舊版整合型 Web 應用程式的範例應用程式。 第一個 Web 應用程式採用 ASP.NET MVC 開發而成；第二個 Web 應用程式採用 ASP.NET Web Forms 開發而成；第三個應用程式採用多層式架構 (N-Tier) 搭配 WinForms 用戶端桌面應用程式，加上使用 WCF 服務後端。 所有應用程式都採用傳統的 .NET Framework。 因為這些範例程式理應是要現代化的現有/舊版 .NET Framework 應用程式，所以不會使用 .NET Core 或 ASP.NET Core。

這些範例應用程式都有現代化版程式碼第二個版本，十分容易。 應用程式版本間最主要的差異在於，第二個版本使用了 Windows 容器作為部署選項。 第二個版本也多了一些附加功能，像是用來管理影像的 Azure 儲存體 Blob、用來管理安全性的 Azure Active Directory，以及用來監視與稽核應用程式的 Azure Application Insights。

## <a name="send-your-feedback"></a>傳送您的意見反應

本指南的目的在協助您了解改進及現代化現有 .NET Web 應用程式時的選項。 本指南與相關範例應用程式將會不斷更新。 歡迎您提供寶貴的意見！ 如果您對如何改進本指南有任何意見，請傳送到 [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)。

>[!div class="step-by-step"]
>[下一步](lift-and-shift-existing-apps-azure-iaas.md) <!-- Next Chapter -->
