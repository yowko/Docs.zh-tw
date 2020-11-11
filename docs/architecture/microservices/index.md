---
title: .NET 微服務。 容器化 .NET 應用程式的架構
description: 容器化 .NET 應用程式的 .NET 微服務架構 | 微服務是模組化的獨立可部署服務。 適用於 Linux 與 Windows 的 Docker 容器，可統合服務及其相依性到單一個單位，簡化部署及測試，然後即可於隔離的環境中執行。
ms.date: 11/10/2020
ms.openlocfilehash: 2055dacd46f90ba3714edb1437bcacad4c175e65
ms.sourcegitcommit: bc9c63541c3dc756d48a7ce9d22b5583a18cf7fd
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/11/2020
ms.locfileid: "94507263"
---
# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="cc1a7-105">.NET 微服務：容器化 .NET 應用程式的架構</span><span class="sxs-lookup"><span data-stu-id="cc1a7-105">.NET Microservices: Architecture for Containerized .NET Applications</span></span>

![書籍封面](./media/cover-small.png)

<span data-ttu-id="cc1a7-107">**版本 3.1** -更新為 ASP.NET Core 3。1</span><span class="sxs-lookup"><span data-stu-id="cc1a7-107">**EDITION v3.1** - Updated to ASP.NET Core 3.1</span></span>

<span data-ttu-id="cc1a7-108">請參閱 [變更記錄](https://aka.ms/MicroservicesEbookChangelog) ，以取得書籍更新和社區貢獻。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-108">Refer [changelog](https://aka.ms/MicroservicesEbookChangelog) for the book updates and community contributions.</span></span>

<span data-ttu-id="cc1a7-109">本指南介紹如何開發微服務應用程式及使用容器進行管理，</span><span class="sxs-lookup"><span data-stu-id="cc1a7-109">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="cc1a7-110">並討論使用 .NET Core 和 Docker 容器的架構設計和實作方法。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-110">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span>

<span data-ttu-id="cc1a7-111">為了讓您更輕鬆地開始使用，本指南將重點放在您可以探索的容器化和微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-111">To make it easier to get started, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="cc1a7-112">此參考應用程式位於 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-112">The reference application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

## <a name="action-links"></a><span data-ttu-id="cc1a7-113">動作連結</span><span class="sxs-lookup"><span data-stu-id="cc1a7-113">Action links</span></span>

- <span data-ttu-id="cc1a7-114">這本電子書也提供 PDF 格式 (英文版僅) [下載](https://aka.ms/microservicesebook)</span><span class="sxs-lookup"><span data-stu-id="cc1a7-114">This e-book is also available in a PDF format (English version only) [Download](https://aka.ms/microservicesebook)</span></span>

- <span data-ttu-id="cc1a7-115">複製/派生 [GitHub 上的 eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) 參考應用程式</span><span class="sxs-lookup"><span data-stu-id="cc1a7-115">Clone/Fork the reference application [eShopOnContainers on GitHub](https://github.com/dotnet-architecture/eShopOnContainers)</span></span>

- <span data-ttu-id="cc1a7-116">觀賞 [Channel 9 上的介紹影片](https://aka.ms/microservices-video)</span><span class="sxs-lookup"><span data-stu-id="cc1a7-116">Watch the [introductory video on Channel 9](https://aka.ms/microservices-video)</span></span>

- <span data-ttu-id="cc1a7-117">立即了解[微服務架構](https://aka.ms/MicroservicesArchitecture)</span><span class="sxs-lookup"><span data-stu-id="cc1a7-117">Get to know the [Microservices Architecture](https://aka.ms/MicroservicesArchitecture) right away</span></span>

## <a name="introduction"></a><span data-ttu-id="cc1a7-118">簡介</span><span class="sxs-lookup"><span data-stu-id="cc1a7-118">Introduction</span></span>

<span data-ttu-id="cc1a7-119">企業透過容器，逐漸實現成本節約、解決部署問題，以及改善 DevOps 和生產環境作業。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-119">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="cc1a7-120">Microsoft 藉由建立 Azure Kubernetes Service 和 Azure Service Fabric 等產品，以及藉由與 Docker、Mesosphere 和 Kubernetes 等業界領導者合作，不斷為 Windows 和 Linux 創新容器。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-120">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Kubernetes Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="cc1a7-121">這些產品提供容器解決方案，可協助公司以雲端速度和規模建置及部署應用程式，而不論其選擇的平台或工具為何。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-121">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="cc1a7-122">Docker 成為容器產業的既定標準，並受到 Windows 和 Linux 生態系統中最重要廠商的支援</span><span class="sxs-lookup"><span data-stu-id="cc1a7-122">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="cc1a7-123"> (Microsoft 是支援 Docker 的主要雲端廠商之一。未來 ) ，Docker 可能會在雲端或內部部署的任何資料中心內普遍存在。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-123">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="cc1a7-124">此外，[微服務](https://martinfowler.com/articles/microservices.html)架構已躍升為分散式關鍵任務應用程式的重要方法。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-124">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="cc1a7-125">在微服務架構中，應用程式會建置在一組可獨立開發、測試、部署及設定版本的服務之上。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-125">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="cc1a7-126">關於本指南</span><span class="sxs-lookup"><span data-stu-id="cc1a7-126">About this guide</span></span>

<span data-ttu-id="cc1a7-127">本指南介紹如何開發微服務應用程式及使用容器進行管理，</span><span class="sxs-lookup"><span data-stu-id="cc1a7-127">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="cc1a7-128">並討論使用 .NET Core 和 Docker 容器的架構設計和實作方法。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-128">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="cc1a7-129">為了讓您更輕鬆地開始使用容器和微服務，本指南將重點放在您可以探索的容器化和微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-129">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="cc1a7-130">此範例應用程式位於 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-130">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="cc1a7-131">本指南提供主要在開發環境層級的基本開發和架構指引，並著重於兩項技術：Docker 和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-131">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="cc1a7-132">我們的用意是讓您在思考應用程式設計，但不想要將重點放在生產環境的基礎結構 (雲端或內部部署) 時，可以閱讀本指南。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-132">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="cc1a7-133">稍後，當您建立可實際執行的應用程式時，您將會制定基礎結構的相關決策。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-133">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="cc1a7-134">因此，本指南與基礎結構無關，而是偏重開發環境。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-134">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="cc1a7-135">研讀本指南之後，您的下一個步驟是了解 Microsoft Azure 上可實際執行的微服務。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-135">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="version"></a><span data-ttu-id="cc1a7-136">版本</span><span class="sxs-lookup"><span data-stu-id="cc1a7-136">Version</span></span>

<span data-ttu-id="cc1a7-137">本指南已經過修訂，涵蓋了 **.Net core 3.1** 版本，以及許多與相同「wave」技術相關的其他更新 (也就是，Azure 和其他協力廠商技術) 導致及時使用 .net Core 3.1 版本。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-137">This guide has been revised to cover **.NET Core 3.1** version along with many additional updates related to the same “wave” of technologies (that is, Azure and additional third-party technologies) coinciding in time with the .NET Core 3.1 release.</span></span> <span data-ttu-id="cc1a7-138">這就是為什麼書籍版本也更新為 **3.1** 版。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-138">That’s why the book version has also been updated to version **3.1**.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="cc1a7-139">本指南未涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="cc1a7-139">What this guide does not cover</span></span>

<span data-ttu-id="cc1a7-140">本指南的重點不在應用程式生命週期、DevOps、CI/CD 管線或小組合作。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-140">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="cc1a7-141">補充性指南 [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Microsoft 平台和工具的容器化 Docker 應用程式生命週期) 會以該主題為重點。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-141">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="cc1a7-142">目前的指南也不提供 Azure 基礎結構的實作詳細資料，例如特定 Orchestrator 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-142">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="cc1a7-143">其他資源</span><span class="sxs-lookup"><span data-stu-id="cc1a7-143">Additional resources</span></span>

- <span data-ttu-id="cc1a7-144">**Microsoft 平台和工具的容器化 Docker 應用程式生命週期** (可下載的電子書)</span><span class="sxs-lookup"><span data-stu-id="cc1a7-144">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable e-book)</span></span>  
    <https://aka.ms/dockerlifecycleebook>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="cc1a7-145">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="cc1a7-145">Who should use this guide</span></span>

<span data-ttu-id="cc1a7-146">本指南的撰寫對象是剛接觸 Docker 應用程式開發和微服務架構的開發人員和解決方案架構師。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-146">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="cc1a7-147">如果您想要了解如何使用 Microsoft 開發技術 (特別是 .NET Core) 和 Docker 容器，來架構、設計及實作概念證明應用程式，則本指南很適合您。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-147">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="cc1a7-148">如果您是技術決策者 (例如企業架構師)，想概括了解架構和技術，再決定要選取哪個方法以用於新的現代化分散式應用程式，您也會發現本指南很實用。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-148">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="cc1a7-149">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="cc1a7-149">How to use this guide</span></span>

<span data-ttu-id="cc1a7-150">本指南的第一部分介紹 Docker 容器、討論如何在 .NET Core 和 .NET Framework 之間選擇開發架構，並提供微服務概觀。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-150">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="cc1a7-151">此內容適用於需要概觀但重點不在程式碼實作詳細資料的架構師和技術決策者。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-151">This content is for architects and technical decision makers who want an overview but don't need to focus on code implementation details.</span></span>

<span data-ttu-id="cc1a7-152">本指南的第二部分以 [Docker 應用程式的開發程序](./docker-application-development-process/index.md)一節開頭，</span><span class="sxs-lookup"><span data-stu-id="cc1a7-152">The second part of the guide starts with the [Development process for Docker based applications](./docker-application-development-process/index.md) section.</span></span> <span data-ttu-id="cc1a7-153">它著重于使用 .NET Core 和 Docker 來執行應用程式的開發和微服務模式。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-153">It focuses on the development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="cc1a7-154">本節對於想要專注於程式碼、模式和實作詳細資料的開發人員和架構師最為重要。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-154">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="cc1a7-155">相關微服務和容器參考應用程式：eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="cc1a7-155">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="cc1a7-156">eShopOnContainers 應用程式是 .NET Core 和微服務的開放原始碼參考應用程式，專為使用 Docker 容器進行部署所設計。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-156">The eShopOnContainers application is an open-source reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="cc1a7-157">應用程式是由多個子系統所組成，包括數個電子商店 UI 前端 (Web MVC 應用程式、Web SPA 和原生行動應用程式) 。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-157">The application consists of multiple subsystems, including several e-store UI front-ends (a Web MVC app, a Web SPA, and a native mobile app).</span></span> <span data-ttu-id="cc1a7-158">它也包含用來執行所有必要伺服器端作業的後端微服務和容器。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-158">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="cc1a7-159">應用程式的目的是要展示架構模式。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-159">The purpose of the application is to showcase architectural patterns.</span></span> <span data-ttu-id="cc1a7-160">**這不是用於生產環境的範本** ，無法用來啟動真實世界應用程式。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-160">**IT IS NOT A PRODUCTION-READY TEMPLATE** to start real-world applications.</span></span> <span data-ttu-id="cc1a7-161">事實上，應用程式會處於永久的 Beta 狀態，因為它也可用來測試出現的新可能有趣技術。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-161">In fact, the application is in a permanent beta state, as it's also used to test new potentially interesting technologies as they show up.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="cc1a7-162">將您的意見反應傳送給我們！</span><span class="sxs-lookup"><span data-stu-id="cc1a7-162">Send us your feedback!</span></span>

<span data-ttu-id="cc1a7-163">本指南的撰寫目的是為了協助您了解 .NET 中的容器化應用程式和微服務架構。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-163">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="cc1a7-164">本指南和相關參考應用程式會不斷改進，因此歡迎您提供寶貴的意見反應！</span><span class="sxs-lookup"><span data-stu-id="cc1a7-164">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="cc1a7-165">如果您有關于如何改進本指南的意見，請在中提交意見反應 <https://aka.ms/ebookfeedback> 。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-165">If you have comments about how this guide can be improved, submit feedback at <https://aka.ms/ebookfeedback>.</span></span>

## <a name="credits"></a><span data-ttu-id="cc1a7-166">學分</span><span class="sxs-lookup"><span data-stu-id="cc1a7-166">Credits</span></span>

<span data-ttu-id="cc1a7-167">共同作者：</span><span class="sxs-lookup"><span data-stu-id="cc1a7-167">Co-Authors:</span></span>

> <span data-ttu-id="cc1a7-168">**Cesar de la Torre** ，Sr. Microsoft Corp. .NET 產品小組 PM</span><span class="sxs-lookup"><span data-stu-id="cc1a7-168">**Cesar de la Torre** , Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="cc1a7-169">**Bill Wagner** ，Sr. Microsoft Corp. C+E 內容開發人員</span><span class="sxs-lookup"><span data-stu-id="cc1a7-169">**Bill Wagner** , Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="cc1a7-170">**Mike Rousos** ，Microsoft DevDiv CAT 小組首席軟體工程師</span><span class="sxs-lookup"><span data-stu-id="cc1a7-170">**Mike Rousos** , Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="cc1a7-171">編輯者：</span><span class="sxs-lookup"><span data-stu-id="cc1a7-171">Editors:</span></span>

> <span data-ttu-id="cc1a7-172">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="cc1a7-172">**Mike Pope**</span></span>
>
> <span data-ttu-id="cc1a7-173">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="cc1a7-173">**Steve Hoag**</span></span>

<span data-ttu-id="cc1a7-174">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="cc1a7-174">Participants and reviewers:</span></span>

> <span data-ttu-id="cc1a7-175">**Jeffrey Ritcher** ，Microsoft Azure 小組合作夥伴軟體工程師</span><span class="sxs-lookup"><span data-stu-id="cc1a7-175">**Jeffrey Richter** , Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-176">**Jimmy Bogard** ，Headspring 首席架構師</span><span class="sxs-lookup"><span data-stu-id="cc1a7-176">**Jimmy Bogard** , Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="cc1a7-177">**Udi Dahan** ，Particular Software 創辦人暨執行長</span><span class="sxs-lookup"><span data-stu-id="cc1a7-177">**Udi Dahan** , Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="cc1a7-178">**Jimmy Nilsson** ，Factor10 共同創辦人暨執行長</span><span class="sxs-lookup"><span data-stu-id="cc1a7-178">**Jimmy Nilsson** , Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="cc1a7-179">**Glenn Condron** ，Sr. ASP.NET 小組計畫經理</span><span class="sxs-lookup"><span data-stu-id="cc1a7-179">**Glenn Condron** , Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="cc1a7-180">**Mark Fussell** ，Microsoft Azure Service Fabric 小組 PM 主管</span><span class="sxs-lookup"><span data-stu-id="cc1a7-180">**Mark Fussell** , Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-181">**Diego Vega** ，Microsoft Entity Framework 小組 PM 主管</span><span class="sxs-lookup"><span data-stu-id="cc1a7-181">**Diego Vega** , PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-182">**Barry Dorrans** ，Sr. 安全性計畫經理</span><span class="sxs-lookup"><span data-stu-id="cc1a7-182">**Barry Dorrans** , Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="cc1a7-183">**Rowan Miller** ，Sr. Microsoft 計畫經理</span><span class="sxs-lookup"><span data-stu-id="cc1a7-183">**Rowan Miller** , Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-184">**Ankit Asthana** ，Microsoft .NET 小組 PM 總經理</span><span class="sxs-lookup"><span data-stu-id="cc1a7-184">**Ankit Asthana** , Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-185">**Scott Hunter** ，Microsoft .NET 小組合夥人暨 PM 主管</span><span class="sxs-lookup"><span data-stu-id="cc1a7-185">**Scott Hunter** , Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-186">**Nish Anil** ，Microsoft NET 小組資深方案經理</span><span class="sxs-lookup"><span data-stu-id="cc1a7-186">**Nish Anil** , Sr. Program Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-187">**Dylan Reisenberger** ，Polly 架構師暨開發部門主管</span><span class="sxs-lookup"><span data-stu-id="cc1a7-187">**Dylan Reisenberger** , Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="cc1a7-188">**Steve "ardalis" Smith** - 軟體架構設計人員和講師 - [Ardalis.com](https://ardalis.com)</span><span class="sxs-lookup"><span data-stu-id="cc1a7-188">**Steve "ardalis" Smith** - Software Architect and Trainer - [Ardalis.com](https://ardalis.com)</span></span>
>
> <span data-ttu-id="cc1a7-189">**Ian Cooper** ，Brighter 程式碼架構師</span><span class="sxs-lookup"><span data-stu-id="cc1a7-189">**Ian Cooper** , Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="cc1a7-190">**Unai Zorrilla** ，Plain Concepts 架構師暨開發部門主管</span><span class="sxs-lookup"><span data-stu-id="cc1a7-190">**Unai Zorrilla** , Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="cc1a7-191">**Eduard Tomas** ，Plain Concepts 開發部門主管</span><span class="sxs-lookup"><span data-stu-id="cc1a7-191">**Eduard Tomas** , Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="cc1a7-192">**Ramon Tomas** ，Plain Concepts 開發人員</span><span class="sxs-lookup"><span data-stu-id="cc1a7-192">**Ramon Tomas** , Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="cc1a7-193">**David Sanz** ，Plain Concepts 開發人員</span><span class="sxs-lookup"><span data-stu-id="cc1a7-193">**David Sanz** , Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="cc1a7-194">**Javier Valero** ，Grupo Solutio 營運長</span><span class="sxs-lookup"><span data-stu-id="cc1a7-194">**Javier Valero** , Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="cc1a7-195">**Pierre Millet** ，Sr. Microsoft 顧問</span><span class="sxs-lookup"><span data-stu-id="cc1a7-195">**Pierre Millet** , Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-196">**Michael Friis** ，Docker Inc. 產品經理</span><span class="sxs-lookup"><span data-stu-id="cc1a7-196">**Michael Friis** , Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="cc1a7-197">**Charles Lowell** ，Microsoft VS CAT 小組軟體工程師</span><span class="sxs-lookup"><span data-stu-id="cc1a7-197">**Charles Lowell** , Software Engineer, VS CAT team, Microsoft</span></span>
>
> <span data-ttu-id="cc1a7-198">以簡單的概念 **Miguel Veloso** 軟體發展工程師</span><span class="sxs-lookup"><span data-stu-id="cc1a7-198">**Miguel Veloso** , Software Development Engineer at Plain Concepts</span></span>
>
> <span data-ttu-id="cc1a7-199">Neudesic 提供的首席顧問 **Sumit Ghosh**</span><span class="sxs-lookup"><span data-stu-id="cc1a7-199">**Sumit Ghosh** , Principal Consultant at Neudesic</span></span>

## <a name="copyright"></a><span data-ttu-id="cc1a7-200">著作權</span><span class="sxs-lookup"><span data-stu-id="cc1a7-200">Copyright</span></span>

<span data-ttu-id="cc1a7-201">發行者</span><span class="sxs-lookup"><span data-stu-id="cc1a7-201">PUBLISHED BY</span></span>

<span data-ttu-id="cc1a7-202">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="cc1a7-202">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="cc1a7-203">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="cc1a7-203">A division of Microsoft Corporation</span></span>

<span data-ttu-id="cc1a7-204">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="cc1a7-204">One Microsoft Way</span></span>

<span data-ttu-id="cc1a7-205">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="cc1a7-205">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="cc1a7-206">Microsoft Corporation 的著作權©2020</span><span class="sxs-lookup"><span data-stu-id="cc1a7-206">Copyright © 2020 by Microsoft Corporation</span></span>

<span data-ttu-id="cc1a7-207">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-207">All rights reserved.</span></span> <span data-ttu-id="cc1a7-208">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-208">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="cc1a7-209">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-209">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="cc1a7-210">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-210">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="cc1a7-211">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-211">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="cc1a7-212">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-212">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="cc1a7-213">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-213">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="cc1a7-214">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-214">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="cc1a7-215">Docker whale 標誌是 Docker，Inc. 所用的注冊商標。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-215">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="cc1a7-216">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="cc1a7-216">All other marks and logos are property of their respective owners.</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="cc1a7-217">下一步</span><span class="sxs-lookup"><span data-stu-id="cc1a7-217">Next</span></span>](container-docker-introduction/index.md)
