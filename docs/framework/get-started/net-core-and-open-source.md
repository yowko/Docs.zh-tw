---
title: .NET 的核心和開放原始碼
ms.date: 03/30/2017
ms.assetid: e6bd4655-ce37-4003-8462-468a6fe2c40f
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 5eeef28f9a1d81ffa6328bfa5f2a8ed5295b47aa
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59163419"
---
# <a name="net-core-and-open-source"></a><span data-ttu-id="e41a5-102">.NET 的核心和開放原始碼</span><span class="sxs-lookup"><span data-stu-id="e41a5-102">.NET Core and Open-Source</span></span>
<span data-ttu-id="e41a5-103">本主題概要說明什麼是 .NET Core，並說明如何尋找更多資訊。</span><span class="sxs-lookup"><span data-stu-id="e41a5-103">This topic provides a brief overview  of what .NET Core is and shows how you can find more information.</span></span> <span data-ttu-id="e41a5-104">若要尋找 .NET Core 主題的完整清單，請瀏覽 [.NET Core 指南](../../core/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e41a5-104">To find the complete list of topics for .NET Core, visit the [.NET Core Guide](../../core/index.md).</span></span>
  
<a name="BKMK_WhatisNETCore"></a>   
## <a name="what-is-net-core"></a><span data-ttu-id="e41a5-105">什麼是 .NET Core？</span><span class="sxs-lookup"><span data-stu-id="e41a5-105">What is .NET Core?</span></span>  
 <span data-ttu-id="e41a5-106">.NET Core 是 .NET Standard 的一般用途、模組化、跨平台和開放原始碼實作。</span><span class="sxs-lookup"><span data-stu-id="e41a5-106">.NET Core is a general purpose, modular, cross-platform and open source implementation of the .NET Standard.</span></span> <span data-ttu-id="e41a5-107">它包含與 .NET Framework 相同的許多 API (但 .NET Core 是較小的集合)，並包含支援各種作業系統和晶片目標的執行階段、架構、編譯器和工具元件。</span><span class="sxs-lookup"><span data-stu-id="e41a5-107">It contains many of the same APIs as the .NET Framework (but .NET Core is a smaller set) and includes runtime, framework, compiler and tools components that support a variety of operating systems and chip targets.</span></span> <span data-ttu-id="e41a5-108">.NET Core 實作主要是由 ASP.NET Core 工作負載所驅動，但若需要及想要更新的實作，也會驅動此實作。</span><span class="sxs-lookup"><span data-stu-id="e41a5-108">The .NET Core implementation was primarily driven by the ASP.NET Core workloads but also by the need and desire to have a more modern implementation.</span></span> <span data-ttu-id="e41a5-109">它可用於裝置、雲端和內嵌/IoT 情節。</span><span class="sxs-lookup"><span data-stu-id="e41a5-109">It can be used in device, cloud and embedded/IoT scenarios.</span></span>  
  
 <span data-ttu-id="e41a5-110">若要開始使用 .NET Core，請前往 [.NET Core 首頁](https://www.microsoft.com/net/core)。</span><span class="sxs-lookup"><span data-stu-id="e41a5-110">To get started with .NET Core, please visit the [.NET Core homepage](https://www.microsoft.com/net/core).</span></span>  
  
 <span data-ttu-id="e41a5-111">.NET Core 的主要特性如下：</span><span class="sxs-lookup"><span data-stu-id="e41a5-111">Here are the main characteristics of .NET Core:</span></span>  
  
-   <span data-ttu-id="e41a5-112">**跨平台：**.NET Core 的主要功能是實作您所需要的應用程式功能，並不分平台地重複使用此程式碼。</span><span class="sxs-lookup"><span data-stu-id="e41a5-112">**Cross-platform:** .NET Core provides key functionality to implement the app features you need and reuse this code regardless of your platform target.</span></span> <span data-ttu-id="e41a5-113">它目前支援三個主要作業系統 (OS)：Windows、Linux 和 macOS。</span><span class="sxs-lookup"><span data-stu-id="e41a5-113">It currently supports three main operating systems (OS): Windows, Linux and macOS.</span></span> <span data-ttu-id="e41a5-114">您可以撰寫應用程式和程式庫，未經修改即可在支援的作業系統上執行。</span><span class="sxs-lookup"><span data-stu-id="e41a5-114">You can write apps and libraries that run unmodified across supported operating systems.</span></span> <span data-ttu-id="e41a5-115">若要查看支援的作業系統清單，請瀏覽 [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md) (.NET Core 藍圖)。</span><span class="sxs-lookup"><span data-stu-id="e41a5-115">To see the list of supported operating systems, visit [.NET Core roadmap](https://github.com/dotnet/core/blob/master/roadmap.md).</span></span>
  
-   <span data-ttu-id="e41a5-116">**開放原始碼︰**.NET Core 是 [.NET Foundation](https://www.dotnetfoundation.org/) 監管下之許多專案的其中一個，並且會在 [GitHub](https://github.com/) 上提供。</span><span class="sxs-lookup"><span data-stu-id="e41a5-116">**Open source:** .NET Core is one of the many projects under the stewardship of the [.NET Foundation](https://www.dotnetfoundation.org/) and is available on [GitHub](https://github.com/).</span></span>  <span data-ttu-id="e41a5-117">以 .NET Core 作為開放原始碼專案可促進更透明的開發程序，以及主動參與的社群。</span><span class="sxs-lookup"><span data-stu-id="e41a5-117">Having .NET Core as an open source project promotes a more transparent development process and promotes an active and engaged community.</span></span>  
  
-   <span data-ttu-id="e41a5-118">**彈性的部署︰** 部署應用程式的方式主要有兩種︰架構相依部署或獨立部署。</span><span class="sxs-lookup"><span data-stu-id="e41a5-118">**Flexible deployment:** there are two main ways to deploy your app: framework-dependent deployment or self-contained deployment.</span></span> <span data-ttu-id="e41a5-119">在架構相依部署中，只會安裝您的應用程式和協力廠商相依性，而且您的應用程式需要有 .NET Core 的全系統版本。</span><span class="sxs-lookup"><span data-stu-id="e41a5-119">With framework-dependent deployment, only your app and third-party dependencies are installed and your app depends on a system-wide version of .NET Core to be present.</span></span>  <span data-ttu-id="e41a5-120">在獨立部署中，用來建置應用程式的 .NET Core 版本也會隨應用程式和協力廠商相依性一起部署，而且可以與其他版本並存執行。</span><span class="sxs-lookup"><span data-stu-id="e41a5-120">With self-contained deployment, the .NET Core version used to build your application is also deployed along with your app and third-party dependencies and can run side-by-side with other versions.</span></span>    <span data-ttu-id="e41a5-121">如需詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e41a5-121">For more information, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>

-   <span data-ttu-id="e41a5-122">**模組化：**.NET Core 因為是透過 NuGet 以較小型的組件套件發行，所以稱為模組化版本。</span><span class="sxs-lookup"><span data-stu-id="e41a5-122">**Modular:** .NET Core is modular because it's released through NuGet in smaller assembly packages.</span></span> <span data-ttu-id="e41a5-123">不同於大型組件會包含大部分的核心功能，.NET Core 著眼於特定功能，會以較小型的套件提供。</span><span class="sxs-lookup"><span data-stu-id="e41a5-123">Rather than one large assembly that contains most of the core functionality, .NET Core is made available as smaller feature-centric packages.</span></span> <span data-ttu-id="e41a5-124">這讓我們有更靈活的開發模型，並可讓您最佳化應用程式，只包含所需的 NuGet 套件。</span><span class="sxs-lookup"><span data-stu-id="e41a5-124">This enables a more agile development model for us and allows you to optimize your app to include just the NuGet packages you need.</span></span> <span data-ttu-id="e41a5-125">應用程式介面區較小的優點包括更嚴密的安全性、減少維護工作、提升效能，以及降低依使用內容付費模型的成本。</span><span class="sxs-lookup"><span data-stu-id="e41a5-125">The benefits of a smaller app surface area include tighter security, reduced servicing, improved performance, and decreased costs in a pay-for-what-you-use model.</span></span>  
  
## <a name="the-net-core-platform"></a><span data-ttu-id="e41a5-126">.NET Core 平台</span><span class="sxs-lookup"><span data-stu-id="e41a5-126">The .NET Core Platform</span></span>  
 <span data-ttu-id="e41a5-127">.NET Core 平台是由幾個元件所組成，其中包含 Managed 編譯器、執行階段、基底類別庫，以及許多應用程式模型 (例如 ASP.NET Core)。</span><span class="sxs-lookup"><span data-stu-id="e41a5-127">The .NET Core platform is made of several components, which includes the managed compilers, the runtime, the base class libraries, and numerous application models, such as ASP.NET Core.</span></span> <span data-ttu-id="e41a5-128">您可以前往下列 [GitHub](https://github.com/) 存放庫，以深入了解並使用不同的元件：</span><span class="sxs-lookup"><span data-stu-id="e41a5-128">You can learn more about the different components and get engaged, by visiting the following [GitHub](https://github.com/) repos:</span></span>  
  
-   [<span data-ttu-id="e41a5-129">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e41a5-129">.NET Core</span></span>](https://github.com/dotnet/core)  
  
-   [<span data-ttu-id="e41a5-130">CoreFX - .NET Core 基本程式庫</span><span class="sxs-lookup"><span data-stu-id="e41a5-130">CoreFX - .NET Core foundational libraries</span></span>](https://github.com/dotnet/corefx)  
  
-   [<span data-ttu-id="e41a5-131">CoreCLR - .NET Core 執行階段</span><span class="sxs-lookup"><span data-stu-id="e41a5-131">CoreCLR - .NET Core runtime</span></span>](https://github.com/dotnet/coreclr)  
  
-   [<span data-ttu-id="e41a5-132">CLI - .NET Core 命令列工具</span><span class="sxs-lookup"><span data-stu-id="e41a5-132">CLI - .NET Core command-line tools</span></span>](https://github.com/dotnet/cli)  
  
-   [<span data-ttu-id="e41a5-133">Roslyn - .NET 編譯器平台</span><span class="sxs-lookup"><span data-stu-id="e41a5-133">Roslyn - .NET Compiler Platform</span></span>](https://github.com/dotnet/roslyn)  
  
-   [<span data-ttu-id="e41a5-134">ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="e41a5-134">ASP.NET Core</span></span>](https://github.com/aspnet/home)  
  
## <a name="see-also"></a><span data-ttu-id="e41a5-135">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e41a5-135">See also</span></span>

- [<span data-ttu-id="e41a5-136">.NET Core 首頁</span><span class="sxs-lookup"><span data-stu-id="e41a5-136">.NET Core homepage</span></span>](https://www.microsoft.com/net/core)
- [<span data-ttu-id="e41a5-137">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="e41a5-137">.NET Core Guide</span></span>](../../core/index.md)
- [<span data-ttu-id="e41a5-138">ASP.NET Core 文件</span><span class="sxs-lookup"><span data-stu-id="e41a5-138">ASP.NET Core Documentation</span></span>](/aspnet/core/)
