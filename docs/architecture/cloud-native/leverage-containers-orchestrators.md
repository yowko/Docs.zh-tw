---
title: 利用容器和協調器
description: 使用 Azure 中的 Docker 容器和庫伯內特協調器
ms.date: 06/30/2019
ms.openlocfilehash: 44b2fff8c9c88717d83e41a421b9817e2cc68135
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989034"
---
# <a name="leveraging-containers-and-orchestrators"></a>利用容器和協調器

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

容器和協調器旨在解決單一部署方法中常見的問題。

## <a name="challenges-with-monolithic-deployments"></a>整體部署的挑戰

傳統上,大多數應用程式都部署為單個單元。 此類應用程式稱為單體。 這種將應用程式部署為單個單元的一般方法,即使它們由多個模組或程式集組成,也稱為單片架構,如圖 3-1 所示。

![單體架構。](./media/monolithic-architecture.png)

**圖3-1**。 單體架構。

儘管單片式架構具有簡單性的優點,但它們面臨著許多挑戰:

### <a name="deployments"></a>部署

部署到單一應用程式通常需要重新啟動整個應用程式,即使只替換一個小型模組也是如此。 根據託管應用程式的計算機數,這可能導致部署期間的停機時間。

### <a name="hosting"></a>裝載

單片應用程式完全託管在單個計算機實例上。 這可能需要比分布式應用程式中任何模組所需的更高功能的硬體。 此外,如果應用的任何部分成為瓶頸,則必須將整個應用程式部署到其他計算機節點才能橫向擴展。

### <a name="environment"></a>環境

單片應用程式通常部署到現有的託管環境(作業系統、已安裝的框架等)。 此環境可能與開發或測試應用程式的環境不匹配。 應用程序環境中的不一致是單一部署的常見問題來源。

### <a name="coupling"></a>耦合

單片應用程式在應用程式的不同部分之間以及應用程式與其環境之間可能有很大的耦合。 這會使以後難以分解特定服務或問題,以便增加其可伸縮性或在替代實現中交換。 這種耦合還會導致對系統更改產生更大的潛在影響,需要在較大的應用中進行廣泛的測試。

### <a name="technology-choice"></a>技術選擇

單片應用程序作為一個單元構建和部署。 這提供了簡單性和統一性,但可能是創新的障礙。 儘管系統中的新功能或模組可能更適合更現代的平臺或框架,但為了一致性以及易於開發和部署,可能會使用應用程式的當前方法構建它。

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>容器和協調器有什麼好處?

Docker 是最受歡迎的容器管理和映射平台,允許您快速處理 Linux 和 Windows 上的容器。 容器提供單獨但可重現的應用程式環境,這些環境在任何系統上以相同的方式運行。 這使得它們非常適合在雲原生應用程式中開發和託管應用程式和應用程式元件。 容器彼此隔離,因此同一主機硬體上的兩個容器可以安裝不同版本的軟體,甚至操作系統,而不會造成依賴項衝突。

此外,容器由可簽入原始程式碼管理的簡單檔定義。 與完整伺服器(甚至虛擬機器)不同,通常需要手動工作才能應用更新或安裝其他服務,因此容器基礎結構很容易被版本控制。 因此,在容器中運行構建的應用可以使用自動工具作為生成管道的一部分進行開發、測試和部署。

容器是不可改變的。 獲得容器的定義後,可以重新創建該容器,並且它將以完全相同的方式運行。 這種不變性適用於基於元件的設計。 如果應用程式的某些部分更改頻率不如其他部分頻繁,那麼為什麼當您只需部署更改次數最多的部分時,才能重新部署整個應用程式? 應用的不同功能和交叉問題可以分解為單獨的單元。 圖 3-2 顯示了單片應用如何通過委派某些功能或功能來利用容器和微服務。 應用本身的剩餘功能也已容器化。

![分解單片應用,在後端使用微服務。](./media/breaking-up-monolith-with-backend-microservices.png)
**圖3-2**. 分解單片應用,在後端使用微服務。

使用單獨的容器構建的雲原生應用可根據需要部署盡可能多的或很少的應用程式。 單個服務可以託管在具有適合每個服務的節點上。 每個服務運行的環境是不可變的,可以在開發、測試和生產之間共用,並且可以輕鬆進行版本控制。 應用程式不同區域之間的耦合作為服務之間的調用或消息顯式發生,而不是單體中的編譯時間依賴項。 整個應用的任何給定部分都可以選擇對該功能或功能最有意義的技術,而無需更改應用的其餘部分。

## <a name="what-are-the-scaling-benefits"></a>擴展優勢是什麼?

構建在容器上的服務可以利用庫伯奈斯等業務流程工具提供的擴展優勢。 根據設計,容器只知道自己。 一旦開始有多個容器需要協同工作,就可以在更高的級別組織它們。 組織大量容器及其共享依賴項(如網路配置)是業務流程工具用於節省一天的位置! Kubernetes 是一個容器編排平臺,旨在自動部署、擴展和管理容器化應用程式。 在容器群組之上建立抽象層,並將它們組織到*窗格中*。 在稱為*節點*的工作電腦上運行的 Pod。 整個有組織的群組稱為*群組*。 圖 3-3 顯示了庫伯內斯群集的不同元件。

![庫伯內斯集群組。](./media/kubernetes-cluster-components.png)
**圖3-3**. 庫伯內斯集群組。

Kubernetes 內置支援擴展群集以滿足需求。 結合容器化微服務,這為雲原生應用程式提供了在需要時和任何地方使用額外資源快速高效地回應需求高峰的能力。

### <a name="declarative-versus-imperative"></a>宣告性與命令性

庫伯內斯支援聲明性物件和命令性物件配置。 命令性方法涉及運行各種命令,告訴 Kubernetes 如何執行每一步。 *運行*此映射。 *刪除*此窗格。 *公開*此埠。 使用聲明性方法,您可以使用一個配置檔來描述*您想要做什麼*而不是*做什麼*,Kubernetes 會找出要做什麼來實現所需的結束狀態。 如果已經使用指令命令設定群集,則可以使用 匯出宣告性`kubectl get svc SERVICENAME -o yaml > service.yaml`清單 。 這會產生以下的清單檔:

```yaml
apiVersion: v1
kind: Service
metadata:
  creationTimestamp: "2019-09-13T13:58:47Z"
  labels:
    component: apiserver
    provider: kubernetes
  name: kubernetes
  namespace: default
  resourceVersion: "153"
  selfLink: /api/v1/namespaces/default/services/kubernetes
  uid: 9b1fac62-d62e-11e9-8968-00155d38010d
spec:
  clusterIP: 10.96.0.1
  ports:
  - name: https
    port: 443
    protocol: TCP
    targetPort: 6443
  sessionAffinity: None
  type: ClusterIP
status:
  loadBalancer: {}
```

使用聲明性配置時,可以通過對配置檔所在的資料夾進行`kubectl diff -f FOLDERNAME`引用 之前預覽這些更改。 確定要套用變更後,`kubectl apply -f FOLDERNAME`請執行 。 添加到`-R`遞歸處理資料夾層次結構。

除了服務之外,還可以對其他 Kubernetes 功能(如*部署*)使用聲明性配置。 聲明性部署由部署控制器用於更新群集資源。 部署用於添加新更改、向上擴展以支援更多負載或回滾到以前的修訂版。 如果群集不穩定,聲明性部署提供了自動將群集恢復到所需狀態的機制。

使用聲明性配置可以將基礎結構表示為代碼,該代碼可以簽入並隨著應用程式代碼進行版本控制。 這提供了改進的更改控制,並更好地支援使用與原始程式碼管理更改關聯的生成和部署管道進行持續部署。

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>哪些方案非常適合容器和協調器?

以下方案非常適合使用容器和協調器。

### <a name="applications-requiring-high-uptime-and-scalability"></a>需要高停機時間和可擴充性的應用程式

具有高高高高高高高擴展性和可擴充性要求的各個應用程式是使用微服務、容器和協調器的雲原生體系結構的理想選擇。 這些應用程式可以使用版本化環境在容器中開發,可以在生產前進行廣泛測試,並且可以以零停機時間部署到生產中。 使用 Kubernetes 群集可確保此類應用還可以按需擴展,並從節點故障中自動恢復。

### <a name="large-numbers-of-applications"></a>大量應用

部署並隨後必須維護大量應用程式的組織受益於容器和協調器。 設置容器化環境和 Kubernetes 群集的前期工作主要是固定成本。 部署、維護和更新單個應用程式的成本隨必須維護的應用程序數量而異。 除了數量相當少的應用程式之外,手動維護自定義應用程式的複雜性超過了使用容器和協調器實現解決方案的成本。

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>何時應避免使用容器和協調器?

如果您不願意或無法按照十二因子應用原則構建應用程式,則最好避免容器和協調器。 在這些情況下,最好使用基於 VM 的託管平臺,或者可能採用一些混合系統,您可以在其中將某些功能引入單獨的容器甚至無伺服器功能。

## <a name="development-resources"></a>開發資源

本節顯示一個開發資源的簡短清單,這些資源可説明您開始為下一個應用程式使用容器和協調器。 如果您要尋找有關如何設計雲原生微服務體系結構應用的指導,請閱讀本書的配套書[.NET 微服務:容器化 .NET 應用程式的體系結構](https://aka.ms/microservicesebook)。

### <a name="local-kubernetes-development"></a>當地庫伯內斯開發

Kubernetes 部署在生產環境中提供了巨大的價值,但您也可以在本地運行它們。 儘管大部分時間都能夠獨立處理單個應用或微服務是件好事,但有時能夠像部署到生產時一樣在本地運行整個系統是件好事。 有幾種方法可以實現此目的,其中兩種方法是 Minikube 和 Docker 桌面。 Visual Studio 還為 Docker 開發提供工具。

### <a name="minikube"></a>Minikube

什麼是米尼庫貝? Minikube 專案說:「Minikube 在 macOS、Linux 和 Windows 上實現了本地 Kubernetes 群集。 其主要目標是"成為本地Kubernetes應用程式開發的最佳工具,並支援所有適合的Kubernetes功能。 安裝 Minikube 與 Docker 是分開的,但 Minikube 支援與 Docker 桌面支援不同的虛擬機器管理程式。 Minikube 目前支援以下庫伯奈斯功能:

- DNS
- 節點連接埠
- 設定對應及機密
- 儀表板
- 容器執行時:碼頭、rkt、CRI-O 和容器
- 開啟容器網路介面 (CNI)
- 輸入

安裝 Minikube 後,`minikube start`可以通過運行 命令快速開始使用它,該命令下載映射並啟動本地 Kubernetes 叢集。 群集啟動后,您將使用標準的 Kubernetes`kubectl`命令與其交互。

### <a name="docker-desktop"></a>Docker Desktop

您還可以直接從 Windows 上的 Docker 桌面使用 Kubernetes。 如果您使用的是 Windows 容器,這是您唯一的選擇,也是非 Windows 容器的絕佳選擇。 標準 Docker 桌面設定應用用於設定從 Docker 桌面執行的庫伯內特。

![Docker 桌面中設定庫伯內斯](./media/docker-desktop-kubernetes.png)

**圖3-4**。 在 Docker 桌面中配置庫伯內斯。

Docker 桌面已經是本地配置和運行容器化應用的最常見工具。 使用 Docker Desktop 時,可以針對要部署到生產的完全相同的 Docker 容器映射集在本地進行開發。 Docker 桌面旨在"在本地構建、測試和發貨"容器化應用。 將映射發送到映像註冊表(如 Azure 容器註冊表或 Docker Hub)後,Azure Kubernetes 服務 (AKS) 等服務將管理生產中的應用程式。

### <a name="visual-studio-docker-tooling"></a>視覺工作室碼頭工具

Visual Studio 支援 Web 應用程式的 Docker 開發。 建立新的ASP.NET核心應用程式時,您可以選擇使用 Docker 支援來設定該應用程式,作為專案創建過程的一部分,如圖 3-5 所示。

![視覺化工作室啟用 Docker 支援](./media/visual-studio-enable-docker-support.png)

**圖3-5**。 視覺化工作室啟用 Docker 支援

選擇此選項後,將使用 root`Dockerfile`中的專案創建專案,可用於在 Docker 容器中生成和託管應用。 如圖 3-6 所示有一個範例 Dockerfile。

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.0-stretch-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.0-stretch AS build
WORKDIR /src
COPY ["WebApplication3/WebApplication3.csproj", "WebApplication3/"]
RUN dotnet restore "WebApplication3/WebApplication3.csproj"
COPY . .
WORKDIR "/src/WebApplication3"
RUN dotnet build "WebApplication3.csproj" -c Release -o /app

FROM build AS publish
RUN dotnet publish "WebApplication3.csproj" -c Release -o /app

FROM base AS final
WORKDIR /app
COPY --from=publish /app .
ENTRYPOINT ["dotnet", "WebApplication3.dll"]
```

**圖3-6**. 視覺化工作室產生的 Dockerfile

應用執行時的預設行為也配置為使用 Docker。 圖 3-7 顯示了添加了 Docker 支援後創建的新ASP.NET核心專案中可用的不同運行選項。

![視覺化工作室 Docker 執行選項](./media/visual-studio-docker-run-options.png)

**圖3-7**。 視覺化工作室 Docker 執行選項

除了本地開發之外[,Azure 開發人員空間](https://docs.microsoft.com/azure/dev-spaces/)還為多個開發人員提供了一種在 Azure 中處理其自己的 Kubernets 配置的便捷方法。 如圖 3-7 所示,您還可以在 Azure 開發空間中運行應用程式。

如果在創建ASP.NET酷應用程式時未將 Docker 支援添加到該應用程式,則始終可以在以後添加它。 在可視化工作室解決方案資源管理器中,右鍵單擊專案並選擇 **「添加** > **Docker 支援**」,如圖 3-8 所示。

![視覺化工作室加入 Docker 支援](./media/visual-studio-add-docker-support.png)

**圖3-8**。 視覺化工作室加入 Docker 支援

除了 Docker 支援之外,您還可以添加容器業務流程支援,如圖 3-8 所示。 默認情況下,協調器使用庫伯奈斯和赫爾姆。 選擇協調器後,將`azds.yaml`檔添加到專案根,並添加一個`charts`資料夾,其中包含用於配置應用程式並將應用程式部署到 Kubernetes 的 Helm 圖表。 圖 3-9 顯示了新專案中生成的檔。

![視覺化工作室新增協調器支援](./media/visual-studio-add-orchestrator-support.png)

**圖3-9**. 視覺化工作室新增協調器支援

## <a name="references"></a>參考

- [什麼是 Kubernetes？](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [安裝庫伯內斯與米尼庫貝](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [迷你庫貝 vs Docker 桌面](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[前一個](scale-applications.md)
>[下一個](leverage-serverless-functions.md)
