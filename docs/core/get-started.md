---
title: .NET Core 使用者入門
description: 查找資源以瞭解如何在 Windows、Linux 和 macOS 上構建 .NET 核心應用程式。
author: thraka
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 0968d9db1dbfbdc8c586328ee8e02315f17950b9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "75714386"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="9bd2c-103">.NET Core 使用者入門</span><span class="sxs-lookup"><span data-stu-id="9bd2c-103">Get started with .NET Core</span></span>

<span data-ttu-id="9bd2c-104">本文提供 .NET Core 使用者入門的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="9bd2c-105">.NET Core 可以安裝在 Windows、Linux 和 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="9bd2c-106">您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="9bd2c-107">如果您不確定 .NET Core 為何，或不確定它與其他 .NET 技術的關聯，請從 [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) (什麼是 .NET) 概觀開始。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-107">If you're unsure what .NET Core is, or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="9bd2c-108">簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="9bd2c-109">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="9bd2c-109">Create an application</span></span>

<span data-ttu-id="9bd2c-110">首先，在您的電腦上下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="9bd2c-111">接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="9bd2c-112">鍵入以下`dotnet`命令以創建和運行 C# 應用程式：</span><span class="sxs-lookup"><span data-stu-id="9bd2c-112">Type the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="9bd2c-113">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="9bd2c-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="9bd2c-114">恭喜！</span><span class="sxs-lookup"><span data-stu-id="9bd2c-114">Congratulations!</span></span> <span data-ttu-id="9bd2c-115">您已建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="9bd2c-116">您也可以使用 [Visual Studio Code](./tutorials/with-visual-studio-code.md)、[Visual Studio](./tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (僅限 macOS) 建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](./tutorials/using-on-mac-vs.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="9bd2c-117">教學課程</span><span class="sxs-lookup"><span data-stu-id="9bd2c-117">Tutorials</span></span>

<span data-ttu-id="9bd2c-118">通過按照以下分步教程開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="9bd2c-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="9bd2c-119">Windows</span><span class="sxs-lookup"><span data-stu-id="9bd2c-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="9bd2c-120">在 Visual Studio 2019 中創建您的第一個 .NET 核心主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="9bd2c-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="9bd2c-121">在視覺化工作室中使用 .NET 標準構建類庫</span><span class="sxs-lookup"><span data-stu-id="9bd2c-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="9bd2c-122">使用 .NET 核心 CLI 開始使用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="9bd2c-122">Get started with .NET Core using the .NET Core CLI</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="9bd2c-123">![影片的電影攝影機圖示](./media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="9bd2c-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="9bd2c-124">觀看如何在第 9 頻道[上安裝和使用 Visual Studio 代碼和 .NET 核心](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/)視頻。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="9bd2c-125">![影片的電影攝影機圖示](./media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="9bd2c-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="9bd2c-126">在 YouTube 上觀看[.NET 核心 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80)視頻。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="9bd2c-127">有關受支援的 Windows 版本的清單，請參閱[.NET Core 依賴項和要求](install/dependencies.md?pivots=os-windows)文章。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="9bd2c-128">Linux</span><span class="sxs-lookup"><span data-stu-id="9bd2c-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="9bd2c-129">通過按照以下分步教程開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="9bd2c-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="9bd2c-130">使用 命令列開始使用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="9bd2c-130">Get started with .NET Core using the command line</span></span>](./tutorials/cli-create-console-app.md)

|   |   |
|---|---|
| <span data-ttu-id="9bd2c-131">![影片的電影攝影機圖示](./media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="9bd2c-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="9bd2c-132">觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="9bd2c-133">有關支援的 Linux 發行版本和版本的清單，請參閱[.NET Core 依賴項和要求](install/dependencies.md?pivots=os-linux)文章。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="9bd2c-134">macOS</span><span class="sxs-lookup"><span data-stu-id="9bd2c-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="9bd2c-135">通過按照以下分步教程開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="9bd2c-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="9bd2c-136">使用 Visual Studio Code 在 macOS 上開始使用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="9bd2c-136">Get started with .NET Core on macOS using Visual Studio Code</span></span>](./tutorials/using-on-macos.md)
- [<span data-ttu-id="9bd2c-137">使用命令列開始使用 .NET 核心</span><span class="sxs-lookup"><span data-stu-id="9bd2c-137">Get started with .NET Core using the command-line</span></span>](./tutorials/cli-create-console-app.md)
- [<span data-ttu-id="9bd2c-138">使用 Visual Studio for Mac 在 macOS 上開始使用 .NET Core</span><span class="sxs-lookup"><span data-stu-id="9bd2c-138">Get started with .NET Core on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs.md)
- [<span data-ttu-id="9bd2c-139">使用 Mac 視覺化工作室在 macOS 上構建完整的 .NET 核心解決方案</span><span class="sxs-lookup"><span data-stu-id="9bd2c-139">Build a complete .NET Core solution on macOS using Visual Studio for Mac</span></span>](./tutorials/using-on-mac-vs-full-solution.md)

|   |   |
|---|---|
| <span data-ttu-id="9bd2c-140">![影片的電影攝影機圖示](media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="9bd2c-140">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="9bd2c-141">觀看[macOS 上使用 C# 和 .NET Core 開始使用 Visual Studio 代碼](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)的視頻。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-141">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="9bd2c-142">有關支援的 OS X/ macOS 版本的清單，請參閱[.NET Core 依賴項和要求](install/dependencies.md?pivots=os-macos)文章。</span><span class="sxs-lookup"><span data-stu-id="9bd2c-142">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
