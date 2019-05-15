---
title: 建置開始使用雲端的復原服務。 接受雲端中的暫時性失敗
description: 將現有的.NET 應用程式使用 Azure 雲端和 Windows 容器現代化 |建置開始使用雲端的復原服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: ca5d5e0c3af772ac52a02894c96889c776cf7d48
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65643729"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>建置準備好在雲端執行的彈性服務：接受雲端中的暫時性失敗

「復原」是指能夠從失敗中復原並繼續運作的能力。 復原不是關於避免失敗，但接受，將會失敗，事實，然後回應它們以避免停機或資料遺失的方式。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

您的應用程式時，開始使用雲端，最小值，它會實作的復原能力，以軟體為基礎的模型，而不是以硬體為基礎的模型。 您的雲端應用程式必須不怕當然就會發生部分失敗。 設計或部分重構您的應用程式，以達到預期的部分失敗的恢復功能。 它應該設計成能夠回應部分失敗，例如暫時性網路中斷和節點或在雲端中損毀的 Vm。 移至不同的節點，協調器叢集內的平均容器可能會導致在應用程式中的間歇性短暫性失敗。

## <a name="handling-partial-failure"></a>處理部分失敗

在雲端為基礎的應用程式，則部分失敗的風險無所不在。 比方說，單一網站執行個體或容器可能會失敗，或可能無法使用或無回應一小段時間。 或者，您也可以在單一 VM 或伺服器可能會當機。

用戶端和服務是不同的處理序，因為服務可能無法及時回應用戶端的要求。 服務可能會多載，並回應變慢的要求，或它可能無法存取一小段時間因為網路問題。

例如，請考慮單體式的.NET 應用程式可存取 Azure SQL Database 中的資料庫。 如果 Azure SQL database 或任何其他第三方服務沒有回應的簡短時間 （Azure SQL database 可能會移到另一個節點或伺服器，而且沒有回應幾秒鐘的時間），當使用者嘗試執行任何動作時，應用程式可能會當機和顯示w 在相同時間點發生例外狀況。

使用 HTTP 服務的應用程式可能會發生類似的狀況。 網路或服務本身可能無法在雲端中簡短的暫時性失敗。

靈活的應用程式，在圖 4-9 所示應該實作 「 使用指數輪詢重試 」 等技術，以讓應用程式有機會處理暫時性失敗的資源。 您也應該在應用程式中使用 「 斷路器 」。 斷路器會停止應用程式嘗試存取資源時實際長期失敗。 藉由使用斷路器，應用程式可避免誘發阻絕服務本身。

![使用指數輪詢重試處理部分失敗](./media/image9.png)

> **圖 4 至 9。** 使用指數輪詢重試處理部分失敗

在 HTTP 資源和資料庫資源，您可以使用這些技術。 在 圖 4-9、 應用程式根據 3 層式架構，因此您必須在服務層級 (HTTP) 和資料層級 (TCP)，這些技術。 使用只單一應用程式層除了資料庫 （不含其他服務或微服務） 的整合型應用程式，在處理暫時性失敗，資料庫層級的連線可能就足夠了。 在此情況下，只是資料庫連接的特定組態則是必要項目。

實作具有恢復功能存取資料庫時，根據您使用的.NET 版本的通訊時可能很簡單 (例如[Entity Framework 6 或更新版本](/ef/ef6/fundamentals/connection-resiliency/retry-logic)。 它是只需設定資料庫連接）。 或者，您可能需要使用額外的程式庫，例如[暫時性錯誤處理應用程式區塊](https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50))（適用於舊版的.NET），或甚至是實作您自己的程式庫。

實作 HTTP 重試與斷路器時，適用於.NET 的建議是使用[Polly](https://github.com/App-vNext/Polly)目標.NET Framework 4.0，.NET Framework 4.5 和.NET Standard 1.1 中，其中包含.NET Core 支援程式庫。

若要了解如何實作的策略來處理雲端中的部分失敗，請參閱下列參考。

### <a name="additional-resources"></a>其他資源

- **實作具有恢復功能的通訊，來處理部分失敗**

    [https://docs.microsoft.com/dotnet/standard/microservices-architecture/implement-resilient-applications/partial-failure-strategies](../../microservices-architecture/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework 連接恢復功能和重試邏輯 （6 或更新版本）**

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **暫時性錯誤處理應用程式區塊**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **Polly 程式庫，適用於具有恢復功能的 HTTP 通訊**

    https://github.com/App-vNext/Polly

>[!div class="step-by-step"]
>[上一頁](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md)
>[下一頁](modernize-your-apps-with-monitoring-and-telemetry.md)
