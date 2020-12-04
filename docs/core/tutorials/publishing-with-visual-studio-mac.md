---
title: 使用 Visual Studio for Mac 發佈 .NET 主控台應用程式
description: 瞭解如何使用 Visual Studio for Mac 來建立執行 .NET 應用程式所需的一組檔案。
ms.date: 11/30/2020
ms.openlocfilehash: 88f143011b19ca8eda6610803c894e619d06a635
ms.sourcegitcommit: 9d525bb8109216ca1dc9e39c149d4902f4b43da5
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/04/2020
ms.locfileid: "96599178"
---
# <a name="tutorial-publish-a-net-console-application-using-visual-studio-for-mac"></a><span data-ttu-id="1e459-103">教學課程：使用 Visual Studio for Mac 發佈 .NET 主控台應用程式</span><span class="sxs-lookup"><span data-stu-id="1e459-103">Tutorial: Publish a .NET console application using Visual Studio for Mac</span></span>

<span data-ttu-id="1e459-104">本教學課程說明如何發佈主控台應用程式，讓其他使用者可以執行它。</span><span class="sxs-lookup"><span data-stu-id="1e459-104">This tutorial shows how to publish a console app so that other users can run it.</span></span> <span data-ttu-id="1e459-105">發行會建立一組執行您的應用程式所需的檔案。</span><span class="sxs-lookup"><span data-stu-id="1e459-105">Publishing creates the set of files that are needed to run your application.</span></span> <span data-ttu-id="1e459-106">若要部署檔案，請將檔案複製到目的電腦。</span><span class="sxs-lookup"><span data-stu-id="1e459-106">To deploy the files, copy them to the target machine.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="1e459-107">必要條件</span><span class="sxs-lookup"><span data-stu-id="1e459-107">Prerequisites</span></span>

- <span data-ttu-id="1e459-108">本教學課程適用于您 [使用 Visual Studio for Mac 建立 .net 主控台應用程式](with-visual-studio-mac.md)中所建立的主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e459-108">This tutorial works with the console app that you create in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

## <a name="publish-the-app"></a><span data-ttu-id="1e459-109">發佈應用程式</span><span class="sxs-lookup"><span data-stu-id="1e459-109">Publish the app</span></span>

1. <span data-ttu-id="1e459-110">開始 Visual Studio for Mac。</span><span class="sxs-lookup"><span data-stu-id="1e459-110">Start Visual Studio for Mac.</span></span>

1. <span data-ttu-id="1e459-111">開啟您在 [使用 Visual Studio for Mac 建立 .net 主控台應用程式](with-visual-studio-mac.md)中建立的 HelloWorld 專案。</span><span class="sxs-lookup"><span data-stu-id="1e459-111">Open the HelloWorld project that you created in [Create a .NET console application using Visual Studio for Mac](with-visual-studio-mac.md).</span></span>

1. <span data-ttu-id="1e459-112">請確定 Visual Studio 正在組置您應用程式的發行版本。</span><span class="sxs-lookup"><span data-stu-id="1e459-112">Make sure that Visual Studio is building the Release version of your application.</span></span> <span data-ttu-id="1e459-113">如有必要，請將工具列上的組建組態設定從 **[偵錯]** 變更為 **[發行]**。</span><span class="sxs-lookup"><span data-stu-id="1e459-113">If necessary, change the build configuration setting on the toolbar from **Debug** to **Release**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/toolbar-release.png" alt-text="選取 [發行] 組建的 Visual Studio 工具列":::

1. <span data-ttu-id="1e459-115">從主功能表中，選擇 [**組建**  >  **發行至資料夾 ...**]。</span><span class="sxs-lookup"><span data-stu-id="1e459-115">From the main menu, choose **Build** > **Publish to Folder...**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-context-menu.png" alt-text="Visual Studio [發行] 操作功能表":::

1. <span data-ttu-id="1e459-117">在 [ **發行至資料夾** ] 對話方塊中，選取 [ **發行**]。</span><span class="sxs-lookup"><span data-stu-id="1e459-117">In the **Publish to Folder** dialog, select **Publish**.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-to-folder-dialog.png" alt-text="Visual Studio 發佈到資料夾] 對話方塊":::

   <span data-ttu-id="1e459-119">[發行] 資料夾隨即開啟，其中會顯示已建立的檔案。</span><span class="sxs-lookup"><span data-stu-id="1e459-119">The publish folder opens, showing the files that were created.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/publish-folder.png" alt-text="發佈資料夾":::

1. <span data-ttu-id="1e459-121">選取齒輪圖示，然後從操作功能表中選取 [ **發佈] 作為路徑名稱** 。</span><span class="sxs-lookup"><span data-stu-id="1e459-121">Select the gear icon, and select **Copy "publish" as Pathname** from the context menu.</span></span>

   :::image type="content" source="media/publishing-with-visual-studio-mac/copy-path.png" alt-text="複製發佈資料夾的路徑":::

## <a name="inspect-the-files"></a><span data-ttu-id="1e459-123">檢查檔案</span><span class="sxs-lookup"><span data-stu-id="1e459-123">Inspect the files</span></span>

<span data-ttu-id="1e459-124">發佈程式會建立與 framework 相依的部署，這是一種部署類型，其中已發佈的應用程式會在已安裝 .NET 執行時間的電腦上執行。</span><span class="sxs-lookup"><span data-stu-id="1e459-124">The publishing process creates a framework-dependent deployment, which is a type of deployment where the published application runs on a machine that has the .NET runtime installed.</span></span> <span data-ttu-id="1e459-125">使用者可以從命令提示字元執行命令，以執行已發佈的應用程式 `dotnet HelloWorld.dll` 。</span><span class="sxs-lookup"><span data-stu-id="1e459-125">Users can run the published app by running the `dotnet HelloWorld.dll` command from a command prompt.</span></span>

<span data-ttu-id="1e459-126">如上圖所示，已發行的輸出包含下列檔案：</span><span class="sxs-lookup"><span data-stu-id="1e459-126">As the preceding image shows, the published output includes the following files:</span></span>

* <span data-ttu-id="1e459-127">*HelloWorld.deps.json*</span><span class="sxs-lookup"><span data-stu-id="1e459-127">*HelloWorld.deps.json*</span></span>

  <span data-ttu-id="1e459-128">這是應用程式的執行時間相依性檔案。</span><span class="sxs-lookup"><span data-stu-id="1e459-128">This is the application's runtime dependencies file.</span></span> <span data-ttu-id="1e459-129">它會定義 .NET 元件和程式庫 (包括動態連結程式庫，其中包含執行應用程式所需的應用程式) 。</span><span class="sxs-lookup"><span data-stu-id="1e459-129">It defines the .NET components and the libraries (including the dynamic link library that contains your application) needed to run the app.</span></span> <span data-ttu-id="1e459-130">如需詳細資訊，請參閱 [執行時間設定檔](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md)。</span><span class="sxs-lookup"><span data-stu-id="1e459-130">For more information, see [Runtime configuration files](https://github.com/dotnet/cli/blob/85ca206d84633d658d7363894c4ea9d59e515c1a/Documentation/specs/runtime-configuration-file.md).</span></span>

* <span data-ttu-id="1e459-131">*HelloWorld.dll*</span><span class="sxs-lookup"><span data-stu-id="1e459-131">*HelloWorld.dll*</span></span>

   <span data-ttu-id="1e459-132">這是應用程式的 [framework 相依部署](../deploying/deploy-with-cli.md#framework-dependent-deployment) 版本。</span><span class="sxs-lookup"><span data-stu-id="1e459-132">This is the [framework-dependent deployment](../deploying/deploy-with-cli.md#framework-dependent-deployment) version of the application.</span></span> <span data-ttu-id="1e459-133">若要執行這個動態連結程式庫，請 `dotnet HelloWorld.dll` 在命令提示字元中輸入。</span><span class="sxs-lookup"><span data-stu-id="1e459-133">To execute this dynamic link library, enter `dotnet HelloWorld.dll` at a command prompt.</span></span> <span data-ttu-id="1e459-134">執行應用程式的這個方法適用于已安裝 .NET 執行時間的任何平臺。</span><span class="sxs-lookup"><span data-stu-id="1e459-134">This method of running the app works on any platform that has the .NET runtime installed.</span></span>

* <span data-ttu-id="1e459-135">*HelloWorld.pdb* (對於部署為選用)</span><span class="sxs-lookup"><span data-stu-id="1e459-135">*HelloWorld.pdb* (optional for deployment)</span></span>

   <span data-ttu-id="1e459-136">這是 debug 符號檔。</span><span class="sxs-lookup"><span data-stu-id="1e459-136">This is the debug symbols file.</span></span> <span data-ttu-id="1e459-137">此檔案不需要隨您的應用程式部署，但當您需要對應用程式發行的版本進行偵錯，則應該儲存它。</span><span class="sxs-lookup"><span data-stu-id="1e459-137">You aren't required to deploy this file along with your application, although you should save it in the event that you need to debug the published version of your application.</span></span>

* <span data-ttu-id="1e459-138">*HelloWorld.runtimeconfig.json*</span><span class="sxs-lookup"><span data-stu-id="1e459-138">*HelloWorld.runtimeconfig.json*</span></span>

   <span data-ttu-id="1e459-139">這是應用程式的執行時間設定檔案。</span><span class="sxs-lookup"><span data-stu-id="1e459-139">This is the application's run-time configuration file.</span></span> <span data-ttu-id="1e459-140">它會識別您的應用程式建立用來執行的 .NET 版本。</span><span class="sxs-lookup"><span data-stu-id="1e459-140">It identifies the version of .NET that your application was built to run on.</span></span> <span data-ttu-id="1e459-141">您也可以將設定選項新增至其中。</span><span class="sxs-lookup"><span data-stu-id="1e459-141">You can also add configuration options to it.</span></span> <span data-ttu-id="1e459-142">如需詳細資訊，請參閱 [.net 執行時間設定](../run-time-config/index.md#runtimeconfigjson)。</span><span class="sxs-lookup"><span data-stu-id="1e459-142">For more information, see [.NET run-time configuration settings](../run-time-config/index.md#runtimeconfigjson).</span></span>

## <a name="run-the-published-app"></a><span data-ttu-id="1e459-143">執行已發佈的應用程式</span><span class="sxs-lookup"><span data-stu-id="1e459-143">Run the published app</span></span>

1. <span data-ttu-id="1e459-144">開啟終端機，然後流覽至 [ *發佈* ] 資料夾。</span><span class="sxs-lookup"><span data-stu-id="1e459-144">Open a terminal and navigate to the *publish* folder.</span></span> <span data-ttu-id="1e459-145">若要這樣做，請輸入 `cd` 並貼上您先前複製的路徑。</span><span class="sxs-lookup"><span data-stu-id="1e459-145">To do that, enter `cd` and then paste the path that you copied earlier.</span></span> <span data-ttu-id="1e459-146">例如：</span><span class="sxs-lookup"><span data-stu-id="1e459-146">For example:</span></span>

   ```console
   cd ~/Projects/HelloWorld/HelloWorld/bin/Release/net5.0/publish/
   ```

1. <span data-ttu-id="1e459-147">使用下列命令來執行應用程式 `dotnet` ：</span><span class="sxs-lookup"><span data-stu-id="1e459-147">Run the app by using the `dotnet` command:</span></span>

   1. <span data-ttu-id="1e459-148">輸入 `dotnet HelloWorld.dll` ，然後按 <kbd>enter</kbd>鍵。</span><span class="sxs-lookup"><span data-stu-id="1e459-148">Enter `dotnet HelloWorld.dll` and press <kbd>enter</kbd>.</span></span>

   1. <span data-ttu-id="1e459-149">輸入名稱以回應提示，然後按任意鍵以結束。</span><span class="sxs-lookup"><span data-stu-id="1e459-149">Enter a name in response to the prompt, and press any key to exit.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="1e459-150">其他資源</span><span class="sxs-lookup"><span data-stu-id="1e459-150">Additional resources</span></span>

- [<span data-ttu-id="1e459-151">.NET 應用程式部署</span><span class="sxs-lookup"><span data-stu-id="1e459-151">.NET application deployment</span></span>](../deploying/index.md)

## <a name="next-steps"></a><span data-ttu-id="1e459-152">後續步驟</span><span class="sxs-lookup"><span data-stu-id="1e459-152">Next steps</span></span>

<span data-ttu-id="1e459-153">在本教學課程中，您已發佈主控台應用程式。</span><span class="sxs-lookup"><span data-stu-id="1e459-153">In this tutorial, you published a console app.</span></span> <span data-ttu-id="1e459-154">在下一個教學課程中，您將建立類別庫。</span><span class="sxs-lookup"><span data-stu-id="1e459-154">In the next tutorial, you create a class library.</span></span>

> [!div class="nextstepaction"]
> [<span data-ttu-id="1e459-155">使用 Visual Studio for Mac 建立 .NET 程式庫</span><span class="sxs-lookup"><span data-stu-id="1e459-155">Create a .NET library using Visual Studio for Mac</span></span>](library-with-visual-studio-mac.md)
