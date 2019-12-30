---
title: 安裝當地語系化的 IntelliSense 檔案
description: 了解如何設定開發電腦，以在 Visual Studio 中使用 .NET Core 專案的當地語系化 IntelliSense 檔案。
author: mairaw
ms.author: mairaw
ms.date: 12/18/2019
ms.openlocfilehash: 98d75544ab853e75c175dd2919991b250cfaa3b0
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: zh-TW
ms.lasthandoff: 12/25/2019
ms.locfileid: "75443474"
---
# <a name="how-to-install-localized-intellisense-files-for-net-core"></a><span data-ttu-id="e5174-103">如何安裝 .NET Core 的當地語系化 IntelliSense 檔案</span><span class="sxs-lookup"><span data-stu-id="e5174-103">How to install localized IntelliSense files for .NET Core</span></span>

<span data-ttu-id="e5174-104">[IntelliSense](/visualstudio/ide/using-intellisense) 是一種可在不同整合式開發環境 (IDE)，例如 Visual Studio 中使用的程式碼完成輔助工具。</span><span class="sxs-lookup"><span data-stu-id="e5174-104">[IntelliSense](/visualstudio/ide/using-intellisense) is a code-completion aid that is available in different integrated development environments (IDEs), such as Visual Studio.</span></span> <span data-ttu-id="e5174-105">根據預設，在開發 .NET Core 專案時，SDK 只會包含 IntelliSense 檔案的英文版本。</span><span class="sxs-lookup"><span data-stu-id="e5174-105">By default, when you're developing .NET Core projects, the SDK only includes the English version of the IntelliSense files.</span></span> <span data-ttu-id="e5174-106">本文說明：</span><span class="sxs-lookup"><span data-stu-id="e5174-106">This article explains:</span></span>

- <span data-ttu-id="e5174-107">如何安裝這些檔案的當地語系化版本。</span><span class="sxs-lookup"><span data-stu-id="e5174-107">How to install the localized version of those files.</span></span>
- <span data-ttu-id="e5174-108">如何修改 Visual Studio 安裝以使用不同語言。</span><span class="sxs-lookup"><span data-stu-id="e5174-108">How to modify the Visual Studio installation to use a different language.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e5174-109">必要條件</span><span class="sxs-lookup"><span data-stu-id="e5174-109">Prerequisites</span></span>

- <span data-ttu-id="e5174-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e5174-110">[.NET Core 3.0 SDK](https://dotnet.microsoft.com/download/dotnet-core) or a later version.</span></span>
- <span data-ttu-id="e5174-111">[Visual Studio 2019 版本 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) 或更新版本。</span><span class="sxs-lookup"><span data-stu-id="e5174-111">[Visual Studio 2019 version 16.3](https://visualstudio.microsoft.com/downloads/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link&utm_content=download+vs2019) or a later version.</span></span>

## <a name="download-and-install-the-localized-intellisense-files"></a><span data-ttu-id="e5174-112">下載及安裝當地語系化 IntelliSense 檔案</span><span class="sxs-lookup"><span data-stu-id="e5174-112">Download and install the localized IntelliSense files</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5174-113">此程序需要具備將 IntelliSense 檔案複製到 .NET Core 安裝資料夾的系統管理員權限。</span><span class="sxs-lookup"><span data-stu-id="e5174-113">This procedure requires that you have administrator permission to copy the IntelliSense files to the .NET Core installation folder.</span></span>

1. <span data-ttu-id="e5174-114">前往[下載 IntelliSense 檔案](https://dotnet.microsoft.com/download/dotnet-core/intellisense)頁面。</span><span class="sxs-lookup"><span data-stu-id="e5174-114">Go to the [Download IntelliSense files](https://dotnet.microsoft.com/download/dotnet-core/intellisense) page.</span></span>

1. <span data-ttu-id="e5174-115">下載要使用的 IntelliSense 語言及版本檔案。</span><span class="sxs-lookup"><span data-stu-id="e5174-115">Download the IntelliSense file for the language and version you'd like to use.</span></span>

1. <span data-ttu-id="e5174-116">解壓縮 ZIP 檔案的內容。</span><span class="sxs-lookup"><span data-stu-id="e5174-116">Extract the contents of the zip file.</span></span>

1. <span data-ttu-id="e5174-117">巡覽至 .NET Core 安裝資料夾。</span><span class="sxs-lookup"><span data-stu-id="e5174-117">Navigate to the .NET Core installation folder.</span></span> <span data-ttu-id="e5174-118">根據預設，其位於 *%ProgramFiles%\dotnet\packs*。</span><span class="sxs-lookup"><span data-stu-id="e5174-118">By default, it's under *%ProgramFiles%\dotnet\packs*.</span></span>

   - <span data-ttu-id="e5174-119">選擇要為其安裝 IntelliSense 的 SDK，然後巡覽至相關聯的路徑。</span><span class="sxs-lookup"><span data-stu-id="e5174-119">Choose which SDK you want to install the IntelliSense for, and navigate to the associated path.</span></span> <span data-ttu-id="e5174-120">下列選項可供您選擇：</span><span class="sxs-lookup"><span data-stu-id="e5174-120">You have the following options:</span></span>

      | <span data-ttu-id="e5174-121">SDK 類型</span><span class="sxs-lookup"><span data-stu-id="e5174-121">SDK type</span></span>        | <span data-ttu-id="e5174-122">路徑</span><span class="sxs-lookup"><span data-stu-id="e5174-122">Path</span></span>                               |
      | --------------- | ---------------------------------- |
      | <span data-ttu-id="e5174-123">.NET Core</span><span class="sxs-lookup"><span data-stu-id="e5174-123">.NET Core</span></span>       | <span data-ttu-id="e5174-124">*Microsoft.NETCore.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="e5174-124">*Microsoft.NETCore.App.Ref*</span></span>        |
      | <span data-ttu-id="e5174-125">Windows 桌面</span><span class="sxs-lookup"><span data-stu-id="e5174-125">Windows Desktop</span></span> | <span data-ttu-id="e5174-126">*Microsoft.WindowsDesktop.App.Ref*</span><span class="sxs-lookup"><span data-stu-id="e5174-126">*Microsoft.WindowsDesktop.App.Ref*</span></span> |
      | <span data-ttu-id="e5174-127">.NET Standard</span><span class="sxs-lookup"><span data-stu-id="e5174-127">.NET Standard</span></span>   | <span data-ttu-id="e5174-128">*NETStandard.Library.Ref*</span><span class="sxs-lookup"><span data-stu-id="e5174-128">*NETStandard.Library.Ref*</span></span>          |
   
   - <span data-ttu-id="e5174-129">巡覽至要為其安裝當地語系化 IntelliSense 的版本。</span><span class="sxs-lookup"><span data-stu-id="e5174-129">Navigate to the version you want to install the localized IntelliSense for.</span></span> <span data-ttu-id="e5174-130">例如，*3.1.0*。</span><span class="sxs-lookup"><span data-stu-id="e5174-130">For example, *3.1.0*.</span></span>
   - <span data-ttu-id="e5174-131">開啟 *ref* 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e5174-131">Open the *ref* folder.</span></span>
   - <span data-ttu-id="e5174-132">開啟 Moniker 資料夾。</span><span class="sxs-lookup"><span data-stu-id="e5174-132">Open the moniker folder.</span></span> <span data-ttu-id="e5174-133">例如，*netcoreapp3.1*。</span><span class="sxs-lookup"><span data-stu-id="e5174-133">For example, *netcoreapp3.1*.</span></span>

   <span data-ttu-id="e5174-134">因此，您巡覽的目標完整路徑看起來會如下：*C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*。</span><span class="sxs-lookup"><span data-stu-id="e5174-134">So, the full path that you'd navigate to would look similar to *C:\Program Files\dotnet\packs\Microsoft.NETCore.App.Ref\3.1.0\ref\netcoreapp3.1*.</span></span>

1. <span data-ttu-id="e5174-135">在剛開啟的 Moniker 資料夾中建立子資料夾。</span><span class="sxs-lookup"><span data-stu-id="e5174-135">Create a subfolder inside the moniker folder you just opened.</span></span> <span data-ttu-id="e5174-136">資料夾名稱會指出所要使用的語言。</span><span class="sxs-lookup"><span data-stu-id="e5174-136">The name of the folder indicates which language you want to use.</span></span> <span data-ttu-id="e5174-137">下表指定不同選項：</span><span class="sxs-lookup"><span data-stu-id="e5174-137">The following table specifies the different options:</span></span>

   | <span data-ttu-id="e5174-138">語言</span><span class="sxs-lookup"><span data-stu-id="e5174-138">Language</span></span>              | <span data-ttu-id="e5174-139">資料夾名稱</span><span class="sxs-lookup"><span data-stu-id="e5174-139">Folder name</span></span> |
   | --------------------- | ----------- |
   | <span data-ttu-id="e5174-140">巴西葡萄牙文</span><span class="sxs-lookup"><span data-stu-id="e5174-140">Brazilian Portuguese</span></span>  | <span data-ttu-id="e5174-141">*pt-br*</span><span class="sxs-lookup"><span data-stu-id="e5174-141">*pt-br*</span></span>     |
   | <span data-ttu-id="e5174-142">中文 (簡體)</span><span class="sxs-lookup"><span data-stu-id="e5174-142">Chinese (simplified)</span></span>  | <span data-ttu-id="e5174-143">*zh-hans*</span><span class="sxs-lookup"><span data-stu-id="e5174-143">*zh-hans*</span></span>   |
   | <span data-ttu-id="e5174-144">中文 (繁體)</span><span class="sxs-lookup"><span data-stu-id="e5174-144">Chinese (traditional)</span></span> | <span data-ttu-id="e5174-145">*zh-hant*</span><span class="sxs-lookup"><span data-stu-id="e5174-145">*zh-hant*</span></span>   |
   | <span data-ttu-id="e5174-146">法文</span><span class="sxs-lookup"><span data-stu-id="e5174-146">French</span></span>                | <span data-ttu-id="e5174-147">*fr*</span><span class="sxs-lookup"><span data-stu-id="e5174-147">*fr*</span></span>        |
   | <span data-ttu-id="e5174-148">德文</span><span class="sxs-lookup"><span data-stu-id="e5174-148">German</span></span>                | <span data-ttu-id="e5174-149">*de*</span><span class="sxs-lookup"><span data-stu-id="e5174-149">*de*</span></span>        |
   | <span data-ttu-id="e5174-150">義大利文</span><span class="sxs-lookup"><span data-stu-id="e5174-150">Italian</span></span>               | <span data-ttu-id="e5174-151">*it*</span><span class="sxs-lookup"><span data-stu-id="e5174-151">*it*</span></span>        |
   | <span data-ttu-id="e5174-152">日文</span><span class="sxs-lookup"><span data-stu-id="e5174-152">Japanese</span></span>              | <span data-ttu-id="e5174-153">*ja*</span><span class="sxs-lookup"><span data-stu-id="e5174-153">*ja*</span></span>        |
   | <span data-ttu-id="e5174-154">韓文</span><span class="sxs-lookup"><span data-stu-id="e5174-154">Korean</span></span>                | <span data-ttu-id="e5174-155">*ko*</span><span class="sxs-lookup"><span data-stu-id="e5174-155">*ko*</span></span>        |
   | <span data-ttu-id="e5174-156">俄文</span><span class="sxs-lookup"><span data-stu-id="e5174-156">Russian</span></span>               | <span data-ttu-id="e5174-157">*ru*</span><span class="sxs-lookup"><span data-stu-id="e5174-157">*ru*</span></span>        |
   | <span data-ttu-id="e5174-158">西班牙文</span><span class="sxs-lookup"><span data-stu-id="e5174-158">Spanish</span></span>               | <span data-ttu-id="e5174-159">*es*</span><span class="sxs-lookup"><span data-stu-id="e5174-159">*es*</span></span>        |

1. <span data-ttu-id="e5174-160">將您在步驟 3 解壓縮的 *.xml* 檔案複製到此新資料夾。</span><span class="sxs-lookup"><span data-stu-id="e5174-160">Copy the *.xml* files you extracted on step 3 to this new folder.</span></span> <span data-ttu-id="e5174-161">*.xml* 檔案會依照 SDK 資料夾細分，因此請將這些檔案複製到在步驟 4 選擇的相符 SDK。</span><span class="sxs-lookup"><span data-stu-id="e5174-161">The *.xml* files are broken down by SDK folders, so copy them to the matching SDK you chose on step 4.</span></span>

## <a name="modify-visual-studio-language"></a><span data-ttu-id="e5174-162">修改 Visual Studio 語言</span><span class="sxs-lookup"><span data-stu-id="e5174-162">Modify Visual Studio language</span></span>

<span data-ttu-id="e5174-163">若要讓 Visual Studio 使用不同的 IntelliSense 語言，請安裝適當的語言套件。</span><span class="sxs-lookup"><span data-stu-id="e5174-163">For Visual Studio to use a different language for IntelliSense, install the appropriate language pack.</span></span> <span data-ttu-id="e5174-164">這可以透過在[安裝期間](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional)或於稍後修改 Visual Studio 安裝來進行。</span><span class="sxs-lookup"><span data-stu-id="e5174-164">This can be done [during installation](/visualstudio/install/install-visual-studio#step-6---install-language-packs-optional) or at a later time by modifying the Visual Studio installation.</span></span> <span data-ttu-id="e5174-165">如果您已將 Visual Studio 設為選擇的語言，則 IntelliSense 安裝便已準備就緒。</span><span class="sxs-lookup"><span data-stu-id="e5174-165">If you already have Visual Studio configured to the language of your choice, your IntelliSense installation is ready.</span></span>

### <a name="install-the-language-pack"></a><span data-ttu-id="e5174-166">安裝語言套件</span><span class="sxs-lookup"><span data-stu-id="e5174-166">Install the language pack</span></span>

<span data-ttu-id="e5174-167">如果您並未在安裝期間安裝所需要的語言套件，請遵循以下方式更新 Visual Studio 來安裝語言套件：</span><span class="sxs-lookup"><span data-stu-id="e5174-167">If you didn't install the desired language pack during setup, update Visual Studio as follows to install the language pack:</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e5174-168">若要安裝、更新或修改 Visual Studio，您必須以具有系統管理權限的帳戶登入。</span><span class="sxs-lookup"><span data-stu-id="e5174-168">To install, update, or modify Visual Studio, you must log on with an account that has administrative permissions.</span></span> <span data-ttu-id="e5174-169">如需詳細資訊，請參閱[使用者權限和 Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio)。</span><span class="sxs-lookup"><span data-stu-id="e5174-169">For more information, see [User permissions and Visual Studio](/visualstudio/ide/user-permissions-and-visual-studio).</span></span>

1. <span data-ttu-id="e5174-170">在電腦上找到 Visual Studio 安裝程式。</span><span class="sxs-lookup"><span data-stu-id="e5174-170">Find the Visual Studio Installer on your computer.</span></span>

   <span data-ttu-id="e5174-171">例如，在執行 Windows 10，的電腦上，選取 [開始]  ，然後捲動到字母 [V]  ，它在其中列為 [Visual Studio Installer]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-171">For example, on a computer running Windows 10, select **Start**, and then scroll to the letter **V**, where it's listed as **Visual Studio Installer**.</span></span>

   ![在 Windows 上開啟 Visual Studio 安裝程式](./media/localized-intellisense/vs-installer-windows-start.png)

   > [!NOTE]
   > <span data-ttu-id="e5174-173">您也可以在下列位置找到 Visual Studio 安裝程式：</span><span class="sxs-lookup"><span data-stu-id="e5174-173">You can also find the Visual Studio Installer in the following location:</span></span>
   >
   > `C:\Program Files (x86)\Microsoft Visual Studio\Installer\vs_installer.exe`

   <span data-ttu-id="e5174-174">您可能需要更新安裝程式才能繼續。</span><span class="sxs-lookup"><span data-stu-id="e5174-174">You might have to update the installer before continuing.</span></span> <span data-ttu-id="e5174-175">若是如此，請遵循提示。</span><span class="sxs-lookup"><span data-stu-id="e5174-175">If so, follow the prompts.</span></span>

1. <span data-ttu-id="e5174-176">在安裝程式中，尋找要新增語言套件的目標 Visual Studio 版本，然後選擇 [修改]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-176">In the installer, look for the edition of Visual Studio that you want to add the language pack to, and then choose **Modify**.</span></span>

   ![更新或修改 Visual Studio](./media/localized-intellisense/vs-installer-modify.png)

   > [!IMPORTANT]
   > <span data-ttu-id="e5174-178">如果您沒有看到 [修改]  按鈕，但有看到 [更新]  按鈕，則表示您需要先更新 Visual Studio，之後才能修改安裝。</span><span class="sxs-lookup"><span data-stu-id="e5174-178">If you don't see a **Modify** button but you see an **Update** one instead, you need to update your Visual Studio before you can modify your installation.</span></span>
   > <span data-ttu-id="e5174-179">更新完成後，[修改]  按鈕應該會隨即出現。</span><span class="sxs-lookup"><span data-stu-id="e5174-179">After the update is finished, the **Modify** button should appear.</span></span>

1. <span data-ttu-id="e5174-180">在 [語言套件]  索引標籤中，選取或取消選取要安裝或解除安裝的語言。</span><span class="sxs-lookup"><span data-stu-id="e5174-180">In the **Language packs** tab, select or deselect the languages you want to install or uninstall.</span></span>

   ![Visual Studio [語言套件] 索引標籤](./media/localized-intellisense/vs-modify-language-packs.png)

1. <span data-ttu-id="e5174-182">選擇 [修改]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-182">Choose **Modify**.</span></span> <span data-ttu-id="e5174-183">更新會開始進行。</span><span class="sxs-lookup"><span data-stu-id="e5174-183">The update starts.</span></span>

### <a name="modify-language-settings-in-visual-studio"></a><span data-ttu-id="e5174-184">修改 Visual Studio 中的語言設定</span><span class="sxs-lookup"><span data-stu-id="e5174-184">Modify language settings in Visual Studio</span></span>

<span data-ttu-id="e5174-185">在安裝所需要的語言套件後，請修改您的 Visual Studio 設定，以使用不同語言：</span><span class="sxs-lookup"><span data-stu-id="e5174-185">Once you've installed the desired language packs, modify your Visual Studio settings to use a different language:</span></span>

1. <span data-ttu-id="e5174-186">開啟 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e5174-186">Open Visual Studio.</span></span>

1. <span data-ttu-id="e5174-187">在 [開始] 視窗中，選擇 [不使用程式碼繼續]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-187">On the start window, choose **Continue without code**.</span></span>

1. <span data-ttu-id="e5174-188">在主功能表中，選取 [工具]   > [選項]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-188">On the main menu, select **Tools** > **Options**.</span></span> <span data-ttu-id="e5174-189">[選項] 對話方塊隨即開啟。</span><span class="sxs-lookup"><span data-stu-id="e5174-189">The Options dialog opens.</span></span>

1. <span data-ttu-id="e5174-190">在 [環境]  資料夾下方，選擇 [國際設定]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-190">Under the **Environment** folder, choose **International Settings**.</span></span>

1. <span data-ttu-id="e5174-191">在 [語言]  下拉式清單中，選取所需要的語言。</span><span class="sxs-lookup"><span data-stu-id="e5174-191">On the **Language** drop-down, select the desired language.</span></span> <span data-ttu-id="e5174-192">選擇 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-192">Choose **OK**.</span></span> 

1. <span data-ttu-id="e5174-193">對話方塊會通知您必須重新啟動 Visual Studio，才能使變更生效。</span><span class="sxs-lookup"><span data-stu-id="e5174-193">A dialog informs you that you have to restart Visual Studio for the changes to take effect.</span></span> <span data-ttu-id="e5174-194">選擇 [確定]  。</span><span class="sxs-lookup"><span data-stu-id="e5174-194">Choose **OK**.</span></span>

1. <span data-ttu-id="e5174-195">重新啟動 Visual Studio。</span><span class="sxs-lookup"><span data-stu-id="e5174-195">Restart Visual Studio.</span></span>

<span data-ttu-id="e5174-196">之後在開啟以您剛安裝 IntelliSense 檔案版本為目標的 .NET Core 專案時，IntelliSense 應該就會如預期般運作。</span><span class="sxs-lookup"><span data-stu-id="e5174-196">After this, your IntelliSense should work as expected when you open a .NET Core project that targets the version of the IntelliSense files you just installed.</span></span>

## <a name="see-also"></a><span data-ttu-id="e5174-197">另請參閱</span><span class="sxs-lookup"><span data-stu-id="e5174-197">See also</span></span>

- [<span data-ttu-id="e5174-198">Visual Studio 中的 IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e5174-198">IntelliSense in Visual Studio</span></span>](/visualstudio/ide/using-intellisense)
