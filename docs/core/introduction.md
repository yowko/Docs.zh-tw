---
title: .NET Core 簡介和總覽
description: .NET Core 是適用于建立 Windows、Linux 和 macOS 應用程式之 .NET 的模組化高效能執行。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/26/2020
ms.custom: updateeachrelease
ms.openlocfilehash: 350fd50bee3403a05d1c19c9a692535613b17498
ms.sourcegitcommit: 27a15a55019f6b5f2733961738babe94aec0def3
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/15/2020
ms.locfileid: "90538272"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="34f63-104">.NET Core 簡介</span><span class="sxs-lookup"><span data-stu-id="34f63-104">Introduction to .NET Core</span></span>

<span data-ttu-id="34f63-105">[.Net Core](about.md) 是一個 [開放原始](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)碼的一般用途開發平臺。</span><span class="sxs-lookup"><span data-stu-id="34f63-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform.</span></span> <span data-ttu-id="34f63-106">您可以使用多種程式設計語言，為 x64、x86、ARM32 和 ARM64 處理器建立適用于 Windows、macOS 和 Linux 的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="34f63-106">You can create .NET Core apps for Windows, macOS, and Linux for x64, x86, ARM32, and ARM64 processors using multiple programming languages.</span></span> <span data-ttu-id="34f63-107">提供適用于 [雲端](/aspnet/core/)、 [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0)、 [用戶端 UI](../desktop-wpf/overview/index.md)和 [機器學習](../machine-learning/index.yml)的架構和 api。</span><span class="sxs-lookup"><span data-stu-id="34f63-107">Frameworks and APIs are provided for [cloud](/aspnet/core/), [IoT](/archive/msdn-magazine/2019/august/net-core-cross-platform-iot-programming-with-net-core-3-0), [client UI](../desktop-wpf/overview/index.md), and [machine learning](../machine-learning/index.yml).</span></span>

<span data-ttu-id="34f63-108">[下載 .NET Core SDK](https://dotnet.microsoft.com/download) ，以在您的電腦上嘗試 .net Core。</span><span class="sxs-lookup"><span data-stu-id="34f63-108">[Download the .NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your machine.</span></span> <span data-ttu-id="34f63-109">最新版本是 [.Net Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/)。</span><span class="sxs-lookup"><span data-stu-id="34f63-109">The latest version is [.NET Core 3.1](https://devblogs.microsoft.com/dotnet/announcing-net-core-3-1/).</span></span>

## <a name="download-net-core"></a><span data-ttu-id="34f63-110">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="34f63-110">Download .NET Core</span></span>

<span data-ttu-id="34f63-111">您可以透過下列方式取得 .NET Core：</span><span class="sxs-lookup"><span data-stu-id="34f63-111">You can get .NET Core in the following ways:</span></span>

* [<span data-ttu-id="34f63-112">適用于 Windows 和 macOS 的安裝程式</span><span class="sxs-lookup"><span data-stu-id="34f63-112">Installers for Windows and macOS</span></span>](https://dotnet.microsoft.com/download)
* [<span data-ttu-id="34f63-113">Linux 套件</span><span class="sxs-lookup"><span data-stu-id="34f63-113">Linux packages</span></span>](./install/linux.md)
* [<span data-ttu-id="34f63-114">Docker 容器</span><span class="sxs-lookup"><span data-stu-id="34f63-114">Docker containers</span></span>](https://hub.docker.com/_/microsoft-dotnet-core/)
* [<span data-ttu-id="34f63-115">Zips 和留下 tarball</span><span class="sxs-lookup"><span data-stu-id="34f63-115">Zips and tarballs</span></span>](https://dotnet.microsoft.com/download/dotnet-core/3.1)
* [<span data-ttu-id="34f63-116">安裝腳本</span><span class="sxs-lookup"><span data-stu-id="34f63-116">Install scripts</span></span>](https://dotnet.microsoft.com/download/dotnet-core/scripts)
* [<span data-ttu-id="34f63-117">版本資訊</span><span class="sxs-lookup"><span data-stu-id="34f63-117">Release notes</span></span>](https://github.com/dotnet/core/tree/master/release-notes)

## <a name="create-your-first-application"></a><span data-ttu-id="34f63-118">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="34f63-118">Create your first application</span></span>

<span data-ttu-id="34f63-119">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="34f63-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="34f63-120">使用下列命令來建立和執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="34f63-120">Use the following commands to create and run an application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="34f63-121">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="34f63-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="contribute"></a><span data-ttu-id="34f63-122">參與</span><span class="sxs-lookup"><span data-stu-id="34f63-122">Contribute</span></span>

<span data-ttu-id="34f63-123">.NET Core 是開放式平臺。</span><span class="sxs-lookup"><span data-stu-id="34f63-123">.NET Core is an open platform.</span></span> <span data-ttu-id="34f63-124">大家都歡迎參與。</span><span class="sxs-lookup"><span data-stu-id="34f63-124">Everyone is welcome to participate.</span></span>

* <span data-ttu-id="34f63-125">在 [開發人員社群](https://developercommunity.visualstudio.com/spaces/61/index.html)提出產品問題和問題。</span><span class="sxs-lookup"><span data-stu-id="34f63-125">File product issues and questions at [Developer Community](https://developercommunity.visualstudio.com/spaces/61/index.html).</span></span>
* <span data-ttu-id="34f63-126">您應該在其中一個專案存放庫（例如 [dotnet/runtime](https://github.com/dotnet/runtime)、 [dotnet/sdk](https://github.com/dotnet/sdk)、 [dotnet/rosyln](https://github.com/dotnet/roslyn)或 [aspnetcore](https://github.com/dotnet/aspnetcore)）上進行產品貢獻。</span><span class="sxs-lookup"><span data-stu-id="34f63-126">Product contributions should be made on one of the project repositories, such as [dotnet/runtime](https://github.com/dotnet/runtime), [dotnet/sdk](https://github.com/dotnet/sdk), [dotnet/rosyln](https://github.com/dotnet/roslyn), or [aspnetcore](https://github.com/dotnet/aspnetcore).</span></span> <span data-ttu-id="34f63-127">如需詳細資訊，請參閱 [.Net Core 存放庫](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md)。</span><span class="sxs-lookup"><span data-stu-id="34f63-127">For more information, see [.NET Core repos](https://github.com/dotnet/core/blob/master/Documentation/core-repos.md).</span></span>

## <a name="support"></a><span data-ttu-id="34f63-128">支援</span><span class="sxs-lookup"><span data-stu-id="34f63-128">Support</span></span>

<span data-ttu-id="34f63-129">Microsoft 在 Windows、macOS 和 Linux 上以及 Red Hat Enterprise Linux 上的 Red Hat 都支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="34f63-129">.NET Core is supported by Microsoft on Windows, macOS, and Linux and by Red Hat on Red Hat Enterprise Linux.</span></span>

## <a name="next-steps"></a><span data-ttu-id="34f63-130">後續步驟</span><span class="sxs-lookup"><span data-stu-id="34f63-130">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="34f63-131">.NET Core 教學課程</span><span class="sxs-lookup"><span data-stu-id="34f63-131">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="34f63-132">在您的瀏覽器中嘗試 .NET Core</span><span class="sxs-lookup"><span data-stu-id="34f63-132">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
