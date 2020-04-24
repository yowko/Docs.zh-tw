---
title: .NET 核心簡介和概述
description: .NET Core 是 .NET 的模組化高性能實現,用於創建 Windows、Linux 和 macOS 應用。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: f99b446bbd38b2b814c13afa13ab34cd5c9aa086
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/20/2020
ms.locfileid: "81645529"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="89c5f-104">.NET Core 簡介</span><span class="sxs-lookup"><span data-stu-id="89c5f-104">Introduction to .NET Core</span></span>

<span data-ttu-id="89c5f-105">[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺。</span><span class="sxs-lookup"><span data-stu-id="89c5f-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="89c5f-106">您可以使用多種程式設計語言為 X64、x86、ARM32 和 ARM64 處理器創建 .NET 核心應用。</span><span class="sxs-lookup"><span data-stu-id="89c5f-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="89c5f-107">為[雲端](/aspnet/core/)、[物聯網](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、[用戶端 UI](../desktop-wpf/overview/index.md)和[機器學習](/dotnet/machine-learning/)提供了框架和 API。</span><span class="sxs-lookup"><span data-stu-id="89c5f-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](/dotnet/machine-learning/).</span></span>

<span data-ttu-id="89c5f-108">[下載 .NET 核心 SDK,](https://dotnet.microsoft.com/download)在電腦上嘗試 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="89c5f-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="89c5f-109">最新版本是[.NET 核心 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="89c5f-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="89c5f-110">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="89c5f-110">Download .NET Core</span></span>

<span data-ttu-id="89c5f-111">您可以透過以下方式取得 .NET Core:</span><span class="sxs-lookup"><span data-stu-id="89c5f-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="89c5f-112">適用於 Windows 和 macOS 安裝程式</span><span class="sxs-lookup"><span data-stu-id="89c5f-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="89c5f-113">Linux 套件</span><span class="sxs-lookup"><span data-stu-id="89c5f-113">Linux packages</span></span>](https://docs.microsoft.com/dotnet/core/install/linux-package-managers)
* [<span data-ttu-id="89c5f-114">Docker 容器</span><span class="sxs-lookup"><span data-stu-id="89c5f-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="89c5f-115">拉鍊和焦油球</span><span class="sxs-lookup"><span data-stu-id="89c5f-115">Zips and tar balls</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="89c5f-116">安裝文稿</span><span class="sxs-lookup"><span data-stu-id="89c5f-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="89c5f-117">版本資訊</span><span class="sxs-lookup"><span data-stu-id="89c5f-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="89c5f-118">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="89c5f-118">Create your first application</span></span>

<span data-ttu-id="89c5f-119">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="89c5f-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="89c5f-120">使用以下指令建立與執行應用程式:</span><span class="sxs-lookup"><span data-stu-id="89c5f-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="89c5f-121">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="89c5f-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="89c5f-122">參與</span><span class="sxs-lookup"><span data-stu-id="89c5f-122">Contribute</span></span>

<span data-ttu-id="89c5f-123">.NET 核心是一個開放的平臺。</span><span class="sxs-lookup"><span data-stu-id="89c5f-123">.NET Core is an open platform.</span></span> <span data-ttu-id="89c5f-124">歡迎大家參加。</span><span class="sxs-lookup"><span data-stu-id="89c5f-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="89c5f-125">在[開發人員社區](https://developercommunity.visualstudio.com/spaces/61/index.html)中歸檔產品問題和問題。</span><span class="sxs-lookup"><span data-stu-id="89c5f-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="89c5f-126">應在其中一個項目儲存函式庫上進行產品貢獻,例如[dotnet/執行時](https://github.com/dotnet/runtime),[點網 / sdk、 dotnet/ rosyln](https://github.com/dotnet/sdk)或[aspnetcore](https://github.com/dotnet/aspnetcore)。 [dotnet/rosyln](https://github.com/dotnet/roslyn)</span><span class="sxs-lookup"><span data-stu-id="89c5f-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="89c5f-127">有關詳細資訊,請參閱[.NET 核心儲存庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="89c5f-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="89c5f-128">支援</span><span class="sxs-lookup"><span data-stu-id="89c5f-128">Support</span></span>

<span data-ttu-id="89c5f-129">.NET Core 在 Windows、macOS 和 Linux 上得到 Microsoft 的支援,紅帽企業 Linux 上支援紅帽。</span><span class="sxs-lookup"><span data-stu-id="89c5f-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="89c5f-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="89c5f-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="89c5f-131">.NET 核心教程</span><span class="sxs-lookup"><span data-stu-id="89c5f-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="89c5f-132">在瀏覽器中試用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="89c5f-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
