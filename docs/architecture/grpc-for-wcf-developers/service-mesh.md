---
title: 服務網格-適用于 WCF 開發人員的 gRPC
description: 使用服務網格來路由傳送要求，並對 Kubernetes 叢集中的 gRPC 服務進行平衡。
ms.date: 12/15/2020
ms.openlocfilehash: a1c72a4facf1c133af912bbee242328653a051b6
ms.sourcegitcommit: 655f8a16c488567dfa696fc0b293b34d3c81e3df
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/06/2021
ms.locfileid: "97938126"
---
# <a name="service-meshes"></a>服務網格

服務網格是一種基礎結構元件，可控制網路內的路由服務要求。 服務網格可以處理 Kubernetes 叢集中的各種網路層級問題，包括：

- 服務探索
- 負載平衡
- 容錯
- 加密
- 監視

Kubernetes 服務網格的運作方式是將額外的容器（稱為 *側車 proxy*）新增至網格中包含的每個 pod。 Proxy 會處理所有的輸入和輸出網路要求。 然後，您可以讓網路的設定和管理工作與應用程式容器分開。 在許多情況下，此分隔不需要對應用程式程式碼進行任何變更。

在 [上一章的範例](kubernetes.md#test-the-application)中，web 應用程式的 gRPC 要求都會路由傳送至 gRPC 服務的單一實例。 發生這種情況是因為服務的主機名稱已解析為 IP 位址，且該 IP 位址會在實例的存留期內快取 `HttpClientHandler` 。 您可以手動處理 DNS 查閱或建立多個用戶端，以解決這種行為。 但此因應措施會使應用程式程式碼變得複雜，而不會增加任何商務或客戶價值。

當您使用服務網格時，來自應用程式容器的要求會傳送至側車 proxy。 然後，側車 proxy 可以在其他服務的所有實例上以智慧方式散發它們。 網格也可以：

- 順暢地回應服務的個別實例失敗。
- 處理失敗呼叫或超時的重試語義。
- 將失敗的要求重新路由傳送至替代的實例，而不傳回用戶端應用程式。

下列螢幕擷取畫面顯示以 Linkerd 服務網格執行的 StockWeb 應用程式。 應用程式程式碼沒有任何變更，也沒有使用 Docker 映射。 唯一需要的變更是在和服務的 YAML 檔中，將批註新增至部署 `stockdata` `stockweb` 。

![StockWeb 與服務網格](media/service-mesh/stockweb-servicemesh-screenshot.png)

您可以從 [ **伺服器** ] 資料行看到 StockWeb 應用程式的要求已路由傳送至 StockData 服務的這兩個複本，儘管是源自 `HttpClient` 應用程式程式碼中的單一實例。 事實上，如果您檢查程式碼，就會看到 StockData 服務的所有100要求都是使用相同的實例同時進行 `HttpClient` 。 使用服務網格時，這些要求將會平衡，不過有許多可用的服務實例。

服務網格只適用于叢集中的流量。 若為外部用戶端，請參閱下一章的 [負載平衡](load-balancing.md)。

## <a name="service-mesh-options"></a>服務網格選項

目前有三種一般用途的服務網狀架構可與 Kubernetes 搭配使用： [Istio](https://istio.io)、 [Linkerd](https://linkerd.io)和 [Consul Connect](https://consul.io/mesh.html)。 這三個都提供要求路由/proxy 處理、流量加密、復原、主機對主機驗證，以及流量控制。

選擇服務網格取決於多個因素：

- 組織對成本、合規性、付費支援方案等方面的特定需求。
- 叢集的本質、其大小、部署的服務數目，以及叢集網路內的流量量。
- 輕鬆地部署和管理網格，並將其與服務搭配使用。

## <a name="example-add-linkerd-to-a-deployment"></a>範例：將 Linkerd 新增至部署

在此範例中，您將瞭解如何使用 Linkerd 服務網格與 [上一節](kubernetes.md)中的 *StockKube* 應用程式。
若要遵循此範例，您必須 [安裝 LINKERD CLI](https://linkerd.io/2/getting-started/#step-1-install-the-cli)。 您可以從列出 GitHub 版本的區段下載 Windows 二進位檔。 請務必使用最新的 *穩定* 版本，而不是其中一個 edge 版本。

安裝 Linkerd CLI 之後，請遵循 [消費者入門](https://linkerd.io/2/getting-started/index.html) 指示，在您的 Kubernetes 叢集上安裝 Linkerd 元件。 這些指示很簡單，而安裝只需要幾分鐘的時間就可以在本機 Kubernetes 實例上執行。

### <a name="add-linkerd-to-kubernetes-deployments"></a>將 Linkerd 新增至 Kubernetes 部署

Linkerd CLI 提供 `inject` 命令，以將必要的區段和屬性新增至 Kubernetes 檔案。 您可以執行命令，並將輸出寫入至新的檔案。

```console
linkerd inject stockdata.yml > stockdata-with-mesh.yml
linkerd inject stockweb.yml > stockweb-with-mesh.yml
```

您可以檢查新的檔案，以查看已進行的變更。 針對部署物件，會加入中繼資料注釋，以告知 Linkerd 在建立時將側車 proxy 容器插入至 pod。

您也可以透過管線將命令的輸出 `linkerd inject` 直接傳送到 `kubectl` 。 下列命令可在 PowerShell 或任何 Linux shell 中運作。

```console
linkerd inject stockdata.yml | kubectl apply -f -
linkerd inject stockweb.yml | kubectl apply -f -
```

### <a name="inspect-services-in-the-linkerd-dashboard"></a>檢查 Linkerd 儀表板中的服務

使用 CLI 開啟 Linkerd 儀表板 `linkerd` 。

```console
linkerd dashboard
```

儀表板會提供與網格連接的所有服務相關的詳細資訊。

![顯示 StockKube 應用程式的 Linkerd 儀表板](media/service-mesh/linkerd-screenshot.png)

如果您增加 StockData gRPC 服務的複本數目（如下列範例所示），並重新整理瀏覽器中的 [StockWeb] 頁面，您應該會在 [ **伺服器** ] 資料行中看到混合的識別碼。 這種混合表示所有可用的實例都為要求提供服務。

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
>[上一個](kubernetes.md) 
>[下一步](load-balancing.md)
