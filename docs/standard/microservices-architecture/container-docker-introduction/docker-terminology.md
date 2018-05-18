---
title: Docker 術語
description: 容器化 .NET 應用程式的 .NET 微服務架構 | Docker 術語
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 9bbeff8c467e762e682fdaf99c8a11851b291db8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="docker-terminology"></a>Docker 術語

本節列出您應該熟悉才能深入探索 Docker 的術語和定義。 如需進一步定義，請參閱 Docker 所提供的詳盡[字彙表](https://docs.docker.com/glossary/)。

**容器映像**：包含建立容器所需之所有相依性和資訊的封裝。 映像會包含所有相依性 (例如架構)，以及容器執行階段所要使用的部署和執行組態。 通常，一個映像會衍生自多個基底映像，這些基底映像是彼此交互堆疊以構成容器檔案系統的圖層。 映像一旦建立，就不可改變。

**容器**：Docker 映像的執行個體。 容器代表單一應用程式、處理序或服務的執行。 其中包含 Docker 映像的內容、執行環境和一組標準的指示。 擴充服務時，您會從同一個映像建立容器的多個執行個體。 或者，一個批次工作可以從同一個映像建立多個容器，並將不同的參數傳遞至每個執行個體。

**標記**：您可以套用至映像的標記或標籤，以便識別相同映像的不同映像版本 (視版本號碼或目標環境而定)。

**Dockerfile**：文字檔，其中包含有關如何建立 Docker 映像的指示。

**建立**：建立容器映像的動作，該映像會以其 Dockerfile 及建立映像之資料夾中其他檔案所提供的資訊和內容為依據。 您可以使用 Docker 的 docker build 命令來建立映像。

**存放庫 (Repository 或 Repo)**：相關的 Docker 映像集合，已加上標記指出映像版本。 某些存放庫包含特定映像的多種變化，例如包含 SDK 的映像 (較大)、只包含執行階段的映像 (較小) 等等。這些變化可以加上標記。 一個存放庫可以包含多種平台變化，例如 Linux 映像和 Windows 映像。

**登錄**：提供存放庫存取權的服務。 大多數公用映像的預設登錄是 [Docker Hub](https://hub.docker.com/) (以組織形式為 Docker 所擁有）。 登錄通常會包含來自多個小組的存放庫。 公司通常會有私人登錄來儲存及管理其所建立的映像。 Azure Container Registry 是另一個範例。

**Docker Hub**：上傳並使用映像的公開登錄。 Docker Hub 提供 Docker 映像裝載、公開或私人登錄、組建觸發程序和 Webhook，以及與 GitHub 和 Bitbucket 的整合。

**Azure Container Registry**：Azure 中使用 Docker 映像及其元件的公用資源。 這會提供接近 Azure 部署的登錄，並可讓您控制存取權，以便使用您的 Azure Active Directory 群組和權限。

**Docker Trusted Registry (DTR)**：可在內部部署安裝的 Docker 登錄服務 (來自 Docker)，以便存在於組織的資料中心和網路內。 這會方便在企業內管理私人映像。 Docker Trusted Registry 隨附於 Docker Datacenter 產品中。 如需詳細資訊，請參閱 [Docker Trusted Registry (DTR)](https://docs.docker.com/docker-trusted-registry/overview/)。

**Docker Community Edition (CE)**：適用於 Windows 和 macOS 的開發工具，可在本機建置、執行及測試容器。 Docker CE for Windows 提供適用於 Linux 和 Windows 容器的開發環境。 Windows 上的 Linux Docker 主機是以 [Hyper-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx) 虛擬機器為基礎。 Windows 容器的主機則是直接以 Windows 為基礎。 Docker CE for Mac 是以 Apple Hypervisor 架構和 [xhyve hypervisor](https://github.com/mist64/xhyve) 為基礎，其提供 Mac OS X 版的 Linux Docker 主機虛擬機器。Docker CE for Windows 和 Docker CE for Mac 取代以 Oracle VirtualBox 為基礎的 Docker Toolbox。

**Docker Enterprise Edition (EE)**：適用於 Linux 和 Windows 開發之企業級版本的 Docker 工具。

**撰寫**：命令列工具和 YAML 檔案格式，其中繼資料可定義及執行多容器應用程式。 您可以使用一或多個 .yml 檔案，來定義以多個映像為基礎的單一應用程式，這些檔案可能會覆寫相依於環境的值。 建立定義之後，您可以使用單一命令 (docker-compose up) 來部署整個多容器應用程式，以在 Docker 主機上針對每個映像建立一個容器。

**叢集**：以單一虛擬 Docker 主機形式公開的 Docker 主機集合，讓應用程式可以擴充為分散到叢集內多部主機的多個服務執行個體。 您可以使用 Docker Swarm、Mesosphere DC/OS、Kubernetes 和 Azure Service Fabric 來建立 Docker 叢集 (如果您使用 Docker Swarm 來管理叢集，您通常會將叢集稱為「群集」而不是叢集)。

**協調器**：可簡化叢集和 Docker 主機管理的工具。 協調器可讓您透過命令列介面 (CLI) 或圖形化 UI 來管理其映像、容器和主機。 您可以管理容器網路功能、組態、負載平衡、服務探索、高可用性、Docker 主機組態等等。 協調器會負責跨節點集合執行、散發、擴充及修復工作負載。 一般而言，協調器產品與提供叢集基礎結構的產品相同，例如 Mesosphere DC/OS、Kubernetes、Docker Swarm 和 Azure Service Fabric。


>[!div class="step-by-step"]
[上一個] (docker-defined.md) [下一個] (docker-containers-images-registries.md)
