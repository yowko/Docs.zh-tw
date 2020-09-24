---
title: 將 eShopOnContainers 部署至 Azure
description: 使用 Azure Kubernetes Service、Helm 和 Microsoft.devspaces 部署 eShopOnContainers 應用程式。
ms.date: 05/13/2020
ms.openlocfilehash: b3871dae2b414709bfe24b6f7bdbf06de1689d12
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91160719"
---
# <a name="deploying-eshoponcontainers-to-azure"></a>將 eShopOnContainers 部署至 Azure

EShopOnContainers 應用程式可以部署到各種不同的 Azure 平臺。 建議的方法是將應用程式部署到 Azure Kubernetes Services (AKS) 。 Helm 是一種 Kubernetes 的部署工具，可用來降低部署的複雜度。 （選擇性）開發人員可能會為 Kubernetes 實行 Azure Dev Spaces，以簡化開發流程。

## <a name="azure-kubernetes-service"></a>Azure Kubernetes Service

若要在 AKS 中裝載 eShop，第一個步驟是建立 AKS 叢集。 若要這樣做，您可以使用 Azure 入口網站，這會引導您完成必要的步驟。 您也可以從 Azure CLI 建立叢集，並小心啟用角色型存取控制 (RBAC) 和應用程式路由。 EShopOnContainers 的檔詳細說明建立您自己的 AKS 叢集的步驟。 建立之後，您就可以從 Kubernetes 儀表板存取和管理叢集。

您現在可以利用 Helm 和 Tiller，將 eShop 應用程式部署到叢集。

## <a name="deploying-to-azure-kubernetes-service-using-helm"></a>使用 Helm 部署到 Azure Kubernetes Service

Helm 是直接與 Kubernetes 搭配運作的應用程式套件管理員工具。 它可協助您定義、安裝及升級 Kubernetes 應用程式。 雖然您可以使用自訂的 CLI 腳本或簡單的部署檔案將簡單的應用程式部署至 AKS，但複雜的應用程式可以包含許多 Kubernetes 物件，並受益于 Helm。

使用 Helm 時，應用程式會包含以文字為基礎的設定檔，稱為 Helm 圖表，以宣告方式描述 Helm 套件中的應用程式和設定。 圖表使用標準的 YAML 格式檔案來描述一組相關的 Kubernetes 資源。 這些應用程式會與它們所描述的應用程式程式碼一起建立版本。 Helm 圖的範圍從簡單到複雜，取決於其所描述的安裝需求。

Helm 是由命令列用戶端工具所組成，它會取用 Helm 圖表並將命令啟動至名為 Tiller 的伺服器元件。 Tiller 會與 Kubernetes API 通訊，以確保正確布建您的容器化工作負載。 Helm 是由雲端原生運算基礎所維護。

下列 yaml 檔呈現 Helm 範本：

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

請注意範本如何描述一組動態的索引鍵/值組。 叫用範本時，會從其他以 yaml 為基礎的設定檔中提取以大括弧括住的值。

您會在/k8s/helm 資料夾中找到 eShopOnContainers helm 圖表。 圖2-6 顯示如何將應用程式的不同元件組織成 helm 用來定義和管理部署的資料夾結構。

![eShopOnContainers 架構 ](./media/eshoponcontainers-helm-folder.png)
 **圖 2-6**。 EShopOnContainers helm 資料夾。

每個個別元件都是使用 `helm install` 命令來安裝。 eShop 包含「全部部署」腳本，它會使用其個別的 helm 圖表進行迴圈，並安裝元件。 結果是可重複的程式，並在原始檔控制中使用應用程式進行版本設定，小組中的任何人都可以使用單行指令碼命令部署至 AKS 叢集。

> 請注意，Helm 的第3版已正式移除 Tiller 伺服器元件的需求。 您可以在 [這裡](https://medium.com/better-programming/why-is-tiller-missing-in-helm-3-2347c446714)找到這項增強功能的詳細資訊。

## <a name="azure-dev-spaces"></a>Azure 開發人員空間

雲端原生應用程式可能會快速成長，需要大量的計算資源才能執行。 在這些案例中，整個應用程式無法裝載于開發電腦上， (特別是膝上型電腦) 。 Azure Dev Spaces 的設計目的是要使用 AKS 來解決此問題。 它可讓開發人員使用其服務的本機版本，而將其餘的應用程式裝載在 AKS 開發叢集中。

開發人員會在包含整個容器化應用程式的 AKS 叢集中，共用正在執行的 (開發) 實例。 但它們會在電腦上使用個人空間設定，以在本機開發服務。 當您準備好時，它們會在 AKS 叢集中的端對端進行測試，而不會複寫相依性。 Azure Dev Spaces 將來自本機電腦的程式碼與 AKS 中的服務合併。 小組成員可以看到其變更在實際 AKS 環境中的行為。 開發人員可以使用 Visual Studio 2017 或 Visual Studio Code，直接在 Kubernetes 中快速地逐一查看和偵測程式碼。

在圖2-7 中，您可以看到開發人員 Susie 已將更新版本的自行車微服務部署至她的開發人員空間。 她接著可以使用自訂 URL （以她的空間名稱開頭 (susie.s.dev.myapp.eus.azds.io) ）來測試她的變更。

![eShopOnContainers 架構 ](./media/azure-devspaces-one.png)
 **圖 2-7**。 開發人員 Susie 會部署自己的自行車微服務版本，並進行測試。

同時，developer John 會自訂保留專案微服務，並需要測試其變更。 他將他的變更部署到自己的開發空間，而不會與 Susie 的變更相衝突，如圖2-8 所示。 John 接著會使用自己的 URL 來測試他的變更，而該 URL 前面會加上他的空間名稱 (john.s.dev.myapp.eus.azds.io) 。

![eShopOnContainers 架構 ](./media/azure-devspaces-two.png)
 **圖 2-8**。 開發人員 John 部署自己的保留微服務版本，並在不與其他開發人員衝突的情況下進行測試。

使用 Azure Dev Spaces，小組可以直接使用 AKS，同時獨立變更、部署及測試其變更。 這種方法可減少個別專用託管環境的需求，因為每位開發人員實際上都有自己的 AKS 環境。 開發人員可以使用其 CLI 來處理 Azure Dev Spaces，或啟動其應用程式，以直接從 Visual Studio Azure Dev Spaces。 [深入瞭解 Azure Dev Spaces 的運作方式和設定方式。](/azure/dev-spaces/how-dev-spaces-works)

## <a name="azure-functions-and-logic-apps-serverless"></a>Azure Functions 和 Logic Apps (無伺服器) 

EShopOnContainers 範例包含追蹤線上行銷活動的支援。 Azure 函數用來追蹤特定行銷活動識別碼的行銷活動詳細資料。 單一 Azure 函式並不會建立完整的微服務，而是更簡單且足夠的功能。 Azure Functions 具有簡單的組建和部署模型，尤其是當設定為在 Kubernetes 中執行時。 部署函式時，會使用 Azure Resource Manager (ARM) 範本和 Azure CLI 編寫腳本。 這項活動服務並不是面向客戶，而且會叫用單一作業，使其成為 Azure Functions 的絕佳候選項目。 函數需要最基本的設定，包括資料庫連接字串資料和影像基底 URI 設定。 您會在 Azure 入口網站中設定 Azure Functions。

>[!div class="step-by-step"]
>[上一個](map-eshoponcontainers-azure-services.md) 
>[下一步](centralized-configuration.md)
