---
title: Docker 應用程式之外部迴圈 DevOps 工作流程中的步驟
description: 了解 DevOps 工作流程的「外部迴圈」步驟
ms.date: 02/15/2019
ms.openlocfilehash: e7a82d2e5a5d503e5efbe9ac8242b163baab1286
ms.sourcegitcommit: f20dd18dbcf2275513281f5d9ad7ece6a62644b4
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/30/2019
ms.locfileid: "68673705"
---
# <a name="steps-in-the-outer-loop-devops-workflow-for-a-docker-application"></a>Docker 應用程式之外部迴圈 DevOps 工作流程中的步驟

圖 5-1 顯示 DevOps 外部迴圈工作流程中所包含步驟的端對端描述。

![此圖顯示 DevOps 的「外部迴圈」。 將程式碼推送到存放庫之後會啟動 CI 管線，然後開始 CD 管線以將應用程式部署在其中。 從已部署應用程式收集的計量會回饋給開發工作負載，其中會出現「內部迴圈」，讓開發小組有實際資料可回應使用者和商務需求。](./media/image1.png)

**圖 5-1**. 使用 Microsoft 工具的 Docker 應用程式 DevOps 外部迴圈工作流程

現在，讓我們更詳細地探討每個步驟。

## <a name="step-1-inner-loop-development-workflow"></a>步驟 1：內部迴圈開發工作流程

此步驟會在第 4 章中詳細說明，但概括而言，這是外部迴圈開始的位置，此時開發人員會將程式碼推送到原始檔控制管理系統 (例如 Git) 以起始 CI 管線動作。

## <a name="step-2-source-code-control-integration-and-management-with-azure-devops-services-and-git"></a>步驟 2：使用 Azure DevOps Services 和 Git 的原始檔控制整合與管理

在此步驟中，您需要有版本控制系統，才能收集來自小組中不同開發人員的所有程式碼合併版本。

即使大多數開發人員對於原始程式碼控制 (SCC) 和原始程式碼管理似乎很熟悉，但在 DevOps 生命週期中建立 Docker 應用程式時，請務必強調您不得從開發人員電腦將具有應用程式的 Docker 映像直接提交給全域 Docker 登錄 (例如 Azure Container Registry 或 Docker Hub)。 相反地，若要將 Docker 映像發行並部署到生產環境，則只能在根據原始程式碼存放庫 (例如 Git) 整合到全域組建或 CI 管線的原始程式碼上建立這些映像。

開發人員所產生的本機映像，只能供他們用來在自己的電腦內進行測試。 這就是為什麼必須從 SCC 程式碼啟用 DevOps 管線。

Azure DevOps Services 和 Team Foundation Server 支援 Git 和 Team Foundation 版本控制。 您可以在兩者之間進行選擇，並用於端對端 Microsoft 體驗。 不過，您也可以在外部存放庫 (例如 GitHub、內部部署 Git 存放庫或 Subversion) 中管理您的程式碼，且仍然能夠與其連線，並取得程式碼作為 DevOps CI 管線的起點。

## <a name="step-3-build-ci-integrate-and-test-with-azure-devops-services-and-docker"></a>步驟 3：使用 Azure DevOps Services 和 Docker 的組建、CI、整合與測試

CI 已脫穎而出成為現代軟體測試和傳遞的標準。 Docker 解決方案會在開發小組與作業小組之間維持清楚的關注點分離。 Docker 映像的不變性確保在已開發、已透過 CI 測試並在生產環境中執行的項目之間可重複部署。 跨開發人員膝上型電腦與測試基礎結構部署的 Docker 引擎，可讓容器移植到不同的環境。

此時，在您讓版本控制系統提交正確的程式碼之後，您需要「組建服務」  才能選擇程式碼並執行全域建置和測試。

此步驟的內部工作流程 (CI、建置、測試) 與 CI 管線的建構相關，其中包含您的程式碼存放庫 (Git 等)、您的組建伺服器 (Azure DevOps Services)、Docker 引擎和 Docker 登錄。

您可以使用 Azure DevOps Services 作為基礎，來建置您的應用程式並設定 CI 管線，以及將組建「成品」發佈到「成品存放庫」，其將在下一個步驟中進行說明。

使用 Docker 進行部署時，所要部署的「最終成品」是 Docker 映像，其中內嵌您的應用程式或服務。 這些映像會推送或發佈到「Docker 登錄」  (例如您可以在 Azure Container Registry 中擁有的私人存放庫，或 Docker Hub Registry 之類的公用存放庫，後者通常會用於官方基底映像)。

以下是基本概念：CI 管線會藉由認可到 Git 等 SCC 存放庫來開始。 認可會使 Azure DevOps Services 在 Docker 容器中執行組建作業，並在該作業成功完成時，將 Docker 映像推送到 Docker 登錄，如圖 5-2 示。

![外部迴圈的第一個部分牽涉到步驟 1 到 3，從程式碼、執行、偵錯和驗證，到程式碼存放庫，再到組建和測試 CI 步驟](./media/image2.png)

**圖 5-2**。 CI 中的相關步驟

以下是使用 Docker 和 Azure DevOps Services 的基本 CI 工作流程步驟：

1. 開發人員將認可推送到 SCC 存放庫 (Git/Azure DevOps Services、GitHub 等)。

2. 如果您使用 Azure DevOps Services 或 Git，則會內建 CI，這表示會與在 Azure DevOps Services 中選取核取方塊一樣簡單。 如果您使用外部 SCC (例如 GitHub)，則 `webhook` 會通知 Azure DevOps Services 更新或推送到 Git/GitHub。

3. Azure DevOps Services 提取 SCC 存放庫，包括描述映像的 Dockerfile，以及應用程式和測試程式碼。

4. Azure DevOps Services 建置 Docker 映像並使用組建編號來標記它。

5. Azure DevOps Services 具現化已佈建 Docker 主機中的 Docker 容器，並執行適當的測試。

6. 如果測試成功，映像會先重新標記為有意義的名稱，讓您知道這是「經過驗證的組建」(例如 "/1.0.0" 或任何其他標籤)，然後向上推送到您的 Docker 登錄 (Docker Hub、Azure Container Registry、DTR 等)

### <a name="implementing-the-ci-pipeline-with-azure-devops-services-and-the-docker-extension-for-azure-devops-services"></a>使用 Azure DevOps Services 和 Azure DevOps Services 的 Docker 延伸模組來實作 CI 管線

Visual Studio Azure DevOps Services 包含組建與發行範本，您可以在 CI/CD 管線中用來建置 Docker 映像，將 Docker 映像推送到已驗證的 Docker 登錄、執行 Docker 映像，或執行 Docker CLI 所提供的其他作業。 它也會新增 Docker Compose 工作，讓您用來建置、推送及執行多容器 Docker 應用程式，或執行 Docker Compose CLI 所提供的其他作業，如圖 5-3 所示。

![Azure DevOps 中 Docker CI 管線的瀏覽器檢視](./media/image3.png)

**圖 5-3**。 Azure DevOps Services 中的 Docker CI 管線，包括組建與發行範本以及相關聯的工作。

您可以使用這些範本和工作，來建構要在 Azure Service Fabric、Azure Kubernetes Service 和類似供應項目中建置/測試及部署的 CI/CD 成品。

有了這些 Visual Studio Team Services 工作、Linux-Docker 主機/VM 佈建在 Azure 中的組建，以及您慣用的 Docker 登錄 (Azure Container Registry、Docker Hub、私人 Docker DTR 或任何其他 Docker 登錄)，您就能夠以非常一致的方式來組合 Docker CI 管線。

***需求：***

- Azure DevOps Services，或是 Team Foundation Server 2015 Update 3 或更新版本 (適用於內部部署安裝)。

- 具有 Docker 二進位檔的 Azure DevOps Services 代理程式。

  建立其中一個代理程式的一個簡單方法就是使用 Docker 來執行以 Azure DevOps Services 代理程式 Docker 映像為基礎的容器。

> [!INFORMATION] 若要深入了解如何組合Azure DevOps Services Docker CI 管線並檢視逐步解說，請瀏覽下列網站：
>
> - 以 Docker 容器執行 Visual Studio Team Services (現在為 Azure DevOps Services) 代理程式：\
>   <https://hub.docker.com/_/microsoft-azure-pipelines-vsts-agent>
>
> - 使用 Azure DevOps Services 建置 .NET Core Linux Docker 映像：\
>   <https://blogs.msdn.microsoft.com/stevelasker/2016/06/13/building-net-core-linux-docker-images-with-visual-studio-team-services/>
>
> - 透過 Docker 支援建置 Linux 型 Visual Studio Team Service 組建電腦：\
>   <http://donovanbrown.com/post/2016/06/03/Building-a-Linux-Based-Visual-Studio-Team-Service-Build-Machine-with-Docker-Support>

### <a name="integrate-test-and-validate-multi-container-docker-applications"></a>整合、測試及驗證多容器 Docker 應用程式

一般而言，大多數 Docker 應用程式是由多個容器而不是單一容器所組成。 一個良好的範例是微服務導向應用程式，其中每個微服務會有一個容器。 但即使沒有嚴格遵循微服務方法模式，您的 Docker 應用程式還是有可能由多個容器或服務所組成。

因此，在 CI 管線中建置應用程式容器之後，您還必須部署、整合及測試整體應用程式，以及其在整合 Docker 主機內或甚至在容器散發目標測試叢集中的所有容器。

如果您使用單一主機，您可以使用 Docker 命令 (例如 docker-compose) 來建置及部署相關容器，以測試及驗證單一 VM 中的 Docker 環境。 但如果您使用協調器叢集 (例如 DC/OS、Kubernetes 或 Docker Swarm)，則需要根據您所選取的叢集/排程器，透過不同機制或協調器來部署您的容器。

下列是您可以對 Docker 容器執行的幾種測試類型：

- Docker 容器的單元測試

- 相互關聯應用程式或微服務的測試群組

- 生產環境和 "Canary" 發行中的測試

重點是當執行整合與功能測試時，您必須從容器外部執行這些測試。 測試不會包含在您要部署的容器中或在其中執行，因為容器是以靜態映像為基礎，應該與您要部署到生產環境的映像完全相同。

測試更進階的案例時，例如包括數個叢集 (測試叢集、預備叢集和生產叢集)，一個實用的選項是將映像發佈到登錄，以便可在各種叢集中測試。

### <a name="push-the-custom-application-docker-image-into-your-global-docker-registry"></a>將自訂應用程式 Docker 映像推送到全域 Docker 登錄

測試和驗證 Docker 映像之後，您會想要標記映像並將其發佈到您的 Docker 登錄。 Docker 登錄是 Docker 應用程式生命週期中很重要的一部分，因為這是您儲存自訂測試 (也稱為「經過驗證的映像」) 以部署到 QA 和生產環境的中央位置。

與應用程式程式碼儲存在 SCC 存放庫 (Git 等) 的方式相似之處在於您的「信任來源」，Docker 登錄是您將二進位應用程式或位元部署到 QA 或生產環境的「信任來源」。

一般而言，您可能想要有存放自訂映像的私人存放庫，可以存放在 Azure Container Registry 或內部部署登錄 (例如 Docker Trusted Registry) 的私人存放庫中，也可以存放在限制存取的公用雲端登錄中 (例如 Docker Hub)；但在後者的情況下，如果您的程式碼不是開放原始碼，您必須信任廠商的安全性。 無論如何，所使用的方法都很類似且會採用 `docker push` 命令，如圖 5-4 所示。

![在步驟 3 中，針對建置整合與測試 (CI)，您可能會將產生的 docker 映像發佈到私人或公用登錄。](./media/image4.png)

**圖 5-4**。 將自訂映像發佈到 Docker 登錄

Azure Container Registry、Amazon Web Services Container Registry、Google Container Registry、Quay Registry 等雲端廠商提供多種 Docker 登錄服務。

使用 Docker 工作，您可以將 `docker-compose.yml` 檔案所定義並具有多個標記的一組服務映像，推送到已驗證的 Docker 登錄 (例如 Azure Container Registry)，如圖 5-5 所示。

![將映像從 Azure DevOps 發佈到登錄之步驟的瀏覽器檢視。](./media/image5.png)

**圖 5-5**。 使用 Azure DevOps Services 將自訂映像發佈到 Docker 登錄

> [!INFORMATION] 如需 Azure Container Registry 的詳細資訊，請參閱 <https://aka.ms/azurecontainerregistry>。

## <a name="step-4-cd-deploy"></a>步驟 4：CD、部署

Docker 映像的不變性確保可重複部署已開發、已透過 CI 測試並在生產環境中執行的項目。 當您在 Docker 登錄 (私人或公用) 中發佈應用程式 Docker 映像之後，您可以使用 Azure DevOps Services 管線工作或 Azure DevOps Services Release Management，從您的 CD 管線將這些映像部署到您可能擁有的數個環境 (生產環境、QA、預備環境等)。

不過，此時取決於您要部署的 Docker 應用程式類型。 部署簡單的應用程式 (從撰寫和部署觀點來看)，例如由一些容器或服務所組成並部署到一些伺服器或 VM 的整合型應用程式，會不同於部署較複雜的應用程式，例如具有超大規模功能的微服務導向應用程式。 下列各節將說明這兩個案例。

### <a name="deploying-composed-docker-applications-to-multiple-docker-environments"></a>將組合的 Docker 應用程式部署到多個 Docker 環境

首先討論較不複雜的案例：部署到單一環境或多個環境 (QA、預備環境和生產環境) 中的簡單 Docker 主機 (VM 或伺服器)。 在此案例中，CD 管線可以在內部使用 docker-compose (從您的 Azure DevOps Services 部署工作)，來部署 Docker 應用程式及一組相關容器或服務，如圖 5-6 所示。

![CD 部署步驟 (#4) 可以發佈到不同的環境，例如問與答、預備環境和生產環境。](./media/image6.png)

**圖 5-6**. 將應用程式容器部署到簡單的 Docker 主機環境登錄

圖 5-7 顯示您如何按一下 [新增工作] 對話方塊中的 [Docker Compose]，透過 Azure DevOps Services 將您的組建 CI 連線到 QA/測試環境。 不過，部署到預備環境或生產環境時，您通常會使用 Release Management 功能來處理多個環境 (例如 QA、預備環境和生產環境)。 如果您要部署到單一 Docker 主機，它會使用 Azure DevOps Services "Docker Compose" 工作 (這會在幕後叫用 `docker-compose up` 命令)。 如果您要部署到 Azure Kubernetes Service (AKS)，它會使用 Docker 部署工作，如下一節中所述。

![新增 Docker Compose 工作的瀏覽器檢視。](./media/image7.png)

**圖 5-7**。 在 Azure DevOps Services 管線中新增 Docker Compose 工作

當您在 Azure DevOps Services 中建立發行時，它會接受一組輸入成品。 這些成品在所有不同環境的發行存留期中會保持不變。 當您引進容器時，輸入成品會識別登錄中要部署的映像。 根據這些映像的識別方式，不保證會在發行期間保持相同的輸送量，最明顯的例子是當您從 `docker-compose` 檔案參考 `myimage:latest` 時。

Azure DevOps Services 範本可讓您產生包含特定登錄映像摘要的組建成品，保證可唯一識別相同的映像二進位檔。 這些是您真正想要用作發行輸入的檔案。

### <a name="managing-releases-to-docker-environments-by-using-azure-devops-services-release-management"></a>使用 Azure DevOps Services Release Management 管理對 Docker 環境的發行

透過 Azure DevOps Services 範本，您可以建置新的映像、將其發佈到 Docker 登錄、在 Linux 或 Windows 主機上執行，以及使用 `docker-compose` 等命令將多個容器部署為整個應用程式，全部都是透過適用於多個環境的 Azure DevOps Services Release Management 功能，如圖 5-8 所示。

![Azure DevOps 的瀏覽器檢視，其中設定 Docker compose 發行。](./media/image8.png)

**圖 5-8**。 從 Azure DevOps Services Release Management 設定 Azure DevOps Services Docker Compose 工作

不過請記住，在圖 5-6 中顯示並在圖 5-8 中實作的案例是一個簡單案例 (部署到單一 Docker 主機和 VM，每個映像會有一個容器或執行個體)，可能僅適用於開發或測試案例。 在大多數企業生產案例中，您會想要在多個節點、伺服器和 VM 之間進行負載平衡，以取得高可用性 (HA) 和便於管理的延展性；此外，您也想要有「智慧型容錯移轉」，以便在伺服器或節點失敗時，可將其服務和容器移至另一個主機伺服器或 VM。 在此情況下，您需要更進階的技術，例如容器叢集、協調器和排程器。 因此，部署到這些叢集的方式是藉由處理下一節中所述的進階案例。

### <a name="deploying-docker-applications-to-docker-clusters"></a>將 Docker 應用程式部署到 Docker 叢集

分散式應用程式的本質需要同時散發計算資源。 若要取得生產級別功能，您必須擁有可根據集區資源提供高延展性和高可用性的叢集功能。

您可以從 CLI 工具或 Web UI 手動將容器部署到這些叢集，但您應該將這類手動工作保留給位置部署測試或管理目的使用，例如向外延展或監視。

從 CD 觀點來看，特別是 Azure DevOps Services，您可以從 Azure DevOps Services Release Management 環境執行特別建立的部署工作，這會將容器化應用程式部署到 Container Service 中的分散式叢集，如圖 5-9 所示。

![CD 部署步驟 (#4) 也可以透過協調器發佈到叢集。](./media/image9.png)

**圖 5-9**。 將分散式應用程式部署到 Container Service

一開始，當部署到特定叢集或協調器時，傳統上會使用每個協調器的特定部署指令碼和機制 (亦即，Kubernetes 與 Service Fabric 會有不同的部署機制)，而不是更簡單且便於使用的 `docker-compose` 工具 (以 `docker-compose.yml` 定義檔為基礎)。 不過，幸好有 Azure DevOps Services Docker 部署工作 (如圖 5-10 所示)，您現在也可以直接使用熟悉的 `docker-compose.yml` 檔案部署到支援的協調器，因為此工具會為您執行該「轉譯」(從您的 `docker-compose.yml` 檔案轉譯為協調器所需的格式)。

![Azure DevOps 中工作目錄的瀏覽器檢視，其中顯示 [部署至 Kubernetes] 工作。](./media/add-deploy-to-kubernetes-task.png)

**圖 5-10**。 將 [部署至 Kubernetes] 工作新增至您的環境

圖 5-11 示範如何使用可設定的區段來編輯 [部署至 Kubernetes] 工作。 此工作會擷取可供使用的自訂 Docker 映像，以部署為叢集中的容器。

![Azure DevOps 中 [部署至 Kubernetes] 工作定義的瀏覽器檢視。](./media/edit-deploy-to-kubernetes-task.png)

**圖 5-11**。 部署到 ACS DC/OS 的 Docker 部署工作定義

> [!INFORMATION] 若要深入了解使用 Azure DevOps Services 和 Docker 的 CD 管線，請瀏覽 <https://azure.microsoft.com/services/devops/pipelines>

## <a name="step-5-run-and-manage"></a>步驟 5：執行和管理

由於在企業生產層級執行和管理應用程式本身就是個重要的主題，且由於在該層級執行之作業和人員類型 (IT 作業) 及此領域的廣大範圍，因此下一章將全部用來說明該主題。

## <a name="step-6-monitor-and-diagnose"></a>步驟 6：監視與診斷

本主題也會在下一章中討論，這是 IT 人員在生產系統中執行工作的一部分；不過，值得注意的是，此步驟中取得的見解必須回饋給開發小組，以便持續改善應用程式。 從該觀點來看，這也是 DevOps 的一部分，但通常會由 IT 人員來執行工作和作業。

只有在監視和診斷 100% 位於 DevOps 領域內時，開發小組才會對測試或搶鮮版 (Beta) 環境執行監視程序和分析。 這會藉由執行負載測試，或是藉由監視搶鮮版 (Beta) 或 QA 環境來完成，其中搶鮮版 (Beta) 測試人員會嘗試新版本。

>[!div class="step-by-step"]
>[上一頁](index.md)
>[下一頁](create-ci-cd-pipelines-azure-devops-services-aspnetcore-kubernetes.md)
