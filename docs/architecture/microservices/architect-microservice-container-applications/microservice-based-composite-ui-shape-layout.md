---
title: 建立以微服務為基礎的複合 UI
description: 微服務架構不只可用於後端。 預覽以了解如何用於前端。
ms.date: 01/13/2021
ms.openlocfilehash: 3d866172cf7d15486dd2cc0d5dbb286c77693cea
ms.sourcegitcommit: a4cecb7389f02c27e412b743f9189bd2a6dea4d6
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/14/2021
ms.locfileid: "98189406"
---
# <a name="creating-composite-ui-based-on-microservices"></a>建立以微服務為基礎的複合 UI

微服務架構通常是從伺服器端處理資料和邏輯開始，但在許多情況下，UI 仍會以單體的方式處理。 不過，更先進的方法稱為 [微前端](https://martinfowler.com/articles/micro-frontends.html)，也就是根據微服務來設計您的應用程式 UI。 這表示具有微服務所產生的複合 UI，而不是在伺服器上擁有多個微服務，並只由一個整合型用戶端應用程式來取用這些微服務。 透過此方法，您建置的微服務就會同時具備邏輯和視覺表示。

圖 4-20 顯示更簡單的方法，該方法只會從整合型用戶端應用程式取用微服務。 當然，您在產生 HTML 與 JavaScript 之間可能會有 ASP.NET MVC 服務。 下圖已經過簡化，顯示您有取用微服務的單一 (整合型) 用戶端 UI，只著重於邏輯和資料，而不是 UI 形狀 (HTML 和 JavaScript)。

![連接至微服務的整合型 UI 應用程式圖表。](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

**圖 4-20**： 取用後端微服務的整合型 UI 應用程式

相較之下，複合 UI 是由微服務本身精確地產生和撰寫而成。 部分微服務會支援特定 UI 區域的視覺形狀。 主要差異在於您有以範本為基礎的用戶端 UI 元件 (例如 TypeScript 類別)，而且這些範本的資料成形 UI ViewModel 來自每個微服務。

用戶端應用程式啟動時，每個用戶端 UI 元件 (例如 TypeScript 類別) 會向基礎結構微服務註冊其本身，以便能夠針對指定案例提供 ViewModel。 如果微服務變更形狀，UI 也會變更。

圖 4-21 顯示此複合 UI 方法的版本。 這種方法已經過簡化，因為您可能會有其他微服務會匯總以不同技術為基礎的細微部分。 這取決於您建置的是傳統 Web 方法 (ASP.NET MVC) 或 SPA (單頁應用程式)。

![複合 UI 的圖表，由許多視圖模型組成。](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

**圖 4-21**： 由後端微服務成形的複合 UI 應用程式範例

每個 UI 組合微服務會類似於小型 API 閘道。 但在這種情況下，每一個都有一個小的 UI 區域。

根據您所使用的 UI 技術，微服務導向的複合 UI 方法可能挑戰性很高，也可能很低。 例如，您不會使用與用來建置 SPA 或原生行動應用程式相同的技術來建置傳統 Web 應用程式 (例如開發 Xamarin 應用程式時，此方法的挑戰性可能更高)。

[eShopOnContainers](https://aka.ms/MicroservicesArchitecture) 範例應用程式使用整合型 UI 方法的原因有很多。 首先，它是微服務和容器的前導。 複合 UI 更進階，但在設計及開發 UI 時也需要更高的複雜度。 其次，eShopOnContainers 也提供以 Xamarin 為基礎的原生行動應用程式，因此在用戶端 \# 側會更複雜。

不過，建議您使用下列參考，深入了解以微服務為基礎的複合 UI。

## <a name="additional-resources"></a>其他資源

- **微前端 (聖馬丁 Fowler 的 blog)**  
  <https://martinfowler.com/articles/micro-frontends.html>
  
- **微前端 (Michael Geers 網站)**  
  <https://micro-frontends.org/>
  
- **使用 ASP.NET 的複合 UI (特定研討)**  
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- **Ruben Oostinga。微服務架構中的整合前端**  
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- **Mauro Servienti。更好的 UI 組合秘密**  
  <https://particular.net/blog/secret-of-better-ui-composition>

- **Viktor Farcic.將 Front-End Web 元件納入微服務**  
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- **Managing Frontend in the Microservices Architecture (管理微服務架構中的前端)**  
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
>[上一個](microservices-addressability-service-registry.md) 
>[下一步](resilient-high-availability-microservices.md)
