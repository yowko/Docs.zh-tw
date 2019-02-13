---
title: Docker 術語
description: 了解使用 Docker 時，已使用每天的一些基本術語。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/23/2018
ms.openlocfilehash: 1514a2199efe52a411f61649fc21e906bba5b13c
ms.sourcegitcommit: 30e2fe5cc4165aa6dde7218ec80a13def3255e98
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/13/2019
ms.locfileid: "56218719"
---
# <a name="docker-terminology"></a>Docker 術語

此區段會列出詞彙和定義，您應該熟悉在深入探究 Docker 之前 (如需進一步定義，請參閱廣泛[詞彙](https://docs.docker.com/glossary/)提供在 Docker <https://docs.docker.com/glossary/>:

-   **容器映像** 封裝的所有相依性和建立容器所需的資訊。 映像會包含所有的相依性 （例如架構） 以及部署和設定，以供容器執行階段。 通常，映像衍生自多個基底映像，層級堆疊在另一個則以構成容器檔案系統之上的其中一個。 一旦建立後，影像是不可變。

-   **容器** Docker 映像執行個體。 容器代表單一應用程式、 處理序或服務的執行階段。 它包含 Docker 映像，執行階段環境和一組標準的指示的內容。 擴充服務時，您會從同一個映像建立容器的多個執行個體。 或者，以批次工作可以建立多個容器從相同的映像，並將不同的參數傳遞給每個執行個體。

-   **標記** 的標記或，如此就可以識別不同的映像或版本 （取決於版本號碼或目的地環境） 的相同映像，您可以套用至映像的標籤。

-   **Dockerfile** 文字檔案，其中包含如何建置 Docker 映像的指示。

-   **建置** 建置容器映像的動作會根據其 Dockerfile，以及其他檔案的映像的建立位置的資料夾中所提供的內容與資訊。 您可以使用 Docker 的 docker build 命令建置映像。

-   **存放庫 (也稱為 repo)** 加上標記指出映像版本相關的 Docker 映像的集合。 某些存放庫包含多個特定的映像，例如包含 Sdk （更繁重），其中包含只執行階段 （較淺） 映像的映像變體，依此類推。 這些變化可以加上標記。 單一存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。

-   **登錄** 服務可提供存取權儲存機制。 大多數公用映像的預設登錄是 [Docker Hub](https://hub.docker.com/) (以組織形式為 Docker 所擁有）。 登錄通常會包含來自多個小組的存放庫。 公司通常會有私人登錄來儲存和管理他們所建立的映像。 *Azure Container Registry*是另一個範例。

-   **Docker Hub** 影像上傳並使用它們的公開登錄。 Docker Hub 提供 Docker 映像裝載、公開或私人登錄、組建觸發程序和 Webhook，以及與 GitHub 和 Bitbucket 的整合。

-   **Azure Container Registry** 使用 Docker 映像和其元件在 Azure 中的公用資源。 這會提供接近 Azure 部署的登錄，並可讓您控制存取權，以便使用您的 Azure Active Directory 群組和權限。

-   **Docker Trusted Registry (DTR)** （來自 Docker) 的 Docker 登錄服務，您可以安裝在內部部署，讓它位於組織的資料中心和網路。 這會方便在企業內管理私人映像。 Docker Trusted Registry 隨附於 Docker Datacenter 產品中。 如需詳細資訊，請移至[ https://docs.docker.com/docker-trusted-registry/overview/ ](https://docs.docker.com/docker-trusted-registry/overview/)。

-   **Docker Community Edition (CE)** 適用於 Windows 和 macOS 的建置、 執行和測試在本機容器開發工具。 Docker CE for Windows 提供適用於 Linux 和 Windows 容器的開發環境。 在 Windows 上的 Linux Docker 主機根據[HYPER-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) VM。 Windows 容器的主機則是直接以 Windows 為基礎。 Docker CE for Mac 以 Apple Hypervisor 架構為基礎而[xhyve hypervisor](https://github.com/mist64/xhyve)，以提供 Linux Docker 主機 VM，在 Mac OS x。 Docker CE for Windows 和 Mac 取代以 Oracle VirtualBox 為基礎的 Docker Toolbox。

-   **Docker Enterprise Edition (EE)** 是企業級的舊版適用於 Linux 和 Windows 開發的 Docker 工具。

-   **Compose** 命令列工具和 YAML 檔案來定義和執行多容器應用程式的中繼資料格式。 您可以使用一或多個 .yml 檔案，來定義以多個映像為基礎的單一應用程式，這些檔案可能會覆寫相依於環境的值。 您已建立的定義之後，您可以部署整個多容器應用程式使用單一命令 (docker-docker-compose up) Docker 主機上建立一個容器，每個影像。

-   **叢集** 如同它們是單一虛擬 Docker 主機，確保應用程式可以擴展多個執行個體的服務所公開的 Docker 主機集合分散在叢集內的多部主機。 您可以使用 Docker Swarm、 Mesosphere DC/OS、 Kubernetes 和 Azure Service Fabric 來建立 Docker 叢集。 (如果您使用 Docker Swarm 來管理叢集，您通常會將叢集稱為「群集」而不是叢集)。

-   **Orchestrator** 可簡化叢集和 Docker 主機的管理工具。 使用協調器，您可以管理其映像、 容器和主機透過 CLI 或圖形化使用者介面。 您可以管理容器網路功能、組態、負載平衡、服務探索、高可用性、Docker 主機組態等等。 協調器會負責跨節點集合執行、散發、擴充及修復工作負載。 一般而言，協調器產品與提供叢集基礎結構的產品相同，例如 Mesosphere DC/OS、Kubernetes、Docker Swarm 和 Azure Service Fabric。

>[!div class="step-by-step"]
>[上一頁](what-is-docker.md)
>[下一頁](docker-containers-images-and-registries.md)