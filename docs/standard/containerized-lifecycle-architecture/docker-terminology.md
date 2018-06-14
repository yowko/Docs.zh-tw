---
title: Docker 術語
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 09/21/2017
ms.openlocfilehash: 7a8ec2233b7927c1e3f85f5a3536a889a6a55e22
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
ms.locfileid: "33574022"
---
# <a name="docker-terminology"></a>Docker 術語

此區段會列出詞彙和定義，您應該熟悉在更深入探究 Docker 之前 (如需進一步定義，請參閱廣泛[詞彙](https://docs.docker.com/glossary/)提供在 Docker <https://docs.docker.com/glossary/>:

-   **容器映像** 封裝的所有相依性和建立容器所需的資訊。 映像包括所有的相依性 （例如架構） 以及部署和容器執行階段所使用的組態。 通常，映像衍生自多個基底映像，圖層堆疊在彼此構成容器的檔案系統的其中一個。 一旦建立後，映像不變。

-   **容器** Docker 映像的執行個體。 容器代表執行階段為單一應用程式、 處理序或服務。 其中包含內容的 Docker 映像、 在執行階段環境，以及一組標準的指示。 擴充服務時，您會從同一個映像建立容器的多個執行個體。 或者，批次工作可以建立多個容器從相同的映像，將不同的參數傳遞至每個執行個體。

-   **標記** 記號或標籤，如此就可以識別不同的影像或相同的映像 （依據版本號碼或目的地環境） 的版本，您可以套用至映像。

-   **Dockerfile** 文字檔案，其中包含有關如何建立 Docker 映像。

-   **建置** 建立容器映像的動作為基礎的資訊和提供其 Dockerfile 與映像的建立位置的資料夾中的其他檔案的內容。 您可以建立映像使用 Docker docker 建置命令。

-   **儲存機制 (也稱為 repo)** 相關 Docker 映像加上標記，指出映像版本的集合。 某些儲存機制包含多個變異的特定映像，例如包含 Sdk （高），包含只執行階段 （輕），映像的映像，依此類推。 這些變化可以加上標記。 單一存放庫可包含平台的變異，例如 Linux 映像和 Windows 映像。

-   **登錄** 服務可提供存取至儲存機制。 大多數公用映像的預設登錄是 [Docker Hub](https://hub.docker.com/) (以組織形式為 Docker 所擁有）。 登錄通常會包含來自多個小組的存放庫。 公司通常具有私人登錄來儲存和管理他們所建立的映像。 *Azure 容器登錄中*是另一個範例。

-   **Docker Hub** 公用登錄上傳映像，並使用它們。 Docker Hub 提供 Docker 映像裝載、公開或私人登錄、組建觸發程序和 Webhook，以及與 GitHub 和 Bitbucket 的整合。

-   **Azure 容器登錄中** 公用使用 Docker 映像和其元件在 Azure 中的資源。 這會提供接近 Azure 部署的登錄，並可讓您控制存取權，以便使用您的 Azure Active Directory 群組和權限。

-   **Docker 信任登錄 (DTR)** （從 Docker) Docker 登錄服務，您可以安裝在內部部署，讓它位於組織的資料中心和網路中。 這會方便在企業內管理私人映像。 Docker Trusted Registry 隨附於 Docker Datacenter 產品中。 如需詳細資訊，請移至[ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/)。

-   **Docker Community Edition (CE)** 適用於 Windows 和 macOS 如建置、 執行和測試容器在本機開發工具。 Docker CE for Windows 提供適用於 Linux 和 Windows 容器的開發環境。 在 Windows 上的 Linux Docker 主機根據[HYPER-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM。 Windows 容器的主機則是直接以 Windows 為基礎。 適用於 Mac 的 docker CE 根據 Apple Hypervisor 架構和[xhyve hypervisor](https://github.com/mist64/xhyve)，文中提供的 Linux Docker 主機 VM 在 Mac OS X Docker CE for Windows 和 Mac 的取代 Docker [工具箱]，Oracle VirtualBox 為基礎。

-   **Docker Enterprise Edition (EE)** 企業規模的版本適用於 Linux 和 Windows 開發的 Docker 工具。

-   **撰寫** 命令列工具及 YAML 檔案格式定義和執行 multicontainer 應用程式的中繼資料。 您可以使用一或多個 .yml 檔案，來定義以多個映像為基礎的單一應用程式，這些檔案可能會覆寫相依於環境的值。 您已建立定義之後，您可以部署整個 multicontainer 應用程式使用單一命令 (docker-撰寫總) 會建立 Docker 主機上的每個影像的容器。

-   **叢集** 分散在叢集中的多個主機的 Docker 主機公開就如同單一虛擬 Docker 主機，讓應用程式可以擴充至多個服務執行個體的集合。 您可以透過 Docker Swarm、 Mesosphere DC/OS、 Kubernetes 和 Azure Service Fabric 建立 Docker 叢集。 (如果您使用 Docker Swarm 來管理叢集，您通常會將叢集稱為「群集」而不是叢集)。

-   **Orchestrator** 一種工具，可簡化管理的叢集與 Docker 主機。 您可以使用 orchestrators，管理其影像、 容器和主機透過 CLI 或圖形化使用者介面。 您可以管理容器網路功能、組態、負載平衡、服務探索、高可用性、Docker 主機組態等等。 協調器會負責跨節點集合執行、散發、擴充及修復工作負載。 一般而言，協調器產品與提供叢集基礎結構的產品相同，例如 Mesosphere DC/OS、Kubernetes、Docker Swarm 和 Azure Service Fabric。


>[!div class="step-by-step"]
[上一個] (的模擬層是-docker.md) [下一步] (docker-容器-映像-和-registries.md)
