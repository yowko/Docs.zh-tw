---
title: 構建為雲做好準備的彈性服務。 接受雲端中的暫時性失敗
description: 使用 Azure 雲和 Windows 容器對現有 .NET 應用程式進行現代化 |構建為雲做好準備的彈性服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: e516dc675ceb8def25c6d676bced0ea7f253b2d5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "74711253"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>建置可用於雲端的復原服務：包含雲端中的暫時性失敗

復原是從失敗中復原並繼續運作的能力。 恢復能力不是要避免故障，而是接受失敗將發生的事實，然後以避免停機或資料丟失的方式回應它們。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

應用程式至少實現了基於軟體的恢復能力模型（而不是基於硬體的模型）即可訪問雲。 您的雲應用程式必須接受肯定會發生的部分故障。 設計或部分重構應用程式，以在預期部分故障時實現彈性。 它應設計為可應對部分故障，如瞬態網路中斷和節點，或雲中崩潰的 VM。 即使容器移動到協調器群集中的其他節點也可能導致應用程式中間歇性短路故障。

## <a name="handling-partial-failure"></a>處理部分失敗

在基於雲的應用程式中，存在部分故障的風險。 例如，單個網站實例或容器可能會失敗，或者它可能在短時間內不可用或無回應。 或者，單個 VM 或伺服器可能會崩潰。

由於用戶端和服務是單獨的進程，因此服務可能無法及時回應用戶端的請求。 服務可能超載並緩慢回應請求，或者由於網路問題，該服務可能在短時間內無法訪問。

例如，考慮訪問 Azure SQL 資料庫中資料庫的單片 .NET 應用程式。 如果 Azure SQL 資料庫或任何其他協力廠商服務在一段時間內無回應（Azure SQL 資料庫可能移動到其他節點或伺服器，並且無回應幾秒鐘），當使用者嘗試執行任何操作時，應用程式可能會崩潰和在同一時刻顯示異常。

在使用 HTTP 服務的應用中可能會出現類似的情況。 在短暫的瞬態故障期間，網路或服務本身可能在雲中不可用。

如圖 4-9 所示的彈性應用程式應實現"使用指數回退重試"等技術，使應用程式有機會處理資源中的瞬態故障。 您還應在應用程式中使用"斷路器"。 斷路器阻止應用程式嘗試訪問資源時，它實際上是一個長期故障。 通過使用斷路器，應用程式避免了引發對自身的拒絕服務。

![通過使用指數回退重試處理的部分故障圖。](./media/retry-partial-failures.png)

**圖 4-9。** 通過使用指數回退重試處理的部分故障

您可以在 HTTP 資源和資料庫資源中使用這些技術。 在圖 4-9 中，應用程式基於 3 層體系結構，因此您需要在服務等級 （HTTP） 和資料層級別 （TCP） 使用這些技術。 在除了資料庫（沒有其他服務或微服務）之外僅使用單個應用層的單一應用程式中，在資料庫連接級別處理瞬態故障可能就足夠了。 在這種情況下，只需要資料庫連接的特定配置。

實現訪問資料庫的彈性通信時，根據正在使用的 .NET 版本，它非常簡單（例如，[使用實體框架 6 或更高版本](/ef/ef6/fundamentals/connection-resiliency/retry-logic)）。 這只是設定資料庫連接的問題）。 或者，您可能需要使用其他庫，如[瞬態故障處理應用程式塊](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50))（對於早期版本的 .NET），甚至實現您自己的庫。

在實現 HTTP 重試和斷路器時，建議 .NET 使用[Polly](https://github.com/App-vNext/Polly)庫，該庫的目標是 .NET 框架 4.0、.NET 框架 4.5 和 .NET 標準 1.1，其中包括 .NET 核心支援。

要瞭解如何實施處理雲中部分故障的策略，請參閱以下參考。

### <a name="additional-resources"></a>其他資源

- **實現彈性通信以處理部分故障**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **實體框架連接恢復性和重試邏輯（版本 6 及更高版本）**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **暫時性錯誤處理應用程式區塊**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **用於彈性 HTTP 通信的波利庫**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[上一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[下一個](modernize-your-apps-with-monitoring-and-telemetry.md)
