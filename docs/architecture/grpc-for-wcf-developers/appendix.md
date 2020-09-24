---
title: 附錄-WCF 開發人員的 gRPC
description: 分散式交易及其在新式微服務架構中的實作討論。
ms.date: 09/02/2019
ms.openlocfilehash: f60899463a13e9f740f6ae63150d18eab3069124
ms.sourcegitcommit: 5b475c1855b32cf78d2d1bbb4295e4c236f39464
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2020
ms.locfileid: "91165854"
---
# <a name="appendix-a---transactions"></a>附錄 A-交易

Windows Communication Foundation (WCF) 支援分散式交易，可讓您跨多個服務執行不可部分完成的作業。 這項功能是以 [Microsoft Distributed Transaction Coordinator](/previous-versions/windows/desktop/ms684146(v=vs.85))為基礎。

在較新的微服務環境中，無法進行這種類型的自動分散式交易處理。 牽涉到許多不同的技術，包括關係資料庫、NoSQL 資料存放區，以及訊息系統。 在單一環境中，也可能會混用作業系統、程式設計語言和架構。

WCF 分散式交易是所謂的 [兩階段認可的實 (2pc) ](https://en.wikipedia.org/wiki/Two-phase_commit_protocol)。 您可以藉由協調服務之間的訊息、在每個服務中建立開啟的交易，以及傳送認可或回復訊息（視成功或失敗而定），以手動方式執行2PC 交易。 但是，管理2PC 時所牽涉到的複雜性會隨著系統演進而以指數方式增加。 開啟交易會保存可能對效能造成負面影響的資料庫鎖定，或更糟的原因會導致跨服務的鎖死。

可能的話，最好完全避免分散式交易。 如果有兩個數據專案連結為需要不可部分完成的更新，請考慮使用相同的服務來處理它們。 使用單一要求或訊息將這些不可部分完成的變更套用至該服務。

如果無法這麼做，則有一個替代方法是使用 [Saga 模式](https://microservices.io/patterns/data/saga.html)。 在 saga 中，更新會依序處理;每次更新成功時，就會觸發下一個更新。 這些觸發程式可以從服務傳播至服務，或由 saga 協調器或協調器進行管理。 如果在處理期間的任何時間點更新失敗，已完成其更新的服務會套用特定邏輯以將其還原。

另一個選項是使用網域導向設計 (DDD) 和命令/查詢責任隔離 (CQRS) ，如 [.Net 微服務電子書](../microservices/microservice-ddd-cqrs-patterns/index.md)中所述。 尤其是，使用領域事件或 [事件來源](https://martinfowler.com/eaaDev/EventSourcing.html) 有助於確保一致地套用更新（如果不會立即套用）。

>[!div class="step-by-step"]
>[[上一步]](application-performance-management.md)
