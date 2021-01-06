---
title: 適用于 WCF 開發人員的 Kubernetes-gRPC
description: 在 Kubernetes 叢集中執行 ASP.NET Core gRPC services。
ms.date: 12/15/2020
ms.openlocfilehash: 0b457d6fa982b5f5b983194d4aedbff0eb782f36
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938051"
---
# <a name="kubernetes"></a>Kubernetes

雖然可以在 Docker 主機上手動執行容器，但是針對可靠的生產系統，最好使用容器協調流程引擎來管理叢集中數部伺服器上執行的多個實例。 有各種可用的容器協調流程引擎，包括 Kubernetes、Docker Swarm 和 Apache Mesos。 但在這些引擎中，Kubernetes 的範圍遠超出最廣泛使用的範圍，因此將會是本章的焦點。

Kubernetes 包含下列功能：

- **排程** 會在叢集中的多個節點上執行容器，以確保可用資源的使用量達到平衡，並在發生中斷時讓容器保持執行狀態，以及處理新版本映射或新設定的輪流更新。
- **健康情況檢查** 會監視容器，以確保持續的服務。
- **DNS & 服務探索** 會處理叢集中服務之間的路由。
- 輸入會在 **外部公開選取** 的服務，通常會在這些服務的實例之間提供負載平衡。
- **資源管理** 會將儲存體等外部資源（例如儲存體）附加至容器。

本章將詳細說明如何將 ASP.NET Core gRPC 服務和取用服務的網站部署至 Kubernetes 叢集中。 使用的範例應用程式可在 GitHub 上的 [dotnet 架構/grpc-適用于 wcf 的開發人員](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample) 存放庫中取得。

## <a name="kubernetes-terminology"></a>Kubernetes 術語

Kubernetes 使用 *預期的狀態* 設定：此 API 可用來描述物件（*例如 pod*、*部署* 和 *服務*），而 *控制平面* 會負責在叢集中的所有 *節點* 上執行所需的 *狀態。* Kubernetes 叢集具有執行 *KUBERNETES API* 的 *主要* 節點，您可以用程式設計方式或使用 `kubectl` 命令列工具進行通訊。 `kubectl` 可以透過命令列引數來建立和管理物件，但它與包含 Kubernetes 物件之宣告資料的 YAML 檔案效果最好。

### <a name="kubernetes-yaml-files"></a>Kubernetes YAML 檔

每個 Kubernetes YAML 檔案至少會有三個最上層屬性：

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

`apiVersion`屬性可用來指定 (的版本，以及檔案所要) 的 API。 `kind`屬性會指定 YAML 所代表的物件類型。 `metadata`屬性包含物件屬性，例如 `name` 、 `namespace` 和 `labels` 。

大部分的 Kubernetes YAML 檔也會有一個 `spec` 區段，描述建立物件所需的資源和設定。

### <a name="pods"></a>Pod

Pod 是 Kubernetes 中的基本執行單位。 他們可以執行多個容器，但也可以用來執行單一容器。 Pod 也包含容器所需的任何儲存體資源，以及網路 IP 位址。

### <a name="services"></a>服務

服務是中繼物件，可描述 pod (或 pod 集合) 並提供在叢集中存取它們的方式，例如使用叢集 DNS 服務將服務名稱對應至一組 pod IP 位址。

### <a name="deployments"></a>部署

部署是 pod 的 *預期狀態* 物件。 如果您以手動方式建立 pod，它就不會在終止時重新開機。 部署是用來告訴叢集哪些 pod 以及這些 pod 的複本數目，應該在目前的時間執行。

### <a name="other-objects"></a>其他物件

Pod、服務和部署只是其中三種最基本的物件類型。 Kubernetes 叢集還管理了許多其他的物件類型。 如需詳細資訊，請參閱 [Kubernetes 概念](https://kubernetes.io/docs/concepts/) 檔。

### <a name="namespaces"></a>命名空間

Kubernetes 叢集的設計目的是要擴充至數百個或數千個節點，並執行類似的服務數目。 為了避免物件名稱之間的衝突，命名空間是用來將物件群組在一起成為較大應用程式的一部分。 Kubernetes 本身的服務會在 `default` 命名空間中執行。 所有使用者物件都應該在自己的命名空間中建立，以避免可能與叢集中的預設物件或其他租使用者發生衝突。

## <a name="get-started-with-kubernetes"></a>開始使用 Kubernetes

如果您正在執行適用于 Windows 的 Docker Desktop 或適用于 Mac 的 Docker Desktop，Kubernetes 已可供使用。 請在 [**設定**] 視窗的 [ **Kubernetes** ] 區段中啟用它：

![在 Docker Desktop 中啟用 Kubernetes](media/kubernetes/enable-kubernetes-docker-desktop-v2.png)

若要在 Linux 上執行本機 Kubernetes 叢集，請考慮使用 [minikube](https://github.com/kubernetes/minikube)或 [MicroK8s](https://microk8s.io/) （如果您的 linux 發行版本支援 [snap](https://snapcraft.io/)）。

若要確認您的叢集正在執行且可供存取，請執行 `kubectl version` 下列命令：

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:50:19Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"19", GitVersion:"v1.19.3", GitCommit:"1e11e4a2108024935ecfcb2912226cedeafd99df", GitTreeState:"clean", BuildDate:"2020-10-14T12:41:49Z", GoVersion:"go1.15.2", Compiler:"gc", Platform:"linux/amd64"}
```

在此範例中， `kubectl` CLI 和 Kubernetes 伺服器都是執行版本1.14.6。 的每個版本 `kubectl` 都應該支援舊版和下一版的伺服器，因此 `kubectl` 1.14 應該也適用于伺服器版本1.13 和1.15。

## <a name="run-services-on-kubernetes"></a>在 Kubernetes 上執行服務

範例應用程式有一個 `kube` 目錄，其中包含三個 YAML 檔案。 檔案會宣告 `namespace.yml` 自訂命名空間： `stocks` 。 此檔案 `stockdata.yml` 會宣告 gRPC 應用程式的部署和服務，而且此檔案 `stockweb.yml` 會宣告使用 gRPC 服務之 ASP.NET CORE 5.0 MVC web 應用程式的部署和服務。

若要搭配使用檔案 `YAML` `kubectl` ，請執行 `apply -f` 下列命令：

```console
kubectl apply -f object.yml
```

此 `apply` 命令會檢查 YAML 檔的有效性，並顯示從 API 收到的任何錯誤，但不會等到檔案中宣告的所有物件都已建立，因為此步驟可能需要一些時間。 使用 `kubectl get` 命令搭配相關的物件類型，以檢查叢集中的物件建立。

### <a name="the-namespace-declaration"></a>命名空間宣告

命名空間宣告很簡單，只需要指派 `name` ：

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

使用 `kubectl` 以套用檔案 `namespace.yml` ，並確認已成功建立命名空間：

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>StockData 應用程式

檔案會宣告 `stockdata.yml` 兩個物件：部署和服務。

#### <a name="the-stockdata-deployment"></a>StockData 部署

YAML 檔的部署部分會提供 `spec` 部署本身的，包括所需的複本數目，以及 `template` 要由部署建立和管理的 Pod 物件的。 請注意，部署物件是由 `apps` API 管理，如中所指定 `apiVersion` ，而不是主要 Kubernetes API。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockdata
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockdata
  replicas: 1
  template:
    metadata:
      labels:
        run: stockdata
    spec:
      containers:
      - name: stockdata
        image: stockdata:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
```

`spec.selector`屬性是用來比對執行中的 pod 與部署。 Pod 的 `metadata.labels` 屬性必須符合屬性， `matchLabels` 否則 API 呼叫將會失敗。

`template.spec`區段會宣告要執行的容器。 當您使用本機 Kubernetes 叢集（例如 Docker Desktop 提供的叢集）時，您可以指定在本機建立的映射（只要它們具有版本戳記）。

> [!IMPORTANT]
> 根據預設，Kubernetes 一律會檢查並嘗試提取新的映射。 如果它在任何已知的儲存機制中找不到映射，Pod 建立將會失敗。 若要使用本機映射，請將設定 `imagePullPolicy` 為 `Never` 。

`ports`屬性會指定應該在 Pod 上發佈的容器埠。 `stockservice`映射會在標準 HTTP 埠上執行服務，因此會發佈埠80。

`resources`區段會將資源限制套用至在 Pod 中執行的容器。 這是很好的作法，因為它會防止個別的 Pod 耗用節點上的所有可用 CPU 或記憶體。

> [!NOTE]
> ASP.NET Core 5.0 已經過優化和調整，可在資源有限的容器中執行。 `dotnet/core/aspnet`Docker 映射會設定環境變數，以告訴 `dotnet` 執行時間它在容器中。

#### <a name="the-stockdata-service"></a>StockData 服務

YAML 檔的服務部分會宣告提供叢集內 pod 存取權的服務。

```yaml
apiVersion: v1
kind: Service
metadata:
  name: stockdata
  namespace: stocks
spec:
  ports:
  - port: 80
  selector:
    run: stockdata
```

這項服務 `spec` `selector` 會使用屬性來比對 `Pods` 執行，在此案例中，尋找具有標籤 `run: stockdata` 的 pod。 在相符 pod 上指定的 `port` 是由命名的服務發行。 在命名空間中執行的其他 pod `stocks` 可以使用做為位址，存取此服務上的 HTTP `http://stockdata` 。 在其他命名空間中執行的 pod 可以使用 `http://stockdata.stocks` 主機名稱。 您可以使用 [網路原則](https://kubernetes.io/docs/concepts/services-networking/network-policies/)來控制跨命名空間的服務存取。

#### <a name="deploy-the-stockdata-application"></a>部署 StockData 應用程式

使用 `kubectl` 以套用檔案 `stockdata.yml` ，並確認已建立部署和服務：

```console
> kubectl apply -f .\stockdata.yml
deployment.apps/stockdata created
service/stockdata created

> kubectl get deployment stockdata --namespace stocks
NAME        READY   UP-TO-DATE   AVAILABLE   AGE
stockdata   1/1     1            1           17s

> kubectl get service stockdata --namespace stocks
NAME        TYPE        CLUSTER-IP      EXTERNAL-IP   PORT(S)   AGE
stockdata   ClusterIP   10.97.132.103   <none>        80/TCP    33s
```

### <a name="the-stockweb-application"></a>StockWeb 應用程式

檔案會宣告 `stockweb.yml` MVC 應用程式的部署和服務。

```yaml
apiVersion: apps/v1
kind: Deployment
metadata:
  name: stockweb
  namespace: stocks
spec:
  selector:
    matchLabels:
      run: stockweb
  replicas: 1
  template:
    metadata:
      labels:
        run: stockweb
    spec:
      containers:
      - name: stockweb
        image: stockweb:1.0.0
        imagePullPolicy: Never
        resources:
          limits:
            cpu: 100m
            memory: 100Mi
        ports:
        - containerPort: 80
        env:
        - name: StockData__Address
          value: "http://stockdata"
        - name: DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT
          value: "true"

---

apiVersion: v1
kind: Service
metadata:
  name: stockweb
  namespace: stocks
spec:
  type: NodePort
  ports:
  - port: 80
  selector:
    run: stockweb
```

#### <a name="environment-variables"></a>環境變數

`env`Deployment 物件的區段會指定要在執行映射的容器中設定的環境變數 `stockweb:1.0.0` 。

**`StockData__Address`** 由於 EnvironmentVariables 設定提供者，環境變數會對應至 `StockData:Address` 設定設定。 此設定會在名稱之間使用雙底線來分隔區段。 位址會使用服務的服務名稱 `stockdata` （在相同的 Kubernetes 命名空間中執行）。

**`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** 環境變數 <xref:System.AppContext> 會設定參數，以啟用的未加密 HTTP/2 連接 <xref:System.Net.Http.HttpClient> 。 此環境變數執行的動作與在程式碼中設定參數相同，如下所示：

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

如果您針對參數使用環境變數，您可以輕鬆地根據應用程式執行所在的內容來變更內容。

#### <a name="service-types"></a>服務類型

`type: NodePort`屬性是用來使 web 應用程式可從叢集外部存取。 此屬性類型會讓 Kubernetes 將服務上的埠80發佈到叢集外部網路通訊端上的任意埠。 您可以使用命令來尋找指派的埠 `kubectl get service` 。

`stockdata`服務不應從叢集外部存取，因此會使用預設類型 `ClusterIP` 。

生產系統很可能會使用整合式負載平衡器，將公用應用程式公開給外部取用者。 以這種方式公開的服務應該使用 `LoadBalancer` 類型。

如需服務類型的詳細資訊，請參閱 [Kubernetes 發行服務](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types) 檔。

#### <a name="deploy-the-stockweb-application"></a>部署 StockWeb 應用程式

使用 `kubectl` 以套用檔案 `stockweb.yml` ，並確認已建立部署和服務：

```console
> kubectl apply -f .\stockweb.yml
deployment.apps/stockweb created
service/stockweb created

> kubectl get deployment stockweb --namespace stocks
NAME       READY   UP-TO-DATE   AVAILABLE   AGE
stockweb   1/1     1            1           8s

> kubectl get service stockweb --namespace stocks
NAME       TYPE       CLUSTER-IP     EXTERNAL-IP   PORT(S)        AGE
stockweb   NodePort   10.106.141.5   <none>        80:32564/TCP   13s
```

命令的輸出 `get service` 顯示 HTTP 埠已發佈至 `32564` 外部網路上的埠。 若為 Docker Desktop，此 IP 位址會是 localhost。 您可以藉由流覽至來存取應用程式 `http://localhost:32564` 。

### <a name="test-the-application"></a>測試應用程式

StockWeb 應用程式會顯示從簡單要求-回復服務取出的 NASDAQ 股票清單。 在此示範中，每一行也會顯示傳回它之服務實例的唯一識別碼。

![StockWeb 螢幕擷取畫面](media/kubernetes/stockweb-screenshot.png)

如果服務的複本數目 `stockdata` 已增加，您可能會預期 **伺服器** 值從行變更為行，但事實上，所有100記錄一律會從相同的實例傳回。 如果您每隔幾秒重新整理頁面，伺服器識別碼會維持不變。 為什麼會這樣呢？ 這裡有兩個因素。

首先，Kubernetes 服務探索系統預設會使用迴圈配置資源負載平衡。 第一次查詢 DNS 伺服器時，它會傳回第一個相符的服務 IP 位址。 下一次，它會傳回清單中的下一個 IP 位址，依此類推，直到結束為止。 屆時，它會迴圈回到一開始。

其次， `HttpClient` 用於 StockWeb 應用程式 gRPC 用戶端的會由 [ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)建立和管理，而且此用戶端的單一實例會用於每次呼叫頁面。 用戶端只會執行一次 DNS 查閱，因此所有要求都會路由至相同的 IP 位址。 而且因為基於 `HttpClientHandler` 效能考慮而快取，所以快速連續的多個要求都會使用相同的 IP 位址，直到快取的 DNS 專案過期或因某些原因處置處理常式實例為止。

結果是 gRPC 服務的預設要求不會在叢集中該服務的所有實例之間平衡。 不同的取用者會使用不同的實例，但這不保證會有良好的要求分配或資源的平衡使用。

下一章的 [服務網格](service-mesh.md)將解決此問題。

>[!div class="step-by-step"]
>[上一個](docker.md) 
>[下一步](service-mesh.md)
