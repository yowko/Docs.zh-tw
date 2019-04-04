---
title: 無伺服器應用程式：架構、模式和 Azure 實作
description: 無伺服器架構指南。 了解實作企業應用程式的無伺服器架構 (與基礎結構即服務 [IaaS] 或平台即服務 [PaaS] 相對) 的時機、原因和方式。
author: JEREMYLIKNESS
ms.author: jeliknes
ms.date: 6/26/2018
ms.openlocfilehash: a44af1fc76b54ec9be0d8e3b3ba2e54f3e3b220b
ms.sourcegitcommit: 15ab532fd5e1f8073a4b678922d93b68b521bfa0
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/29/2019
ms.locfileid: "58653934"
---
# <a name="serverless-apps-architecture-patterns-and-azure-implementation"></a><span data-ttu-id="c9e76-104">無伺服器應用程式：架構、模式和 Azure 實作</span><span class="sxs-lookup"><span data-stu-id="c9e76-104">Serverless apps: Architecture, patterns, and Azure implementation</span></span>

![顯示無伺服器應用程式電子書封面的螢幕擷取畫面。](./media/index/serverless-apps-cover.jpg)

> <span data-ttu-id="c9e76-106">下載：<https://aka.ms/serverless-ebook></span><span class="sxs-lookup"><span data-stu-id="c9e76-106">DOWNLOAD available at: <https://aka.ms/serverless-ebook></span></span>

<span data-ttu-id="c9e76-107">發行者</span><span class="sxs-lookup"><span data-stu-id="c9e76-107">PUBLISHED BY</span></span>

<span data-ttu-id="c9e76-108">Microsoft 開發人員部門 .NET 和 Visual Studio 產品小組</span><span class="sxs-lookup"><span data-stu-id="c9e76-108">Microsoft Developer Division, .NET, and Visual Studio product teams</span></span>

<span data-ttu-id="c9e76-109">Microsoft Corporation 部門</span><span class="sxs-lookup"><span data-stu-id="c9e76-109">A division of Microsoft Corporation</span></span>

<span data-ttu-id="c9e76-110">One Microsoft Way</span><span class="sxs-lookup"><span data-stu-id="c9e76-110">One Microsoft Way</span></span>

<span data-ttu-id="c9e76-111">Redmond, Washington 98052-6399</span><span class="sxs-lookup"><span data-stu-id="c9e76-111">Redmond, Washington 98052-6399</span></span>

<span data-ttu-id="c9e76-112">Copyright © 2018 by Microsoft Corporation</span><span class="sxs-lookup"><span data-stu-id="c9e76-112">Copyright © 2018 by Microsoft Corporation</span></span>

<span data-ttu-id="c9e76-113">著作權所有，並保留一切權利。</span><span class="sxs-lookup"><span data-stu-id="c9e76-113">All rights reserved.</span></span> <span data-ttu-id="c9e76-114">本書內容的任何部分在未經過發行者書面許可下，不得以任何形式或透過任何方式進行重製或傳送。</span><span class="sxs-lookup"><span data-stu-id="c9e76-114">No part of the contents of this book may be reproduced or transmitted in any form or by any means without the written permission of the publisher.</span></span>

<span data-ttu-id="c9e76-115">本書依照「現況」提供，代表作者的觀點和意見。</span><span class="sxs-lookup"><span data-stu-id="c9e76-115">This book is provided "as-is" and expresses the author's views and opinions.</span></span> <span data-ttu-id="c9e76-116">本書中所述之觀點、意見與資訊 (包括 URL 及其他網際網路網站參考) 可能會隨時變更，恕不另行通知。</span><span class="sxs-lookup"><span data-stu-id="c9e76-116">The views, opinions and information expressed in this book, including URL and other Internet website references, may change without notice.</span></span>

<span data-ttu-id="c9e76-117">此處所描述的一些範例僅供說明，純屬虛構。</span><span class="sxs-lookup"><span data-stu-id="c9e76-117">Some examples depicted herein are provided for illustration only and are fictitious.</span></span> <span data-ttu-id="c9e76-118">任何實際關聯或連結純屬巧合。</span><span class="sxs-lookup"><span data-stu-id="c9e76-118">No real association or connection is intended or should be inferred.</span></span>

<span data-ttu-id="c9e76-119">Microsoft 與列於 <https://www.microsoft.com>「商標」網頁的商標是 Microsoft 集團的商標。</span><span class="sxs-lookup"><span data-stu-id="c9e76-119">Microsoft and the trademarks listed at <https://www.microsoft.com> on the "Trademarks" webpage are trademarks of the Microsoft group of companies.</span></span>

<span data-ttu-id="c9e76-120">Mac 與 macOS 是 Apple Inc. 的商標。</span><span class="sxs-lookup"><span data-stu-id="c9e76-120">Mac and macOS are trademarks of Apple Inc.</span></span>

<span data-ttu-id="c9e76-121">所有其他商標和標誌屬於其各自擁有者的財產。</span><span class="sxs-lookup"><span data-stu-id="c9e76-121">All other marks and logos are property of their respective owners.</span></span>

<span data-ttu-id="c9e76-122">作者: </span><span class="sxs-lookup"><span data-stu-id="c9e76-122">Author:</span></span>

> <span data-ttu-id="c9e76-123">**[Jeremy Likness](https://twitter.com/jeremylikness)**，Microsoft Corp. APEX 資深雲端開發大使。</span><span class="sxs-lookup"><span data-stu-id="c9e76-123">**[Jeremy Likness](https://twitter.com/jeremylikness)**, Sr. Cloud Developer Advocate, APEX, Microsoft Corp.</span></span>

<span data-ttu-id="c9e76-124">參與者：</span><span class="sxs-lookup"><span data-stu-id="c9e76-124">Contributor:</span></span>

> <span data-ttu-id="c9e76-125">**[Cecil Phillip](https://twitter.com/cecilphillip)**，Microsoft Corp. APEX 雲端開發大使 II</span><span class="sxs-lookup"><span data-stu-id="c9e76-125">**[Cecil Phillip](https://twitter.com/cecilphillip)**, Cloud Developer Advocate II, APEX, Microsoft Corp.</span></span>

<span data-ttu-id="c9e76-126">編輯者：</span><span class="sxs-lookup"><span data-stu-id="c9e76-126">Editors:</span></span>

> <span data-ttu-id="c9e76-127">**[Bill Wagner](https://twitter.com/billwagner)**，Microsoft Corp. APEX 資深內容開發人員</span><span class="sxs-lookup"><span data-stu-id="c9e76-127">**[Bill Wagner](https://twitter.com/billwagner)**, Senior Content Developer, APEX, Microsoft Corp.</span></span>

> <span data-ttu-id="c9e76-128">**[Maira Wenzel](https://twitter.com/mairacw)**，Microsoft Corp. APEX 資深內容開發人員</span><span class="sxs-lookup"><span data-stu-id="c9e76-128">**[Maira Wenzel](https://twitter.com/mairacw)**, Senior Content Developer, APEX, Microsoft Corp.</span></span>

<span data-ttu-id="c9e76-129">參與者和檢閱者：</span><span class="sxs-lookup"><span data-stu-id="c9e76-129">Participants and reviewers:</span></span>

> <span data-ttu-id="c9e76-130">**[Steve Smith](https://twitter.com/ardalis)**，Ardalis Services 負責人。</span><span class="sxs-lookup"><span data-stu-id="c9e76-130">**[Steve Smith](https://twitter.com/ardalis)**, Owner, Ardalis Services.</span></span>

## <a name="introduction"></a><span data-ttu-id="c9e76-131">簡介</span><span class="sxs-lookup"><span data-stu-id="c9e76-131">Introduction</span></span>

<span data-ttu-id="c9e76-132">[無伺服器](https://azure.microsoft.com/solutions/serverless/)旨在朝純雲端機器碼的方向發展雲端平台。</span><span class="sxs-lookup"><span data-stu-id="c9e76-132">[Serverless](https://azure.microsoft.com/solutions/serverless/) is the evolution of cloud platforms in the direction of pure cloud native code.</span></span> <span data-ttu-id="c9e76-133">無伺服器可帶領開發人員更貼近商務邏輯，同時讓他們需擔心基礎結構。</span><span class="sxs-lookup"><span data-stu-id="c9e76-133">Serverless brings developers closer to business logic while insulating them from infrastructure concerns.</span></span> <span data-ttu-id="c9e76-134">這種模式並不代表「沒有伺服器」，而是「少掉伺服器」。</span><span class="sxs-lookup"><span data-stu-id="c9e76-134">It's a pattern that doesn't imply "no server" but rather, "less server."</span></span> <span data-ttu-id="c9e76-135">無伺服器程式碼由事件驅動。</span><span class="sxs-lookup"><span data-stu-id="c9e76-135">Serverless code is event-driven.</span></span> <span data-ttu-id="c9e76-136">程式碼可能因任何項目 (從傳統 HTTP Web 要求到計時器) 或上傳檔案，而受到觸發。</span><span class="sxs-lookup"><span data-stu-id="c9e76-136">Code may be triggered by anything from a traditional HTTP web request to a timer or the result of uploading a file.</span></span> <span data-ttu-id="c9e76-137">無伺服器背後的基礎結構可立即調整，以符合彈性需求，及提供微帳單以真正「支付您所使用項目的費用」。</span><span class="sxs-lookup"><span data-stu-id="c9e76-137">The infrastructure behind serverless allows for instant scale to meet elastic demands and offers micro-billing to truly "pay for what you use."</span></span> <span data-ttu-id="c9e76-138">無伺服器需要您以新的思考方式和方法建置應用程式，且並不是適合所有問題的解決方案。</span><span class="sxs-lookup"><span data-stu-id="c9e76-138">Serverless requires a new way of thinking and approach to building applications and isn't the right solution for every problem.</span></span> <span data-ttu-id="c9e76-139">身為開發人員，您必須決定：</span><span class="sxs-lookup"><span data-stu-id="c9e76-139">As a developer, you must decide:</span></span>

* <span data-ttu-id="c9e76-140">無伺服器的優缺點為何？</span><span class="sxs-lookup"><span data-stu-id="c9e76-140">What are the pros and cons of serverless?</span></span>
* <span data-ttu-id="c9e76-141">為什麼您應該考慮為自己的應用程式使用無伺服器？</span><span class="sxs-lookup"><span data-stu-id="c9e76-141">Why should you consider serverless for your own applications?</span></span>
* <span data-ttu-id="c9e76-142">您如何建置、測試、部署和維護無伺服器程式碼？</span><span class="sxs-lookup"><span data-stu-id="c9e76-142">How can you build, test, deploy, and maintain your serverless code?</span></span>
* <span data-ttu-id="c9e76-143">在現有應用程式中將程式碼移轉到無伺服器的理由為何，以及完成此轉換的最佳方式是什麼？</span><span class="sxs-lookup"><span data-stu-id="c9e76-143">Where does it make sense to migrate code to serverless in existing applications, and what is the best way to accomplish this transformation?</span></span>

## <a name="about-this-guide"></a><span data-ttu-id="c9e76-144">關於本指南</span><span class="sxs-lookup"><span data-stu-id="c9e76-144">About this guide</span></span>

<span data-ttu-id="c9e76-145">本指南著重使用無伺服器之應用程式的雲端原生開發。</span><span class="sxs-lookup"><span data-stu-id="c9e76-145">This guide focuses on cloud native development of applications that use serverless.</span></span> <span data-ttu-id="c9e76-146">本書會在開發無伺服器應用程式的部分，特別說明優點和指出可能的缺點，並提供無伺服器架構的介紹。</span><span class="sxs-lookup"><span data-stu-id="c9e76-146">The book highlights the benefits and exposes the potential drawbacks of developing serverless apps and provides a survey of serverless architectures.</span></span> <span data-ttu-id="c9e76-147">也會說明許多無伺服器使用方式範例，以及各種不同無伺服器設計模式。</span><span class="sxs-lookup"><span data-stu-id="c9e76-147">Many examples of how serverless can be used are illustrated along with various serverless design patterns.</span></span>

<span data-ttu-id="c9e76-148">本指南說明 Azure 無伺服器平台的元件，並會特別說明如何使用 [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview) 實作無伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9e76-148">This guide explains the components of the Azure serverless platform and focuses specifically on implementation of serverless using [Azure Functions](https://docs.microsoft.com/azure/azure-functions/functions-overview).</span></span> <span data-ttu-id="c9e76-149">您會了解觸發程序和繫結程序，以及如何使用永久的函式實作依賴狀態的無伺服器應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9e76-149">You'll learn about triggers and bindings as well as how to implement serverless apps that rely on state using durable functions.</span></span> <span data-ttu-id="c9e76-150">最後，商務範例和案例研究會提供內容和參考框架，有助您判斷無伺服器是否為適合您專案的方法。</span><span class="sxs-lookup"><span data-stu-id="c9e76-150">Finally, business examples and case studies will help provide context and a frame of reference to determine whether serverless is the right approach for your projects.</span></span>

## <a name="evolution-of-cloud-platforms"></a><span data-ttu-id="c9e76-151">雲端平台的演進</span><span class="sxs-lookup"><span data-stu-id="c9e76-151">Evolution of cloud platforms</span></span>

<span data-ttu-id="c9e76-152">無伺服器是雲端平台多次反覆演進的高峰。</span><span class="sxs-lookup"><span data-stu-id="c9e76-152">Serverless is the culmination of several iterations of cloud platforms.</span></span> <span data-ttu-id="c9e76-153">這項演進從資料中心內的實體電腦開始，逐漸發展為基礎結構即服務 (IaaS) 和平台即服務 (PaaS)。</span><span class="sxs-lookup"><span data-stu-id="c9e76-153">The evolution began with physical metal in the data center and progressed through Infrastructure as a Service (IaaS) and Platform as a Service (PaaS).</span></span>

![演進：從內部部署至無伺服器](./media/serverless-evolution-iaas-paas.png)

<span data-ttu-id="c9e76-155">在發展雲端以前，開發與作業之間的界限非常明確。</span><span class="sxs-lookup"><span data-stu-id="c9e76-155">Before the cloud, a discernible boundary existed between development and operations.</span></span> <span data-ttu-id="c9e76-156">部署應用程式代表要回答無數個問題，如：</span><span class="sxs-lookup"><span data-stu-id="c9e76-156">Deploying an application meant answering myriad questions like:</span></span>

* <span data-ttu-id="c9e76-157">應該安裝什麼硬體？</span><span class="sxs-lookup"><span data-stu-id="c9e76-157">What hardware should be installed?</span></span>
* <span data-ttu-id="c9e76-158">如何保護電腦的實體存取？</span><span class="sxs-lookup"><span data-stu-id="c9e76-158">How is physical access to the machine secured?</span></span>
* <span data-ttu-id="c9e76-159">資料中心需要不斷電供應系統 (UPS) 嗎？</span><span class="sxs-lookup"><span data-stu-id="c9e76-159">Does the data center require an Uninterruptible Power Supply (UPS)?</span></span>
* <span data-ttu-id="c9e76-160">儲存體備份傳送至何處？</span><span class="sxs-lookup"><span data-stu-id="c9e76-160">Where are storage backups sent?</span></span>
* <span data-ttu-id="c9e76-161">應該具有備用電力嗎？</span><span class="sxs-lookup"><span data-stu-id="c9e76-161">Should there be redundant power?</span></span>

<span data-ttu-id="c9e76-162">這份清單還不只如此，而且額外負荷也很龐大。</span><span class="sxs-lookup"><span data-stu-id="c9e76-162">The list goes on and the overhead was enormous.</span></span> <span data-ttu-id="c9e76-163">在許多情況下，IT 部門不得已，必須處理許多浪費的資源。</span><span class="sxs-lookup"><span data-stu-id="c9e76-163">In many situations, IT departments were forced to deal with incredible waste.</span></span> <span data-ttu-id="c9e76-164">浪費的原因是配置太多伺服器作為災害復原用的備份電腦和用於相應放大的待命伺服器。幸運的是，在隨著虛擬機器 (VM) 推出虛擬化技術後 (例如 [Hyper-V](/virtualization/hyper-v-on-windows/about/))，產生了基礎結構即服務 (IaaS)。</span><span class="sxs-lookup"><span data-stu-id="c9e76-164">The waste was due to over-allocation of servers as backup machines for disaster recovery and standby servers to enable scale-out. Fortunately, the introduction of virtualization technology (like [Hyper-V](/virtualization/hyper-v-on-windows/about/)) with Virtual Machines (VMs) gave rise to Infrastructure as a Service (IaaS).</span></span> <span data-ttu-id="c9e76-165">虛擬化的基礎結構可讓作業設定一組標準的伺服器作為骨幹，而創造出彈性的環境，可「視需求」佈建唯一的伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9e76-165">Virtualized infrastructure allowed operations to set up a standard set of servers as the backbone, leading to a flexible environment capable of provisioning unique servers "on demand."</span></span> <span data-ttu-id="c9e76-166">更重要的是，虛擬化為使用雲端提供虛擬機器「作為服務」創造了很棒的條件。</span><span class="sxs-lookup"><span data-stu-id="c9e76-166">More important, virtualization set the stage for using the cloud to provide virtual machines "as a service."</span></span> <span data-ttu-id="c9e76-167">公司可以不用擔心備用電力或實體電腦。</span><span class="sxs-lookup"><span data-stu-id="c9e76-167">Companies could easily get out of the business of worrying about redundant power or physical machines.</span></span> <span data-ttu-id="c9e76-168">相反地，則是以虛擬環境為重心。</span><span class="sxs-lookup"><span data-stu-id="c9e76-168">Instead, they focused on the virtual environment.</span></span>

<span data-ttu-id="c9e76-169">因為作業仍需負責處理各種工作，所以 IaaS 仍然需要龐大的額外負荷。</span><span class="sxs-lookup"><span data-stu-id="c9e76-169">IaaS still requires heavy overhead because operations is still responsible for various tasks.</span></span> <span data-ttu-id="c9e76-170">這些工作包括：</span><span class="sxs-lookup"><span data-stu-id="c9e76-170">These tasks include:</span></span>

* <span data-ttu-id="c9e76-171">修補和備份伺服器。</span><span class="sxs-lookup"><span data-stu-id="c9e76-171">Patching and backing up servers.</span></span>
* <span data-ttu-id="c9e76-172">安裝套件。</span><span class="sxs-lookup"><span data-stu-id="c9e76-172">Installing packages.</span></span>
* <span data-ttu-id="c9e76-173">保持最新的作業系統。</span><span class="sxs-lookup"><span data-stu-id="c9e76-173">Keeping the operating system up-to-date.</span></span>
* <span data-ttu-id="c9e76-174">監視應用程式。</span><span class="sxs-lookup"><span data-stu-id="c9e76-174">Monitoring the application.</span></span>

<span data-ttu-id="c9e76-175">下一階段的演進則提供平台即服務 (PaaS)，以減少額外負荷。</span><span class="sxs-lookup"><span data-stu-id="c9e76-175">The next evolution reduced the overhead by providing Platform as a Service (PaaS).</span></span> <span data-ttu-id="c9e76-176">利用 PaaS，雲端提供者可處理作業系統、安全性修補程式，甚至是必要套件，以支援特定平台。</span><span class="sxs-lookup"><span data-stu-id="c9e76-176">With PaaS, the cloud provider handles operating systems, security patches, and even the required packages to support a specific platform.</span></span> <span data-ttu-id="c9e76-177">開發人員並不需要建置 VM，然後設定 .NET Framework 和 Internet Information Services (IIS) 伺服器，只要選擇「平台目標」，如「Web 應用程式」或「API 端點」，然後直接部署程式碼。</span><span class="sxs-lookup"><span data-stu-id="c9e76-177">Instead of building a VM then configuring the .NET Framework and standing up Internet Information Services (IIS) servers, developers simply choose a "platform target" such as "web application" or "API endpoint" and deploy code directly.</span></span> <span data-ttu-id="c9e76-178">基礎結構問題已減少為：</span><span class="sxs-lookup"><span data-stu-id="c9e76-178">The infrastructure questions are reduced to:</span></span>

* <span data-ttu-id="c9e76-179">需要何種大小的服務？</span><span class="sxs-lookup"><span data-stu-id="c9e76-179">What size services are needed?</span></span>
* <span data-ttu-id="c9e76-180">服務如何相應放大 (新增更多伺服器或節點)？</span><span class="sxs-lookup"><span data-stu-id="c9e76-180">How do the services scale out (add more servers or nodes)?</span></span>
* <span data-ttu-id="c9e76-181">服務如何相應增加 (增加裝載伺服器或節點的容量)？</span><span class="sxs-lookup"><span data-stu-id="c9e76-181">How do the services scale up (increase the capacity of hosting servers or nodes)?</span></span>

<span data-ttu-id="c9e76-182">無伺服器以事件驅動的程式碼為重心，進一步將伺服器抽象化。</span><span class="sxs-lookup"><span data-stu-id="c9e76-182">Serverless further abstracts servers by focusing on event-driven code.</span></span> <span data-ttu-id="c9e76-183">開發人員所專注的部分不是平台，而是執行單一事項的微服務。</span><span class="sxs-lookup"><span data-stu-id="c9e76-183">Instead of a platform, developers can focus on a microservice that does one thing.</span></span> <span data-ttu-id="c9e76-184">建置無伺服器程式碼的兩大關鍵問題為：</span><span class="sxs-lookup"><span data-stu-id="c9e76-184">The two key questions for building the serverless code are:</span></span>

* <span data-ttu-id="c9e76-185">何者觸發程式碼？</span><span class="sxs-lookup"><span data-stu-id="c9e76-185">What triggers the code?</span></span>
* <span data-ttu-id="c9e76-186">程式碼會執行什麼工作？</span><span class="sxs-lookup"><span data-stu-id="c9e76-186">What does the code do?</span></span>

<span data-ttu-id="c9e76-187">使用無伺服器，基礎結構會抽象化。</span><span class="sxs-lookup"><span data-stu-id="c9e76-187">With serverless, infrastructure is abstracted.</span></span> <span data-ttu-id="c9e76-188">在某些情況下，開發人員完全不用再擔心主機。</span><span class="sxs-lookup"><span data-stu-id="c9e76-188">In some cases, the developer no longer worries about the host at all.</span></span> <span data-ttu-id="c9e76-189">不論 IIS、Kestrel、Apache 或一些其它 Web 伺服器的執行個體是否在執行，以管理 Web 要求，開發人員都可專注在 HTTP 觸發程式上。</span><span class="sxs-lookup"><span data-stu-id="c9e76-189">Whether or not an instance of IIS, Kestrel, Apache, or some other web server is running to manage web requests, the developer focuses on an HTTP trigger.</span></span> <span data-ttu-id="c9e76-190">觸發程序會為要求提供標準的跨平台承載。</span><span class="sxs-lookup"><span data-stu-id="c9e76-190">The trigger provides the standard, cross-platform payload for the request.</span></span> <span data-ttu-id="c9e76-191">承載不僅可簡化開發過程，還可協助測試，並在某些情況下，使程式碼容易跨平台移植。</span><span class="sxs-lookup"><span data-stu-id="c9e76-191">The payload not only simplifies the development process, but facilitates testing and in some cases, makes the code easily portable across platforms.</span></span>

<span data-ttu-id="c9e76-192">無伺服器的另一項功能就是微帳單。</span><span class="sxs-lookup"><span data-stu-id="c9e76-192">Another feature of serverless is micro-billing.</span></span> <span data-ttu-id="c9e76-193">Web 應用程式通常會裝載 Web API 端點。</span><span class="sxs-lookup"><span data-stu-id="c9e76-193">It's common for web applications to host Web API endpoints.</span></span> <span data-ttu-id="c9e76-194">在傳統裸機中，對於 IaaS 甚至是 PaaS 的實作，需要持續為要裝載 API 的資源付費。</span><span class="sxs-lookup"><span data-stu-id="c9e76-194">In traditional bare metal, IaaS and even PaaS implementations, the resources to host the APIs are paid for continuously.</span></span> <span data-ttu-id="c9e76-195">這表示即使未存取這些資源，您仍要付費才可裝載端點。</span><span class="sxs-lookup"><span data-stu-id="c9e76-195">That means you pay to host the endpoints even when they aren't being accessed.</span></span> <span data-ttu-id="c9e76-196">通常您會發現其中一個 API 的呼叫次數比其他 API 多，所以整個系統會為了支援常用的端點而有所調整。</span><span class="sxs-lookup"><span data-stu-id="c9e76-196">Often you'll find one API is called more than others, so the entire system is scaled based on supporting the popular endpoints.</span></span> <span data-ttu-id="c9e76-197">無伺服器可讓您個別調整每個端點，並依據使用量付費，所以當您未呼叫 API 時，就不會產生任何費用。</span><span class="sxs-lookup"><span data-stu-id="c9e76-197">Serverless enables you to scale each endpoint independently and pay for usage, so no costs are incurred when the APIs aren't being called.</span></span> <span data-ttu-id="c9e76-198">在許多情況下，移轉可大幅降低持續產生的費用，以支援端點。</span><span class="sxs-lookup"><span data-stu-id="c9e76-198">Migration may in many circumstances dramatically reduce the ongoing cost to support the endpoints.</span></span>

## <a name="what-this-guide-doesnt-cover"></a><span data-ttu-id="c9e76-199">本指南未說明的內容</span><span class="sxs-lookup"><span data-stu-id="c9e76-199">What this guide doesn't cover</span></span>

<span data-ttu-id="c9e76-200">本指南特別說明架構方法和設計模式，但不會深入說明 Azure Functions、[Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps)或其他無伺服器平台的實作詳細資料。</span><span class="sxs-lookup"><span data-stu-id="c9e76-200">This guide specifically emphasizes architecture approaches and design patterns and isn't a deep dive into the implementation details of Azure Functions, [Logic Apps](https://docs.microsoft.com/azure/logic-apps/logic-apps-what-are-logic-apps), or other serverless platforms.</span></span> <span data-ttu-id="c9e76-201">例如，本指南不會說明，Logic Apps 的進階工作流程或 Azure Functions 的功能，例如設定跨原始來源資源共用 (CORS)、套用自訂網域，或上傳 SSL 憑證。</span><span class="sxs-lookup"><span data-stu-id="c9e76-201">This guide doesn't cover, for example, advanced workflows with Logic Apps or features of Azure Functions such as configuring Cross-Origin Resource Sharing (CORS), applying custom domains, or uploading SSL certificates.</span></span> <span data-ttu-id="c9e76-202">這些詳細資料都可透過線上 [Azure Functions 文件](https://docs.microsoft.com/azure/azure-functions/functions-reference)取得。</span><span class="sxs-lookup"><span data-stu-id="c9e76-202">These details are available through the online [Azure Functions documentation](https://docs.microsoft.com/azure/azure-functions/functions-reference).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="c9e76-203">其他資源</span><span class="sxs-lookup"><span data-stu-id="c9e76-203">Additional resources</span></span>

* [<span data-ttu-id="c9e76-204">Azure 架構中心</span><span class="sxs-lookup"><span data-stu-id="c9e76-204">Azure Architecture center</span></span>](https://docs.microsoft.com/azure/architecture/)
* [<span data-ttu-id="c9e76-205">雲端應用程式的最佳做法</span><span class="sxs-lookup"><span data-stu-id="c9e76-205">Best practices for cloud applications</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design)

## <a name="who-should-use-the-guide"></a><span data-ttu-id="c9e76-206">誰應該使用本指南</span><span class="sxs-lookup"><span data-stu-id="c9e76-206">Who should use the guide</span></span>

<span data-ttu-id="c9e76-207">本指南專為想要以 .NET 建置可在內部部署或雲端使用無伺服器元件之企業應用程式的開發人員和解決方案架構設計人員所撰寫。</span><span class="sxs-lookup"><span data-stu-id="c9e76-207">This guide was written for developers and solution architects who want to build enterprise applications with .NET that may use serverless components either on premises or in the cloud.</span></span> <span data-ttu-id="c9e76-208">它適合具有下列興趣的開發人員、架構設計人員和技術決策者：</span><span class="sxs-lookup"><span data-stu-id="c9e76-208">It's useful to developers, architects, and technical decision makers interested in:</span></span>

* <span data-ttu-id="c9e76-209">了解無伺服器開發的優缺點</span><span class="sxs-lookup"><span data-stu-id="c9e76-209">Understanding the pros and cons of serverless development</span></span>
* <span data-ttu-id="c9e76-210">了解如何處理無伺服器架構</span><span class="sxs-lookup"><span data-stu-id="c9e76-210">Learning how to approach serverless architecture</span></span>
* <span data-ttu-id="c9e76-211">無伺服器應用程式的實作範例</span><span class="sxs-lookup"><span data-stu-id="c9e76-211">Example implementations of serverless apps</span></span>

## <a name="how-to-use-the-guide"></a><span data-ttu-id="c9e76-212">如何使用本指南</span><span class="sxs-lookup"><span data-stu-id="c9e76-212">How to use the guide</span></span>

<span data-ttu-id="c9e76-213">本指南的第一部分會比較數個不同的架構方法，來探究為何無伺服器是可行的選項。</span><span class="sxs-lookup"><span data-stu-id="c9e76-213">The first part of this guide examines why serverless is a viable option by comparing several different architecture approaches.</span></span> <span data-ttu-id="c9e76-214">因為軟體開發的所有層面都會受到架構決策所影響，所以其會同時探究技術和開發生命週期。</span><span class="sxs-lookup"><span data-stu-id="c9e76-214">It examines both the technology and development lifecycle, because all aspects of software development are impacted by architecture decisions.</span></span> <span data-ttu-id="c9e76-215">接著本指南會探究使用案例和設計模式，並包含使用 Azure Functions 的參考實作。</span><span class="sxs-lookup"><span data-stu-id="c9e76-215">The guide then examines use cases and design patterns and includes reference implementations using Azure Functions.</span></span> <span data-ttu-id="c9e76-216">每個章節都會包含其他資源以深入了解特定領域。</span><span class="sxs-lookup"><span data-stu-id="c9e76-216">Each section contains additional resources to learn more about a particular area.</span></span> <span data-ttu-id="c9e76-217">最後本指南會提供無伺服器實作的逐步解說與實際操作探索資源。</span><span class="sxs-lookup"><span data-stu-id="c9e76-217">The guide concludes with resources for walkthroughs and hands-on exploration of serverless implementation.</span></span>

## <a name="send-your-feedback"></a><span data-ttu-id="c9e76-218">傳送您的意見反應</span><span class="sxs-lookup"><span data-stu-id="c9e76-218">Send your feedback</span></span>

<span data-ttu-id="c9e76-219">本指南和相關範例會不斷改進，因此歡迎您提供意見反應！</span><span class="sxs-lookup"><span data-stu-id="c9e76-219">The guide and related samples are constantly evolving, so your feedback is welcomed!</span></span> <span data-ttu-id="c9e76-220">如果您想提出如何改進本指南意見，請使用 [GitHub 問題](https://github.com/dotnet/docs/issues)之任何頁面底部的意見反應區段。</span><span class="sxs-lookup"><span data-stu-id="c9e76-220">If you have comments about how this guide can be improved, use the feedback section at the bottom of any page built on [GitHub issues](https://github.com/dotnet/docs/issues).</span></span>

>[!div class="step-by-step"]
>[<span data-ttu-id="c9e76-221">下一步</span><span class="sxs-lookup"><span data-stu-id="c9e76-221">Next</span></span>](architecture-approaches.md)