---
title: Docker 應用程式的外部迴圈 DevOps 工作流程中的步驟
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/10/2018
ms.openlocfilehash: 37dd5481da571be56f134a5e142b7ba46427d7d8
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/10/2018
ms.locfileid: "53143645"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker 應用程式的外部迴圈 DevOps 工作流程中的步驟

圖 5-1 顯示端對端描述組成 DevOps 外部迴圈工作流程的步驟。

![](./media/image1.png)

圖 5-1:DevOps 與 Microsoft 工具的 Docker 應用程式的外部迴圈工作流程

現在，讓我們檢查每個更新版本的詳細步驟。

## <a name="step-1-inner-loop-development-workflow"></a>步驟 1:內部迴圈開發工作流程

此步驟中會詳細說明第 4 章中，但總而言之，以下是外部迴圈開始的位置，開發人員將推送程式碼至原始檔控制管理系統 （例如 Git) 起始 CI 管線動作的時刻。

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>步驟 2：原始程式碼控制整合和管理 Azure DevOps Services 與 Git

在此步驟中，您需要有版本控制系統來蒐集來自不同的開發人員在小組中的所有程式碼的合併的版本。

即使原始碼控制 (SCC) 和原始碼管理似乎竟循環的大部分開發人員、 DevOps 生命週期中建立 Docker 應用程式時，請務必強調，您必須提交與應用程式的 Docker 映像直接向全球 Docker 登錄中 （例如 Azure Container Registry 或 Docker Hub） 從開發人員的電腦。 相反地，發行並部署到生產環境的 Docker 映像必須全域組建或您的原始程式碼儲存機制 （例如 Git) 為基礎的 CI 管線中建立於要整合的原始程式碼。

在自己的機器內測試時，應該使用本機開發人員本身所產生的映像只是由開發人員。 這是非常重要的 DevOps 管線從 SCC 的程式碼啟動的原因。

Azure DevOps 服務和 Team Foundation Server 支援 Git 和 Team Foundation 版本控制。 您可以選擇它們，或使用端對端的 Microsoft 體驗。 不過，您也可以管理您的程式碼，在外部儲存機制 （例如 GitHub、 內部部署的 Git 存放庫或 Subversion），而且仍然能夠連線到它，並取得您的 DevOps 的 CI 管線做為起點的程式碼。

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>步驟 3:建置、 CI、 整合及測試與 Azure 的 DevOps 服務和 Docker

CI 脫穎而出成為現代軟體測試及傳遞的標準。 Docker 解決方案會維持清楚的區隔開發和作業小組之間的問題。 Docker 映像的不變性可確保可重複的部署之間功能開發、 CI，透過測試和生產環境中執行。 開發人員的膝上型電腦上部署的 docker 引擎，並測試基礎結構可讓容器可攜式跨環境。

到目前為止，以正確的程式碼，提交進行版本控制系統之後，您需要*建置服務*挑選 程式碼，並執行全域組建和測試。

此步驟中 （CI、 建置、 測試） 的內部工作流程是關於 CI 管線，組成 （Git 等），您的程式碼存放庫，您的組建伺服器 （Azure DevOps 服務），Docker 引擎及 Docker 登錄的建構。

您可以使用 Azure DevOps 服務作為基礎來建置您的應用程式和設定您的 CI 管線，並可用來發行建置的 「 成品 」 到 「 成品儲存機制，"會在下一個步驟中說明。

使用 Docker 部署，也就是 「 最終成品 」 時部署會與您的應用程式或服務的 Docker 映像當中內嵌。 這些映像會推送或發行至*Docker 登錄*（私用儲存機制的項目，您可以在 Azure Container Registry，或一個公用 Docker 中樞登錄，常用於官方的基底映像等）。

以下是基本概念：CI 管線將會開始-關閉認可到 Git 等 SCC 儲存機制。 認可會導致 Azure DevOps 服務來執行 Docker 容器內建置工作，並成功完成時的這項工作，將 Docker 映像推送至 Docker 登錄，在圖 5-2 示。

![](./media/image2.png)

圖 5-2:在 CI 中所需的步驟

以下是基本的 CI 工作流程步驟，使用 Docker 和 Azure DevOps 服務：

1.  開發人員將認可推送至 SCC 存放庫 （Git/Azure DevOps Services、 GitHub 等）。

2.  如果您使用 Azure DevOps 服務或 Git、 CI 是內建，這表示它很簡單，只要選取 Azure DevOps 服務中的核取方塊。 如果您使用外部 （例如 GitHub)，SCC *webhook*會通知 Azure DevOps 服務的更新或推送至 Git/GitHub。

3.  Azure 的 DevOps 服務提取 SCC 存放庫，包括描述映像，以及應用程式和測試的程式碼的 DockerFile。

4.  Azure 的 DevOps 服務建置 Docker 映像和標籤組建編號。

5.  Azure 的 DevOps 服務具現化的 Docker 容器內已佈建的 Docker 主機，並執行適當的測試。

6.  如果測試成功，影像先改為有意義的名稱，讓您知道它是 「 blessed 的組建 」 (例如"/ 1.0.0 」 或任何其他標籤)，然後推送至您的 Docker 登錄 （Docker Hub、 Azure Container Registry、 DTR 等等） 的 

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>Azure DevOps 服務實作 CI 管線，使用 Azure DevOps 服務和 Docker 擴充功能

[Azure DevOps 服務 Docker 延伸模組](https://aka.ms/vstsdockerextension)將工作新增至您的 CI 管線，您可以建置 Docker 映像，將 Docker 映像推送到已驗證的 Docker 登錄、 執行 Docker 映像，或執行 Docker 所提供的其他作業CLI。 它也會新增的 Docker Compose 的工作，可用來建置、 推送及執行多容器 Docker 應用程式，或執行其他 Docker Compose CLI 所提供的作業，如所示的 圖 5-3。

![](./media/image3.png)

圖 5-3:Azure DevOps 服務中的 Docker CI 管線

為 Docker 主機或容器或映像登錄，Docker 擴充功能可以使用服務端點。 工作預設都會使用本機的 Docker 主機的話 （這目前需要自訂的 Azure DevOps 服務代理程式）;否則，它們需要您提供的 Docker 主機連線。 取決於使用 Docker 登錄，推送映像，例如正在驗證的動作需要您提供 Docker 登錄連線。

Azure DevOps 服務 Docker 擴充功能會在您的 Azure DevOps 服務帳戶安裝下列元件：

-   連線到 Docker 登錄服務端點

-   服務端點連線至 Docker 容器主機

-   Docker 來執行下列工作：

-   建立映像

-   將映像或存放庫推送至登錄

-   在容器中執行的映像

-   執行 Docker 命令

-   Docker Compose 的工作執行的 Docker Compose 命令

這些 Azure DevOps 服務工作後，建置 Linux Docker 主機/VM 佈建在 Azure 和您慣用的 Docker 登錄 （Azure Container Registry，Docker Hub、 私用 Docker DTR 或任何其他的 Docker 登錄），您可以組合中的 Docker CI 管線非常一致的方式。

***需求：***

-   Azure 的 DevOps 服務，或在內部部署安裝，Team Foundation Server 2015 Update 3 或更新版本。

-   Azure DevOps 服務代理程式具有 Docker 二進位檔。

若要建立其中一種簡單的方法是使用 Docker 來執行 Azure DevOps 服務代理程式的 Docker 映像為基礎的容器。

**進一歩** 讀取詳細資訊組合 Azure DevOps 服務 Docker CI 管線，以及若要檢視的逐步解說，請造訪下列網站：

執行 Azure DevOps 服務代理程式作為 Docker 容器： [ https://hub.docker.com/r/\ microsoft/vsts 代理程式 /](https://hub.docker.com/r/microsoft/vsts-agent/)

Azure 的 DevOps 服務 Docker 擴充功能： <https://aka.ms/vstsdockerextension>

建置使用 Azure DevOps 服務的.NET Core Linux Docker 映像： <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>

建立具有 Docker 支援的 Linux 型 Visual Studio Team Service 組建電腦： <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multicontainer-docker-applications"></a>整合、 測試及驗證多容器 Docker 應用程式

一般而言，大部分的 Docker 應用程式是由多個容器，而不是單一容器組成。 例如，您會有每個微服務的一個容器的微服務導向應用程式。 但是，即使沒有嚴格遵循的微服務方法的模式，是非常有可能您的 Docker 應用程式會組成多個容器或服務。

因此，在建置應用程式中的容器 CI 管線之後, 您還必須部署、 整合及測試與它的所有容器整合 Docker 主機內或甚至是您的容器要測試叢集的整體應用程式散發。

如果您使用單一主機，您可以使用 Docker 命令，例如 docker-compose 來建置和部署相關的容器，以測試和驗證的單一 VM 中的 Docker 環境。 但是，如果您正在使用協調器，如 DC/OS、 Kubernetes 或 Docker Swarm 叢集，您需要部署您的容器，透過不同的機制或協調器時，根據您所選叢集/排程器。

以下是您可以針對 Docker 容器執行的測試的數種：

-   針對 Docker 容器的單元測試

-   測試群組的相互關聯的應用程式或微服務

-   在生產環境和 「 canary 」 版本中測試

重要的一點是當執行整合和功能測試時，您必須執行這些測試容器外。 測試不會定義和執行您要部署，容器內，因為容器以靜態應該完全一樣，您會部署到生產環境的映像為基礎。

測試更進階的案例，例如測試 （測試叢集、 臨時的叢集和生產叢集） 的數個叢集時，非常可行的選項是將映像發佈至登錄，以測試各種不同的叢集中。

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>自訂應用程式的 Docker 映像推送到全球的 Docker 登錄

Docker 映像已測試並驗證之後，您會想要加上標籤，並將其發行至您的 Docker 登錄。 Docker 登錄中 Docker 應用程式生命週期是評選為重要，因為這是您用來儲存您自訂的測試 （也稱為 「 blessed 映像 」），部署至 QA 和生產環境的中央位置。

類似於儲存在您 SCC 的存放庫 （Git 等） 的應用程式程式碼的程式 「 信任來源 」 的方式，Docker 登錄是您 「 信任來源 」 為您的應用程式二進位或位元品管或生產環境部署。

一般而言，您可能想要有您自訂映像的私人存放庫私人存放庫在 Azure Container Registry 或 Docker Trusted Registry，例如內部部署登錄或公用雲端登錄中，以限制的存取權 （例如Docker Hub)，雖然在最後這個情況下如果不是一個開放原始碼，您的程式碼中，您必須信任廠商的安全性。 無論如何，供您執行這項操作的方法是十分類似，最後會根據 docker push 命令中，如上圖中圖 5-4。

![](./media/image4.png)

圖 5-4:發行到 Docker 登錄的自訂映像

有多個供應項目從像是 Azure Container Registry、 Amazon Web Services Container Registry、 Google Container Registry、 爾斯頓碼頭登錄等等的雲端供應商的 Docker 登錄。

使用 Azure DevOps 服務 Docker 延伸模組，您可以將推送一組由 docker-compose.yml 檔案，具有多個標記，已驗證的 Docker 登錄 （例如 Azure Container Registry)，來定義服務映像所示的 圖 5-5。

![](./media/image5.png)

圖 5-5:使用 Azure DevOps 服務來發行至 Docker 登錄的自訂映像

**進一歩** 若要深入了解 Azure DevOps 服務的 Docker 擴充功能，請移至<https://aka.ms/vstsdockerextension>。 若要深入了解 Azure Container Registry，請移至<https://aka.ms/azurecontainerregistry>。

## <a name="step-4-cd-deploy"></a>步驟 4:CD，部署

Docker 映像的不變性可確保可重複使用什麼開發、 CI，透過測試和生產環境中執行的部署。 在您的 Docker 登錄 （私人或公用） 中發佈的應用程式 Docker 映像之後，您就可以將它們部署到您可能會有數個環境 (生產、 品管預備，等等) 從您的 CD 管線，透過使用 Azure DevOps 服務管線工作或 Azure DevOps 服務 Release Management。

不過，此時它會取決於您要部署的 Docker 應用程式種類。 部署簡單的應用程式 （從撰寫和部署觀點來看） 類似整合型應用程式包含幾個容器或服務，並已部署到少數伺服器或 Vm 是非常不同於部署更複雜的應用程式，例如超大規模的功能與微服務導向的應用程式。 下列各節將說明這兩種情況。

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>組成多個 Docker 環境的 Docker 應用程式的部署

首先討論較不複雜的案例： 部署至簡單 Docker 主機 （Vm 或伺服器） 在單一環境或多個環境 (QA，預備和生產環境)。 在此案例中，在內部 CD 管線可以使用 docker-示 圖 5-6，撰寫 （從 Azure DevOps 服務部署工作） 來部署其相關設定的容器或服務，Docker 應用程式。

![](./media/image6.png)

圖 5-6:將應用程式容器部署到簡單的 Docker 主機環境登錄

圖 5-7 中，反白顯示如何連接建置 CI 到透過 Azure DevOps 服務的 QA/測試環境按一下 新增工作 對話方塊中的 Docker Compose。 不過，部署至預備環境或生產環境時，您會通常使用 Release Management 功能處理多個環境 (例如品管預備和生產環境)。 如果您要部署至單一 Docker 主機，它會使用 Azure DevOps 服務 「 Docker Compose 」 工作 (這叫用 docker-docker-compose up 命令，在幕後)。 如果您要部署到 Azure Container Service，它會使用 Docker 部署工作中下, 節中所述。

![](./media/image7.png)

圖 5-7:Azure DevOps 服務管線中新增 Docker Compose 的工作

當您建立 Azure DevOps 服務中的發行時，它會採用一組輸入的成品。 這些設定被為了跨多個環境是不可變的存留期的發行。 當您引入容器時，輸入的成品會識別在登錄中部署的映像。 根據這些識別的方式，他們不保證維持不變的版本中，最明顯的情形下當您從 docker-compose 檔案參考 「 myimage:latest"期間。

Azure DevOps 服務的 Docker 擴充功能可讓您產生包含特定的登錄機映像的組建成品的功能摘要保證可唯一識別相同的二進位映像。 這些是什麼您真的想要做為輸入至版本。

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>使用 Azure DevOps 服務 Release Management 來管理 Docker 環境的版本

透過 Azure DevOps 服務延伸模組，您可以建置新的映像、 將它發行到 Docker 登錄、 執行 Linux 或 Windows 主機上並使用命令，例如 docker-compose 來部署多個容器作為整個應用程式，透過 Azure DevOps如所示的 圖 5-8，服務適用於多個環境的發行管理功能。

![](./media/image8.png)

圖 5-8:設定 Azure DevOps 服務 Docker Compose 的 Azure DevOps 服務 Release Management 的工作

不過，請記住，是相當基本，（它部署簡單的 Docker 主機和 Vm，並會有單一容器或每個影像的執行個體） 的案例中，顯示 圖 5-6，並實作 圖 5-8，並可能應僅適用於開發或測試的 scenarios。 在大部分的企業生產環境案例中，您會想要有高可用性 (HA) 和方便管理可調整性的負載分散於多個節點、 伺服器和 Vm，以及 「 智慧型容錯移轉 」 因此，如果伺服器或節點失敗，其服務和容器將會移至另一部主機伺服器或 VM。 在此情況下，您需要更進階的技術，例如容器叢集、 協調器和排程器。 因此，部署到這些叢集的方式，就是精確地透過進階的案例下一節所述。

### <a name="deploying-complex-docker-applications-to-docker-clusters-dcos-kubernetes-and-docker-swarm"></a>部署複雜的 Docker 應用程式到 Docker 叢集 （DC/OS、 Kubernetes 和 Docker Swarm）

分散式應用程式的本質需要也分散式的運算資源。 若要讓生產環境調整功能，您必須叢集提供高延展性的功能和 HA 根據集區的資源。

您可以將容器部署手動到這些叢集從 CLI 工具，例如 Docker Swarm (例如使用[建立 docker 服務](https://docs.docker.com/engine/swarm/swarm-tutorial/deploy-service/)) 或 web UI 這類[Mesosphere Marathon](https://mesosphere.github.io/marathon/docs/marathon-ui.html) DC/os 叢集，但您應該只針對 punctual 部署測試或管理用途，例如相應放大，或監視的目的，請保留的。

從 CD 的觀點而言和 Azure DevOps 服務明確地說，您可以特別製作的部署工作從執行您的 Azure DevOps 服務 Release Management 環境會部署到容器中的分散式叢集容器化的應用程式服務，如所示的 圖 5-9。

![](./media/image9.png)

圖 5-9:部署容器服務的分散式應用程式

一開始，部署到特定的叢集或協調器時，您將傳統上使用特定的部署指令碼和每個協調器 （亦即，Mesosphere DC/OS 或 Kubernetes 有不同的部署機制比 Docker 與 Docker 的機制Swarm) 而不是更簡單且方便使用 docker compose docker-compose.yml 定義檔案為基礎的工具。 不過，多虧有 Microsoft Azure DevOps 服務 Docker 部署工作，顯示在 圖 5-10，您現在也可以部署至 DC/OS 只使用您熟悉的 docker-compose.yml 檔案，因為 Microsoft 會為您執行該 「 轉譯 」 (從您docker-compose.yml 檔案為其他格式所需的 DC/OS）。

![](./media/image10.png)

圖 5-10:部署 Docker 工作新增到您環境的 RM

圖 5-11 示範如何編輯 Docker 部署工作，並指定目標類型 (Azure Container Service DC/OS，在此情況下)、 您 Docker Compose 檔案，以及 Docker 登錄連線 （例如 Azure Container Registry 或 Docker Hub）。 這是工作擷取要部署 DC/OS 叢集中的容器為您已準備好使用自訂 Docker 映像的地方。

![](./media/image11.png)

圖 5-11:Docker 部署工作定義部署 Azure Container Service DC/OS 以

**進一歩** 若要深入了解 CD 管線中使用 Azure DevOps 服務和 Docker，請瀏覽下列網站：

Docker 和 Azure Container Service 的 azure DevOps 服務延伸模組： [ https://aka.ms/\ vstsdockerextension](https://aka.ms/vstsdockerextension)

Azure Container Service: <https://aka.ms/azurecontainerservice>

Mesosphere DC/OS: <https://mesosphere.com/product/>

## <a name="step-5-run-and-manage"></a>步驟 5:執行和管理

因為執行及管理應用程式在生產環境的企業層級是主要的主旨在本身，並因為作業的類型和工作該層級 （IT 作業），以及此區域的大範圍的人，我們有專門提供整個下一步若要說明的章節。

## <a name="step-6-monitor-and-diagnose"></a>步驟 6:監視和診斷

本主題也涵蓋在下一步] 一章中一部分的 IT 作業會對生產系統; 中執行的工作不過，請務必反白顯示 [在此步驟中取得的深入解析必須摘要回到開發小組，以便持續改善應用程式。 從該觀點來看，也是一部分的 DevOps，雖然工作和作業通常都是透過 IT。

監視和診斷是 DevOps 領域內的 100%時，只是監視程序和針對測試或測試環境的開發小組所執行的分析。 這是執行負載測試，或只是藉由監視 beta 或 QA 環境中，嘗試 beta 版測試人員的新版本。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](../run-manage-monitor-docker-environments/index.md)