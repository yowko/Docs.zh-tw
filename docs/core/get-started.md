---
title: .NET Core 使用者入門
description: 尋找資源以瞭解如何在 Windows、Linux 和 macOS 上建立 .NET Core 應用程式。
author: adegeo
ms.author: adegeo
ms.date: 12/03/2019
ms.custom: vs-dotnet
ms.openlocfilehash: 56eebc0fc5bad6f57d93358cbbef389d6355d66b
ms.sourcegitcommit: c4a15c6c4ecbb8a46ad4e67d9b3ab9b8b031d849
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 08/20/2020
ms.locfileid: "88656686"
---
# <a name="get-started-with-net-core"></a><span data-ttu-id="de455-103">.NET Core 使用者入門</span><span class="sxs-lookup"><span data-stu-id="de455-103">Get started with .NET Core</span></span>

<span data-ttu-id="de455-104">本文提供 .NET Core 使用者入門的相關資訊。</span><span class="sxs-lookup"><span data-stu-id="de455-104">This article provides information on getting started with .NET Core.</span></span> <span data-ttu-id="de455-105">.NET Core 可以安裝在 Windows、Linux 和 macOS 上。</span><span class="sxs-lookup"><span data-stu-id="de455-105">.NET Core can be installed on Windows, Linux, and macOS.</span></span> <span data-ttu-id="de455-106">您可以在慣用的文字編輯器中撰寫程式碼，然後產生跨平台的程式庫和應用程式。</span><span class="sxs-lookup"><span data-stu-id="de455-106">You can code in your favorite text editor and produce cross-platform libraries and applications.</span></span>

<span data-ttu-id="de455-107">如果您不確定什麼是 .NET Core 或與其他 .NET 技術有何關聯，請從 [什麼是 .net](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) 總覽著手。</span><span class="sxs-lookup"><span data-stu-id="de455-107">If you're unsure what .NET Core is or how it relates to other .NET technologies, start with the [What is .NET](https://dotnet.microsoft.com/learn/dotnet/what-is-dotnet) overview.</span></span> <span data-ttu-id="de455-108">簡單來說，.NET Core 是 .NET 的開放原始碼跨平台實作。</span><span class="sxs-lookup"><span data-stu-id="de455-108">Put simply, .NET Core is an open-source, cross-platform implementation of .NET.</span></span>

## <a name="create-an-application"></a><span data-ttu-id="de455-109">建立應用程式</span><span class="sxs-lookup"><span data-stu-id="de455-109">Create an application</span></span>

<span data-ttu-id="de455-110">首先，在您的電腦上下載並安裝 [.NET Core SDK](https://dotnet.microsoft.com/download)。</span><span class="sxs-lookup"><span data-stu-id="de455-110">First, download and install the [.NET Core SDK](https://dotnet.microsoft.com/download) on your computer.</span></span>

<span data-ttu-id="de455-111">接下來，開啟終端機，例如 **PowerShell**、**命令提示字元**或 **bash**。</span><span class="sxs-lookup"><span data-stu-id="de455-111">Next, open a terminal such as **PowerShell**, **Command Prompt**, or **bash**.</span></span> <span data-ttu-id="de455-112">輸入下列 `dotnet` 命令來建立和執行 c # 應用程式：</span><span class="sxs-lookup"><span data-stu-id="de455-112">Enter the following `dotnet` commands to create and run a C# application:</span></span>

```dotnetcli
dotnet new console --output sample1
dotnet run --project sample1
```

<span data-ttu-id="de455-113">您應該會看見下列輸出：</span><span class="sxs-lookup"><span data-stu-id="de455-113">You should see the following output:</span></span>

```console
Hello World!
```

<span data-ttu-id="de455-114">恭喜！</span><span class="sxs-lookup"><span data-stu-id="de455-114">Congratulations!</span></span> <span data-ttu-id="de455-115">您已建立簡單的 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="de455-115">You've created a simple .NET Core application.</span></span> <span data-ttu-id="de455-116">您也可以使用 [Visual Studio Code](./tutorials/with-visual-studio-code.md)、[Visual Studio](./tutorials/with-visual-studio.md) (僅限 Windows) 或 [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (僅限 macOS) 建立 .NET Core 應用程式。</span><span class="sxs-lookup"><span data-stu-id="de455-116">You can also use [Visual Studio Code](./tutorials/with-visual-studio-code.md), [Visual Studio](./tutorials/with-visual-studio.md) (Windows only), or [Visual Studio for Mac](tutorials/with-visual-studio-mac.md) (macOS only), to create a .NET Core application.</span></span>

## <a name="tutorials"></a><span data-ttu-id="de455-117">教學課程</span><span class="sxs-lookup"><span data-stu-id="de455-117">Tutorials</span></span>

<span data-ttu-id="de455-118">遵循下列逐步教學課程，開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="de455-118">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

<!-- markdownlint-disable MD025 -->

# <a name="windows"></a>[<span data-ttu-id="de455-119">Windows</span><span class="sxs-lookup"><span data-stu-id="de455-119">Windows</span></span>](#tab/windows)

- [<span data-ttu-id="de455-120">在 Visual Studio 2019 中建立您的第一個 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="de455-120">Create your first .NET Core console application in Visual Studio 2019</span></span>](./tutorials/with-visual-studio.md)
- [<span data-ttu-id="de455-121">在 Visual Studio 中建立具有 .NET Standard 的類別庫</span><span class="sxs-lookup"><span data-stu-id="de455-121">Build a class library with .NET Standard in Visual Studio</span></span>](./tutorials/library-with-visual-studio.md)
- [<span data-ttu-id="de455-122">教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="de455-122">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="de455-123">![影片的電影攝影機圖示](./media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="de455-123">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="de455-124">觀看 Channel 9 上的 [如何安裝和使用 Visual Studio Code 和 .Net Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) 影片。</span><span class="sxs-lookup"><span data-stu-id="de455-124">Watch the [how to install and use Visual Studio Code and .NET Core](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-using-CSharp-and-NET-Core/) video on Channel 9.</span></span> |
| <span data-ttu-id="de455-125">![影片的電影攝影機圖示](./media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="de455-125">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="de455-126">觀看 YouTube 上的 [.Net Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) 影片。</span><span class="sxs-lookup"><span data-stu-id="de455-126">Watch the [.NET Core 101](https://www.youtube.com/playlist?list=PLdo4fOcmZ0oWoazjhXQzBKMrFuArxpW80) videos on YouTube.</span></span> |

<span data-ttu-id="de455-127">如需支援的 Windows 版本清單，請參閱 [.Net Core 相依性和需求](install/dependencies.md?pivots=os-windows) 文章。</span><span class="sxs-lookup"><span data-stu-id="de455-127">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-windows) article for a list of the supported Windows versions.</span></span>

# <a name="linux"></a>[<span data-ttu-id="de455-128">Linux</span><span class="sxs-lookup"><span data-stu-id="de455-128">Linux</span></span>](#tab/linux)

<span data-ttu-id="de455-129">遵循下列逐步教學課程，開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="de455-129">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="de455-130">教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="de455-130">Tutorial: Create a .NET Core console app using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)

|   |   |
|---|---|
| <span data-ttu-id="de455-131">![影片的電影攝影機圖示](./media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="de455-131">![movie camera icon for video](./media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="de455-132">觀看影片以了解[使用 C# 和 .NET Core 在 Ubuntu 上開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu)。</span><span class="sxs-lookup"><span data-stu-id="de455-132">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on Ubuntu](https://channel9.msdn.com/Blogs/dotnet/Get-started-with-VS-Code-Csharp-dotnet-Core-Ubuntu).</span></span> |

<span data-ttu-id="de455-133">如需支援的 Linux 散發版本和版本清單，請參閱 [.Net Core 相依性和需求](install/dependencies.md?pivots=os-linux) 文章。</span><span class="sxs-lookup"><span data-stu-id="de455-133">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-linux) article for a list of the supported Linux distros and versions.</span></span>

# <a name="macos"></a>[<span data-ttu-id="de455-134">macOS</span><span class="sxs-lookup"><span data-stu-id="de455-134">macOS</span></span>](#tab/macos)

<span data-ttu-id="de455-135">遵循下列逐步教學課程，開始開發 .NET Core 應用程式：</span><span class="sxs-lookup"><span data-stu-id="de455-135">Get started developing .NET Core applications by following these step-by-step tutorials:</span></span>

- [<span data-ttu-id="de455-136">教學課程：使用 Visual Studio Code 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="de455-136">Tutorial: Create a .NET Core console application using Visual Studio Code</span></span>](tutorials/with-visual-studio-code.md)
- [<span data-ttu-id="de455-137">教學課程：使用 Visual Studio for Mac 建立 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="de455-137">Tutorial: Create a .NET Core console application using Visual Studio for Mac</span></span>](tutorials/with-visual-studio-mac.md)
- [<span data-ttu-id="de455-138">使用 Visual Studio for Mac 在 macOS 上建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="de455-138">Build a .NET Standard library on macOS using Visual Studio for Mac</span></span>](tutorials/library-with-visual-studio-mac.md)

|   |   |
|---|---|
| <span data-ttu-id="de455-139">![影片的電影攝影機圖示](media/video-icon.png "觀看影片")</span><span class="sxs-lookup"><span data-stu-id="de455-139">![movie camera icon for video](media/video-icon.png "Watch a video")</span></span> | <span data-ttu-id="de455-140">觀看在 macOS 上 [使用 c # 和 .Net Core 開始使用 Visual Studio Code](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac)的影片。</span><span class="sxs-lookup"><span data-stu-id="de455-140">Watch a video on [getting started with Visual Studio Code using C# and .NET Core on macOS](https://channel9.msdn.com/Blogs/dotnet/Get-started-VSCode-NET-Core-Mac).</span></span> |

<span data-ttu-id="de455-141">請參閱 [.Net Core 相依性和需求](install/dependencies.md?pivots=os-macos) 一文，以取得支援的 OS X/macOS 版本清單。</span><span class="sxs-lookup"><span data-stu-id="de455-141">See the [.NET Core dependencies and requirements](install/dependencies.md?pivots=os-macos) article for a list of the supported OS X / macOS versions.</span></span>

---
