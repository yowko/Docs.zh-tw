---
title: 使用 Visual Studio 發佈 .NET 主控台應用程式
description: 瞭解如何使用 Visual Studio 來建立執行 .NET 應用程式所需的一組檔案。
ms.date: 06/08/2020
dev_langs:
- csharp
- vb
ms.custom: vs-dotnet
ms.openlocfilehash: b0c6bd85ddf86f0eb11c56f01abb74a7e9786363
ms.sourcegitcommit: 5114e7847e0ff8ddb8c266802d47af78567949cf
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 11/19/2020
ms.locfileid: "94915997"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio"></a><span data-ttu-id="886a8-103">教學課程：使用 Visual Studio 發佈 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="886a8-103">Tutorial: Publish a .NET console application using Visual Studio</span></span>

<span data-ttu-id="886a8-104">本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。</span><span class="sxs-lookup"><span data-stu-id="886a8-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="886a8-105">發行會建立一組執行您的應用程式所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="886a8-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="886a8-106">若要部署檔案，請將檔案複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="886a8-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="886a8-107">先決條件</span><span class="sxs-lookup"><span data-stu-id="886a8-107">Prerequisites</span></span>

- <span data-ttu-id="886a8-108">本教學課程適用于您 [使用 Visual Studio 建立 .net 主控台應用程式](with-visual-studio.md)中所建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="886a8-108">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="886a8-109">發佈應用程式</span><span class="sxs-lookup"><span data-stu-id="886a8-109">Publish the app</span></span>

1. <span data-ttu-id="886a8-110">啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="886a8-110">Start Visual Studio.</span></span>

1. <span data-ttu-id="886a8-111">開啟您在 [使用 Visual Studio 建立 .net 主控台應用程式](with-visual-studio.md)中建立的 *HelloWorld* 專案。</span><span class="sxs-lookup"><span data-stu-id="886a8-111">Open the *HelloWorld* project that you created in [Create a .NET console application using Visual Studio](with-visual-studio.md).</span></span>

1. <span data-ttu-id="886a8-112">請確定 Visual Studio 使用發行組建設定。</span><span class="sxs-lookup"><span data-stu-id="886a8-112">Make sure that Visual Studio is using the Release build configuration.</span></span> <span data-ttu-id="886a8-113">如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。</span><span class="sxs-lookup"><span data-stu-id="886a8-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/visual-studio-toolbar-release.png" alt-text="選取 [發行] 組建的 Visual Studio 工具列":::

1. <span data-ttu-id="886a8-115">以滑鼠右鍵按一下 **HelloWorld** 專案， (不是 HelloWorld 方案) 然後從功能表中選取 [ **發行** ]。</span><span class="sxs-lookup"><span data-stu-id="886a8-115">Right-click on the **HelloWorld** project (not the HelloWorld solution) and select **Publish** from the menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-context-menu.png" alt-text="Visual Studio [發行] 操作功能表":::

1. <span data-ttu-id="886a8-117">在 [**發行**] 頁面的 [**目標**] 索引標籤上選取 [**資料夾**]，然後選取 **[下一步]**。</span><span class="sxs-lookup"><span data-stu-id="886a8-117">On the **Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/pick-publish-target.png" alt-text="在 Visual Studio 中挑選發佈目標":::

1. <span data-ttu-id="886a8-119">在 [**發行**] 頁面的 **特定目標** 索引標籤上，選取 [**資料夾**]，然後選取 **[下一步**]。</span><span class="sxs-lookup"><span data-stu-id="886a8-119">On the **Specific Target** tab of the **Publish** page, select **Folder**, and then select **Next**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/pick-specific-publish-target.png" alt-text="在 Visual Studio 中挑選特定的發佈目標":::

1. <span data-ttu-id="886a8-121">在 [**發行**] 頁面的 [**位置**] 索引標籤上，選取 **[完成]**。</span><span class="sxs-lookup"><span data-stu-id="886a8-121">On the **Location** tab of the **Publish** page, select **Finish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-page-loc-tab.png" alt-text="Visual Studio 發佈頁面位置] 索引標籤":::

1. <span data-ttu-id="886a8-123">在 [**發行**] 視窗的 [**發行**] 索引標籤上，選取 [**發行**]。</span><span class="sxs-lookup"><span data-stu-id="886a8-123">On the **Publish** tab of the **Publish** window, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/publish-page.png" alt-text="Visual Studio [發行] 視窗":::

## <a name="inspect-the-files"></a><span data-ttu-id="886a8-125">檢查檔案</span><span class="sxs-lookup"><span data-stu-id="886a8-125">Inspect the files</span></span>

<span data-ttu-id="886a8-126">根據預設，發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET 執行時間的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="886a8-126">By default, the publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on machine that has the .NET runtime installed.</span></span> <span data-ttu-id="886a8-127">使用者可以按兩下可執行檔，或從命令提示字元發出命令，以執行已發佈的應用程式 `dotnet HelloWorld.dll` 。</span><span class="sxs-lookup"><span data-stu-id="886a8-127">Users can run the published app by double-clicking the executable or issuing the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="886a8-128">在下列步驟中，您將查看發佈程式所建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="886a8-128">In the following steps, you'll look at the files created by the publish process.</span></span>

1. <span data-ttu-id="886a8-129">在 **方案總管** 中，選取 [ **顯示所有** 檔案]。</span><span class="sxs-lookup"><span data-stu-id="886a8-129">In **Solution Explorer**, select **Show all files**.</span></span>

1. <span data-ttu-id="886a8-130">在專案資料夾中，展開 *bin/Release/net 5.0/publish*。</span><span class="sxs-lookup"><span data-stu-id="886a8-130">In the project folder, expand *bin/Release/net5.0/publish*.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio/published-files-output.png" alt-text="顯示已發佈檔案方案總管":::

   <span data-ttu-id="886a8-132">如圖所示，已發行的輸出包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="886a8-132">As the image shows, the published output includes the following files:</span></span>

   * <span data-ttu-id="886a8-133">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="886a8-133">*HelloWorld.deps.json*</span></span>

      <span data-ttu-id="886a8-134">這是應用程式的執行時間相依性檔案。</span><span class="sxs-lookup"><span data-stu-id="886a8-134">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="886a8-135">它會定義 .NET 元件和程式庫 (包括動態連結程式庫，其中包含執行應用程式所需的應用程式) 。</span><span class="sxs-lookup"><span data-stu-id="886a8-135">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="886a8-136">如需詳細資訊，請參閱 [執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="886a8-136">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

   * <span data-ttu-id="886a8-137">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="886a8-137">*HelloWorld.dll*</span></span>

      <span data-ttu-id="886a8-138">這是應用程式的 [framework 相依部署](../deploying/deploy-with-cli.md#framework-dependent-deployment) 版本。</span><span class="sxs-lookup"><span data-stu-id="886a8-138">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="886a8-139">若要執行這個動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。</span><span class="sxs-lookup"><span data-stu-id="886a8-139">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="886a8-140">執行應用程式的這個方法適用于已安裝 .NET 執行時間的任何平臺。</span><span class="sxs-lookup"><span data-stu-id="886a8-140">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

   * <span data-ttu-id="886a8-141">*HelloWorld.exe*</span><span class="sxs-lookup"><span data-stu-id="886a8-141">*HelloWorld.exe*</span></span>

      <span data-ttu-id="886a8-142">這是應用程式的 [framework 相依可執行檔](../deploying/deploy-with-cli.md#framework-dependent-executable) 版本。</span><span class="sxs-lookup"><span data-stu-id="886a8-142">This is the [framework-dependent executable](../deploying/deploy-with-cli.md#framework-dependent-executable) version of the application.</span></span> <span data-ttu-id="886a8-143">若要執行，請 `HelloWorld.exe` 在命令提示字元中輸入。</span><span class="sxs-lookup"><span data-stu-id="886a8-143">To run it, enter `HelloWorld.exe` at a command prompt.</span></span> <span data-ttu-id="886a8-144">檔案是作業系統特定的。</span><span class="sxs-lookup"><span data-stu-id="886a8-144">The file is operating-system-specific.</span></span>

   * <span data-ttu-id="886a8-145">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="886a8-145">*HelloWorld.pdb* (optional for deployment)</span></span>

      <span data-ttu-id="886a8-146">這是 debug 符號檔。</span><span class="sxs-lookup"><span data-stu-id="886a8-146">This is the debug symbols file.</span></span> <span data-ttu-id="886a8-147">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="886a8-147">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

   * <span data-ttu-id="886a8-148">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="886a8-148">*HelloWorld.runtimeconfig.json*</span></span>

      <span data-ttu-id="886a8-149">這是應用程式的執行時間設定檔案。</span><span class="sxs-lookup"><span data-stu-id="886a8-149">This is the application's run-time configuration file.</span></span> <span data-ttu-id="886a8-150">它會識別您的應用程式建立用來執行的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="886a8-150">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="886a8-151">您也可以將設定選項新增至其中。</span><span class="sxs-lookup"><span data-stu-id="886a8-151">You can also add configuration options to it.</span></span> <span data-ttu-id="886a8-152">如需詳細資訊，請參閱 [.net 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="886a8-152">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="886a8-153">執行已發佈的應用程式</span><span class="sxs-lookup"><span data-stu-id="886a8-153">Run the published app</span></span>

1. <span data-ttu-id="886a8-154">在 **方案總管** 中，以滑鼠右鍵按一下 [ *發佈* ] 資料夾，然後選取 [ **複製完整路徑**]。</span><span class="sxs-lookup"><span data-stu-id="886a8-154">In **Solution Explorer**, right-click the *publish* folder, and select **Copy Full Path**.</span></span>

1. <span data-ttu-id="886a8-155">開啟命令提示字元，然後流覽至 [ *發佈* ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="886a8-155">Open a command prompt and navigate to the *publish* folder.</span></span> <span data-ttu-id="886a8-156">若要這樣做，請輸入， `cd` 然後貼上完整的路徑。</span><span class="sxs-lookup"><span data-stu-id="886a8-156">To do that, enter `cd` and then paste the full path.</span></span> <span data-ttu-id="886a8-157">例如：</span><span class="sxs-lookup"><span data-stu-id="886a8-157">For example:</span></span>

   ```console
   cd C:\Projects\HelloWorld\bin\Release\netcoreapp3.1\publish\
   ```

1. <span data-ttu-id="886a8-158">使用可執行檔來執行應用程式：</span><span class="sxs-lookup"><span data-stu-id="886a8-158">Run the app by using the executable:</span></span>

   1. <span data-ttu-id="886a8-159">輸入 `HelloWorld.exe` ，然後按 <kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="886a8-159">Enter `HelloWorld.exe` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="886a8-160">輸入名稱以回應提示，然後按任意鍵以結束。</span><span class="sxs-lookup"><span data-stu-id="886a8-160">Enter a name in response to the prompt, and press any key to exit.</span></span>

1. <span data-ttu-id="886a8-161">使用下列命令來執行應用程式 `dotnet` ：</span><span class="sxs-lookup"><span data-stu-id="886a8-161">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="886a8-162">輸入 `dotnet HelloWorld.dll` ，然後按 <kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="886a8-162">Enter `dotnet HelloWorld.dll` and press <kbd>Enter</kbd>.</span></span>

   1. <span data-ttu-id="886a8-163">輸入名稱以回應提示，然後按任意鍵以結束。</span><span class="sxs-lookup"><span data-stu-id="886a8-163">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="886a8-164">其他資源</span><span class="sxs-lookup"><span data-stu-id="886a8-164">Additional resources</span></span>

- [<span data-ttu-id="886a8-165">.NET 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="886a8-165">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="886a8-166">後續步驟</span><span class="sxs-lookup"><span data-stu-id="886a8-166">Next steps</span></span>

<span data-ttu-id="886a8-167">在本教學課程中，您已發佈主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="886a8-167">In this tutorial, you published a console app.</span></span> <span data-ttu-id="886a8-168">在下一個教學課程中，您將建立類別庫。</span><span class="sxs-lookup"><span data-stu-id="886a8-168">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="886a8-169">使用 Visual Studio 建立 .NET 類別庫</span><span class="sxs-lookup"><span data-stu-id="886a8-169">Create a .NET class library using Visual Studio</span></span>](library-with-visual-studio.md)
