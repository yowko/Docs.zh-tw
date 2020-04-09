---
title: 雲端原生應用程式簡介
description: 瞭解雲原生計算
author: robvet
ms.date: 08/26/2019
ms.openlocfilehash: c9ffd34ec3deb04abddbbf85a9e5a6ed2b57c8f9
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/09/2020
ms.locfileid: "80989047"
---
# <a name="introduction-to-cloud-native-applications"></a><span data-ttu-id="716b5-103">雲端原生應用程式簡介</span><span class="sxs-lookup"><span data-stu-id="716b5-103">Introduction to cloud-native applications</span></span>

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

<span data-ttu-id="716b5-104">又一天,在辦公室,工作"下一件大事"。</span><span class="sxs-lookup"><span data-stu-id="716b5-104">Another day, at the office, working on "the next big thing."</span></span>

<span data-ttu-id="716b5-105">你的手機響了</span><span class="sxs-lookup"><span data-stu-id="716b5-105">Your cellphone rings.</span></span> <span data-ttu-id="716b5-106">這是你友好的招聘人員,他每天給你兩次打電話詢問新工作。</span><span class="sxs-lookup"><span data-stu-id="716b5-106">It's your friendly recruiter - the one who calls you twice a day about new jobs.</span></span>

<span data-ttu-id="716b5-107">但這次不同了:創業、股票和大量的資金。</span><span class="sxs-lookup"><span data-stu-id="716b5-107">But this time it's different: Start-up, equity, and plenty of funding.</span></span>

<span data-ttu-id="716b5-108">雲和尖端技術的提及將您推到了邊緣。</span><span class="sxs-lookup"><span data-stu-id="716b5-108">The mention of the cloud and cutting-edge technology pushes you over the edge.</span></span>

<span data-ttu-id="716b5-109">快進幾個星期,你現在是設計會話的新員工,設計一個主要的電子商務應用程式。</span><span class="sxs-lookup"><span data-stu-id="716b5-109">Fast forward a few weeks and you're now a new employee in a design session architecting a major eCommerce application.</span></span> <span data-ttu-id="716b5-110">您將完成其他主要電子商務網站。</span><span class="sxs-lookup"><span data-stu-id="716b5-110">You're going to complete with other leading eCommerce sites.</span></span>

<span data-ttu-id="716b5-111">您將如何構建它?</span><span class="sxs-lookup"><span data-stu-id="716b5-111">How will you build it?</span></span>

<span data-ttu-id="716b5-112">如果您遵循過去 15 年的指導,則最有可能構建圖 1.1 所示的系統。</span><span class="sxs-lookup"><span data-stu-id="716b5-112">If you follow the guidance from past 15 years, you'll most likely build the system shown in Figure 1.1.</span></span>

![傳統單體設計](./media/monolithic-design.png)

<span data-ttu-id="716b5-114">**圖 1-1**.</span><span class="sxs-lookup"><span data-stu-id="716b5-114">**Figure 1-1**.</span></span> <span data-ttu-id="716b5-115">傳統單體設計</span><span class="sxs-lookup"><span data-stu-id="716b5-115">Traditional monolithic design</span></span>

<span data-ttu-id="716b5-116">建構包含所有域邏輯的大型核心應用程式。</span><span class="sxs-lookup"><span data-stu-id="716b5-116">You construct a large core application containing all of your domain logic.</span></span> <span data-ttu-id="716b5-117">它包括標識、目錄、訂購等模組。</span><span class="sxs-lookup"><span data-stu-id="716b5-117">It includes modules such as Identity, Catalog, Ordering, and more.</span></span> <span data-ttu-id="716b5-118">核心應用程式與大型關係資料庫通信。</span><span class="sxs-lookup"><span data-stu-id="716b5-118">The core app communicates with a large relational database.</span></span> <span data-ttu-id="716b5-119">內核通過 HTML 介面公開功能。</span><span class="sxs-lookup"><span data-stu-id="716b5-119">The core exposes functionality via an HTML interface.</span></span>

<span data-ttu-id="716b5-120">恭喜！</span><span class="sxs-lookup"><span data-stu-id="716b5-120">Congratulations!</span></span>  <span data-ttu-id="716b5-121">您剛剛創建了一個整體應用程式。</span><span class="sxs-lookup"><span data-stu-id="716b5-121">You just created a monolithic application.</span></span>

<span data-ttu-id="716b5-122">不是所有都是壞的。</span><span class="sxs-lookup"><span data-stu-id="716b5-122">Not all is bad.</span></span> <span data-ttu-id="716b5-123">單體具有一些明顯的優勢。</span><span class="sxs-lookup"><span data-stu-id="716b5-123">Monoliths offer some distinct advantages.</span></span> <span data-ttu-id="716b5-124">例如,它們直截了當地...</span><span class="sxs-lookup"><span data-stu-id="716b5-124">For example, they're straightforward to...</span></span>

- <span data-ttu-id="716b5-125">build</span><span class="sxs-lookup"><span data-stu-id="716b5-125">build</span></span>
- <span data-ttu-id="716b5-126">test</span><span class="sxs-lookup"><span data-stu-id="716b5-126">test</span></span>
- <span data-ttu-id="716b5-127">部署</span><span class="sxs-lookup"><span data-stu-id="716b5-127">deploy</span></span>
- <span data-ttu-id="716b5-128">解決</span><span class="sxs-lookup"><span data-stu-id="716b5-128">troubleshoot</span></span>
- <span data-ttu-id="716b5-129">級別</span><span class="sxs-lookup"><span data-stu-id="716b5-129">scale</span></span>

<span data-ttu-id="716b5-130">今天存在的許多成功應用都是作為單體創建的。</span><span class="sxs-lookup"><span data-stu-id="716b5-130">Many successful apps that exist today were created as monoliths.</span></span> <span data-ttu-id="716b5-131">該應用程式是一個熱門,並繼續發展,反覆運算後反覆運算,添加更多的功能。</span><span class="sxs-lookup"><span data-stu-id="716b5-131">The app is a hit and continues to evolve, iteration after iteration, adding more and more functionality.</span></span>

<span data-ttu-id="716b5-132">然而,在某些時候,你開始感到不舒服。</span><span class="sxs-lookup"><span data-stu-id="716b5-132">At some point, however, you begin to feel uncomfortable.</span></span> <span data-ttu-id="716b5-133">您發現自己失去了對應用程式的控制。</span><span class="sxs-lookup"><span data-stu-id="716b5-133">You find yourself losing control of the application.</span></span> <span data-ttu-id="716b5-134">隨著時間的流逝,感覺變得更加強烈,你最終進入一種稱為**恐懼循環**的狀態。</span><span class="sxs-lookup"><span data-stu-id="716b5-134">As time goes on, the feeling becomes more intense and you eventually enter a state known as the **Fear Cycle**.</span></span>

- <span data-ttu-id="716b5-135">該應用程式已經變得極其複雜,沒有人理解它。</span><span class="sxs-lookup"><span data-stu-id="716b5-135">The app has become so overwhelmingly complicated that no single person understands it.</span></span>
- <span data-ttu-id="716b5-136">你害怕做出改變 - 每個改變都有意外和代價高昂的副作用。</span><span class="sxs-lookup"><span data-stu-id="716b5-136">You fear making changes - each change has unintended and costly side effects.</span></span>
- <span data-ttu-id="716b5-137">新功能/修復功能變得棘手、耗時且成本高昂。</span><span class="sxs-lookup"><span data-stu-id="716b5-137">New features/fixes become tricky, time-consuming, and expensive to implement.</span></span>
- <span data-ttu-id="716b5-138">每個版本都盡可能小,但可能需要對整個應用程式進行全面部署。</span><span class="sxs-lookup"><span data-stu-id="716b5-138">Each release as small as it may be requires a full deployment of the entire application.</span></span>
- <span data-ttu-id="716b5-139">一個不穩定的元件可能會使整個系統崩潰。</span><span class="sxs-lookup"><span data-stu-id="716b5-139">One unstable component can crash the entire system.</span></span>
- <span data-ttu-id="716b5-140">新技術和框架不是一種選擇。</span><span class="sxs-lookup"><span data-stu-id="716b5-140">New technologies and frameworks aren't an option.</span></span>
- <span data-ttu-id="716b5-141">實現敏捷交付方法是很困難的。</span><span class="sxs-lookup"><span data-stu-id="716b5-141">It's difficult to implement agile delivery methodologies.</span></span>
- <span data-ttu-id="716b5-142">隨著代碼庫的惡化,隨著無休止的"特殊情況",體系結構侵蝕會加劇。</span><span class="sxs-lookup"><span data-stu-id="716b5-142">Architectural erosion sets in as the code base deteriorates with never-ending "special cases."</span></span>
- <span data-ttu-id="716b5-143">顧問們叫你重寫它。</span><span class="sxs-lookup"><span data-stu-id="716b5-143">The consultants tell you to rewrite it.</span></span>

<span data-ttu-id="716b5-144">許多組織通過採用雲原生方法來構建系統來解決整體恐懼迴圈。</span><span class="sxs-lookup"><span data-stu-id="716b5-144">Many organizations have addressed the monolithic fear cycle by adopting a cloud-native approach to building systems.</span></span> <span data-ttu-id="716b5-145">圖 1-2 顯示了應用雲本機技術和實踐構建的相同系統。</span><span class="sxs-lookup"><span data-stu-id="716b5-145">Figure 1-2 shows the same system built applying cloud-native techniques and practices.</span></span>

![雲原生設計](./media/cloud-native-design.png)

<span data-ttu-id="716b5-147">**圖1-2**.</span><span class="sxs-lookup"><span data-stu-id="716b5-147">**Figure 1-2**.</span></span> <span data-ttu-id="716b5-148">雲原生設計</span><span class="sxs-lookup"><span data-stu-id="716b5-148">Cloud-native design</span></span>

<span data-ttu-id="716b5-149">請注意如何在一組小型孤立的微服務中分解應用程式。</span><span class="sxs-lookup"><span data-stu-id="716b5-149">Note how the application is decomposed across a set of small isolated microservices.</span></span> <span data-ttu-id="716b5-150">每個服務都是自包含的,並封裝自己的代碼、數據和依賴項。</span><span class="sxs-lookup"><span data-stu-id="716b5-150">Each service is self-contained and encapsulates its own code, data, and dependencies.</span></span> <span data-ttu-id="716b5-151">每個元件都部署在軟體容器中,並由容器協調器管理。</span><span class="sxs-lookup"><span data-stu-id="716b5-151">Each is deployed in a software container and managed by a container orchestrator.</span></span> <span data-ttu-id="716b5-152">每個服務都擁有自己的數據存儲,而不是大型關係資料庫,其類型因數據需求而異。</span><span class="sxs-lookup"><span data-stu-id="716b5-152">Instead of a large relational database, each service owns it own datastore, the type of which vary based upon the data needs.</span></span> <span data-ttu-id="716b5-153">請注意某些服務如何依賴於關係資料庫,但在 NoSQL 資料庫上依賴於其他服務。</span><span class="sxs-lookup"><span data-stu-id="716b5-153">Note how some services depend on a relational database, but other on NoSQL databases.</span></span> <span data-ttu-id="716b5-154">一個服務將其狀態存儲在分散式緩存中。</span><span class="sxs-lookup"><span data-stu-id="716b5-154">One service stores its state in a distributed cache.</span></span> <span data-ttu-id="716b5-155">請注意,所有流量如何通過 API 閘道服務路由,該服務負責將流量路由到核心後端服務並強制實施許多交叉問題。</span><span class="sxs-lookup"><span data-stu-id="716b5-155">Note how all traffic routes through an API Gateway service that is responsible for routing traffic to the core back-end services  and enforcing many cross-cutting concerns.</span></span> <span data-ttu-id="716b5-156">最重要的是,該應用程式充分利用了現代雲平臺中的可擴展性和彈性功能。</span><span class="sxs-lookup"><span data-stu-id="716b5-156">Most importantly, the application takes full advantage of the scalability and resiliency features found in modern cloud platforms.</span></span>

### <a name="cloud-native-computing"></a><span data-ttu-id="716b5-157">雲原生計算</span><span class="sxs-lookup"><span data-stu-id="716b5-157">Cloud-native computing</span></span>

<span data-ttu-id="716b5-158">嗯。。。我們只是使用了「*雲原生*」這個詞。</span><span class="sxs-lookup"><span data-stu-id="716b5-158">Hmm... We just used the term, "*Cloud Native*."</span></span> <span data-ttu-id="716b5-159">你首先想到的可能是,「這到底是什麼意思?</span><span class="sxs-lookup"><span data-stu-id="716b5-159">You first thought might be, "What exactly does that mean?"</span></span> <span data-ttu-id="716b5-160">另一個行業流行語由軟體供應商捏造,以銷售更多的東西?</span><span class="sxs-lookup"><span data-stu-id="716b5-160">Another industry buzzword concocted by software vendors to market more stuff?"</span></span>

<span data-ttu-id="716b5-161">幸運的是,這是完全不同的,希望這本書將有助於說服你。</span><span class="sxs-lookup"><span data-stu-id="716b5-161">Fortunately it's far different and hopefully this book will help convince you.</span></span>

<span data-ttu-id="716b5-162">在短時間內,雲原生已成為軟體行業的驅動力。</span><span class="sxs-lookup"><span data-stu-id="716b5-162">Within a short time, cloud native has become a driving trend in the software industry.</span></span> <span data-ttu-id="716b5-163">這是一種構建大型複雜系統的新方法,該方法充分利用了現代軟體開發實踐、技術和雲基礎架構。</span><span class="sxs-lookup"><span data-stu-id="716b5-163">It's a new way to think about building large, complex systems, an approach that takes full advantage of modern software development practices, technologies, and cloud infrastructure.</span></span> <span data-ttu-id="716b5-164">該方法改變了您設計、實施、部署和操作系統的方式。</span><span class="sxs-lookup"><span data-stu-id="716b5-164">The approach changes the way you design, implement, deploy, and operationalize systems.</span></span>

<span data-ttu-id="716b5-165">與推動我們行業的持續炒作不同,雲原生是"*真實*"。"。</span><span class="sxs-lookup"><span data-stu-id="716b5-165">Unlike the continuous hype that drives our industry, cloud native is "*for-real*".</span></span> <span data-ttu-id="716b5-166">以[雲原生計算基金會](https://www.cncf.io/)(CNCF) 為例,該基金會由 300 多家大公司組成,其章程使雲原生計算在技術和雲堆疊中無處不在。</span><span class="sxs-lookup"><span data-stu-id="716b5-166">Consider the [Cloud Native Computing Foundation](https://www.cncf.io/) (CNCF), a consortium of over 300 major corporations with a charter to make cloud-native computing ubiquitous across technology and cloud stacks.</span></span> <span data-ttu-id="716b5-167">作為最具影響力的開源集團之一,它承載著 GitHub 中許多增長最快的開源專案。</span><span class="sxs-lookup"><span data-stu-id="716b5-167">As one of the most influential open-source groups, it hosts many of the fastest-growing open source-projects in GitHub.</span></span> <span data-ttu-id="716b5-168">這些專案包括[庫伯內斯](https://kubernetes.io/)、[普羅米特斯](https://prometheus.io/)、[赫爾姆](https://helm.sh/)、[特使](https://www.envoyproxy.io/)和[gRPC](https://grpc.io/)等。</span><span class="sxs-lookup"><span data-stu-id="716b5-168">They include projects such as [Kubernetes](https://kubernetes.io/), [Prometheus](https://prometheus.io/), [Helm](https://helm.sh/), [Envoy](https://www.envoyproxy.io/), and [gRPC](https://grpc.io/).</span></span>

<span data-ttu-id="716b5-169">CNCF 培育了開源和供應商中立的生態系統。</span><span class="sxs-lookup"><span data-stu-id="716b5-169">The CNCF fosters an ecosystem of open-source and vendor-neutrality.</span></span> <span data-ttu-id="716b5-170">遵循該領導,我們提出了與技術無關的雲原生原則、模式和最佳實踐。</span><span class="sxs-lookup"><span data-stu-id="716b5-170">Following that lead, we present cloud-native principles, patterns, and best practices that are technology agnostic.</span></span> <span data-ttu-id="716b5-171">同時,我們討論 Microsoft Azure 雲端中用於建構雲端本機系統的服務和基礎結構。</span><span class="sxs-lookup"><span data-stu-id="716b5-171">At the same time, we discuss the services and infrastructure available in the Microsoft Azure cloud for constructing cloud-native systems.</span></span>

<span data-ttu-id="716b5-172">那麼,什麼是雲原生?</span><span class="sxs-lookup"><span data-stu-id="716b5-172">So, what exactly is Cloud Native?</span></span> <span data-ttu-id="716b5-173">坐下來,放鬆,讓我們説明您探索這個新世界。</span><span class="sxs-lookup"><span data-stu-id="716b5-173">Sit back, relax, and let us help you explore this new world.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="716b5-174">[前一個](index.md)
>[下一個](definition.md)</span><span class="sxs-lookup"><span data-stu-id="716b5-174">[Previous](index.md)
[Next](definition.md)</span></span>
