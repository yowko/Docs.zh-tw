---
title: 具有復原性的通訊
description: 設計適用于 Azure 的雲端原生 .NET 應用程式 |復原通訊
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 18b26223634efc5c05f680d0cbb7c8cbc2490a59
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91166036"
---
# <a name="resilient-communications"></a>復原通訊

在本書中，我們採用了以微服務為基礎的架構方法。 雖然這類架構提供重要的優點，但卻帶來許多挑戰：

- *跨進程網路通訊。* 每個微服務都會透過網路通訊協定進行通訊，而這些網路通訊協定會引進網路擁塞、延遲和暫時性錯誤。

- *服務探索。* 在具有自己的 IP 位址和埠的電腦叢集上執行時，微服務如何探索和彼此通訊？

- *彈性。* 您要如何管理短期失敗並讓系統穩定？

- *負載平衡。* 輸入流量如何分散到微服務的多個實例？

- *安全性。* 如何強制執行傳輸層級加密和憑證管理等安全性問題？

- *分散式監視。* -您如何在多個取用微服務之間相互關聯和捕捉單一要求的可追蹤性和監視？

您可以使用不同的程式庫和架構來解決這些問題，但其實作可能很耗費資源、複雜且耗時。 您最後也會有與商務邏輯結合的基礎結構考慮。

## <a name="service-mesh"></a>服務網格

更好的方法是具有 *服務網格*的不斷演進技術。 [服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是可設定的基礎結構層，具有可處理服務通訊的內建功能，以及上述的其他挑戰。 它會將這些考慮移至服務 proxy，以分離這些問題。 Proxy 會部署到個別的進程 (稱為 [側車](/azure/architecture/patterns/sidecar)) ，以提供與商務程式碼的隔離。 不過，側車會連結至服務-它會使用它建立並共用其生命週期。 圖6-7 顯示此案例。

![具有側面汽車的服務網格](./media/service-mesh-with-side-car.png)

**圖 6-7**。 具有側面汽車的服務網格

在上圖中，請注意 proxy 如何攔截及管理微服務與叢集之間的通訊。

服務網格會以邏輯方式分割成兩個不同的元件：一個 [資料平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc) 和一個 [控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。 圖6-8 顯示這些元件及其責任。

![服務網格控制項和資料平面](./media/istio-control-and-data-plane.png)

**圖6-8。** 服務網格控制項和資料平面

一旦設定之後，服務網格會具有高功能。 它可以從服務探索端點取出對應的實例集區。 然後，網格可以將要求傳送至特定的實例，記錄結果的延遲和回應類型。 網格可以根據許多因素（包括觀察到最近的要求所觀察到的延遲），選擇最可能傳回快速回應的實例。

如果實例沒有回應或失敗，網格將會在另一個實例上重試要求。 如果傳回錯誤，網狀架構將會從負載平衡集區中收回實例，並在修復之後重新聲明該實例。 如果要求超時，網格會失敗，然後重試要求。 網格會捕捉併發出計量，並將其發佈至集中式計量系統。

## <a name="istio-and-envoy"></a>Istio 和 Envoy

雖然有一些服務網格選項目前存在，但是在撰寫本文時， [Istio](https://istio.io/docs/concepts/what-is-istio/) 是最受歡迎的。 Istio 是 IBM、Google 和 Lyft 的聯合風險。 它是開放原始碼的供應專案，可整合至新的或現有的分散式應用程式。 此技術提供一致且完整的解決方案，可保護、連線及監視微服務。 其功能包括：

- 使用強式身分識別型驗證和授權，在叢集中保護服務對服務的通訊。
- 適用于 HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量的自動負載平衡。
- 使用豐富的路由規則、重試、容錯移轉和錯誤插入，更精細地控制流量行為。
- 可插入的原則層和設定 API，支援存取控制、速率限制和配額。
- 叢集中所有流量的自動計量、記錄和追蹤，包括叢集輸入和輸出。

Istio 執行的主要元件是有權 [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)的 proxy 服務。 它會與每個服務一起執行，並為下列功能提供平臺中立的基礎：

- 動態服務探索。
- 負載平衡。
- TLS 終止。
- HTTP 和 gRPC proxy。
- 斷路器復原。
- 健康情況檢查。
- [使用未](https://martinfowler.com/bliki/CanaryRelease.html)部署的部署來輪流更新。

如先前所討論，Envoy 會以側車的形式部署至叢集中的每個微服務。

## <a name="integration-with-azure-kubernetes-services"></a>與 Azure Kubernetes Services 整合

Azure 雲端採用 Istio，並在 Azure Kubernetes Services 中為其提供直接支援。 下列連結可協助您開始使用：

- [在 AKS 中安裝 Istio](/azure/aks/istio-install)
- [使用 AKS 和 Istio](/azure/aks/istio-scenario-routing)

### <a name="references"></a>參考資料

- [Polly](http://www.thepollyproject.org/)

- [重試模式](/azure/architecture/patterns/retry)

- [斷路器模式](/azure/architecture/patterns/circuit-breaker)

- [Azure 中的復原技術白皮書](https://azure.microsoft.com/mediahandler/files/resourcefiles/resilience-in-azure-whitepaper/Resilience%20in%20Azure.pdf)

- [網路延遲](https://www.techopedia.com/definition/8553/network-latency)

- [備援性](/azure/architecture/guide/design-principles/redundancy)

- [異地複寫](/azure/sql-database/sql-database-active-geo-replication)

- [Azure 流量管理員](/azure/traffic-manager/traffic-manager-overview)

- [自動調整指引](/azure/architecture/best-practices/auto-scaling)

- [Istio](https://istio.io/docs/concepts/what-is-istio/)

- [Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)

>[!div class="step-by-step"]
>[上一個](infrastructure-resiliency-azure.md) 
>[下一步](monitoring-health.md)
