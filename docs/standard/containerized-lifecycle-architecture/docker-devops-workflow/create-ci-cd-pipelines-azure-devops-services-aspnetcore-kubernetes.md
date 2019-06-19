---
title: Docker 應用程式之外部迴圈 DevOps 工作流程中的步驟
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 5bc85ad81d96b8dc2a90ce53bada475ee5662c44
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/13/2019
ms.locfileid: "65644976"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>在 Azure DevOps Services 中為容器上的 .NET Core 2.0 應用程式建立 CI/CD 管線並部署到 Kubernetes 叢集

在圖 5-12 中，您可以看到端對端 DevOps 案例，涵蓋程式碼管理、程式碼編譯、Docker 映像建置、Docker 映像推送至 Docker 登錄，最後部署至 Azure 中的 Kubernetes 叢集。

![工作流程：在開發電腦中開始。 推送至存放庫會使用自訂映像開始建置/CI 工作，該映像會推送至 Docker 登錄，最後由 CD/部署工作用於推送至 AKS。](media/docker-workflow-ci-cd-aks.png)

**圖 5-12**。 CI/CD 案例建立 Docker 映像並部署至 Azure 中的 Kubernetes 叢集

請務必注意這兩個管線，建置/CI 和發行/CD，這兩者是透過 Docker 登錄 (如 Docker Hub 或 Azure Container Registry) 連線。 相較於不具有 Docker 的傳統 CI/CD 程序，Docker 登錄是其中一項主要差異。

如圖 5-13 所示，第一個階段是建置/CI 管線。 在 Azure DevOps Services 中，您可以建立建置/CI 管線，這些管線將編譯程式碼、建立 Docker 映像，並將其推送至 Docker Hub 或 Azure Container Registry 等Docker 登錄。

![Azure DevOps 中建置程序工作定義的瀏覽器檢視。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**圖 5-13**。 Azure DevOps 中的建置/CI 管線會建置 Docker 映像並將映像推送至 Docker 登錄

第二個階段是建立部署/發行管線。 在 Azure DevOps Services 中，您可以使用 Azure DevOps Services 的 Kubernetes 工作，輕鬆建立以 Kubernetes 叢集為目標的部署管線，如圖 5-14 所示。

![Azure DevOps 中 [部署至 Kubernetes] 工作定義的瀏覽器檢視。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**圖 5-14**。 部署 Azure DevOps Services 中的發行/CD 管線至 Kubernetes 叢集

> [!Walkthrough] 將 eShopModernized 部署至 Kubernetes：
>
> 如需部署至 Kubernetes 之 Azure DevOps CI/CD 管線的詳細逐步解說，請參閱此貼文： \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[上一頁](docker-application-outer-loop-devops-workflow.md)
>[下一頁](../run-manage-monitor-docker-environments/index.md)
