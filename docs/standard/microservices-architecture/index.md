---
title: ".NET 微服務。 容器化 .NET 應用程式的架構"
description: "容器化 .NET 應用程式的 .NET 微服務架構 | 前言"
keywords: "Docker, 微服務, ASP.NET, 容器"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.translationtype: HT
ms.sourcegitcommit: 9bb64ea7199f5699ff166d1affb7f8126dcc6612
ms.openlocfilehash: 4307c21f32e914118c03393be7ed7a632c7a7f0b
ms.contentlocale: zh-tw
ms.lasthandoff: 09/05/2017

---

![](./media/cover.png)

# <a name="net-microservices-architecture-for-containerized-net-applications"></a><span data-ttu-id="3f8eb-105">.NET 微服務。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-105">.NET Microservices.</span></span> <span data-ttu-id="3f8eb-106">容器化 .NET 應用程式的架構</span><span class="sxs-lookup"><span data-stu-id="3f8eb-106">Architecture for Containerized .NET Applications</span></span>

<span data-ttu-id="3f8eb-107">下載位置：<https://aka.ms/microservicesebook></span><span class="sxs-lookup"><span data-stu-id="3f8eb-107">DOWNLOAD available at: <https://aka.ms/microservicesebook></span></span>

<span data-ttu-id="3f8eb-108">發行者</span><span class="sxs-lookup"><span data-stu-id="3f8eb-108">PUBLISHED BY</span></span>

<span data-ttu-id="3f8eb-109">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="3f8eb-109">Microsoft Developer Division, .NET and Visual Studio product teams</span></span>

<span data-ttu-id="3f8eb-110">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="3f8eb-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="3f8eb-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="3f8eb-111">One Microsoft Way</span></span>

<span data-ttu-id="3f8eb-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="3f8eb-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="3f8eb-113">Copyright © 2017 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="3f8eb-113">Copyright © 2017 by Microsoft Corporation</span></span>

<span data-ttu-id="3f8eb-114">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-114">All rights reserved.</span></span> <span data-ttu-id="3f8eb-115">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="3f8eb-116">本書是以「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-116">This book is provided “as-is” and expresses the author’s views and opinions.</span></span> <span data-ttu-id="3f8eb-117">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="3f8eb-118">此處所描述的一些範例僅供說明，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="3f8eb-119">任何實際關聯或連結純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="3f8eb-120">Microsoft 與列於 http://www.microsoft.com「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-120">Microsoft and the trademarks listed at http://www.microsoft.com on the “Trademarks” webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="3f8eb-121">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="3f8eb-122">Docker 鯨魚標誌是 Docker, Inc. 的註冊商標。使用需要許可。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-122">The Docker whale logo is a registered trademark of Docker, Inc. Used by permission.</span></span>

<span data-ttu-id="3f8eb-123">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-123">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="3f8eb-124">共同作者：</span><span class="sxs-lookup"><span data-stu-id="3f8eb-124">Co-Authors:</span></span>

> <span data-ttu-id="3f8eb-125">**Cesar de la Torre**, Sr.，Microsoft Corp. .NET 產品小組 PM</span><span class="sxs-lookup"><span data-stu-id="3f8eb-125">**Cesar de la Torre**, Sr. PM, .NET product team, Microsoft Corp.</span></span>
>
> <span data-ttu-id="3f8eb-126">**Bill Wagner**, Sr.，Microsoft Corp. C+E 內容開發人員</span><span class="sxs-lookup"><span data-stu-id="3f8eb-126">**Bill Wagner**, Sr. Content Developer, C+E, Microsoft Corp.</span></span>
>
> <span data-ttu-id="3f8eb-127">**Mike Rousos**，Microsoft DevDiv CAT 小組首席軟體工程師</span><span class="sxs-lookup"><span data-stu-id="3f8eb-127">**Mike Rousos**, Principal Software Engineer, DevDiv CAT team, Microsoft</span></span>

<span data-ttu-id="3f8eb-128">編輯者：</span><span class="sxs-lookup"><span data-stu-id="3f8eb-128">Editors:</span></span>

> <span data-ttu-id="3f8eb-129">**Mike Pope**</span><span class="sxs-lookup"><span data-stu-id="3f8eb-129">**Mike Pope**</span></span>
>
> <span data-ttu-id="3f8eb-130">**Steve Hoag**</span><span class="sxs-lookup"><span data-stu-id="3f8eb-130">**Steve Hoag**</span></span>

<span data-ttu-id="3f8eb-131">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="3f8eb-131">Participants and reviewers:</span></span>

> <span data-ttu-id="3f8eb-132">**Jeffrey Ritcher**，Microsoft Azure 小組合夥人暨軟體工程師</span><span class="sxs-lookup"><span data-stu-id="3f8eb-132">**Jeffrey Ritcher**, Partner Software Eng, Azure team, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-133">**Jimmy Bogard**，Headspring 首席架構師</span><span class="sxs-lookup"><span data-stu-id="3f8eb-133">**Jimmy Bogard**, Chief Architect at Headspring</span></span>
>
> <span data-ttu-id="3f8eb-134">**Udi Dahan**，Particular Software 創辦人暨執行長</span><span class="sxs-lookup"><span data-stu-id="3f8eb-134">**Udi Dahan**, Founder & CEO, Particular Software</span></span>
>
> <span data-ttu-id="3f8eb-135">**Jimmy Nilsson**，Factor10 共同創辦人暨執行長</span><span class="sxs-lookup"><span data-stu-id="3f8eb-135">**Jimmy Nilsson**, Co-founder and CEO of Factor10</span></span>
>
> <span data-ttu-id="3f8eb-136">**Glenn Condron**, Sr.，ASP.NET 小組程式經理</span><span class="sxs-lookup"><span data-stu-id="3f8eb-136">**Glenn Condron**, Sr. Program Manager, ASP.NET team</span></span>
>
> <span data-ttu-id="3f8eb-137">**Mark Fussell**，Microsoft Azure Service Fabric 小組 PM 主管</span><span class="sxs-lookup"><span data-stu-id="3f8eb-137">**Mark Fussell**, Principal PM Lead, Azure Service Fabric team, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-138">**Diego Vega**，Microsoft Entity Framework 小組 PM 主管</span><span class="sxs-lookup"><span data-stu-id="3f8eb-138">**Diego Vega**, PM Lead, Entity Framework team, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-139">**Barry Dorrans**, Sr.，安全性程式經理</span><span class="sxs-lookup"><span data-stu-id="3f8eb-139">**Barry Dorrans**, Sr. Security Program Manager</span></span>
>
> <span data-ttu-id="3f8eb-140">**Rowan Miller**, Sr.，Microsoft 程式經理</span><span class="sxs-lookup"><span data-stu-id="3f8eb-140">**Rowan Miller**, Sr. Program Manager, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-141">**Ankit Asthana**，Microsoft .NET 小組 PM 總經理</span><span class="sxs-lookup"><span data-stu-id="3f8eb-141">**Ankit Asthana**, Principal PM Manager, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-142">**Scott Hunter**，Microsoft .NET 小組合夥人暨 PM 主管</span><span class="sxs-lookup"><span data-stu-id="3f8eb-142">**Scott Hunter**, Partner Director PM, .NET team, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-143">**Dylan Reisenberger**，Polly 架構師暨開發部門主管</span><span class="sxs-lookup"><span data-stu-id="3f8eb-143">**Dylan Reisenberger**, Architect and Dev Lead at Polly</span></span>
>
> <span data-ttu-id="3f8eb-144">**Steve Smith**，ASPSmith Ltd. 軟體工程師暨訓練員</span><span class="sxs-lookup"><span data-stu-id="3f8eb-144">**Steve Smith**, Software Craftsman & Trainer at ASPSmith Ltd.</span></span>
>
> <span data-ttu-id="3f8eb-145">**Ian Cooper**，Brighter 程式碼架構師</span><span class="sxs-lookup"><span data-stu-id="3f8eb-145">**Ian Cooper**, Coding Architect at Brighter</span></span>
>
> <span data-ttu-id="3f8eb-146">**Unai Zorrilla**，Plain Concepts 架構師暨開發部門主管</span><span class="sxs-lookup"><span data-stu-id="3f8eb-146">**Unai Zorrilla**, Architect and Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="3f8eb-147">**Eduard Tomas**，Plain Concepts 開發部門主管</span><span class="sxs-lookup"><span data-stu-id="3f8eb-147">**Eduard Tomas**, Dev Lead at Plain Concepts</span></span>
>
> <span data-ttu-id="3f8eb-148">**Ramon Tomas**，Plain Concepts 開發人員</span><span class="sxs-lookup"><span data-stu-id="3f8eb-148">**Ramon Tomas**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="3f8eb-149">**David Sanz**，Plain Concepts 開發人員</span><span class="sxs-lookup"><span data-stu-id="3f8eb-149">**David Sanz**, Developer at Plain Concepts</span></span>
>
> <span data-ttu-id="3f8eb-150">**Javier Valero**，Grupo Solutio 營運長</span><span class="sxs-lookup"><span data-stu-id="3f8eb-150">**Javier Valero**, Chief Operating Officer at Grupo Solutio</span></span>
>
> <span data-ttu-id="3f8eb-151">**Pierre Millet**, Sr.，Microsoft 顧問</span><span class="sxs-lookup"><span data-stu-id="3f8eb-151">**Pierre Millet**, Sr. Consultant, Microsoft</span></span>
>
> <span data-ttu-id="3f8eb-152">**Michael Friis**，Docker Inc. 產品經理</span><span class="sxs-lookup"><span data-stu-id="3f8eb-152">**Michael Friis**, Product Manager, Docker Inc</span></span>
>
> <span data-ttu-id="3f8eb-153">**Charles Lowell**，Microsoft VS CAT 小組軟體工程師</span><span class="sxs-lookup"><span data-stu-id="3f8eb-153">**Charles Lowell**, Software Engineer, VS CAT team, Microsoft</span></span>

## <a name="introduction"></a><span data-ttu-id="3f8eb-154">簡介</span><span class="sxs-lookup"><span data-stu-id="3f8eb-154">Introduction</span></span>

<span data-ttu-id="3f8eb-155">企業透過容器，逐漸實現成本節約、解決部署問題，以及改善 DevOps 和生產環境作業。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-155">Enterprises are increasingly realizing cost savings, solving deployment problems, and improving DevOps and production operations by using containers.</span></span> <span data-ttu-id="3f8eb-156">Microsoft 藉由建立 Azure Container Service 和 Azure Service Fabric 等產品，以及藉由與 Docker、Mesosphere 和 Kubernetes 等業界領導者合作，不斷為 Windows 和 Linux 創新容器。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-156">Microsoft has been releasing container innovations for Windows and Linux by creating products like Azure Container Service and Azure Service Fabric, and by partnering with industry leaders like Docker, Mesosphere, and Kubernetes.</span></span> <span data-ttu-id="3f8eb-157">這些產品提供容器解決方案，可協助公司以雲端速度和規模建置及部署應用程式，而不論其選擇的平台或工具為何。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-157">These products deliver container solutions that help companies build and deploy applications at cloud speed and scale, whatever their choice of platform or tools.</span></span>

<span data-ttu-id="3f8eb-158">Docker 成為容器產業的既定標準，並受到 Windows 和 Linux 生態系統中最重要廠商的支援</span><span class="sxs-lookup"><span data-stu-id="3f8eb-158">Docker is becoming the de facto standard in the container industry, supported by the most significant vendors in the Windows and Linux ecosystems.</span></span> <span data-ttu-id="3f8eb-159">(Microsoft 是其中一個支援 Docker 的主要雲端廠商)。未來，Docker 可能會在雲端或內部部署的任何資料中心廣泛運用。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-159">(Microsoft is one of the main cloud vendors supporting Docker.) In the future, Docker will probably be ubiquitous in any datacenter in the cloud or on-premises.</span></span>

<span data-ttu-id="3f8eb-160">此外，[微服務](https://martinfowler.com/articles/microservices.html)架構已躍升為分散式關鍵任務應用程式的重要方法。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-160">In addition, the [microservices](https://martinfowler.com/articles/microservices.html) architecture is emerging as an important approach for distributed mission-critical applications.</span></span> <span data-ttu-id="3f8eb-161">在微服務架構中，應用程式會建置在一組可獨立開發、測試、部署及設定版本的服務之上。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-161">In a microservice-based architecture, the application is built on a collection of services that can be developed, tested, deployed, and versioned independently.</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="3f8eb-162">關於本指南</span><span class="sxs-lookup"><span data-stu-id="3f8eb-162">About this guide</span></span>

<span data-ttu-id="3f8eb-163">本指南介紹如何開發微服務應用程式及使用容器進行管理，</span><span class="sxs-lookup"><span data-stu-id="3f8eb-163">This guide is an introduction to developing microservices-based applications and managing them using containers.</span></span> <span data-ttu-id="3f8eb-164">並討論使用 .NET Core 和 Docker 容器的架構設計和實作方法。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-164">It discusses architectural design and implementation approaches using .NET Core and Docker containers.</span></span> <span data-ttu-id="3f8eb-165">為了讓您更輕鬆地開始使用容器和微服務，本指南將重點放在您可以探索的容器化和微服務應用程式。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-165">To make it easier to get started with containers and microservices, the guide focuses on a reference containerized and microservice-based application that you can explore.</span></span> <span data-ttu-id="3f8eb-166">此範例應用程式位於 [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-166">The sample application is available at the [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) GitHub repo.</span></span>

<span data-ttu-id="3f8eb-167">本指南提供主要在開發環境層級的基本開發和架構指引，並著重於兩項技術：Docker 和 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-167">This guide provides foundational development and architectural guidance primarily at a development environment level with a focus on two technologies: Docker and .NET Core.</span></span> <span data-ttu-id="3f8eb-168">我們的用意是讓您在思考應用程式設計，但不想要將重點放在生產環境的基礎結構 (雲端或內部部署) 時，可以閱讀本指南。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-168">Our intention is that you read this guide when thinking about your application design without focusing on the infrastructure (cloud or on-premises) of your production environment.</span></span> <span data-ttu-id="3f8eb-169">稍後，當您建立可實際執行的應用程式時，您將會制定基礎結構的相關決策。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-169">You will make decisions about your infrastructure later, when you create your production-ready applications.</span></span> <span data-ttu-id="3f8eb-170">因此，本指南與基礎結構無關，而是偏重開發環境。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-170">Therefore, this guide is intended to be infrastructure agnostic and more development-environment-centric.</span></span>

<span data-ttu-id="3f8eb-171">研讀本指南之後，您的下一個步驟是了解 Microsoft Azure 上可實際執行的微服務。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-171">After you have studied this guide, your next step would be to learn about production-ready microservices on Microsoft Azure.</span></span>

## <a name="what-this-guide-does-not-cover"></a><span data-ttu-id="3f8eb-172">本指南未涵蓋的內容</span><span class="sxs-lookup"><span data-stu-id="3f8eb-172">What this guide does not cover</span></span>

<span data-ttu-id="3f8eb-173">本指南的重點不在應用程式生命週期、DevOps、CI/CD 管線或小組合作。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-173">This guide does not focus on the application lifecycle, DevOps, CI/CD pipelines, or team work.</span></span> <span data-ttu-id="3f8eb-174">補充性指南 [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) (Microsoft 平台和工具的容器化 Docker 應用程式生命週期) 會以該主題為重點。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-174">The complementary guide [Containerized Docker Application Lifecycle with Microsoft Platform and Tools](https://aka.ms/dockerlifecycleebook) focuses on that subject.</span></span> <span data-ttu-id="3f8eb-175">目前的指南也不提供 Azure 基礎結構的實作詳細資料，例如特定 Orchestrator 的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-175">The current guide also does not provide implementation details on Azure infrastructure, such as information on specific orchestrators.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="3f8eb-176">其他資源</span><span class="sxs-lookup"><span data-stu-id="3f8eb-176">Additional resources</span></span>

-   <span data-ttu-id="3f8eb-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (Microsoft 平台和工具的容器化 Docker 應用程式生命週期) (可下載的電子書) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span><span class="sxs-lookup"><span data-stu-id="3f8eb-177">**Containerized Docker Application Lifecycle with Microsoft Platform and Tools** (downloadable eBook) [*https://aka.ms/dockerlifecycleebook*](https://aka.ms/dockerlifecycleebook)</span></span>

## <a name="who-should-use-this-guide"></a><span data-ttu-id="3f8eb-178">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="3f8eb-178">Who should use this guide</span></span>

<span data-ttu-id="3f8eb-179">本指南的撰寫對象是剛接觸 Docker 應用程式開發和微服務架構的開發人員和解決方案架構師。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-179">We wrote this guide for developers and solution architects who are new to Docker-based application development and to microservices-based architecture.</span></span> <span data-ttu-id="3f8eb-180">如果您想要了解如何使用 Microsoft 開發技術 (特別是 .NET Core) 和 Docker 容器，來架構、設計及實作概念證明應用程式，則本指南很適合您。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-180">This guide is for you if you want to learn how to architect, design, and implement proof-of-concept applications with Microsoft development technologies (with special focus on .NET Core) and with Docker containers.</span></span>

<span data-ttu-id="3f8eb-181">如果您是技術決策者 (例如企業架構師)，想概括了解架構和技術，再決定要選取哪個方法以用於新的現代化分散式應用程式，您也會發現本指南很實用。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-181">You will also find this guide useful if you are a technical decision maker, such as an enterprise architect, who wants an architecture and technology overview before you decide on what approach to select for new and modern distributed applications.</span></span>

### <a name="how-to-use-this-guide"></a><span data-ttu-id="3f8eb-182">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="3f8eb-182">How to use this guide</span></span>

<span data-ttu-id="3f8eb-183">本指南的第一部分介紹 Docker 容器、討論如何在 .NET Core 和 .NET Framework 之間選擇開發架構，並提供微服務概觀。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-183">The first part of this guide introduces Docker containers, discusses how to choose between .NET Core and the .NET Framework as a development framework, and provides an overview of microservices.</span></span> <span data-ttu-id="3f8eb-184">此內容適用於需要概觀但重點不在程式碼實作詳細資料的架構師和技術決策者。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-184">This content is for architects and technical decision makers who want an overview but who do not need to focus on code implementation details.</span></span>

<span data-ttu-id="3f8eb-185">本指南的第二部分以 [Docker 應用程式的開發程序](#ch_dev_process_for_docker_based_apps)一節開頭，</span><span class="sxs-lookup"><span data-stu-id="3f8eb-185">The second part of the guide starts with the [Development process for Docker based applications](#ch_dev_process_for_docker_based_apps) section.</span></span> <span data-ttu-id="3f8eb-186">並將重點放在使用 .NET Core 和 Docker 實作應用程式的開發和微服務模式。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-186">It focuses on development and microservice patterns for implementing applications using .NET Core and Docker.</span></span> <span data-ttu-id="3f8eb-187">本節對於想要專注於程式碼、模式和實作詳細資料的開發人員和架構師最為重要。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-187">This section will be of most interest to developers and architects who want to focus on code and on patterns and implementation details.</span></span>

## <a name="related-microservice-and-container-based-reference-application-eshoponcontainers"></a><span data-ttu-id="3f8eb-188">相關微服務和容器參考應用程式：eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="3f8eb-188">Related microservice and container-based reference application: eShopOnContainers</span></span>

<span data-ttu-id="3f8eb-189">eShopOnContainers 應用程式是 .NET Core 和微服務的參考應用程式，專為使用 Docker 容器進行部署所設計。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-189">The eShopOnContainers application is a reference app for .NET Core and microservices that is designed to be deployed using Docker containers.</span></span> <span data-ttu-id="3f8eb-190">此應用程式是由多個子系統所組成，包括數個電子商店 UI 前端 (Web 應用程式和原生行動應用程式)。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-190">The application consists of multiple subsystems, including several e-store UI front ends (a Web app and a native mobile app).</span></span> <span data-ttu-id="3f8eb-191">它也包含用來執行所有必要伺服器端作業的後端微服務和容器。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-191">It also includes the back-end microservices and containers for all required server-side operations.</span></span>

<span data-ttu-id="3f8eb-192">此微服務和容器應用程式原始碼是開放原始碼，並位於 [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub 存放庫中。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-192">This microservice and container-based application source code is open source and available at the [eShopOnContainers](http://aka.ms/MicroservicesArchitecture) GitHub repo.</span></span>

## <a name="send-us-your-feedback"></a><span data-ttu-id="3f8eb-193">將您的意見反應傳送給我們！</span><span class="sxs-lookup"><span data-stu-id="3f8eb-193">Send us your feedback!</span></span>

<span data-ttu-id="3f8eb-194">本指南的撰寫目的是為了協助您了解 .NET 中的容器化應用程式和微服務架構。</span><span class="sxs-lookup"><span data-stu-id="3f8eb-194">We wrote this guide to help you understand the architecture of containerized applications and microservices in .NET.</span></span> <span data-ttu-id="3f8eb-195">本指南和相關參考應用程式會不斷改進，因此歡迎您提供寶貴的意見反應！</span><span class="sxs-lookup"><span data-stu-id="3f8eb-195">The guide and related reference application will be evolving, so we welcome your feedback!</span></span> <span data-ttu-id="3f8eb-196">如果您對如何改進本指南有任何意見，請傳送到：</span><span class="sxs-lookup"><span data-stu-id="3f8eb-196">If you have comments about how this guide can be improved, please send them to:</span></span>

[dotnet-architecture-ebooks-feedback@service.microsoft.com](mailto:dotnet-architecture-ebooks-feedback@service.microsoft.com)

>[!div class="step-by-step"]
<span data-ttu-id="3f8eb-197">[下一個] (container-docker-introduction/index.md)</span><span class="sxs-lookup"><span data-stu-id="3f8eb-197">[Next] (container-docker-introduction/index.md)</span></span>

