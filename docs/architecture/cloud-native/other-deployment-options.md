---
title: 其他容器部署選項
description: 使用 Azure 的其他容器部署選項
ms.date: 04/13/2020
ms.openlocfilehash: 3cae771b3877215a7fc91afd4f406fdfc9ff2771
ms.sourcegitcommit: 5988e9a29cedb8757320817deda3c08c6f44a6aa
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/28/2020
ms.locfileid: "82199998"
---
# <a name="other-container-deployment-options"></a>其他容器部署選項

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

除了 Azure Kubernetes Service （AKS）之外，您也可以將容器部署到容器和 Azure 容器實例的 Azure App Service。

## <a name="when-does-it-make-sense-to-deploy-to-app-service-for-containers"></a>部署至容器的 App Service 有何意義？

不需要協調流程的簡單生產應用程式非常適合用於容器的 Azure App Service。

## <a name="how-to-deploy-to-app-service-for-containers"></a>如何部署至容器的 App Service

若要部署至[容器的 Azure App Service](https://azure.microsoft.com/services/app-service/containers/)，您需要有 AZURE CONTAINER REGISTRY （ACR）實例和認證才能存取。 將您的容器映射推送至 ACR 存放庫，讓它可以提取到您的 Azure App Service。 完成後，您可以設定應用程式以進行持續部署。 如此一來，每當 ACR 中的映射變更時，就會自動部署更新。

## <a name="when-does-it-make-sense-to-deploy-to-azure-container-instances"></a>部署至 Azure 容器實例的時機為何？

[Azure 容器實例（ACI）](https://azure.microsoft.com/services/container-instances/)可讓您在受控、無伺服器的雲端環境中執行 Docker 容器，而不需要設定虛擬機器或叢集。 對於可在隔離容器中執行的短期工作負載而言，這是很好的解決方案。 針對簡單的服務、測試案例、工作自動化和組建作業，請考慮 ACI。 ACI 會向上旋轉容器實例、執行工作，然後將其旋轉。

## <a name="how-to-deploy-an-app-to-azure-container-instances"></a>如何將應用程式部署至 Azure 容器實例

若要部署至[Azure 容器實例（ACI）](https://docs.microsoft.com/azure/container-instances/)，您需要 AZURE CONTAINER REGISTRY （ACR）和認證來進行存取。 一旦您將容器映射推送至存放庫，就可以使用它來提取 ACI。 您可以使用 Azure 入口網站或命令列介面來處理 ACI。 ACR 提供與 ACI 的緊密整合。 圖3-14 顯示如何將個別容器映射推送至 ACR。

![Azure Container Registry 執行實例](./media/acr-runinstance-contextmenu.png)

**圖 3-14**。 Azure Container Registry 執行實例

在 ACI 中建立實例，可以快速完成。 指定映射登錄、Azure 資源群組資訊、要配置的記憶體數量，以及要接聽的埠。 本[快速入門說明如何使用 Azure 入口網站將容器實例部署至 ACI](https://docs.microsoft.com/azure/container-instances/container-instances-quickstart-portal)。

部署完成之後，尋找新部署容器的 IP 位址，並透過您指定的埠與其通訊。

Azure 容器實例提供最快的方式，在 Azure 中執行簡單的容器工作負載。 您不需要設定 app service、orchestrator 或虛擬機器。 對於需要完整容器協調流程、服務探索、自動調整或協調升級的案例，我們建議 Azure Kubernetes Service （AKS）。

## <a name="references"></a>參考

- [什麼是 Kubernetes？](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [使用 Minikube 安裝 Kubernetes](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube 與 Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)
- [瞭解無伺服器冷啟動](https://azure.microsoft.com/blog/understanding-serverless-cold-start/)
- [預先準備就緒 Azure Functions 實例](https://docs.microsoft.com/azure/azure-functions/functions-premium-plan#pre-warmed-instances)
- [在使用自訂映像的 Linux 上建立函式](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [在 Docker 容器中執行 Azure Functions](https://markheath.net/post/azure-functions-docker)
- [在使用自訂映像的 Linux 上建立函式](https://docs.microsoft.com/azure/azure-functions/functions-create-function-linux-custom-image)
- [具有 Kubernetes 事件驅動自動調整的 Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-kubernetes-keda)
- [未進行的版本](https://martinfowler.com/bliki/CanaryRelease.html)
- [使用 VS Code 的 Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [使用 Visual Studio 的 Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)
- [AKS 多個節點集區](https://docs.microsoft.com/azure/aks/use-multiple-node-pools)
- [AKS Cluster 自動調整程式](https://docs.microsoft.com/azure/aks/cluster-autoscaler)
- [教學課程：在 AKS 中調整應用程式](https://docs.microsoft.com/azure/aks/tutorial-kubernetes-scale)
- [Azure Functions 的規模調整和主控](https://docs.microsoft.com/azure/azure-functions/functions-scale)
- [Azure 容器實例檔](https://docs.microsoft.com/azure/container-instances/)
- [從 ACR 部署容器實例](https://docs.microsoft.com/azure/container-instances/container-instances-using-azure-container-registry#deploy-with-azure-portal)

>[!div class="step-by-step"]
>[上一頁](scale-containers-serverless.md)
>[下一頁](communication-patterns.md)
