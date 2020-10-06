---
title: 利用容器和協調器
description: 利用 Azure 中的 Docker 容器和 Kubernetes 協調器
ms.date: 05/31/2020
ms.openlocfilehash: b4bdbe5c6b3946658e6c11a40cbbb2feb07cc951
ms.sourcegitcommit: a8a205034eeffc7c3e1bdd6f506a75b0f7099ebf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/06/2020
ms.locfileid: "91755905"
---
# <a name="leveraging-containers-and-orchestrators"></a>利用容器和協調器

容器和協調器的設計目的是要解決整合型部署方法常見的問題。

## <a name="challenges-with-monolithic-deployments"></a>整合型部署的挑戰

傳統上，大部分的應用程式都已部署為單一單位。 這類應用程式稱為單體。 這是將應用程式部署為單一單位的一般方法，即使它們是由多個模組或元件所組成，如圖3-1 所示。

![整合型架構。](./media/monolithic-design.png)

**圖 3-1**。 整合型架構。

雖然它們具有簡單的優點，但整合型架構卻面臨一些挑戰：

### <a name="deployment"></a>部署

整合型應用程式需要整個應用程式的完整部署，即使只進行了少許變更。 完整部署可能很昂貴，而且容易出錯。 此外，它們需要重新開機應用程式，這會暫時影響無法使用的情況。

### <a name="scaling"></a>調整大小

整合型應用程式完全裝載在單一電腦實例上，通常需要高功能硬體。 如果單體的任何部分需要調整，則必須將整個應用程式的另一個複本部署到另一部電腦。 有了單體，您就無法個別調整應用程式元件，而是全部或無。 調整不需要調整的元件會導致效率不佳和成本高昂的資源使用量。

### <a name="environment"></a>環境

整合型應用程式通常會部署到裝載環境，其中包含預先安裝的作業系統、執行時間和程式庫相依性。 此環境可能不符合開發或測試應用程式的環境。 應用程式環境之間的不一致是整合型部署問題的常見來源。

### <a name="coupling"></a>耦合

整合型應用程式可能會在其功能元件之間經歷高結合性。 如果沒有固定界限，系統變更通常會導致非預期且高成本的副作用。 新功能/修正變得很難處理、耗時且昂貴。 更新需要廣泛的測試。 結合也會讓您難以重構元件或在替代的執行中交換。 即使是以嚴格的考慮分隔來建造，架構削弱還是會將 in 作為整合型程式碼基底降低，並使用永不結束的「特殊案例」。

### <a name="platform-lock-in"></a>平臺鎖定

整合型應用程式是以單一技術堆疊來建立。 雖然提供一致性，但這種承諾會成為創新的障礙。 新的功能和元件將會使用應用程式的目前堆疊來建立，即使更多新式技術可能是更好的選擇。 長期的風險是您的技術堆疊變成過期和淘汰。 將整個應用程式重新架構到全新、更新式的平臺，成本最高且有風險。

## <a name="what-are-the-benefits-of-containers-and-orchestrators"></a>容器和協調器的優點為何？

我們在第1章推出了容器。 我們強調了雲端原生運算基礎 (CNCF) 排名容器化如何成為其 [雲端原生線索對應](https://raw.githubusercontent.com/cncf/trailmap/master/CNCF_TrailMap_latest.png) 的第一步，也就是開始其雲端原生旅程的企業。 在本節中，我們會討論容器的優點。

Docker 是最受歡迎的容器管理平臺。 它適用于 Linux 或 Windows 上的容器。 容器提供個別但可重現的應用程式環境，以相同的方式在任何系統上執行。 此層面讓它們非常適合用來開發和裝載雲端原生服務。 容器互相隔離。 相同主機硬體上的兩個容器可以有不同版本的軟體，而不會造成衝突。

容器是由成為專案成品並簽入原始檔控制的簡單文字型檔案所定義。 雖然完整的伺服器和虛擬機器需要手動進行更新，但容器很容易受到版本控制。 您可以使用自動化工具作為組建管線的一部分，來開發、測試和部署在容器中執行的應用程式。

容器是不可變的。 定義容器之後，您可以用完全相同的方式重新建立並執行容器。 這種永久性也適合以元件為基礎的設計。 如果應用程式的某些部分與其他部分的發展方式不同，當您只部署最常變更的元件時，為什麼要重新部署整個應用程式？ 應用程式的不同功能和跨領域考慮可以分成不同的單位。 圖3-2 顯示整合型應用程式如何藉由委派特定功能或功能來利用容器和微服務。 應用程式本身的其餘功能也已經過容器化。

![將整合型應用程式分解成在後端使用微服務。](./media/cloud-native-design.png)

**圖 3-2**。 分解整合型應用程式以採用微服務。

每個雲端原生服務都是在個別的容器中建立和部署。 每個都可以視需要進行更新。 個別服務可以裝載在具有適用于每個服務之資源的節點上。 每個服務執行所在的環境都是不可變的，在開發、測試和生產環境之間共用，而且可以輕鬆地建立版本。 應用程式不同區域之間的結合會明確地做為服務之間的呼叫或訊息，而不是單體內的編譯時間相依性。 您也可以選擇最適合指定功能的技術，而不需要變更應用程式的其餘部分。

容器化服務需要自動化管理。 手動管理一組大量獨立部署的容器是不可行的。 例如，請考慮下列工作：

- 如何在多部電腦的叢集中布建容器實例？
- 一旦部署之後，容器會如何探索和彼此通訊？
- 容器如何隨選相應放大或縮小？
- 如何監視每個容器的健全狀況？
- 如何保護容器以防止硬體和軟體失敗？
- 如何升級即時應用程式的容器，而不會有停機時間？

容器協調器會解決這些問題，並將其自動化。

在雲端原生的生態系統中，Kubernetes 已成為實際的容器協調器。 它是由雲端原生運算基礎管理的開放原始碼平臺 (CNCF) 。 Kubernetes 可將容器化工作負載在電腦叢集中的部署、規模調整和操作考慮自動化。 但是，安裝和管理 Kubernetes 相當複雜。

更好的方法是使用 Kubernetes 作為雲端廠商的受控服務。 Azure 雲端具備 [Azure Kubernetes Service (AKS) ](https://azure.microsoft.com/services/kubernetes-service/)的完全受控 Kubernetes 平臺。 AKS 可抽象化管理 Kubernetes 的複雜性和操作額外負荷。 您可以使用 Kubernetes 作為雲端服務;Microsoft 負責管理和支援。 AKS 也會與其他 Azure 服務和開發工具緊密整合。

AKS 是以叢集為基礎的技術。 同盟虛擬機器或節點的集區會部署至 Azure 雲端。 它們會形成高可用性環境或叢集。 叢集會顯示為您雲端原生應用程式的無縫單一實體。 在幕後，AKS 會在這些節點上部署您的容器化服務，並遵循可平均分配負載的預先定義策略。

## <a name="what-are-the-scaling-benefits"></a>調整的優點為何？

以容器為基礎的服務可利用協調流程工具（例如 Kubernetes）所提供的調整優勢。 設計容器只知道自己的身分。 當您有多個需要一起運作的容器時，您應該將它們組織在較高層級。 組織大量的容器及其共用的相依性（例如網路設定），就是協調流程工具在每天儲存的地方！ Kubernetes 會在容器群組之間建立抽象層，並將其 *組織成 pod*。 Pod 會在稱為 *節點*的背景工作電腦上執行。 此組織結構稱為「叢集」（ *cluster*）。 圖3-3 顯示 Kubernetes 群集的不同元件。

![Kubernetes 叢集元件。 ](./media/kubernetes-cluster-components.png)
**圖 3-3**。 Kubernetes 叢集元件。

調整容器化工作負載是容器協調器的重要功能。 AKS 支援在兩個維度之間進行自動調整：容器實例和計算節點。 它們一起讓 AKS 能夠快速且有效率地回應尖峰需求，並新增其他資源。 我們將在本章稍後討論調整 AKS。

### <a name="declarative-versus-imperative"></a>宣告式和命令式

Kubernetes 同時支援宣告式和命令式設定。 命令式方法牽涉到執行各種命令，告訴 Kubernetes 該怎麼做的每個步驟。 執行此映射。 刪除此 pod。 公開此埠。 使用宣告式方法時，您會建立稱為資訊清單的設定檔，以描述您想要的內容，而不是要做什麼。 Kubernetes 會讀取資訊清單，並將您想要的結束狀態轉換成實際的結束狀態。

命令式命令很適合用於學習和互動式實驗。 不過，您會想要以宣告方式建立 Kubernetes 資訊清單檔，以採用基礎結構即程式碼方法，提供可靠且可重複的部署。 資訊清單檔案會變成專案成品，並用於您的 CI/CD 管線，以自動化 Kubernetes 部署。

如果您已經使用命令式命令設定您的叢集，您可以使用匯出宣告式資訊清單 `kubectl get svc SERVICENAME -o yaml > service.yaml` 。 此命令會產生類似下面所示的資訊清單：

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

使用宣告式設定時，您可以 `kubectl diff -f FOLDERNAME` 針對設定檔所在的資料夾使用，在認可之前，先預覽將進行的變更。 一旦您確定要套用變更，請執行 `kubectl apply -f FOLDERNAME` 。 加入 `-R` 以遞迴方式處理資料夾階層。

您也可以使用宣告式設定搭配其他 Kubernetes 功能，也就是部署的其中一個。 宣告式部署有助於管理版本、更新和調整。 他們會指示 Kubernetes 部署控制器如何部署新的變更、向外延展負載，或回復為先前的修訂。 如果叢集不穩定，宣告式部署會自動將叢集傳回所需的狀態。 例如，如果節點應損毀，部署機制將會重新部署取代以達成您所要的狀態

使用宣告式設定可讓基礎結構以程式碼的形式來表示，該程式碼可與應用程式程式碼一起簽入和建立版本。 它針對使用組建和部署管線的持續部署提供改良的變更控制及更好的支援。

## <a name="what-scenarios-are-ideal-for-containers-and-orchestrators"></a>哪些案例適用于容器和協調器？

下列案例適用于使用容器和協調器。

### <a name="applications-requiring-high-uptime-and-scalability"></a>需要高執行時間和擴充性的應用程式

具有高執行時間和擴充性需求的個別應用程式，是使用微服務、容器和協調器的雲端原生架構的絕佳候選項目。 它們可以在容器中開發、在已建立版本的環境中進行測試，並部署到生產環境中，而不需要停機。 使用 Kubernetes 叢集可確保這類應用程式也可以視需要進行調整，並自動從節點失敗中復原。

### <a name="large-numbers-of-applications"></a>大量的應用程式

部署和維護大量應用程式的組織可從容器和協調器獲益。 設定容器化環境和 Kubernetes 叢集的前一項工作，主要是固定成本。 部署、維護和更新個別應用程式的成本會隨著應用程式數目而異。 除了少數的應用程式之外，手動維護自訂應用程式的複雜度會超過使用容器和協調器來執行解決方案的成本。

## <a name="when-should-you-avoid-using-containers-and-orchestrators"></a>您應該避免使用容器和協調器？

如果您無法依照12要素應用程式原則來建立應用程式，您應該考慮避免容器和協調器。 在這些情況下，請考慮以 VM 為基礎的裝載平臺，或可能的混合式系統。 有了這項功能，您就可以隨時將某些功能關閉到個別的容器或甚至無伺服器功能。

## <a name="development-resources"></a>開發資源

本節說明可協助您開始針對下一個應用程式使用容器和協調器的開發資源的簡短清單。 如果您要尋找有關如何設計您的雲端原生微服務架構應用程式的指引，請閱讀這本書隨附的 [.Net 微服務：容器化 .Net 應用程式的架構](https://dotnet.microsoft.com/download/thank-you/microservices-architecture-ebook)。

### <a name="local-kubernetes-development"></a>本機 Kubernetes 開發

Kubernetes 部署在生產環境中提供絕佳的價值，但也可以在您的開發機器本機上執行。 雖然您可以獨立處理個別的微服務，但有時您可能需要在本機執行整個系統，就像是在部署到生產環境時執行一樣。 有幾個工具可協助： Minikube 和 Docker Desktop。 Visual Studio 也提供 Docker 開發的工具。

### <a name="minikube"></a>Minikube

什麼是 Minikube？ Minikube 專案會顯示「Minikube 在 macOS、Linux 和 Windows 上實行本機 Kubernetes 叢集」。 其主要目標是「最適合用來進行本機 Kubernetes 應用程式開發的工具，並支援所有符合的 Kubernetes 功能」。 安裝 Minikube 與 Docker 不同，但 Minikube 支援的虛擬器與 Docker Desktop 所支援的不同。 Minikube 目前支援下列 Kubernetes 功能：

- DNS
- NodePorts
- ConfigMaps 和秘密
- 儀表板
- 容器執行時間： Docker、>rkt、CRI-O 和 containerd
-  (CNI) 啟用容器網路介面
- 輸入

安裝 Minikube 之後，您可以藉由執行命令來快速開始使用 `minikube start` ，此命令會下載映射並啟動本機 Kubernetes 叢集。 啟動叢集之後，您可以使用標準 Kubernetes 命令與其互動 `kubectl` 。

### <a name="docker-desktop"></a>Docker Desktop

您也可以直接從 Windows 上的 Docker Desktop 使用 Kubernetes。 如果您是使用 Windows 容器，這是您唯一的選項，而且也是非 Windows 容器的絕佳選擇。 圖3-4 顯示如何在執行 Docker Desktop 時啟用本機 Kubernetes 支援。

![在 Docker Desktop 中設定 Kubernetes](./media/docker-desktop-kubernetes.png)

**圖 3-4**。 在 Docker Desktop 中設定 Kubernetes。

Docker Desktop 是最受歡迎的工具，可在本機設定和執行容器化應用程式。 當您使用 Docker Desktop 時，您可以在本機針對您將部署到生產環境的相同 Docker 容器映射集進行本機開發。 Docker Desktop 的設計目的是在本機「建立、測試和傳送」容器化應用程式。 它同時支援 Linux 和 Windows 容器。 將映射推送至映射登錄（例如 Azure Container Registry 或 Docker Hub）後，AKS 可以將其提取並部署到生產環境。

### <a name="visual-studio-docker-tooling"></a>Visual Studio Docker 工具

Visual Studio 支援 web 應用程式的 Docker 開發。 當您建立新的 ASP.NET Core 應用程式時，您可以選擇使用 Docker 支援進行設定，如 [圖 3-5] 所示。

![Visual Studio 啟用 Docker 支援](./media/visual-studio-enable-docker-support.png)

**圖 3-5**。 Visual Studio 啟用 Docker 支援

選取此選項時，會 `Dockerfile` 在其根目錄中建立專案，此專案可以用來在 Docker 容器中建立和裝載應用程式。 圖 3-6 中顯示的範例 Dockerfile

```dockerfile
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

當應用程式執行時，預設行為也會設定為使用 Docker。 [圖 3-7] 顯示新的 ASP.NET Core 專案中可用的不同回合選項，這些選項是在已新增 Docker 支援的情況中建立

![Visual Studio Docker 執行選項](./media/visual-studio-docker-run-options.png)

**圖 3-7**。 Visual Studio Docker 執行選項

除了本機開發之外， [Azure Dev Spaces](/azure/dev-spaces/) 也提供便利的方法，讓多個開發人員在 Azure 中使用自己的 Kubernetes 設定。 如圖3-7 中所示，您也可以在 Azure Dev Spaces 中執行應用程式。

此外，您隨時都可以將 Docker 支援新增至現有的 ASP.NET Core 應用程式。 在 [Visual Studio] 方案總管中，以滑鼠右鍵按一下專案，然後選取 [**新增**  >  **Docker 支援**]，如圖3-8 所示。

![Visual Studio 新增 Docker 支援](./media/visual-studio-add-docker-support.png)

**圖 3-8**。 將 Docker 支援新增至 Visual Studio

您也可以新增容器協調流程支援，也會顯示在圖3-8 中。 根據預設，orchestrator 會使用 Kubernetes 和 Helm。 選擇協調器之後，會將檔案 `azds.yaml` 新增至專案根目錄，並 `charts` 新增包含用來設定和部署應用程式至 Kubernetes 之 Helm 圖表的資料夾。 圖3-9 顯示新專案中產生的檔案。

![Visual Studio 新增協調器支援](./media/visual-studio-add-orchestrator-support.png)

**圖 3-9**。 將協調流程支援新增至 Visual Studio

### <a name="visual-studio-code-docker-tooling"></a>Visual Studio Code Docker 工具

有一些延伸模組可用於支援 Docker 開發的 Visual Studio Code。

Microsoft [為 Visual Studio Code 擴充](https://marketplace.visualstudio.com/items?itemName=ms-azuretools.vscode-docker)功能提供 Docker。 此延伸模組可簡化將容器支援新增至應用程式的程式。 它 scaffold 必要的檔案、建立 Docker 映射，並可讓您在容器內進行應用程式的偵錯工具。 擴充功能可讓您輕鬆地在容器和影像（例如啟動、停止、檢查、移除等）上採取動作。 延伸模組也支援 Docker Compose，可讓您將多個執行中的容器當作單一單位來管理。

>[!div class="step-by-step"]
>[上一個](scale-applications.md) 
>[下一步](leverage-serverless-functions.md)
