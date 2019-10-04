---
title: 建立以微服務為基礎的複合 UI
description: 微服務架構不只可用於後端。 預覽以了解如何用於前端。
ms.date: 09/20/2018
ms.openlocfilehash: 60e0e6d59738f3f1fec31226cb842ceb1af303e4
ms.sourcegitcommit: 8a0fe8a2227af612f8b8941bdb8b19d6268748e7
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 10/03/2019
ms.locfileid: "71834381"
---
# <a name="creating-composite-ui-based-on-microservices"></a><span data-ttu-id="f92d8-104">建立以微服務為基礎的複合 UI</span><span class="sxs-lookup"><span data-stu-id="f92d8-104">Creating composite UI based on microservices</span></span>

<span data-ttu-id="f92d8-105">微服務架構一開始通常是處理資料和邏輯的伺服器端。</span><span class="sxs-lookup"><span data-stu-id="f92d8-105">Microservices architecture often starts with the server-side handling data and logic.</span></span> <span data-ttu-id="f92d8-106">不過，更進階的方法是同時根據微服務來設計應用程式 UI。</span><span class="sxs-lookup"><span data-stu-id="f92d8-106">However, a more advanced approach is to design your application UI based on microservices as well.</span></span> <span data-ttu-id="f92d8-107">這表示具有微服務所產生的複合 UI，而不是在伺服器上擁有多個微服務，並只由一個整合型用戶端應用程式來取用這些微服務。</span><span class="sxs-lookup"><span data-stu-id="f92d8-107">That means having a composite UI produced by the microservices, instead of having microservices on the server and just a monolithic client app consuming the microservices.</span></span> <span data-ttu-id="f92d8-108">透過此方法，您建置的微服務就會同時具備邏輯和視覺表示。</span><span class="sxs-lookup"><span data-stu-id="f92d8-108">With this approach, the microservices you build can be complete with both logic and visual representation.</span></span>

<span data-ttu-id="f92d8-109">圖 4-20 顯示更簡單的方法，該方法只會從整合型用戶端應用程式取用微服務。</span><span class="sxs-lookup"><span data-stu-id="f92d8-109">Figure 4-20 shows the simpler approach of just consuming microservices from a monolithic client application.</span></span> <span data-ttu-id="f92d8-110">當然，您在產生 HTML 與 JavaScript 之間可能會有 ASP.NET MVC 服務。</span><span class="sxs-lookup"><span data-stu-id="f92d8-110">Of course, you could have an ASP.NET MVC service in between producing the HTML and JavaScript.</span></span> <span data-ttu-id="f92d8-111">下圖已經過簡化，顯示您有取用微服務的單一 (整合型) 用戶端 UI，只著重於邏輯和資料，而不是 UI 形狀 (HTML 和 JavaScript)。</span><span class="sxs-lookup"><span data-stu-id="f92d8-111">The figure is a simplification that highlights that you have a single (monolithic) client UI consuming the microservices, which just focus on logic and data and not on the UI shape (HTML and JavaScript).</span></span>

![連接到微服務的整合型 UI 應用程式圖表。](./media/microservice-based-composite-ui-shape-layout/monolith-ui-consume-microservices.png)

<span data-ttu-id="f92d8-113">**圖 4-20**：</span><span class="sxs-lookup"><span data-stu-id="f92d8-113">**Figure 4-20**.</span></span> <span data-ttu-id="f92d8-114">取用後端微服務的整合型 UI 應用程式</span><span class="sxs-lookup"><span data-stu-id="f92d8-114">A monolithic UI application consuming back-end microservices</span></span>

<span data-ttu-id="f92d8-115">相較之下，複合 UI 是由微服務本身精確地產生和撰寫而成。</span><span class="sxs-lookup"><span data-stu-id="f92d8-115">In contrast, a composite UI is precisely generated and composed by the microservices themselves.</span></span> <span data-ttu-id="f92d8-116">部分微服務會支援特定 UI 區域的視覺形狀。</span><span class="sxs-lookup"><span data-stu-id="f92d8-116">Some of the microservices drive the visual shape of specific areas of the UI.</span></span> <span data-ttu-id="f92d8-117">主要差異在於您有以範本為基礎的用戶端 UI 元件 (例如 TypeScript 類別)，而且這些範本的資料成形 UI ViewModel 來自每個微服務。</span><span class="sxs-lookup"><span data-stu-id="f92d8-117">The key difference is that you have client UI components (TypeScript classes, for example) based on templates, and the data-shaping-UI ViewModel for those templates comes from each microservice.</span></span>

<span data-ttu-id="f92d8-118">用戶端應用程式啟動時，每個用戶端 UI 元件 (例如 TypeScript 類別) 會向基礎結構微服務註冊其本身，以便能夠針對指定案例提供 ViewModel。</span><span class="sxs-lookup"><span data-stu-id="f92d8-118">At client application start-up time, each of the client UI components (TypeScript classes, for example) registers itself with an infrastructure microservice capable of providing ViewModels for a given scenario.</span></span> <span data-ttu-id="f92d8-119">如果微服務變更形狀，UI 也會變更。</span><span class="sxs-lookup"><span data-stu-id="f92d8-119">If the microservice changes the shape, the UI changes also.</span></span>

<span data-ttu-id="f92d8-120">圖 4-21 顯示此複合 UI 方法的版本。</span><span class="sxs-lookup"><span data-stu-id="f92d8-120">Figure 4-21 shows a version of this composite UI approach.</span></span> <span data-ttu-id="f92d8-121">這已經過簡化，因為您可能會有根據不同技術彙總更細緻部分的其他微服務。</span><span class="sxs-lookup"><span data-stu-id="f92d8-121">This is simplified because you might have other microservices that are aggregating granular parts that are based on different techniques.</span></span> <span data-ttu-id="f92d8-122">這取決於您建置的是傳統 Web 方法 (ASP.NET MVC) 或 SPA (單頁應用程式)。</span><span class="sxs-lookup"><span data-stu-id="f92d8-122">It depends on whether you're building a traditional web approach (ASP.NET MVC) or an SPA (Single Page Application).</span></span>

![由許多視圖模型組成的複合 UI 圖表。](./media/microservice-based-composite-ui-shape-layout/microservice-generate-composite-ui.png)

<span data-ttu-id="f92d8-124">**圖 4-21**：</span><span class="sxs-lookup"><span data-stu-id="f92d8-124">**Figure 4-21**.</span></span> <span data-ttu-id="f92d8-125">由後端微服務成形的複合 UI 應用程式範例</span><span class="sxs-lookup"><span data-stu-id="f92d8-125">Example of a composite UI application shaped by back-end microservices</span></span>

<span data-ttu-id="f92d8-126">每個 UI 組合微服務會類似於小型 API 閘道。</span><span class="sxs-lookup"><span data-stu-id="f92d8-126">Each of those UI composition microservices would be similar to a small API Gateway.</span></span> <span data-ttu-id="f92d8-127">但在此情況下，每個都是由一個小型 UI 區域負責。</span><span class="sxs-lookup"><span data-stu-id="f92d8-127">But in this case, each one is responsible for a small UI area.</span></span>

<span data-ttu-id="f92d8-128">根據您所使用的 UI 技術，微服務導向的複合 UI 方法可能挑戰性很高，也可能很低。</span><span class="sxs-lookup"><span data-stu-id="f92d8-128">A composite UI approach that's driven by microservices can be more challenging or less so, depending on what UI technologies you're using.</span></span> <span data-ttu-id="f92d8-129">例如，您不會使用與用來建置 SPA 或原生行動應用程式相同的技術來建置傳統 Web 應用程式 (例如開發 Xamarin 應用程式時，此方法的挑戰性可能更高)。</span><span class="sxs-lookup"><span data-stu-id="f92d8-129">For instance, you won't use the same techniques for building a traditional web application that you use for building an SPA or for native mobile app (as when developing Xamarin apps, which can be more challenging for this approach).</span></span>

<span data-ttu-id="f92d8-130">[eShopOnContainers](https://aka.ms/MicroservicesArchitecture) 範例應用程式使用整合型 UI 方法的原因有很多。</span><span class="sxs-lookup"><span data-stu-id="f92d8-130">The [eShopOnContainers](https://aka.ms/MicroservicesArchitecture) sample application uses the monolithic UI approach for multiple reasons.</span></span> <span data-ttu-id="f92d8-131">首先，它是微服務和容器的前導。</span><span class="sxs-lookup"><span data-stu-id="f92d8-131">First, it's an introduction to microservices and containers.</span></span> <span data-ttu-id="f92d8-132">複合 UI 更進階，但在設計及開發 UI 時也需要更高的複雜度。</span><span class="sxs-lookup"><span data-stu-id="f92d8-132">A composite UI is more advanced but also requires further complexity when designing and developing the UI.</span></span> <span data-ttu-id="f92d8-133">其次，eShopOnContainers 也提供以 Xamarin 為基礎的原生行動應用程式，因此在用戶端 \# 側會更複雜。</span><span class="sxs-lookup"><span data-stu-id="f92d8-133">Second, eShopOnContainers also provides a native mobile app based on Xamarin, which would make it more complex on the client C\# side.</span></span>

<span data-ttu-id="f92d8-134">不過，建議您使用下列參考，深入了解以微服務為基礎的複合 UI。</span><span class="sxs-lookup"><span data-stu-id="f92d8-134">However, we encourage you to use the following references to learn more about composite UI based on microservices.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f92d8-135">其他資源</span><span class="sxs-lookup"><span data-stu-id="f92d8-135">Additional resources</span></span>

- <span data-ttu-id="f92d8-136">**使用 ASP.NET 的複合 UI (特定研討)**  </span><span class="sxs-lookup"><span data-stu-id="f92d8-136">**Composite UI using ASP.NET (Particular's Workshop)** </span></span>\
  <https://github.com/Particular/Workshop/tree/master/demos/asp-net-core>

- <span data-ttu-id="f92d8-137">**Ruben Oostinga：The Monolithic Frontend in the Microservices Architecture (微服務架構中的整合型前端)**  </span><span class="sxs-lookup"><span data-stu-id="f92d8-137">**Ruben Oostinga. The Monolithic Frontend in the Microservices Architecture** </span></span>\
  <https://xebia.com/blog/the-monolithic-frontend-in-the-microservices-architecture/>

- <span data-ttu-id="f92d8-138">**Mauro Servienti：The secret of better UI composition (更佳 UI 組合的祕密)**  </span><span class="sxs-lookup"><span data-stu-id="f92d8-138">**Mauro Servienti. The secret of better UI composition** </span></span>\
  <https://particular.net/blog/secret-of-better-ui-composition>

- <span data-ttu-id="f92d8-139">**Viktor Farcic：Including Front-End Web Components Into Microservices (將前端 Web 元件併入微服務)**  </span><span class="sxs-lookup"><span data-stu-id="f92d8-139">**Viktor Farcic. Including Front-End Web Components Into Microservices** </span></span>\
  <https://technologyconversations.com/2015/08/09/including-front-end-web-components-into-microservices/>

- <span data-ttu-id="f92d8-140">**Managing Frontend in the Microservices Architecture (管理微服務架構中的前端)**  </span><span class="sxs-lookup"><span data-stu-id="f92d8-140">**Managing Frontend in the Microservices Architecture** </span></span>\
  <https://allegro.tech/2016/03/Managing-Frontend-in-the-microservices-architecture.html>

>[!div class="step-by-step"]
><span data-ttu-id="f92d8-141">[上一頁](microservices-addressability-service-registry.md)
>[下一頁](resilient-high-availability-microservices.md)</span><span class="sxs-lookup"><span data-stu-id="f92d8-141">[Previous](microservices-addressability-service-registry.md)
[Next](resilient-high-availability-microservices.md)</span></span>
