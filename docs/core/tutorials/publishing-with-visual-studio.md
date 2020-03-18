---
title: 使用視覺化工作室發佈您的 .NET 核心 Hello World 應用程式
description: 發行會建立一組執行您的 .NET Core 應用程式所需的檔案。
author: BillWagner
ms.author: wiwagn
ms.date: 12/10/2019
ms.custom: vs-dotnet
ms.openlocfilehash: bdd6e28713bdece2bd144e6763bd84d719e91449
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 03/14/2020
ms.locfileid: "78156630"
---
# <a name="publish-your-net-core-hello-world-application-with-visual-studio"></a><span data-ttu-id="8de16-103">使用視覺化工作室發佈您的 .NET 核心 Hello World 應用程式</span><span class="sxs-lookup"><span data-stu-id="8de16-103">Publish your .NET Core Hello World application with Visual Studio</span></span>

<span data-ttu-id="8de16-104">在[創建一個Hello世界應用程式與.NET核心在視覺工作室](with-visual-studio.md)，你建立了一個Hello世界主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="8de16-104">In [Create a Hello World application with .NET Core in Visual Studio](with-visual-studio.md), you built a Hello World console application.</span></span> <span data-ttu-id="8de16-105">在[調試你的Hello世界應用程式與視覺化工作室](debugging-with-visual-studio.md)，你測試它使用視覺化工作室調試器。</span><span class="sxs-lookup"><span data-stu-id="8de16-105">In [Debug your Hello World application with Visual Studio](debugging-with-visual-studio.md), you tested it using the Visual Studio debugger.</span></span> <span data-ttu-id="8de16-106">現在，您確定它會如預期般地運作，您可以發行，讓其他使用者也可以執行它。</span><span class="sxs-lookup"><span data-stu-id="8de16-106">Now that you're sure that it works as expected, you can publish it so that other users can run it.</span></span> <span data-ttu-id="8de16-107">發行會建立一組執行您的應用程式所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="8de16-107">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="8de16-108">要部署檔，請將它們複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="8de16-108">To deploy the files, copy them to the target machine.</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="8de16-109">發佈應用程式</span><span class="sxs-lookup"><span data-stu-id="8de16-109">Publish the app</span></span>

1. <span data-ttu-id="8de16-110">請確定 Visual Studio 正在組置您應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="8de16-110">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="8de16-111">如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。</span><span class="sxs-lookup"><span data-stu-id="8de16-111">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="8de16-113">按右鍵**HelloWorld**專案（不是 HelloWorld 解決方案），然後從功能表中選擇 **"發佈**"。</span><span class="sxs-lookup"><span data-stu-id="8de16-113">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span> <span data-ttu-id="8de16-114">（您還可以從主**生成**功能表中選擇 **"發佈 HelloWorld"。**</span><span class="sxs-lookup"><span data-stu-id="8de16-114">(You can also select **Publish HelloWorld** from the main **Build** menu.)</span></span>

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="8de16-116">在 **"選取發佈目標**"頁上，選擇 **"資料夾**"，然後選擇"**創建設定檔**"。</span><span class="sxs-lookup"><span data-stu-id="8de16-116">On the **Pick a publish target** page, select **Folder**, and then select **Create Profile**.</span></span>

   ![在視覺化工作室中選擇發佈目標](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="8de16-118">在 **"發佈"** 頁上，選擇 **"發佈**"。</span><span class="sxs-lookup"><span data-stu-id="8de16-118">On the **Publish** page, select **Publish**.</span></span>

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="8de16-120">檢查檔</span><span class="sxs-lookup"><span data-stu-id="8de16-120">Inspect the files</span></span>

<span data-ttu-id="8de16-121">發佈過程創建一個與框架相關的部署，這是一種部署類型，其中已發佈的應用程式在 .NET Core 支援的任何平臺上運行，系統上安裝了 .NET Core。</span><span class="sxs-lookup"><span data-stu-id="8de16-121">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on any platform supported by .NET Core with .NET Core installed on the system.</span></span> <span data-ttu-id="8de16-122">使用者可以通過按兩下可執行檔或從命令提示符發出`dotnet HelloWorld.dll`命令來運行已發佈的應用。</span><span class="sxs-lookup"><span data-stu-id="8de16-122">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="8de16-123">在以下步驟中，您將查看發佈過程創建的檔。</span><span class="sxs-lookup"><span data-stu-id="8de16-123">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="8de16-124">開啟命令提示字元。</span><span class="sxs-lookup"><span data-stu-id="8de16-124">Open a command prompt.</span></span>

   <span data-ttu-id="8de16-125">打開命令提示符的一種方法是在 Windows 工作列上的搜索框中輸入**命令提示**符（或簡稱**cmd）。**</span><span class="sxs-lookup"><span data-stu-id="8de16-125">One way to open a command prompt is to enter **Command Prompt** (or **cmd** for short) in the search box on the Windows taskbar.</span></span> <span data-ttu-id="8de16-126">選擇**命令提示**桌面應用，或按 **"如果**已在搜尋結果中選中"。"</span><span class="sxs-lookup"><span data-stu-id="8de16-126">Select the **Command Prompt** desktop app, or press **Enter** if it's already selected in the search results.</span></span>

1. <span data-ttu-id="8de16-127">導航到應用程式專案目錄的*bin_Release_netcoreapp3.1_發佈*子目錄中的已發佈應用程式。</span><span class="sxs-lookup"><span data-stu-id="8de16-127">Navigate to the published application in the *bin\Release\netcoreapp3.1\publish* subdirectory of the application's project directory.</span></span>

   ![主控台視窗顯示已發行的檔案](media/publishing-with-visual-studio/published-files-output.png)

   <span data-ttu-id="8de16-129">如圖所示，已發佈的輸出包括以下檔：</span><span class="sxs-lookup"><span data-stu-id="8de16-129">As the image shows, the published output includes the following files:</span></span>

      * <span data-ttu-id="8de16-130">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="8de16-130">*HelloWorld.deps.json*</span></span>

         <span data-ttu-id="8de16-131">這是應用程式的運行時依賴項檔。</span><span class="sxs-lookup"><span data-stu-id="8de16-131">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="8de16-132">它定義了 .NET Core 元件和運行應用程式所需的庫（包括包含應用程式的動態連結程式庫）。</span><span class="sxs-lookup"><span data-stu-id="8de16-132">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="8de16-133">有關詳細資訊，請參閱[運行時設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="8de16-133">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

      * <span data-ttu-id="8de16-134">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="8de16-134">*HelloWorld.dll*</span></span>

         <span data-ttu-id="8de16-135">這是應用程式[與框架相關的部署](../deploying/deploy-with-cli.md#framework-dependent-deployment)版本。</span><span class="sxs-lookup"><span data-stu-id="8de16-135">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="8de16-136">要執行此動態連結程式庫，`dotnet HelloWorld.dll`請輸入命令提示符。</span><span class="sxs-lookup"><span data-stu-id="8de16-136">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span>

      * <span data-ttu-id="8de16-137">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="8de16-137">*HelloWorld.exe*</span></span>

         <span data-ttu-id="8de16-138">這是應用程式[與框架相關的可執行](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。</span><span class="sxs-lookup"><span data-stu-id="8de16-138">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="8de16-139">要運行它，`HelloWorld.exe`請輸入命令提示符。</span><span class="sxs-lookup"><span data-stu-id="8de16-139">To run it, enter `HelloWorld.exe` at a command prompt.</span></span>

      * <span data-ttu-id="8de16-140">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="8de16-140">*HelloWorld.pdb* (optional for deployment)</span></span>

         <span data-ttu-id="8de16-141">這是調試符號檔。</span><span class="sxs-lookup"><span data-stu-id="8de16-141">This is the debug symbols file.</span></span> <span data-ttu-id="8de16-142">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="8de16-142">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

      * <span data-ttu-id="8de16-143">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="8de16-143">*HelloWorld.runtimeconfig.json*</span></span>

         <span data-ttu-id="8de16-144">這是應用程式的運行時設定檔。</span><span class="sxs-lookup"><span data-stu-id="8de16-144">This is the application's run-time configuration file.</span></span> <span data-ttu-id="8de16-145">它會識別建置您應用程式以在其上執行的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="8de16-145">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="8de16-146">您還可以向其添加配置選項。</span><span class="sxs-lookup"><span data-stu-id="8de16-146">You can also add configuration options to it.</span></span> <span data-ttu-id="8de16-147">有關詳細資訊，請參閱[.NET Core 運行時配置設置](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="8de16-147">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8de16-148">其他資源</span><span class="sxs-lookup"><span data-stu-id="8de16-148">Additional resources</span></span>

- [<span data-ttu-id="8de16-149">.NET 核心應用程式部署</span><span class="sxs-lookup"><span data-stu-id="8de16-149">.NET Core application deployment</span></span>](../deploying/index.md)
