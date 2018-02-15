---
title: "Docker 應用程式的外部迴圈 DevOps 工作流程中的步驟"
description: "Microsoft 平台和工具的容器化 Docker 應用程式生命週期"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/22/2017
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: fe51fc4b5026d17f0f9b93e7fd0dedde93ef4a3c
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker 應用程式的外部迴圈 DevOps 工作流程中的步驟

圖 5-1 提供端對端的描述組成 DevOps 外部迴圈的工作流程的步驟。

![](./media/image1.png)

Docker 應用程式與 Microsoft 工具，如圖 5-1: DevOps 外部迴圈工作流程

現在，讓我們來檢查每個步驟更詳細地。

## <a name="step-1-inner-loop-development-workflow"></a>步驟 1： 內部迴圈的開發工作流程

此步驟中會詳細說明第 4 章，但要複習，以下是外部迴圈開始處，開發人員將推送程式碼加入原始檔控制管理系統，（例如 Git) 起始 CI 管線動作的時間。

## <a name="step-2-source-code-control-integration-and-management-with-visual-studio-team-services-and-git"></a>步驟 2： 原始程式碼控制整合性和管理 Visual Studio Team Services 與 Git

在此步驟中，您需要有版本控制系統來蒐集合併來自不同的開發人員在小組中的所有程式碼的版本。

即使原始程式碼控制 (SCC) 和原始碼管理可能看起來是第二個本質循環至大部分的開發人員，DevOps 生活中建立 Docker 應用程式時，務必強調您必須提交與應用程式的 Docker 映像直接到全域 Docker 登錄中 （例如 Azure 容器登錄中或 Docker Hub） 從開發人員的電腦。 相反地，發行和部署到生產環境的 Docker 映像必須全域建置或根據您的原始程式碼儲存機制 （例如 Git) CI 管線中建立單獨針對要整合的原始程式碼。

測試自己的機器中時，應該只由開發人員使用本機開發人員本身所產生的映像。 這是必須要有 DevOps 管線從 SCC 程式碼啟動的原因。

Visual Studio Team Services 和 Team Foundation Server 支援 Git 和 Team Foundation 版本控制。 您可以選擇兩者之間，然後將它用於端對端 Microsoft 體驗。 不過，您也可以管理您的程式碼在外部儲存機制中 （如 GitHub、 內部 Git 儲存機制中或 Subversion） 仍然可以連接到它，並取得程式碼做為起點 DevOps CI 管線。

## <a name="step-3-build-ci-integrate-and-test-with-visual-studio-team-services-and-docker"></a>步驟 3： 組建、 CI，整合和測試 Visual Studio Team Services 和 Docker

CI 已經成為現代化軟體測試及傳遞的標準。 Docker 方案會維持清楚的開發和作業團隊之間的重要性分離。 Docker 映像的不變性可確保可重複的部署之間什麼已開發、 測試透過 CI，並在生產中執行。 Docker 引擎跨 developer 膝上型電腦部署和測試基礎結構使其成為容器可攜式的環境。

此時，以正確的程式碼，提交進行版本控制系統之後，您需要*組建服務*拾取該程式碼，並執行全域的組建和測試。

這個步驟 （CI，建置、 測試） 的內部工作流程是需建構的 CI 管線，您的組建伺服器 (Visual Studio Team Services)，Docker 引擎及 Docker 登錄所組成 （Git 等），您的程式碼儲存機制。

您可以使用 Visual Studio Team Services 做為基礎建置您的應用程式和設定您的 CI 管線，以及發行內建的 「 成品 」 到 「 成品儲存機制，「 的下一個步驟中說明。

部署，也就是 「 最終成品 」 使用 Docker 時部署會與您的應用程式或服務的 Docker 映像內嵌在它們。 這些映像會推入或發行到*Docker 登錄*（您可以在 Azure 容器登錄中或公開的一個像 Docker Hub 登錄，常用於正式的基底映像等私用儲存機制）。

以下是基本概念： 的 CI 管線將會排除-關閉依據認可到 SCC Git 等儲存機制。 圖 5-2 的說明，認可會造成執行 Docker 容器中的建置工作，並在該作業的成功完成時，將 Docker 映像推送至 Docker 登錄，Visual Studio Team Services。

![](./media/image2.png)

圖 5-2： 所需的步驟 CI

以下是使用 Docker 和 Visual Studio Team Services 的基本 CI 工作流程步驟：

1.  開發人員將認可推送到 SCC 儲存機制 （Git/Visual Studio Team Services、 GitHub）。

2.  如果您使用 Visual Studio Team Services 或 Git，CI 為內建的這表示很簡單，只選取 Visual Studio Team Services 中的 核取方塊。 如果您使用外部 （例如 GitHub) SCC *webhook*會通知更新的 Visual Studio Team Services 或推送至 Git/GitHub。

3.  Visual Studio Team Services 中提取 SCC 存放庫，包括 DockerFile 描述映像，以及將應用程式和測試程式碼。

4.  Visual Studio Team Services 建置 Docker 映像，並標示標上組建編號。

5.  Visual Studio Team Services Docker 容器內佈建 Docker 主機時，會具現化，並執行適當的測試。

6.  測試都成功，如果影像第一次嚴格的有意義的名稱，讓您知道它是 blessed 的組建 (例如"/ 1.0.0 」 或任何其他標籤)，然後推送至 Docker 登錄 （Docker Hub、 Azure 容器登錄中、 DTR 等等） 的 和

### <a name="implementing-the-ci-pipeline-with-visual-studio-team-services-and-the-docker-extension-for-visual-studio-team-services"></a>為 Visual Studio Team Services 實作 CI 管線，與 Visual Studio Team Services 和 Docker 擴充功能

[Visual Studio Team Services Docker 擴充功能](https://aka.ms/vstsdockerextension)將工作加入您與您可以建立 Docker 映像、 將 Docker images 推送到已驗證的 Docker 登錄、 執行 Docker 映像，或執行其他作業所提供的 CI 管線Docker CLI。 它也會將 Docker Compose 工作可讓您建置、 推入，並執行 multicontainer Docker 應用程式，或執行 Docker 撰寫 CLI 所提供的其他作業，如圖 5-3 所示。

![](./media/image3.png)

圖 5-3: Docker CI 中的管線 Visual Studio Team Services

Docker 主機和容器或映像 Docker 擴充功能可以使用服務端點。 工作預設都會使用本機的 Docker 主機的話 （這目前需要自訂的 Visual Studio Team Services 代理程式）。否則，它們需要您提供的 Docker 主機連接。 相依於 Docker 登錄，例如推入映像，將驗證的動作需要您提供 Docker 登錄連線。

Visual Studio Team Services Docker 擴充功能會在您的 Visual Studio Team Services 帳戶中安裝下列元件：

-   連接到 Docker 登錄服務端點

-   服務端點連線至 Docker 容器主機

-   Docker 來執行下列工作：

-   建置的映像

-   將映像或儲存機制發送到登錄

-   在容器中執行映像

-   執行 Docker 命令

-   Docker Compose 工作執行 Docker Compose 命令

這些 Visual Studio Team Services 工作後，組建 Linux Docker 主機/佈建 VM 在 Azure 中並您慣用的 Docker 登錄 （Azure 容器登錄中，Docker Hub、 私用 Docker DTR 或任何其他 Docker 登錄），您可以組合您的 Docker CI 管線中非常一致的方式。

***需求：***

-   Visual Studio Team Services，或在內部部署安裝，Team Foundation Server 2015 Update 3 或更新版本。

-   Visual Studio Team Services 代理程式具有 Docker 二進位檔。

若要建立下列其中一種簡單的方法是使用 Docker 執行 Visual Studio Team Services 代理程式的 Docker 映像為基礎的容器。

**進一歩** 讀取組合 Visual Studio Team Services Docker CI 管線，以及若要檢視的逐步解說，請造訪下列網站：

以 Docker 容器中執行 Visual Studio Team Services 代理程式： [https://hub.docker.com/r/ \ microsoft/vsts 代理 /](https://hub.docker.com/r/microsoft/vsts-agent/)

VSTS Docker 擴充功能： <https://aka.ms/vstsdockerextension>

建立具有 Visual Studio Team Services 的.NET Core Linux Docker images: <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

建立 Linux 型 Visual Studio Team 服務使用建立機器 Docker 的支援： <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>整合、 測試及驗證 multicontainer Docker 應用程式

一般而言，大部分的 Docker 應用程式所組成的多個容器，而不是單一的容器。 例如，microservices 導向應用程式會對每個微服務一個容器。 但是，即使沒有嚴格遵守 microservices 方法模式，是很可能您的 Docker 應用程式會組成多個容器或服務。

因此，在建置之後 CI 管線中的應用程式容器，您也需要部署、 整合和測試與它的所有容器中整合的 Docker 主機，或甚至您容器要測試叢集的整體應用程式散發。

如果您使用單一主機，您可以使用 Docker 命令，例如 docker-撰寫建置和部署來測試及驗證單一 VM 的 Docker 環境相關的容器。 但是，如果您使用像是 DC/OS、 Kubernetes，或 Docker Swarm orchestrator 叢集，您要部署您的容器，透過不同的機制或 orchestrator，根據您所選叢集/排程器。

以下是幾種類型的測試，您可以針對 Docker 容器執行：

-   Docker 容器的單元測試

-   相互關聯的應用程式或 microservices 測試群組

-   在生產環境和"canary 」 版本中的測試

重點是當執行整合和功能測試，您必須執行這些測試的容器外。 測試不會定義並因為容器都根據應該與您要部署到實際執行環境的完全相同的靜態影像，您要部署，在容器內執行。

測試更進階的案例，例如測試數個群集 （測試叢集、 臨時的叢集，以及實際執行叢集） 時非常可行的選項是將映像發佈到登錄，以測試不同叢集中。

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>推送到全域 Docker 登錄的自訂應用程式的 Docker 映像

Docker 映像已經測試並驗證之後，您會想要標記，並將它們發行至 Docker 登錄。 Docker 登錄在 Docker 應用程式生命週期中是一項重要，因為它是您在其中儲存您的自訂測試 （也稱為 「 blessed 影像 」） 可以部署到品管及生產環境的中央位置。

類似於儲存在您 SCC 的儲存機制 （Git 等） 的應用程式程式碼的程式 」 事實來源 」 的方式，Docker 登錄是您 「 事實來源 」 二進位應用程式或位元 QA 或生產環境部署。

一般而言，您可能想要具有您自訂映像的私用儲存機制中的私用儲存機制 Azure 容器登錄中或 Docker Trusted Registry 像在內部部署登錄或公用雲端登錄中，以限制的存取權 （例如Docker Hub)，不過在這個最後一個的情況下您的程式碼不是開放原始碼，如果必須信任廠商的安全性。 無論如何，依據您執行這項操作的方法很類似並且為最後根據 docker push 命令，如圖 5-4 所示。

![](./media/image4.png)

圖 5-4： 發行至 Docker 登錄的自訂映像

有多個供應項目，例如 Azure 容器登錄中、 Amazon Web Services 容器登錄中、 Google 容器登錄中、 爾斯頓碼頭登錄和等等的雲端廠商的 Docker 所登錄。

使用 Visual Studio Team Services Docker 延伸模組，您可以推送服務映像 docker compose.yml 檔，具有多個標記，已驗證的 Docker 登錄 （例如 Azure 容器登錄中），所定義的一組圖 5-5 所示。

![](./media/image5.png)

圖 5-5： 使用 Visual Studio Team Services 來發行至 Docker 登錄的自訂映像

**進一歩** 要閱讀更多有關 Visual Studio Team Services 的 Docker 擴充功能，請移至<https://aka.ms/vstsdockerextension>。 若要深入了解 Azure 容器登錄中，移至<https://aka.ms/azurecontainerregistry>。

## <a name="step-4-cd-deploy"></a>步驟 4: CD，部署

Docker 映像的不變性可確保可重複的部署使用什麼已開發、 測試透過 CI，並在生產中執行。 Docker 登錄 （私人或公用） 中發行的應用程式 Docker 映像之後，您就可以將它們部署到您可能需要數個環境 (生產環境中，不必在 QA、 暫存、 等等) 從您的 CD 管線，使用 Visual Studio Team Services管線工作或 Visual Studio Team Services Release Management。

不過，此時它會取決於您要部署哪種 Docker 應用程式。 部署簡單的應用程式 （從撰寫與部署觀點來看） 類似龐大組成少數的容器或服務應用程式及部署幾個伺服器或 Vm 是非常不同部署更複雜的應用程式，例如具有超功能 microservices 導向的應用程式。 下列各節會說明這兩種情況。

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>部署由多個 Docker 環境 Docker 應用程式

讓我們來查看較不複雜的案例： 簡單 Docker 主機 （Vm 或伺服器） 單一的環境或多個環境中部署 (QA、 預備及生產)。 在此案例中，在內部 CD 管線可以使用 docker-如圖 5-6 所述，撰寫 （從 Visual Studio Team Services 部署工作） 來部署容器或服務，其相關設定 Docker 應用程式。

![](./media/image6.png)

圖 5-6： 部署簡單的 Docker 主機環境登錄應用程式容器

圖 5-7 中，反白顯示如何連接建置 CI 到 QA/測試環境，Visual Studio Team Services 透過 Docker Compose 在 新增工作對話方塊，即可。 不過，當部署至預備環境或生產環境，您會通常使用處理多個環境版本管理功能 (例如 QA，預備及生產)。 如果您要部署到單一的 Docker 主機，它使用 Visual Studio Team Services"Docker Compose 」 工作 (這叫用 docker-向上命令實際上撰寫)。 如果您要部署至 Azure 容器服務，它會使用 Docker 部署工作，在下節中所述。

![](./media/image7.png)

圖 5-7： 在 Visual Studio Team Services 管線中加入 Docker Compose 工作

當您在 Visual Studio Team Services 中建立發行時，它會採用一組輸入成品。 這些被要跨多個環境是不可變的存留期中的版本。 當您引入容器時，輸入的成品會識別在登錄中部署的映像。 根據這些識別的方式，他們不保證維持相同的版本中，最明顯的情況，當您從 docker-compose 檔案參考 」 myimage:latest 」 時期間。

Visual Studio Team Services 的 Docker 擴充功能可讓您產生包含特定的登錄機映像的組建成品的功能摘要保證可唯一識別相同的二進位映像。 這些是您真的要使用什麼做為輸入的版本。

### <a name="managing-releases-to-docker-environments-by-using-visual-studio-team-services-release-management"></a>使用 Visual Studio Team Services Release Management 來管理發行至 Docker 環境

透過 Visual Studio Team Services 延伸模組中，您可以建立新的映像、 將它發行到 Docker 登錄、 執行 Linux 或 Windows 主機上和使用例如 docker 命令-撰寫來部署多個容器，為整個應用程式，面對視覺效果Studio Team Services 版本管理功能，供多個環境，如圖 5-8 所示。

![](./media/image8.png)

圖 5-8： 設定 Visual 的 Studio Team Services Docker Compose 的工作，從 Visual Studio Team Services Release Management

不過，請記住，顯示在圖 5-6 中，並實作圖 5-8 案例 （它將它部署到簡單的 Docker 主機和 Vm，而且會有單一容器或每個影像的執行個體），很基本，而且可能應該僅適用於開發或測試 scenarios。 在大部分的企業生產案例中，您會想讓高可用性 (HA) 和輕鬆管理擴充性的方式之間的負載平衡多個節點、 伺服器和 Vm，再加上 「 智慧型容錯移轉 」 因此，如果伺服器或節點失敗，其服務和容器將會移至另一部主機伺服器或 VM。 在此情況下，您需要更進階的技術，例如容器叢集、 orchestrators，以及排程器。 因此，將部署到這些群集的方法是精確地透過下一節中說明的進階案例。

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>部署複雜的 Docker 應用程式至 Docker 叢集 （DC/OS、 Kubernetes，和 Docker Swarm）

分散式應用程式的本質要求也會分散的計算資源。 要有生產調整功能，您必須先叢集功能，可提供高延展性和高可用性集區資源。

您可以部署容器手動這些群集來從 CLI 工具，例如 Docker Swarm (像是使用[docker 服務建立](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) 或 web UI 例如[Mesosphere 馬拉松](https://mesosphere.github.io/marathon/docs/marathon-ui.html)DC/OS 的叢集，但是您應該僅限 punctual 部署測試或基於管理目的而向外擴充或監視的目的，請保留的。

從 CD 觀點來看和 Visual Studio Team Services 具體來說，您可以特別建立的部署工作從執行您將部署在分散式叢集您容器化應用程式的 Visual Studio Team Services Release Management 環境容器服務，如圖 5-9 中所述。

![](./media/image9.png)

圖 5-9： 部署容器服務的分散式應用程式

一開始，當部署至特定的叢集或 orchestrators，您將會傳統上使用特定的部署指令碼和每個每個 orchestrator （也就是 Mesosphere DC/OS 或 Kubernetes 有不同的部署機制比 Docker 和 Docker 的機制廣域） 而非更簡單且容易使用 docker-撰寫 docker compose.yml 定義檔案為基礎的工具。 不過，由於 Microsoft Visual Studio Team Services Docker 部署工作中，顯示在圖 5-10，您現在也可以將部署 DC/OS 只使用熟悉的 docker compose.yml 檔案，因為 Microsoft 為您執行該 「 轉譯 」 (從您docker compose.yml 檔案為其他格式所需的 DC/OS）。

![](./media/image10.png)

圖 5-10： 加入環境 RM Docker 部署工作

圖 5-11 會示範如何編輯 Docker 部署工作，並指定目標類型 （Azure 容器服務 DC/作業系統，在此情況下）、 您 Docker 撰寫的檔案，以及 Docker 登錄連線 （例如 Azure 容器登錄中或 Docker Hub）。 這是工作擷取做為容器 DC/OS 叢集中部署您已備妥要使用自訂 Docker 映像的地方。

![](./media/image11.png)

圖 5-11: Docker 部署工作定義部署 Azure 容器服務 DC/OS 到

**進一歩** 来閱讀更多有關 Visual Studio Team Services 和 Docker CD 管線，請造訪下列網站：

Docker 和 Azure 容器服務的 visual Studio Team Services 擴充功能： [https://aka.ms/ \ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure 容器服務： <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>步驟 5： 執行和管理

因為執行和管理應用程式在企業實際執行層級是主要的主題中的本身，和因為作業的類型和工作該層級 （IT 作業），以及此區域的大範圍的人，我們有專供整個下一步它說明的章節。

## <a name="step-6-monitor-and-diagnose"></a>步驟 6： 監視和診斷

此主題也涵蓋在下一章，IT 部門在生產系統; 所執行之工作的一部分不過，請務必反白顯示，讓應用程式會持續改善，必須回到開發團隊摘要在此步驟中取得的深入資訊。 從該觀點來看，它也是部分 DevOps，雖然工作和作業通常都是透過 IT。

監視和診斷是 DevOps 領域內的 100%時，只會監視的處理程序和開發小組對測試或測試環境中執行的分析。 這是藉由執行負載測試，或只是藉由監視 beta 或 QA 環境中，嘗試測試版測試人員的新版本。

>[!div class="step-by-step"]
[上一個](index.md) [下一步] (.../run-manage-monitor-docker-environments/index.md)
