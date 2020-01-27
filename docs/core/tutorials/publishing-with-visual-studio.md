---
title: 使用 Visual Studio 發佈您的 .NET Core Hello World 應用程式
description: 發行會建立一組執行您的 .NET Core 應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: a82934fd2ea9568681a3bec82c3b15513decc926
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 01/24/2020
ms.locfileid: "76741574"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="f0a64-103">使用 Visual Studio 發佈您的 .NET Core Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="f0a64-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="f0a64-104">在[Visual Studio 中使用 .Net Core 建立 Hello World 應用程式](with-visual-studio.md)時，您已建立 Hello World 主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0a64-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="f0a64-105">在[使用 Visual Studio 來進行 Hello World 應用程式](debugging-with-visual-studio.md)的「偵測」時，您會使用 Visual Studio 偵錯工具進行測試。</span><span class="sxs-lookup"><span data-stu-id="f0a64-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="f0a64-106">現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。</span><span class="sxs-lookup"><span data-stu-id="f0a64-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="f0a64-107">發行會建立一組執行您的應用程式所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="f0a64-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="f0a64-108">若要部署檔案，請將檔案複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="f0a64-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="f0a64-109">發行應用程式</span><span class="sxs-lookup"><span data-stu-id="f0a64-109">Publish the app</span></span>

1. <span data-ttu-id="f0a64-110">請確定 Visual Studio 正在組置您應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="f0a64-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="f0a64-111">如有必要，請將工具列上的組建組態設定從 [偵錯] 變更為 [發行]。</span><span class="sxs-lookup"><span data-stu-id="f0a64-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="f0a64-113">在 **HelloWorld** 專案 (而非 HelloWorld 方案) 上按一下滑鼠右鍵，然後從功能表選取 [發行]。</span><span class="sxs-lookup"><span data-stu-id="f0a64-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="f0a64-114">（您也可以從主要的 [**組建**] 功能表中選取 [**發佈 HelloWorld** ]）。</span><span class="sxs-lookup"><span data-stu-id="f0a64-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)
   
1. <span data-ttu-id="f0a64-116">在 [**挑選發行目標**] 頁面上，選取 [**資料夾**]，然後選取 [**建立設定檔**]。</span><span class="sxs-lookup"><span data-stu-id="f0a64-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![在 Visual Studio 中挑選發行目標](media/publishing-with-visual-studio/pick-publish-target.png)
   
1. <span data-ttu-id="f0a64-118">在 [**發行**] 頁面上，選取 [**發佈**]。</span><span class="sxs-lookup"><span data-stu-id="f0a64-118">On the **Publish** page, select **Publish**.</span></span>

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-page.png)
   
## <a name="inspect-the-files"></a><span data-ttu-id="f0a64-120">檢查檔案</span><span class="sxs-lookup"><span data-stu-id="f0a64-120">Inspect the files</span></span>

<span data-ttu-id="f0a64-121">發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在 .NET Core 所支援的任何平臺上執行，並在系統上安裝 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="f0a64-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="f0a64-122">使用者可以按兩下可執行檔，或從命令提示字元發出 `dotnet HelloWorld.dll` 命令，以執行已發佈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0a64-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="f0a64-123">在下列步驟中，您將查看發行程式所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="f0a64-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="f0a64-124">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="f0a64-124">Open a command prompt.</span></span>

   <span data-ttu-id="f0a64-125">開啟命令提示字元的方法之一，就是在 Windows 工作列的 [搜尋] 方塊中輸入**命令提示**字元（簡稱**cmd** ）。</span><span class="sxs-lookup"><span data-stu-id="f0a64-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="f0a64-126">選取 [**命令提示**字元] 桌面應用程式，如果已在搜尋結果中選取，請按**enter** 。</span><span class="sxs-lookup"><span data-stu-id="f0a64-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="f0a64-127">在應用程式專案目錄的*bin\Release\netcoreapp3.1\publish*子目錄中，流覽至已發佈的應用程式。</span><span class="sxs-lookup"><span data-stu-id="f0a64-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="f0a64-129">如圖所示，已發行的輸出會包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="f0a64-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="f0a64-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="f0a64-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="f0a64-131">這是應用程式的執行時間相依性檔案。</span><span class="sxs-lookup"><span data-stu-id="f0a64-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="f0a64-132">它會定義執行應用程式所需的 .NET Core 元件和程式庫（包括包含您應用程式的動態連結程式庫）。</span><span class="sxs-lookup"><span data-stu-id="f0a64-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="f0a64-133">如需詳細資訊，請參閱[執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="f0a64-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="f0a64-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="f0a64-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="f0a64-135">這是與[framework 相依](../deploying/deploy-with-cli.md#framework-dependent-deployment)的應用程式部署版本。</span><span class="sxs-lookup"><span data-stu-id="f0a64-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="f0a64-136">若要執行此動態連結程式庫，請在命令提示字元中輸入 `dotnet HelloWorld.dll`。</span><span class="sxs-lookup"><span data-stu-id="f0a64-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="f0a64-137">*HelloWorld .exe*</span><span class="sxs-lookup"><span data-stu-id="f0a64-137">*HelloWorld.exe*</span></span>
      
         <span data-ttu-id="f0a64-138">這是與[framework 相依的應用程式可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。</span><span class="sxs-lookup"><span data-stu-id="f0a64-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="f0a64-139">若要執行，請在命令提示字元中輸入 `HelloWorld.exe`。</span><span class="sxs-lookup"><span data-stu-id="f0a64-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="f0a64-140">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="f0a64-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="f0a64-141">這是 debug 符號檔案。</span><span class="sxs-lookup"><span data-stu-id="f0a64-141">This is the debug symbols file.</span></span> <span data-ttu-id="f0a64-142">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="f0a64-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="f0a64-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="f0a64-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="f0a64-144">這是應用程式的執行時間設定檔。</span><span class="sxs-lookup"><span data-stu-id="f0a64-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="f0a64-145">它會識別建置您應用程式以在其上執行的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="f0a64-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="f0a64-146">您也可以在其中新增設定選項。</span><span class="sxs-lookup"><span data-stu-id="f0a64-146">You can also add configuration options to it.</span></span> <span data-ttu-id="f0a64-147">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="f0a64-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="f0a64-148">其他資源</span><span class="sxs-lookup"><span data-stu-id="f0a64-148">Additional resources</span></span>

- [<span data-ttu-id="f0a64-149">.NET Core 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="f0a64-149">.NET Core application deployment</span></span>](../deploying/index.md)
