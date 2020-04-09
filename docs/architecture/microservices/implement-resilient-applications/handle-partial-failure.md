---
title: 處理部分失敗
description: 了解如何適當地處理部分失敗。 微服務可能無法完全正常運作，但它仍可能可以執行一些有用的工作。
ms.date: 10/16/2018
ms.openlocfilehash: 0300719360e1a2500db0af8454c91fdfe2e5b09b
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988866"
---
# <a name="handle-partial-failure"></a>處理部分失敗

在微服務架構應用程式等分散式系統中，部分失敗的風險無所不在。 例如，單一微服務/容器可能會失敗或暫時無法回應，或是單一 VM 或伺服器可能會當機。 由於用戶端和服務是單獨的進程,因此服務可能無法及時回應客戶端的請求。 服務可能會多載且回應要求的速度相當慢，或只是因為網路問題而暫時無法存取。

以 eShopOnContainers 範例應用程式中的 [訂單] 詳細資料頁面為例。 如果當使用者嘗試送出訂單時，訂購微服務沒有回應，不正確的用戶端處理序 (MVC Web 應用程式) 實作 (例如若用戶端程式碼使用沒有逾時的同步 RPC) 會無限期地封鎖等候回應的執行緒。 除了造成不良的使用者體驗之外，每個沒有回應的等候都會耗用或封鎖執行緒，而執行緒對於可高度擴充的應用程式而言相當重要。 如果有許多阻塞的線程,則最終應用程式的運行時可能會耗盡線程。 在此情況下，應用程式可能會變得全部沒有回應，而不只是部分沒有回應，如圖 8-1 所示。

![顯示部分故障的圖表。](./media/handle-partial-failure/partial-failures-diagram.png)

**圖 8-1**： 由於影響服務執行緒可用性的相依性所造成的部分失敗

在大型微服務架構應用程式中，任何部分失敗都可能會擴大，特別是如果大多數內部微服務互動是以同步 HTTP 呼叫為基礎 (視為反面模式)。 假設有個系統，每天會收到數百萬個傳入呼叫。 如果您的系統設計錯誤,該設計基於長同步 HTTP 調用鏈,則這些傳入呼叫可能會導致數百萬個傳出呼叫(假設為 1:4)與數十個內部微服務作為同步依賴項的比率。 這種情況如圖 8-2 所示,尤其是\#啟動鏈 、調用依賴項#4的依賴項 3。 呼叫#5。

![顯示多個分散式依賴項的圖表。](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**圖8-2**. HTTP 要求鏈結太長的不正確設計影響

分散式和雲端式系統一定會發生間歇性失敗，即使每個相依性本身有絕佳的可用性也一樣。 這是您需要考量的事實。

如果您未設計及實作技術來確保容錯，即使是短暫的停機也可能會擴大。 例如，可用性達 99.99% 的 50 個相依性會因為此漣漪效果而導致每個月數小時的停機。 當微服務相依性處理大量要求失敗時，該失敗很快就會使每個服務中的所有可用要求執行緒達到飽和，而導致整個應用程式損毀。

![顯示部分故障放大微服務中的圖表。](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**圖 8-3**： 部分失敗因同步 HTTP 呼叫鏈結太長的微服務而擴大

為了最小化此問題,在[非同步微服務整合部分中強制實施微服務的自主性](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy),本指南鼓勵您跨內部微服務使用非同步通訊。

此外，請務必設計微服務和用戶端應用程式來處理部分失敗，也就是建置具有恢復功能的微服務和用戶端應用程式。

>[!div class="step-by-step"]
>[前一個](index.md)
>[下一個](partial-failure-strategies.md)
