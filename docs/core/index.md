---
title: .NET Core 指南
description: .NET Core 是 .NET 的模組化高性能實現，用於創建 Windows、Linux 和 macOS 應用。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 12/04/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 6d2ce5951fa01ca3945ce0e64aa58fbadc8ab5af
ms.sourcegitcommit: 34dc3c0d0d0a1cc418abff259d9daa8078d00b81
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/19/2020
ms.locfileid: "79546545"
---
# <a name="net-core-guide"></a><span data-ttu-id="d78ec-104">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="d78ec-104">.NET Core guide</span></span>

<span data-ttu-id="d78ec-105">[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺，由微軟和[GitHub](https://github.com/dotnet/core)上的 .NET 社區維護。</span><span class="sxs-lookup"><span data-stu-id="d78ec-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="d78ec-106">它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d78ec-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="d78ec-107">請參閱[關於 .NET Core](about.md)以深入了解 .NET Core，包括其特性、支援的語言與架構，亦即主要 API。</span><span class="sxs-lookup"><span data-stu-id="d78ec-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="d78ec-108">查看 [.NET Core 教學課程](tutorials/index.md) 以了解如何建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="d78ec-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="d78ec-109">只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="d78ec-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="d78ec-110">若要在您的瀏覽器中嘗試 .NET Core，請查看 [C# 中的數字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)線上教學課程。</span><span class="sxs-lookup"><span data-stu-id="d78ec-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="d78ec-111">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="d78ec-111">Download .NET Core</span></span>

<span data-ttu-id="d78ec-112">下載[.NET 核心 SDK，](https://dotnet.microsoft.com/download)在 Windows、macOS 或 Linux 電腦上嘗試 .NET 酷睿。</span><span class="sxs-lookup"><span data-stu-id="d78ec-112">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="d78ec-113">如果您更喜歡使用 Docker 容器，請訪問[.NET 核心 Docker 集線器 。](https://hub.docker.com/_/microsoft-dotnet-core/)</span><span class="sxs-lookup"><span data-stu-id="d78ec-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="d78ec-114">若您要尋找另一個 .NET Core 版本，所有 .NET Core 版本都可以在 [.NET Core 下載 ](https://dotnet.microsoft.com/download/dotnet-core)找到。</span><span class="sxs-lookup"><span data-stu-id="d78ec-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-31"></a><span data-ttu-id="d78ec-115">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="d78ec-115">.NET Core 3.1</span></span>

<span data-ttu-id="d78ec-116">最新版本是 .NET 核心 3.1。</span><span class="sxs-lookup"><span data-stu-id="d78ec-116">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="d78ec-117">3.1 包括對 .NET Core 3.0 的細微改進，但是.NET Core 3.1 是長期[支援的版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="d78ec-117">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="d78ec-118">有關 .NET Core 3.1 版本的詳細資訊，請參閱[.NET Core 3.1 中的新增功能](./whats-new/dotnet-core-3-1.md)。</span><span class="sxs-lookup"><span data-stu-id="d78ec-118">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="d78ec-119">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="d78ec-119">Create your first application</span></span>

<span data-ttu-id="d78ec-120">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="d78ec-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="d78ec-121">輸入以下`dotnet`命令以創建和運行 C# 應用程式：</span><span class="sxs-lookup"><span data-stu-id="d78ec-121">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="d78ec-122">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="d78ec-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="d78ec-123">支援</span><span class="sxs-lookup"><span data-stu-id="d78ec-123">Support</span></span>

<span data-ttu-id="d78ec-124">.NET Core 在 Windows、macOS 和 Linux 上[得到微軟的支援](https://dotnet.microsoft.com/platform/support/policy)。</span><span class="sxs-lookup"><span data-stu-id="d78ec-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="d78ec-125">每年都為它推出安全性與品質更新數次，通常是一個月一次。</span><span class="sxs-lookup"><span data-stu-id="d78ec-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="d78ec-126">.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。</span><span class="sxs-lookup"><span data-stu-id="d78ec-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="d78ec-127">[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。</span><span class="sxs-lookup"><span data-stu-id="d78ec-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="d78ec-128">Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。</span><span class="sxs-lookup"><span data-stu-id="d78ec-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="d78ec-129">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="d78ec-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
