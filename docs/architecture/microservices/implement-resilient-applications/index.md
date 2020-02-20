---
title: 執行彈性應用程式
description: 了解彈性這個微服務架構中的核心概念。 您必須知道如何在發生暫時性失敗時進行正常處理。
ms.date: 01/30/2020
ms.openlocfilehash: ccdb2470c727ad4bd89c4e0634da8564b8010e63
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502648"
---
# <a name="implement-resilient-applications"></a>執行彈性應用程式

*您的微服務和雲端式應用程式必須接受最後才會發生的部分失敗。您必須將應用程式設計為可復原那些部分失敗。*

復原是從失敗中復原並繼續運作的能力。 這不是為了避免失敗，而是要接受失敗將會發生的事實，並以避免停機或資料遺失的方式予以回應。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

設計和部署微服務應用程式的挑戰性就已經很高。 但您還必須確保應用程式在必然會發生某些失敗的環境中繼續執行。 因此，您的應用程式應該能夠復原。 它應該設計成能夠回應部分失敗，如網路中斷，或是雲端中的節點或 VM 沒有回應。 即使是微服務 (容器) 移至叢集中的其他節點，也會導致應用程式內發生間歇且短暫性失敗。

您應用程式的許多個別元件也應該納入狀況監控功能。 您可以遵循本章中的指引，建立即使在複雜的雲端式部署中發生暫時性停機或一般延遲的情況下也能順暢運作的應用程式。

>[!IMPORTANT]
> eShopOnContainer 已使用 Polly 連結[庫](http://www.thepollyproject.org/)，在發行3.0.0 之前，使用具[類型的用戶端](./use-httpclientfactory-to-implement-resilient-http-requests.md)來執行復原。
>
> 從 release 3.0.0 開始，會使用[Linkerd 網格](https://linkerd.io/)來執行 HTTP 呼叫復原，以在 Kubernetes 叢集中以透明且可設定的方式處理重試，而不必處理常式代碼中的那些疑慮。
>
> Polly 程式庫仍然用來增加資料庫連接的恢復功能，特別是在啟動服務時。

>[!WARNING]
> 在使用 Linkerd 之前，本節中的所有程式碼範例都是有效的，而且不會更新以反映目前的實際程式碼。 因此，它們在本節內容中是合理的。

>[!div class="step-by-step"]
>[上一頁](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[下一頁](handle-partial-failure.md)
