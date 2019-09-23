---
title: 復原通訊
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |復原通訊
ms.date: 06/30/2019
ms.openlocfilehash: 75a2ffe611ad0cf4bfa20efb49a6993bdbe6b073
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184845"
---
# <a name="resilient-communications"></a>復原通訊

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在本書中，我們 evangelized 了超越傳統整合型應用程式設計的優勢，並採用以微服務為基礎的架構，其中一組分散、獨立的服務獨立執行，並與每個伺服器通訊其他使用標準通訊協定，例如 HTTP 和 HTTPS。 雖然這類架構會為您購買許多重要的好處，但它也有許多挑戰。 例如，請考慮下列事項：

- *跨進程的網路通訊。* 每個服務都會透過網路通訊協定進行通訊，這會引進網路擁塞、延遲和暫時性錯誤。
- *服務探索。* 當每個服務在具有自己 IP 位址和埠的機器叢集上執行時，服務如何彼此探索及通訊？
- *恢復.* 如何管理短期失敗並讓系統穩定？
- *負載平衡。* 輸入流量如何分散到服務的多個實例？
- *安全性。* 如何強制執行傳輸層級加密和憑證管理等安全性考慮？
- \* 分散式監視。 -如何讓多個取用服務的單一要求相互關聯和捕捉追蹤性和監視？

雖然這些問題可以透過各種程式庫和架構來處理，但在程式碼基底中執行它們可能既昂貴又複雜又耗時。 此外，您最後會得到一個解決方案，其中的基礎結構顧慮會結合商務邏輯。

## <a name="service-mesh"></a>服務網格

較好的方法是考慮採用*服務網格*的全新且快速進化技術。 [服務網格](https://www.nginx.com/blog/what-is-a-service-mesh/)是一個可設定的基礎結構層，具有可處理服務通訊的內建功能，以及上述許多挑戰。 它會將這些疑慮與您的商務程式碼分開，並將其移至服務 proxy 中，這是每個服務隨附的實例。 通常稱為[側車模式](https://docs.microsoft.com/azure/architecture/patterns/sidecar)，服務網格 proxy 會部署到個別的進程，以供應商務程式碼的隔離和封裝。 不過，proxy 會與建立的服務緊密連結，並共用其生命週期。 圖6-9 顯示這種情況。

![具有側車的服務網格](./media/service-mesh-with-side-car.png)

**圖 6-9**。 具有側車的服務網格

在上圖中，請注意 proxy 如何攔截及管理微服務與叢集之間的通訊。

服務網格會以邏輯方式分割成兩個不同的元件：[資料平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)和[控制平面](https://blog.envoyproxy.io/service-mesh-data-plane-vs-control-plane-2774e720f7fc)。 圖6-10 顯示這些元件及其責任。

![服務網格控制項和資料平面](./media/istio-control-and-data-plane.png)

**圖6-10。** 服務網格控制項和資料平面

設定好之後，服務網格就能發揮高功能。 它可以從服務探索端點取得對應的實例集區。 然後，它可以將要求傳送至特定實例，並記錄結果的延遲和回應類型。 網格可以根據許多因素（包括觀察到最近要求的延遲），選擇最有可能傳回快速回應的實例。

如果實例沒有回應或失敗，則網格可以重試另一個實例上的要求。 如果集區一致地傳回錯誤，則網格可以將其從負載平衡集區收回，以便稍後在修復後定期重試。 如果要求超時，網格可能會失敗，然後重試要求。 網格會以計量和分散式追蹤的形式來捕捉行為，然後可以發出至集中式計量系統。

## <a name="istio-and-envoy"></a>Istio 和 Envoy

雖然目前有一些服務網格選項存在，但[Istio](https://istio.io/docs/concepts/what-is-istio/)是在撰寫本文時最受歡迎的。 IBM、Google 和 Lyft 司機的聯合風險，是一個開放原始碼的供應專案，可以整合到新的或現有的分散式應用程式中。 它提供一致且完整的解決方案來保護、連接和監視微服務。 其功能包括：

- 在具有強式身分識別型驗證和授權的叢集中，保護服務對服務的通訊。
- HTTP、 [gRPC](https://grpc.io/)、WEBSOCKET 和 TCP 流量的自動負載平衡。
- 使用豐富的路由規則、重試、容錯移轉和錯誤插入來精細控制流量行為。
- 可插入的原則層和設定 API，支援存取控制、速率限制和配額。
- 叢集中所有流量的自動計量、記錄和追蹤，包括叢集輸入和輸出。

Istio 執行的主要元件是具有[Envoy proxy](https://www.envoyproxy.io/docs/envoy/latest/intro/what_is_envoy)資格的 proxy 服務。 從 Lyft 司機開始，並提供給[雲端原生運算基礎](https://www.cncf.io/)（在第1章中討論），Envoy proxy 會與每個服務一起執行，並為下列功能提供不受平臺限制的基礎：

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

>[!div class="step-by-step"]
>[上一頁](infrastructure-resiliency-azure.md)
>[下一頁](monitoring-health.md) <!-- Next Chapter -->