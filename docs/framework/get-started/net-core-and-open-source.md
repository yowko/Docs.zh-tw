---
title: .NET 的核心和開放原始碼
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
ms.openlocfilehash: 4d9d42304c58c631020d8b12bec5c038bc0c07ab
ms.sourcegitcommit: 2b3b2d684259463ddfc76ad680e5e09fdc1984d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2020
ms.locfileid: "80888237"
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="b4500-102">.NET Core 與開放原始碼</span><span class="sxs-lookup"><span data-stu-id="b4500-102">.NET Core and open source</span></span>

<span data-ttu-id="b4500-103">本文簡要概述了什麼是 .NET Core,並展示了如何找到更多資訊。</span><span class="sxs-lookup"><span data-stu-id="b4500-103">This article provides a brief overview of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="b4500-104">要尋找 .NET Core 的完整文件清單,請造[訪 .NET 核心指南](../../core/index.yml)。</span><span class="sxs-lookup"><span data-stu-id="b4500-104">To find the complete list of documentation for .NET Core, visit the [.NET Core guide](../../core/index.yml).</span></span>

## <a name="what-is-net-core"></a><span data-ttu-id="b4500-105">什麼是 .NET Core？</span><span class="sxs-lookup"><span data-stu-id="b4500-105">What is .NET Core?</span></span>  

<span data-ttu-id="b4500-106">.NET Core 是 .NET 標準的通用、模組化、跨平臺和開源實現。</span><span class="sxs-lookup"><span data-stu-id="b4500-106">.NET Core is a general purpose, modular, cross-platform, and open-source implementation of the .NET Standard.</span></span> <span data-ttu-id="b4500-107">它包含許多與 .NET 框架相同的 API(但 .NET Core 是一個較小的集),並且包括支援各種作業系統和晶片目標的運行時、框架、編譯器和工具元件。</span><span class="sxs-lookup"><span data-stu-id="b4500-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler, and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="b4500-108">.NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。</span><span class="sxs-lookup"><span data-stu-id="b4500-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="b4500-109">它可用於設備、雲和嵌入式/IoT 方案。</span><span class="sxs-lookup"><span data-stu-id="b4500-109">It can be used in device, cloud, and embedded/IoT scenarios.</span></span>  
  
<span data-ttu-id="b4500-110">要開始與 .NET Core, 訪問 .NET 教程[Hello World 在 10 分鐘內](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span><span class="sxs-lookup"><span data-stu-id="b4500-110">To get started with .NET Core, visit the .NET tutorial [Hello World in 10 minutes](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro).</span></span>  
  
<span data-ttu-id="b4500-111">.NET 核心的主要特點是:</span><span class="sxs-lookup"><span data-stu-id="b4500-111">The main characteristics of .NET Core are:</span></span>
  
- <span data-ttu-id="b4500-112">**跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。</span><span class="sxs-lookup"><span data-stu-id="b4500-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="b4500-113">它目前支援三個主要作業系統 (OS):Windows、Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="b4500-113">It currently supports three main operating systems (OS): Windows, Linux, and macOS.</span></span> <span data-ttu-id="b4500-114">您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="b4500-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="b4500-115">若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。</span><span class="sxs-lookup"><span data-stu-id="b4500-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
- <span data-ttu-id="b4500-116">**開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。</span><span class="sxs-lookup"><span data-stu-id="b4500-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](https://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span> <span data-ttu-id="b4500-117">作為一個開源專案,.NET Core 促進更加透明的開發過程和積極和參與的社區。</span><span class="sxs-lookup"><span data-stu-id="b4500-117">As an open-source project, .NET Core promotes a more transparent development process and an active and engaged community.</span></span>  
  
- <span data-ttu-id="b4500-118">**彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。</span><span class="sxs-lookup"><span data-stu-id="b4500-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="b4500-119">在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。</span><span class="sxs-lookup"><span data-stu-id="b4500-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span> <span data-ttu-id="b4500-120">使用自包含部署時,用於構建應用程式的.NET Core版本也會與應用和第三方依賴項一起部署,並可以與其他版本並行運行。</span><span class="sxs-lookup"><span data-stu-id="b4500-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side by side with other versions.</span></span> <span data-ttu-id="b4500-121">有關詳細資訊,請參閱[.NET 核心應用程式部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="b4500-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

- <span data-ttu-id="b4500-122">**模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。</span><span class="sxs-lookup"><span data-stu-id="b4500-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="b4500-123">.NET Core 不是包含大多數核心功能的大型程式集,而是作為更小、以功能為中心的包提供。</span><span class="sxs-lookup"><span data-stu-id="b4500-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller, feature-centric packages.</span></span> <span data-ttu-id="b4500-124">這種模組化為我們提供了一個更靈活的開發模式,並允許您優化你的應用,只包括您需要的 NuGet 包。</span><span class="sxs-lookup"><span data-stu-id="b4500-124">This modularity enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="b4500-125">應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。</span><span class="sxs-lookup"><span data-stu-id="b4500-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="b4500-126">.NET 核心平臺</span><span class="sxs-lookup"><span data-stu-id="b4500-126">The .NET Core platform</span></span>
  
<span data-ttu-id="b4500-127">.NET Core 平臺由多個元件組成,包括託管編譯器、運行時、基類庫和大量應用程式模型,如ASP.NET Core。</span><span class="sxs-lookup"><span data-stu-id="b4500-127">The .NET Core platform is made up of several components, including the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="b4500-128">您可以瞭解有關不同元件的更多內容,並透過存取以下[GitHub](https://github.com/)儲存函式庫進行參與:</span><span class="sxs-lookup"><span data-stu-id="b4500-128">You can learn more about the different components and get engaged by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
- [<span data-ttu-id="b4500-129">.NET 核心首頁</span><span class="sxs-lookup"><span data-stu-id="b4500-129">.NET Core home</span></span>](https://github.com/dotnet/core)  
  
- [<span data-ttu-id="b4500-130">執行時 - .NET 核心平台與執行時</span><span class="sxs-lookup"><span data-stu-id="b4500-130">Runtime - .NET Core platform and runtime</span></span>](https://github.com/dotnet/runtime)  
  
- [<span data-ttu-id="b4500-131">CLI - .NET Core 命令列工具</span><span class="sxs-lookup"><span data-stu-id="b4500-131">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
- [<span data-ttu-id="b4500-132">Roslyn - .NET 編譯器平台</span><span class="sxs-lookup"><span data-stu-id="b4500-132">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
- [<span data-ttu-id="b4500-133">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b4500-133">ASP.NET Core</span></span>](https://github.com/dotnet/aspnetcore)  
  
## <a name="see-also"></a><span data-ttu-id="b4500-134">另請參閱</span><span class="sxs-lookup"><span data-stu-id="b4500-134">See also</span></span>

- [<span data-ttu-id="b4500-135">.NET 教程 - 10 分鐘內的"你好世界"</span><span class="sxs-lookup"><span data-stu-id="b4500-135">.NET tutorial - Hello World in 10 minutes</span></span>](https://dotnet.microsoft.com/learn/dotnet/hello-world-tutorial/intro)
- [<span data-ttu-id="b4500-136">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="b4500-136">.NET Core guide</span></span>](../../core/index.yml)
- [<span data-ttu-id="b4500-137">ASP.NET核心文件</span><span class="sxs-lookup"><span data-stu-id="b4500-137">ASP.NET Core docs</span></span>](/aspnet/core/)
