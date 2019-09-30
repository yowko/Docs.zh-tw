---
title: .NET Core 指南
description: .NET Core 是 .NET 的模組化、高效能實作，可用於建立 Windows、Linux 和 Mac 應用程式。 了解 .NET Core 以開始使用。
author: richlander
ms.date: 09/23/2019
ms.custom: updateeachrelease
ms.openlocfilehash: 95f18ca09852ce139a4b99ed7aef4802d4883e13
ms.sourcegitcommit: 56f1d1203d0075a461a10a301459d3aa452f4f47
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 09/24/2019
ms.locfileid: "71216214"
---
# <a name="net-core-guide"></a><span data-ttu-id="e628c-104">.NET Core 指南</span><span class="sxs-lookup"><span data-stu-id="e628c-104">.NET Core Guide</span></span>

<span data-ttu-id="e628c-105">[.NET Core](about.md) 是[開放原始碼](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT)的一般用途開發平台，由 Microsoft 與 [GitHub](https://github.com/dotnet/core) 上的 .NET 社群共同維護。</span><span class="sxs-lookup"><span data-stu-id="e628c-105">[.NET Core](about.md) is an [open-source](https://github.com/dotnet/coreclr/blob/master/LICENSE.TXT), general-purpose development platform maintained by Microsoft and the .NET community on [GitHub](https://github.com/dotnet/core).</span></span> <span data-ttu-id="e628c-106">它可以跨平台支援 Windows、macOS 與 Linux，並可用於建置裝置、雲端與 IoT 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e628c-106">It's cross-platform (supporting Windows, macOS, and Linux) and can be used to build device, cloud, and IoT applications.</span></span>

<span data-ttu-id="e628c-107">請參閱[關於 .NET Core](about.md)以深入了解 .NET Core，包括其特性、支援的語言與架構，亦即主要 API。</span><span class="sxs-lookup"><span data-stu-id="e628c-107">See [About .NET Core](about.md) to learn more about .NET Core, including its characteristics, supported languages and frameworks, and key APIs.</span></span>

<span data-ttu-id="e628c-108">查看 [.NET Core 教學課程](tutorials/index.md) 以了解如何建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="e628c-108">Check out [.NET Core Tutorials](tutorials/index.md) to learn how to create a simple .NET Core application.</span></span> <span data-ttu-id="e628c-109">只需要幾分鐘，您就可以啟動並執行您的第一個應用程式。</span><span class="sxs-lookup"><span data-stu-id="e628c-109">It only takes a few minutes to get your first app up and running.</span></span> <span data-ttu-id="e628c-110">若要在您的瀏覽器中嘗試 .NET Core，請查看 [C# 中的數字](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml)線上教學課程。</span><span class="sxs-lookup"><span data-stu-id="e628c-110">If you want to try .NET Core in your browser, look at the [Numbers in C#](../csharp/tutorials/intro-to-csharp/numbers-in-csharp.yml) online tutorial.</span></span>

## <a name="download-net-core"></a><span data-ttu-id="e628c-111">下載 .NET Core</span><span class="sxs-lookup"><span data-stu-id="e628c-111">Download .NET Core</span></span>

<span data-ttu-id="e628c-112">下載[.NET Core SDK](https://www.microsoft.com/net/download) ，在您的 Windows、MacOS 或 Linux 電腦上嘗試 .net Core。</span><span class="sxs-lookup"><span data-stu-id="e628c-112">Download the [.NET Core SDK](https://www.microsoft.com/net/download) to try .NET Core on your Windows, macOS, or Linux machine.</span></span> <span data-ttu-id="e628c-113">如果您想要使用 Docker 容器，請造訪[.Net Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/)。</span><span class="sxs-lookup"><span data-stu-id="e628c-113">And if you prefer to use Docker containers, visit the [.NET Core Docker Hub](https://hub.docker.com/_/microsoft-dotnet-core/).</span></span>

<span data-ttu-id="e628c-114">若您要尋找另一個 .NET Core 版本，所有 .NET Core 版本都可以在 [.NET Core 下載 ](https://dotnet.microsoft.com/download/dotnet-core)找到。</span><span class="sxs-lookup"><span data-stu-id="e628c-114">All .NET Core versions are available at [.NET Core Downloads](https://dotnet.microsoft.com/download/dotnet-core) if you're looking for another .NET Core version.</span></span>

## <a name="net-core-30"></a><span data-ttu-id="e628c-115">.NET Core 3.0</span><span class="sxs-lookup"><span data-stu-id="e628c-115">.NET Core 3.0</span></span>

<span data-ttu-id="e628c-116">最新版本是 .NET Core 3.0。</span><span class="sxs-lookup"><span data-stu-id="e628c-116">The latest version is .NET Core 3.0.</span></span> <span data-ttu-id="e628c-117">新功能包括具有 Windows Presentation Foundation (WPF) 與 Windows Forms 的 Windows 桌面支援、使用 Blazor 的完整堆疊 C# Web 開發、SignalR 與 Azure SignalR Service 的新增強功能、C# 8 的新 C# 語言功能等。</span><span class="sxs-lookup"><span data-stu-id="e628c-117">New features include Windows Desktop support with Windows Presentation Foundation (WPF) and Windows Forms, full stack C# web development with Blazor, new enhancements to SignalR and Azure SignalR Service, new C# language features with C# 8, and much more.</span></span> <span data-ttu-id="e628c-118">如需 .NET Core 3.0 中新功能的完整清單，請參閱 [.Net Core 3.0 的新功能](./whats-new/dotnet-core-3-0.md)。</span><span class="sxs-lookup"><span data-stu-id="e628c-118">For a full listing of the new features in .NET Core 3.0, see [What's new in .NET Core 3.0](./whats-new/dotnet-core-3-0.md).</span></span>

## <a name="create-your-first-application"></a><span data-ttu-id="e628c-119">建立您的第一個應用程式</span><span class="sxs-lookup"><span data-stu-id="e628c-119">Create your first application</span></span>

<span data-ttu-id="e628c-120">安裝 .NET Core SDK 之後，請開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="e628c-120">After installing the .NET Core SDK, open a command prompt.</span></span> <span data-ttu-id="e628c-121">輸入下列`dotnet`命令來建立並執行C#應用程式：</span><span class="sxs-lookup"><span data-stu-id="e628c-121">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console
dotnet run
```

<span data-ttu-id="e628c-122">您應該會看到下列輸出：</span><span class="sxs-lookup"><span data-stu-id="e628c-122">You should see the following output:</span></span>

```output
Hello World!
```

## <a name="support"></a><span data-ttu-id="e628c-123">支援</span><span class="sxs-lookup"><span data-stu-id="e628c-123">Support</span></span>

<span data-ttu-id="e628c-124">Microsoft、Windows、macOS 和 Linux 上都[支援](https://dotnet.microsoft.com/platform/support/policy).net Core。</span><span class="sxs-lookup"><span data-stu-id="e628c-124">.NET Core is [supported by Microsoft](https://dotnet.microsoft.com/platform/support/policy), on Windows, macOS, and Linux.</span></span> <span data-ttu-id="e628c-125">每年都為它推出安全性與品質更新數次，通常是一個月一次。</span><span class="sxs-lookup"><span data-stu-id="e628c-125">It's updated for security and quality several times a year, typically monthly.</span></span>

<span data-ttu-id="e628c-126">.NET Core 二進位發行版本是在 Azure 中由 Microsoft 維護的服務上建置及測試，而且享有與任何 Microsoft 產品一樣的支援。</span><span class="sxs-lookup"><span data-stu-id="e628c-126">.NET Core binary distributions are built and tested on Microsoft-maintained servers in Azure and supported just like any Microsoft product.</span></span>

<span data-ttu-id="e628c-127">[Red Hat 在 Red Hat Enterprise Linux (RHEL) 上支援 .NET Core](http://redhatloves.net/)。</span><span class="sxs-lookup"><span data-stu-id="e628c-127">[Red Hat supports .NET Core](http://redhatloves.net/) on Red Hat Enterprise Linux (RHEL).</span></span> <span data-ttu-id="e628c-128">Red Hat 從原始碼建置 .NET Core 並在 [Red Hat 軟體集合](https://developers.redhat.com/products/softwarecollections/overview/)中提供。</span><span class="sxs-lookup"><span data-stu-id="e628c-128">Red Hat builds .NET Core from source and makes it available in the [Red Hat Software Collections](https://developers.redhat.com/products/softwarecollections/overview/).</span></span> <span data-ttu-id="e628c-129">Red Hat 與 Microsoft 共同作業以確保 .NET Core 可在 RHEL 上正確運作。</span><span class="sxs-lookup"><span data-stu-id="e628c-129">Red Hat and Microsoft collaborate to ensure that .NET Core works well on RHEL.</span></span>
