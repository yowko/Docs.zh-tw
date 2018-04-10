---
title: 實作復原應用程式
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 實作復原應用程式
keywords: Docker, 微服務, ASP.NET, 容器
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 93e5435b402cc1a8ff049f25465de0f719516f31
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-resilient-applications"></a>實作復原應用程式

您的微服務和與雲端式應用程式必須接受部分失敗終究是不可避免的。您必須將應用程式設計成可從這些部分失敗中復原。

「復原」是指能夠從失敗中復原並繼續運作的能力。 它不是為了避免失敗，而是接受失敗將會發生的事實，並以避免停機或資料遺失的方式對失敗做出回應。 復原的目標是在失敗後將應用程式返回完全運作的狀態。

設計和部署微服務應用程式的挑戰性就已經很高。 但您還必須確保應用程式在必然會發生某些失敗的環境中繼續執行。 因此，您的應用程式應該能夠復原。 它應該設計成能夠回應部分失敗，如網路中斷，或是雲端中的節點或 VM 沒有回應。 即使是微服務 (容器) 移至叢集中的其他節點，也會導致應用程式內發生間歇且短暫性失敗。

您應用程式的許多個別元件也應該納入狀況監控功能。 您可以遵循本章中的指引，建立即使在複雜的雲端式部署中發生暫時性停機或一般延遲的情況下也能順暢運作的應用程式。


>[!div class="step-by-step"]
[上一個] (../microservice-ddd-cqrs-patterns/microservice-application-layer-implementation-web-api.md) [下一個] (handle-partial-failure.md)
