---
title: 實現彈性應用程式
description: 了解彈性這個微服務架構中的核心概念。 您必須知道如何在瞬態故障發生時正常處理它們。
ms.date: 01/30/2020
ms.openlocfilehash: 46276a6b9b36a494bfae657275692ca9d5554d86
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "78847228"
---
# <a name="implement-resilient-applications"></a>實現彈性應用程式

*您的微服務和基於雲的應用程式必須接受最終肯定會發生的部分故障。您必須將應用程式設計為對這些部分故障具有彈性。*

復原是從失敗中復原並繼續運作的能力。 這不是為了避免失敗，而是要接受失敗將會發生的事實，並以避免停機或資料遺失的方式予以回應。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

設計和部署微服務應用程式的挑戰性就已經很高。 但您還必須確保應用程式在必然會發生某些失敗的環境中繼續執行。 因此，您的應用程式應該能夠復原。 它應該設計成能夠回應部分失敗，如網路中斷，或是雲端中的節點或 VM 沒有回應。 即使是微服務 (容器) 移至叢集中的其他節點，也會導致應用程式內發生間歇且短暫性失敗。

您應用程式的許多個別元件也應該納入狀況監控功能。 您可以遵循本章中的指引，建立即使在複雜的雲端式部署中發生暫時性停機或一般延遲的情況下也能順暢運作的應用程式。

>[!IMPORTANT]
> eShopOnContainer 一直在使用[Polly 庫](http://www.thepollyproject.org/)在版本 3.0.0 之前使用[類型用戶端](./use-httpclientfactory-to-implement-resilient-http-requests.md)實現恢復能力。
>
> 從版本 3.0.0 開始，HTTP 調用恢復能力使用[Linkerd 網格](https://linkerd.io/)實現，該網格在 Kubernetes 群集中以透明且可配置的方式處理重試，而無需在代碼中處理這些問題。
>
> Polly 庫仍用於向資料庫連接添加恢復能力，特別是在啟動服務時。

>[!WARNING]
> 在使用 Linkerd 之前，本節中的所有代碼示例都有效，並且不會更新以反映當前實際代碼。 因此，它們在本節中具有意義。

>[!div class="step-by-step"]
>[上一個](../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md)
>[下一個](handle-partial-failure.md)
