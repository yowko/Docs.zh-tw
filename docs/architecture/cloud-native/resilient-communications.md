---
title: 具有復原性的通訊
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |復原通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 33e4c03c1f3d8c01f72c588326fbb0bdfa512cdd
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613742"
---
# <a name="resilient-communications"></a>復原通訊

在本書中，我們採用了以微服務為基礎的架構方法。 雖然這類架構提供重要的優點，但卻帶來許多挑戰：

- *跨進程的網路通訊。* 每個微服務都會透過網路通訊協定進行通訊，這會引進網路擁塞、延遲和暫時性錯誤。

- *服務探索。* 在具有自己的 IP 位址和埠的電腦叢集上執行時，微服務會如何探索彼此，並彼此通訊？

- *恢復.* 如何管理短期失敗並讓系統穩定？

- *負載平衡。* 輸入流量如何分散到微服務的多個實例？

- *安全級.* 如何強制執行傳輸層級加密和憑證管理等安全性考慮？

- *分散式監視。* -如何在多個取用微服務中相互關聯和取得單一要求的可追蹤性和監視？

您可以使用不同的程式庫和架構來解決這些問題，但執行的成本很高、複雜且耗時。 最後，您也會得到結合商務邏輯的基礎結構顧慮。

## <a name="service-mesh"></a>服務網格

較佳的方法是一種已發展的*服務網格*技術。 [服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一個可設定的基礎結構層，具有可處理服務通訊的內建功能，以及前述的其他挑戰。 它會將這些考慮移到服務 proxy 中，以將這些顧慮分離。 Proxy 會部署到個別的進程（稱為[側車](https://docs.microsoft.com/azure/architecture/patterns/sidecar)），以提供與商務程式碼的隔離。 不過，側車會連結至服務-它是使用它建立的，並且會共用其生命週期。 圖6-7 顯示這種情況。

![具有側車的服務網格](./media/service-mesh-with-side-car.png)

**圖 6-7**。 具有側車的服務網格

在上圖中，請注意 proxy 如何攔截及管理微服務與叢集之間的通訊。

服務網格會以邏輯方式分割成兩個不同的元件：[資料平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)和[控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。 圖6-8 顯示這些元件及其責任。

![服務網格控制項和資料平面](./media/istio-control-and-data-plane.png)

**圖6-8。** 服務網格控制項和資料平面

設定好之後，服務網格就能發揮高功能。 它可以從服務探索端點取得對應的實例集區。 然後，網格可以將要求傳送至特定實例，並記錄結果的延遲和回應類型。 網格可以根據許多因素（包括觀察到最近要求的延遲），選擇最有可能傳回快速回應的實例。

如果實例沒有回應或失敗，網格將會重試另一個實例上的要求。 如果傳回錯誤，則網格會從負載平衡集區收回實例，並在修復之後加以重新聲明。 如果要求超時，網格可能會失敗，然後重試要求。 網格會在集中式計量系統上捕捉併發出計量和分散式追蹤。

## <a name="istio-and-envoy"></a>Istio 和 Envoy

雖然目前有一些服務網格選項存在，但[Istio](https://istio.io/docs/concepts/what-is-istio/)在撰寫本文時是最受歡迎的。 Istio 是 IBM、Google 和 Lyft 司機的聯合風險。 它是一個開放原始碼的供應專案，可以整合到新的或現有的分散式應用程式中。 這項技術提供一致且完整的解決方案來保護、連接和監視微服務。 其功能包括：

- 在具有強式身分識別型驗證和授權的叢集中，保護服務對服務的通訊。
- HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量的自動負載平衡。
- 使用豐富的路由規則、重試、容錯移轉和錯誤插入來精細控制流量行為。
- 可插入的原則層和設定 API，支援存取控制、速率限制和配額。
- 叢集中所有流量的自動計量、記錄和追蹤，包括叢集輸入和輸出。

Istio 執行的主要元件是具有[Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)資格的 proxy 服務。 它會與每個服務一起執行，並為下列功能提供平臺中立的基礎：

- 動態服務探索。
- 負載平衡。
- TLS 終止。
- HTTP 和 gRPC proxy。
- 斷路器復原功能。
- 健康情況檢查。
- [使用未](https://martinfowler.com/bliki/CanaryRelease.html)通過部署的輪流更新。

如先前所討論，Envoy 會以側車的形式部署至叢集中的每個微服務。

## <a name="integration-with-azure-kubernetes-services"></a>與 Azure Kubernetes Services 整合

Azure 雲端採用 Istio，並在 Azure Kubernetes Services 中提供對其的直接支援。 下列連結可協助您開始使用：

- [在 AKS 中安裝 Istio](https://docs.microsoft.com/azure/aks/istio-install)
- [使用 AKS 和 Istio](https://docs.microsoft.com/azure/aks/istio-scenario-routing)

### <a name="references"></a>參考

- [Polly](http://www.thepollyproject.org/)

- [重試模式](https://docs.microsoft.com/azure/architecture/patterns/retry)

- [斷路器模式](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)

- [Azure 中的復原技術白皮書](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [網路延遲](https://www.techopedia.com/definition/8553/network-latency)

- [備援性](https://docs.microsoft.com/azure/architecture/guide/design-principles/redundancy)

- [異地複寫](https://docs.microsoft.com/azure/sql-database/sql-database-active-geo-replication)

- [Azure 流量管理員](https://docs.microsoft.com/azure/traffic-manager/traffic-manager-overview)

- [自動調整指引](https://docs.microsoft.com/azure/architecture/best-practices/auto-scaling)

- [Istio](https://istio.io/docs/concepts/what-is-istio/)

- [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
>[上一個](infrastructure-resiliency-azure.md) 
>[下一步](monitoring-health.md)
