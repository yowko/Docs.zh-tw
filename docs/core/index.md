---
title: .NET Core 指南
description: .NET Core 是適用于建立 Windows、Linux 和 macOS 應用程式的模組化、高效能的 .NET 執行。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 3db98d21a7cdc80d8a98b23782a81ffa37520937
ms.sourcegitcommit: 9a97c76e141333394676bc5d264c6624b6f45bcf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/08/2020
ms.locfileid: "75740754"
---
# <a name="net-core-guide"></a><span data-ttu-id="1b929-104">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="1b929-104">.NET Core guide</span></span>

<span data-ttu-id="1b929-105">[.NET Core](about.md) 是[開放原始碼](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的一般用途開發平台，由 Microsoft 與 [GitHub](https://github.com/dotnet/core) 上的 .NET 社群共同維護。</span><span class="sxs-lookup"><span data-stu-id="1b929-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="1b929-106">它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b929-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="1b929-107">請參閱[關於 .NET Core](about.md)以深入了解 .NET Core，包括其特性、支援的語言與架構，亦即主要 API。</span><span class="sxs-lookup"><span data-stu-id="1b929-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="1b929-108">查看 [.NET Core 教學課程](tutorials/index.md) 以了解如何建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b929-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="1b929-109">只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="1b929-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="1b929-110">若要在您的瀏覽器中嘗試 .NET Core，請查看 [C# 中的數字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)線上教學課程。</span><span class="sxs-lookup"><span data-stu-id="1b929-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="1b929-111">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="1b929-111">Download .NET Core</span></span>

<span data-ttu-id="1b929-112">下載[.NET Core SDK](https://www.microsoft.com/net/download) ，在您的 Windows、MacOS 或 Linux 電腦上嘗試 .net Core。</span><span class="sxs-lookup"><span data-stu-id="1b929-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="1b929-113">如果您想要使用 Docker 容器，請造訪[.Net Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/)。</span><span class="sxs-lookup"><span data-stu-id="1b929-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="1b929-114">若您要尋找另一個 .NET Core 版本，所有 .NET Core 版本都可以在 [.NET Core 下載 ](https://dotnet.microsoft.com/download/dotnet-core)找到。</span><span class="sxs-lookup"><span data-stu-id="1b929-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="1b929-115">.NET Core 3.1</span><span class="sxs-lookup"><span data-stu-id="1b929-115">.NET Core 3.1</span></span>

<span data-ttu-id="1b929-116">最新版本是 .NET Core 3.1。</span><span class="sxs-lookup"><span data-stu-id="1b929-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="1b929-117">3.1 包含 .NET Core 3.0 的次要改良功能，但是 .NET Core 3.1 是[長期支援的版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="1b929-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="1b929-118">如需 .NET Core 3.1 版本的詳細資訊，請參閱[.Net core 3.1 的新功能](./whats-new/dotnet-core-3-1.md)。</span><span class="sxs-lookup"><span data-stu-id="1b929-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="1b929-119">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="1b929-119">Create your first application</span></span>

<span data-ttu-id="1b929-120">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="1b929-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="1b929-121">輸入下列 `dotnet` 命令來建立和執行C#應用程式：</span><span class="sxs-lookup"><span data-stu-id="1b929-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="1b929-122">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="1b929-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="1b929-123">支援</span><span class="sxs-lookup"><span data-stu-id="1b929-123">Support</span></span>

<span data-ttu-id="1b929-124">Microsoft、Windows、macOS 和 Linux 上都[支援](https://dotnet.microsoft.com/platform/support/policy).net Core。</span><span class="sxs-lookup"><span data-stu-id="1b929-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="1b929-125">每年都為它推出安全性與品質更新數次，通常是一個月一次。</span><span class="sxs-lookup"><span data-stu-id="1b929-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="1b929-126">.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。</span><span class="sxs-lookup"><span data-stu-id="1b929-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="1b929-127">[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。</span><span class="sxs-lookup"><span data-stu-id="1b929-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="1b929-128">Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。</span><span class="sxs-lookup"><span data-stu-id="1b929-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="1b929-129">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="1b929-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
