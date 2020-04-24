---
title: 無伺服器應用程式：架構、模式和 Azure 實作
description: 無伺服器架構指南。 了解實作企業應用程式的無伺服器架構 (與基礎結構即服務 [IaaS] 或平台即服務 [PaaS] 相對) 的時機、原因和方式。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 04/22/2020
ms.openlocfilehash: 16e658a99feda6537189a45b53da514e67766999
ms.sourcegitcommit: 8b02d42f93adda304246a47f49f6449fc74a3af4
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/24/2020
ms.locfileid: "82135683"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a><span data-ttu-id="b74e5-104">無伺服器應用程式：架構、模式和 Azure 實作</span><span class="sxs-lookup"><span data-stu-id="b74e5-104">Serverless apps: Architecture, patterns, and Azure implementation</span></span>

![顯示無伺服器應用程式電子書封面的螢幕擷取畫面。](./media/index/serverless-apps-cover-v3.png)

<span data-ttu-id="b74e5-106">**版本 v3.0** -已更新為 Azure Functions v3</span><span class="sxs-lookup"><span data-stu-id="b74e5-106">**EDITION v3.0** - Updated to Azure Functions v3</span></span>

> <span data-ttu-id="b74e5-107">下載：<https://aka.ms/serverlessbookpdf></span><span class="sxs-lookup"><span data-stu-id="b74e5-107">DOWNLOAD available at: <https://aka.ms/serverlessbookpdf></span></span>

<span data-ttu-id="b74e5-108">發行者</span><span class="sxs-lookup"><span data-stu-id="b74e5-108">PUBLISHED BY</span></span>

<span data-ttu-id="b74e5-109">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="b74e5-109">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="b74e5-110">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="b74e5-110">A division of Microsoft Corporation</span></span>

<span data-ttu-id="b74e5-111">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="b74e5-111">One Microsoft Way</span></span>

<span data-ttu-id="b74e5-112">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="b74e5-112">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="b74e5-113">Microsoft &copy; Corporation 的著作權2018-2020</span><span class="sxs-lookup"><span data-stu-id="b74e5-113">Copyright &copy; 2018-2020 by Microsoft Corporation</span></span>

<span data-ttu-id="b74e5-114">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="b74e5-114">All rights reserved.</span></span> <span data-ttu-id="b74e5-115">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="b74e5-115">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="b74e5-116">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="b74e5-116">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="b74e5-117">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="b74e5-117">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="b74e5-118">此處描述的一些範例僅供說明之用，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="b74e5-118">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="b74e5-119">並未影射或關聯任何真實的人、事、物。</span><span class="sxs-lookup"><span data-stu-id="b74e5-119">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="b74e5-120">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="b74e5-120">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="b74e5-121">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="b74e5-121">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="b74e5-122">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="b74e5-122">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="b74e5-123">作者︰</span><span class="sxs-lookup"><span data-stu-id="b74e5-123">Author:</span></span>

> <span data-ttu-id="b74e5-124">**[Jeremy Likness](https://twitter.com/jeremylikness)**，Microsoft Corp 的資深 .Net 資料程式經理。</span><span class="sxs-lookup"><span data-stu-id="b74e5-124">**[Jeremy Likness](https://twitter.com/jeremylikness)**, Senior .NET Data Program Manager, Microsoft Corp.</span></span>

<span data-ttu-id="b74e5-125">參與者：</span><span class="sxs-lookup"><span data-stu-id="b74e5-125">Contributor:</span></span>

> <span data-ttu-id="b74e5-126">Microsoft Corp 的資深雲端提倡者**[Cecil Phillip](https://twitter.com/cecilphillip)**。</span><span class="sxs-lookup"><span data-stu-id="b74e5-126">**[Cecil Phillip](https://twitter.com/cecilphillip)**, Senior Cloud Advocate, Microsoft Corp.</span></span>

<span data-ttu-id="b74e5-127">編輯者：</span><span class="sxs-lookup"><span data-stu-id="b74e5-127">Editors:</span></span>

> <span data-ttu-id="b74e5-128">**[Bill Wagner](https://twitter.com/billwagner)**，Microsoft Corp 的資深內容開發人員。</span><span class="sxs-lookup"><span data-stu-id="b74e5-128">**[Bill Wagner](https://twitter.com/billwagner)**, Senior Content Developer, Microsoft Corp.</span></span>

> <span data-ttu-id="b74e5-129">Microsoft Corp 的資深內容開發人員**[Maira Wenzel](https://twitter.com/mairacw)**。</span><span class="sxs-lookup"><span data-stu-id="b74e5-129">**[Maira Wenzel](https://twitter.com/mairacw)**, Senior Content Developer, Microsoft Corp.</span></span>

<span data-ttu-id="b74e5-130">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="b74e5-130">Participants and reviewers:</span></span>

> <span data-ttu-id="b74e5-131">**[Steve Smith](https://twitter.com/ardalis)**，Ardalis Services 負責人。</span><span class="sxs-lookup"><span data-stu-id="b74e5-131">**[Steve Smith](https://twitter.com/ardalis)**, Owner, Ardalis Services.</span></span>

## <a name="introduction"></a><span data-ttu-id="b74e5-132">簡介</span><span class="sxs-lookup"><span data-stu-id="b74e5-132">Introduction</span></span>

<span data-ttu-id="b74e5-133">[無伺服器](https://azure.microsoft.com/solutions/serverless/)旨在朝純雲端機器碼的方向發展雲端平台。</span><span class="sxs-lookup"><span data-stu-id="b74e5-133">[Serverless](https://azure.microsoft.com/solutions/serverless/) is the evolution of cloud platforms in the direction of pure cloud native code.</span></span> <span data-ttu-id="b74e5-134">無伺服器可帶領開發人員更貼近商務邏輯，同時讓他們需擔心基礎結構。</span><span class="sxs-lookup"><span data-stu-id="b74e5-134">Serverless brings developers closer to business logic while insulating them from infrastructure concerns.</span></span> <span data-ttu-id="b74e5-135">這種模式並不代表「沒有伺服器」，而是「少掉伺服器」。</span><span class="sxs-lookup"><span data-stu-id="b74e5-135">It's a pattern that doesn't imply "no server" but rather, "less server."</span></span> <span data-ttu-id="b74e5-136">無伺服器程式碼由事件驅動。</span><span class="sxs-lookup"><span data-stu-id="b74e5-136">Serverless code is event-driven.</span></span> <span data-ttu-id="b74e5-137">程式碼可能因任何項目 (從傳統 HTTP Web 要求到計時器) 或上傳檔案，而受到觸發。</span><span class="sxs-lookup"><span data-stu-id="b74e5-137">Code may be triggered by anything from a traditional HTTP web request to a timer or the result of uploading a file.</span></span> <span data-ttu-id="b74e5-138">無伺服器背後的基礎結構可立即調整，以符合彈性需求，及提供微帳單以真正「支付您所使用項目的費用」。</span><span class="sxs-lookup"><span data-stu-id="b74e5-138">The infrastructure behind serverless allows for instant scale to meet elastic demands and offers micro-billing to truly "pay for what you use."</span></span> <span data-ttu-id="b74e5-139">無伺服器需要您以新的思考方式和方法建置應用程式，且並不是適合所有問題的解決方案。</span><span class="sxs-lookup"><span data-stu-id="b74e5-139">Serverless requires a new way of thinking and approach to building applications and isn't the right solution for every problem.</span></span> <span data-ttu-id="b74e5-140">身為開發人員，您必須決定：</span><span class="sxs-lookup"><span data-stu-id="b74e5-140">As a developer, you must decide:</span></span>

- <span data-ttu-id="b74e5-141">無伺服器的優缺點為何？</span><span class="sxs-lookup"><span data-stu-id="b74e5-141">What are the pros and cons of serverless?</span></span>
- <span data-ttu-id="b74e5-142">為什麼您應該考慮為自己的應用程式使用無伺服器？</span><span class="sxs-lookup"><span data-stu-id="b74e5-142">Why should you consider serverless for your own applications?</span></span>
- <span data-ttu-id="b74e5-143">您如何建置、測試、部署和維護無伺服器程式碼？</span><span class="sxs-lookup"><span data-stu-id="b74e5-143">How can you build, test, deploy, and maintain your serverless code?</span></span>
- <span data-ttu-id="b74e5-144">在現有應用程式中將程式碼移轉到無伺服器的理由為何，以及完成此轉換的最佳方式是什麼？</span><span class="sxs-lookup"><span data-stu-id="b74e5-144">Where does it make sense to migrate code to serverless in existing applications, and what is the best way to accomplish this transformation?</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="b74e5-145">關於本指南</span><span class="sxs-lookup"><span data-stu-id="b74e5-145">About this guide</span></span>

<span data-ttu-id="b74e5-146">本指南著重使用無伺服器之應用程式的雲端原生開發。</span><span class="sxs-lookup"><span data-stu-id="b74e5-146">This guide focuses on cloud native development of applications that use serverless.</span></span> <span data-ttu-id="b74e5-147">本書會在開發無伺服器應用程式的部分，特別說明優點和指出可能的缺點，並提供無伺服器架構的介紹。</span><span class="sxs-lookup"><span data-stu-id="b74e5-147">The book highlights the benefits and exposes the potential drawbacks of developing serverless apps and provides a survey of serverless architectures.</span></span> <span data-ttu-id="b74e5-148">也會說明許多無伺服器使用方式範例，以及各種不同無伺服器設計模式。</span><span class="sxs-lookup"><span data-stu-id="b74e5-148">Many examples of how serverless can be used are illustrated along with various serverless design patterns.</span></span>

<span data-ttu-id="b74e5-149">本指南說明 Azure 無伺服器平台的元件，並會特別說明如何使用 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) 實作無伺服器。</span><span class="sxs-lookup"><span data-stu-id="b74e5-149">This guide explains the components of the Azure serverless platform and focuses specifically on implementation of serverless using [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span> <span data-ttu-id="b74e5-150">您會了解觸發程序和繫結程序，以及如何使用永久的函式實作依賴狀態的無伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="b74e5-150">You'll learn about triggers and bindings as well as how to implement serverless apps that rely on state using durable functions.</span></span> <span data-ttu-id="b74e5-151">最後，商務範例和案例研究會提供內容和參考框架，有助您判斷無伺服器是否為適合您專案的方法。</span><span class="sxs-lookup"><span data-stu-id="b74e5-151">Finally, business examples and case studies will help provide context and a frame of reference to determine whether serverless is the right approach for your projects.</span></span>

## <a name="evolution-of-cloud-platforms"></a><span data-ttu-id="b74e5-152">雲端平台的演進</span><span class="sxs-lookup"><span data-stu-id="b74e5-152">Evolution of cloud platforms</span></span>

<span data-ttu-id="b74e5-153">無伺服器是雲端平台多次反覆演進的高峰。</span><span class="sxs-lookup"><span data-stu-id="b74e5-153">Serverless is the culmination of several iterations of cloud platforms.</span></span> <span data-ttu-id="b74e5-154">這項演進從資料中心內的實體電腦開始，逐漸發展為基礎結構即服務 (IaaS) 和平台即服務 (PaaS)。</span><span class="sxs-lookup"><span data-stu-id="b74e5-154">The evolution began with physical metal in the data center and progressed through Infrastructure as a Service (IaaS) and Platform as a Service (PaaS).</span></span>

![演進：從內部部署至無伺服器](./media/serverless-evolution-iaas-paas.png)

<span data-ttu-id="b74e5-156">在發展雲端以前，開發與作業之間的界限非常明確。</span><span class="sxs-lookup"><span data-stu-id="b74e5-156">Before the cloud, a discernible boundary existed between development and operations.</span></span> <span data-ttu-id="b74e5-157">部署應用程式代表要回答無數個問題，如：</span><span class="sxs-lookup"><span data-stu-id="b74e5-157">Deploying an application meant answering myriad questions like:</span></span>

- <span data-ttu-id="b74e5-158">應該安裝什麼硬體？</span><span class="sxs-lookup"><span data-stu-id="b74e5-158">What hardware should be installed?</span></span>
- <span data-ttu-id="b74e5-159">如何保護電腦的實體存取？</span><span class="sxs-lookup"><span data-stu-id="b74e5-159">How is physical access to the machine secured?</span></span>
- <span data-ttu-id="b74e5-160">資料中心需要不斷電供應系統 (UPS) 嗎？</span><span class="sxs-lookup"><span data-stu-id="b74e5-160">Does the data center require an Uninterruptible Power Supply (UPS)?</span></span>
- <span data-ttu-id="b74e5-161">儲存體備份傳送至何處？</span><span class="sxs-lookup"><span data-stu-id="b74e5-161">Where are storage backups sent?</span></span>
- <span data-ttu-id="b74e5-162">應該具有備用電力嗎？</span><span class="sxs-lookup"><span data-stu-id="b74e5-162">Should there be redundant power?</span></span>

<span data-ttu-id="b74e5-163">這份清單還不只如此，而且額外負荷也很龐大。</span><span class="sxs-lookup"><span data-stu-id="b74e5-163">The list goes on and the overhead was enormous.</span></span> <span data-ttu-id="b74e5-164">在許多情況下，IT 部門不得已，必須處理許多浪費的資源。</span><span class="sxs-lookup"><span data-stu-id="b74e5-164">In many situations, IT departments were forced to deal with incredible waste.</span></span> <span data-ttu-id="b74e5-165">浪費的原因是過度佈建服務器作為損毀修復和待命伺服器的備份電腦，以啟用相應放大。幸運的是，使用虛擬機器（Vm）的虛擬化技術（如[hyper-v](/virtualization/hyper-v-on-windows/about/)）引進了基礎結構即服務（IaaS）。</span><span class="sxs-lookup"><span data-stu-id="b74e5-165">The waste was due to over-allocation of servers as backup machines for disaster recovery and standby servers to enable scale-out. Fortunately, the introduction of virtualization technology (like [Hyper-V](/virtualization/hyper-v-on-windows/about/)) with Virtual Machines (VMs) gave rise to Infrastructure as a Service (IaaS).</span></span> <span data-ttu-id="b74e5-166">虛擬化的基礎結構可讓作業設定一組標準的伺服器作為骨幹，而創造出彈性的環境，可「視需求」佈建唯一的伺服器。</span><span class="sxs-lookup"><span data-stu-id="b74e5-166">Virtualized infrastructure allowed operations to set up a standard set of servers as the backbone, leading to a flexible environment capable of provisioning unique servers "on demand."</span></span> <span data-ttu-id="b74e5-167">更重要的是，虛擬化為使用雲端提供虛擬機器「作為服務」創造了很棒的條件。</span><span class="sxs-lookup"><span data-stu-id="b74e5-167">More important, virtualization set the stage for using the cloud to provide virtual machines "as a service."</span></span> <span data-ttu-id="b74e5-168">公司可以不用擔心備用電力或實體電腦。</span><span class="sxs-lookup"><span data-stu-id="b74e5-168">Companies could easily get out of the business of worrying about redundant power or physical machines.</span></span> <span data-ttu-id="b74e5-169">相反地，則是以虛擬環境為重心。</span><span class="sxs-lookup"><span data-stu-id="b74e5-169">Instead, they focused on the virtual environment.</span></span>

<span data-ttu-id="b74e5-170">因為作業仍需負責處理各種工作，所以 IaaS 仍然需要龐大的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="b74e5-170">IaaS still requires heavy overhead because operations is still responsible for various tasks.</span></span> <span data-ttu-id="b74e5-171">這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="b74e5-171">These tasks include:</span></span>

- <span data-ttu-id="b74e5-172">修補和備份伺服器。</span><span class="sxs-lookup"><span data-stu-id="b74e5-172">Patching and backing up servers.</span></span>
- <span data-ttu-id="b74e5-173">安裝套件。</span><span class="sxs-lookup"><span data-stu-id="b74e5-173">Installing packages.</span></span>
- <span data-ttu-id="b74e5-174">保持最新的作業系統。</span><span class="sxs-lookup"><span data-stu-id="b74e5-174">Keeping the operating system up-to-date.</span></span>
- <span data-ttu-id="b74e5-175">監視應用程式。</span><span class="sxs-lookup"><span data-stu-id="b74e5-175">Monitoring the application.</span></span>

<span data-ttu-id="b74e5-176">下一階段的演進則提供平台即服務 (PaaS)，以減少額外負荷。</span><span class="sxs-lookup"><span data-stu-id="b74e5-176">The next evolution reduced the overhead by providing Platform as a Service (PaaS).</span></span> <span data-ttu-id="b74e5-177">利用 PaaS，雲端提供者可處理作業系統、安全性修補程式，甚至是必要套件，以支援特定平台。</span><span class="sxs-lookup"><span data-stu-id="b74e5-177">With PaaS, the cloud provider handles operating systems, security patches, and even the required packages to support a specific platform.</span></span> <span data-ttu-id="b74e5-178">開發人員可以直接選擇「平臺目標」（例如「web 應用程式」或「API 端點」）並直接部署程式碼，而不需建立 VM，然後再設定 .NET 並啟動 Internet Information Services （IIS）伺服器。</span><span class="sxs-lookup"><span data-stu-id="b74e5-178">Instead of building a VM then configuring .NET and standing up Internet Information Services (IIS) servers, developers simply choose a "platform target" such as "web application" or "API endpoint" and deploy code directly.</span></span> <span data-ttu-id="b74e5-179">基礎結構問題已減少為：</span><span class="sxs-lookup"><span data-stu-id="b74e5-179">The infrastructure questions are reduced to:</span></span>

- <span data-ttu-id="b74e5-180">需要何種大小的服務？</span><span class="sxs-lookup"><span data-stu-id="b74e5-180">What size services are needed?</span></span>
- <span data-ttu-id="b74e5-181">服務如何相應放大 (新增更多伺服器或節點)？</span><span class="sxs-lookup"><span data-stu-id="b74e5-181">How do the services scale out (add more servers or nodes)?</span></span>
- <span data-ttu-id="b74e5-182">服務如何相應增加 (增加裝載伺服器或節點的容量)？</span><span class="sxs-lookup"><span data-stu-id="b74e5-182">How do the services scale up (increase the capacity of hosting servers or nodes)?</span></span>

<span data-ttu-id="b74e5-183">無伺服器以事件驅動的程式碼為重心，進一步將伺服器抽象化。</span><span class="sxs-lookup"><span data-stu-id="b74e5-183">Serverless further abstracts servers by focusing on event-driven code.</span></span> <span data-ttu-id="b74e5-184">開發人員所專注的部分不是平台，而是執行單一事項的微服務。</span><span class="sxs-lookup"><span data-stu-id="b74e5-184">Instead of a platform, developers can focus on a microservice that does one thing.</span></span> <span data-ttu-id="b74e5-185">建置無伺服器程式碼的兩大關鍵問題為：</span><span class="sxs-lookup"><span data-stu-id="b74e5-185">The two key questions for building the serverless code are:</span></span>

- <span data-ttu-id="b74e5-186">何者觸發程式碼？</span><span class="sxs-lookup"><span data-stu-id="b74e5-186">What triggers the code?</span></span>
- <span data-ttu-id="b74e5-187">程式碼會執行什麼工作？</span><span class="sxs-lookup"><span data-stu-id="b74e5-187">What does the code do?</span></span>

<span data-ttu-id="b74e5-188">使用無伺服器，基礎結構會抽象化。</span><span class="sxs-lookup"><span data-stu-id="b74e5-188">With serverless, infrastructure is abstracted.</span></span> <span data-ttu-id="b74e5-189">在某些情況下，開發人員完全不用再擔心主機。</span><span class="sxs-lookup"><span data-stu-id="b74e5-189">In some cases, the developer no longer worries about the host at all.</span></span> <span data-ttu-id="b74e5-190">不論 IIS、Kestrel、Apache 或一些其它 Web 伺服器的執行個體是否在執行，以管理 Web 要求，開發人員都可專注在 HTTP 觸發程式上。</span><span class="sxs-lookup"><span data-stu-id="b74e5-190">Whether or not an instance of IIS, Kestrel, Apache, or some other web server is running to manage web requests, the developer focuses on an HTTP trigger.</span></span> <span data-ttu-id="b74e5-191">觸發程序會為要求提供標準的跨平台承載。</span><span class="sxs-lookup"><span data-stu-id="b74e5-191">The trigger provides the standard, cross-platform payload for the request.</span></span> <span data-ttu-id="b74e5-192">承載不僅可簡化開發過程，還可協助測試，並在某些情況下，使程式碼容易跨平台移植。</span><span class="sxs-lookup"><span data-stu-id="b74e5-192">The payload not only simplifies the development process, but facilitates testing and in some cases, makes the code easily portable across platforms.</span></span>

<span data-ttu-id="b74e5-193">無伺服器的另一項功能就是微帳單。</span><span class="sxs-lookup"><span data-stu-id="b74e5-193">Another feature of serverless is micro-billing.</span></span> <span data-ttu-id="b74e5-194">Web 應用程式通常會裝載 Web API 端點。</span><span class="sxs-lookup"><span data-stu-id="b74e5-194">It's common for web applications to host Web API endpoints.</span></span> <span data-ttu-id="b74e5-195">在傳統裸機中，對於 IaaS 甚至是 PaaS 的實作，需要持續為要裝載 API 的資源付費。</span><span class="sxs-lookup"><span data-stu-id="b74e5-195">In traditional bare metal, IaaS and even PaaS implementations, the resources to host the APIs are paid for continuously.</span></span> <span data-ttu-id="b74e5-196">這表示即使未存取這些資源，您仍要付費才可裝載端點。</span><span class="sxs-lookup"><span data-stu-id="b74e5-196">That means you pay to host the endpoints even when they aren't being accessed.</span></span> <span data-ttu-id="b74e5-197">通常您會發現其中一個 API 的呼叫次數比其他 API 多，所以整個系統會為了支援常用的端點而有所調整。</span><span class="sxs-lookup"><span data-stu-id="b74e5-197">Often you'll find one API is called more than others, so the entire system is scaled based on supporting the popular endpoints.</span></span> <span data-ttu-id="b74e5-198">無伺服器可讓您個別調整每個端點，並依據使用量付費，所以當您未呼叫 API 時，就不會產生任何費用。</span><span class="sxs-lookup"><span data-stu-id="b74e5-198">Serverless enables you to scale each endpoint independently and pay for usage, so no costs are incurred when the APIs aren't being called.</span></span> <span data-ttu-id="b74e5-199">在許多情況下，移轉可大幅降低持續產生的費用，以支援端點。</span><span class="sxs-lookup"><span data-stu-id="b74e5-199">Migration may in many circumstances dramatically reduce the ongoing cost to support the endpoints.</span></span>

## <a name="what-this-guide-doesnt-cover"></a><span data-ttu-id="b74e5-200">本指南未說明的內容</span><span class="sxs-lookup"><span data-stu-id="b74e5-200">What this guide doesn't cover</span></span>

<span data-ttu-id="b74e5-201">本指南特別說明架構方法和設計模式，但不會深入說明 Azure Functions、[Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)或其他無伺服器平台的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="b74e5-201">This guide specifically emphasizes architecture approaches and design patterns and isn't a deep dive into the implementation details of Azure Functions, [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps), or other serverless platforms.</span></span> <span data-ttu-id="b74e5-202">例如，本指南不會說明，Logic Apps 的進階工作流程或 Azure Functions 的功能，例如設定跨原始來源資源共用 (CORS)、套用自訂網域，或上傳 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="b74e5-202">This guide doesn't cover, for example, advanced workflows with Logic Apps or features of Azure Functions such as configuring Cross-Origin Resource Sharing (CORS), applying custom domains, or uploading SSL certificates.</span></span> <span data-ttu-id="b74e5-203">這些詳細資料都可透過線上 [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions/functions-reference)取得。</span><span class="sxs-lookup"><span data-stu-id="b74e5-203">These details are available through the online [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions/functions-reference).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b74e5-204">其他資源</span><span class="sxs-lookup"><span data-stu-id="b74e5-204">Additional resources</span></span>

- [<span data-ttu-id="b74e5-205">Azure 架構中心</span><span class="sxs-lookup"><span data-stu-id="b74e5-205">Azure Architecture center</span></span>](https://docs.microsoft.com/azure/architecture/)
- [<span data-ttu-id="b74e5-206">雲端應用程式的最佳做法</span><span class="sxs-lookup"><span data-stu-id="b74e5-206">Best practices for cloud applications</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a><span data-ttu-id="b74e5-207">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="b74e5-207">Who should use the guide</span></span>

<span data-ttu-id="b74e5-208">本指南專為想要以 .NET 建置可在內部部署或雲端使用無伺服器元件之企業應用程式的開發人員和解決方案架構設計人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="b74e5-208">This guide was written for developers and solution architects who want to build enterprise applications with .NET that may use serverless components either on premises or in the cloud.</span></span> <span data-ttu-id="b74e5-209">它適合具有下列興趣的開發人員、架構設計人員和技術決策者：</span><span class="sxs-lookup"><span data-stu-id="b74e5-209">It's useful to developers, architects, and technical decision makers interested in:</span></span>

- <span data-ttu-id="b74e5-210">了解無伺服器開發的優缺點</span><span class="sxs-lookup"><span data-stu-id="b74e5-210">Understanding the pros and cons of serverless development</span></span>
- <span data-ttu-id="b74e5-211">了解如何處理無伺服器架構</span><span class="sxs-lookup"><span data-stu-id="b74e5-211">Learning how to approach serverless architecture</span></span>
- <span data-ttu-id="b74e5-212">無伺服器應用程式的實作範例</span><span class="sxs-lookup"><span data-stu-id="b74e5-212">Example implementations of serverless apps</span></span>

## <a name="how-to-use-the-guide"></a><span data-ttu-id="b74e5-213">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="b74e5-213">How to use the guide</span></span>

<span data-ttu-id="b74e5-214">本指南的第一部分會比較數個不同的架構方法，來探究為何無伺服器是可行的選項。</span><span class="sxs-lookup"><span data-stu-id="b74e5-214">The first part of this guide examines why serverless is a viable option by comparing several different architecture approaches.</span></span> <span data-ttu-id="b74e5-215">因為軟體開發的所有層面都會受到架構決策所影響，所以其會同時探究技術和開發生命週期。</span><span class="sxs-lookup"><span data-stu-id="b74e5-215">It examines both the technology and development lifecycle, because all aspects of software development are impacted by architecture decisions.</span></span> <span data-ttu-id="b74e5-216">接著本指南會探究使用案例和設計模式，並包含使用 Azure Functions 的參考實作。</span><span class="sxs-lookup"><span data-stu-id="b74e5-216">The guide then examines use cases and design patterns and includes reference implementations using Azure Functions.</span></span> <span data-ttu-id="b74e5-217">每個章節都會包含其他資源以深入了解特定領域。</span><span class="sxs-lookup"><span data-stu-id="b74e5-217">Each section contains additional resources to learn more about a particular area.</span></span> <span data-ttu-id="b74e5-218">最後本指南會提供無伺服器實作的逐步解說與實際操作探索資源。</span><span class="sxs-lookup"><span data-stu-id="b74e5-218">The guide concludes with resources for walkthroughs and hands-on exploration of serverless implementation.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="b74e5-219">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="b74e5-219">Send your feedback</span></span>

<span data-ttu-id="b74e5-220">本指南和相關範例會不斷改進，因此歡迎您提供意見反應！</span><span class="sxs-lookup"><span data-stu-id="b74e5-220">The guide and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="b74e5-221">如果您想提出如何改進本指南意見，請使用 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。</span><span class="sxs-lookup"><span data-stu-id="b74e5-221">If you have comments about how this guide can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="b74e5-222">下一步</span><span class="sxs-lookup"><span data-stu-id="b74e5-222">Next</span></span>](architecture-approaches.md)
