---
title: 適用于 WCF 開發人員的 Kubernetes-gRPC
description: 在 Kubernetes 叢集中執行 ASP.NET Core gRPC 服務。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 3af1b92ade106cf2338816ec69e6b13312681339
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184404"
---
# <a name="kubernetes"></a>Kubernetes

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

雖然可以在 Docker 主機上手動執行容器，但在可靠的生產系統中，最好是使用容器協調流程引擎來管理多個在叢集中多部伺服器執行的實例。 有各種不同的容器協調流程引擎可供使用，包括 Kubernetes、Docker Swarm 和 Apache Mesos。 但在這些引擎中，Kubernetes 遠低於最廣泛使用的，因此將會成為本章的重點。

Kubernetes 包含下列功能：

- **排程**會在叢集內的多個節點上執行容器，確保可用資源的使用量達到平衡，並在發生中斷時讓容器保持運作，以及處理新版本映射或新設定的輪流更新。
- **健全狀況檢查**會監視容器以確保繼續服務。
- **DNS & 服務探索**會處理叢集中服務之間的路由。
- 輸入會從**外部公開選取**的服務，而且通常會提供這些服務實例之間的負載平衡。
- **資源管理**會將儲存體之類的外部資源附加至容器。

本章將詳細說明如何將 ASP.NET Core gRPC 服務和使用此服務的網站部署至 Kubernetes 叢集。 使用的範例應用程式可從 GitHub 上的[RendleLabs/grpc-wcf 開發人員存放庫取得。](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/KubernetesSample)

## <a name="kubernetes-terminology"></a>Kubernetes 術語

Kubernetes 會使用*預期狀態*設定：此 API 可用來描述 pod、*部署*和*服務*等*物件，而* *控制平面*會負責在所有節點上執行所需的狀態*在叢集中。* Kubernetes 叢集具有執行*Kubernetes API*的`kubectl` *主要*節點，可以透過程式設計方式或使用命令列工具來進行通訊。 `kubectl`可以使用命令列引數來建立和管理物件，但最適合用於包含 Kubernetes 物件之宣告資料的 YAML 檔案。

### <a name="kubernetes-yaml-files"></a>Kubernetes YAML 檔

每個 Kubernetes YAML 檔至少會有三個最上層屬性。

```yaml
apiVersion: v1
kind: Namespace
metadata:
  # Object properties
```

`apiVersion`屬性是用來指定檔案的目標版本（以及哪個 API）。 `kind`屬性會指定 YAML 代表的物件種類。 屬性包含物件屬性`name`，例如、 `namespace`或`labels`。 `metadata`

大部分的 Kubernetes YAML 檔案也會有`spec`一個區段，描述建立物件所需的資源和設定。

### <a name="pods"></a>Pod

Pod 是 Kubernetes 中的基本執行單位。 它們可以執行多個容器，但也會用來執行單一容器。 Pod 也包含容器所需的任何儲存體資源，以及網路 IP 位址。

### <a name="services"></a>服務

服務是一種中繼物件，可描述 pod （或 pod 集），並提供在叢集中存取它們的方式，例如使用叢集 DNS 服務將服務名稱對應至一組 pod IP 位址。

### <a name="deployments"></a>部署

部署是適用于 pod 的*說明狀態*物件。 如果您手動建立 Pod，當它終止時，將不會重新開機。 部署是用來告訴叢集哪些 pod，以及這些 pod 的多少複本應該在目前的時間執行。

### <a name="other-objects"></a>其他物件

Pod、服務和部署只是其中三個最基本的物件類型。 Kubernetes 叢集會管理數十種其他類型的物件。 如需詳細資訊，請參閱[Kubernetes 概念](https://kubernetes.io/docs/concepts/)檔。

### <a name="namespaces"></a>命名空間

Kubernetes 叢集的設計是要擴充至數百個或數千個節點，並執行類似的服務數目。 為了避免物件名稱之間的衝突，命名空間是用來將物件群組在一起，以作為較大應用程式的一部分。 Kubernetes 本身的`default`服務會在命名空間中執行。 所有使用者物件都應該建立在自己的命名空間中，以避免可能與叢集中的預設物件或其他租使用者衝突。

## <a name="get-started-with-kubernetes"></a>開始使用 Kubernetes

如果您執行的是適用于 Windows 或 macOS 的 Docker Desktop，Kubernetes 已經可以使用。 只要在 [設定] 視窗的 [Kubernetes] 區段中啟用它即可。

![在 Docker Desktop 中啟用 Kubernetes](media/kubernetes/enable-kubernetes-docker-desktop.png)

若要在 Linux 中執行本機 Kubernetes 叢集，請查看[minikube](https://github.com/kubernetes/minikube)或[MicroK8s](https://microk8s.io/) （如果您的 linux 發行版本支援[snap](https://snapcraft.io/)）。

若要檢查您的叢集是否正在執行且可供`kubectl version`存取，請執行命令。

```console
kubectl version
Client Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:13:49Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"windows/amd64"}
Server Version: version.Info{Major:"1", Minor:"14", GitVersion:"v1.14.6", GitCommit:"96fac5cd13a5dc064f7d9f4f23030a6aeface6cc", GitTreeState:"clean", BuildDate:"2019-08-19T11:05:16Z", GoVersion:"go1.12.9", Compiler:"gc", Platform:"linux/amd64"}
```

在此範例中， `kubectl` CLI 和 Kubernetes 伺服器都是執行版本1.14.6。 的`kubectl`每個版本都應該支援伺服器的上一個和下一個版本，因此`kubectl` 1.14 也應該與伺服器版本1.13 和1.15 搭配運作。

## <a name="run-services-on-kubernetes"></a>在 Kubernetes 上執行服務

範例應用程式有一個`kube`包含三個 YAML 檔案的目錄。 檔案會宣告自訂`stocks`命名空間。 `namespace.yml` 檔案會宣告 gRPC 應用程式的部署和服務，而此`stockweb.yml`檔案會針對使用 gRPC 服務的 ASP.NET Core 3.0 MVC web 應用程式宣告部署和服務。 `stockdata.yml`

若要使用`YAML` `kubectl`檔案搭配，請使用`apply -f`命令。

```console
kubectl apply -f object.yml
```

此`apply`命令會檢查 YAML 檔案的有效性，並顯示從 API 收到的任何錯誤，但不會等到檔案中宣告的所有物件都已建立，因為這可能需要一些時間。 `kubectl get`使用命令搭配相關的物件類型，以檢查叢集中的物件建立。

### <a name="the-namespace-declaration"></a>命名空間宣告

命名空間宣告很簡單，而且只需要`name`指派。

```yaml
apiVersion: v1
kind: Namespace
metadata:
  name: stocks
```

使用`kubectl` 來`namespace.yml`套用檔案，並檢查是否已成功建立命名空間。

```console
> kubectl apply -f namespace.yml
namespace/stocks created

> kubectl get namespaces
NAME              STATUS   AGE
stocks            Active   2m53s
```

### <a name="the-stockdata-application"></a>StockData 應用程式

`stockdata.yml`檔案會宣告兩個物件：部署和服務。

#### <a name="the-stockdata-deployment"></a>StockData 部署

部署元件會`spec`為部署本身提供，包括所需的複本數目， `template`以及要由部署建立和管理 Pod 物件的。 請注意，部署物件是使用`apps` API 來管理，如中`apiVersion`所指定，而不是主要的 Kubernetes API。

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

`spec.selector`屬性會用來比對執行中的 pod 與部署。 Pod 的`metadata.labels`屬性必須符合屬性， `matchLabels`否則 API 呼叫將會失敗。

`template.spec`區段會宣告要執行的容器。 使用本機 Kubernetes 叢集（例如 Docker Desktop 提供的叢集）時，您可以指定在本機建立的映射，只要它們有版本戳記即可。

> [!IMPORTANT]
> 根據預設，Kubernetes 一律會檢查並嘗試提取新的映射。 如果它在其已知的存放庫中找不到映射，Pod 建立將會失敗。 若要使用本機影像，請將`imagePullPolicy`設定`Never`為。

`ports`屬性會指定要在 Pod 上發佈的容器埠。  `stockservice`映射會在標準 HTTP 埠上執行服務，因此會發佈埠80。

`resources`區段會將資源限制套用至在 pod 中執行的容器。 這是很好的作法，因為它會防止個別 pod 耗用節點上的所有可用 CPU 或記憶體。

> [!NOTE]
> ASP.NET Core 3.0 已優化並微調為在資源限制的容器中執行，且`dotnet/core/aspnet` Docker 映射會設定環境變數，以`dotnet`告知執行時間其位於容器中。

#### <a name="the-stockdata-service"></a>StockData 服務

YAML 檔案的服務部分會宣告服務，以提供對叢集中 pod 的存取權。

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

服務規格會使用`selector`屬性來比對`Pods`執行，在此情況下，會尋找具有卷`run: stockdata`標的 pod。 在相符`port` pod 上指定的會由已命名的服務發行。 在命名空間中執行`stocks`的其他 pod 可以使用`http://stockdata`作為位址，在此服務上存取 HTTP。 在其他命名空間中執行的`http://stockdata.stocks` pod 可以使用主機名稱。 您可以使用[網路原則](https://kubernetes.io/docs/concepts/services-networking/network-policies/)來控制跨命名空間服務存取。

#### <a name="deploy-the-stockdata-application"></a>部署 StockData 應用程式

使用`kubectl` 來`stockdata.yml`套用檔案，並檢查是否已建立部署和服務。

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

`stockweb.yml`檔案會宣告 MVC 應用程式的部署和服務。

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

部署`env`物件的區段會指定要在執行`stockweb:1.0.0`映射的容器中設定的環境變數。

由於 EnvironmentVariables 設定提供者的不同`StockData:Address` ，**環境變數將會對應到configuration設定。`StockData__Address`** 此設定會在名稱之間使用雙底線來分隔區段。 此位址會使用`stockdata`服務的服務名稱，這會在相同的 Kubernetes 命名空間中執行。

環境變數會<xref:System.AppContext>設定參數，以啟用的<xref:System.Net.Http.HttpClient>未加密 HTTP/2 連接。 **`DOTNET_SYSTEM_NET_HTTP_SOCKETSHTTPHANDLER_HTTP2UNENCRYPTEDSUPPORT`** 此環境變數相當於在程式碼中設定參數，如下所示。

```csharp
AppContext.SetSwitch("System.Net.Http.SocketsHttpHandler.Http2UnencryptedSupport", true);
```

針對參數使用環境變數，表示可以根據應用程式執行所在的內容，輕鬆地變更設定。

#### <a name="service-types"></a>服務類型

若要讓 Web 應用程式可從叢集外部存取， `type: NodePort`則會使用屬性。 此屬性類型會導致 Kubernetes 將服務上的埠80發佈至叢集的外部網路通訊端上的任意埠。 您可以使用`kubectl get service`命令來尋找指派的埠。

服務不應可從叢集外部存取，因此會使用預設`ClusterIP`類型。 `stockdata`

生產系統很可能會使用整合式負載平衡器向外部取用者公開公用應用程式。 以這種方式公開的服務應該`LoadBalancer`使用型別。

如需有關服務類型的詳細資訊，請參閱[Kubernetes 的發佈服務](https://kubernetes.io/docs/concepts/services-networking/service/#publishing-services-service-types)檔。

#### <a name="deploy-the-stockweb-application"></a>部署 StockWeb 應用程式

使用`kubectl` 來`stockweb.yml`套用檔案，並檢查是否已建立部署和服務。

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

`get service`命令的輸出顯示 HTTP 埠已發佈至外部網路上的埠`32564` ; 針對 Docker Desktop，這會是 localhost。 您可以流覽至來`http://localhost:32564`存取應用程式。

### <a name="testing-the-application"></a>測試應用程式

StockWeb 應用程式會顯示從簡單的要求-回復服務中取出的 NASDAQ 股票清單。 基於示範目的，每一行也會顯示傳回它之服務實例的唯一識別碼。

![StockWeb 螢幕擷取畫面](media/kubernetes/stockweb-screenshot.png)

如果`stockdata`服務的複本數目已增加，您可能會預期**伺服器**值從行變更為行，但事實上，所有100記錄一律會從相同的實例傳回。 如果您每隔幾秒鐘就重新整理頁面，伺服器識別碼會維持不變。 為什麼會發生這種情況？ 這裡有兩個因素。

首先，Kubernetes 服務探索系統預設會使用「迴圈配置資源」負載平衡。 第一次查詢 DNS 伺服器時，它會傳回服務的第一個相符的 IP 位址。 下一次是清單中的下一個 IP 位址，依此類推，直到結束為止，然後才會迴圈回到開始位置。

第二， `HttpClient`用於 StockWeb 應用程式的 gRPC 用戶端的會由[ASP.NET Core HttpClientFactory](../microservices/implement-resilient-applications/use-httpclientfactory-to-implement-resilient-http-requests.md)建立和管理，而這個用戶端的單一實例會用於每次呼叫頁面。 用戶端只會執行一個 DNS 查閱，因此所有要求都會路由傳送至相同的 IP 位址。 此外，因為`HttpClientHandler`會基於效能考慮而快取，所以快速連續的多個要求*全都*會使用相同的 IP 位址，直到快取的 DNS 專案到期，或因某些原因處置處理常式實例為止。

這表示根據預設，gRPC 服務的要求不會在叢集中該服務的所有實例之間平衡。 不同的取用者會使用不同的實例，但這並不保證會有良好的要求散發和平衡的資源使用。

下一章的[服務網格](service-mesh.md)將探討如何解決此問題。

>[!div class="step-by-step"]
>[上一頁](docker.md)
>[下一頁](service-mesh.md)
