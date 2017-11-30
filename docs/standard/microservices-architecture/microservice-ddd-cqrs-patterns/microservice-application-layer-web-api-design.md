---
title: "設計微服務應用程式層和 Web API"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |設計微服務應用程式層和 Web API"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7509b470a30005dd48fa88eefa91f7ed241e4e09
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/18/2017
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>設計微服務應用程式層和 Web API

## <a name="using-solid-principles-and-dependency-injection"></a>使用純色的原則和相依性插入

純色的原則是重要的技術，以用於任何現代和業務關鍵應用程式，例如開發與 DDD 模式微服務。 實線是為縮寫字的五個群組的基本原則：

-   單一責任原則

-   開啟/關閉原則

-   Liskov 替代的原則

-   反轉隔離原則

-   相依性反向原則

實線是更多有關您如何設計應用程式或微服務內部層級，以及減少之間的相依性。 沒有關聯到網域，但應用程式的技術設計。 最後一個原則，也就是相依性反向 (DI) 原則，可讓您分離其餘的圖層，可讓 DDD 圖層的好解除解合的實作基礎結構層。

DI 是一種方式實作的相依性反向原則。 它是針對達到物件及其相依性之間的鬆散偶合的技術。 而非直接具現化共同作業者，或使用靜態參考，才能執行其動作的類別需要的物件是提供給 （或 「 插入 」） 的類別。 大多數情況下，類別會宣告透過其建構函式，讓他們遵循明確的相依性原則及其相依性。 DI 通常根據特定的逆轉控制 (IoC) 容器。 ASP.NET Core 提供簡單的內建 IoC 容器，但您也可以使用您最愛的 IoC 容器，例如 Autofac 或 Ninject。

依照實心原則，類別通常會自然小型、 構造良好且輕鬆地測試過。 但是，您要如何知道是否太多的相依性會被插入您的類別？ 如果您使用 DI 透過建構函式時，就可輕易偵測出只要查看您建構函式的參數數目。 如果有太多的相依性，這通常是一個符號 ([程式碼氣味](http://deviq.com/code-smells/)) 嘗試太多，您的類別，並可能會違反單一責任原則。

需要其他的指南，以涵蓋詳細的實線。 因此，本指南必須要有這些主題的最小知識。

#### <a name="additional-resources"></a>其他資源

-   **實線： 基本 OOP 原則**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **逆轉控制容器和相依性插入模式**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith。新是黏附**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[上一個](nosql-資料庫-持續性-infrastructure.md) [下一步] (microservice-application-layer-implementation-web-api.md)
