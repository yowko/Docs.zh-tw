---
title: 在 Azure 中部署容器
description: 使用 Azure Container Registry、Azure Kubernetes Service 和 Azure Dev Spaces 在 Azure 中部署容器。
ms.date: 06/30/2019
ms.openlocfilehash: 6d95db26b6a45dd6825c88693308ffe90d1ed071
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183263"
---
# <a name="deploying-containers-in-azure"></a>在 Azure 中部署容器

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

容器提供許多優點，其中一個是可攜性。 您可以輕鬆地採用您已在本機開發和測試的相同容器，並將其部署至 Azure，以便在預備和生產環境中執行您的應用程式。 Azure 提供許多適用于容器型應用程式裝載的選項，同樣支援數種不同的部署方法。 最常見且最有彈性的方法，就是將您的容器部署至 Azure Container Registry （ACR），而您想要使用這些服務來裝載它們。 Azure 用於容器的 Web App、Azure Kubernetes Services （AKS）和 Azure 容器實例（ACI）都可以存取已推送至 ACR 的容器映射。

## <a name="azure-container-registry"></a>Azure Container Registry

Azure Container Registry （ACR）可讓您建立、儲存和管理所有容器部署的映射。 還有其他容器登錄，也就是公用和私用，您可以在其中部署容器。 ACR 透過其他選項的優點是，您可以讓影像靠近生產環境，以改善組建和部署時間。 您也可以使用您用於其他 Azure 資源的相同安全性程式來保護它們，以提高安全性並降低資產管理工作。

您可以[使用 Azure 入口網站](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-portal)或[使用 Azure CLI](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-azure-cli)或[PowerShell 工具](https://docs.microsoft.com/azure/container-registry/container-registry-get-started-powershell)來建立容器登錄。 建立新的 container registry 只需要 Azure 訂用帳戶、資源群組和唯一名稱。 圖3-11 顯示建立登錄的基本選項，其將裝載于*于: registryname*. azurecr.io。

![建立 container registry](./media/create-container-registry.png)
**圖 3-11**。 建立容器登錄

建立登錄之後，您必須先向它進行驗證，才能使用它。 一般來說，您會使用 Azure CLI 命令登入登錄：

```azurecli
az acr login --name *registryname*
```

在 Azure Container Registry 中建立登錄之後，您就可以使用 docker 命令將容器映射推送到它。 不過，在這樣做之前，您必須先使用 ACR 登入伺服器的完整名稱（URL）來標記映射。 這會使用*于: registryname*. azurecr.io 格式。

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

開發人員不應該直接從他們的電腦推送至容器登錄。 相反地，在這 Azure DevOps 類工具中定義的組建管線應該負責此程式。 在[雲端原生 DevOps 一章](devops.md)中深入瞭解。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

如果您以容器為基礎的應用程式牽涉到多個容器，您很可能會想要使用 Kubernetes 之類的*協調*器來定義和管理容器之間的互動。 將容器映射部署至 ACR 之後，您就可以輕鬆地設定 Azure Kubernetes Services，從 ACR 自動部署更新的映射。 備妥完整的 CI/CD 管線之後，您可以設定未完成的[發行](https://martinfowler.com/bliki/CanaryRelease.html)策略，以將快速部署更新時所牽涉到的風險降到最低。 新版本的應用程式一開始會在生產環境中設定，而不會路由傳送流量，然後少數的使用者會路由傳送至新部署的應用程式版本。 當小組在新版本的軟體中獲得信心時，新版本的更多實例會被推出，而舊版的實例也會淘汰。 AKS 輕鬆支援這種部署樣式。

如同 Azure 中的大部分資源，您可以使用入口網站建立 Azure Kubernetes 叢集，或使用命令列工具或基礎結構自動化工具（例如 Helm 或 Terraform）。 若要開始使用新的叢集，您必須提供下列資訊：

- Azure 訂用帳戶
- 資源群組
- Kubernetes 叢集名稱
- 區域
- Kubernetes 版本
- DNS 名稱前置詞
- 節點大小
- 節點計數

這種資訊就足以開始使用。 在 Azure 入口網站中建立程式的過程中，您也可以設定叢集下列功能的選項：

- 縮放
- 驗證
- 網路
- 監視
- Tags

本[快速入門會逐步引導您使用 Azure 入口網站來部署 AKS](https://docs.microsoft.com/azure/aks/kubernetes-walkthrough-portal)叢集。

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

複雜的 Kubernetes 叢集可能需要大量的資源來裝載，讓開發人員難以在單一電腦（尤其是膝上型電腦）上執行整個應用程式。 Azure Dev Spaces 提供這項解決方案，可讓開發人員使用自己在 Azure 中託管的 Azure Kubernetes 叢集版本。 Azure Dev Spaces 的設計目的是要使用 AKS 輕鬆地開發微服務應用程式。

若要瞭解 Azure Dev Spaces 的值，請在 Microsoft Azure，讓我在容器的領導處 Gabe Monroy 分享此報價：

「假設您是一個新的員工，嘗試修正由數十個元件組成的複雜微服務應用程式中的 bug，每一個都有自己的設定和支援服務。 若要開始使用，您必須設定本機開發環境，讓它可以模擬生產，包括設定您的 IDE、建立工具鏈、容器化服務相依性、本機 Kubernetes 環境、支援服務的模擬等等。 只要設定您的開發環境，修正該第一個錯誤可能需要數天的時間。

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

接下來，您可以使用`azds prep`命令來產生必要的 Docker 和 Helm 圖表資產，以執行應用程式。 然後，您可以使用`azds up`在 AKS 中執行程式碼。 當您第一次執行此命令時，將會安裝 Helm 圖，並根據您的指示來建立和部署容器。 這可能會在第一次執行時需要幾分鐘的時間。 不過，在您進行變更之後，您可以使用`azds space select`連接到您自己的子開發人員空間，然後在隔離的子開發人員空間中部署和偵錯工具。 當開發人員空間啟動並執行之後，您可以藉由重新發出`azds up`命令，或使用 Visual Studio 或 Visual Studio Code 中的內建工具，將更新傳送給它。 使用 VS Code，您可以使用命令選擇區來連接到您的開發人員空間。 圖3-12 顯示如何使用 Visual Studio 中的 Azure Dev Spaces 啟動 web 應用程式。

![連接到 Visual Studio](./media/azure-dev-spaces-visual-studio-launchsettings.png)
**圖 3-12**中的 Azure Dev Spaces。 連接到 Visual Studio 中的 Azure Dev Spaces

## <a name="references"></a>reference

- [未進行的版本](https://martinfowler.com/bliki/CanaryRelease.html)
- [使用 VS Code 的 Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore)
- [使用 Visual Studio 的 Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/quickstart-netcore-visualstudio)

>[!div class="step-by-step"]
>[上一頁](combine-containers-serverless-approaches.md)
>[下一頁](scale-containers-serverless.md)
