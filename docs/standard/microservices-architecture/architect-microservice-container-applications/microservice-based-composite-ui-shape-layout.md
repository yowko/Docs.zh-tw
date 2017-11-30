---
title: "根據建立複合 UI microservices，包括 visual UI 圖形和多個 microservices 所產生的版面配置"
description: "容器化的.NET 應用程式的.NET Microservices 架構 |根據建立複合 UI microservices，包括 visual UI 圖形和多個 microservices 所產生的版面配置"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 4b32fed5eb0de02b01665efa4368eb83e3fda08d
ms.sourcegitcommit: e99dfadbca1992c187179b6a3b42bef44534ebb6
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/01/2017
---
# <a name="creating-composite-ui-based-on-microservices-including-visual-ui-shape-and-layout-generated-by-multiple-microservices"></a>根據建立複合 UI microservices，包括 visual UI 圖形和多個 microservices 所產生的版面配置

使用伺服器端處理資料和邏輯通常開始 Microservices 架構。 不過，更進階的方法是設計的 UI 根據 microservices 以及應用程式。 這表示具有 microservices，而不需要在伺服器與剛整合型用戶端應用程式耗用 microservices 上的 microservices 所產生的複合 UI。 使用此方法時，您建置 microservices 可以是完整的邏輯和視覺化表示。

圖 4-20 顯示只使用 microservices 從龐大的用戶端應用程式的更簡單的方法。 當然，您可能會產生 HTML 和 JavaScript 之間的 ASP.NET MVC 服務。 圖已簡化反白顯示您有單一 （龐大） 用戶端 UI 耗用 microservices，把重點放在邏輯與資料，而不是在 UI 圖形 （HTML 和 JavaScript）。

![](./media/image20.png)

**圖 4-20**。 使用後端 microservices 龐大 UI 應用程式

相較之下，複合 UI 精確地產生並由 microservices 本身組成。 某些 microservices 磁碟機視覺 UI 的特定區域的形狀。 主要差異是，您必須根據範本，用戶端 UI 元件 （例如 TS 類別），而且這些範本資料成形 UI ViewModel 來自每個微服務。

在用戶端應用程式啟動時，每個用戶端 UI 元件 （例如 TypeScript 類別） 註冊其本身與基礎結構微服務能夠提供 ViewModels 特定案例。 如果微服務變更形狀，UI 也會變更。

圖 4-21 顯示此複合 UI 方法的版本。 這已經過簡化，因為您可能會有彙總不同的技術為基礎的精細的部分其他 microservices — 這取決於您要建置的傳統 web 方法 (ASP.NET MVC) 或 SPA （單一頁面應用程式）。

![](./media/image21.png)

**圖 4-21**。 後端 microservices 塑造的複合 UI 應用程式範例

每個這些 UI 組合 microservices 會是類似於小型的 API 閘道。 但在此情況下每一個都是負責小的 UI 區域。

由 microservices 所驅動的複合 UI 方法可以是更具挑戰性或較少，依據哪些 UI 技術使用。 比方說，您將不使用相同的技術來建置建置 SPA 或原生行動裝置應用程式使用的傳統 web 應用程式 （做為開發的 Xamarin 應用程式，它可以是這種方法更具挑戰性）。

[EShopOnContainers](http://aka.ms/MicroservicesArchitecture)範例應用程式使用整合型 UI 方法可能有多種原因。 首先，它是 microservices 和容器的簡介。 複合 UI 更進階的但也需要進一步的設計和開發 UI 時的複雜性。 第二，eShopOnContainers 也提供原生行動應用程式根據是否有讓它更複雜 C 在用戶端的 Xamarin\#側邊。

不過，我們建議您若要深入了解複合 UI 根據 microservices 使用下列的參考。

## <a name="additional-resources"></a>其他資源

-   **使用 ASP.NET (特定的 Workshop 中) 的複合 UI**
    [*http://go.particular.net/workshop-composite-ui-demo*](http://go.particular.net/workshop-composite-ui-demo)

-   **Ruben Oostinga。在 Microservices 架構整合前端**
    [*http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/*](http://blog.xebia.com/the-monolithic-frontend-in-the-microservices-architecture/)

-   **Mauro Servienti。更好的 UI 撰寫的密碼**
    [*https://particular.net/blog/secret-of-better-ui-composition*](https://particular.net/blog/secret-of-better-ui-composition)

-   **Viktor Farcic。前端 Web 元件包含 Microservices**
    [*https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/*](https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/)

-   **管理 Microservices 架構中的前端**\
    [*http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html*](http://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html)


>[!div class="step-by-step"]
[上一個](microservices-可定址性-服務-registry.md) [下一步] (具有恢復功能-高的可用性-microservices.md)
