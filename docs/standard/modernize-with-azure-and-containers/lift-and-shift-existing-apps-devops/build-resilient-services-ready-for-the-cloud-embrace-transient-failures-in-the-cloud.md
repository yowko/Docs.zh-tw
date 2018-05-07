---
title: 建立具有恢復功能服務就緒雲端。 運用雲端中的暫時性失敗
description: 容器化的.NET 應用程式的.NET Microservices 架構 |建立具有恢復功能服務就緒雲端。 運用雲端中的暫時性失敗
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/26/2017
ms.openlocfilehash: 23b8dce9fb5dd3388c1d76e5ba9c2412c7d17a21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/04/2018
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>建立具有恢復功能服務就緒定域機組： 面向的雲端中的暫時性失敗

「復原」是指能夠從失敗中復原並繼續運作的能力。 恢復功能不是關於避免失敗，但接受的事實，將會失敗，並再回應給它們的方式可避免停機時間或資料遺失。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

您的應用程式可供雲端時最少，它會實作軟體為基礎的模型的恢復功能，而不是硬體為基礎的模型。 您的雲端應用程式也必須不怕一定會發生部分失敗。 您要設計或部分重構您的應用程式，如果您想要達到預期的部分失敗的恢復功能。 它應該設計成處理部分失敗，例如暫時性網路中斷和節點或 Vm 雲端中損毀。 即使正在移動至另一個節點 orchestrator 叢集內的容器可能會導致應用程式中的間歇性簡短失敗。

## <a name="handling-partial-failure"></a>處理部分失敗

以雲端為基礎的應用程式，在沒有部分失敗無所不在風險。 例如，單一網站執行個體或容器可能會失敗，或可能無法使用或沒有回應的短暫時間。 或者，在單一 VM 或伺服器可能會當機。

用戶端和服務會個別處理序，因為服務可能無法及時回應至用戶端的要求。 服務可能會多載，並回應速度極為緩慢要求，或它可能只是無法存取一小段時間因為網路問題。

例如，請考慮龐大的.NET 應用程式可存取 Azure SQL Database 中的資料庫。 如果 Azure SQL 資料庫或任何其他第三方服務沒有回應的簡短時間 （Azure SQL database 可能會移到另一個節點或伺服器，而且沒有回應數秒鐘），當使用者嘗試執行任何動作時，應用程式可能會當機並顯示w 完全相同的目前例外狀況。

使用 HTTP 服務的應用程式中，會發生類似的情況。 網路或服務本身可能無法在雲端中簡短、 暫時性的失敗期間。

具有恢復功能的應用程式，例如在圖 4 至 9 中所示應該實作 「 重試指數型輪詢使用 「 類似的技術，讓應用程式有機會處理資源中的暫時性失敗。 您也應該在應用程式中使用 「 斷路器 」。 斷路器就會停止應用程式嘗試存取資源時，它實際上長期失敗。 藉由使用斷路器，應用程式可避免誘發阻絕服務本身。

![使用指數型輪詢的重試所處理的部分失敗](./media/image9.png)

> **圖 4 至 9。** 使用指數型輪詢的重試所處理的部分失敗

在 HTTP 資源和資料庫資源中，您可以使用這些技術。 在圖 4-9、 應用程式為基礎的 3 層式架構，因此您必須在服務層級 (HTTP) 和資料層級 (TCP)，這些技術。 在使用只除了資料庫 （沒有其他服務或 microservices） 的單一應用程式層的整合應用程式，處理暫時性資料庫連接層級的失敗可能不夠。 在這種情況下，通常只資料庫連接的特定組態則是必要項目。

實作存取資料庫時，根據您使用的.NET 版本的彈性通訊時可能非常直接 (例如， [Entity Framework 6 或更新版本](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)，它是只需設定資料庫連接）。 或者，您可能需要使用額外的程式庫，例如[暫時性錯誤處理應用程式區塊](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)（適用於舊版的.NET），或甚至會實作您自己的程式庫。

實作 HTTP 重試與斷路器時，適用於.NET 的建議是使用[Polly](https://github.com/App-vNext/Polly)目標.NET 4.0、.NET 4.5 和.NET 標準 1.1 中，其中包含.NET Core 支援程式庫。

若要深入了解如何實作的策略來處理在雲端中的部分失敗，請參閱下列參考。

### <a name="additional-resources"></a>其他資源

-   **實作有彈性的通訊，來處理部分失敗**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

-   **Entity Framework 連接恢復功能和重試邏輯 （6 或更新版本）**

    [https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx](https://msdn.microsoft.com/library/dn456835(v=vs.113).aspx)

-   **暫時性錯誤處理應用程式區塊**

-   [https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx](https://msdn.microsoft.com/library/hh680934(v=pandp.50).aspx)

-   **具有恢復功能的 HTTP 通訊的 Polly 程式庫**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
[下一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
