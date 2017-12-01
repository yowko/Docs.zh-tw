---
title: "微服務架構"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |Microservices 架構"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 5ede1f0ad19270ca6b7556ff1bb7e4cf8ccf7cbe
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/21/2017
---
# <a name="microservices-architecture"></a>微服務架構

正如其名，microservices 架構就會是一種方法建立的一組小型服務的伺服器應用程式。 每個服務會在自己的處理序中執行，並使用通訊協定，例如 HTTP/HTTPS，WebSockets，其他處理程序與通訊或[AMQP](https://en.wikipedia.org/wiki/Advanced_Message_Queuing_Protocol)。 每個微服務實作特定的端對端網域或在特定內容界限內的商務功能，每個必須獨立開發和獨立不可配置。 最後，每個微服務應該擁有網域邏輯 （sovereignty 和分散式的資料管理） 根據不同的資料儲存技術 （SQL、 NoSQL） 和不同的程式設計語言及其相關的網域資料模型。

微服務應該是何種大小？ 在開發微服務時，大小不能很重要的一點。 相反地，很重要的一點應該建立鬆散耦合服務因此需要自主性的開發、 部署和小數位數，每個服務。 當然，當識別並設計 microservices 時，您應該嘗試使其越小越好，只要您不需要與其他 microservices 太多直接相依性。 更重要的微服務的大小大於它必須要有內部一致性和獨立於其他服務。

Microservices 架構為何？ 簡單地說，它提供長期的靈活度。 Microservices 複雜、 大，且高度可擴充的系統中啟用更佳的可維護性，讓您建立基礎，其各有細微和自發生命週期的許多可獨立部署服務的應用程式。

另一個好處是，microservices 可以向外延展獨立。 您不需要單一的整合應用程式，您必須向外擴充做為一個單位，您可以改為向外擴充特定 microservices。 這樣一來，您可以調整只需要較多處理電源或網路頻寬需求，而不是向外延展的應用程式不需要調整其他區域所支援的功能區域。 這表示節省成本，因為您需要較少的硬體。

![](./media/image6.png)

**圖 4-6**。 整合的部署與 microservices 方法

如圖 4-6 所示，microservices 方法允許敏捷式軟體開發的變更和快速的反覆項目的每個微服務，因為您可以變更的複雜、 大，且可延展的應用程式特定的小型區域。

更細緻的 microservices 應用程式可讓持續整合及連續傳遞作法架構。 它也會提升新函式的傳遞至應用程式。 更細緻的組合的應用程式也可讓您執行及測試 microservices 隔離中，並維持清除它們之間的合約、 發展。 只要您不要變更合約的介面，您可以變更任何微服務的內部實作，或加入新的功能，而不會中斷其他 microservices。

以下是要啟用成功移到實際執行環境與 microservices 為基礎的系統中的重要層面：

-   監視與健全狀況檢查的服務和基礎結構。

-   可擴充的服務 （也就是雲端及 orchestrators） 的基礎結構。

-   安全性設計和實作多個層級： 驗證、 授權、 密碼管理、 安全通訊等。

-   快速應用程式傳遞，通常會有不同的小組將焦點放在不同的 microservices。

-   DevOps 與 CI/CD 的作法和基礎結構。

其中前, 三個是涵蓋或本指南中導入。 最後兩個點，與應用程式生命週期，會包含在其他[容器化 Docker 應用程式生命週期的 Microsoft 平台和工具](https://aka.ms/dockerlifecycleebook)電子書。

## <a name="additional-resources"></a>其他資源

-   **Mark Russinovich。Microservices： 由雲端應用程式 revolution**
    [*https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/*](https://azure.microsoft.com/blog/microservices-an-application-revolution-powered-by-the-cloud/)

-   **Martin Fowler：Microservices**
    [*http://www.martinfowler.com/articles/microservices.html*](http://www.martinfowler.com/articles/microservices.html)

-   **Martin Fowler：微服務必要條件**
    [*http://martinfowler.com/bliki/MicroservicePrerequisites.html*](http://martinfowler.com/bliki/MicroservicePrerequisites.html)

-   **Jimmy Nilsson：區塊雲端運算**
    [*https://www.infoq.com/articles/CCC-Jimmy-Nilsson*](https://www.infoq.com/articles/CCC-Jimmy-Nilsson)

-   **Cesar de la Torre：容器化 Microsoft 平台和工具與 Docker 的應用程式生命週期**（可下載的電子書） [ *https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)




>[!div class="step-by-step"]
[上一個](服務-導向-architecture.md) [下一步] (資料-sovereignty-每個-microservice.md)
