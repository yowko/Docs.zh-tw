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
# <a name="designing-the-microservice-application-layer-and-web-api"></a><span data-ttu-id="50ef0-104">設計微服務應用程式層和 Web API</span><span class="sxs-lookup"><span data-stu-id="50ef0-104">Designing the microservice application layer and Web API</span></span>

## <a name="using-solid-principles-and-dependency-injection"></a><span data-ttu-id="50ef0-105">使用純色的原則和相依性插入</span><span class="sxs-lookup"><span data-stu-id="50ef0-105">Using SOLID principles and Dependency Injection</span></span>

<span data-ttu-id="50ef0-106">純色的原則是重要的技術，以用於任何現代和業務關鍵應用程式，例如開發與 DDD 模式微服務。</span><span class="sxs-lookup"><span data-stu-id="50ef0-106">SOLID principles are critical techniques to be used in any modern and mission-critical application, such as developing a microservice with DDD patterns.</span></span> <span data-ttu-id="50ef0-107">實線是為縮寫字的五個群組的基本原則：</span><span class="sxs-lookup"><span data-stu-id="50ef0-107">SOLID is an acronym that groups five fundamental principles:</span></span>

-   <span data-ttu-id="50ef0-108">單一責任原則</span><span class="sxs-lookup"><span data-stu-id="50ef0-108">Single Responsibility principle</span></span>

-   <span data-ttu-id="50ef0-109">開啟/關閉原則</span><span class="sxs-lookup"><span data-stu-id="50ef0-109">Open/closed principle</span></span>

-   <span data-ttu-id="50ef0-110">Liskov 替代的原則</span><span class="sxs-lookup"><span data-stu-id="50ef0-110">Liskov substitution principle</span></span>

-   <span data-ttu-id="50ef0-111">反轉隔離原則</span><span class="sxs-lookup"><span data-stu-id="50ef0-111">Inversion Segregation principle</span></span>

-   <span data-ttu-id="50ef0-112">相依性反向原則</span><span class="sxs-lookup"><span data-stu-id="50ef0-112">Dependency Inversion principle</span></span>

<span data-ttu-id="50ef0-113">實線是更多有關您如何設計應用程式或微服務內部層級，以及減少之間的相依性。</span><span class="sxs-lookup"><span data-stu-id="50ef0-113">SOLID is more about how you design your application or microservice internal layers and about decoupling dependencies between them.</span></span> <span data-ttu-id="50ef0-114">沒有關聯到網域，但應用程式的技術設計。</span><span class="sxs-lookup"><span data-stu-id="50ef0-114">It is not related to the domain, but to the application’s technical design.</span></span> <span data-ttu-id="50ef0-115">最後一個原則，也就是相依性反向 (DI) 原則，可讓您分離其餘的圖層，可讓 DDD 圖層的好解除解合的實作基礎結構層。</span><span class="sxs-lookup"><span data-stu-id="50ef0-115">The final principle, the Dependency Inversion (DI) principle, allows you to decouple the infrastructure layer from the rest of the layers, which allows a better decoupled implementation of the DDD layers.</span></span>

<span data-ttu-id="50ef0-116">DI 是一種方式實作的相依性反向原則。</span><span class="sxs-lookup"><span data-stu-id="50ef0-116">DI is one way to implement the Dependency Inversion principle.</span></span> <span data-ttu-id="50ef0-117">它是針對達到物件及其相依性之間的鬆散偶合的技術。</span><span class="sxs-lookup"><span data-stu-id="50ef0-117">It is a technique for achieving loose coupling between objects and their dependencies.</span></span> <span data-ttu-id="50ef0-118">而非直接具現化共同作業者，或使用靜態參考，才能執行其動作的類別需要的物件是提供給 （或 「 插入 」） 的類別。</span><span class="sxs-lookup"><span data-stu-id="50ef0-118">Rather than directly instantiating collaborators, or using static references, the objects that a class needs in order to perform its actions are provided to (or "injected into") the class.</span></span> <span data-ttu-id="50ef0-119">大多數情況下，類別會宣告透過其建構函式，讓他們遵循明確的相依性原則及其相依性。</span><span class="sxs-lookup"><span data-stu-id="50ef0-119">Most often, classes will declare their dependencies via their constructor, allowing them to follow the Explicit Dependencies principle.</span></span> <span data-ttu-id="50ef0-120">DI 通常根據特定的逆轉控制 (IoC) 容器。</span><span class="sxs-lookup"><span data-stu-id="50ef0-120">DI is usually based on specific Inversion of Control (IoC) containers.</span></span> <span data-ttu-id="50ef0-121">ASP.NET Core 提供簡單的內建 IoC 容器，但您也可以使用您最愛的 IoC 容器，例如 Autofac 或 Ninject。</span><span class="sxs-lookup"><span data-stu-id="50ef0-121">ASP.NET Core provides a simple built-in IoC container, but you can also use your favorite IoC container, like Autofac or Ninject.</span></span>

<span data-ttu-id="50ef0-122">依照實心原則，類別通常會自然小型、 構造良好且輕鬆地測試過。</span><span class="sxs-lookup"><span data-stu-id="50ef0-122">By following the SOLID principles, your classes will tend naturally to be small, well-factored, and easily tested.</span></span> <span data-ttu-id="50ef0-123">但是，您要如何知道是否太多的相依性會被插入您的類別？</span><span class="sxs-lookup"><span data-stu-id="50ef0-123">But how can you know if too many dependencies are being injected into your classes?</span></span> <span data-ttu-id="50ef0-124">如果您使用 DI 透過建構函式時，就可輕易偵測出只要查看您建構函式的參數數目。</span><span class="sxs-lookup"><span data-stu-id="50ef0-124">If you use DI through the constructor, it will be easy to detect that by just looking at the number of parameters for your constructor.</span></span> <span data-ttu-id="50ef0-125">如果有太多的相依性，這通常是一個符號 ([程式碼氣味](http://deviq.com/code-smells/)) 嘗試太多，您的類別，並可能會違反單一責任原則。</span><span class="sxs-lookup"><span data-stu-id="50ef0-125">If there are too many dependencies, this is generally a sign (a [code smell](http://deviq.com/code-smells/)) that your class is trying to do too much, and is probably violating the Single Responsibility principle.</span></span>

<span data-ttu-id="50ef0-126">需要其他的指南，以涵蓋詳細的實線。</span><span class="sxs-lookup"><span data-stu-id="50ef0-126">It would take another guide to cover SOLID in detail.</span></span> <span data-ttu-id="50ef0-127">因此，本指南必須要有這些主題的最小知識。</span><span class="sxs-lookup"><span data-stu-id="50ef0-127">Therefore, this guide requires you to have only a minimum knowledge of these topics.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="50ef0-128">其他資源</span><span class="sxs-lookup"><span data-stu-id="50ef0-128">Additional resources</span></span>

-   <span data-ttu-id="50ef0-129">**實線： 基本 OOP 原則**
    [*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span><span class="sxs-lookup"><span data-stu-id="50ef0-129">**SOLID: Fundamental OOP Principles**
[*http://deviq.com/solid/*](http://deviq.com/solid/%20)</span></span>

-   <span data-ttu-id="50ef0-130">**逆轉控制容器和相依性插入模式**
    [*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span><span class="sxs-lookup"><span data-stu-id="50ef0-130">**Inversion of Control Containers and the Dependency Injection pattern**
[*https://martinfowler.com/articles/injection.html*](https://martinfowler.com/articles/injection.html)</span></span>

-   <span data-ttu-id="50ef0-131">**Steve Smith。新是黏附**
    [*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span><span class="sxs-lookup"><span data-stu-id="50ef0-131">**Steve Smith. New is Glue**
[*http://ardalis.com/new-is-glue*](http://ardalis.com/new-is-glue)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="50ef0-132">[上一個](nosql-資料庫-持續性-infrastructure.md) [下一步] (microservice-application-layer-implementation-web-api.md)</span><span class="sxs-lookup"><span data-stu-id="50ef0-132">[Previous] (nosql-database-persistence-infrastructure.md) [Next] (microservice-application-layer-implementation-web-api.md)</span></span>
