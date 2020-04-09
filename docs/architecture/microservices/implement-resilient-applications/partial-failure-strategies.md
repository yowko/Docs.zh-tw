---
title: 處理部分失敗的策略
description: 了解適當處理部分失敗的幾個策略。
ms.date: 10/16/2018
ms.openlocfilehash: abf87df5afed02b4d794a1307a0ed943cafb4db3
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988800"
---
# <a name="strategies-to-handle-partial-failure"></a>處理部分失敗的策略

處理部分失敗的策略包含下列項目。

**使用跨內部微服務的非同步通訊 (例如以訊息為基礎的通訊)**。 我們強烈建議您不要跨內部微服務建立一長串的同步 HTTP 呼叫，因為不正確的設計最終可能會成為不良中斷的主要原因。 相反地，除了用戶端應用程式與微服務第一層或微調 API 閘道之間的前端通訊，通常建議在通過初始要求/回應循環之後僅使用跨內部微服務的非同步式 (以訊息為基礎) 通訊。 最終一致性和事件驅動架構會協助最小化漣漪效果。 這些方法會強制更高層級微服務的自主性，從而防止此處註明的問題。

**利用指數輪詢來使用重試**。 這項技術可在服務短時間內無法使用的情況下，藉由執行特定次數的呼叫重試，來協助避免簡短而間歇的失敗。 這可能會因為間歇性的網路問題或當微服務/容器移動到叢集中不同的節點時而發生。 然而，若這些重試並未適當的使用斷路器進行設計，它可能會加劇漣漪效果，並最終導致[enial of Service (DoS) (拒絕服務)](https://en.wikipedia.org/wiki/Denial-of-service_attack)。

**網路逾時的因應措施**。 一般情況下，用戶端應設計成不會無限期的進行封鎖，並在等待回應時總是使用逾時。 使用逾時可確保資源不會無限期的遭到繫結。

**使用斷路器模式**。 在這種方法中，用戶端處理序會追蹤失敗要求的次數。 如果錯誤率超過配置限制,「斷路器」跳閘,以便進一步嘗試立即失敗。 (如果大量請求失敗,則表明服務不可用,並且發送請求毫無意義。超時后,客戶端應重試,如果新請求成功,請關閉斷路器。

**提供後援**。 在這種方法中，用戶端處理序會在要求失敗時執行後援邏輯，例如傳回快取資料或預設值。 這是一種適合查詢的方法，而針對更新或命令會更為複雜。

**限制佇列要求的數目**。 用戶端也應設定用戶端微服務可傳送至特定服務之未處理要求的數目上限。 若達到該限制，則繼續傳送額外的要求可能會沒有意義，因此應讓那些嘗試立即失敗。 在實作方面，Polly [Bulkhead Isolation](https://github.com/App-vNext/Polly/wiki/Bulkhead) 原則可用於完成這項要求。 此方法本質上即是使用 <xref:System.Threading.SemaphoreSlim> 作為實作的並行節流。 它也允許了艙壁之外的「佇列」。 您甚至可以在執行之前主動流出過量的負載 (例如因為容量被視為已滿)。 這可讓其回應特定失敗案例的速度比斷路器要來得更快，因為斷路器會等待失敗。 [Polly](http://www.thepollyproject.org/) 中的 BulkheadPolicy 物件會公開艙壁及佇列充滿的程度，並在溢位時提供事件，使其也可用於驅動自動化水平規模調整。

## <a name="additional-resources"></a>其他資源

- **恢復能力模式**\
  [https://docs.microsoft.com/azure/architecture/patterns/category/resiliency](/azure/architecture/patterns/category/resiliency)

- **增加彈性和最佳化效能**\
  <https://docs.microsoft.com/previous-versions/msp-n-p/jj591574(v=pandp.10)>

- **艙壁。** GitHub 存放庫。 Polly 原則的實作。\
  <https://github.com/App-vNext/Polly/wiki/Bulkhead>

- **為 Azure 設計彈性應用程式**\
  [https://docs.microsoft.com/azure/architecture/resiliency/](/azure/architecture/resiliency/)

- **瞬態故障處理**\
  [https://docs.microsoft.com/azure/architecture/best-practices/transient-faults](/azure/architecture/best-practices/transient-faults)

>[!div class="step-by-step"]
>[前一個](handle-partial-failure.md)
>[下一個](implement-retries-exponential-backoff.md)
