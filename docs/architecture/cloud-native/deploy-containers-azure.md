---
title: 在 Azure 中部署容器
description: 使用 Azure Container Registry、Azure Kubernetes Service 和 Azure Dev Spaces 在 Azure 中部署容器。
ms.date: 04/13/2020
ms.openlocfilehash: 57a4739d39b8ad022d699d54255f56f16d305440
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895608"
---
# <a name="deploying-containers-in-azure"></a>在 Azure 中部署容器

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

我們已討論過本章和第1章中的容器。 我們已瞭解容器為雲端原生應用程式提供許多優點，包括可攜性。 在 Azure 雲端中，您可以在預備和生產環境中部署相同的容器化服務。 Azure 提供數個選項來裝載這些容器化的工作負載：

- Azure Kubernetes Services (AKS)
- Azure 容器執行個體 (ACI)
- 適用于容器的 Azure Web Apps

## <a name="azure-container-registry"></a>Azure Container Registry

容器化微服務時，您會先建立「映射」組建容器。 影像是服務程式代碼、相依性和執行時間的二進位標記法。 雖然您可以使用 Docker API 中的`Docker Build`命令手動建立映射，但更好的方法是將它建立為自動化組建流程的一部分。

建立之後，容器映射會儲存在容器登錄中。 它們可讓您建立、儲存和管理容器映射。 有許多登錄可供使用，兩者都是公用和私用。 Azure Container Registry （ACR）是 Azure 雲端中完全受控的 Container Registry 服務。 它會將您的映射保存在 Azure 網路中，縮短將其部署至 Azure 容器主機的時間。 您也可以使用其他 Azure 資源所使用的相同安全性和身分識別程式來保護它們。

您可以使用[Azure 入口網站](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal)、 [Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)或[PowerShell 工具](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell)來建立 Azure Container Registry。 在 Azure 中建立登錄非常簡單。 它需要 Azure 訂用帳戶、資源群組和唯一的名稱。 圖3-11 顯示用來建立登錄的基本選項，其將裝載于`registryname.azurecr.io`。

![建立容器登錄](./media/create-container-registry.png)

**圖 3-11**。 建立容器登錄

建立登錄之後，您必須先向它進行驗證，才能使用它。 一般來說，您會使用 Azure CLI 命令登入登錄：

```azurecli
az acr login --name *registryname*
```

驗證之後，您可以使用 docker 命令將容器映射推送至該檔案。 不過，您必須先使用 ACR 登入伺服器的完整名稱（URL）來標記映射，才能執行此動作。 它的格式會是*于: registryname*. azurecr.io。

```console
docker tag mycontainer myregistry.azurecr.io/mycontainer:v1
```

標記影像之後，您可以使用`docker push`命令將映射推送至您的 ACR 實例。

```console
docker push myregistry.azurecr.io/mycontainer:v1
```

將映射推送至登錄之後，使用下列命令從本機 Docker 環境中移除映射是個不錯的主意：

```console
docker rmi myregistry.azurecr.io/mycontainer:v1
```

最佳做法是，開發人員不應將映射手動推送至容器登錄。 相反地，在 GitHub 或 Azure DevOps 這類工具中定義的組建管線，應負責處理此程式。 在[雲端原生 DevOps 一章](devops.md)中深入瞭解。

## <a name="acr-tasks"></a>ACR 工作

[ACR 工作](https://docs.microsoft.com/azure/container-registry/container-registry-tasks-overview)是可從 Azure Container Registry 取得的一組功能。 它會在 Azure 雲端中建立和管理容器映射，以擴充您的[內部迴圈開發週期](https://docs.microsoft.com/dotnet/architecture/containerized-lifecycle/design-develop-containerized-apps/docker-apps-inner-loop-workflow)。 它們不會在`docker build`您`docker push`的開發電腦上叫用和本機，而是由雲端中的 ACR 工作自動處理。

下列 AZ CLI 命令會建立容器映射，並將其推送至 ACR：

```azurecli
# create a container registry
az acr create --resource-group myResourceGroup --name myContainerRegistry008 --sku Basic

# build container image in ACR and push it into your container regsitry
az acr build --image sample/hello-world:v1  --registry myContainerRegistry008 --file Dockerfile .
```

您可以從先前的命令區塊看到，不需要在您的開發電腦上安裝 Docker Desktop。 此外，您可以設定 ACR 工作觸發程式，以在原始程式碼和基底映射更新上重建容器映射。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

我們在本章中討論了 Azure Kubernetes Service （AKS）。 我們已瞭解，它是管理容器化雲端原生應用程式的容器協調器。

將映射部署至登錄（例如 ACR）之後，您可以將 AKS 設定為自動提取並部署它。 備妥 CI/CD 管線之後，您可能會設定未完成的[發行](https://martinfowler.com/bliki/CanaryRelease.html)策略，以將快速部署更新時所牽涉到的風險降到最低。 新版本的應用程式一開始會在生產環境中設定，而不會路由傳送流量。 然後，系統會將少量的使用者路由傳送至新部署的版本。 隨著小組在新版本中獲得信心，它可以推出更多實例並淘汰舊的。 AKS 輕鬆支援這種部署樣式。

如同 Azure 中的大部分資源，您可以使用入口網站、命令列或自動化工具（例如 Helm 或 Terraform）來建立 Azure Kubernetes Service 叢集。 若要開始使用新的叢集，您必須提供下列資訊：

- Azure 訂用帳戶
- 資源群組
- Kubernetes 叢集名稱
- 區域
- Kubernetes 版本
- DNS 名稱前置詞
- 節點大小
- 節點計數

這種資訊就足以開始使用。 在 Azure 入口網站的建立過程中，您也可以為叢集的下列功能設定選項：

- 調整
- 驗證
- 網路功能
- 監視
- Tags

本[快速入門會逐步引導您使用 Azure 入口網站來部署 AKS](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)叢集。

## <a name="azure-dev-spaces"></a>Azure 開發人員空間

雲端原生應用程式可能很快就會變得很大，而且需要大量計算資源才能執行。 在這些情況下，整個應用程式無法裝載于開發電腦（特別是膝上型電腦）上。 Azure Dev Spaces 的設計目的是要使用 AKS 來解決此問題。 它可讓開發人員使用其服務的本機版本，同時在 AKS 開發叢集中裝載應用程式的其餘部分。

開發人員會在包含整個容器化應用程式的 AKS 叢集中共用執行中（開發）實例。 但他們會在其電腦上使用個人空間設定，以在本機開發其服務。 準備好時，他們會在 AKS 叢集中從端對端測試，而不會複寫相依性。 Azure Dev Spaces 會將本機電腦的程式碼與 AKS 中的服務合併。 開發人員可以使用 Visual Studio 或 Visual Studio Code，直接在 Kubernetes 中快速反復查看和偵錯工具代碼。

若要瞭解 Azure Dev Spaces 的值，請在 Microsoft Azure，讓我在容器的領導處 Gabe Monroy 分享此報價：

> 「想像一下，您是一名新員工，嘗試修正包含數十個元件的複雜微服務應用程式中的 bug，每一個都有自己的設定和支援服務。 若要開始使用，您必須設定本機開發環境，讓它可以模擬生產，包括設定您的 IDE、建立工具鏈、容器化服務相依性、本機 Kubernetes 環境、支援服務的模擬等等。 只要設定您的開發環境，修正該第一個錯誤可能需要數天的時間。
> 或者，您可以使用 Dev Spaces 和 AKS。」

處理 Azure Dev Spaces 的套裝程式含下列步驟：

1. 建立開發人員空間。
2. 設定根開發人員空間。
3. 設定子開發人員空間（適用于您自己的系統版本）。
4. 連接到開發人員空間。

所有這些步驟都可以使用 Azure CLI 和新`azds`的命令列工具來執行。 例如，若要為指定的 Kubernetes 叢集建立新的 Azure 開發人員空間，您可以使用如下所示的命令：

```azurecli
az aks use-dev-spaces -g my-aks-resource-group -n MyAKSCluster
```

接下來，您可以使用`azds prep`命令來產生必要的 Docker 和 Helm 圖表資產，以執行應用程式。 然後，您可以使用`azds up`在 AKS 中執行程式碼。 第一次執行此命令時，將會安裝 Helm 圖表。 系統會根據您的指示來建立和部署容器。 這項工作可能會在第一次執行時需要幾分鐘的時間。 不過，在您進行變更之後，您可以使用`azds space select`連接到您自己的子開發人員空間，然後在隔離的子開發人員空間中部署和偵錯工具。 開發人員空間啟動並執行之後，您可以藉由重新發出`azds up`命令將更新傳送給它，或者您可以在 Visual Studio 或 Visual Studio Code 中使用內建工具。 使用 VS Code，您可以使用命令選擇區來連接到您的開發人員空間。 圖3-12 顯示如何使用 Visual Studio 中的 Azure Dev Spaces 啟動 web 應用程式。

![連接到 Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**圖 3-12**中的 Azure Dev Spaces。 連接到 Visual Studio 中的 Azure Dev Spaces

>[!div class="step-by-step"]
>[上一頁](combine-containers-serverless-approaches.md)
>[下一頁](scale-containers-serverless.md)
