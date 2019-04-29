---
title: 容器化應用程式的 Microsoft 平台和工具簡介
description: 了解 Microsoft 的供應項目，以支援 Docker 應用程式生命週期。
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 02/15/2019
ms.openlocfilehash: 8536703a520434c0e393c5f46005c2ac02d5d849
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/23/2019
ms.locfileid: "61934653"
---
# <a name="introduction-to-the-microsoft-platform-andtools-for-containerized-apps"></a>Microsoft 平台和容器化應用程式的工具簡介

*願景：建立具可調適性，企業級容器化應用程式生命週期，來擴展您的開發、 IT 營運和進入生產階段管理。*

圖 3-1 顯示依工作類型分類的 Docker 應用程式生命週期中的主要部分，而工作類型是由多個小組 (應用程式開發、DevOps 基礎結構程序以及 IT 管理和作業) 所衍生。 通常，在企業中，負責每個區域之「人物代表」的設定檔會不同。 就是他們的技術。

![Microsoft 的工具。 針對開發/設計的工作負載：Windows、 VS 和 VS Code 中，.NET Core，Azure Kubernetes Service 的 docker 引擎。 出貨建置/測試工作負載：Azure DevOps，Team Foundation Server，Docker CLI，Azure Kubernetes 服務。 執行/監視/管理工作負載：Azure 監視器中，Azure 入口網站 Azure Kubernetes 服務，Service Fabric 中，其他協調器。](./media/image1.png)

**圖 3-1** 在 Microsoft 平台和工具的容器化 Docker 應用程式生命週期的主要支柱

容器化的 Docker 生命週期工作流程可以是一開始規範性根據 「 預設產品選項，」 讓開發人員開始更快、 更容易，但很基本，實際上有必須開放的架構，因此它會是彈性的工作流程可調整為不同的內容中，從每個組織或企業。 工作流程基礎結構 (元件和產品) 必須具有足夠的彈性，才能涵蓋每家公司未來將要有的環境，即使可以將開發或 DevOps 產品切換成其他開發或 DevOps 產品也是一樣。 此彈性、開放性以及平台和基礎結構中各種技術就是容器化 Docker 應用程式的 Microsoft 優先順序，如下列各章所述。

表 3-1 示範容器化 Docker 應用程式的 Microsoft DevOps 意圖是提供開放式 DevOps 工作流程，讓您可以選擇要用於每個階段的產品 (Microsoft 或協力廠商)，同時提供簡化工作流程以提供已連線「預設產品」；因此，您可以快速地開始使用 Docker 應用程式的企業級 DevOps 工作流程。

**表 3-1。** DevOps 工作流程中，開啟任何技術

| 主機 | Microsoft 技術 | 協力廠商 - Azure 插入式 |
| ---------------------------| ----------------------------------------------------| --------------------------------------------------------------------------------|
| Docker 應用程式的平台   | • Microsoft Visual Studio 和 Visual Studio Code<br /> • .NET<br /> • Microsoft Azure Container Service<br /> • Azure Service Fabric<br /> • Azure Container Registry<br /> | • 任何程式碼編輯器 (例如，Sublime)<br /> • 任何語言 (Node.js、Java、Go 等等)<br /> • 任何協調器和排程器<br /> • 任何 Docker 登錄<br /> |
| Docker 應用程式的 DevOps     | • Azure DevOps 服務<br /> • Microsoft Team Foundation Server<br /> • Azure Container Service<br /> • Azure Service Fabric<br /> | • GitHub、Git、Subversion 等等<br /> • Jenkins、Chef、Puppet、Velocity、CircleCI、TravisCI 等等<br /> • 內部部署 Docker Datacenter、Docker Swarm、Mesos DC/OS、Kubernetes 等等<br /> |
| 管理和監視  | • Operations Management Suite<br /> • Applications Insights<br /> | • Marathon、Chronos 等等<br />

表 3-1 中所定義之容器化 Docker 應用程式的 Microsoft 平台和工具，包含下列元件：

- **Docker 應用程式開發的平台**：服務的開發，或構成「應用程式」的服務集合。 開發平台提供開發人員在 將其程式碼推送至共用程式碼存放庫之前所需的所有工作。 開發服務，部署為容器，是類似於具有相同的應用程式或服務不使用 Docker 的開發。 您繼續使用您慣用的語言 （.NET、 Node.js、 Go 等） 和慣用的編輯器或 IDE，例如 Visual Studio 或 Visual Studio Code。 不過，您可以開發 Docker 環境中的服務，而不需要將 Docker 視為部署目的地。 您可以在本機建置、執行、測試和偵錯容器中的程式碼，並在開發階段提供目的地環境。 透過在本機提供目的地環境，Docker 容器設定項目將有助於大幅改善 DevOps 生命週期。 Visual Studio 和 Visual Studio Code 的延伸模組可以整合開發程序內的 Docker 容器。

- **Docker 應用程式的 DevOps**建立 Docker 應用程式的開發人員可以使用[Azure DevOps 服務](https://azure.microsoft.com/services/devops/)或任何其他第三方產品，例如 Jenkins，以建置完整自動化應用程式生命週期管理 (ALM)。

  使用 Azure DevOps 服務，開發人員可以建立焦點所在容器的 DevOps 快速且反覆的程序，它涵蓋了原始碼控制從任何地方 （Azure DevOps 服務-Git、 GitHub、 任何遠端 Git 存放庫或 Subversion），持續整合 (CI)內部的單元測試、 間 container/服務的整合測試、 持續傳遞 (CD) 和發行管理 (RM)。 開發人員也可以自動化其 Docker 應用程式從預備和生產環境的開發到 Azure Container Service 的發行。

- **管理和監視**IT 管理及監視生產應用程式和服務整合一致的體驗中的兩個檢視方塊的數種方式。

  - **Azure 入口網站** 如果您使用開放原始碼協調器，Azure Kubernetes Service (AKS)、 Service Fabric 和其他 orchestrator 協助您設定和維護 Docker 環境。 如果您要使用 Azure Service Fabric，則 Service Fabric Explorer 工具可讓您視覺化和設定叢集。

  - **Docker 工具** 您可以使用熟悉的工具來管理容器應用程式。 不需要變更現有 Docker 管理做法，即可將容器工作負載移至雲端。 使用您已熟悉並透過所選擇協調器的標準 API 端點所連線的應用程式管理工具。 您也可以使用其他協力廠商工具來管理 Docker 應用程式 (例如 Docker Datacenter) 甚至是 CLI Docker 工具。 

    即使您熟悉 Linux 命令，您可以管理容器應用程式使用 Microsoft Windows 和 PowerShell 子系統 Linux 命令列] 和 [產品 （Docker、 Kubernetes...） 在此 Linux 子系統功能上執行的用戶端。 您將進一步了解使用這些工具，在稍後在本書中使用您最愛的 Microsoft Windows 作業系統的 Linux 子系統。

  - **開放原始碼工具** 因為 AKS 會公開協調流程引擎的標準 API 端點，最熱門的工具會與 AKS 相容，並在大部分情況下，將現成 — 包括視覺化檢視、 監視，命令列工具，並甚至是未來可用的工具。

  - **Azure 監視器**是 Azure 的解決方案，以監視您的生產環境的每個角度。 您可以只將其 SDK 設定至您的服務，讓您可以從應用程式取得系統產生的記錄資料來監視生產 Docker 應用程式。

因此，Microsoft 會提供端對端容器化 Docker 應用程式生命週期的完整基礎。 不過，很*集合的產品和技術，讓您選擇性地選取，並整合現有工具和程序*。 廣泛方式的彈性以及功能深度的強度讓 Microsoft 十分適合進行容器化 Docker 應用程式開發。

>[!div class="step-by-step"]
>[上一頁](../Docker-application-lifecycle/containers-foundation-for-devops-collaboration.md)
>[下一頁](../design-develop-containerized-apps/index.md)
