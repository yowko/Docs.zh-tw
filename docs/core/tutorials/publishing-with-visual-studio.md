---
title: 使用 Visual Studio 發行 .NET Core 主控台應用程式
description: 發行會建立一組執行 .NET Core 應用程式所需的檔案。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: 44646a307d230db395b55b9dec5acfd168605940
ms.sourcegitcommit: 1cbd77da54405ea7dba343ac0334fb03237d25d2
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 06/11/2020
ms.locfileid: "84701280"
---
# <a name="tutorial-publish-a-net-core-console-application-using-visual-studio"></a><span data-ttu-id="e6781-103">教學課程：使用 Visual Studio 發行 .NET Core 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="e6781-103">Tutorial: Publish a .NET Core console application using Visual Studio</span></span>

<span data-ttu-id="e6781-104">本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。</span><span class="sxs-lookup"><span data-stu-id="e6781-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="e6781-105">發行會建立一組執行您的應用程式所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6781-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="e6781-106">若要部署檔案，請將檔案複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="e6781-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e6781-107">Prerequisites</span><span class="sxs-lookup"><span data-stu-id="e6781-107">Prerequisites</span></span>

- <span data-ttu-id="e6781-108">本教學課程適用于您在[Visual Studio 2019 的建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6781-108">This tutorial works with the console app that you create in [Create a .NET Core console application in Visual Studio 2019](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="e6781-109">發佈應用程式</span><span class="sxs-lookup"><span data-stu-id="e6781-109">Publish the app</span></span>

1. <span data-ttu-id="e6781-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e6781-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="e6781-111">開啟您在[Visual Studio 中建立 .Net Core 主控台應用程式](with-visual-studio.md)中建立的*HelloWorld*專案。</span><span class="sxs-lookup"><span data-stu-id="e6781-111">Open the *HelloWorld* project that you created in [Create a .NET Core console application in Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="e6781-112">請確定 Visual Studio 使用的是發行組建設定。</span><span class="sxs-lookup"><span data-stu-id="e6781-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="e6781-113">如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。</span><span class="sxs-lookup"><span data-stu-id="e6781-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   ![選取 [發行] 組建的 Visual Studio 工具列](media/publishing-with-visual-studio/visual-studio-toolbar-release.png)

1. <span data-ttu-id="e6781-115">以滑鼠右鍵按一下**HelloWorld**專案（而非 HelloWorld 方案），然後從功能表中選取 [**發佈**]。</span><span class="sxs-lookup"><span data-stu-id="e6781-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   ![Visual Studio [發行] 操作功能表](media/publishing-with-visual-studio/publish-context-menu.png)

1. <span data-ttu-id="e6781-117">在**發行**頁面的 [**目標**] 索引標籤上，選取 [**資料夾**]，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="e6781-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   ![在 Visual Studio 中挑選發行目標](media/publishing-with-visual-studio/pick-publish-target.png)

1. <span data-ttu-id="e6781-119">在 [**發佈**] 頁面的 [**位置**] 索引標籤上，選取 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="e6781-119">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   ![Visual Studio 發行頁面位置] 索引標籤](media/publishing-with-visual-studio/publish-page-loc-tab.png)

1. <span data-ttu-id="e6781-121">在 **[發行] 視窗的**[**發行**] 索引標籤上，選取 [**發佈**]。</span><span class="sxs-lookup"><span data-stu-id="e6781-121">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   ![Visual Studio [發行] 視窗](media/publishing-with-visual-studio/publish-page.png)

## <a name="inspect-the-files"></a><span data-ttu-id="e6781-123">檢查檔案</span><span class="sxs-lookup"><span data-stu-id="e6781-123">Inspect the files</span></span>

<span data-ttu-id="e6781-124">根據預設，發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET Core 執行時間的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="e6781-124">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET Core runtime installed.</span></span> <span data-ttu-id="e6781-125">使用者可以按兩下可執行檔，或從命令提示字元發出命令，以執行已發佈的應用程式 `dotnet HelloWorld.dll` 。</span><span class="sxs-lookup"><span data-stu-id="e6781-125">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="e6781-126">在下列步驟中，您將查看發行程式所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6781-126">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="e6781-127">在**方案總管**中，選取 [**顯示所有**檔案]。</span><span class="sxs-lookup"><span data-stu-id="e6781-127">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="e6781-128">在專案資料夾中，展開 [ *bin/Release/netcoreapp 3.1/publish*]。</span><span class="sxs-lookup"><span data-stu-id="e6781-128">In the project folder, expand *bin/Release/netcoreapp3.1/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="顯示已發佈檔案的方案總管":::

   <span data-ttu-id="e6781-130">如圖所示，已發行的輸出會包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="e6781-130">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="e6781-131">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="e6781-131">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="e6781-132">這是應用程式的執行時間相依性檔案。</span><span class="sxs-lookup"><span data-stu-id="e6781-132">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="e6781-133">它會定義執行應用程式所需的 .NET Core 元件和程式庫（包括包含您應用程式的動態連結程式庫）。</span><span class="sxs-lookup"><span data-stu-id="e6781-133">It defines the .NET Core components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="e6781-134">如需詳細資訊，請參閱[執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="e6781-134">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="e6781-135">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="e6781-135">*HelloWorld.dll*</span></span>

      <span data-ttu-id="e6781-136">這是與[framework 相依](../deploying/deploy-with-cli.md#framework-dependent-deployment)的應用程式部署版本。</span><span class="sxs-lookup"><span data-stu-id="e6781-136">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="e6781-137">若要執行此動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。</span><span class="sxs-lookup"><span data-stu-id="e6781-137">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="e6781-138">這種執行應用程式的方法可在已安裝 .NET Core 執行時間的任何平臺上運作。</span><span class="sxs-lookup"><span data-stu-id="e6781-138">This method of running the app works on any platform that has the .NET Core runtime installed.</span></span>

   * <span data-ttu-id="e6781-139">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="e6781-139">*HelloWorld.exe*</span></span>

      <span data-ttu-id="e6781-140">這是與[framework 相依的應用程式可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable)版本。</span><span class="sxs-lookup"><span data-stu-id="e6781-140">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="e6781-141">若要執行，請 `HelloWorld.exe` 在命令提示字元中輸入。</span><span class="sxs-lookup"><span data-stu-id="e6781-141">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="e6781-142">檔案是作業系統特定的檔案。</span><span class="sxs-lookup"><span data-stu-id="e6781-142">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="e6781-143">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="e6781-143">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="e6781-144">這是 debug 符號檔案。</span><span class="sxs-lookup"><span data-stu-id="e6781-144">This is the debug symbols file.</span></span> <span data-ttu-id="e6781-145">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="e6781-145">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="e6781-146">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="e6781-146">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="e6781-147">這是應用程式的執行時間設定檔。</span><span class="sxs-lookup"><span data-stu-id="e6781-147">This is the application's run-time configuration file.</span></span> <span data-ttu-id="e6781-148">它會識別建置您應用程式以在其上執行的 .NET Core 版本。</span><span class="sxs-lookup"><span data-stu-id="e6781-148">It identifies the version of .NET Core that your application was built to run on.</span></span> <span data-ttu-id="e6781-149">您也可以在其中新增設定選項。</span><span class="sxs-lookup"><span data-stu-id="e6781-149">You can also add configuration options to it.</span></span> <span data-ttu-id="e6781-150">如需詳細資訊，請參閱[.Net Core 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="e6781-150">For more information, see [.NET Core run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="e6781-151">執行已發佈的應用程式</span><span class="sxs-lookup"><span data-stu-id="e6781-151">Run the published app</span></span>

1. <span data-ttu-id="e6781-152">在**方案總管**中，以滑鼠右鍵按一下 [*發行*] 資料夾，然後選取 [**複製完整路徑**]。</span><span class="sxs-lookup"><span data-stu-id="e6781-152">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="e6781-153">開啟命令提示字元，並流覽至 [*發行*] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e6781-153">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="e6781-154">若要這麼做，請輸入 `cd` ，然後貼上完整路徑。</span><span class="sxs-lookup"><span data-stu-id="e6781-154">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="e6781-155">例如：</span><span class="sxs-lookup"><span data-stu-id="e6781-155">For example:</span></span>

   ```
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="e6781-156">使用可執行檔來執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="e6781-156">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="e6781-157">輸入 `HelloWorld.exe` ，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="e6781-157">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="e6781-158">輸入名稱以回應提示，然後按任意鍵結束。</span><span class="sxs-lookup"><span data-stu-id="e6781-158">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="e6781-159">使用命令執行應用程式 `dotnet` ：</span><span class="sxs-lookup"><span data-stu-id="e6781-159">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="e6781-160">輸入 `dotnet HelloWorld.dll` ，然後按<kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="e6781-160">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="e6781-161">輸入名稱以回應提示，然後按任意鍵結束。</span><span class="sxs-lookup"><span data-stu-id="e6781-161">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e6781-162">其他資源</span><span class="sxs-lookup"><span data-stu-id="e6781-162">Additional resources</span></span>

- [<span data-ttu-id="e6781-163">.NET Core 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="e6781-163">.NET Core application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="e6781-164">後續步驟</span><span class="sxs-lookup"><span data-stu-id="e6781-164">Next steps</span></span>

<span data-ttu-id="e6781-165">在本教學課程中，您已發佈主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="e6781-165">In this tutorial, you published a console app.</span></span> <span data-ttu-id="e6781-166">在下一個教學課程中，您會建立類別庫。</span><span class="sxs-lookup"><span data-stu-id="e6781-166">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="e6781-167">在 Visual Studio 中建立 .NET Standard 程式庫</span><span class="sxs-lookup"><span data-stu-id="e6781-167">Create a .NET Standard library in Visual Studio</span></span>](library-with-visual-studio.md)
