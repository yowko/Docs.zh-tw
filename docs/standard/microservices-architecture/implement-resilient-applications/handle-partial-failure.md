---
title: "處理部分失敗"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |處理部分失敗"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b7d16acf3de2d395da70e8f46e59c129dec24f71
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="handling-partial-failure"></a>處理部分失敗

在分散式系統如 microservices 為基礎的應用程式中，會有部分失敗的無所不在風險。 例如，單一微服務/容器可能會失敗，或可能無法回應一段時間，或單一 VM 或伺服器可能會損毀。 由於用戶端和服務的個別處理序，服務可能無法在用戶端的要求能夠及時回應。 服務可能會多載和回應速度極為緩慢的要求，或可能只是無法存取一小段時間因為網路問題。

例如，請考慮從 eShopOnContainers 的訂單詳細資料頁面範例應用程式。 如果順序的微服務沒有回應當使用者嘗試送出訂單時，用戶端處理序 （MVC web 應用程式） 的不正確實作 — 比方說，如果用戶端程式碼都不會逾時與使用同步 Rpc — 會無限期地封鎖執行緒等待回應。 除了提供不正確的使用者體驗，每一個回應的等候取用或會阻擋執行緒，而且執行緒高度可擴充的應用程式中非常重要。 如果有許多已封鎖的執行緒，最終應用程式的執行階段可以用完執行緒。 在此情況下，應用程式可能會變得全域沒有回應，而不是只部分沒有回應，以顯示圖 10-1。

![](./media/image1.png)

**圖 10 1**。 部分失敗，因為會影響服務的執行緒可用性的相依性

在大型 microservices 型應用程式中，任何部分失敗可以會隨之增加，尤其是如果大部分的內部 microservices 互動的同步 HTTP 呼叫 （這可反面模式）。 請思考接收每日的連入呼叫數百萬的系統。 如果您的系統具有不正確的設計為基礎的同步 HTTP 呼叫長的鏈結，這些連入呼叫可能會導致許多數百萬詳細 （假設的比率為 1:4） 的連出呼叫數十個內部 microservices 做為同步的相依性。 這種情況下會顯示在圖 10-2，特別是相依性\#3。

![](./media/image2.png)

**圖 10 2**。 讓包含很長的鏈結的 HTTP 要求的設計不正確的影響

幾乎是間歇性失敗保證在分散式部署和雲端架構的系統，即使每個相依性本身具有極佳的可用性。 這應該是您需要考慮的事實。

如果您未設計及實作以確保容錯技術，甚至小停機可以幅度加大。 為例，50 與相依性每個 99.99%的可用性可能會導致數小時停機時間的每個月，因為此產生漣漪效果。 當微服務相依性失敗時處理大量的要求時，該失敗快速 saturate 中每個服務的所有可用的要求執行緒和整個應用程式會損毀。

![](./media/image3.png)

**圖 10-3**。 幅度加大 microservices 使用長的鏈結的同步 HTTP 呼叫的部分失敗

若要減少此問題，一節中的"*非同步的微服務整合，強制執行 「 微服務的自主*」 （本章架構），我們建議您在內部使用的非同步通訊microservices。 我們簡要說明更下一節。

此外，務必您設計 microservices 和用戶端應用程式處理部分失敗 — 也就是建立具有恢復功能 microservices 和用戶端應用程式。


>[!div class="step-by-step"]
[上一個](index.md) [下一步] (部分-失敗-strategies.md)
