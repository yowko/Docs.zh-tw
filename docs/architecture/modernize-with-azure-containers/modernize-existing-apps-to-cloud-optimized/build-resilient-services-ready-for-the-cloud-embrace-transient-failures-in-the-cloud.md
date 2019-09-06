---
title: 為雲端打造可復原的服務。 接受雲端中的暫時性失敗
description: 使用 Azure 雲端和 Windows 容器現代化現有的 .NET 應用程式 |為雲端打造可復原的服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: 5f44029a214cf1f366fc787e27a9ac34599c4dca
ms.sourcegitcommit: c70542d02736e082e8dac67dad922c19249a8893
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/05/2019
ms.locfileid: "70373963"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>建置準備好在雲端執行的彈性服務：接受雲端中的暫時性失敗

「復原」是指能夠從失敗中復原並繼續運作的能力。 復原不是為了避免失敗，而是要接受發生失敗的事實，然後以避免停機或資料遺失的方式來回應它們。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

您的應用程式已準備好進行雲端，因為它至少會實行以軟體為基礎的復原模型，而不是以硬體為基礎的模型。 您的雲端應用程式必須採用一定會發生的部分失敗。 設計或部分重構您的應用程式，以在預期的部分失敗時達到復原能力。 其設計目的是要處理部分失敗，例如暫時性網路中斷和節點，或在雲端中損毀的 Vm。 即使是移到 orchestrator 叢集中不同節點的容器，也可能會導致應用程式內發生間歇短失敗。

## <a name="handling-partial-failure"></a>處理部分失敗

在雲端式應用程式中，部分失敗有一個既有的風險。 例如，單一網站實例或容器可能會失敗，或短時間可能無法使用或無回應。 或者，單一 VM 或伺服器可能損毀。

因為用戶端和服務是不同的進程，服務可能無法及時回應用戶端的要求。 服務可能會多載，而且對要求的回應速度很慢，或因為網路問題而短時間內可能無法存取。

例如，請考慮在 Azure SQL Database 中存取資料庫的整合型 .NET 應用程式。 如果 Azure SQL 資料庫或任何其他協力廠商服務短暫沒有回應（Azure SQL 資料庫可能會移至不同的節點或伺服器，而且有幾秒鐘沒有回應），則當使用者嘗試執行任何動作時，應用程式可能會損毀並建立同時有一個例外狀況。

使用 HTTP 服務的應用程式可能會發生類似的情況。 在短暫的暫時性失敗期間，網路或服務本身可能無法在雲端中使用。

如圖4-9 所示，彈性應用程式應該執行像是「使用指數輪詢重試」之類的技術，讓應用程式有機會處理資源中的暫時性失敗。 您也應該在應用程式中使用「斷路器」。 當應用程式實際上是長期失敗時，斷路器會停止嘗試存取資源。 藉由使用斷路器，應用程式可避免誘發本身的拒絕服務。

![以指數輪詢的重試處理部分失敗](./media/image9.png)

**圖4-9。** 以指數輪詢的重試處理部分失敗

您可以在 HTTP 資源和資料庫資源中使用這些技術。 在圖4-9 中，應用程式是以三層式架構為基礎，因此您需要在服務層級（HTTP）和資料層層級（TCP）上使用這些技術。 在只使用資料庫（沒有其他服務或微服務）的單一應用層的整合型應用程式中，處理資料庫連接層級的暫時性失敗可能就已足夠。 在該案例中，只需要特定的資料庫連接設定。

根據您所使用的 .NET 版本，執行存取資料庫的復原通訊時，可能很簡單（例如，[使用 Entity Framework 6 或更新](/ef/ef6/fundamentals/connection-resiliency/retry-logic)版本）。 這只是設定資料庫連接的相關事項。 或者，您可能需要使用其他程式庫，例如[暫時性錯誤處理應用程式區塊](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50))（適用于舊版 .net），或甚至是執行您自己的程式庫。

實作 HTTP 重試與斷路器時，適用於.NET 的建議是使用[Polly](https://github.com/App-vNext/Polly)目標.NET Framework 4.0，.NET Framework 4.5 和.NET Standard 1.1 中，其中包含.NET Core 支援程式庫。

若要瞭解如何在雲端中執行處理部分失敗的策略，請參閱下列參考。

### <a name="additional-resources"></a>其他資源

- **執行復原性通訊以處理部分失敗**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework 連接復原和重試邏輯（第6版和更新版本）**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **暫時性錯誤處理應用程式區塊**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **適用于復原 HTTP 通訊的 Polly 程式庫**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[下一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
