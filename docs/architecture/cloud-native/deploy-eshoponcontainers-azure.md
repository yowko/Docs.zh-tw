---
title: 將 eShopOnContainers 部署至 Azure
description: 使用 Azure Kubernetes Service、Helm 和 DevSpaces 部署 eShopOnContainers 應用程式。
ms.date: 04/20/2020
ms.openlocfilehash: a3eacedac946cb25cf3cced305d7921e29f0d204
ms.sourcegitcommit: 957c49696eaf048c284ef8f9f8ffeb562357ad95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/07/2020
ms.locfileid: "82895588"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>將 eShopOnContainers 部署至 Azure

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

EShopOnContainers 應用程式可以部署至各種不同的 Azure 平臺。 建議的方法是將應用程式部署至 Azure Kubernetes Services （AKS）。 Helm 是一種 Kubernetes 的部署工具，可用來降低部署複雜度。 開發人員可以選擇性地執行 Azure Dev Spaces Kubernetes，以簡化其開發流程。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

若要在 AKS 中裝載 eShop，第一個步驟是建立 AKS 叢集。 若要這麼做，您可以使用 Azure 入口網站，這會引導您完成必要的步驟。 您也可以從 Azure CLI 建立叢集，並負責啟用角色型存取控制（RBAC）和應用程式路由。 EShopOnContainers 的檔詳細說明建立您自己的 AKS 叢集的步驟。 建立之後，您就可以從 Kubernetes 儀表板存取和管理叢集。

您現在可以利用 Helm 和 Tiller，將 eShop 應用程式部署到叢集。

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>使用 Helm 部署到 Azure Kubernetes Service

Helm 是直接與 Kubernetes 搭配運作的應用程式套件管理員工具。 它可協助您定義、安裝及升級 Kubernetes 應用程式。 雖然可以使用自訂的 CLI 腳本或簡單的部署檔案來部署簡單的應用程式 AKS，但複雜的應用程式可以包含許多 Kubernetes 物件，並受益于 Helm。

應用程式會使用 Helm，包括以文字為基礎的設定檔，稱為 Helm 圖表，以宣告方式描述 Helm 套件中的應用程式和設定。 圖表使用標準 YAML 格式的檔案來描述一組相關的 Kubernetes 資源。 它們會與它們所描述的應用程式代碼一起建立版本。 Helm 圖表的範圍從簡單到複雜，視其所描述的安裝需求而定。

Helm 是由命令列用戶端工具所組成，它會取用 Helm 圖表，並對名為 Tiller 的伺服器元件啟動命令。 Tiller 會與 Kubernetes API 通訊，以確保容器化工作負載的正確布建。 Helm 是由雲端原生計算基礎所維護。

下列 yaml 檔提供 Helm 範本：

```yaml
apiVersion: v1
kind: Service
metadata:
  name: {{ .Values.app.svc.marketing }}
  labels:
    app: {{ template "marketing-api.name" . }}
    chart: {{ template "marketing-api.chart" . }}
    release: {{ .Release.Name }}
    heritage: {{ .Release.Service }}
spec:
  type: {{ .Values.service.type }}
  ports:
    - port: {{ .Values.service.port }}
      targetPort: http
      protocol: TCP
      name: http
  selector:
    app: {{ template "marketing-api.name" . }}
    release: {{ .Release.Name }}
```

請注意範本如何描述一組動態的索引鍵/值配對。 叫用範本時，括在大括弧中的值會從其他以 yaml 為基礎的設定檔提取。

您會在/k8s/helm 資料夾中找到 eShopOnContainers helm 圖表。 圖2-6 顯示如何將應用程式的不同元件組織成 helm 用來定義和管理部署的資料夾結構。

![eShopOnContainers 架構](./media/eshoponcontainers-helm-folder.png)
**圖 2-6**。 EShopOnContainers helm 資料夾。

每個個別元件都是使用`helm install`命令來安裝。 eShop 包含「部署所有」腳本，它會迴圈執行並使用其各自的 helm 圖表來安裝元件。 結果是可重複的程式，在原始檔控制中使用應用程式進行版本設定，而小組中的任何人都可以使用單行指令碼命令，部署到 AKS 叢集。

> 請注意，Helm 的第3版已正式移除 Tiller 伺服器元件的需求。 如需這項增強功能的詳細資訊，請參閱[這裡](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714)。

## <a name="azure-dev-spaces"></a>Azure 開發人員空間

雲端原生應用程式可能很快就會變得很大，而且需要大量計算資源才能執行。 在這些情況下，整個應用程式無法裝載于開發電腦（特別是膝上型電腦）上。 Azure Dev Spaces 的設計目的是要使用 AKS 來解決此問題。 它可讓開發人員使用其服務的本機版本，同時在 AKS 開發叢集中裝載應用程式的其餘部分。

開發人員會在包含整個容器化應用程式的 AKS 叢集中共用執行中（開發）實例。 但他們會在其電腦上使用個人空間設定，以在本機開發其服務。 準備好時，他們會在 AKS 叢集中從端對端測試，而不會複寫相依性。 Azure Dev Spaces 會將本機電腦的程式碼與 AKS 中的服務合併。 小組成員可以查看他們的變更在實際 AKS 環境中的行為。 開發人員可以使用 Visual Studio 2017 或 Visual Studio Code，直接在 Kubernetes 中快速反復查看和偵錯工具代碼。

在圖2-7 中，您可以看到開發人員 Susie 已將更新版的自行車微服務部署到其開發人員空間。 然後她就能夠使用自訂 URL （以她的空間名稱（susie.s.dev.myapp.eus.azds.io）開頭）來測試她的變更。

![eShopOnContainers 架構](./media/azure-devspaces-one.png)
**圖 2-7**。 開發人員 Susie 會部署自己的自行車微服務版本，並加以測試。

同時，開發人員 John 會自訂保留微服務，並需要測試其變更。 他會將自己的變更部署到自己的開發人員空間，而不會與 Susie 的變更相衝突，如圖2-8 所示。 John 接著會使用自己的 URL （前面加上他的空間名稱（john.s.dev.myapp.eus.azds.io））來測試他的變更。

![eShopOnContainers 架構](./media/azure-devspaces-two.png)
**圖 2-8**。 開發人員 John 會部署自己的保留微服務版本，並測試它，而不會與其他開發人員衝突。

使用 Azure Dev Spaces，小組可以直接處理 AKS，同時獨立變更、部署和測試其變更。 這種方法可減少個別專用託管環境的需求，因為每位開發人員實際上都有自己的 AKS 環境。 開發人員可以使用其 CLI 來處理 Azure Dev Spaces，或啟動其應用程式直接從 Visual Studio Azure Dev Spaces。 [深入瞭解 Azure Dev Spaces 的運作方式和設定。](https://docs.microsoft.com/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions 和 Logic Apps （無伺服器）

EShopOnContainers 範例包含追蹤線上行銷活動的支援。 Azure 函式可用來追蹤指定之行銷活動識別碼的行銷活動詳細資料。 單一 Azure 函式比較簡單且足夠，而不是建立完整的微服務。 Azure Functions 具有簡單的組建和部署模型，特別是當設定為在 Kubernetes 中執行時。 部署函式的功能是使用 Azure Resource Manager （ARM）範本和 Azure CLI。 此活動服務不是面向客戶，而且會叫用單一作業，使其成為 Azure Functions 的絕佳候選項目。 函數需要最少的設定，包括資料庫連接字串資料和影像基底 URI 設定。 您會在 Azure 入口網站中設定 Azure Functions。

>[!div class="step-by-step"]
>[上一頁](map-eshoponcontainers-azure-services.md)
>[下一頁](centralized-configuration.md)
