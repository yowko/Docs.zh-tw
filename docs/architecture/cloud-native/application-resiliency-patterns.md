---
title: 應用程式復原模式
description: 架構適用于 Azure 的雲端原生 .NET 應用程式 |應用程式復原模式
ms.date: 06/30/2019
ms.openlocfilehash: 8455584fe1d5b02f6d9543c3bad32cca7369c158
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71183718"
---
# <a name="application-resiliency-patterns"></a>應用程式復原模式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

第一道防線是具備軟體功能的應用程式恢復功能。 

雖然您可以投入相當長的時間來撰寫自己的復原架構，但這類產品已經存在。 例如， [Polly](http://www.thepollyproject.org/)是完整的 .net 復原和暫時性錯誤處理程式庫，可讓開發人員以流暢且安全線程的方式來表示復原原則。 Polly 是以完整 .NET Framework 或 .NET Core 所建立的應用程式為目標。 圖6-2 顯示可從 Polly 程式庫取得的復原原則（也就是功能）。 這些原則可以個別套用或結合在一起。

![Polly 架構](./media/polly-resiliency-framework.png)

**圖 6-2**. Polly 復原架構功能

請注意，在上圖中，復原原則會套用至要求訊息，不論是來自外部用戶端還是其他後端服務。 其目標是要補償可能暫時無法使用之服務的要求。 這些短暫的中斷通常會以 [圖 6-3] 所示的 HTTP 狀態碼來進行資訊清單。

![要重試的 HTTP 狀態碼](./media/http-status-codes.png)

**圖 6-3**. 要重試的 HTTP 狀態碼

問題：是否要重試 HTTP 狀態碼 403-禁止？ 否。 在這裡，系統會正常運作，但會通知呼叫者未獲授權執行要求的作業。 請務必小心，只重試失敗所造成的作業。

如第1章所建議，建立雲端原生應用程式的 Microsoft 開發人員應該以 .NET Core 為目標。 2\.1 版引進了[HTTPClientFactory](https://www.stevejgordon.co.uk/introduction-to-httpclientfactory-aspnetcore)程式庫，可用於建立與 URL 型資源互動的 HTTP 用戶端實例。 取代原始的 HTTPClient 類別，factory 類別支援許多增強功能，其中一個與 Polly 復原程式庫[緊密整合](../microservices/implement-resilient-applications/implement-http-call-retries-exponential-backoff-polly.md)。 有了這項功能，您就可以在應用程式啟動類別中輕鬆定義復原原則，以處理部分失敗和連接問題。

接下來，讓我們展開重試和斷路器模式。

### <a name="retry-pattern"></a>重試模式

在分散式雲端原生環境中，服務和雲端資源的呼叫可能會因為暫時性（短期）失敗而失敗，這通常會在短時間後自行修正。 執行重試策略可協助雲端原生服務處理這些案例。

[重試模式](https://docs.microsoft.com/azure/architecture/patterns/retry)可讓服務以指數方式增加等候時間，重試失敗的要求作業 a （可設定）的次數。 圖6-4 顯示重試動作。

![動作中的重試模式](./media/retry-pattern.png)

**圖 6-4**。 動作中的重試模式

在上圖中，已針對要求作業實作為重試模式。 它會設定為在失敗後的輪詢間隔（等待時間）後最多允許四次重試，每次後續嘗試會以指數方式加倍。

- 第一個調用失敗，並傳回 HTTP 狀態碼500。 應用程式會等待兩秒，並 reties 呼叫。
- 第二個調用也會失敗，並傳回 HTTP 狀態碼500。 應用程式現在會將輪詢間隔加倍到四秒，然後重試呼叫。
- 最後，第三個呼叫會成功。
- 在此案例中，重試作業最多會嘗試四次重試，同時將輪詢持續時間加倍，再使呼叫失敗。

請務必增加輪詢期間，再重試呼叫以允許服務時間自行修正。 最佳做法是實施以指數方式增加的輪詢（每次重試的間隔加倍），以允許適當的更正時間。

## <a name="circuit-breaker-pattern"></a>斷路器模式

雖然重試模式可以協助搶救在部分失敗中光子的要求，但在某些情況下，失敗可能是因為無法預期的事件而需要較長的時間來解決。 這些錯誤的嚴重性可能從失去部分連線到服務完全失敗。 在這些情況下，應用程式會持續重試不太可能成功的作業，這是無意義的。

為了讓事情更糟，在無回應的服務上執行連續的重試作業，可以將您移至自我加諸的阻絕服務案例，其中會持續呼叫耗盡資源（例如記憶體、執行緒和資料庫）來淹沒服務連接，導致系統中使用相同資源的不相關部分發生失敗。

在這些情況下，最好是讓作業立即失敗，而且只有在可能成功時才嘗試叫用服務。

[斷路器模式](https://docs.microsoft.com/azure/architecture/patterns/circuit-breaker)可防止應用程式重複嘗試執行可能失敗的作業。 它也會透過定期試用呼叫來監視應用程式，以判斷錯誤是否已解決。 圖6-5 顯示作用中的斷路器模式。

![動作中的斷路器模式](./media/circuit-breaker-pattern.png)

**圖 6-5**。 動作中的斷路器模式

在上圖中，已將斷路器模式新增至原始的重試模式。 請注意，在10次失敗的要求之後，斷路器會開啟，不再允許服務的呼叫。 設定為30秒的 CheckCircuit 值會指定程式庫允許一個要求繼續至服務的頻率。 如果該呼叫成功，則電路會關閉，且服務會再次提供給流量。

請記住，斷路器模式的目的與重試模式*不同*。 重試模式可讓應用程式在預期會成功的情況下重試操作。 斷路器模式可防止應用程式執行可能失敗的作業。 應用程式通常會使用重試模式*結合*這兩種模式，透過斷路器叫用操作。 不過，重試邏輯應該會受到斷路器所傳回之任何例外狀況的影響，而且如果斷路器指出錯誤不是暫時性的，就會放棄重試嘗試。

應用程式復原是處理有問題的要求作業時必須具備的。 但是，這只是故事的一半而已。 接下來，我們將討論 Azure 雲端中可用的復原功能。

>[!div class="step-by-step"]
>[上一頁](resiliency.md)
>[下一頁](infrastructure-resiliency-azure.md)
