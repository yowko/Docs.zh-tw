---
title: 附錄-適用于 WCF 開發人員的 gRPC
description: 討論分散式交易及其在現代化微服務架構中的執行方式。
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 10c4e77794c5ffe1aa6d5a629ce0b6cdf92f4ada
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184614"
---
# <a name="appendix-a---transactions"></a>附錄 A-交易

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

Windows Communication Foundation （WCF）支援的分散式交易，允許跨多個服務執行不可部分完成的作業。 此功能是以[Microsoft 分散式交易協調器](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85))為基礎。

在現代化的微服務環境中，這種類型的自動化分散式交易處理並不可行。 在遊戲中有太多不同的技術，包括關係資料庫、NoSQL 資料存放區和訊息系統，而不是要提及可能在單一環境中使用的作業系統、程式設計語言和架構組合。

WCF 分散式交易是所謂的[兩階段認可（2pc）](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)。 藉由協調服務之間的訊息、在每個服務中建立開啟的交易，以及根據成功或失敗傳送「認可」或「回復」訊息，可以手動執行2PC 交易。 不過，管理2PC 時所牽涉到的複雜性可能會隨著系統的演進而以指數方式增加，而開啟的交易則保有可能對效能造成負面影響的資料庫鎖定，因而導致跨服務的鎖死。

可能的話，最好完全避免分散式交易。 如果兩個數據的專案是因此連結成需要不可部分完成的更新，請考慮同時使用相同的服務來處理它們，並使用單一要求或訊息將那些不可部分完成的變更套用至該服務。

如果無法這麼做，則其中一種替代方式是使用[Saga 模式](https://microservices.io/patterns/data/saga.html)。 在 saga 中，更新會依序進行處理;當每個更新成功時，就會觸發下一個更新。 這些觸發程式可以從服務傳播到服務，或由 saga 協調器或「orchestrator」進行管理。 如果在程式中的任何時間點發生更新失敗，已完成其更新的服務會套用特定邏輯來將它們反轉。

另一個選項是使用網域導向設計（DDD）和命令/查詢責任隔離（CQRS），如[.Net 微服務電子書](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)中所述。 特別是，使用領域事件或[事件來源](https://martinfowler.com/eaaDev/EventSourcing.html)有助於確保更新在不會立即&mdash; &mdash;套用的情況下仍會一致。

>[!div class="step-by-step"]
>[上一步](application-performance-management.md)
