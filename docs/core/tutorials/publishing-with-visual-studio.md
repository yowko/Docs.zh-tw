---
title: "使用 Visual Studio 2017 發行您的 Hello World 應用程式"
description: "發行會建立一組執行您的應用程式所需的檔案。"
keywords: ".NET, .NET Core, 主控台應用程式, 發行, 部署"
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.topic: article
ms.prod: .net-core
ms.technology: devlang-csharp
ms.devlang: csharp
ms.assetid: a19545d3-24af-4a32-9778-cfb5ae938287
ms.workload: dotnetcore
ms.openlocfilehash: 40479d85f9b31fcc80e3d12537126941878a09a4
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/23/2017
---
# <a name="publish-your-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="e9794-104">使用 Visual Studio 2017 發行您的 Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="e9794-104">Publish your Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="e9794-105">於[在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式](with-visual-studio.md)或[在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic Hello World 應用程式](vb-with-visual-studio.md)中，您建立了 Hello World 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9794-105">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="e9794-106">在[使用 Visual Studio 2017 針對 C# Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)中，您已使用 Visual Studio 偵錯工具加以測試。</span><span class="sxs-lookup"><span data-stu-id="e9794-106">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="e9794-107">現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。</span><span class="sxs-lookup"><span data-stu-id="e9794-107">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="e9794-108">發行會建立一組執行您的應用程式所需的檔案，您可以將這些檔案複製到目標電腦來加以部署。</span><span class="sxs-lookup"><span data-stu-id="e9794-108">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="e9794-109">編譯和執行您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="e9794-109">To publish and run your application:</span></span> 

1. <span data-ttu-id="e9794-110">請確定 Visual Studio 正在組置您應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="e9794-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="e9794-111">如有必要，請將工具列上的組建組態設定從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="e9794-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![Visual Studio 工具列](media/publishing-with-visual-studio/toolbar.png)

1. <span data-ttu-id="e9794-113">在 **HelloWorld** 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="e9794-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="e9794-114">您也可以從主要的 Visual Studio **[建置]** 功能表，選取 **[發行 HelloWorld]**。</span><span class="sxs-lookup"><span data-stu-id="e9794-114">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio 工具列](media/publishing-with-visual-studio/publish1.png)


   ![Visual Studio 工具列](media/publishing-with-visual-studio/publishwindow.png)

1. <span data-ttu-id="e9794-117">開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="e9794-117">Open a console window.</span></span> <span data-ttu-id="e9794-118">例如，在 Windows 工作列的 [Type here to search] (在這裡鍵入要搜尋的文字) 文字方塊中，輸入 `Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="e9794-118">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="e9794-119">巡覽至已發行的應用程式，其位於應用程式專案目錄的 `bin\release\PublishOutput` 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="e9794-119">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="e9794-120">如下圖所示，已發行的輸出包含下列四個檔案：</span><span class="sxs-lookup"><span data-stu-id="e9794-120">As the following figure shows, the published output includes the following four files:</span></span>

      * <span data-ttu-id="e9794-121">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="e9794-121">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="e9794-122">應用程式的執行階段相依性檔案。</span><span class="sxs-lookup"><span data-stu-id="e9794-122">The application's runtime dependencies file.</span></span> <span data-ttu-id="e9794-123">它會定義執行您應用程式所需的 .NET Core 元件和程式庫 (包含內含您應用程式的動態連結程式庫)。</span><span class="sxs-lookup"><span data-stu-id="e9794-123">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="e9794-124">如需詳細資訊，請參閱[執行階段組態檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="e9794-124">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * <span data-ttu-id="e9794-125">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="e9794-125">*HelloWorld.dll*</span></span>

         <span data-ttu-id="e9794-126">包含您應用程式的檔案。</span><span class="sxs-lookup"><span data-stu-id="e9794-126">The file that contains your application.</span></span> <span data-ttu-id="e9794-127">它是動態連結程式庫，可在主控台視窗中輸入 `dotnet HelloWorld.dll` 命令予以執行。</span><span class="sxs-lookup"><span data-stu-id="e9794-127">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="e9794-128">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="e9794-128">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="e9794-129">包含偵錯符號的檔案。</span><span class="sxs-lookup"><span data-stu-id="e9794-129">A file that contains debug symbols.</span></span> <span data-ttu-id="e9794-130">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="e9794-130">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="e9794-131">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="e9794-131">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="e9794-132">應用程式的執行階段組態檔。</span><span class="sxs-lookup"><span data-stu-id="e9794-132">The application's runtime configuration file.</span></span> <span data-ttu-id="e9794-133">它會識別建置您應用程式以在其上執行的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="e9794-133">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="e9794-134">如需詳細資訊，請參閱[執行階段組態檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="e9794-134">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/publishedfiles.png)

<span data-ttu-id="e9794-136">發行程序會建立與 Framework 相依的部署，在這種部署類型中，只要 .NET Core 安裝在系統上，發行的應用程式即可以在 .NET Core 支援的任何平台上執行。</span><span class="sxs-lookup"><span data-stu-id="e9794-136">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="e9794-137">使用者可以從主控台視窗發出 `dotnet HelloWorld.dll` 命令來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="e9794-137">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="e9794-138">如需有關發行和部署 .NET Core 應用程式的詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="e9794-138">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
