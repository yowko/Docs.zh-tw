---
title: 雲端原生應用程式簡介
description: 瞭解雲端原生計算
author: robvet
ms.date: 05/13/2020
ms.openlocfilehash: 6ec02a1388d6e0f26cdaa1f728f23a22ba52d735
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 05/19/2020
ms.locfileid: "83613937"
---
# <a name="introduction-to-cloud-native-applications"></a><span data-ttu-id="0c05d-103">雲端原生應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="0c05d-103">Introduction to cloud-native applications</span></span>

<span data-ttu-id="0c05d-104">在辦公室的另一天，處理「下一大事」。</span><span class="sxs-lookup"><span data-stu-id="0c05d-104">Another day, at the office, working on "the next big thing."</span></span>

<span data-ttu-id="0c05d-105">您的行動電話環形。</span><span class="sxs-lookup"><span data-stu-id="0c05d-105">Your cellphone rings.</span></span> <span data-ttu-id="0c05d-106">這是您好用的招聘人員，也就是一天呼叫您一次的新作業。</span><span class="sxs-lookup"><span data-stu-id="0c05d-106">It's your friendly recruiter - the one who calls you twice a day about new jobs.</span></span>

<span data-ttu-id="0c05d-107">但這次並不相同：啟動、股東權益和大量資金。</span><span class="sxs-lookup"><span data-stu-id="0c05d-107">But this time it's different: Start-up, equity, and plenty of funding.</span></span>

<span data-ttu-id="0c05d-108">提到雲端和最尖端的技術會將您帶到邊緣。</span><span class="sxs-lookup"><span data-stu-id="0c05d-108">The mention of the cloud and cutting-edge technology pushes you over the edge.</span></span>

<span data-ttu-id="0c05d-109">向前快轉幾周，您現在在設計會話中的新員工架構了主要的電子商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c05d-109">Fast forward a few weeks and you're now a new employee in a design session architecting a major eCommerce application.</span></span> <span data-ttu-id="0c05d-110">您將與領先的電子商務網站競爭。</span><span class="sxs-lookup"><span data-stu-id="0c05d-110">You're going to compete with the leading eCommerce sites.</span></span>

<span data-ttu-id="0c05d-111">您將如何建立它？</span><span class="sxs-lookup"><span data-stu-id="0c05d-111">How will you build it?</span></span>

<span data-ttu-id="0c05d-112">如果您遵循過去15年的指導方針，您很可能會建立如圖1.1 所示的系統。</span><span class="sxs-lookup"><span data-stu-id="0c05d-112">If you follow the guidance from past 15 years, you'll most likely build the system shown in Figure 1.1.</span></span>

![傳統的整合式設計](./media/monolithic-design.png)

<span data-ttu-id="0c05d-114">**圖 1-1**。</span><span class="sxs-lookup"><span data-stu-id="0c05d-114">**Figure 1-1**.</span></span> <span data-ttu-id="0c05d-115">傳統的整合式設計</span><span class="sxs-lookup"><span data-stu-id="0c05d-115">Traditional monolithic design</span></span>

<span data-ttu-id="0c05d-116">您會建立包含所有網域邏輯的大型核心應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c05d-116">You construct a large core application containing all of your domain logic.</span></span> <span data-ttu-id="0c05d-117">其中包括身分識別、目錄、排序等模組。</span><span class="sxs-lookup"><span data-stu-id="0c05d-117">It includes modules such as Identity, Catalog, Ordering, and more.</span></span> <span data-ttu-id="0c05d-118">核心應用程式會與大型關係資料庫通訊。</span><span class="sxs-lookup"><span data-stu-id="0c05d-118">The core app communicates with a large relational database.</span></span> <span data-ttu-id="0c05d-119">核心會透過 HTML 介面公開功能。</span><span class="sxs-lookup"><span data-stu-id="0c05d-119">The core exposes functionality via an HTML interface.</span></span>

<span data-ttu-id="0c05d-120">恭喜！</span><span class="sxs-lookup"><span data-stu-id="0c05d-120">Congratulations!</span></span>  <span data-ttu-id="0c05d-121">您剛建立了單一應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c05d-121">You just created a monolithic application.</span></span>

<span data-ttu-id="0c05d-122">並非全部都是錯誤的。</span><span class="sxs-lookup"><span data-stu-id="0c05d-122">Not all is bad.</span></span> <span data-ttu-id="0c05d-123">是開化「提供一些獨特的優勢。</span><span class="sxs-lookup"><span data-stu-id="0c05d-123">Monoliths offer some distinct advantages.</span></span> <span data-ttu-id="0c05d-124">例如，它們很容易 .。。</span><span class="sxs-lookup"><span data-stu-id="0c05d-124">For example, they're straightforward to...</span></span>

- <span data-ttu-id="0c05d-125">build</span><span class="sxs-lookup"><span data-stu-id="0c05d-125">build</span></span>
- <span data-ttu-id="0c05d-126">test</span><span class="sxs-lookup"><span data-stu-id="0c05d-126">test</span></span>
- <span data-ttu-id="0c05d-127">部署</span><span class="sxs-lookup"><span data-stu-id="0c05d-127">deploy</span></span>
- <span data-ttu-id="0c05d-128">疑難排解</span><span class="sxs-lookup"><span data-stu-id="0c05d-128">troubleshoot</span></span>
- <span data-ttu-id="0c05d-129">級別</span><span class="sxs-lookup"><span data-stu-id="0c05d-129">scale</span></span>

<span data-ttu-id="0c05d-130">現今存在的許多成功應用程式都是以是開化「的方式建立。</span><span class="sxs-lookup"><span data-stu-id="0c05d-130">Many successful apps that exist today were created as monoliths.</span></span> <span data-ttu-id="0c05d-131">應用程式會被叫用並持續演進，反復專案之後的反復專案，加入更多和更多功能。</span><span class="sxs-lookup"><span data-stu-id="0c05d-131">The app is a hit and continues to evolve, iteration after iteration, adding more and more functionality.</span></span>

<span data-ttu-id="0c05d-132">不過，在某些時候，您會開始覺得不舒服。</span><span class="sxs-lookup"><span data-stu-id="0c05d-132">At some point, however, you begin to feel uncomfortable.</span></span> <span data-ttu-id="0c05d-133">您發現自己失去了應用程式的控制權。</span><span class="sxs-lookup"><span data-stu-id="0c05d-133">You find yourself losing control of the application.</span></span> <span data-ttu-id="0c05d-134">當時間增加時，感覺就會變得更密集，而且您最後會進入所謂的狀態 `Fear Cycle` 。</span><span class="sxs-lookup"><span data-stu-id="0c05d-134">As time goes on, the feeling becomes more intense and you eventually enter a state known as the `Fear Cycle`.</span></span>

- <span data-ttu-id="0c05d-135">應用程式已變得回應非常正面複雜，因此不會有任何人瞭解。</span><span class="sxs-lookup"><span data-stu-id="0c05d-135">The app has become so overwhelmingly complicated that no single person understands it.</span></span>
- <span data-ttu-id="0c05d-136">您想要進行變更，每項變更都有非預期且成本高昂的副作用。</span><span class="sxs-lookup"><span data-stu-id="0c05d-136">You fear making changes - each change has unintended and costly side effects.</span></span>
- <span data-ttu-id="0c05d-137">新功能/修正程式會變得很困難、耗時，而且需要耗費大量的時間。</span><span class="sxs-lookup"><span data-stu-id="0c05d-137">New features/fixes become tricky, time-consuming, and expensive to implement.</span></span>
- <span data-ttu-id="0c05d-138">每個版本越小越好，而且需要完整部署整個應用程式。</span><span class="sxs-lookup"><span data-stu-id="0c05d-138">Each release as small as possible and requires a full deployment of the entire application.</span></span>
- <span data-ttu-id="0c05d-139">一個不穩定的元件可能會損毀整個系統。</span><span class="sxs-lookup"><span data-stu-id="0c05d-139">One unstable component can crash the entire system.</span></span>
- <span data-ttu-id="0c05d-140">新的技術和架構並不是一個選項。</span><span class="sxs-lookup"><span data-stu-id="0c05d-140">New technologies and frameworks aren't an option.</span></span>
- <span data-ttu-id="0c05d-141">這很難以實現 agile 傳遞方法。</span><span class="sxs-lookup"><span data-stu-id="0c05d-141">It's difficult to implement agile delivery methodologies.</span></span>
- <span data-ttu-id="0c05d-142">架構削弱會將中的設定為程式碼基底 deteriorates，並使用永不結束的「特殊案例」。</span><span class="sxs-lookup"><span data-stu-id="0c05d-142">Architectural erosion sets in as the code base deteriorates with never-ending "special cases."</span></span>
- <span data-ttu-id="0c05d-143">顧問會告訴您重寫它。</span><span class="sxs-lookup"><span data-stu-id="0c05d-143">The consultants tell you to rewrite it.</span></span>

<span data-ttu-id="0c05d-144">許多組織都藉由採用雲端原生方法來建立系統，來解決整合的恐懼週期。</span><span class="sxs-lookup"><span data-stu-id="0c05d-144">Many organizations have addressed the monolithic fear cycle by adopting a cloud-native approach to building systems.</span></span> <span data-ttu-id="0c05d-145">圖1-2 顯示的相同系統已建立雲端原生技術和實務。</span><span class="sxs-lookup"><span data-stu-id="0c05d-145">Figure 1-2 shows the same system built applying cloud-native techniques and practices.</span></span>

![雲端原生設計](./media/cloud-native-design.png)

<span data-ttu-id="0c05d-147">**圖 1-2**。</span><span class="sxs-lookup"><span data-stu-id="0c05d-147">**Figure 1-2**.</span></span> <span data-ttu-id="0c05d-148">雲端原生設計</span><span class="sxs-lookup"><span data-stu-id="0c05d-148">Cloud-native design</span></span>

<span data-ttu-id="0c05d-149">請注意應用程式如何分解成一組小型隔離的微服務。</span><span class="sxs-lookup"><span data-stu-id="0c05d-149">Note how the application is decomposed across a set of small isolated microservices.</span></span> <span data-ttu-id="0c05d-150">每個服務都是獨立的，並封裝自己的程式碼、資料和相依性。</span><span class="sxs-lookup"><span data-stu-id="0c05d-150">Each service is self-contained and encapsulates its own code, data, and dependencies.</span></span> <span data-ttu-id="0c05d-151">每個都會部署在軟體容器中，並由容器協調器管理。</span><span class="sxs-lookup"><span data-stu-id="0c05d-151">Each is deployed in a software container and managed by a container orchestrator.</span></span> <span data-ttu-id="0c05d-152">除了大型的關係資料庫，每個服務都擁有它自己的資料存放區，而這種類型會根據資料需求而有所不同。</span><span class="sxs-lookup"><span data-stu-id="0c05d-152">Instead of a large relational database, each service owns it own datastore, the type of which vary based upon the data needs.</span></span> <span data-ttu-id="0c05d-153">請注意某些服務如何依賴關係資料庫，但在 NoSQL 資料庫上則是其他。</span><span class="sxs-lookup"><span data-stu-id="0c05d-153">Note how some services depend on a relational database, but other on NoSQL databases.</span></span> <span data-ttu-id="0c05d-154">其中一個服務會將其狀態儲存在分散式快取中。</span><span class="sxs-lookup"><span data-stu-id="0c05d-154">One service stores its state in a distributed cache.</span></span> <span data-ttu-id="0c05d-155">請注意所有流量如何透過 API 閘道服務進行路由傳送，負責將流量導向核心後端服務，並強制執行許多跨領域關注。</span><span class="sxs-lookup"><span data-stu-id="0c05d-155">Note how all traffic routes through an API Gateway service that is responsible for directing traffic to the core back-end services and enforcing many cross-cutting concerns.</span></span> <span data-ttu-id="0c05d-156">最重要的是，應用程式會充分利用現代化雲端平臺中的擴充性、可用性和復原功能。</span><span class="sxs-lookup"><span data-stu-id="0c05d-156">Most importantly, the application takes full advantage of the scalability, availability, and resiliency features found in modern cloud platforms.</span></span>

### <a name="cloud-native-computing"></a><span data-ttu-id="0c05d-157">雲端原生計算</span><span class="sxs-lookup"><span data-stu-id="0c05d-157">Cloud-native computing</span></span>

<span data-ttu-id="0c05d-158">嗯 .。。我們剛剛使用「_雲端原生_」一詞。</span><span class="sxs-lookup"><span data-stu-id="0c05d-158">Hmm... We just used the term, _Cloud Native_.</span></span> <span data-ttu-id="0c05d-159">您的第一個想法可能是「到底是什麼意思呢？」</span><span class="sxs-lookup"><span data-stu-id="0c05d-159">Your first thought might be, "What exactly does that mean?"</span></span> <span data-ttu-id="0c05d-160">另一家由軟體廠商 concocted 的產業流行語，以更多的東西行銷？」</span><span class="sxs-lookup"><span data-stu-id="0c05d-160">Another industry buzzword concocted by software vendors to market more stuff?"</span></span>

<span data-ttu-id="0c05d-161">幸運的是，這本書的外觀並不盡相同，希望您可以協助您。</span><span class="sxs-lookup"><span data-stu-id="0c05d-161">Fortunately it's far different and hopefully this book will help convince you.</span></span>

<span data-ttu-id="0c05d-162">在短時間內，雲端原生已成為軟體產業的駕駛趨勢。</span><span class="sxs-lookup"><span data-stu-id="0c05d-162">Within a short time, cloud native has become a driving trend in the software industry.</span></span> <span data-ttu-id="0c05d-163">這是一種新的方法，可讓您瞭解如何建立大型、複雜的系統，這是一種充分利用新式軟體發展實務、技術和雲端基礎結構的方法。</span><span class="sxs-lookup"><span data-stu-id="0c05d-163">It's a new way to think about building large, complex systems, an approach that takes full advantage of modern software development practices, technologies, and cloud infrastructure.</span></span> <span data-ttu-id="0c05d-164">這個方法會改變您設計、實施、部署和讓系統的方式。</span><span class="sxs-lookup"><span data-stu-id="0c05d-164">The approach changes the way you design, implement, deploy, and operationalize systems.</span></span>

<span data-ttu-id="0c05d-165">不同于驅動我們產業的連續 hype，雲端原生是_真實的_。</span><span class="sxs-lookup"><span data-stu-id="0c05d-165">Unlike the continuous hype that drives our industry, cloud native is _for-real_.</span></span> <span data-ttu-id="0c05d-166">請考慮使用[雲端原生運算基礎](https://www.cncf.io/)（由 cncf），這是超過300個主要企業的聯盟，可讓雲端原生運算在技術和雲端堆疊上普及。</span><span class="sxs-lookup"><span data-stu-id="0c05d-166">Consider the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), a consortium of over 300 major corporations with a charter to make cloud-native computing ubiquitous across technology and cloud stacks.</span></span> <span data-ttu-id="0c05d-167">作為其中一個最具影響力的開放原始碼群組，它會在 GitHub 中裝載許多最快速成長的開放原始碼專案。</span><span class="sxs-lookup"><span data-stu-id="0c05d-167">As one of the most influential open-source groups, it hosts many of the fastest-growing open source-projects in GitHub.</span></span> <span data-ttu-id="0c05d-168">其中包括[Kubernetes](https://kubernetes.io/)、 [Prometheus](https://prometheus.io/)、 [Helm](https://helm.sh/)、 [Envoy](https://www.envoyproxy.io/)和[gRPC](https://grpc.io/)等專案。</span><span class="sxs-lookup"><span data-stu-id="0c05d-168">They include projects such as [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/), and [gRPC](https://grpc.io/).</span></span>

<span data-ttu-id="0c05d-169">由 CNCF 會促進開放原始碼和廠商中立的生態系統。</span><span class="sxs-lookup"><span data-stu-id="0c05d-169">The CNCF fosters an ecosystem of open-source and vendor-neutrality.</span></span> <span data-ttu-id="0c05d-170">這本書會遵循該線索，呈現與技術無關的雲端原生原則、模式和最佳作法。</span><span class="sxs-lookup"><span data-stu-id="0c05d-170">Following that lead, this book presents cloud-native principles, patterns, and best practices that are technology agnostic.</span></span> <span data-ttu-id="0c05d-171">同時，我們也會討論 Microsoft Azure 雲端中可用來建立雲端原生系統的服務和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="0c05d-171">At the same time, we discuss the services and infrastructure available in the Microsoft Azure cloud for constructing cloud-native systems.</span></span>

<span data-ttu-id="0c05d-172">那麼，雲端原生到底是什麼？</span><span class="sxs-lookup"><span data-stu-id="0c05d-172">So, what exactly is Cloud Native?</span></span> <span data-ttu-id="0c05d-173">請放心，放鬆，讓我們協助您探索這個新世界。</span><span class="sxs-lookup"><span data-stu-id="0c05d-173">Sit back, relax, and let us help you explore this new world.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="0c05d-174">[上一個](index.md) 
>[下一步](definition.md)</span><span class="sxs-lookup"><span data-stu-id="0c05d-174">[Previous](index.md)
[Next](definition.md)</span></span>
