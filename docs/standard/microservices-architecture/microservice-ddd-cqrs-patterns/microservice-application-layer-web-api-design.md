---
title: 設計微服務應用程式層及 Web API
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 設計微服務應用程式層及 Web API
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: e5c7e0acb0496aebce4d9cbe8cb51ced0c7166a2
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106602"
---
# <a name="designing-the-microservice-application-layer-and-web-api"></a>設計微服務應用程式層及 Web API

## <a name="using-solid-principles-and-dependency-injection"></a>使用 SOLID 準則及相依性插入

SOLID 準則是用於任何現代及任務關鍵性應用程式的重要技術，例如使用 DDD 模式開發微服務。 SOLID 是五個基本準則的縮寫：

-   單一責任準則 (Single Responsibility principle)

-   開啟/關閉準則 (Open/closed principle)

-   里斯可夫替代準則 (Liskov substitution principle)

-   介面隔離準則 (Interface Segregation principle)

-   相依性反轉準則 (Dependency Inversion principle)

SOLID 與您設計應用程式或微服務的內部層及減少其之間的相依性關係更為密切。 它與領域無關，而是與應用程式的技術設計有關。 最後一個準則，相依性反轉 (DI) 準則，可允許您將基礎結構層和剩餘的層分離，使其可更進一步的分離 DDD 層的實作。

DI 是一種實作相依性反轉準則的方式。 它是一種為了達到物件及其相依性間鬆散結合的技術。 類別要執行其動作所需的物件，會提供 (或「插入」) 給類別，而不是直接具現化共同作業者，或使用靜態參考。 大多數情況下，類別會透過其建構函式宣告它們的相依性，讓他們能遵循「明確相依性準則」。 DI 通常會基於特定的控制反轉 (IoC) 容器。 ASP.NET Core 提供了簡單的內建 IoC 容器，但您也可以使用您最愛的 IoC 容器，例如 Autofac 或 Ninject。

藉由遵循 SOLID 準則，您的類別自然而然會傾向小型、構造良好且輕鬆的測試。 但是如何才能知道您的類別已插入太多相依性？ 若您是透過建構函式使用 DI，您可以藉由查看您建構函式參數的數量來進行偵測。 若有太多的相依性，這通常表示 ([code smell (程式碼異味)](http://deviq.com/code-smells/)) 您的類別嘗試完成太多事項，並且可能違反了單一責任準則。

通常需要其他指南才能完整涵蓋 SOLID 的詳細資料。 因此，本指南僅需要您具備關於這些主題的最低程度知識。

#### <a name="additional-resources"></a>其他資源

-   **SOLID：基本 OOP 準則**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)

-   **Inversion of Control Containers and the Dependency Injection Pattern** (逆轉控制容器和相依性插入模式)
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)

-   **Steve Smith.接著劑：New**
    [*https://ardalis.com/new-is-glue*](https://ardalis.com/new-is-glue)


>[!div class="step-by-step"]
[上一頁](nosql-database-persistence-infrastructure.md)
[下一頁](microservice-application-layer-implementation-web-api.md)
