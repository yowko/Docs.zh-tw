---
title: 雲端原生通訊模式
description: 瞭解雲端原生應用程式中的重要服務通訊考慮
author: robvet
ms.date: 08/31/2019
ms.openlocfilehash: 3bda9baa516b7bd8f893e0f58bbe5e2bfde2b61d
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71214015"
---
# <a name="cloud-native-communication-patterns"></a>雲端原生通訊模式

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

在建立雲端原生系統時，通訊會成為重要的設計決策。 前端用戶端應用程式如何與後端微服務通訊？ 後端微服務如何彼此通訊？ 在雲端原生應用程式中執行通訊時，需要考慮哪些原則、模式和最佳作法？

## <a name="communication-considerations"></a>通訊考慮

在整合型應用程式中，通訊非常簡單。 程式碼模組會在伺服器上的同一個可執行空間（進程）中一起執行。 當所有專案都在共用記憶體中一起執行時，這個方法可能會有效能上的優勢，但會產生緊密結合的程式碼，而變得很容易維護、演進和調整。

雲端原生系統會實微服務架構，其中包含許多小型、獨立的微服務。 每個微服務會在個別的進程中執行，且通常會在部署至叢集*的容器內執行。*

叢集會將虛擬機器的集區群組在一起，以形成高可用性的環境。 它們是使用協調流程工具來管理，負責部署和管理容器化微服務。 圖4-1 顯示使用完全受控[Azure Kubernetes 服務](https://docs.microsoft.com/azure/aks/intro-kubernetes)部署到 azure 雲端的[Kubernetes](https://kubernetes.io)叢集。

![Azure 中的 Kubernetes 叢集](./media/kubernetes-cluster-in-azure.png)

**圖 4-1**： Azure 中的 Kubernetes 叢集

在整個叢集中，微服務透過 Api 和訊息技術彼此通訊。

雖然它們提供許多優點，但微服務沒有免費的午餐。 元件之間的本機同進程方法呼叫現在已由網路呼叫取代。 每個微服務都必須透過網路通訊協定進行通訊，這會增加系統的複雜度：

- 網路擁塞、延遲和暫時性錯誤是一大考慮。

- 復原（也就是重試失敗的要求）是不可或缺的。

- 有些呼叫必須具有[等冪](https://www.restapitutorial.com/lessons/idempotency.html)性，才能保持一致的狀態。

- 每個微服務都必須驗證和授權呼叫。

- 每個訊息都必須經過序列化，然後再還原序列化-這可能很耗費資源。

- 訊息加密/解密變得很重要。

書籍[.net 微服務：容器化 .net 應用程式](https://docs.microsoft.com/dotnet/standard/microservices-architecture/)的架構（可從 Microsoft 免費取得）提供微服務應用程式通訊模式的深入涵蓋範圍。 在本章中，我們會提供這些模式的高階概述，以及 Azure 雲端中可用的實作為選項。

在本章中，我們會先解決前端應用程式與後端微服務之間的通訊。 然後，我們將探討後端微服務彼此通訊。 我們將探討 up 和 gRPC 通訊技術。 最後，我們將使用服務網格技術來探討新的創新通訊模式。 我們也將瞭解 Azure 雲端如何提供不同種類的支援*服務*，以支援雲端原生通訊。

>[!div class="step-by-step"]
>[上一頁](other-deployment-options.md)
>[下一頁](front-end-communication.md)
