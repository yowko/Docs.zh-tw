---
title: 附錄-適用于 WCF 開發人員的 gRPC
description: 討論分散式交易及其在現代化微服務架構中的執行方式。
ms.date: 09/02/2019
ms.openlocfilehash: 9931681727f921e007c2f80852ad0e69cd7288de
ms.sourcegitcommit: 5fb5b6520b06d7f5e6131ec2ad854da302a28f2e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/03/2019
ms.locfileid: "74711474"
---
# <a name="appendix-a---transactions"></a>附錄 A-交易

Windows Communication Foundation （WCF）支援分散式交易，可讓您跨多個服務執行不可部分完成的作業。 此功能是以[Microsoft 分散式交易協調器](https://docs.microsoft.com/previous-versions/windows/desktop/ms684146(v=vs.85))為基礎。

在較新的微服務環境中，這種類型的自動化分散式交易處理並不可行。 牽涉到太多不同的技術，包括關係資料庫、NoSQL 資料存放區和訊息系統。 在單一環境中，可能也會混合使用作業系統、程式設計語言和架構。

WCF 分散式交易是所謂的[兩階段認可（2pc）](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)。 您可以透過協調服務之間的訊息、在每個服務中建立開啟的交易，以及傳送認可或回復訊息（視成功或失敗而定），以手動方式執行2PC 交易。 不過，管理2PC 時所牽涉到的複雜性可能會隨著系統的發展而以指數方式增加。 開啟交易會保存可能會對效能造成負面影響的資料庫鎖定，或更糟的會導致跨服務的鎖死。

可能的話，最好完全避免分散式交易。 如果有兩個數據的專案因需要不可部分完成的更新而連結，請考慮同時使用相同的服務來處理它們。 使用單一要求或訊息將這些不可部分完成的變更套用至該服務。

如果無法這麼做，則其中一種替代方式是使用[Saga 模式](https://microservices.io/patterns/data/saga.html)。 在 saga 中，更新會依序處理;當每個更新成功時，就會觸發下一個更新。 這些觸發程式可以從服務傳播到服務，或由 saga 協調器或 orchestrator 管理。 如果在程式中的任何時間點發生更新失敗，已完成其更新的服務會套用特定邏輯來將它們反轉。

另一個選項是使用網域導向設計（DDD）和命令/查詢責任隔離（CQRS），如[.Net 微服務電子書](https://docs.microsoft.com/dotnet/architecture/microservices/microservice-ddd-cqrs-patterns/)中所述。 特別是，使用領域事件或[事件來源](https://martinfowler.com/eaaDev/EventSourcing.html)有助於確保更新一致（如果未立即套用）。

>[!div class="step-by-step"]
>[上一篇](application-performance-management.md)
