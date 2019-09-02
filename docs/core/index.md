---
title: .NET Core 指南
description: .NET Core 是 .NET 的模組化、高效能實作，可用於建立 Windows、Linux 和 Mac 應用程式。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 08/01/2018
ms.custom: updateeachrelease
ms.openlocfilehash: db4daa8c78a181f0599c4c75ccd31f46ee278e63
ms.sourcegitcommit: 2d792961ed48f235cf413d6031576373c3050918
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/31/2019
ms.locfileid: "70202834"
---
# <a name="net-core-guide"></a><span data-ttu-id="01c53-104">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="01c53-104">.NET Core Guide</span></span>

<span data-ttu-id="01c53-105">[.NET Core](about.md) 是[開放原始碼](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)的一般用途開發平台，由 Microsoft 與 [GitHub](https://github.com/dotnet/core) 上的 .NET 社群共同維護。</span><span class="sxs-lookup"><span data-stu-id="01c53-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="01c53-106">它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01c53-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="01c53-107">請參閱[關於 .NET Core](about.md)以深入了解 .NET Core，包括其特性、支援的語言與架構，亦即主要 API。</span><span class="sxs-lookup"><span data-stu-id="01c53-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="01c53-108">查看 [.NET Core 教學課程](tutorials/index.md) 以了解如何建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01c53-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="01c53-109">只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="01c53-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="01c53-110">若要在您的瀏覽器中嘗試 .NET Core，請查看 [C# 中的數字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)線上教學課程。</span><span class="sxs-lookup"><span data-stu-id="01c53-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core-22"></a><span data-ttu-id="01c53-111">下載 .NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="01c53-111">Download .NET Core 2.2</span></span>

<span data-ttu-id="01c53-112">下載 [.NET Core  2.2 SDK](https://www.microsoft.com/net/download) 以在您的 Windows、macOS 或 Linux 電腦上嘗試 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="01c53-112">Download the [.NET Core  2.2 SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="01c53-113">若您想要使用 Docker 容器，請瀏覽 [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/)。</span><span class="sxs-lookup"><span data-stu-id="01c53-113">Visit [dotnet/core](https://hub.docker.com/_/microsoft-dotnet-core/) if you prefer to use Docker containers.</span></span>

<span data-ttu-id="01c53-114">若您要尋找另一個 .NET Core 版本，所有 .NET Core 版本都可以在 [.NET Core 下載 ](https://www.microsoft.com/net/download/archives)找到。</span><span class="sxs-lookup"><span data-stu-id="01c53-114">All .NET Core versions are available at [.NET Core Downloads](https://www.microsoft.com/net/download/archives) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-22"></a><span data-ttu-id="01c53-115">.NET Core 2.2</span><span class="sxs-lookup"><span data-stu-id="01c53-115">.NET Core 2.2</span></span>

<span data-ttu-id="01c53-116">最新版本是最新版本是 [.NET Core 2.2](whats-new/dotnet-core-2-2.md)。</span><span class="sxs-lookup"><span data-stu-id="01c53-116">The latest version is [.NET Core 2.2](whats-new/dotnet-core-2-2.md).</span></span> <span data-ttu-id="01c53-117">新功能包括：架構相機部署、啟動攔截程序、使用 Azure SQL 的 AAD 驗證，以及對 Windows ARM32 的支援。</span><span class="sxs-lookup"><span data-stu-id="01c53-117">New features include: framework-dependent deployments, startup hooks, AAD authentication with Azure SQL, and support for Windows ARM32.</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="01c53-118">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="01c53-118">Create your first application</span></span>

<span data-ttu-id="01c53-119">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="01c53-119">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="01c53-120">鍵入下列 `dotnet` 命令以建立並執行 C# 應用程式。</span><span class="sxs-lookup"><span data-stu-id="01c53-120">Type the following `dotnet` commands to create and run a C# application.</span></span>

```console
dotnet new console
dotnet run
```

<span data-ttu-id="01c53-121">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="01c53-121">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="01c53-122">支援</span><span class="sxs-lookup"><span data-stu-id="01c53-122">Support</span></span>

<span data-ttu-id="01c53-123">[Microsoft 在 Windows、macOS 與 Linux上](https://www.microsoft.com/net/support/policy) 都支援 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="01c53-123">.NET Core is [supported by Microsoft](https://www.microsoft.com/net/support/policy), on Windows, macOS and Linux.</span></span> <span data-ttu-id="01c53-124">每年都為它推出安全性與品質更新數次，通常是一個月一次。</span><span class="sxs-lookup"><span data-stu-id="01c53-124">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="01c53-125">.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。</span><span class="sxs-lookup"><span data-stu-id="01c53-125">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="01c53-126">[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。</span><span class="sxs-lookup"><span data-stu-id="01c53-126">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="01c53-127">Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。</span><span class="sxs-lookup"><span data-stu-id="01c53-127">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="01c53-128">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="01c53-128">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
