---
title: 利用容器和協調器
description: 在 Azure 中利用 Docker 容器和 Kubernetes 協調器
ms.date: 06/30/2019
ms.openlocfilehash: 4008a14e4db28e07d5fda0a1f175aada9ffe6734
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71182878"
---
# <a name="leveraging-containers-and-orchestrators"></a>利用容器和協調器

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

容器和協調器的設計是為了解決整合型部署方法常見的問題。

## <a name="challenges-with-monolithic-deployments"></a>整合型部署的挑戰

傳統上，大部分的應用程式都已部署為單一單位。 這類應用程式稱為單體。 這種將應用程式部署為單一單位的一般方法，即使它們是由多個模組或元件所組成，也稱為整合型架構，如圖3-1 所示。

![整合型架構。](./media/monolithic-architecture.png)

**圖 3-1**。 整合型架構。

雖然它們具有簡單的優點，但是整合型架構也面臨一些挑戰：

### <a name="deployments"></a>部署

部署到整合型應用程式通常需要重新開機整個應用程式，即使只更換一個小模組也一樣。 視裝載應用程式的機器數目而定，這可能會導致部署期間的停機時間。

### <a name="hosting"></a>裝載

整合型應用程式完全裝載于單一機器實例上。 這可能需要更高功能的硬體，而不是分散式應用程式所需的任何模組。 此外，如果應用程式有任何部分變成瓶頸，則整個應用程式必須部署到其他電腦節點，才能相應放大。

### <a name="environment"></a>環境

整合型應用程式通常會部署到現有的裝載環境（作業系統、已安裝的架構等）。 此環境可能不符合開發或測試應用程式的環境。 應用程式環境中的不一致是整合型部署問題的常見來源。

### <a name="coupling"></a>緊密

整合型應用程式的不同元件之間，以及應用程式與其環境之間，可能會有很多的結合。 這可能會使它難以分解特定的服務，或在稍後考慮，以便增加其擴充性或交換替代的執行方式。 這種結合也會導致對系統變更有更大的潛在影響，需要在較大型的應用程式中進行大量測試。

### <a name="technology-choice"></a>技術選擇

整合型應用程式會建立並部署為一個單位。 這提供簡化和一致性，但可能是創新的障礙。 雖然系統中的新功能或模組可能較適合較新式的平臺或架構，但可能會使用應用程式目前的方法來建立，以達成一致性以及輕鬆的開發和部署。

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>容器和協調器的優點為何？

Docker 是最受歡迎的容器管理和映射處理平臺，可讓您快速使用 Linux 和 Windows 上的容器。 容器提供不同但可重現的應用程式環境，在任何系統上執行相同的方式。 這讓它們適合用來在雲端原生應用程式中開發和裝載應用程式和應用程式元件。 容器會彼此隔離，因此相同主機硬體上的兩個容器可以有不同版本的軟體，甚至是安裝作業系統，而不會造成衝突。

更多的是，容器是由可簽入原始檔控制的簡單檔案所定義。 不同于完整伺服器，甚至是虛擬機器，通常需要手動執行工作來套用更新或安裝其他服務，容器基礎結構很容易受到版本控制。 因此，建立在容器中執行的應用程式可以使用自動化工具來進行開發、測試及部署，以作為組建管線的一部分。

容器是不可變的。 一旦有了容器的定義，您就可以重新建立該容器，而且它會以完全相同的方式執行。 這種不會將其本身用於以元件為基礎的設計。 如果應用程式的某些部分不會經常變更，當您可以直接部署最常變更的元件時，為什麼要重新部署整個應用程式？ 應用程式的不同功能和跨領域考慮可能會分成不同的單位。 圖3-2 顯示單一應用程式如何藉由委派特定的功能來利用容器和微服務。 應用程式本身的其餘功能也已容器化。

![將整合型應用程式分解成在後端使用微服務。**圖 3-2**。 ](./media/breaking-up-monolith-with-backend-microservices.png)
 將整合型應用程式分解成在後端使用微服務。

使用個別容器所建立的雲端原生應用程式，可讓您視需要部署最多或最少的應用程式。 個別服務可以裝載于節點上，並具有適用于每個服務的資源。 在中執行的每個服務都是不可變的，可以在開發、測試和生產環境之間共用，而且可以輕鬆地進行版本設定。 應用程式的不同區域之間的結合，會明確成為服務之間的呼叫或訊息，而不是單體內的編譯時間相依性。 整體應用程式的任何特定部分都可以選擇最適合該功能或功能的技術，而不需要變更應用程式的其餘部分。

## <a name="what-are-the-scaling-benefits"></a>什麼是調整優點？

以容器為基礎的服務可以利用協調流程工具（例如 Kubernetes）所提供的調整優勢。 根據設計，容器只知道自己的關係。 一旦您開始有多個需要共同作業的容器，就可以在較高的層級進行組織。 組織大量的容器及其共用的相依性（例如網路設定）就是協調流程工具的儲存時間！ Kubernetes 是一種容器協調流程平臺，專門設計來自動化部署、調整和管理容器化應用程式。 它會在容器群組之上建立抽象層，並將其*組織成 pod*。 Pod 會在稱為*節點*的工作者機器上執行。 整個組織的群組稱為「叢集」（ *cluster*）。 圖3-3 顯示 Kubernetes 叢集的不同元件。

![Kubernetes 叢集元件。**圖 3-3**。 ](./media/kubernetes-cluster-components.png)
 Kubernetes 叢集元件。

Kubernetes 有內建支援，可調整叢集以符合需求。 相較于容器化微服務，這可讓雲端原生應用程式能夠快速且有效率地回應需求尖峰，並在需要時使用其他資源。

### <a name="declarative-versus-imperative"></a>宣告式與命令式

Kubernetes 支援宣告式和命令式物件設定。 命令式方法牽涉到執行各種命令，告訴 Kubernetes 該怎麼做的每個步驟。 *執行*此映射。 *刪除*此 pod。 *公開*此埠。 使用宣告式方法時，您可以使用設定檔來描述*您想要的內容*，而不是*要執行*的動作，並 Kubernetes 瞭解要怎麼做才能達成所要的結束狀態。 如果您已經使用命令式命令來設定您的叢集，您可以使用`kubectl get svc SERVICENAME -o yaml > service.yaml`來匯出宣告式資訊清單。 這會產生資訊清單檔案，如下所示：

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

使用宣告式設定時，您可以使用`kubectl diff -f FOLDERNAME` ，針對設定檔所在的資料夾，先預覽將進行的變更。 一旦您確定要套用變更，請執行`kubectl apply -f FOLDERNAME`。 新增`-R`以遞迴方式處理資料夾階層。

除了服務以外，您還可以針對其他 Kubernetes 功能（例如*部署*）使用宣告式設定。 部署控制器會使用宣告式部署來更新叢集資源。 部署是用來推出新的變更、相應增加以支援更多負載，或復原到先前的修訂版本。 如果叢集不穩定，宣告式部署會提供一種機制，讓叢集自動復原成所需的狀態。

使用宣告式設定可讓基礎結構以程式碼的形式來表示，並可簽入和設定版本。 這可讓您使用組建和部署管線（系結至原始檔控制變更）來改善持續部署的變更控制和更好的支援。

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>什麼是適用于容器和協調器的案例？

下列案例適用于使用容器和協調器。

### <a name="applications-requiring-high-uptime-and-scalability"></a>需要高執行時間和擴充性的應用程式

具有高執行時間和擴充性需求的個別應用程式，是使用微服務、容器和協調器之雲端原生架構的理想候選項目。 這些應用程式可以在使用已建立版本環境的容器中開發，可以在進入生產階段之前進行廣泛的測試，而且可以部署到生產環境，而不會發生任何停機時間。 使用 Kubernetes 叢集可確保這類應用程式也可以根據需求進行調整，並自動從節點失敗中復原。

### <a name="large-numbers-of-applications"></a>大量應用程式

部署和之後必須維護大量應用程式的組織，可從容器和協調器獲益。 設定容器化環境和 Kubernetes 叢集的前期工作，主要是固定成本。 部署、維護和更新個別應用程式的成本，會因必須維護的應用程式數目而異。 除了特定相當少的應用程式，維護自訂應用程式的複雜性也超出了使用容器和協調器來執行解決方案的成本。

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>何時應避免使用容器和協調器？

如果您不願意或無法遵循12因素應用程式原則來建立應用程式，您可能會更有效地避免容器和協調器。 在這些情況下，最好是使用以 VM 為基礎的裝載平臺，或可能是一些混合式系統，您可以在其中將特定功能關閉到個別容器或甚至無伺服器功能。 

## <a name="development-resources"></a>開發資源

本節顯示的開發資源簡短清單，可協助您開始使用容器和協調器來進行下一個應用程式。 如果您要尋找如何設計雲端原生微服務架構應用程式的指引，請閱讀這本書的[.net 微服務：容器化 .NET 應用程式的架構](https://aka.ms/microservicesebook)。

### <a name="local-kubernetes-development"></a>本機 Kubernetes 開發

Kubernetes 部署在生產環境中提供絕佳價值，但您也可以在本機執行。 雖然大部分的時間都可以單獨處理個別應用程式或微服務，但有時最好能夠在本機執行整個系統，就像是部署到生產環境時執行的一樣。 有幾種方式可以達到這個目的，其中兩個是 Minikube 和 Docker Desktop。 Visual Studio 也提供 Docker 開發的工具。

### <a name="minikube"></a>Minikube

什麼是 Minikube？ Minikube 專案指出「Minikube 在 macOS、Linux 和 Windows 上執行本機 Kubernetes 叢集」。 其主要目標是「作為本機 Kubernetes 應用程式開發的最佳工具，並支援所有符合的 Kubernetes 功能」。 安裝 Minikube 與 Docker 分開，但是 Minikube 支援不同于 Docker Desktop 支援的虛擬機器。 Minikube 目前支援下列 Kubernetes 功能：

- DNS
- NodePorts
- ConfigMaps 和秘密
- 儀表板
- 容器執行時間：Docker、rkt、CRI 和 containerd
- 啟用容器網路介面（CNI）
- 站

安裝 Minikube 之後，您可以執行`minikube start`命令快速開始使用它，這會下載映射並啟動本機 Kubernetes 叢集。 啟動叢集之後，您可以使用標準 Kubernetes `kubectl`命令與它互動。

### <a name="docker-desktop"></a>Docker Desktop

您也可以直接從 Windows 上的 Docker Desktop 使用 Kubernetes。 如果您使用的是 Windows 容器，這是您唯一的選項，而且也是非 Windows 容器的絕佳選擇。 標準 Docker 桌面設定應用程式是用來設定從 Docker Desktop 執行的 Kubernetes。

![在 Docker Desktop 中設定 Kubernetes](./media/docker-desktop-kubernetes.png)

**圖 3-4**。 在 Docker Desktop 中設定 Kubernetes。

Docker Desktop 已經是最受歡迎的工具，可在本機設定和執行容器化應用程式。 當您使用 Docker Desktop 時，可以針對您要部署到生產環境的完全相同 Docker 容器映射，在本機進行開發。 Docker Desktop 是設計成在本機「建立、測試及傳送」容器化應用程式。 映射一旦送出至映射登錄（例如 Azure Container Registry 或 Docker Hub）之後，Azure Kubernetes Service （AKS）之類的服務就會在生產環境中管理應用程式。

### <a name="visual-studio-docker-tooling"></a>Visual Studio Docker 工具

Visual Studio 支援 web 應用程式的 Docker 開發。 當您建立新的 ASP.NET Core 應用程式時，您可以選擇使用 Docker 支援來設定它，做為專案建立過程的一部分，如圖3-5 所示。

![Visual Studio 啟用 Docker 支援](./media/visual-studio-enable-docker-support.png)

**圖 3-5**。 Visual Studio 啟用 Docker 支援

選取此選項時，會`Dockerfile`使用其根目錄中的建立專案，這可用來在 Docker 容器中建立和裝載應用程式。 範例 Dockerfile 如圖3-6 所示。

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

**圖 3-6**。 Visual Studio 產生的 Dockerfile

應用程式執行時的預設行為也會設定為使用 Docker。 圖3-7 顯示新的 ASP.NET Core 專案提供的不同執行選項，並已新增 Docker 支援。

![Visual Studio Docker 執行選項](./media/visual-studio-docker-run-options.png)

**圖 3-7**。 Visual Studio Docker 執行選項

除了本機開發以外， [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/)提供便利的方式讓多個開發人員在 Azure 內使用自己的 Kubernetes 設定。 如 [圖 3-10] 所示，您也可以在 Azure Dev Spaces 中執行應用程式。

如果您在建立時未將 Docker 支援新增至 ASP.NET Core 應用程式，您可以隨時將其新增。 在 Visual Studio 方案總管中，以滑鼠右鍵按一下專案，然後選取 **新增** >  **Docker 支援**，如圖3-8 所示。

![Visual Studio 新增 Docker 支援](./media/visual-studio-add-docker-support.png)

**圖 3-8**。 Visual Studio 新增 Docker 支援

除了 Docker 支援以外，您也可以新增容器協調流程支援，如圖3-11 所示。 根據預設，orchestrator 會使用 Kubernetes 和 Helm。 一旦您選擇協調器， `azds.yaml`檔案就會新增至專案根目錄，並加入一個`charts`資料夾，其中包含用來設定和部署應用程式至 Kubernetes 的 Helm 圖表。 圖3-9 顯示新專案中產生的檔案。

![Visual Studio 新增協調器支援](./media/visual-studio-add-orchestrator-support.png)

**圖 3-9**。 Visual Studio 新增協調器支援

## <a name="references"></a>reference

- [什麼是 Kubernetes？](https://blog.newrelic.com/engineering/what-is-kubernetes/)
- [使用 Minikube 安裝 Kubernetes](https://kubernetes.io/docs/setup/learning-environment/minikube/)
- [MiniKube 與 Docker Desktop](https://medium.com/containers-101/local-kubernetes-for-windows-minikube-vs-docker-desktop-25a1c6d3b766)
- [Visual Studio Tools for Docker](https://docs.microsoft.com/dotnet/standard/containerized-lifecycle-architecture/design-develop-containerized-apps/visual-studio-tools-for-docker)

>[!div class="step-by-step"]
>[上一頁](scale-applications.md)
>[下一頁](leverage-serverless-functions.md)
