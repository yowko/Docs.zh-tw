---
title: Docker 應用程式之外部迴圈 DevOps 工作流程中的步驟
description: Microsoft 平台和工具的容器化 Docker 應用程式生命週期
ms.date: 02/15/2019
ms.openlocfilehash: 9fdc5acfd375e4f2266859f061ef1c854286b914
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65644976"
---
# <a name="creating-cicd-pipelines-in-azure-devops-services-for-a-net-core-20-application-on-containers-and-deploying-to-a-kubernetes-cluster"></a>在 Azure DevOps Services 中為容器上的 .NET Core 2.0 應用程式建立 CI/CD 管線並部署到 Kubernetes 叢集

圖 5-12，您可以看到的端對端 DevOps 案例，涵蓋的程式碼管理程式碼編譯、 建置 Docker 映像、 Docker 映像推送到 Docker 登錄及最後部署至 Azure 中的 Kubernetes 叢集。

![工作流程：在開發電腦中啟動。 推送到存放庫開始使用自訂的映像，以取得推送到 Docker 登錄，並接著由 CD/部署工作，最後，將推送至 AKS / CI 組建的工作。](media/docker-workflow-ci-cd-aks.png)

**圖 5-12**。 建立 Docker 映像和部署到 Azure 中的 Kubernetes 叢集的 CI/CD 案例

請務必反白顯示兩個管線、 組建/CI 和發行/CD，透過 Docker 登錄 （例如 Docker Hub 或 Azure Container Registry） 連線。 Docker 登錄是其中一個主要的差異，相較於傳統的 CI/CD 程序，不使用 Docker。

如所示的圖 5-13，第一個階段是組建/CI 管線。 Azure DevOps 服務中，您可以建立組建/CI 管線，將會編譯程式碼、 建立 Docker 映像，並將其推送到 Docker Hub 或 Azure Container Registry 的 Docker 登錄。

![Azure DevOps，建置程序工作定義的瀏覽器檢視。](media/build-ci-pipeline-azure-devops-push-to-docker-registry.png)

**圖 5-13**。 Azure DevOps 建置 Docker 映像，並將映像推送到 Docker 登錄中的組建/CI 管線

第二個階段是建立的部署/發行管線。 在 Azure DevOps 服務中，您可以輕鬆建立使用 Azure DevOps 服務，Kubernetes 工作目標的 Kubernetes 叢集，如所示的圖 5-14 部署管線。

![Azure DevOps 的瀏覽器檢視部署至 Kubernetes 工作定義。](media/release-cd-pipeline-azure-devops-deploy-to-kubernetes.png)

**圖 5-14**。 Azure DevOps 服務部署到 Kubernetes 叢集的發行/CD 管線

> [!逐步解說] eShopModernized 部署至 Kubernetes:
>
> Azure DevOps 的 CI/CD 管線的詳細逐步解說將部署至 Kubernetes，請參閱這篇文章: \
><https://github.com/dotnet-architecture/eShopModernizing/wiki/04.-How-to-deploy-your-Windows-Containers-based-apps-into-Kubernetes-in-Azure-Container-Service-(Including-CI-CD)>

>[!div class="step-by-step"]
>[上一頁](docker-application-outer-loop-devops-workflow.md)
>[下一頁](../run-manage-monitor-docker-environments/index.md)
