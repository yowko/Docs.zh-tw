---
title: 在 Azure 中部署容器
description: 使用 Azure Container Registry、Azure Kubernetes Service 和 Azure Dev Spaces 在 Azure 中部署容器。
ms.date: 04/13/2020
ms.openlocfilehash: d848a146a2bdb5d8d02543f57f19d6a39c9699e6
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160771"
---
# <a name="deploying-containers-in-azure"></a>在 Azure 中部署容器

我們已討論過本章和第1章中的容器。 我們已瞭解容器可為雲端原生應用程式提供許多優點，包括可攜性。 在 Azure 雲端中，您可以在預備和生產環境中部署相同的容器化服務。 Azure 提供數個選項來裝載這些容器化工作負載：

- Azure Kubernetes Services (AKS)
- Azure 容器執行個體 (ACI)
- 適用于容器的 Azure Web Apps

## <a name="azure-container-registry"></a>Azure Container Registry

容器化微服務時，您會先建立一個「映射」組建容器。 映射是服務程式代碼、相依性和執行時間的二進位標記法。 雖然您可以使用 `Docker Build` DOCKER API 中的命令手動建立映射，但更好的方法是將它建立為自動化組建程式的一部分。

建立容器映射之後，容器映射會儲存在容器登錄中。 它們可讓您建立、儲存和管理容器映射。 有許多登錄可用，包括公用和私用。 Azure Container Registry (ACR) 是 Azure 雲端中完全受控的 Container Registry 服務。 它會將您的映射保存在 Azure 網路中，縮短將其部署至 Azure 容器主機的時間。 您也可以使用其他 Azure 資源所用的相同安全性和身分識別程式來保護它們。

您可以使用 [Azure 入口網站](/azure/container-registry/container-registry-get-started-portal)、 [Azure CLI](/azure/container-registry/container-registry-get-started-azure-cli)或 [PowerShell 工具](/azure/container-registry/container-registry-get-started-powershell)來建立 Azure Container Registry。 在 Azure 中建立登錄很簡單。 它需要 Azure 訂用帳戶、資源群組和唯一的名稱。 [圖 3-11] 顯示用來建立登錄的基本選項，此登錄將裝載于 `registryname.azurecr.io` 。

![建立容器登錄](./media/create-container-registry.png)

**圖 3-11**。 建立容器登錄

建立登錄之後，您必須先使用它進行驗證，才能使用它。 一般來說，您會使用 Azure CLI 命令登入登錄：

```azurecli
az acr login --name *registryname*
```

經過驗證之後，您就可以使用 docker 命令將容器映射推送到它。 不過，您必須先使用 ACR 登入伺服器的完整名稱 (URL) 來標記映射，才能這樣做。 它的格式會是 *registryname*. azurecr.io。

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

標記映射之後，您可以使用 `docker push` 命令將映射推送至 ACR 實例。

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

將映射推送至登錄之後，最好使用下列命令從本機 Docker 環境中移除映射：

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

最佳做法是，開發人員不應手動將映射推送至容器登錄。 相反地，在 GitHub 或 Azure DevOps 這類工具中定義的組建管線應該負責此程式。 若要深入瞭解，請在 [雲端原生 DevOps 章節](devops.md)。

## <a name="acr-tasks"></a>ACR 工作

[ACR 工作](/azure/container-registry/container-registry-tasks-overview) 是可從 Azure Container Registry 取得的一組功能。 它會藉由在 Azure 雲端中建立及管理容器映射，來擴充您的 [內部迴圈開發週期](../containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow.md) 。 `docker build` `docker push` 它們不會在您的開發電腦上叫用和本機，而是由雲端中的 ACR 工作自動處理。

下列 AZ CLI 命令會建立容器映射，並將其推送至 ACR：

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

您可以從先前的命令區塊中看到，不需要在您的開發電腦上安裝 Docker Desktop。 此外，您可以設定 ACR 工作觸發程式，以重建原始程式碼和基底映射更新上的容器映射。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

我們在本章 Azure Kubernetes Service (AKS) 的長度討論。 我們已瞭解，它是管理容器化雲端原生應用程式的容器協調器。

將映射部署至登錄（例如 ACR）後，您可以將 AKS 設定為自動提取和部署。 備妥 CI/CD 管線後，您可能會設定未放置的  [發行](https://martinfowler.com/bliki/CanaryRelease.html) 策略，將快速部署更新時所牽涉到的風險降至最低。 新版本的應用程式一開始會在生產環境中設定，且不會路由傳送流量。 然後，系統會將少量的使用者路由傳送至新部署的版本。 當小組在新版本中獲得信心時，可能會推出更多實例並淘汰舊的版本。 AKS 可輕鬆支援這種部署樣式。

如同 Azure 中的大部分資源，您可以使用入口網站、命令列或自動化工具（例如 Helm 或 Terraform）來建立 Azure Kubernetes Service 叢集。 若要開始使用新的叢集，您必須提供下列資訊：

- Azure 訂用帳戶
- 資源群組
- Kubernetes 叢集名稱
- 區域
- Kubernetes 版本
- DNS 名稱前置詞
- 節點大小
- 節點計數

這項資訊就足以開始著手。 在 Azure 入口網站的建立程式過程中，您也可以設定叢集的下列功能選項：

- 調整
- 驗證
- 網路
- 監視
- 標籤

本快速入門會逐步解說如何 [使用 Azure 入口網站部署 AKS](/azure/aks/kubernetes-walkthrough-portal)叢集。

## <a name="azure-dev-spaces"></a>Azure 開發人員空間

雲端原生應用程式可能會快速成長，需要大量的計算資源才能執行。 在這些案例中，整個應用程式無法裝載于開發電腦上， (特別是膝上型電腦) 。 Azure Dev Spaces 的設計目的是要使用 AKS 來解決此問題。 它可讓開發人員使用其服務的本機版本，而將其餘的應用程式裝載在 AKS 開發叢集中。

開發人員會在包含整個容器化應用程式的 AKS 叢集中，共用正在執行的 (開發) 實例。 但它們會在電腦上使用個人空間設定，以在本機開發服務。 當您準備好時，它們會在 AKS 叢集中的端對端進行測試，而不會複寫相依性。 Azure Dev Spaces 將來自本機電腦的程式碼與 AKS 中的服務合併。 開發人員可以使用 Visual Studio 或 Visual Studio Code，直接在 Kubernetes 中快速地逐一查看和偵測程式碼。

若要瞭解 Azure Dev Spaces 的值，請讓我分享此報價，從 Gabe Monroy，Microsoft Azure 容器的領導負責人：

> 「假設您是新的員工，試圖修正包含數十個元件的複雜微服務應用程式中的 bug，每個元件都有自己的設定和支援服務。 若要開始使用，您必須設定您的本機開發環境，讓它可以模仿生產環境，包括設定您的 IDE、建立工具鏈、容器化服務相依性、本機 Kubernetes 環境、支援服務的模擬等等。 在設定開發環境所需的所有時間內，修正第一個 bug 可能需要幾天的時間。
> 或者，您可以使用 Dev Spaces 和 AKS。」

處理 Azure Dev Spaces 的套裝程式含下列步驟：

1. 建立開發人員空間。
2. 設定根開發空間。
3. 設定您自己的系統) 版本的子開發空間 (。
4. 連接至開發人員空間。

所有這些步驟都可以使用 Azure CLI 和新的  `azds` 命令列工具來執行。 例如，若要為指定的 Kubernetes 叢集建立新的 Azure 開發人員空間，您可以使用如下的命令：

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

接下來，您可以使用 `azds prep` 命令來產生必要的 Docker 和 Helm 圖表資產，以執行應用程式。 然後，您可以使用在 AKS 中執行程式碼 `azds up` 。 當您第一次執行此命令時，將會安裝 Helm 圖表。 系統會根據您的指示來建立和部署容器。 這項工作可能會在第一次執行時需要幾分鐘的時間。 不過，在您進行變更之後，您可以使用來連接到您自己的子開發空間， `azds space select` 然後在隔離的子開發空間中部署和偵測更新。 當您的開發人員空間啟動並執行之後，您就可以重新發出命令以傳送更新給它， `azds up` 也可以在 Visual Studio 或 Visual Studio Code 中使用內建工具。 使用 VS Code 時，您可以使用命令選擇區連接到您的開發人員空間。 圖3-12 顯示如何使用 Visual Studio 中的 Azure Dev Spaces 來啟動 web 應用程式。

![連接到 Visual Studio ](./media/azure-dev-spaces-visual-studio-launchsettings.png)
 **圖 3-12**中的 Azure Dev Spaces。 連接至 Visual Studio 中的 Azure Dev Spaces

>[!div class="step-by-step"]
>[上一個](combine-containers-serverless-approaches.md) 
>[下一步](scale-containers-serverless.md)
