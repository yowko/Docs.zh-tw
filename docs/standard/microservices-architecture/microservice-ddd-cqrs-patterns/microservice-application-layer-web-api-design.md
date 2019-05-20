---
title: 設計微服務應用程式層及 Web API
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 用於設計應用程式層的 SOLID 準則簡介。
ms.date: 10/08/2018
ms.openlocfilehash: 3c3b9f74e76e01deafa1f97de5d3250d57716014
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639498"
---
# <a name="design-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="b7eb2-103">設計微服務應用程式層及 Web API</span><span class="sxs-lookup"><span data-stu-id="b7eb2-103">Design the microservice application layer and Web API</span></span>

## <a name="use-solid-principles-and-dependency-injection"></a><span data-ttu-id="b7eb2-104">使用 SOLID 準則及相依性插入</span><span class="sxs-lookup"><span data-stu-id="b7eb2-104">Use SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="b7eb2-105">SOLID 準則是用於任何現代及任務關鍵性應用程式的重要技術，例如使用 DDD 模式開發微服務。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-105">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="b7eb2-106">SOLID 是五個基本準則的縮寫：</span><span class="sxs-lookup"><span data-stu-id="b7eb2-106">SOLID is an acronym that groups five fundamental principles:</span></span>

- <span data-ttu-id="b7eb2-107">單一責任準則 (Single Responsibility principle)</span><span class="sxs-lookup"><span data-stu-id="b7eb2-107">Single Responsibility principle</span></span>

- <span data-ttu-id="b7eb2-108">開啟/關閉準則 (Open/closed principle)</span><span class="sxs-lookup"><span data-stu-id="b7eb2-108">Open/closed principle</span></span>

- <span data-ttu-id="b7eb2-109">里斯可夫替代準則 (Liskov substitution principle)</span><span class="sxs-lookup"><span data-stu-id="b7eb2-109">Liskov substitution principle</span></span>

- <span data-ttu-id="b7eb2-110">介面隔離準則 (Interface Segregation principle)</span><span class="sxs-lookup"><span data-stu-id="b7eb2-110">Interface Segregation principle</span></span>

- <span data-ttu-id="b7eb2-111">相依性反轉準則 (Dependency Inversion principle)</span><span class="sxs-lookup"><span data-stu-id="b7eb2-111">Dependency Inversion principle</span></span>

<span data-ttu-id="b7eb2-112">SOLID 與您設計應用程式或微服務的內部層及減少其之間的相依性關係更為密切。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-112">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="b7eb2-113">它與領域無關，而是與應用程式的技術設計有關。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-113">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="b7eb2-114">最後一個準則是「相依性反轉」準則，它可允許您將基礎結構層與剩餘的層分離，使其可更進一步地分離 DDD 層的實作。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-114">The final principle, the Dependency Inversion principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="b7eb2-115">相依性插入 (DI) 是一種實作「相依性反轉」準則的方式。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-115">Dependency Injection (DI) is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="b7eb2-116">它是一種為了達到物件及其相依性間鬆散結合的技術。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-116">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="b7eb2-117">類別要執行其動作所需的物件，會提供 (或「插入」) 給類別，而不是直接具現化共同作業者，或使用靜態參考 (亦即使用 new…)。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-117">Rather than directly instantiating collaborators, or using static references (that is, using new…), the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="b7eb2-118">大多數情況下，類別會透過其建構函式宣告它們的相依性，讓他們能遵循「明確相依性準則」。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-118">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="b7eb2-119">相依性插入通常會基於特定的控制反轉 (IoC) 容器。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-119">Dependency Injection is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="b7eb2-120">ASP.NET Core 提供了簡單的內建 IoC 容器，但您也可以使用您最愛的 IoC 容器，例如 Autofac 或 Ninject。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-120">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="b7eb2-121">藉由遵循 SOLID 準則，您的類別自然而然會傾向小型、構造良好且輕鬆的測試。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-121">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="b7eb2-122">但是如何才能知道您的類別已插入太多相依性？</span><span class="sxs-lookup"><span data-stu-id="b7eb2-122">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="b7eb2-123">若您是透過建構函式使用 DI，您可以藉由查看您建構函式參數的數量來進行偵測。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-123">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="b7eb2-124">若有太多的相依性，這通常表示 ([code smell (程式碼異味)](https://deviq.com/code-smells/)) 您的類別嘗試完成太多事項，並且可能違反了單一責任準則。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-124">If there are too many dependencies, this is generally a sign (a [code smell](https://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="b7eb2-125">通常需要其他指南才能完整涵蓋 SOLID 的詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-125">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="b7eb2-126">因此，本指南僅需要您具備關於這些主題的最低程度知識。</span><span class="sxs-lookup"><span data-stu-id="b7eb2-126">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b7eb2-127">其他資源</span><span class="sxs-lookup"><span data-stu-id="b7eb2-127">Additional resources</span></span>

- <span data-ttu-id="b7eb2-128">**SOLID：基本 OOP 準則** \\</span><span class="sxs-lookup"><span data-stu-id="b7eb2-128">**SOLID: Fundamental OOP Principles** \\</span></span>
  <https://deviq.com/solid/>

- <span data-ttu-id="b7eb2-129">**Inversion of Control Containers and the Dependency Injection pattern (逆轉控制容器和相依性插入模式)** \\</span><span class="sxs-lookup"><span data-stu-id="b7eb2-129">**Inversion of Control Containers and the Dependency Injection pattern** \\</span></span>
  <https://martinfowler.com/articles/injection.html>

- <span data-ttu-id="b7eb2-130">**Steve Smith.New is Glue (接著劑：New)** \\</span><span class="sxs-lookup"><span data-stu-id="b7eb2-130">**Steve Smith. New is Glue** \\</span></span>
  <https://ardalis.com/new-is-glue>

> [!div class="step-by-step"]
> <span data-ttu-id="b7eb2-131">[上一頁](nosql-database-persistence-infrastructure.md)
> [下一頁](microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="b7eb2-131">[Previous](nosql-database-persistence-infrastructure.md)
[Next](microservice-application-layer-implementation-web-api.md)</span></span>
