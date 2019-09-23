---
title: 將 eShopOnContainers 部署至 Azure
description: 使用 Azure Kubernetes Service、Helm 和 DevSpaces 部署 eShopOnContainers 應用程式。
ms.date: 06/30/2019
ms.openlocfilehash: 21033cc904dc595193c69f3452ce2522740f8ff6
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183270"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>將 eShopOnContainers 部署至 Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Azure 可以使用各種不同的服務支援支援 eShopOnContainers 應用程式的邏輯。 建議的方法是使用 Azure Kubernetes Service （AKS）來利用 Kubernetes。 這可以與 Helm 部署結合，以確保能輕鬆地重複基礎結構設定。 或者，開發人員可以在開發過程中，利用 Kubernetes 的 Azure Dev Spaces。 另一個選項是使用 Azure 無伺服器功能（如 Azure Functions 和 Azure Logic Apps）來裝載應用程式的功能。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

如果您想要在自己的 AKS 叢集中裝載 eShopOnContainers 應用程式，第一個步驟是建立您的叢集。 您可以使用 Azure 入口網站來完成此動作，這會引導您完成必要的步驟，或者您可以使用 Azure CLI，以確保您在執行此動作時，啟用以角色為基礎的存取控制（RBAC）和應用程式路由。 EShopOnContainers 的檔說明建立您自己的 AKS 叢集所需的步驟。 建立叢集之後，您必須啟用 Kubernetes 儀表板的存取權，此時您應該能夠流覽至 Kubernetes 儀表板來管理叢集。

建立並設定叢集之後，您就可以使用 Helm 和 Tiller 將應用程式部署至該叢集。

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>使用 Helm 部署到 Azure Kubernetes Service

AKS 的基本部署可以使用自訂 CLI 腳本或簡單的部署檔案，但更複雜的應用程式應該使用相依性管理工具，例如 Helm。 Helm 是由雲端原生運算基礎所維護，可協助您定義、安裝及升級 Kubernetes 應用程式。 Helm 是由命令列用戶端、Helm （使用 Helm 圖表）和叢集內元件 Tiller 所組成。 Helm 圖會使用標準的 YAML 格式檔案來描述一組相關的 Kubernetes 資源，而且通常會與它們所描述的應用程式一起建立版本。 Helm 圖表的範圍從簡單到複雜，視其所描述的安裝需求而定。

您會在/k8s/helm 資料夾中找到 eShopOnContainers helm 圖表。 圖2-6 顯示如何將應用程式的不同元件組織成 helm 用來定義和管理部署的資料夾結構。

![eShopOnContainers 架構](./media/eshoponcontainers-helm-folder.png)
**圖 2-6**。 EShopOnContainers helm 資料夾。

每個個別元件都是使用`helm install`命令來安裝。 這些命令很容易編寫腳本，而 eShopOnContainers 提供「部署所有」腳本，它會在不同的元件之間進行迴圈，並使用其各自的 helm 圖表進行安裝。 結果是可重複的程式，在原始檔控制中使用應用程式進行版本設定，而小組中的任何人都可以使用單行指令碼命令，部署到 AKS 叢集。 特別是當與 Azure Dev Spaces 結合時，讓開發人員能夠輕鬆地診斷及測試其微服務型雲端原生應用程式的個別變更。

## <a name="azure-dev-spaces"></a>Azure Dev Spaces

Azure Dev Spaces 可協助個別開發人員在開發期間，于 Azure 中裝載自己專屬的 AKS 叢集版本。 這可將本機電腦需求降到最低，讓小組成員能夠快速查看其變更在實際 AKS 環境中的行為。 Azure Dev Spaces 提供 CLI，讓開發人員用來管理其開發人員空間，並視需要部署到特定的子開發人員空間。 每個子開發人員空間都會使用唯一的 URL 子域來參考，允許並存部署已修改的叢集，讓個別開發人員可以避免與彼此進行中的工作互相衝突。 在圖2-7 中，您可以看到開發人員 Susie 如何將自己的自行車微服務版本部署到其開發人員空間。 然後她就能夠使用自訂 URL （以她的空間名稱（susie.s.dev.myapp.eus.azds.io）開頭）來測試她的變更。

![eShopOnContainers 架構](./media/azure-devspaces-one.png)
**圖 2-7**。 開發人員 Susie 會部署自己的自行車微服務版本，並加以測試。

同時，開發人員 John 會自訂保留微服務，並需要測試其變更。 他可以將自己的變更部署到自己的開發人員空間，而不會與 Susie 的變更相衝突，如圖2-8 所示。 他可以使用自己的 URL 來測試他的變更，其前面會加上他的空間名稱（john.s.dev.myapp.eus.azds.io）。

![eShopOnContainers 架構](./media/azure-devspaces-two.png)
**圖 2-8**。 開發人員 John 會部署自己的保留微服務版本，並測試它，而不會與其他開發人員衝突。

使用 Azure Dev Spaces，小組可以直接處理 AKS，同時獨立變更、部署和測試其變更。 這種方法可減少個別專用託管環境的需求，因為每位開發人員實際上都有自己的 AKS 環境。 開發人員可以使用其 CLI 來處理 Azure Dev Spaces，或啟動其應用程式直接從 Visual Studio Azure Dev Spaces。 [深入瞭解 Azure Dev Spaces 的運作方式和設定。](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions 和 Logic Apps （無伺服器）

EShopOnContainers 範例包含追蹤線上行銷活動的支援。 Azure 函式是用來針對指定的活動識別碼提取行銷活動詳細資料。 單一 Azure 函式端點比較簡單且足夠，而不是為此目的建立完整的 ASP.NET Core 應用程式。 Azure Functions 具有比完整 ASP.NET Core 應用程式更簡單的組建和部署模型，特別是當設定為在 Kubernetes 中執行時。 部署函式的功能是使用 Azure Resource Manager （ARM）範本和 Azure CLI。 此活動詳細資料微服務不是面向客戶，而且與線上商店的需求並不相同，因此這是 Azure Functions 的理想候選。 函式需要某些設定才能正常運作，例如資料庫連接字串資料和映射基底 URI 設定。 您會在 Azure 入口網站中設定 Azure Functions。

## <a name="references"></a>reference

- [EShopOnContainers在 AKS 中建立 Kubernetes 叢集](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Deploy-to-Azure-Kubernetes-Service-(AKS)#create-kubernetes-cluster-in-aks)
- [EShopOnContainersAzure Dev Spaces](https://github.com/dotnet-architecture/eShopOnContainers/wiki/Azure-Dev-Spaces)
- [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/about)

>[!div class="step-by-step"]
>[上一頁](map-eshoponcontainers-azure-services.md)
>[下一頁](centralized-configuration.md)
