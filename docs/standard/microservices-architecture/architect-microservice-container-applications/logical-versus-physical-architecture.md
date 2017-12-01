---
title: "與實體架構的邏輯架構"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |與實體架構的邏輯架構"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 635774a8fcd0cf1c0ede6a73c604071f538a37fd
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="logical-architecture-versus-physical-architecture"></a>與實體架構的邏輯架構

會很有用，此時若要停止，並討論邏輯架構和實體架構，和如何這適用於微服務為基礎的應用程式的設計之間的差別。

若要開始，建置 microservices 不需要任何特定技術的使用。 比方說，Docker 容器不是強制性，才能建立微服務為基礎的架構。 這些 microservices 也無法做為一般的處理序執行。 Microservices 是邏輯架構。

此外，即使微服務無法實體方式實作成單一服務、 處理序或容器 (為了簡單起見，是在初始的版本中所採取的方法[eShopOnContainers](http://aka.ms/MicroservicesArchitecture))，這之間的同位檢查商務微服務和實體的服務或容器是不一定需要在所有情況下當您建置許多數十個或甚至數百個服務所組成的大型且複雜的應用程式。

這是 where 沒有應用程式的邏輯架構和實體架構之間的差異。 邏輯架構和系統的邏輯界限不一定會對應一對一實體或部署的架構。 還是有可能發生，但它通常沒有。

雖然您可能會發現特定商務 microservices 或繫結的內容，不表示的最佳方式將它們實作一律會藉由建立單一服務 （例如 ASP.NET Web API) 或單一 Docker 容器的每個商務微服務。 規則，指出每個商務微服務會有單一的服務實作，或容器太嚴格。

因此，「 商務微服務 」 或 「 繫結內容是邏輯架構 （或停用），同時可能會發生與實體架構。 很重要的一點是，商務微服務或繫結的內容必須是自發允許程式碼和狀態，進行獨立版本設定，部署，以及縮放。

如圖 4-8 所示，類別目錄商務微服務無法撰寫的數個服務或處理序。 這些可能是多個 ASP.NET Web API 服務或任何其他種類的服務使用 HTTP 或任何其他通訊協定。 更重要的是，服務無法共用相同的資料，只要這些服務是凝聚力相對於相同商務網域。

![](./media/image8.png)

**圖 4-8**。 數個實體的服務與商務微服務

此範例中的服務會共用相同的資料模型，因為 Web API 服務為目標的搜尋服務相同的資料。 因此，在實體商務微服務實作中，因此您可以視需要調整每個這些內部服務向上或向下會分割該功能。 可能只有 Web API 服務通常需要更多執行個體比搜尋服務，反之亦然。）

簡單地說，microservices 的邏輯架構一律沒有與實際的部署架構一致。 本指南中，每當我們曾經提到的微服務，是指商務或無法對應至一或多個服務的邏輯微服務。 在大部分情況下，這會是一項服務，但可能更多。


>[!div class="step-by-step"]
[上一個](資料-sovereignty-每個-microservice.md) [下一步] (分散式的資料-management.md)
