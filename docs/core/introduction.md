---
title: .NET Core 簡介和總覽
description: .NET Core 是適用于建立 Windows、Linux 和 macOS 應用程式的模組化、高效能的 .NET 執行。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: b28ad965e54680e2e1134c389266741ade28084f
ms.sourcegitcommit: 67cf756b033c6173a1bbd1cbd5aef1fccac99e34
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 07/10/2020
ms.locfileid: "86226578"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="9d511-104">.NET Core 簡介</span><span class="sxs-lookup"><span data-stu-id="9d511-104">Introduction to .NET Core</span></span>

<span data-ttu-id="9d511-105">[.Net Core](about.md)是一個[開放原始](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)碼的一般用途開發平臺。</span><span class="sxs-lookup"><span data-stu-id="9d511-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="9d511-106">您可以使用多種程式設計語言，為 x64、x86、ARM32 和 ARM64 處理器建立適用于 Windows、macOS 和 Linux 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9d511-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="9d511-107">針對[雲端](/aspnet/core/)、 [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](../desktop-wpf/overview/index.md)和[機器學習](/dotnet/machine-learning/)服務提供架構和 api。</span><span class="sxs-lookup"><span data-stu-id="9d511-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="9d511-108">[下載 .NET Core SDK](https://dotnet.microsoft.com/download)以在您的電腦上試用 .net Core。</span><span class="sxs-lookup"><span data-stu-id="9d511-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="9d511-109">最新版本是[.Net Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="9d511-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="9d511-110">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d511-110">Download .NET Core</span></span>

<span data-ttu-id="9d511-111">您可以透過下列方式取得 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="9d511-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="9d511-112">Windows 和 macOS 的安裝程式</span><span class="sxs-lookup"><span data-stu-id="9d511-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="9d511-113">Linux 套件</span><span class="sxs-lookup"><span data-stu-id="9d511-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="9d511-114">Docker 容器</span><span class="sxs-lookup"><span data-stu-id="9d511-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="9d511-115">Zips 和留下 tarball</span><span class="sxs-lookup"><span data-stu-id="9d511-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="9d511-116">安裝腳本</span><span class="sxs-lookup"><span data-stu-id="9d511-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="9d511-117">版本資訊</span><span class="sxs-lookup"><span data-stu-id="9d511-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="9d511-118">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="9d511-118">Create your first application</span></span>

<span data-ttu-id="9d511-119">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="9d511-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="9d511-120">使用下列命令來建立和執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="9d511-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="9d511-121">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9d511-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="9d511-122">參與</span><span class="sxs-lookup"><span data-stu-id="9d511-122">Contribute</span></span>

<span data-ttu-id="9d511-123">.NET Core 是一個開放式平臺。</span><span class="sxs-lookup"><span data-stu-id="9d511-123">.NET Core is an open platform.</span></span> <span data-ttu-id="9d511-124">大家都歡迎參加。</span><span class="sxs-lookup"><span data-stu-id="9d511-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="9d511-125">在[開發人員的社區](https://developercommunity.visualstudio.com/spaces/61/index.html)提出產品問題和問題。</span><span class="sxs-lookup"><span data-stu-id="9d511-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="9d511-126">產品貢獻應在其中一個專案存放庫上進行，例如[dotnet/runtime](https://github.com/dotnet/runtime)、 [dotnet/sdk](https://github.com/dotnet/sdk)、 [dotnet/rosyln](https://github.com/dotnet/roslyn)或[aspnetcore](https://github.com/dotnet/aspnetcore)。</span><span class="sxs-lookup"><span data-stu-id="9d511-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="9d511-127">如需詳細資訊，請參閱[.Net Core 存放庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="9d511-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="9d511-128">支援</span><span class="sxs-lookup"><span data-stu-id="9d511-128">Support</span></span>

<span data-ttu-id="9d511-129">Windows、macOS 和 Linux 上的 Microsoft 以及 Red Hat Enterprise Linux 上的 Red Hat 都支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="9d511-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="9d511-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="9d511-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d511-131">.NET Core 教學課程</span><span class="sxs-lookup"><span data-stu-id="9d511-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="9d511-132">在您的瀏覽器中嘗試 .NET Core</span><span class="sxs-lookup"><span data-stu-id="9d511-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
