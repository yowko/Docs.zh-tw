---
title: .NET 的核心和開放原始碼
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: b5aa42d0460d743bffe8f17a2603773c03c09ce0
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/15/2020
ms.locfileid: "79181615"
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="d7c4c-102">.NET 核心和開源</span><span class="sxs-lookup"><span data-stu-id="d7c4c-102">.NET Core and open source</span></span>

<span data-ttu-id="d7c4c-103">本文簡要概述了什麼是 .NET Core，並展示了如何找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-103">This article provides a brief overview of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="d7c4c-104">要查找 .NET Core 的完整文檔清單，請訪問[.NET 核心指南](../../core/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-104">To find the complete list of documentation for .NET Core, visit the [.NET Core guide](../../core/index.md).</span></span>

## <a name="what-is-net-core"></a><span data-ttu-id="d7c4c-105">什麼是 .NET Core？</span><span class="sxs-lookup"><span data-stu-id="d7c4c-105">What is .NET Core?</span></span>  

<span data-ttu-id="d7c4c-106">.NET Core 是 .NET Standard 的一般用途、模組化、跨平台和開放原始碼實作。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-106">.NET Core is a general purpose, modular, cross-platform and open source implementation of the .NET Standard.</span></span> <span data-ttu-id="d7c4c-107">它包含與 .NET Framework 相同的許多 API (但 .NET Core 是較小的集合)，並包含支援各種作業系統和晶片目標的執行階段、架構、編譯器和工具元件。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="d7c4c-108">.NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="d7c4c-109">它可用於裝置、雲端和內嵌/IoT 情節。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-109">It can be used in device, cloud and embedded/IoT scenarios.</span></span>  
  
<span data-ttu-id="d7c4c-110">要開始與 .NET Core， 訪問 .NET 教程[Hello World 在 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span><span class="sxs-lookup"><span data-stu-id="d7c4c-110">To get started with .NET Core, visit the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span>  
  
<span data-ttu-id="d7c4c-111">.NET 核心的主要特點是：</span><span class="sxs-lookup"><span data-stu-id="d7c4c-111">The main characteristics of .NET Core are:</span></span>
  
- <span data-ttu-id="d7c4c-112">**跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="d7c4c-113">它目前支援三個主要作業系統 (OS)：Windows、Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-113">It currently supports three main operating systems (OS): Windows, Linux and macOS.</span></span> <span data-ttu-id="d7c4c-114">您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="d7c4c-115">若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
- <span data-ttu-id="d7c4c-116">**開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](https://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span>  <span data-ttu-id="d7c4c-117">以 .NET Core 作為開放原始碼專案可促進更透明的開發程序，以及主動參與的社群。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-117">Having .NET Core as an open source project promotes a more transparent development process and promotes an active and engaged community.</span></span>  
  
- <span data-ttu-id="d7c4c-118">**彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="d7c4c-119">在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span>  <span data-ttu-id="d7c4c-120">在獨立部署中，用來建置應用程式的 .NET Core 版本也會隨應用程式和協力廠商相依性一起部署，而且可以與其他版本並存執行。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side-by-side with other versions.</span></span>    <span data-ttu-id="d7c4c-121">有關詳細資訊，請參閱[.NET 核心應用程式部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

- <span data-ttu-id="d7c4c-122">**模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="d7c4c-123">不同於大型組件會包含大部分的核心功能，.NET Core 著眼於特定功能，會以較小型的套件提供。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller feature-centric packages.</span></span> <span data-ttu-id="d7c4c-124">這讓我們有更靈活的開發模型，並可讓您最佳化應用程式，只包含所需的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-124">This enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="d7c4c-125">應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="d7c4c-126">.NET 核心平臺</span><span class="sxs-lookup"><span data-stu-id="d7c4c-126">The .NET Core platform</span></span>
  
<span data-ttu-id="d7c4c-127">.NET Core 平臺由多個元件組成，包括託管編譯器、運行時、基類庫和大量應用程式模型，如ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="d7c4c-127">The .NET Core platform is made up of several components, including the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="d7c4c-128">您可以瞭解有關不同元件的更多內容，並通過訪問以下[GitHub](https://github.com/)存儲庫進行參與：</span><span class="sxs-lookup"><span data-stu-id="d7c4c-128">You can learn more about the different components and get engaged by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
- [<span data-ttu-id="d7c4c-129">.NET 核心主頁</span><span class="sxs-lookup"><span data-stu-id="d7c4c-129">.NET Core home</span></span>](https://github.com/dotnet/core)  
  
- [<span data-ttu-id="d7c4c-130">運行時 - .NET 核心平臺和運行時</span><span class="sxs-lookup"><span data-stu-id="d7c4c-130">Runtime - .NET Core platform and runtime</span></span>](https://github.com/dotnet/runtime)  
  
- [<span data-ttu-id="d7c4c-131">CLI - .NET Core 命令列工具</span><span class="sxs-lookup"><span data-stu-id="d7c4c-131">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
- [<span data-ttu-id="d7c4c-132">Roslyn - .NET 編譯器平台</span><span class="sxs-lookup"><span data-stu-id="d7c4c-132">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
- [<span data-ttu-id="d7c4c-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="d7c4c-133">ASP.NET Core</span></span>](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a><span data-ttu-id="d7c4c-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="d7c4c-134">See also</span></span>

- [<span data-ttu-id="d7c4c-135">.NET 教程 - 10 分鐘內的"你好世界"</span><span class="sxs-lookup"><span data-stu-id="d7c4c-135">.NET tutorial - Hello World in 10 minutes</span></span>](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [<span data-ttu-id="d7c4c-136">.NET 核心指南</span><span class="sxs-lookup"><span data-stu-id="d7c4c-136">.NET Core guide</span></span>](../../core/index.md)
- [<span data-ttu-id="d7c4c-137">ASP.NET核心文檔</span><span class="sxs-lookup"><span data-stu-id="d7c4c-137">ASP.NET Core docs</span></span>](/aspnet/core/)
