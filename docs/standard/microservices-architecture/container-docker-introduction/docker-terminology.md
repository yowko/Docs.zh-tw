---
title: "Docker 術語"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Docker 術語"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 885b1fbd3369dec54ebde21a5378630c764f852d
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="docker-terminology"></a>Docker 術語

此區段會列出詞彙和定義，您應該要熟悉之前深入 Docker。 如需進一步定義，請參閱廣泛[詞彙](https://docs.docker.com/v1.11/engine/reference/glossary/)Docker 所提供。

**容器映像**: 套件與所有相依性和建立容器所需的資訊。 映像包括所有相依性 （例如架構），再加上部署和執行容器執行階段所使用的組態。 通常，映像會衍生自會彼此交互堆疊以構成容器的檔案系統層級的多個基底映像。 一旦建立之後，映像不變。

**容器**： 的 Docker 映像的執行個體。 容器代表執行單一應用程式、 處理序或服務。 其中包含內容的 Docker 映像、 執行環境，以及一組標準的指示。 擴充服務，當您從相同的映像建立容器的多個執行個體。 或批次工作可以建立多個容器從相同的映像，將不同的參數傳遞至每個執行個體。

**標記**： 記號或標籤，如此就可以識別不同的影像或相同的映像 （依據版本號碼或目標環境） 的版本，您可以套用至映像。

**Dockerfile**： 文字檔案，其中包含有關如何建立 Docker 映像。

**建置**： 建立容器映像的動作為基礎的資訊和提供其 Dockerfile 中，以及映像的建立位置的資料夾中的其他檔案的內容。 您可以建立 Docker docker 建置命令的影像。

**儲存機制 （儲存機制）**： 相關的 Docker 映像，加上標記，指出映像版本的集合。 某些儲存機制包含多個變異的特定映像，例如包含 Sdk （高），其中包含唯一的執行階段，（輕） 映像的映像等等。這些變異可以使用標記來標記。 單一儲存機制可以包含平台的變異，例如 Linux 映像和 Windows 映像。

**登錄**： 服務可提供存取至儲存機制。 最公用映像的預設登錄是[Docker Hub](https://hub.docker.com/) （Docker 做為組織所擁有）。 登錄通常包含多個小組的儲存機制。 公司通常具有私人登錄來儲存和管理他們所建立的映像。 Azure 容器登錄中是另一個範例。

**Docker Hub**： 上傳映像，並使用它們的公用登錄。 Docker Hub 提供 Docker 映像裝載、 公用或私人登錄、 組建觸發程序和 web 連結，以及與 GitHub 和 Bitbucket 整合。

**Azure 容器登錄中**： 公用使用 Docker 映像和其元件在 Azure 中的資源。 這可提供的登錄，這是您在 Azure 中部署接近和，可讓您控制存取權，讓您可以使用您的 Azure Active Directory 群組和權限。

**Docker 信任登錄 (DTR)**: （從 Docker) Docker 登錄服務，可以是安裝在內部部署，讓它都位於組織的資料中心和網路內。 很方便應管理企業內的私人映像。 Docker Trusted Registry 是 Docker Datacenter 產品的一部分。 如需詳細資訊，請參閱[Docker 信任登錄 (DTR)](https://docs.docker.com/docker-trusted-registry/overview/)。

**Docker Community Edition (CE)**： 適用於 Windows 和 macOS 如建置、 執行和測試容器在本機開發工具。 用於 Windows CE docker 會提供開發環境適用於 Linux 和 Windows 容器。 在 Windows 上的 Linux Docker 主機根據[HYPER-V](https://www.microsoft.com/en-us/server-cloud/solutions/virtualization.aspx)虛擬機器。 Windows 容器主機直接以 Windows 為基礎。 適用於 Mac 的 docker CE 根據 Apple Hypervisor 架構和[xhyve hypervisor](https://github.com/mist64/xhyve)，文中提供 Linux Docker 主機的虛擬機器在 Mac OS X Docker CE for Windows 和 Mac 的取代以 Oracle 為基礎的 Docker 工具箱VirtualBox。

**Docker Enterprise Edition (EE)**： 適用於 Linux 和 Windows 開發的 Docker 工具的企業規模版本。

**撰寫**： 命令列工具及 YAML 檔案格式定義和執行多個容器應用程式的中繼資料。 您定義的一個或多個.yml 檔案，可以覆寫值根據環境的多個映像為基礎的單一應用程式。 您已建立定義之後，您可以部署整個多容器應用程式使用單一命令 (docker-撰寫總) 會建立 Docker 主機上的每個影像的容器。

**叢集**： 的 Docker 主機，讓應用程式可以擴充至多個執行個體的服務公開好像單一虛擬 Docker 主機時，集合會分散在叢集中的多個主機。 Docker 叢集可以使用 Docker Swarm、 Mesosphere DC/OS、 Kubernetes 和 Azure Service Fabric 建立。 (如果您使用 Docker Swarm 來管理叢集，您通常參照為叢集*廣域*而不是叢集。)

**Orchestrator**： 一種工具，可簡化管理的叢集與 Docker 主機。 Orchestrators 可讓您管理其影像、 容器和主機透過命令列介面 (CLI) 或圖形化使用者介面。 您可以管理容器網路功能、 設定、 負載平衡，服務探索、 高可用性、 Docker 主機組態，等等。 協調者負責執行、 散發、 調整及修復的節點集合之間的工作負載。 一般而言，orchestrator 產品是提供叢集基礎結構，例如 Mesosphere DC/OS、 Kubernetes、 Docker Swarm，和 Azure Service Fabric 的相同產品。


>[!div class="step-by-step"]
[上一個](docker-defined.md) [下一步] (docker-容器-映像-registries.md)
