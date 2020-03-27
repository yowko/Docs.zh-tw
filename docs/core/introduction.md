---
title: .NET 核心簡介和概述
description: .NET Core 是 .NET 的模組化高性能實現，用於創建 Windows、Linux 和 macOS 應用。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 03/25/2020
ms.custom: updateeachrelease
ms.openlocfilehash: edd3864d3c3c5c0e9fd8c26ee806ffc9e100423d
ms.sourcegitcommit: 59e36e65ac81cdd094a5a84617625b2a0ff3506e
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/27/2020
ms.locfileid: "80351698"
---
# <a name="introduction-to-net-core"></a><span data-ttu-id="51d1c-104">.NET 核心簡介</span><span class="sxs-lookup"><span data-stu-id="51d1c-104">Introduction to .NET Core</span></span>

<span data-ttu-id="51d1c-105">[.NET Core](about.md)是一個[開源](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT)的通用開發平臺，由微軟和[GitHub](https://github.com/dotnet/core)上的 .NET 社區維護。</span><span class="sxs-lookup"><span data-stu-id="51d1c-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/runtime/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="51d1c-106">它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="51d1c-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="51d1c-107">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="51d1c-107">Download .NET Core</span></span>

<span data-ttu-id="51d1c-108">下載[.NET 核心 SDK，](https://dotnet.microsoft.com/download)在 Windows、macOS 或 Linux 電腦上嘗試 .NET 酷睿。</span><span class="sxs-lookup"><span data-stu-id="51d1c-108">Download the [.NET Core SDK](https://dotnet.microsoft.com/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="51d1c-109">如果您更喜歡使用 Docker 容器，請訪問[.NET 核心 Docker 集線器 。](https://hub.docker.com/_/microsoft-dotnet-core/)</span><span class="sxs-lookup"><span data-stu-id="51d1c-109">If you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

## <a name="net-core-31"></a><span data-ttu-id="51d1c-110">.NET 核心 3.1</span><span class="sxs-lookup"><span data-stu-id="51d1c-110">.NET Core 3.1</span></span>

<span data-ttu-id="51d1c-111">最新版本是 .NET 核心 3.1。</span><span class="sxs-lookup"><span data-stu-id="51d1c-111">The latest version is .NET Core 3.1.</span></span> <span data-ttu-id="51d1c-112">3.1 包括對 .NET Core 3.0 的細微改進，但是.NET Core 3.1 是長期[支援的版本](https://dotnet.microsoft.com/platform/support/policy/dotnet-core)。</span><span class="sxs-lookup"><span data-stu-id="51d1c-112">3.1 includes minor improvements over .NET Core 3.0, however, .NET Core 3.1 is a [long-term supported release](https://dotnet.microsoft.com/platform/support/policy/dotnet-core).</span></span> <span data-ttu-id="51d1c-113">有關 .NET Core 3.1 版本的詳細資訊，請參閱[.NET Core 3.1 中的新增功能](./whats-new/dotnet-core-3-1.md)。</span><span class="sxs-lookup"><span data-stu-id="51d1c-113">For more information about the .NET Core 3.1 release, see [What's new in .NET Core 3.1](./whats-new/dotnet-core-3-1.md).</span></span>

<span data-ttu-id="51d1c-114">如果您正在尋找 .NET Core 的另一個版本，所有版本都可以在[.NET Core 下載中](https://dotnet.microsoft.com/download/dotnet-core)提供。</span><span class="sxs-lookup"><span data-stu-id="51d1c-114">If you're looking for another version of .NET Core, all the versions are available at [.NET Core downloads](https://dotnet.microsoft.com/download/dotnet-core).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="51d1c-115">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="51d1c-115">Create your first application</span></span>

<span data-ttu-id="51d1c-116">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="51d1c-116">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="51d1c-117">輸入以下`dotnet`命令以創建和運行 C# 應用程式：</span><span class="sxs-lookup"><span data-stu-id="51d1c-117">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="51d1c-118">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="51d1c-118">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="51d1c-119">支援</span><span class="sxs-lookup"><span data-stu-id="51d1c-119">Support</span></span>

<span data-ttu-id="51d1c-120">.NET Core 在 Windows、macOS 和 Linux 上[得到微軟的支援](https://dotnet.microsoft.com/platform/support/policy)。</span><span class="sxs-lookup"><span data-stu-id="51d1c-120">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy) on Windows, macOS, and Linux.</span></span> <span data-ttu-id="51d1c-121">每年都為它推出安全性與品質更新數次，通常是一個月一次。</span><span class="sxs-lookup"><span data-stu-id="51d1c-121">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="51d1c-122">.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。</span><span class="sxs-lookup"><span data-stu-id="51d1c-122">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="51d1c-123">[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。</span><span class="sxs-lookup"><span data-stu-id="51d1c-123">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="51d1c-124">Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。</span><span class="sxs-lookup"><span data-stu-id="51d1c-124">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="51d1c-125">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="51d1c-125">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>

## <a name="next-steps"></a><span data-ttu-id="51d1c-126">後續步驟</span><span class="sxs-lookup"><span data-stu-id="51d1c-126">Next steps</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="51d1c-127">.NET 核心教程</span><span class="sxs-lookup"><span data-stu-id="51d1c-127">.NET Core tutorials</span></span>](tutorials/index.md)

> [!div class="nextstepaction"]
> [<span data-ttu-id="51d1c-128">在瀏覽器中試用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="51d1c-128">Try .NET Core in your browser</span></span>](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)
