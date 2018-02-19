---
title: "利用 Azure 雲端及 Windows 容器將現有的 .NET 應用程式現代化"
description: "了解如何將現有的應用程式隨即轉移到 Azure 雲端及容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 5e1a04a0d8ed151337e00c8147756644dfc9075a
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="modernize-existing-net-applications-with-azure-cloud-and-windows-containers-v10"></a>利用 Azure Cloud 及 Windows 容器將現有的 .NET 應用程式現代化 (v1.0)  

![封面影像](./media/cover.png)

發行者  
Microsoft Corporation  
Microsoft Press 及 Microsoft DevDiv 部門  
One Microsoft Way  
Redmond, Washington 98052-6399  

Copyright © 2017 by Microsoft Corporation  

著作權所有，並保留一切權利。 本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製。

本書以電子書的形式免費提供，可從 Microsoft 透過多個管道取得，例如 <http://dot.net/architecture>

若您對本書有相關問題，請傳送電子郵件到 [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)

本書依照「現況」提供，代表作者的觀點和意見。 本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。

此處所描述的一些範例僅供說明，純屬虛構。 任何實際關聯或連結純屬巧合。

Microsoft 與列於 http://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。 所有其他商標皆屬於其各自擁有者的財產。

作者: 
> **Cesar de la Torre**, Sr.，Microsoft Corp. .NET 產品小組 PM

參與者和檢閱者：
> **Scott Hunter**，Microsoft .NET 小組合夥人暨 PM 主管  
> **Paul Yuknewicz**，Microsoft Visual Studio Tools 小組首席 PM 經理  
> **Lisa Guthrie**, Sr.，Microsoft Visual Studio Tools 小組 PM  
> **Ankit Asthana**，Microsoft .NET 小組 PM 總經理  
> **Unai Zorrilla**，Plain Concepts 開發人員主管  
> **Javier Valero**，Grupo Solutio 營運長  

## <a name="introduction"></a>簡介

當您決定將 Web 應用程式現代化，並將其移至雲端時，並不需要完全重新建構您的應用程式。 由於成本與時間限制，使用微服務等進階方法來重新建構應用程式有時並不會納入考量。 視應用程式的類型而定，也可能沒有必要重新建構應用程式。 為了讓組織的雲端移轉策略發揮最高成本效益，考量您的業務需求與應用程式需求便成了重要的一環。 您必須判斷：

-   哪些應用程式需要轉換或重新建構。

-   哪些應用程式只需要進行部分修改。

-   哪些應用程式沒辦法直接「隨即轉移」到雲端。

## <a name="about-this-guide"></a>關於本指南

本主題的重點在於「隨即轉移」案例，以及現有 Microsoft .NET Framework Web 或服務導向應用程式的初步現代化。 隨即轉移這個動作的定義是，將工作負載移至較新或較現代化的環境，而不變換應用程式的程式碼及基本架構。

本指南會描述如何藉由將特定區域現代化，直接將現有的 .NET Framework 伺服器應用程式移至雲端，而不需要重新建構或重新編寫整個應用程式。

本主題也強調了將應用程式移至雲端，以及使用特定一組新技術及方法 (例如 Windows 容器及 Azure 中的協調器) 將應用程式部分現代化的好處。

## <a name="path-to-the-cloud-for-existing-net-applications"></a>現有 .NET 應用程式前往雲端的路徑

組織通常會選擇移至雲端以提升其應用程式的靈活度與速度。 您可以在數分內於雲端設置上千個伺服器 (VM)，相較之下，設置內部部署伺服器通常需要幾個禮拜的時間。

將應用程式移轉到雲端並沒有一體適用的策略。 適合您的移轉策略取決於組織的需求與優先順序，以及所要移轉的應用程式種類。 並非所有應用程式都適合移至平台即服務 ([PaaS](https://azure.microsoft.com/overview/what-is-paas/)) 模型，或是開發[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)應用程式模型。 在許多情況下，您可以根據業務需求，使用分階或累進式方法將資產移至雲端。

對於具有組織最佳長期靈活度及價值的現代應用程式而言，投資「雲端最佳化」及「雲端原生」應用程式架構可能會使您獲益。 不過，對於現有的應用程式及舊資產而言，重點在於花費最少的時間與金錢將其移至雲端 (不進行重新建構或變更程式碼)，以實現最大收益。

圖 1-1 呈現了您採取累進方式將現有的 .NET 應用程式移至雲端時，可以採用的路徑。

 ![現有 .NET 應用程式及服務的現代化路徑](./media/image1-1.png)

> **圖 1-1**。 現有 .NET 應用程式及服務的現代化路徑

每個移轉方法都有其優點及使用理由。 在將應用程式移至雲端時，您可以選擇單一方法，也可以從多種方法中擷取某些元件。 個別應用程式並不侷限於單一方法或成熟度。 比方說，一般混合方法會有某些內部部署元件，再加上雲端中的其他元件。

在前兩個移轉等級中，您只需要隨即轉移應用程式即可：

**等級 1：雲端基礎結構就緒**：在此移轉方法中，您只需要將目前的內部部署應用程式重新裝載或移動到基礎結構即服務 ([IaaS](https://azure.microsoft.com/overview/what-is-iaas/)) 平台即可。 您的應用程式結構和以前幾乎相同，但您現已將其部署到雲端中的 VM。

**等級 2：雲端 DevOps 就緒**：在此等級中，在起始隨即轉移後仍不需要重新建構或變換程式碼，您在雲端中執行應用程式可享有更多好處。 您可藉由精簡企業開發營運 (DevOps) 程序來增加應用程式的靈活度，加快出貨速度。 您可以使用以 Docker 引擎為基礎的 Windows 容器等技術，來達到這個目的。 容器免除了在多個階段部署時，因應用程式相依性而引起的衝突。 容器也會使用其他與資料相關的雲端受管理服務、監視以及持續整合/持續部署 (CI/CD) 管線。

第三等級的成熟度是雲端的終極目標，但對大多數應用程式而言並非必要，且非本指南的主要重點：

**等級 3：雲端最佳化**：這個移轉方法通常由業務需求驅動，並將目標放在將您的任務關鍵性應用程式現代化上。 在此等級中，您可使用 PaaS 服務將您的應用程式移至 PaaS 運算平台上。 您可以實作[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)應用程式及微服務架構，來發展具長期靈活度的應用程式，以及擴展新界限。 這種類型的現代化通常需要專為雲端設計的架構。 尤其在移至雲端原生應用程式及微服務式模型的時候，通常會需要撰寫新的程式碼。 這項方法可協助您取得在整合型及內部部署應用程式環境中難以達到的優點。

表 1-1 描述了選擇各項移轉或現代化方法的主要優點及理由。

> | **雲端基礎結構就緒** <br /> *隨即轉移* | **雲端 DevOps 就緒** <br /> *隨即轉移* | **雲端最佳化** 現代化/重構/重寫 |
> |---|---|---|
> | **應用程式的計算目標** |
> | 在 Azure 中部署到 VM 的應用程式 | 部署至 VM、Azure Service Fabric 或 Azure Container Service (即 Kubernetes) 的容器化整合型或多層式架構 (N-Tier) 應用程式 | 以 Azure App Service、Azure Service Fabric、Azure Container Service (即 Kubernetes) 之 PaaS 為基礎的容器化微服務或一般應用程式 |
> | **資料目標** |
> | SQL 或 VM 上的任何關聯式資料庫 | Azure SQL Database 受控執行個體 | Azure SQL Database、Azure Cosmos DB 或其他 NoSQL |
> | **優點**|
> | <li>不必重新建構及撰寫新程式碼 <li> 以最少心力快速移轉 <li> Azure 中支援的最普及選項 <li> 保證基本可用性 <li> 移至雲端後更容易現代化 | <li>不必重新建構及撰寫新程式碼 <li> 容器會在 VM 上提供小幅累積的貢獻 <li> 因容器而獲得改善的部署及 DevOps 發行靈活度 <li> 增加密度並降低部署成本 <li> 應用程式及相依性的可攜性 <li> 透過 Azure Container Service (或稱 Kubernetes) 及 Azure Service Fabric 提供高可用性及協調流程 <li> Service Fabric 中的節點/VM 修補 <li> 裝載目標的彈性：Azure VM 或 VM 擴展集、Azure Container Service (或稱 Kubernetes)、Service Fabric 以及未來的容器選擇 | <li>具有所需的雲端架構、重構及新程式碼 <li> 微服務雲端原生方法 <li> 新的 Web 應用程式、整合型、多層式架構 (N-Tier) 及雲端最佳化 <li> 完整受控的服務 <li> 自動修補 <li> 經最佳化以調整規模 <li> 為子系統的自主靈活度最佳化 <li> 建基於部署及 DevOps <li> 增強的 DevOps，例如位置及部署策略 <li> PaaS 及協調器目標：Azure App Service、Azure Container Service (或稱 Kubernetes)、Azure Service Fabric 以及未來的容器式 PaaS |
> | **挑戰** |
> | <li> 除了轉入營業費用或關閉資料中心之外，雲端價值較低 <li> 管理程度極低：沒有 OS 或中介軟體修補；也沒有 Terraform、Spinnaker 或 Puppet 等強大的基礎結構解決方案 | <li> 在需要固定的學習曲線中，容器化是額外的步驟 | <li> 可能需要大規模重構或重寫程式碼 (增加時間及開支) |
>> **表 1-1。** 現有 .NET 應用程式及服務現代化路徑的優點與挑戰

### <a name="key-technologies-and-architectures-by-maturity-level"></a>依成熟度等級分階的主要技術及架構

.NET Framework 應用程式最初從 2001 年年底推出的 .NET Framework 1.0 版開始。 之後，公司移往了更新的版本 (例如 2.0、3.5 及 .NET 4.x)。 這些應用程式大多在 Windows Server 及 Internet Information Server (IIS) 上執行，且使用關聯式資料庫，像是 SQL Server、Oracle、MySQL 或任何其他 RDBMS。

如今，大多數現有的 .NET 應用程式可能以 .NET Framework 4.x 甚至是 .NET Framework 3.5 為基礎，且使用 ASP.NET MVC、ASP.NET Web Forms、ASP.NET Web API、Windows Communication Foundation (WCF)、ASP.NET SignalR 及 ASP.NET Web Pages 等 Web 架構。 這些已建立的 .NET Framework 技術相依於 Windows。 若您只是想移轉舊版應用程式，而且希望將對應用程式基礎結構產生的變更降至最低，該相依性是重要的考慮因素。

圖 1-2 顯示了在三個雲端成熟度等級中，各自使用的主要技術及架構樣式：

![各個成熟度等級將現有 .NET Web 應用程式現代化時使用的主要技術](./media/image1-2.png)

> **圖 1-2。** 將現有 .NET Web 應用程式現代化時，各個成熟度等級使用的主要技術

圖 1-2 強調了大多數常見案例，然而在架構方面有可能會出現許多混合變化。 比方說，成熟度模型不僅適用現有 Web 應用程式中的整合型架構，也適用於服務導向、多層式架構 (N-Tier) 及其他架構樣式變化。

現代化程序中的每個成熟度等級都與下列主要技術和方法相關：

-   **雲端基礎結構就緒** (重新裝載或基本隨即轉移)：就第一步來說，許多組織只想要快速執行雲端移轉策略。 在此情況中，應用程式單純只會重新裝載。 大多數重新裝載作業都能透過使用 [Azure Migrate](https://aka.ms/azuremigrate) 自動執行，此服務會提供必要的指導、深入解析及機制，協助您透過 [Azure Site Recovery](https://azure.microsoft.com/services/site-recovery/) 及 [Azure 資料庫移轉服務](https://azure.microsoft.com/campaigns/database-migration/)等雲端工具移轉到雲端。 您也可以手動設定重新裝載，使您能在將舊版應用程式移至雲端時，了解有關您資產的基礎結構詳細資料。 比方說，您可以將應用程式移至 Azure 中的 VM 而幾乎不需要修改，可能只要進行小幅度設定變更即可。 在此情況中的網路功能與內部部署環境相似，特別是當您在 Azure 中建立虛擬網路的時候。

-   **雲端 DevOps 就緒** (改善的隨即轉移)：此模型的重點在於如何以少數的重要部署最佳化取得最大的雲端效益，而不需要變更應用程式的核心架構。 基本步驟是將 [Windows 容器](https://docs.microsoft.com/virtualization/windowscontainers/about/)支援新增至您現有的 .NET Framework 應用程式。 這項重要的步驟 (容器化) 並不會影響程式碼，因此投入隨即轉移中的整體資源相當少。 您可以使用 [Image2Docker](https://github.com/docker/communitytools-image2docker-win)、Visual Studio 以及 Visual Studio Tools for [Docker](https://www.docker.com/)。 Visual Studio 會自動選擇 ASP.NET 應用程式及 Windows 容器映像的智慧型預設。 這些工具提供了迅速的內部迴圈，以及容器到 Azure 的快速路徑， 並改善您部署到多個環境時的靈活度。 在生產方面，您可以將 Windows 容器部署到 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) 或 [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes、DC/OS 或 Swarm) 等協調器。 在初步現代化期間，您也可以從雲端新增資產，例如 [Azure Application Insights](https://docs.microsoft.com/azure/application-insights/app-insights-overview) 等工具進行監視；使用 [Visual Studio Team Services](https://www.visualstudio.com/team-services/) 建立的應用程式生命週期 CI/CD 管線；以及更多可在 Azure 中取得的資料資源服務。 比方說，您可以修改原先使用傳統 [ASP.NET Web Forms](https://www.asp.net/web-forms) 或 [ASP.NET MVC](https://www.asp.net/mvc) 開發的整合型 Web 應用程式，而您現在可以使用 Windows 容器進行部署。 當您使用 Windows 容器時，也應該將資料移轉到 [Azure SQL Database 受控執行個體](https://docs.microsoft.com/azure/sql-database/)中的資料庫，這完全不需要變更您應用程式的核心架構。

-   **雲端最佳化**：如上所述，在雲端中將應用程式現代化的最終目標，在於將您的系統建基於 [Azure App Service](https://azure.microsoft.com/services/app-service/) 等 PaaS 平台。 PaaS 平台著重於現代 Web 應用程式，並以[無伺服器運算](https://azure.microsoft.com/overview/serverless-computing/)的新服務與 [Azure Functions](https://azure.microsoft.com/services/functions/) 等平台來延伸您的應用程式。 在此成熟度模型中更加重要的進階案例是微服務架構及[雲端原生](https://www.gartner.com/doc/3181919/architect-design-cloudnative-applications)應用程式，其通常會使用 [Azure Service Fabric](https://azure.microsoft.com/services/service-fabric/) 或 [Azure Container Service](https://azure.microsoft.com/services/container-service/) (Kubernetes、DC/OS 或 Swarm) 等協調器。 這些協調器專為微服務及多容器應用程式設計而成。 這所有的方法 (例如微服務及 PaaS) 通常都會要求您撰寫適用特定 PaaS 平台的程式碼，或是符合特定架構 (例如微服務) 的程式碼。

圖 1-3 顯示了您可在每個成熟度等級使用的內部技術：

![每個現代化成熟度等級的內部技術](./media/image1-3.png)

> **圖 1-3。** 每個現代化成熟度等級的內部技術

## <a name="lift-and-shift-scenarios"></a>隨即轉移案例

對於隨即轉移，請記得您可以在應用程式案例中使用多種不同的隨即轉移變化。 如果您只重新裝載應用程式，可能會產生圖 1-4 中的情形，也就是您只在應用程式及資料庫伺服器使用雲端中的 VM。

![雲端中的單純 IaaS 案例範例](./media/image1-4.png)

> **圖 1-4**。 雲端中的單純 IaaS 案例範例

接下來，您可能會有單純的雲端 DevOps 就緒應用程式，其中只使用來自該成熟度等級的元素。 或者，您可能會有處於中繼狀態的應用程式，其中有一些元素來自雲端基礎結構就緒，另一些元素則來自雲端 DevOps 就緒 (即為「挑選」或混合模型)，如圖 1-5 所示。

![有 IaaS 上的資料庫、DevOps 及容器化資產的範例「挑選」案例](./media/image1-5.png)

> **圖 1-5。** 有 IaaS 上的資料庫、DevOps 及容器化資產的範例「挑選」案例

接下來，如果有許多現有 .NET Framework 應用程式要移轉，理想案例是移轉至雲端 DevOps 就緒應用程式，以些許功夫換取莫大利益。 此方法也會為您安排雲端最佳化，以備日後之需。 範例請見圖 1-6。

![有 Windows 容器及受控服務的範例雲端 DevOps 就緒應用程式案例](./media/image1-6.png)

> **圖 1-6。** 有 Windows 容器及受控服務的範例雲端 DevOps 就緒應用程式案例

更進一步來說，您可以為特定案例新增幾個微服務，藉此延伸現有的雲端 DevOps 就緒應用程式。 這會讓您有一部份移至雲端最佳化模型中的雲端原生等級，但這並不是本指導的重點。


## <a name="what-this-guide-does-not-cover"></a>本指南未涵蓋的內容

本指南涵蓋一部份的特定範例案例，如圖 1-7 所示。 本指南僅著重在隨即轉移案例上，乃至於雲端 DevOps 就緒模型。 在雲端 DevOps 就緒模型中，會使用 Windows 容器再加上監視及 CI/CD 管線等元件，將 .NET Framework 應用程式現代化。 若要以快速且具彈性的方式將應用程式部署到雲端，每項元件都是不可或缺的要素。

![雲端 DevOps 就緒應用程式的隨即轉移與基本現代化](./media/image1-7.png)

> **圖 1-7。** 雲端 DevOps 就緒應用程式的隨即轉移與基本現代化

本指南的重點很明確。 我們向您展示了可採取的途徑，讓您可達到現有 .NET 應用程式的隨即轉移，而不需要重新建構或是變更程式碼。 最後，我們向您示範了讓應用程式雲端 DevOps 就緒的方法。

本主題未說明如何運用雲端原生應用程式，例如發展到微服務架構的方法。 若要重新建構您的應用程式，或是以微服務為基礎建立全新的應用程式，請參閱電子書 [.NET Microservices: Architecture for containerized .NET applications](https://aka.ms/microservicesebook) (.NET 微服務：容器化 .NET 應用程式的架構)。

### <a name="additional-resources"></a>其他資源

-   **Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (利用 Microsoft 平台和工具的容器化 Docker 應用程式生命週期) (可下載的電子書)：[*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)

-   **.NET Microservices: Architecture for containerized .NET applications** (.NET 微服務：容器化 .NET 應用程式的架構) (可下載的電子書)：[*https://aka.ms/microservicesebook*](https://aka.ms/microservicesebook)

-   **Architecting modern web applications with ASP.NET Core and Azure** (利用 ASP.NET Core 及 Azure 建構現代 Web 應用程式) (可下載的電子書)：[*https://aka.ms/webappebook*](https://aka.ms/webappebook)

## <a name="who-should-use-this-guide"></a>誰應該使用本指南

開發人員及解決方案架構設計師若想將以 .NET Framework 為基礎的現有 ASP.NET 應用程式現代化，即適合閱讀本篇指南，以改善應用程式出貨與發行的靈活度。

如果您是技術決策者，例如企業架構設計師，或是只想大略了解使用 Windows 容器及使用 Microsoft Azure 部署到雲端有何優點的開發部門主管，這篇指南也會很實用。

## <a name="how-to-use-this-guide"></a>如何使用本指南

本指南說明了「原因」：吸引您將現有應用程式現代化的誘因，以及將應用程式移往雲端時，使用 Windows 容器所能獲得的具體效益。 本指南前幾個章節中的內容專為想了解概要，但不需要專注在實作及技術性、逐步詳細資料的架構設計師與技術決策者設計而成。

本指南的最後一章導入了多個逐步解說，重點放在特定部署案例上。 在本指南中，我們提供了較短版本的逐步解說，以概述案例並強調各案例的優點。 完整的逐步解說會向下切入安裝及實作細節，並以一組 [Wiki 文章](https://github.com/dotnet-architecture/eShopModernizing/wiki)的形式發佈到與範本應用程式所在的相同 [GitHub 存放區](https://github.com/dotnet-architecture/eShopModernizing)中 (會在下一節中提到)。 想要專注在實作細節的開發人員與架構師，可能會對最後一章與 GitHub 上的逐步 Wiki 解說較有興趣。

## <a name="sample-apps-for-modernizing-legacy-apps-eshopmodernizing"></a>將舊版應用程式現代化的範例應用程式：eShopModernizing

GitHub 上的 [eShopModernizing](https://github.com/dotnet-architecture/eShopModernizing) 存放庫提供兩個模擬舊版整合型 Web 應用程式的範例應用程式。 其中一個 Web 應用程式使用了 ASP.NET MVC 進行開發，而第二個應用程式則使用 ASP.NET Web Form 進行開發。 這兩個 Web 應用程式皆以傳統 .NET Framework 為基礎。 因為這些範例程式理應是要現代化的現有/舊版 .NET Framework 應用程式，所以不會使用 .NET Core 或 ASP.NET Core。

這兩個範例應用程式都有程式碼經過現代化的第二版本，其過程相當直接。 應用程式版本間最主要的差異在於，第二個版本使用了 Windows 容器作為部署選項。 第二個版本也多了一些附加功能，像是用來管理影像的 Azure 儲存體 Blob、用來管理安全性的 Azure Active Directory，以及用來監視與稽核應用程式的 Azure Application Insights。

## <a name="send-us-your-feedback"></a>將您的意見反應傳送給我們！

我們撰寫此指南的目的，在於協助您了解改善及現代化現有 .NET Web 應用程式時所擁有的選擇。 本指南與相關範例應用程式將會不斷更新。 Microsoft 十分歡迎您提出意見反應！ 如果您對如何改進本指南有任何意見，請傳送到 [dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com?subject=Feedback%20for%20.NET%20Container%20&%20Microservices%20Architecture%20book)。

>[!div class="step-by-step"]
[下一步](lift-and-shift-existing-apps-azure-iaas.md)
