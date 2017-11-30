---
title: "套用微服務的簡化的 CQRS 和 DDD 模式"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |套用微服務的簡化的 CQRS 和 DDD 模式"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 99fd7ce32039742e23f8e01aa4c33cddd7a9f698
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="applying-simplified-cqrs-and-ddd-patterns-in-a-microservice"></a>套用微服務的簡化的 CQRS 和 DDD 模式

CQRS 會分隔模型來進行讀取和寫入資料的架構模式。 相關的詞彙[命令查詢分離 (CQS)](https://martinfowler.com/bliki/CommandQuerySeparation.html)原本他活頁簿中定義由 Bertrand 慧君*物件導向軟體建構*。 基本概念是，您可以將分割分成兩個加深而大幅分隔分類系統的作業：

-   查詢。 這些傳回結果，不會變更系統的狀態，而且是免費的副作用。

-   命令。 這些變更系統狀態。

CQS 是簡單的概念，它是關於相同物件中的方法正在查詢或命令。 每個方法會傳回狀態或狀態，但兩者不會改變。 甚至單一的儲存機制模式的物件可以遵守 CQS。 CQS 可以考量的基本原則 CQRS。

[命令和查詢責任隔離 (CQRS)](https://martinfowler.com/bliki/CQRS.html)已引進 Greg Young，而且強烈升級 Udi Dahan 等等。 它根據 CQS 原則，雖然會更詳細說明。 它可以視為基礎命令和事件加上選擇性地在非同步訊息模式。 在許多情況下，CQRS 與相關的更進階的案例，像是讓不同的實體資料庫的讀取 （查詢） 比寫入 （更新）。 此外，可能會實作更進化的 CQRS 系統[事件來源 (ES)](http://codebetter.com/gregyoung/2010/02/20/why-use-event-sourcing/)更新資料庫，所以您會只儲存事件中的網域模型，而不是儲存目前的狀態資料。 不過，這不是使用本指南中; 中的方法我們使用簡單的 CQRS 方法，只要從命令分隔的查詢所組成。

CQRS 分離層面被達成分組為一個圖層中的查詢作業和另一個圖層中的命令。 每個圖層有它自己的資料模型 （請注意我們說模型中，不一定是不同的資料庫），而且會根據您使用自己的模式和技術的組合。 更重要的是，兩個圖層可以是相同的階層或微服務，（排序微服務），例如用於本指南中。 或者，他們可能會實作上不同 microservices 或處理程序，才能最佳化以及向外延展個別而不會影響另一個。

CQRS 表示會有兩個物件的讀取/寫入作業，在其他內容中有一個。 有原因有反正規化的讀取資料庫，您可以在更進階的 CQRS 文獻中學習。 但我們不使用以下，該方法的目標在於的查詢，而不是限制與條件約束從 DDD 模式，例如彙總查詢中有更大的彈性。

舉例來說，這種服務是從 eShopOnContainers 參考應用程式排序的微服務。 此服務會實作簡單的 CQRS 方法為基礎的微服務。 它會使用單一資料來源或資料庫，但兩個邏輯模型加上 DDD 模式對於交易式的網域，如圖 9-2 所示。

![](./media/image2.png)

**圖 9 2**。 簡化 CQRS 和 DDD 型微服務

應用程式層都可以是 Web API 本身。 重要的設計層面以下取自微服務有分割的查詢和 ViewModels （特別是建立用戶端應用程式的資料模型） 命令、 網域模型，與下列 CQRS 模式的交易。 這個方法會保留查詢無關的限制與來自 DDD 模式，才有意義的交易與更新，稍後的章節中所述的條件約束。


>[!div class="step-by-step"]
[上一個](index.md) [下一步] (eshoponcontainers-cqrs-ddd-microservice.md)
