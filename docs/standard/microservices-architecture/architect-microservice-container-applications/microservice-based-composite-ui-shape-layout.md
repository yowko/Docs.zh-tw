---
title: 根據微服務建立複合 UI，包括多個微服務所產生的視覺 UI 形狀和配置
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 根據微服務建立複合 UI，包括多個微服務所產生的視覺 UI 形狀和配置
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.openlocfilehash: 79b63c376d25725b2bcb6c16cdb4d06e107d5c07
ms.sourcegitcommit: 6eac9a01ff5d70c6d18460324c016a3612c5e268
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/17/2018
ms.locfileid: "45641270"
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>根據微服務建立複合 UI，包括多個微服務所產生的視覺 UI 形狀和配置

微服務架構一開始通常是處理資料和邏輯的伺服器端。 不過，更進階的方法是同時根據微服務來設計應用程式 UI。 這表示具有微服務所產生的複合 UI，而不是在伺服器上擁有多個微服務，並只由一個整合型用戶端應用程式來取用這些微服務。 透過此方法，您建置的微服務就會同時具備邏輯和視覺表示。

圖 4-20 顯示更簡單的方法，該方法只會從整合型用戶端應用程式取用微服務。 當然，您在產生 HTML 與 JavaScript 之間可能會有 ASP.NET MVC 服務。 下圖已經過簡化，顯示您有取用微服務的單一 (整合型) 用戶端 UI，只著重於邏輯和資料，而不是 UI 形狀 (HTML 和 JavaScript)。

![](./media/image20.png)

**圖 4-20**： 取用後端微服務的整合型 UI 應用程式

相較之下，複合 UI 是由微服務本身精確地產生和撰寫而成。 部分微服務會支援特定 UI 區域的視覺形狀。 主要差異在於您有以範本為基礎的用戶端 UI 元件 (例如 TS 類別)，而且這些範本的資料成形 UI ViewModel 來自每個微服務。

用戶端應用程式啟動時，每個用戶端 UI 元件 (例如 TypeScript 類別) 會向基礎結構微服務註冊其本身，以便能夠針對指定案例提供 ViewModel。 如果微服務變更形狀，UI 也會變更。

圖 4-21 顯示此複合 UI 方法的版本。 這已經過簡化，因為您可能會有根據不同技術彙總更細緻部分的其他微服務，這取決於您建置的是傳統 Web 方法 (ASP.NET MVC) 或 SPA (單頁應用程式)。

![](./media/image21.png)

**圖 4-21**： 由後端微服務成形的複合 UI 應用程式範例

每個 UI 組合微服務會類似於小型 API 閘道。 但在本例中，每個微服務會負責一個很小的 UI 區域。

根據您所使用的 UI 技術，微服務導向的複合 UI 方法可能挑戰性很高，也可能很低。 例如，您不會使用與用來建置 SPA 或原生行動應用程式相同的技術來建置傳統 Web 應用程式 (例如開發 Xamarin 應用程式時，此方法的挑戰性可能更高)。

[eShopOnContainers](https://aka.ms/MicroservicesArchitecture) 範例應用程式使用整合型 UI 方法的原因有很多。 首先，它是微服務和容器的前導。 複合 UI 更進階，但在設計及開發 UI 時也需要更高的複雜度。 其次，eShopOnContainers 也提供以 Xamarin 為基礎的原生行動應用程式，因此在用戶端 \# 側會更複雜。

不過，建議您使用下列參考，深入了解以微服務為基礎的複合 UI。

## <a name="additional-resources"></a>其他資源

-   **使用 ASP.NET 的複合 UI (特定研討)**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga：微服務架構中的整合前端**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti：更佳 UI 組合的祕密**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic：將前端 Web 元件併入微服務**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **Managing Frontend in the Microservices Architecture (管理微服務架構中的前端)**\
    [*https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[上一頁](microservices-addressability-service-registry.md)
[下一頁](resilient-high-availability-microservices.md)
