---
title: 處理部分失敗
description: 了解如何適當地處理部分失敗。 微服務可能無法完全正常運作，但它仍可能可以執行一些有用的工作。
ms.date: 10/16/2018
ms.openlocfilehash: 3345fffe3a38b8336d71ebb9c88e76d3315fd2e2
ms.sourcegitcommit: a8730298170b8d96b4272e0c3dfc9819c606947b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2020
ms.locfileid: "90738758"
---
# <a name="handle-partial-failure"></a>處理部分失敗

在微服務架構應用程式等分散式系統中，部分失敗的風險無所不在。 例如，單一微服務/容器可能會失敗或暫時無法回應，或是單一 VM 或伺服器可能會當機。 由於用戶端和服務是不同的進程，因此服務可能無法及時回應用戶端的要求。 服務可能會多載且回應要求的速度相當慢，或只是因為網路問題而暫時無法存取。

以 eShopOnContainers 範例應用程式中的 [訂單] 詳細資料頁面為例。 如果當使用者嘗試送出訂單時，訂購微服務沒有回應，不正確的用戶端處理序 (MVC Web 應用程式) 實作 (例如若用戶端程式碼使用沒有逾時的同步 RPC) 會無限期地封鎖等候回應的執行緒。 除了造成不良的使用者體驗之外，每個沒有回應的等候都會耗用或封鎖執行緒，而執行緒對於可高度擴充的應用程式而言相當重要。 如果有許多已封鎖的執行緒，則應用程式的執行時間最終可能會用盡執行緒。 在此情況下，應用程式可能會變得全部沒有回應，而不只是部分沒有回應，如圖 8-1 所示。

![顯示部分失敗的圖表。](./media/handle-partial-failure/partial-failures-diagram.png)

**圖 8-1**： 由於影響服務執行緒可用性的相依性所造成的部分失敗

在大型微服務架構應用程式中，任何部分失敗都可能會擴大，特別是如果大多數內部微服務互動是以同步 HTTP 呼叫為基礎 (視為反面模式)。 假設有個系統，每天會收到數百萬個傳入呼叫。 如果您的系統的設計不是以同步 HTTP 呼叫的長鏈為基礎，則這些撥入電話可能會導致許多的連出呼叫 (讓我們假設 1:4) 至數十個內部微服務的比率為同步相依性。 這種情況會顯示在圖8-2 中，特別是相依性 \# 3，會啟動鏈，呼叫相依性 #4，然後呼叫 #5。

![顯示多個分散式相依性的圖表。](./media/handle-partial-failure/multiple-distributed-dependencies.png)

**圖 8-2**。 HTTP 要求鏈結太長的不正確設計影響

分散式和雲端式系統一定會發生間歇性失敗，即使每個相依性本身有絕佳的可用性也一樣。 這是您需要考量的事實。

如果您未設計及實作技術來確保容錯，即使是短暫的停機也可能會擴大。 例如，可用性達 99.99% 的 50 個相依性會因為此漣漪效果而導致每個月數小時的停機。 當微服務相依性處理大量要求失敗時，該失敗很快就會使每個服務中的所有可用要求執行緒達到飽和，而導致整個應用程式損毀。

![顯示微服務中已放大部分失敗的圖表。](./media/handle-partial-failure/partial-failure-amplified-microservices.png)

**圖 8-3**： 部分失敗因同步 HTTP 呼叫鏈結太長的微服務而擴大

為了將這個問題降至最低，在 [非同步微服務整合強制執行微服務的自主性](../architect-microservice-container-applications/communication-in-microservice-architecture.md#asynchronous-microservice-integration-enforces-microservices-autonomy)一節中，本指南鼓勵您在內部微服務之間使用非同步通訊。

此外，請務必設計微服務和用戶端應用程式來處理部分失敗，也就是建置具有恢復功能的微服務和用戶端應用程式。

>[!div class="step-by-step"]
>[上一個](index.md) 
>[下一步](partial-failure-strategies.md)
