---
title: .NET 的核心和開放原始碼
description: 閱讀有關 .NET Core 的總覽，這是 .NET Standard 的一般用途、模組化、跨平臺和開放原始碼的執行。
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 08d30d047c25b3b6d681d72b46b81a0cb21f8e0a
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622753"
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="0e534-103">.NET Core 與開放原始碼</span><span class="sxs-lookup"><span data-stu-id="0e534-103">.NET Core and open source</span></span>

<span data-ttu-id="0e534-104">本文簡要介紹 .NET Core 的功能，並說明您可以如何尋找更多資訊。</span><span class="sxs-lookup"><span data-stu-id="0e534-104">This article provides a brief overview of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="0e534-105">若要尋找 .NET Core 檔的完整清單，請造訪[.Net core 指南](../../core/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="0e534-105">To find the complete list of documentation for .NET Core, visit the [.NET Core guide](../../core/index.yml).</span></span>

## <a name="what-is-net-core"></a><span data-ttu-id="0e534-106">什麼是 .NET Core？</span><span class="sxs-lookup"><span data-stu-id="0e534-106">What is .NET Core?</span></span>  

<span data-ttu-id="0e534-107">.NET Core 是 .NET Standard 的一般用途、模組化、跨平臺和開放原始碼的執行。</span><span class="sxs-lookup"><span data-stu-id="0e534-107">.NET Core is a general purpose, modular, cross-platform, and open-source implementation of the .NET Standard.</span></span> <span data-ttu-id="0e534-108">其中包含許多與 .NET Framework 相同的 Api （但 .NET Core 是較小的集合），並包含支援各種作業系統和晶片目標的執行時間、架構、編譯器和工具元件。</span><span class="sxs-lookup"><span data-stu-id="0e534-108">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler, and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="0e534-109">.NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。</span><span class="sxs-lookup"><span data-stu-id="0e534-109">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="0e534-110">它可用於裝置、雲端和內嵌/IoT 案例。</span><span class="sxs-lookup"><span data-stu-id="0e534-110">It can be used in device, cloud, and embedded/IoT scenarios.</span></span>  
  
<span data-ttu-id="0e534-111">若要開始使用 .NET Core，請[在10分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)流覽 .net 教學課程 Hello World。</span><span class="sxs-lookup"><span data-stu-id="0e534-111">To get started with .NET Core, visit the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span>  
  
<span data-ttu-id="0e534-112">.NET Core 的主要特性如下：</span><span class="sxs-lookup"><span data-stu-id="0e534-112">The main characteristics of .NET Core are:</span></span>
  
- <span data-ttu-id="0e534-113">**跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。</span><span class="sxs-lookup"><span data-stu-id="0e534-113">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="0e534-114">它目前支援三個主要作業系統（OS）： Windows、Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="0e534-114">It currently supports three main operating systems (OS): Windows, Linux, and macOS.</span></span> <span data-ttu-id="0e534-115">您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="0e534-115">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="0e534-116">若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。</span><span class="sxs-lookup"><span data-stu-id="0e534-116">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
- <span data-ttu-id="0e534-117">**開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。</span><span class="sxs-lookup"><span data-stu-id="0e534-117">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](https://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span> <span data-ttu-id="0e534-118">.NET Core 是開放原始碼專案，可提升更透明的開發流程，以及使用中和已參與的社區。</span><span class="sxs-lookup"><span data-stu-id="0e534-118">As an open-source project, .NET Core promotes a more transparent development process and an active and engaged community.</span></span>  
  
- <span data-ttu-id="0e534-119">**彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。</span><span class="sxs-lookup"><span data-stu-id="0e534-119">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="0e534-120">在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。</span><span class="sxs-lookup"><span data-stu-id="0e534-120">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span> <span data-ttu-id="0e534-121">透過獨立部署，用來建立應用程式的 .NET Core 版本也會隨您的應用程式和協力廠商相依性一起部署，而且可以與其他版本並存執行。</span><span class="sxs-lookup"><span data-stu-id="0e534-121">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side by side with other versions.</span></span> <span data-ttu-id="0e534-122">如需詳細資訊，請參閱[.Net Core 應用程式部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="0e534-122">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

- <span data-ttu-id="0e534-123">**模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。</span><span class="sxs-lookup"><span data-stu-id="0e534-123">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="0e534-124">.NET Core 是以較小的功能中心套件提供，而不是一個包含大部分核心功能的大型元件。</span><span class="sxs-lookup"><span data-stu-id="0e534-124">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller, feature-centric packages.</span></span> <span data-ttu-id="0e534-125">此模組化可為我們提供更靈活的開發模型，並可讓您將應用程式優化，使其只包含所需的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="0e534-125">This modularity enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="0e534-126">應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。</span><span class="sxs-lookup"><span data-stu-id="0e534-126">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="0e534-127">.NET Core 平臺</span><span class="sxs-lookup"><span data-stu-id="0e534-127">The .NET Core platform</span></span>
  
<span data-ttu-id="0e534-128">.NET Core 平臺是由數個元件所組成，包括 managed 編譯器、執行時間、基類庫，以及許多應用程式模型（例如 ASP.NET Core）。</span><span class="sxs-lookup"><span data-stu-id="0e534-128">The .NET Core platform is made up of several components, including the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="0e534-129">您可以造訪下列[GitHub](https://github.com/)存放庫，以深入瞭解不同的元件並取得參與：</span><span class="sxs-lookup"><span data-stu-id="0e534-129">You can learn more about the different components and get engaged by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
- [<span data-ttu-id="0e534-130">.NET Core 首頁</span><span class="sxs-lookup"><span data-stu-id="0e534-130">.NET Core home</span></span>](https://github.com/dotnet/core)  
  
- [<span data-ttu-id="0e534-131">執行時間-.NET Core 平臺和執行時間</span><span class="sxs-lookup"><span data-stu-id="0e534-131">Runtime - .NET Core platform and runtime</span></span>](https://github.com/dotnet/runtime)  
  
- [<span data-ttu-id="0e534-132">CLI - .NET Core 命令列工具</span><span class="sxs-lookup"><span data-stu-id="0e534-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
- [<span data-ttu-id="0e534-133">Roslyn - .NET 編譯器平台</span><span class="sxs-lookup"><span data-stu-id="0e534-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
- [<span data-ttu-id="0e534-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="0e534-134">ASP.NET Core</span></span>](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a><span data-ttu-id="0e534-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="0e534-135">See also</span></span>

- [<span data-ttu-id="0e534-136">.NET 教學課程-10 分鐘內 Hello World</span><span class="sxs-lookup"><span data-stu-id="0e534-136">.NET tutorial - Hello World in 10 minutes</span></span>](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [<span data-ttu-id="0e534-137">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="0e534-137">.NET Core guide</span></span>](../../core/index.yml)
- [<span data-ttu-id="0e534-138">ASP.NET Core 檔</span><span class="sxs-lookup"><span data-stu-id="0e534-138">ASP.NET Core docs</span></span>](/aspnet/core/)
