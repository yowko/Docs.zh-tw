---
title: 利用容器和協調器
description: 在 Azure 中利用 Docker 容器和 Kubernetes 協調器
ms.date: 05/13/2020
ms.openlocfilehash: 5d0b7f41caecb3422a4416514de2fdd54e94539a
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613883"
---
# <a name="leveraging-containers-and-orchestrators"></a>利用容器和協調器

容器和協調器的設計是為了解決整合型部署方法常見的問題。

## <a name="challenges-with-monolithic-deployments"></a>整合型部署的挑戰

傳統上，大部分的應用程式都已部署為單一單位。 這類應用程式稱為單體。 這種將應用程式部署為單一單位的一般方法，即使它們是由多個模組或元件所組成，也稱為整合型架構，如圖3-1 所示。

![整合型架構。](./media/monolithic-design.png)

**圖 3-1**。 整合型架構。

雖然它們具有簡單的優點，但是整合型架構也面臨一些挑戰：

### <a name="deployment"></a>部署

整合型應用程式需要整個應用程式的完整部署，即使只進行一項小變更也一樣。 完整部署可能相當昂貴，而且容易出錯。 此外，它們需要重新開機應用程式，這會暫時影響無法使用。

### <a name="scaling"></a>調整大小

整合型應用程式完全裝載于單一機器實例上，通常需要高功能的硬體。 如果單體的任何部分需要調整，則整個應用程式的另一個複本必須部署到另一部電腦。 有了單體，您就無法個別擴充應用程式元件，而是全部或無。 調整不需要調整的元件會導致效率不佳且資源使用量昂貴。

### <a name="environment"></a>環境

整合型應用程式通常會部署到裝載環境，並具有預先安裝的作業系統、執行時間和程式庫相依性。 此環境可能不符合應用程式的開發或測試目標。 跨應用程式環境的不一致是整合型部署問題的常見來源。

### <a name="coupling"></a>緊密

整合型應用程式可能會在其功能元件之間遇到高結合性。 如果沒有固定界限，系統變更通常會導致非預期且成本高昂的副作用。 新功能/修正程式會變得很困難、耗時，而且需要耗費大量的時間。 更新需要大量測試。 結合也會使得重構元件或交換替代的執行變得很容易。 即使是以嚴格的顧慮分離來建造，架構削弱還是會在中將設定為整合式程式碼基底 deteriorates，且不會結束「特殊案例」。

### <a name="platform-lock-in"></a>平臺鎖定

整合型應用程式是以單一技術堆疊來建立。 雖然提供一致性，但這種承諾可能會成為創新的障礙。 新的功能和元件將使用應用程式的目前堆疊來建立，即使是更現代化的技術也是較佳的選擇。 較長期的風險是您的技術堆疊已過時且已過時。 將整個應用程式重新架構到新的、更現代化的平臺，其成本最高，而且有風險。

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>容器和協調器的優點為何？

我們在第1章引進了容器。 我們強調了雲端原生運算基礎（由 CNCF）排名容器化如何作為其雲端原生[線索對應](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png)的第一個步驟-開始雲端原生旅程的企業指導方針。 在本節中，我們將討論容器的優點。

Docker 是最受歡迎的容器管理平臺。 其適用于 Linux 或 Windows 上的容器。 容器提供不同但可重現的應用程式環境，在任何系統上執行相同的方式。 這個層面讓它們適合用來開發和裝載雲端原生服務。 容器會互相隔離。 相同主機硬體上的兩個容器可以有不同版本的軟體，而不會造成衝突。

容器是由變成專案成品並簽入原始檔控制的簡單文字型檔案所定義。 雖然完整伺服器和虛擬機器需要手動進行更新，但容器是可輕鬆控制版本的。 建立在容器中執行的應用程式可以使用自動化工具來進行開發、測試及部署，以作為組建管線的一部分。

容器是不可變的。 定義容器之後，您可以用完全相同的方式重新建立並執行它。 這種不會將其本身用於以元件為基礎的設計。 如果應用程式的某些部分的發展方式不同，當您可以直接部署最常變更的元件時，為何要重新部署整個應用程式？ 應用程式的不同功能和跨領域考慮可能會分成不同的單位。 圖3-2 顯示單一應用程式如何藉由委派特定的功能來利用容器和微服務。 應用程式本身的其餘功能也已容器化。

容器是不可變的。 定義容器之後，您可以用完全相同的方式重新建立並執行它。 這種不會將其本身用於以元件為基礎的設計。 如果應用程式的某些部分的發展方式不同，當您可以直接部署最常變更的元件時，為何要重新部署整個應用程式？ 應用程式的不同功能和跨領域考慮可能會分成不同的單位。 圖3-2 顯示單一應用程式如何藉由委派特定的功能來利用容器和微服務。 應用程式本身的其餘功能也已容器化。

![將整合型應用程式分解成在後端使用微服務。](./media/cloud-native-design.png)

**圖 3-2**。 分解整合型應用程式以採用微服務。

每個雲端原生服務都會在個別的容器中建立及部署。 每個都可以視需要進行更新。 個別服務可以裝載于節點上，並具有適用于每個服務的資源。 在中執行的每個服務都不變、在開發、測試和生產環境之間共用，而且可以輕鬆建立版本。 應用程式的不同區域之間的結合，會明確成為服務之間的呼叫或訊息，而不是單體內的編譯時間相依性。 您也可以選擇最符合指定功能的技術，而不需要變更應用程式的其餘部分。

容器化服務需要自動化管理。 手動管理一大組獨立部署的容器並不可行。 例如，請考慮下列工作：

- 如何在多部電腦的叢集上布建容器實例？
- 一旦部署之後，容器會如何探索並彼此通訊？
- 容器如何依需求相應縮小或放大？
- 如何監視每個容器的健全狀況？
- 如何保護容器免于硬體和軟體失敗？
- 如何將即時應用程式的容器升級為零停機時間？

容器協調器會解決這些問題，並將這些考慮自動化。

在雲端原生的生態系統中，Kubernetes 已成為事實上的容器協調器。 這是由雲端原生運算基礎（由 CNCF）所管理的開放原始碼平臺。 Kubernetes 會將容器化工作負載的部署、調整和操作方面的顧慮自動化到機器叢集上。 不過，安裝和管理 Kubernetes 非常複雜。

更好的方法是利用 Kubernetes 作為雲端廠商的受控服務。 Azure 雲端具備一個完全受控的 Kubernetes 平臺，並[Azure Kubernetes Service （AKS）](https://azure.microsoft.com/services/kubernetes-service/)。 AKS 會將管理 Kubernetes 的複雜性和操作負擔抽象化。 您會使用 Kubernetes 作為雲端服務;Microsoft 會負責管理和支援它。 AKS 也與其他 Azure 服務和開發工具緊密整合。

AKS 是以叢集為基礎的技術。 同盟虛擬機器或節點的集區會部署到 Azure 雲端。 它們會構成高可用性環境或叢集。 叢集會以流暢的單一實體形式呈現給您的雲端原生應用程式。 實際上，AKS 會依照預先定義的策略，將您的容器化服務部署在這些節點上，以平均分配負載。

容器化服務需要自動化管理。 手動管理一大組獨立部署的容器並不可行。 例如，請考慮下列工作：

- 如何在多部電腦的叢集上布建容器實例？
- 一旦部署之後，容器會如何探索並彼此通訊？
- 容器如何依需求相應縮小或放大？
- 如何監視每個容器的健全狀況？
- 如何保護容器免于硬體和軟體失敗？
- 如何將即時應用程式的容器升級為零停機時間？

容器協調器會解決這些問題，並將這些考慮自動化。

在雲端原生的生態系統中，Kubernetes 已成為事實上的容器協調器。 這是由雲端原生運算基礎（由 CNCF）所管理的開放原始碼平臺。 Kubernetes 會將容器化工作負載的部署、調整和操作方面的顧慮自動化到機器叢集上。 不過，安裝和管理 Kubernetes 非常複雜。

更好的方法是利用 Kubernetes 作為雲端廠商的受控服務。 Azure 雲端具備一個完全受控的 Kubernetes 平臺，並[Azure Kubernetes Service （AKS）](https://azure.microsoft.com/services/kubernetes-service/)。 AKS 會將管理 Kubernetes 的複雜性和操作負擔抽象化。 您會使用 Kubernetes 作為雲端服務;Microsoft 會負責管理和支援它。 AKS 也與其他 Azure 服務和開發工具緊密整合。

AKS 是以叢集為基礎的技術。 同盟虛擬機器或節點的集區會部署到 Azure 雲端。 它們會構成高可用性環境或叢集。 叢集會以流暢的單一實體形式呈現給您的雲端原生應用程式。 實際上，AKS 會依照預先定義的策略，將您的容器化服務部署在這些節點上，以平均分配負載。

## <a name="what-are-the-scaling-benefits"></a>什麼是調整優點？

以容器為基礎的服務可以利用協調流程工具（例如 Kubernetes）所提供的調整優勢。 根據設計，容器只知道自己的關係。 當您有多個需要共同作業的容器時，您應該以較高的層級來組織它們。 組織大量的容器及其共用的相依性（例如網路設定）就是協調流程工具的儲存時間！ Kubernetes 會透過容器群組建立抽象層，並將其組織*成 pod*。 Pod 會在稱為*節點*的工作者機器上執行。 此組織結構稱為「叢集」（ *cluster*）。 圖3-3 顯示 Kubernetes 叢集的不同元件。

![Kubernetes 叢集元件。 ](./media/kubernetes-cluster-components.png)
**圖 3-3**。 Kubernetes 叢集元件。

調整容器化工作負載是 container 協調器的一項重要功能。 AKS 支援跨兩個維度進行自動調整：容器實例和計算節點。 它們一起讓 AKS 能夠快速且有效率地回應需求尖峰，並新增額外的資源。 我們將在本章稍後討論 AKS 的調整。

### <a name="declarative-versus-imperative"></a>宣告式與命令式

Kubernetes 支援宣告式和命令式設定。 命令式方法牽涉到執行各種命令，告訴 Kubernetes 該怎麼做的每個步驟。 執行此映射。 刪除此 pod。 公開此埠。 使用宣告式方法時，您可以建立稱為資訊清單的設定檔，以描述您想要的內容，而不是要執行的動作。 Kubernetes 會讀取資訊清單，並將您想要的結束狀態轉換成實際的結束狀態。

命令式命令非常適合用於學習和互動式實驗。 不過，您會想要以宣告方式建立 Kubernetes 資訊清單檔，以將基礎結構作為程式碼方法，以提供可靠且可重複的部署。 資訊清單檔案會變成專案成品，並用於您的 CI/CD 管線，以自動化 Kubernetes 部署。

如果您已經使用命令式命令來設定您的叢集，您可以使用來匯出宣告式資訊清單 `kubectl get svc SERVICENAME -o yaml > service.yaml` 。 此命令會產生類似下面所示的資訊清單：

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

使用宣告式設定時，您可以使用， `kubectl diff -f FOLDERNAME` 針對設定檔所在的資料夾，先預覽將進行的變更。 一旦您確定要套用變更，請執行 `kubectl apply -f FOLDERNAME` 。 新增 `-R` 以遞迴方式處理資料夾階層。

您也可以搭配其他 Kubernetes 功能使用宣告式設定，其中一個是部署。 宣告式部署有助於管理發行、更新和調整。 他們會指示 Kubernetes 部署控制器如何部署新的變更、向外延展負載，或復原到先前的修訂。 如果叢集不穩定，宣告式部署會自動將叢集恢復為所需的狀態。 例如，如果節點應該當機，部署機制會重新部署取代以達到您想要的狀態

使用宣告式設定可讓基礎結構以程式碼的形式來表示，並可簽入和設定版本。 它針對使用組建和部署管線的持續部署提供改良的變更控制和更好的支援。

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>什麼是適用于容器和協調器的案例？

下列案例適用于使用容器和協調器。

### <a name="applications-requiring-high-uptime-and-scalability"></a>需要高執行時間和擴充性的應用程式

具有高執行時間和擴充性需求的個別應用程式，是使用微服務、容器和協調器之雲端原生架構的理想候選項目。 它們可以在容器中開發、在已建立版本的環境中進行測試，以及部署到生產環境中零停機時間。 使用 Kubernetes 叢集可確保這類應用程式也可以根據需求進行調整，並自動從節點失敗中復原。

### <a name="large-numbers-of-applications"></a>大量應用程式

部署和維護大量應用程式的組織會從容器和協調器獲益。 設定容器化環境和 Kubernetes 叢集的前期工作，主要是固定成本。 部署、維護和更新個別應用程式的成本會因應用程式數目而異。 除了少數的應用程式之外，手動維護自訂應用程式的複雜性會超過使用容器和協調器來執行解決方案的成本。

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>何時應避免使用容器和協調器？

如果您無法遵循12個要素的應用程式原則來建立應用程式，您應該考慮避免容器和協調器。 在這些情況下，請考慮以 VM 為基礎的裝載平臺，或可能是某些混合式系統。 有了這項功能，您就可以在不同的容器或甚至無伺服器的函式中，隨時關閉特定的功能。

## <a name="development-resources"></a>開發資源

本節顯示的開發資源簡短清單，可協助您開始使用容器和協調器來進行下一個應用程式。 如果您要尋找如何設計雲端原生微服務架構應用程式的指引，請閱讀這本書隨附的[.Net 微服務：容器化 .Net 應用程式的架構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)。

### <a name="local-kubernetes-development"></a>本機 Kubernetes 開發

Kubernetes 部署在生產環境中提供絕佳價值，但也可以在您的開發電腦本機上執行。 雖然您可以獨立處理個別的微服務，但有時您可能需要在本機執行整個系統，就像是在部署到生產環境時執行一樣。 有數個工具可以協助： Minikube 和 Docker Desktop。 Visual Studio 也提供 Docker 開發的工具。

### <a name="minikube"></a>Minikube

什麼是 Minikube？ Minikube 專案指出「Minikube 在 macOS、Linux 和 Windows 上執行本機 Kubernetes 叢集」。 其主要目標是「作為本機 Kubernetes 應用程式開發的最佳工具，並支援所有符合的 Kubernetes 功能」。 安裝 Minikube 與 Docker 分開，但是 Minikube 支援不同于 Docker Desktop 支援的虛擬機器。 Minikube 目前支援下列 Kubernetes 功能：

- DNS
- NodePorts
- ConfigMaps 和秘密
- 儀表板
- 容器執行時間： Docker、rkt、CRI-O 和 containerd
- 啟用容器網路介面（CNI）
- 輸入

安裝 Minikube 之後，您可以執行命令快速開始使用它 `minikube start` ，這會下載映射並啟動本機 Kubernetes 叢集。 啟動叢集之後，您可以使用標準 Kubernetes 命令與它互動 `kubectl` 。

### <a name="docker-desktop"></a>Docker Desktop

您也可以直接從 Windows 上的 Docker Desktop 使用 Kubernetes。 如果您使用的是 Windows 容器，這是您唯一的選擇，而且也是非 Windows 容器的絕佳選擇。 圖3-4 顯示如何在執行 Docker Desktop 時啟用本機 Kubernetes 支援。

![在 Docker Desktop 中設定 Kubernetes](./media/docker-desktop-kubernetes.png)

**圖 3-4**。 在 Docker Desktop 中設定 Kubernetes。

Docker Desktop 是最受歡迎的工具，可在本機設定和執行容器化應用程式。 當您使用 Docker Desktop 時，可以針對您要部署到生產環境的完全相同 Docker 容器映射，在本機進行開發。 Docker Desktop 是設計成在本機「建立、測試及傳送」容器化應用程式。 它同時支援 Linux 和 Windows 容器。 一旦您將映射推送至映射登錄（例如 Azure Container Registry 或 Docker Hub），AKS 就可以提取並部署到生產環境。

### <a name="visual-studio-docker-tooling"></a>Visual Studio Docker 工具

Visual Studio 支援以 web 應用程式為基礎的 Docker 開發。 當您建立新的 ASP.NET Core 應用程式時，您可以選擇使用 Docker 支援來設定它，如圖3-5 所示。

![Visual Studio 啟用 Docker 支援](./media/visual-studio-enable-docker-support.png)

**圖 3-5**。 Visual Studio 啟用 Docker 支援

選取此選項時，會使用 `Dockerfile` 其根目錄中的建立專案，這可用來在 Docker 容器中建立和裝載應用程式。 範例 Dockerfile 如 [圖 3]-6 所示。

```docker
FROM mcr.microsoft.com/dotnet/core/aspnet:3.1-buster-slim AS base
WORKDIR /app
EXPOSE 80
EXPOSE 443

FROM mcr.microsoft.com/dotnet/core/sdk:3.1-buster AS build
WORKDIR /src
COPY ["eShopWeb/eShopWeb.csproj", "eShopWeb/"]
RUN dotnet restore "eShopWeb/eShopWeb.csproj"
COPY . .
WORKDIR "/src/eShopWeb"
RUN dotnet build "eShopWeb.csproj" -c Release -o /app/build

FROM build AS publish
RUN dotnet publish "eShopWeb.csproj" -c Release -o /app/publish

FROM base AS final
WORKDIR /app
COPY --from=publish /app/publish .
ENTRYPOINT ["dotnet", "eShopWeb.dll"]
```

**圖 3-6**。 Visual Studio 產生的 Dockerfile

應用程式執行時的預設行為也會設定為使用 Docker。 圖3-7 顯示新的 ASP.NET Core 專案提供的不同執行選項，並已新增 Docker 支援。

![Visual Studio Docker 執行選項](./media/visual-studio-docker-run-options.png)

**圖 3-7**。 Visual Studio Docker 執行選項

除了本機開發以外， [Azure Dev Spaces](https://docs.microsoft.com/azure/dev-spaces/)提供便利的方式讓多個開發人員在 Azure 內使用自己的 Kubernetes 設定。 如 [圖 3-7] 所示，您也可以在 Azure Dev Spaces 中執行應用程式。

此外，您隨時都可以將 Docker 支援新增至現有的 ASP.NET Core 應用程式。 在 [Visual Studio 方案總管中，以滑鼠右鍵按一下專案並**新增**  >  **Docker 支援**，如圖3-8 所示。

![Visual Studio 新增 Docker 支援](./media/visual-studio-add-docker-support.png)

**圖 3-8**。 將 Docker 支援新增至 Visual Studio

您也可以新增容器協調流程支援，如圖3-8 所示。 根據預設，orchestrator 會使用 Kubernetes 和 Helm。 一旦您選擇協調器，檔案 `azds.yaml` 就會新增至專案根目錄，並加入一個 `charts` 資料夾，其中包含用來設定和部署應用程式至 Kubernetes 的 Helm 圖表。 圖3-9 顯示新專案中產生的檔案。

您也可以新增容器協調流程支援，如圖3-8 所示。 根據預設，orchestrator 會使用 Kubernetes 和 Helm。 一旦您選擇協調器，檔案 `azds.yaml` 就會新增至專案根目錄，並加入一個 `charts` 資料夾，其中包含用來設定和部署應用程式至 Kubernetes 的 Helm 圖表。 圖3-9 顯示新專案中產生的檔案。

![Visual Studio 新增協調器支援](./media/visual-studio-add-orchestrator-support.png)

**圖 3-9**。 將協調流程支援新增至 Visual Studio

### <a name="visual-studio-code-docker-tooling"></a>Visual Studio Code Docker 工具

有一些擴充功能可用於支援 Docker 開發的 Visual Studio Code。

Microsoft 提供[Docker for Visual Studio Code 延伸](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)模組。 此延伸模組可簡化將容器支援新增至應用程式的過程。 它會 scaffold 所需的檔案、建立 Docker 映射，並可讓您在容器內對應用程式進行調試。 延伸模組具備視覺化瀏覽器的功能，可讓您輕鬆地對容器和映射採取動作，例如啟動、停止、檢查、移除等等。 延伸模組也支援 Docker Compose 可讓您將多個執行中的容器當做單一單位來管理。

>[!div class="step-by-step"]
>[上一個](scale-applications.md) 
>[下一步](leverage-serverless-functions.md)
