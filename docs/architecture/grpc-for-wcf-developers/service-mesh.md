---
title: 服務網格-適用于 WCF 開發人員的 gRPC
description: 使用服務網格來路由傳送要求，並將其與 Kubernetes 叢集中的 gRPC 服務進行平衡。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 7fc80b95937dab9153b72aa6bc8da90f6453779f
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184089"
---
# <a name="service-meshes"></a>服務網格

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

「服務網格」是一種基礎結構元件，可控制網路內的路由服務要求。 服務網格可以處理 Kubernetes 叢集內的各種網路層級問題，包括：

- 服務探索
- 負載平衡
- 容錯
- 加密
- 監視

Kubernetes 服務網格的工作是將額外的容器（稱為*側車 proxy*）新增至網格中包含的每個 pod。 Proxy 會接管處理所有的輸入和輸出網路要求，讓網路的設定和管理與應用程式容器保持分開，而且在許多情況下，不需要對應用程式程式碼進行任何變更。

請使用[上一章的範例](kubernetes.md#testing-the-application)，其中 web 應用程式的 gRPC 要求全都路由傳送至 gRPC 服務的單一實例。 之所以會發生這種情況，是因為服務的主機名稱解析為 ip 位址，而該 ip 位址會在`HttpClientHandler`實例的存留期內快取。 您可以藉由手動處理 DNS 查閱或建立多個用戶端來解決此情況，但這會大幅增加應用程式的程式碼，而不需要新增任何商業或客戶價值。

使用服務網格時，會將來自應用程式容器的要求傳送至側車 proxy，以智慧方式在其他服務的所有實例之間散發。 網格也可以：

- 無縫回應服務的個別實例失敗。
- 處理失敗呼叫或超時的重試語義
- 將失敗的要求重新路由至其他實例，完全不需要返回用戶端應用程式。

下列螢幕擷取畫面顯示使用 Linkerd 服務網格執行的 StockWeb 應用程式，不會變更應用程式程式碼，甚至是使用中的 Docker 映射。 唯一需要的變更是在`stockdata`和`stockweb`服務的 YAML 檔中，新增對部署的注釋。

![使用服務網格的 StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

您可以從 [伺服器] 資料行看到，來自 StockWeb 應用程式的要求已路由傳送至 StockData 服務的兩個複本，儘管是源自`HttpClient`應用程式代碼中的單一實例。 事實上，如果您檢查程式碼，您會看到 StockData 服務的所有100要求都是使用相同`HttpClient`的實例同時進行，但是在服務網格中，這些要求將會在許多服務實例可供使用的情況下平衡。

服務網格僅適用于叢集中的流量。 若是外部用戶端，請參閱[下一章的負載平衡](load-balancing.md)。

## <a name="service-mesh-options"></a>服務網格選項

目前有三個一般用途的服務網格實現可與 Kubernetes 搭配使用：Istio、Linkerd 和 Consul Connect。 這三個都提供要求路由/代理、流量加密、復原、主機對主機驗證，以及流量控制。

選擇服務網格取決於多個因素： 

- 組織對於成本、合規性、付費支援方案等方面的特定需求。 
- 叢集的本質、其大小、已部署的服務數量，以及叢集網路內的流量量。
- 輕鬆部署和管理網格，並將其與服務搭配使用。

每個服務網格的詳細資訊都可從其各自的網站取得。

- [**Istio** -istio.io](https://istio.io)
- [**Linkerd** -linkerd.io](https://linkerd.io)
- [**Consul** -consul.io/mesh.html](https://consul.io/mesh.html)

## <a name="example-add-linkerd-to-a-deployment"></a>範例：將 Linkerd 新增至部署

在此範例中，您將瞭解如何搭配[上一節](kubernetes.md)的*StockKube*應用程式使用 Linkerd 服務網格。
若要遵循此範例，您必須[安裝 LINKERD CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli)。 您可以從 GitHub 版本區段下載 Windows 二進位檔;請務必使用最新的**穩定**版本，而不是其中一個 edge 版本。

安裝 Linkerd CLI 之後，請遵循 Linkerd 網站上的 [*消費者入門*指示]，在您的 Kubernetes 叢集上安裝 Linkerd 元件。 指示是直接的，而安裝只需要幾分鐘的時間，就能在本機 Kubernetes 實例上執行。

### <a name="add-linkerd-to-kubernetes-deployments"></a>將 Linkerd 新增至 Kubernetes 部署

Linkerd CLI 會提供一個`inject`命令，將必要的區段和屬性新增至 Kubernetes 檔案。 您可以執行命令，並將輸出寫入新的檔案。

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

您可以檢查新的檔案，以查看已進行的變更。 針對部署物件，會新增中繼資料注釋，告訴 Linkerd 在建立時將側車 proxy 容器插入 Pod 中。

也可以直接將`linkerd inject`命令的輸出傳送至。 `kubectl` 下列命令可在 PowerShell 或任何 Linux shell 中使用。

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>在 Linkerd 儀表板中檢查服務

使用`linkerd` CLI 啟動 Linkerd 儀表板。

```console
linkerd dashboard
```

儀表板會提供連接到網格的所有服務的詳細資訊。

![顯示 StockKube 應用程式的 Linkerd 儀表板](media/service-mesh/linkerd-screenshot.png)

如果您增加 StockData gRPC 服務的複本數目（如下列範例所示），並在瀏覽器中重新整理 StockWeb 頁面，您應該會在 [伺服器] 資料行中看到識別碼的混合，表示所有可用的實例都已提供要求.

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
  replicas: 2 # Increase the target number of instances
  template:
    metadata:
      annotations:
        linkerd.io/inject: enabled
      creationTimestamp: null
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

>[!div class="step-by-step"]
>[上一頁](kubernetes.md)
>[下一頁](load-balancing.md)
