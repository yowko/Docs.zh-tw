---
title: 使用 Visual Studio 2017 發佈您的 .NET Core Hello World 應用程式
description: 發行會建立一組執行您的 .NET Core 應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 10/05/2017
ms.custom: vs-dotnet, seodec18
ms.openlocfilehash: 0322d44ca37ab8e7faa3188887069c2e04ec755b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: zh-TW
ms.lasthandoff: 04/08/2019
ms.locfileid: "59110262"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio-2017"></a><span data-ttu-id="52509-103">使用 Visual Studio 2017 發佈您的 .NET Core Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="52509-103">Publish your .NET Core Hello World application with Visual Studio 2017</span></span>

<span data-ttu-id="52509-104">於[在 Visual Studio 2017 中使用 .NET Core 建置 C# Hello World 應用程式](with-visual-studio.md)或[在 Visual Studio 2017 中使用 .NET Core 建置 Visual Basic Hello World 應用程式](vb-with-visual-studio.md)中，您建立了 Hello World 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="52509-104">In [Build a C# Hello World application with .NET Core in Visual Studio 2017](with-visual-studio.md) or [Build a Visual Basic Hello World application with .NET Core in Visual Studio 2017](vb-with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="52509-105">在[使用 Visual Studio 2017 針對 C# Hello World 應用程式進行偵錯](debugging-with-visual-studio.md)中，您已使用 Visual Studio 偵錯工具加以測試。</span><span class="sxs-lookup"><span data-stu-id="52509-105">In [Debug your C# Hello World application with Visual Studio 2017](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="52509-106">現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。</span><span class="sxs-lookup"><span data-stu-id="52509-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="52509-107">發行會建立一組執行您的應用程式所需的檔案，您可以將這些檔案複製到目標電腦來加以部署。</span><span class="sxs-lookup"><span data-stu-id="52509-107">Publishing creates the set of files that are needed to run your application, and you can deploy the files by copying them to a target machine.</span></span>

<span data-ttu-id="52509-108">編譯和執行您的應用程式：</span><span class="sxs-lookup"><span data-stu-id="52509-108">To publish and run your application:</span></span> 

1. <span data-ttu-id="52509-109">請確定 Visual Studio 正在組置您應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="52509-109">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="52509-110">如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。</span><span class="sxs-lookup"><span data-stu-id="52509-110">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="52509-112">在 **HelloWorld** 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="52509-112">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="52509-113">您也可以從主要的 Visual Studio **[建置]** 功能表，選取 **[發行 HelloWorld]**。</span><span class="sxs-lookup"><span data-stu-id="52509-113">You can also select **Publish HelloWorld** from the main Visual Studio **Build** menu.</span></span>

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-settings-window.png)

1. <span data-ttu-id="52509-116">開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="52509-116">Open a console window.</span></span> <span data-ttu-id="52509-117">例如，在 Windows 工作列的 [Type here to search] (在這裡鍵入要搜尋的文字) 文字方塊中，輸入 `Command Prompt` (或 `cmd` 簡稱)，然後選取 [命令提示字元] 桌面應用程式，或按 Enter 鍵 (如果已在搜尋結果中選取該應用程式) 來開啟主控台視窗。</span><span class="sxs-lookup"><span data-stu-id="52509-117">For example in the **Type here to search** text box in the Windows taskbar, enter `Command Prompt` (or `cmd` for short), and open a console window by either selecting the **Command Prompt** desktop app or pressing Enter if it's selected in the search results.</span></span>

1. <span data-ttu-id="52509-118">巡覽至已發行的應用程式，其位於應用程式專案目錄的 `bin\release\PublishOutput` 子目錄中。</span><span class="sxs-lookup"><span data-stu-id="52509-118">Navigate to the published application in the `bin\release\PublishOutput` subdirectory of your application's project directory.</span></span> <span data-ttu-id="52509-119">如下圖所示，已發行的輸出包含下列四個檔案：</span><span class="sxs-lookup"><span data-stu-id="52509-119">As the following figure shows, the published output includes the following four files:</span></span>

      * *<span data-ttu-id="52509-120">HelloWorld.deps.json</span><span class="sxs-lookup"><span data-stu-id="52509-120">HelloWorld.deps.json</span></span>*

         <span data-ttu-id="52509-121">應用程式的執行階段相依性檔案。</span><span class="sxs-lookup"><span data-stu-id="52509-121">The application's runtime dependencies file.</span></span> <span data-ttu-id="52509-122">它會定義執行您應用程式所需的 .NET Core 元件和程式庫 (包含內含您應用程式的動態連結程式庫)。</span><span class="sxs-lookup"><span data-stu-id="52509-122">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run your application.</span></span> <span data-ttu-id="52509-123">如需詳細資訊，請參閱[執行階段組態檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="52509-123">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>
 
      * *<span data-ttu-id="52509-124">HelloWorld.dll</span><span class="sxs-lookup"><span data-stu-id="52509-124">HelloWorld.dll</span></span>*

         <span data-ttu-id="52509-125">包含您應用程式的檔案。</span><span class="sxs-lookup"><span data-stu-id="52509-125">The file that contains your application.</span></span> <span data-ttu-id="52509-126">它是動態連結程式庫，可在主控台視窗中輸入 `dotnet HelloWorld.dll` 命令予以執行。</span><span class="sxs-lookup"><span data-stu-id="52509-126">It is a dynamic link library that can be executed by entering the `dotnet HelloWorld.dll` command in a console window.</span></span> 

      * <span data-ttu-id="52509-127">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="52509-127">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="52509-128">包含偵錯符號的檔案。</span><span class="sxs-lookup"><span data-stu-id="52509-128">A file that contains debug symbols.</span></span> <span data-ttu-id="52509-129">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="52509-129">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * *<span data-ttu-id="52509-130">HelloWorld.runtimeconfig.json</span><span class="sxs-lookup"><span data-stu-id="52509-130">HelloWorld.runtimeconfig.json</span></span>*

         <span data-ttu-id="52509-131">應用程式的執行階段組態檔。</span><span class="sxs-lookup"><span data-stu-id="52509-131">The application's runtime configuration file.</span></span> <span data-ttu-id="52509-132">它會識別建置您應用程式以在其上執行的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="52509-132">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="52509-133">如需詳細資訊，請參閱[執行階段組態檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="52509-133">For more information, see [Runtime Configuration Files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>  

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/published-files-output.png)

<span data-ttu-id="52509-135">發行程序會建立與 Framework 相依的部署，在這種部署類型中，只要 .NET Core 安裝在系統上，發行的應用程式即可以在 .NET Core 支援的任何平台上執行。</span><span class="sxs-lookup"><span data-stu-id="52509-135">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application will run on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="52509-136">使用者可以從主控台視窗發出 `dotnet HelloWorld.dll` 命令來執行您的應用程式。</span><span class="sxs-lookup"><span data-stu-id="52509-136">Users can run your application by issuing the `dotnet HelloWorld.dll` command from a console window.</span></span>

<span data-ttu-id="52509-137">如需有關發行和部署 .NET Core 應用程式的詳細資訊，請參閱 [.NET Core 應用程式部署](../../core/deploying/index.md)。</span><span class="sxs-lookup"><span data-stu-id="52509-137">For more information on publishing and deploying .NET Core applications, see [.NET Core Application Deployment](../../core/deploying/index.md).</span></span>
