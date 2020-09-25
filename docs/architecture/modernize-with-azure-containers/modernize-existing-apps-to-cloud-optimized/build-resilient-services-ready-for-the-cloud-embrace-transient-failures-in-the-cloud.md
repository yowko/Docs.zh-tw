---
title: 打造適用于雲端的復原服務。 接受雲端中的暫時性失敗
description: 使用 Azure 雲端和 Windows 容器將現有的 .NET 應用程式現代化 |打造適用于雲端的復原服務。 接受雲端中的暫時性失敗
ms.date: 04/30/2018
ms.openlocfilehash: 8e9f1eda71e4b98a56cbfc1c7a4ff34e67bee3f4
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91172153"
---
# <a name="build-resilient-services-ready-for-the-cloud-embrace-transient-failures-in-the-cloud"></a>建置準備好在雲端執行的彈性服務：接受雲端中的暫時性失敗

復原是從失敗中復原並繼續運作的能力。 復原不是為了避免失敗，而是要接受失敗的事實，然後以避免停機或資料遺失的方式回應。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

當您的應用程式至少會執行以軟體為基礎的復原模型，而不是以硬體為基礎的模型時，您的應用程式就已準備好使用雲端。 您的雲端應用程式必須採用一定會發生的部分失敗。 設計或局部重構您的應用程式，以透過預期的部分失敗來達到復原能力。 其設計目的是要處理部分失敗，例如暫時性的網路中斷和節點，或在雲端中損毀的 Vm。 即使是移至 orchestrator 叢集中不同節點的容器，也可能會導致應用程式中發生間歇性的短暫失敗。

## <a name="handling-partial-failure"></a>處理部分失敗

在雲端式應用程式中，有部分失敗的風險存在。 比方說，單一網站實例或容器可能會失敗，或是短時間可能無法使用或沒有回應。 或者，單一 VM 或伺服器可能會損毀。

由於用戶端和服務是不同的進程，因此服務可能無法及時回應用戶端的要求。 服務可能會多載且回應速度變慢，或可能因為網路問題而無法存取一小段時間。

例如，假設有一個可在 Azure SQL Database 中存取資料庫的整合型 .NET 應用程式。 如果 Azure SQL database 或其他任何協力廠商服務沒有回應短暫的時間 (Azure SQL database 可能會移至不同的節點或伺服器，而且沒有回應幾秒鐘的時間) ，當使用者嘗試執行任何動作時，應用程式可能會損毀，並同時顯示例外狀況。

使用 HTTP 服務的應用程式可能會發生類似的情況。 在短暫的暫時性失敗期間，網路或服務本身可能無法在雲端中使用。

如圖4-9 中所示的復原性應用程式應該採用「以指數輪詢重試」之類的技術，讓應用程式有機會處理資源中的暫時性失敗。 您也應該在您的應用程式中使用「斷路器」。 當應用程式實際上是長期失敗時，斷路器會阻止應用程式嘗試存取資源。 藉由使用斷路器，應用程式可避免誘發本身的拒絕服務。

![以指數輪詢重試所處理部分失敗的圖表。](./media/retry-partial-failures.png)

**圖4-9。** 以指數輪詢重試處理的部分失敗

您可以在 HTTP 資源和資料庫資源中使用這些技術。 在圖4-9 中，應用程式是以三層架構為基礎，因此您在服務層級需要這些技術， (HTTP) 和資料層層級 (的 TCP) 。 在只使用單一應用層的整合型應用程式中， (沒有額外的服務或微服務) ，處理資料庫連接層級的暫時性失敗可能就已足夠。 在該情況下，只需要特定的資料庫連接設定。

當您在執行可存取資料庫的復原通訊時，視您使用的 .NET 版本而定，它可以很簡單 (例如， [Entity Framework 6 或更新](/ef/ef6/fundamentals/connection-resiliency/retry-logic)版本。 這只是設定資料庫連接) 。 或者，您可能需要使用其他程式庫（例如 [暫時性錯誤處理應用程式區塊](/previous-versions/msp-n-p/hh680934(v=pandp.50)) (針對舊版 .net) ），或甚至是執行您自己的程式庫。

當您執行 HTTP 重試和斷路器時，.NET 的建議是使用 [Polly](https://github.com/App-vNext/Polly) 程式庫，該程式庫的目標 .NET Framework 4.0、.NET Framework 4.5 和 .NET Standard 1.1，其中包括 .net Core 支援。

若要瞭解如何在雲端中執行處理部分失敗的策略，請參閱下列參考。

### <a name="additional-resources"></a>其他資源

- **執行復原通訊來處理部分失敗**

    [https://docs.microsoft.com/dotnet/architecture/microservices/implement-resilient-applications/partial-failure-strategies](../../microservices/implement-resilient-applications/partial-failure-strategies.md)

- **Entity Framework 連接復原和重試邏輯 (第6版和更新版本) **

    [https://docs.microsoft.com/ef/ef6/fundamentals/connection-resiliency/retry-logic](/ef/ef6/fundamentals/connection-resiliency/retry-logic)

- **暫時性錯誤處理應用程式區塊**

- <https://docs.microsoft.com/previous-versions/msp-n-p/hh680934(v=pandp.50)>

- **適用于復原 HTTP 通訊的 Polly 程式庫**

    <https://github.com/App-vNext/Polly>

>[!div class="step-by-step"]
>[上一個](when-to-deploy-windows-containers-to-azure-container-service-kubernetes.md) 
>[下一步](modernize-your-apps-with-monitoring-and-telemetry.md)
