---
title: 服務網格-適用于 WCF 開發人員的 gRPC
description: 使用服務網格來路由傳送要求，並將其與 Kubernetes 叢集中的 gRPC 服務進行平衡。
ms.date: 09/02/2019
ms.openlocfilehash: a29d6893e585c7eb60c847cef0149afeeaebcdab
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77503394"
---
# <a name="service-meshes"></a>服務網格

「服務網格」是一種基礎結構元件，可控制網路內的路由服務要求。 服務網格可以處理 Kubernetes 叢集內的各種網路層級問題，包括：

- 服務探索
- 負載平衡
- 容錯
- 加密
- 監視

Kubernetes 服務網格的工作是將額外的容器（稱為*側車 proxy*）新增至網格中包含的每個 pod。 Proxy 會接管處理所有的輸入和輸出網路要求。 接著，您可以繼續設定和管理網路功能，與應用程式容器分開。 在許多情況下，這種分隔並不需要對應用程式程式碼進行任何變更。

在[上一章的範例](kubernetes.md#test-the-application)中，來自 web 應用程式的 gRPC 要求全都會路由傳送至 gRPC 服務的單一實例。 發生這種情況是因為服務的主機名稱解析為 IP 位址，而該 IP 位址會在 `HttpClientHandler` 實例的存留期內快取。 您可以手動處理 DNS 查閱或建立多個用戶端，藉此解決此情況。 但這種因應措施會使應用程式代碼複雜化，而不會增加任何商業或客戶價值。

當您使用服務網格時，來自應用程式容器的要求會傳送至側車 proxy。 然後，側車 proxy 就可以在其他服務的所有實例中，以智慧方式散發它們。 網格也可以：

- 無縫回應服務的個別實例失敗。
- 處理失敗呼叫或超時的重試語法。
- 將失敗的要求重新路由傳送至替代實例，而不需要返回用戶端應用程式。

下列螢幕擷取畫面顯示使用 Linkerd 服務網格執行的 StockWeb 應用程式。 應用程式代碼不會有任何變更，而且不會使用 Docker 映射。 唯一需要的變更是在 `stockdata` 和 `stockweb` 服務的 YAML 檔中，加入部署的注釋。

![使用服務網格的 StockWeb](media/service-mesh/stockweb-servicemesh-screenshot.png)

您可以從 [**伺服器**] 資料行看到，來自 StockWeb 應用程式的要求已路由傳送至 StockData 服務的兩個複本，儘管是來自應用程式代碼中的單一 `HttpClient` 實例。 事實上，如果您檢查程式碼，您會看到 StockData 服務的所有100要求都是使用相同的 `HttpClient` 實例同時進行。 使用服務網格時，這些要求將會平衡，不過有許多服務實例可供使用。

服務網格僅適用于叢集中的流量。 若是外部用戶端，請參閱下一章的[負載平衡](load-balancing.md)。

## <a name="service-mesh-options"></a>服務網格選項

目前有三個一般用途的服務網格實作為可與 Kubernetes 搭配使用： [Istio](https://istio.io)、 [Linkerd](https://linkerd.io)和[Consul Connect](https://consul.io/mesh.html)。 這三個都提供要求路由/代理、流量加密、復原、主機對主機驗證，以及流量控制。

選擇服務網格取決於多個因素：

- 組織對於成本、合規性、付費支援方案等方面的特定需求。
- 叢集的本質、其大小、已部署的服務數量，以及叢集網路內的流量量。
- 輕鬆部署和管理網格，並將其與服務搭配使用。

## <a name="example-add-linkerd-to-a-deployment"></a>範例：將 Linkerd 新增至部署

在此範例中，您將瞭解如何搭配[上一節](kubernetes.md)的*StockKube*應用程式使用 Linkerd 服務網格。
若要遵循此範例，您必須[安裝 LINKERD CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli)。 您可以從列出 GitHub 版本的區段下載 Windows 二進位檔。 請務必使用最新的*穩定*版本，而不是其中一個 edge 版本。

安裝 Linkerd CLI 之後，請遵循[消費者入門](https://linkerd.io/2/getting-started/index.html)指示，在 Kubernetes 叢集上安裝 Linkerd 元件。 這些指示很簡單，而且在本機 Kubernetes 實例上安裝應該只需要幾分鐘的時間。

### <a name="add-linkerd-to-kubernetes-deployments"></a>將 Linkerd 新增至 Kubernetes 部署

Linkerd CLI 會提供 `inject` 命令，將必要的區段和屬性新增至 Kubernetes 檔案。 您可以執行命令，並將輸出寫入新的檔案。

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

您可以檢查新的檔案，以查看已進行的變更。 針對部署物件，會新增中繼資料注釋，告訴 Linkerd 在建立時將側車 proxy 容器插入 pod 中。

也可以透過管道將 `linkerd inject` 命令的輸出傳送至直接 `kubectl`。 下列命令可在 PowerShell 或任何 Linux shell 中使用。

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>在 Linkerd 儀表板中檢查服務

使用 `linkerd` CLI 開啟 [Linkerd] 儀表板。

```console
linkerd dashboard
```

儀表板會提供連接到網格的所有服務的詳細資訊。

![顯示 StockKube 應用程式的 Linkerd 儀表板](media/service-mesh/linkerd-screenshot.png)

如果您增加 StockData gRPC 服務的複本數目（如下列範例所示），並在瀏覽器中重新整理 [StockWeb] 頁面，您應該會在 [**伺服器**] 資料行中看到識別碼的混合。 這種混合表示所有可用的實例都是提供要求。

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
