---
title: .NET 核心簡介和概述
description: .NET Core 是 .NET 的模組化高性能實現，用於創建 Windows、Linux 和 macOS 應用。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: a20cdda5cbd366d04e7ee9e8df3d1b15d10c1f4a
ms.sourcegitcommit: a9b8945630426a575ab0a332e568edc807666d1b
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/30/2020
ms.locfileid: "80391157"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="561e6-104">.NET Core 簡介</span><span class="sxs-lookup"><span data-stu-id="561e6-104">Introduction to .NET Core</span></span>

<span data-ttu-id="561e6-105">[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺。</span><span class="sxs-lookup"><span data-stu-id="561e6-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="561e6-106">您可以使用多種程式設計語言為 X64、x86、ARM32 和 ARM64 處理器創建 .NET 核心應用。</span><span class="sxs-lookup"><span data-stu-id="561e6-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="561e6-107">為[雲](/aspnet/core/)、[物聯網](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](/dotnet/desktop-wpf/overview/index)和[機器學習](/dotnet/machine-learning/)提供了框架和 API。</span><span class="sxs-lookup"><span data-stu-id="561e6-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](/dotnet/desktop-wpf/overview/index), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="561e6-108">[下載 .NET 核心 SDK，](https://dotnet.microsoft.com/download)在電腦上嘗試 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="561e6-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="561e6-109">最新版本是[.NET 核心 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="561e6-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="561e6-110">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="561e6-110">Download .NET Core</span></span>

<span data-ttu-id="561e6-111">您可以通過以下方式獲取 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="561e6-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="561e6-112">適用于 Windows 和 macOS 的安裝程式</span><span class="sxs-lookup"><span data-stu-id="561e6-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="561e6-113">Linux 套件</span><span class="sxs-lookup"><span data-stu-id="561e6-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="561e6-114">Docker 容器</span><span class="sxs-lookup"><span data-stu-id="561e6-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="561e6-115">拉鍊和焦油球</span><span class="sxs-lookup"><span data-stu-id="561e6-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="561e6-116">安裝腳本</span><span class="sxs-lookup"><span data-stu-id="561e6-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="561e6-117">版本資訊</span><span class="sxs-lookup"><span data-stu-id="561e6-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="561e6-118">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="561e6-118">Create your first application</span></span>

<span data-ttu-id="561e6-119">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="561e6-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="561e6-120">使用以下命令創建和運行應用程式：</span><span class="sxs-lookup"><span data-stu-id="561e6-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="561e6-121">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="561e6-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="561e6-122">參與</span><span class="sxs-lookup"><span data-stu-id="561e6-122">Contribute</span></span>

<span data-ttu-id="561e6-123">.NET 核心是一個開放的平臺。</span><span class="sxs-lookup"><span data-stu-id="561e6-123">.NET Core is an open platform.</span></span> <span data-ttu-id="561e6-124">歡迎大家參加。</span><span class="sxs-lookup"><span data-stu-id="561e6-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="561e6-125">在[開發人員社區](https://developercommunity.visualstudio.com/spaces/61/index.html)中歸檔產品問題和問題。</span><span class="sxs-lookup"><span data-stu-id="561e6-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="561e6-126">應在其中一個專案存儲庫上進行產品貢獻，例如[dotnet/運行時](https://github.com/dotnet/runtime)、[點網/sdk、dotnet/rosyln](https://github.com/dotnet/sdk)或[aspnetcore](https://github.com/dotnet/aspnetcore)。 [dotnet/rosyln](https://github.com/dotnet/roslyn)</span><span class="sxs-lookup"><span data-stu-id="561e6-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="561e6-127">有關詳細資訊，請參閱[.NET 核心存儲庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="561e6-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="561e6-128">支援</span><span class="sxs-lookup"><span data-stu-id="561e6-128">Support</span></span>

<span data-ttu-id="561e6-129">.NET Core 在 Windows、macOS 和 Linux 上得到 Microsoft 的支援，紅帽企業 Linux 上支援紅帽。</span><span class="sxs-lookup"><span data-stu-id="561e6-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="561e6-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="561e6-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="561e6-131">.NET 核心教程</span><span class="sxs-lookup"><span data-stu-id="561e6-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="561e6-132">在瀏覽器中試用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="561e6-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
